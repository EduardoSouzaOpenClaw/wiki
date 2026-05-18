# MVP Scope — Invaice

> This document is the source of truth for what ships in the MVP pilot.
> Anything not listed under "In scope" is deferred. No exceptions without editing this file.

---

## The user journey that must work end-to-end

A processor at a CCRC facility logs in, uploads an invoice (PDF via web or photo via camera), waits for AI extraction to complete, reviews and corrects the extracted fields, approves the invoice, and downloads a CSV export — all within a single authenticated session, scoped to their facility.

**Step-by-step:**

1. **Login** — user authenticates via Auth0, is placed in the correct facility tenant
2. **Upload** — drags a PDF or captures a photo; file is validated and queued for extraction
3. **Extraction** — Gemini/Vertex AI extracts fields with confidence scores; user is notified when ready
4. **Review** — split-screen view; user corrects low-confidence fields inline and saves
5. **Approval** — user (or auto-approval rule) approves the invoice; approval is final
6. **Export** — approved invoices exported as a single CSV format; file downloads immediately

An admin can also: manage facility users (invite, assign roles, deactivate), configure auto-approval rules, and manage vendor profiles.

---

## In scope (definitively)

### Authentication & Multi-tenancy
- Auth0 Organizations: one org per facility, full tenant isolation on every query via `facility_id`
- Three roles enforced via Auth0 RBAC: `admin`, `manager`, `processor`
- JWT validation, session timeout (30 min inactivity), email verification, password reset

### Invoice Intake
- Web upload: drag-and-drop PDF/JPG/PNG; file type + size validation
- Camera capture: mobile browser photo with auto-enhancement
- Duplicate detection: same vendor + invoice number + amount → blocked with warning
- Upload limit: max 10 concurrent uploads per user

### AI Extraction
- Gemini via Vertex AI: extracts header fields + line items from uploaded document
- Confidence scoring per field: High (≥90%), Medium (70–89%), Low (<70%)
- Cross-field validation: line item sum vs. stated total, required-field check
- Extraction failure handling: notify user, allow manual re-trigger

### Review & Verification
- Split-screen: original document (left) + extracted fields (right)
- Inline editing of all extracted fields before approval
- Confidence indicators shown per field (color-coded)
- Auto-save on field change
- Status tracking: `pending` → `extracting` → `needs_review` → `approved` → `exported`

### Approval
- Manual approval by any authenticated user (all three roles)
- Auto-approval rules: configurable per facility — conditions on confidence threshold and amount ceiling
- Auto-approval reversal window: configurable (default 48 hours)
- Approved invoices are immutable after reversal window closes or after export

### Export
- Single CSV format (one fixed column layout, no template selection)
- Single-invoice and batch export (up to 500 invoices per batch)
- Export history with download links (time-limited GCS URLs)
- Export audit log entry per event

### Vendor Management
- Vendor profiles: name, contact info, address, tax ID
- Vendor linked to invoices for display and filtering
- Vendor list with basic invoice count and last-seen date

### Notifications
- Email notifications: extraction complete, approval required, auto-approval triggered, export ready
- In-app notification feed: same events, grouped by date, markable as read

### User & Team Management (Admin only)
- Invite users by email, assign role at invite time
- Deactivate / reactivate users
- Role reassignment

### Non-functional
- All queries tenant-scoped by `facility_id` — no cross-tenant data leakage
- PHI never logged at INFO level; `redact()` helper used on all patient-adjacent fields
- Full audit trail: every approval, correction, export, and user-management action logged
- Health checks: DB, GCS, Vertex AI, email service

---

## Out of scope (move to post-MVP issues)

| Feature | Reason deferred |
|---|---|
| Vendor portal (public upload links) | Reduces pilot complexity; vendors can email/upload directly |
| Vendor pattern learning / AI retraining per vendor | Requires sufficient correction volume; not available at pilot launch |
| Analytics dashboard | No decision-making value until volume accumulates |
| Multiple export templates / ERP field mapping | Single format unblocks pilot; custom mapping is post-validation work |
| Mobile native app | Mobile web camera capture is sufficient for pilot |
| SSO / SAML | No enterprise SSO requirement from pilot customer |
| Direct ERP API integration | CSV export meets the immediate pilot need |
| Email-to-invoice intake | Web upload + camera covers pilot workflow |
| Advanced workflow automation beyond auto-approval | Single-rule auto-approval covers the pilot use case |
| A/B testing framework | Not needed until product iterates post-pilot |
| Billing / subscription management | Pilot is pre-commercial |

Each deferred item should become a GitHub Issue (type: Feature or Epic) before the post-MVP sprint begins.

---

## Quality bar (non-negotiable for MVP)

These are hard gates. A PR that ships a feature but violates any of these does not merge.

### Correctness
- Every tenant-scoped endpoint returns only data for the authenticated facility — verified by integration tests
- Approval is irreversible after the reversal window; no code path bypasses this
- Duplicate invoices are always blocked before extraction begins

### Security
- No PHI at INFO log level anywhere in the codebase
- Auth0 JWT validated on every protected endpoint; `@Public()` only on explicitly unauthenticated routes
- `pnpm audit --audit-level=high` passes with zero high/critical CVEs in CI
- `pnpm install --frozen-lockfile` in all CI jobs; no re-resolution

### Test coverage
- All five pipeline steps covered by at least one integration/e2e test
- Every role-permission boundary (admin vs. manager vs. processor) has a test
- Zero flaky tests in CI — fix or delete before merging

### Operations
- Health check endpoint returns non-200 if any critical dependency (DB, GCS, Vertex AI) is degraded
- Extraction failures surface as a user-visible error + retry option — no silent failures
- Audit log entry written for: upload, extraction complete, field correction, approval, export

### Definition of done (every PR)
- `pnpm lint && pnpm format` clean in the relevant sub-repo
- Migration committed if schema changed
- PR body contains `Closes #N`
- Reviewer subagent sign-off before merge