---
title: Multi-Tenancy Patterns
created: 2026-05-19
updated: 2026-05-19
type: concept
tags: [architecture, security, database, devops]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Multi-Tenancy Patterns

Architectural approaches to serve multiple tenants (customers/organizations) from a single application instance while maintaining strict data isolation.

## Overview

Multi-tenancy is a core architectural concern for SaaS products. Invaice uses Auth0 Organizations for identity-level tenancy, with every database query scoped by `facility_id` to ensure no cross-tenant data leakage.

## Key Patterns

### Tenant ID Scoping
Every query includes a `facility_id` filter. This is the primary isolation mechanism in [[invaice]]:
- Every endpoint returns only data for the authenticated facility
- Verified by integration tests
- Enforced at the application layer, not just database

### Auth0 Organizations
One Auth0 Organization per tenant. Organization membership determines tenant identity post-authentication.

### Shared Infrastructure, Isolated Data
- Same application servers, same database, different rows
- `facility_id` column on all tenant-scoped tables
- No shared mutable state between tenants

## Related

- [[invaice]] — the product implementing multi-tenancy
- [[auth0]] — identity provider with Organizations support