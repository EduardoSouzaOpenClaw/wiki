---
title: "AI-Ready Codebase Guide 2025"
summary: "Guia prático: CLAUDE.md templates, Vertical Slice Architecture, e técnicas de otimização que melhoraram AI code generation em 80%"
source: https://llmx.tech/blog/ai-ready-codebase-claude-cursor-integration-guide/
tags: [ai-readiness, codebase-structure, claude-md, vertical-slice, best-practices]
created: 2026-05-23
sources: [raw/articles/brave-search-vsa_specific-2026-05-23.md]
---

# AI-Ready Codebase Guide 2025

## Fonte
https://llmx.tech/blog/ai-ready-codebase-claude-cursor-integration-guide/

## Conceitos principais

### CLAUDE.md
Arquivo de guidelines que documenta:
- Convenções de código do projeto
- Patterns arquitetônicos adotados
- Regras de nomenclatura
- Constraints técnicos

### Vertical Slice Architecture (VSA)
Organiza código por feature, não por camada técnica:
- API endpoints + validation + business logic + data access no mesmo lugar
- Cada feature é uma "fatia" independente
-好处: AI consegue entender escopo completo de uma feature sem navegar por várias camadas

### Métricas
- 80% melhoria em AI code generation reportada com essas práticas

## Práticas recomendadas

1. Pastas descritivas + nomes de arquivos significativos
2. Types explícitos (TypeScript/Python)
3. Testes como documentação (AI usa tests como source of truth)
4. Boundaries claros entre bounded contexts
5. Documentação inline de decisões arquiteturais

## Tópicos relacionados
- [[vertical-slice-architecture]]
- [[ai-friendly-codebase-patterns]]
- [[coding-guidelines-for-ai-agents]]

## Tags
#ai-readiness #codebase-structure