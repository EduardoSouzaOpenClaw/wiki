---
title: "Multi-Agent Systems Fail Patterns"
summary: "7 razões pelas quais sistemas multi-agent falham: stale snapshots, schema violations, kontrak不复", source: https://galileo.ai/blog/why-multi-agent-systems-fail
tags: [multi-agent, failure-modes, coordination, schema-validation]
created: 2026-05-23
sources: [raw/articles/brave-search-multi_agent_specific-2026-05-23.md]
---

# Multi-Agent Systems Fail Patterns

## Fonte
https://galileo.ai/blog/why-multi-agent-systems-fail

## 7 Failure Modes Identificados

### 1. Stale Snapshot Problem
Agent B opera com snapshot desatualizada do mundo. Agent A mudou user schema, mas Agent B não "sabe" e usa estrutura antiga.

### 2. Schema Violations Propagate
Mensagens entre agents violam schema sem detecção. Bad state se propaga antes de ser pego.

### 3. Shared Tool Ownership
Dois agents modificam mesma ferramenta divergently, sem coordenação. Conflitos não detectados.

### 4. Communication Protocol Mismatch
Agents usam formatos diferentes para mesma mensagem. Falta tipagem explícita.

### 5. Implicit vs Explicit Semantics
Mesmo nome de campo significa coisas diferentes em contexts diferentes. Ambiguidade não detectada.

### 6. No Contract at Handoffs
Passagem de dados entre agents treated como "data passing" em vez de "contract with validation". Falta schema enforcement.

### 7. Asynchronous Blind Spots
Agent não sabe se output foi processado corretamente por próximo agent. Falta feedback loop.

## Soluções Recomendadas

- Tratar schema violations como contract failures
- JSON schemas em todo boundary
- Retry/repair/escalate antes de bad state propagar
- Structured communication protocols (e.g., MCP)

## Tópicos relacionados
- [[contract-driven-development-ai-agents]]
- [[model-context-protocol]]
- [[multi-agent-api-contracts]]

## Tags
#multi-agent #failure-modes