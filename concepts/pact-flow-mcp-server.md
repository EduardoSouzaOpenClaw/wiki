---
title: "PactFlow MCP Server"
summary: "Server que expõe contract-testing tools via Model Context Protocol, integrando Pact tests diretamente em AI IDEs como Claude Code e GitHub Copilot"
source: https://pactflow.io/blog/pactflow-mcp-server/
tags: [mcp, pact, contract-testing, ai-agents, ide-integration]
created: 2026-05-23
sources: [raw/articles/brave-search-pact_specific-2026-05-23.md]
---

# PactFlow MCP Server

## Fonte
https://pactflow.io/blog/pactflow-mcp-server/

## Conceito

PactFlow lançou MCP Server que expõe ferramentas `contract-testing_*` além do que o CLI suporta:
- Queries na matriz de contratos
- Acesso estruturado a todos os recursos do broker
- Integração direta com GitHub Copilot e Claude Code

Documentação: https://docs.pact.io/ai_tools/pactflow-skill

## Ferramentas expostas (SmartBear MCP)
- `contract-testing_*` tools
- Matrix queries
- Structured access a todos os broker resources

## Relevância para Invaice

Se a equipe de Invaice adotar AI coding agents (Claude Code, etc), ter contract testing via MCP permite que o agent:
1. Detecte quando uma mudança quebra contrato
2. Regenere contratos automaticamente
3. Validate que novos serviços cumplen contratos existentes

## Tópicos relacionados
- [[ai-augmented-contract-testing]]
- [[contract-driven-development-ai-agents]]
- [[model-context-protocol]]

## Tags
#mcp #pact #ai-agents