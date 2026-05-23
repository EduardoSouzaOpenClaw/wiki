---
title: "Multi-Agent API Contracts"
summary: "Data contracts para agents: manter ferramentas e schemas estáveis enquanto sistemas evoluem, com versionamento explícito e validação"
source: https://medium.com/@deolesopan/data-contracts-for-agents-keep-tools-and-schemas-stable-as-systems-evolve-8af6f3e024ba
tags: [multi-agent, api-contracts, data-contracts, schema-stability]
created: 2026-05-23
sources: [raw/articles/brave-search-multi_agent_specific-2026-05-23.md]
---

# Multi-Agent API Contracts

## Fonte
https://medium.com/@deolesopan/data-contracts-for-agents-keep-tools-and-schemas-stable-as-systems-evolve-8af6f3e024ba

## Conceito

Data contracts para agents AI são acordos explícitos sobre:
- Formato de dados trocados entre agents
- Versões de schemas
- Breaking change policy

## Regras fundamentais

### Breaking Changes = New Major Version
- Renamed fields, removed fields, enum meaning changes = breaking
- Manter duas versões ativas durante migration
- v1 fica estável enquanto v2 rola out

### Schema Validation at Every Boundary
- Agent que recebe mensagem valida contra schema
- Não processa se violação detectada
- Retry ou escalate

### Tool/SKU Stability
- Ferramentas mudam versão, não comportamento
- Se comportamento muda = breaking change

## Frameworks mencionados
- **MCP** — Model Context Protocol (Anthropic)
- **Pact** — consumer-driven contracts

## Tópicos relacionados
- [[contract-driven-development-ai-agents]]
- [[multi-agent-systems-fail]]
- [[model-context-protocol]]

## Tags
#multi-agent #api-contracts