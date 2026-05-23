---
title: "Contract Driven Development with AI Agents"
summary: "CDC em contexto de múltiplos AI coding agents modifies serviços simultaneamente — problema aberto com soluções emergentes via Pact, MCP e schema-first design"
source: Multiplas fontes consolidadas
tags: [contract-driven-development, ai-agents, multi-agent, api-contracts, pact, mcp]
created: 2026-05-23
sources: [raw/articles/brave-search-cdc_ai-2026-05-23.md]
---

# Contract Driven Development with AI Agents

## Problema Central

Quando múltiplos AI agents trabalham em serviços diferentes simultaneamente:
1. Agent A modifica API do serviço X
2. Agent B está usando essa API no serviço Y
3. Nenhum dos dois "sabe" que o contrato mudou
4. Breaking change propaga silenciosamente

## Soluções emergentes

### 1. Pact / PactFlow
- Consumer-driven contracts para validar que Provider não quebrou consumer
- Integração MCP para AI agents consultarem contratos durante code generation
- Pact Broker para rastrear versões de contratos

### 2. Model Context Protocol (MCP)
- Anthropic's MCP impõe schema-validated messages via JSON-RPC 2.0
- Toda mensagem tem tipo explícito — reduce misinterpretation entre agents
- paper: https://arxiv.org/html/2601.08815v1

### 3. Schema-first validation
- JSON schemas em todo boundary
- Breaking changes requer novo major version
- Duas versões ativas durante migration

## Frameworks/Tools
- **PactFlow** — commercial Pact com MCP server
- **Signadot SmartTests** — "Smart Diff" model que compara baseline vs new responses
- **SmartBear MCP** — expõe contract-testing_* tools para AI IDEs

## Leituras recomendadas
- https://nordicapis.com/how-llms-are-breaking-the-api-contract-and-why-that-matters/
- https://github.blog/ai-and-ml/generative-ai/multi-agent-workflows-often-fail-heres-how-to-engineer-ones-that-dont/
- https://docs.pact.io/ai_tools/installation

## Tópicos relacionados
- [[ai-augmented-contract-testing]]
- [[pact-flow-mcp-server]]
- [[multi-agent-systems-fail]]
- [[model-context-protocol]]

## Tags
#contract-driven-development #ai-agents #multi-agent