---
title: Vertex AI
created: 2026-05-19
updated: 2026-05-19
type: entity
tags: [company, ai, ml, google, infrastructure]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Vertex AI

Google Cloud's managed ML platform, used by [[invaice]] to run Gemini for invoice data extraction.

## Overview

Vertex AI provides managed infrastructure for training and serving ML models, including Gemini (Google's family of large language models). In Invaice, Vertex AI hosts the Gemini model that extracts structured fields from uploaded invoice documents.

## Key Facts

- **Provider:** Google Cloud
- **Used in Invaice for:** Running Gemini to extract header fields and line items from invoice PDFs/photos
- **Output:** Structured JSON with per-field confidence scores; cross-field validation (line item sum vs. stated total)

## Related

- [[invaice]] — product using Vertex AI
- [[gemini]] — the model running on Vertex AI
- [[multi-tenancy-patterns]] — tenant isolation consideration for AI calls