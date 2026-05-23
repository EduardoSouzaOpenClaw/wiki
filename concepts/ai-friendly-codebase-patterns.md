---
title: "AI-Friendly Codebase Patterns"
summary: "Padrões de código que tornam bases de código mais navegáveis por AI coding agents: naming, modularidade, contracts, testabilidade"
source: Multiplas fontes consolidadas
tags: [ai-friendly, codebase-patterns, naming, modularity, contracts]
created: 2026-05-23
sources: [raw/articles/brave-search-ai_friendly-2026-05-23.md]
---

# AI-Friendly Codebase Patterns

## Conceitos consolidados de múltiplas fontes

### 1. Explicit over Implicit

AI agents falham mais em código com:
- Side effects ocultos
- DI implícito
- Herança profunda
- Globals/mutable state

**Recomendação:** DI explícito, funções puras quando possível, immutabilidade.

### 2. Flat is Better Than Nested

Estruturas de arquivos rasas com nomes descritivos superam pastas profundas com nomes crípticos.

**Recomendação:**
```
src/
  invoices/
    create-invoice.ts
    list-invoices.ts
    approve-invoice.ts
```
vs
```
src/
  controllers/
  services/
  repositories/  # cada um com nomes cryptic
```

### 3. Tests as Documentation

AI agents que usam tests como source of truth geram código melhor porque:
- Testes mostram intent Expected Behavior
- Testes funcionam como contrato implícito
- Testes indicam edge cases

**Recomendação:** Nome de teste deve descrever behavior, não só método testado.

### 4. Bounded Contexts Claros

Sistemas com fronteiras bem definidas são mais fáceis de AI fazer reasoning sem pedir contexto a cada comando.

**Recomendação:** Cada bounded context tem API surface mínima e contratos explícitos.

### 5. Types Explícitos

TypeScript/Python com types explícitos ajuda AI a inferir escopo.

**Recomendação:** Evitar `any` everywhere, usar types Discrimination unions.

## Fontes
- https://blog.jetbrains.com/idea/2025/05/coding-guidelines-for-your-ai-agents/
- https://www.reddit.com/r/ClaudeAI/comments/1mgma4p/should_we_start_optimizing_codebases_for_ai/
- https://medium.com/@kndkdarshan/cracking-the-code-how-to-make-your-codebase-ai-friendly-and-developer-friendly-9299eb51100a

## Tópicos relacionados
- [[vertical-slice-architecture]]
- [[ai-ready-codebase-guide-2025]]
- [[coding-guidelines-for-ai-agents]]

## Tags
#ai-friendly #codebase-patterns