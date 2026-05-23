---
title: "Model Context Protocol (MCP)"
summary: "Protocolo da Anthropic para comunicação entre AI agents e ferramentas — schema-validated messages via JSON-RPC 2.0"
source: https://futureagi.substack.com/p/why-do-multi-agent-llm-systems-fail
tags: [mcp, anthropic, protocol, multi-agent, schema-validation]
created: 2026-05-23
sources: [raw/articles/brave-search-multi_agent_specific-2026-05-23.md]
---

# Model Context Protocol (MCP)

## Fonte
- https://futureagi.substack.com/p/why-do-multi-agent-llm-systems-fail
- https://developer.smartbear.com/smartbear-mcp/docs/contract-testing-with-pactflow

## Conceito

MCP é um protocolo de Anthropic que impõe:
- **Schema-validated messages** — todo message tem tipo explícito
- **JSON-RPC 2.0** — formato padronizado de comunicação
- **Tool discovery** — agents descobrem capabilities de outros agents automaticamente

## Por que importa para multi-agent

O problema central de multi-agent é que agents confiam que output do outro está no formato esperado. MCP resolve isso com:

1. **Tipo explícito** — mensagem declara seu tipo/camada
2. **Validation automática** — receptor valida message contra schema antes de processar
3. **Tool contracts** — toda ferramenta expõe schema do que aceita/retorna

## Relação com Contract Testing

PactFlow MCP Server expõe `contract-testing_*` tools que usam MCP:
- Agent pode verificar se mudança quebra contrato antes de fazer merge
- Validação automática de breaking changes

## Tópicos relacionados
- [[contract-driven-development-ai-agents]]
- [[pact-flow-mcp-server]]
- [[multi-agent-systems-fail]]

## Tags
#mcp #anthropic #protocol