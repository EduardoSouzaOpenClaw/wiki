---
title: "How LLMs Are Breaking API Contracts"
summary: "LLMs frequentemente quebram contratos de API durante code generation — riscos de segurança e governança, e como preparar APIs para consumo por AI agents"
source: https://nordicapis.com/how-llms-are-breaking-the-api-contract-and-why-that-matters/
tags: [llm, api-contracts, ai-safety, security, governance]
created: 2026-05-23
sources: [raw/articles/brave-search-cdc_ai-2026-05-23.md]
---

# How LLMs Are Breaking API Contracts

## Fonte
https://nordicapis.com/how-llms-are-breaking-the-api-contract-and-why-that-matters/

## Key Insight

LLMs durante code generation frequentemente:
- Omit campos obrigatórios
- Assumem tipos incorretos
- Usam valores default inconsistentes
- Ignoram constraints de schema

Isso cria riscos de segurança e governança em produção.

## Implicações para API Design

APIs consumidas por AI agents precisam de:
1. **Schema estrito** — não permitir ambigüidade
2. **Validation rigorosa** — rejeitar payloads que violam contrato
3. **Versioning explícito** — mudanças breaking requerem nova versão
4. **Feedback loops** — AI agent precisa saber quando quebrou contrato

## Tópicos relacionados
- [[contract-driven-development-ai-agents]]
- [[multi-agent-api-contracts]]
- [[api-versioning]]

## Tags
#llm #api-contracts #ai-safety