---
title: CSV Export
created: 2026-05-19
updated: 2026-05-19
type: concept
tags: [data, tool, product]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# CSV Export

Comma-separated values file export — the output format used by [[invaice]] for approved invoice data.

## Overview

In Invaice, approved invoices are exported as CSV files. The MVP ships a single fixed column layout (no template selection). Exports can be single-invoice or batch (up to 500 invoices).

## Key Facts

- **Format:** Single fixed CSV layout (no template selection in MVP)
- **Batch size:** Up to 500 invoices per batch export
- **Delivery:** Time-limited GCS (Google Cloud Storage) URLs for download
- **Audit:** Export event written to audit log per export action

## Related

- [[invaice]] — the product producing CSV exports
- [[multi-tenancy-patterns]] — tenant isolation applies to exports too