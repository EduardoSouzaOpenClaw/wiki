---
title: Invaice
created: 2026-05-18
updated: 2026-05-22
type: entity
tags: [startup, product, saas, healthcare, invoice-automation]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md, raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Invaice

Invoice automation SaaS for CCRC (Continuing Care Retirement Community) facilities. MVP in active development as of May 2026, targeting a single pilot customer facility.

## Overview

Invaice extracts data from invoice documents using AI (Gemini via Vertex AI) and provides a review/approval workflow before CSV export. Target users: facility processors, managers, and admins at CCRC facilities.

The full user journey: processor logs in → uploads PDF/photo → AI extracts fields with confidence scores → user reviews/corrects in split-screen → approves (manual or auto) → downloads CSV export.

## Key Facts

- **Authentication:** Auth0 with Organizations (one org per facility), three roles: admin, manager, processor
- **Invoice intake:** drag-and-drop PDF or camera capture (mobile), duplicate detection (vendor + invoice number + amount), max 10 concurrent uploads
- **AI extraction:** Gemini via Vertex AI, confidence scoring per field (High ≥90%, Medium 70–89%, Low <70%), cross-field validation, failure handling with retry
- **Review:** split-screen view (original left, extracted right), inline editing, color-coded confidence, auto-save
- **Approval:** manual (any role) or auto (configurable confidence threshold + amount ceiling), 48h reversal window, immutable after close
- **Export:** single fixed CSV format, single or batch (up to 500), time-limited GCS URLs, audit log
- **Vendor management:** profiles with name, contact, address, tax ID; linked to invoices for display/filtering
- **Notifications:** email + in-app feed for extraction complete, approval required, auto-approval, export ready
- **Stack (inferred):** Go backend, TypeScript frontend, Auth0, Vertex AI/Gemini, GCS
- **Quality gates:** tenant isolation by `facility_id`, no PHI at INFO logs, `pnpm audit` pass, full audit trail, zero high/critical CVEs in CI

## Architecture Notes

- Tenant isolation: every query scoped by `facility_id` — no cross-tenant data leakage
- Auth0 Organizations: one org per facility
- Invoice status pipeline: `pending` → `extracting` → `needs_review` → `approved` → `exported`
- Auto-approval configurable per facility with confidence threshold + amount ceiling
- Approved invoices immutable after reversal window (default 48h) or export
- **Health checks:** DB, GCS, Vertex AI, email service
- **Cross-field validation:** line item sum vs. stated total, required-field check
- **Upload limit:** max 10 concurrent uploads per user

## Quality Gates

- Tenant-scoped endpoints verified by integration tests (no cross-tenant leakage)
- Approval irreversible after reversal window — no bypass paths
- Duplicate invoices blocked before extraction
- No PHI at INFO log level; `redact()` helper on patient-adjacent fields
- `pnpm audit --audit-level=high` passes with zero high/critical CVEs in CI
- `pnpm install --frozen-lockfile` in all CI jobs
- Full audit trail: upload, extraction complete, field correction, approval, export

## Related

- [[auth0]] — authentication provider
- [[vertex-ai]] — AI extraction infrastructure
- [[multi-tenancy-patterns]] — tenant isolation approach
- [[invoice-automation]] — concept covering AI invoice workflows

## Deferred to Post-MVP

- Public vendor portal, AI retraining per vendor, analytics dashboard, multiple export templates / ERP field mapping, mobile native app, SSO/SAML, direct ERP API integration, email-to-invoice intake, advanced workflow automation, A/B testing framework, billing/subscription management

## Related

- [[auth0]] — authentication provider
- [[vertex-ai]] — AI extraction infrastructure
- [[multi-tenancy-patterns]] — tenant isolation approach