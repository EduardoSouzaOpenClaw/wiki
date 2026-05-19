---
title: Gemini
created: 2026-05-19
updated: 2026-05-19
type: entity
tags: [model, ai, google, llm]
sources: [raw/articles/invaice-mvp-scope-2026-05-18.md]
---

# Gemini

Google's family of large language models, used in [[invaice]] for invoice data extraction via [[vertex-ai]].

## Overview

Gemini is Google's multi-modal LLM family, capable of understanding text, images, and documents. In Invaice, Gemini is hosted on Vertex AI and processes uploaded invoice documents (PDF or photo) to extract structured field data.

## Key Facts

- **Provider:** Google
- **Used in Invaice for:** Extracting header fields and line items from invoice documents
- **Confidence scoring:** Per-field confidence scores output (High ≥90%, Medium 70–89%, Low <70%)
- **Capabilities:** Multi-modal (text + image), document understanding

## Related

- [[invaice]] — product using Gemini
- [[vertex-ai]] — the platform hosting Gemini
- [[multi-tenancy-patterns]] — tenant isolation for AI inference calls