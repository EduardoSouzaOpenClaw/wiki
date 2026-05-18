---
title: Invaice
created: 2026-05-18
updated: 2026-05-18
type: entity
tags: [startup, product, saas, healthcare, invoice-automation]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Invaice

Invoice automation SaaS for CCRC (Continuing Care Retirement Community) facilities. MVP in development as of May 2026.

## Overview

Invaice extracts data from invoice documents using AI (Gemini/Vertex AI) and provides a review/approval workflow before CSV export. Target users: facility processors, managers, and admins at CCRC facilities.

## Key Facts

- **MVP scope:** Auth0 RBAC multi-tenancy, PDF/photo upload, AI extraction with confidence scoring, split-screen review, manual/auto-approval, single-format CSV export, vendor management, notifications, admin user management
- **Stack (inferred from scope):** Go backend, TypeScript frontend, Auth0, Vertex AI/Gemini, GCS
- **Quality bar:** Tenant isolation by `facility_id`, no PHI at INFO logs, full audit trail, zero high/critical CVEs in CI
- **Pilot customer:** A CCRC facility (exact name not specified in MVP scope)

## Architecture Notes

- Tenant isolation: every query scoped by `facility_id`
- Auth0 Organizations: one org per facility
- Three roles: admin, manager, processor
- Invoice status pipeline: `pending` → `extracting` → `needs_review` → `approved` → `exported`
- Auto-approval: configurable per facility with confidence threshold + amount ceiling
- Immutable after reversal window (default 48h) or export

## Related

- [[auth0]] — authentication provider
- [[vertex-ai]] — AI extraction infrastructure
- [[multi-tenancy-patterns]] — tenant isolation approach