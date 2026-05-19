---
title: Auth0
created: 2026-05-19
updated: 2026-05-19
type: entity
tags: [company, security, identity, saas]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Auth0

Identity and authentication platform (now part of Okta) used by [[invaice]] for user authentication and multi-tenant authorization.

## Overview

Auth0 provides authentication-as-a-service with support for Organizations (multi-tenancy), RBAC, and JWT validation. Used in Invaice to isolate CCRC facility tenants.

## Key Facts

- **Product:** Authentication/authorization platform, part of Okta since 2021
- **Used in Invaice for:** Organizations (one org per facility tenant), RBAC with three roles (admin, manager, processor), JWT validation, session management, email verification, password reset
- **Session timeout:** 30 min inactivity

## In Invaice Architecture

- One Auth0 Organization per facility — full tenant isolation on every query via `facility_id`
- Three roles enforced via Auth0 RBAC
- `@Public()` decorator only on explicitly unauthenticated routes
- Email verification and password reset flow

## Related

- [[invaice]] — the product using Auth0
- [[multi-tenancy-patterns]] — the isolation pattern Auth0 enables