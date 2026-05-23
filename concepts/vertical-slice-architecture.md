---
title: "Vertical Slice Architecture (VSA)"
summary: "Padrão arquitetural que organiza código por feature (não por camada), facilitando AI agents a entender contexto completo de cada feature"
source: https://medium.com/@richardhightower/ai-optimizing-codebase-architecture-for-ai-coding-tools-ff6bb6fdc497
tags: [vertical-slice, architecture, ai-friendly, code-organization]
created: 2026-05-23
sources: [raw/articles/brave-search-vsa_specific-2026-05-23.md]
---

# Vertical Slice Architecture (VSA)

## Fonte
- https://medium.com/@richardhightower/ai-optimizing-codebase-architecture-for-ai-coding-tools-ff6bb6fdc497
- https://cloudurable.com/blog/a-deeper-dive-when-the-vibe-dies-comparing-codebase-architectures-for-ai-tools/
- https://www.furdak.net/articles/dotnet-vsa-webapi-skill

## Conceito

VSA organiza código por feature/feature slices, não por camadas técnicas (controllers, services, repositories).

Cada "fatia" contém:
- API endpoints
- Validação
- Business logic
- Data access

## Por que é AI-friendly

1. **Contexto completo** — AI consegue ver tudo sobre uma feature em um lugar
2. **Menos navegação** — não precisa pular entre pastas de controllers/services/repositories
3. **Mudanças autocontidas** — feature mudança não afeta camadas cruzadas
4. **Regra clara** — fácil para AI inferir onde colocar novo código

## Comparação com outras arquiteturas

| Arquitetura | AI Friendliness | Reusabilidade | Complexidade |
|-------------|-----------------|---------------|--------------|
| Vertical Slice | Alta | Média (duplicação controlada) | Baixa |
| Clean/Hexagonal | Média | Alta | Alta |
| Layered | Baixa (muita navegação) | Alta | Média |
| Atomic Composables | Média | Alta | Alta |

## Alternativa: Pipeline Architecture
Clara para AI, mas requer disciplina. Cada passo do pipeline é bem definido.

## Tópicos relacionados
- [[ai-ready-codebase-guide-2025]]
- [[ai-friendly-codebase-patterns]]
- [[clean-architecture]]

## Tags
#vertical-slice #architecture #ai-friendly