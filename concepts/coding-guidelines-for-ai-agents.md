---
title: "Coding Guidelines for AI Agents"
summary: "JetBrains IntelliJ IDEA guide: como criar guidelines.md que documenta convenções do codebase para AI agents seguirem"
source: https://blog.jetbrains.com/idea/2025/05/coding-guidelines-for-your-ai-agents/
tags: [coding-guidelines, ai-agents, jetbrains, claude-md, conventions]
created: 2026-05-23
sources: [raw/articles/brave-search-ai_friendly-2026-05-23.md]
---

# Coding Guidelines for AI Agents

## Fonte
https://blog.jetbrains.com/idea/2025/05/coding-guidelines-for-your-ai-agents/

## Conceito

JetBrains IDEA (via Junie AI agent) recomenda criar `guidelines.md` com:
- Convenções de código do projeto
- Patterns adotados
- Regras de nomenclatura
- Constraints técnicos

O agent pode gerar um draft inicial baseado no codebase existente, e o developer refina.

## Estrutura recomendada de um guidelines.md

```markdown
# Coding Guidelines

## Project Overview
[descrição do projeto e stack]

## Architecture
[patterns arquiteturais adotados]

## Coding Conventions
### Naming
- [convenção de nomenclatura]
### File Structure
- [como organizar arquivos]
### Error Handling
- [padrão de tratamento de erros]

## Testing
- [como escrever testes]
- [naming convention para testes]

## Git Conventions
- [branch strategy, commit messages, etc]
```

## Ferramenta
- JetBrains IDEA com Junie — AI coding agent integrado ao IDE
- Gera guidelines.md automaticamente baseado no codebase

## Tópicos relacionados
- [[ai-ready-codebase-guide-2025]]
- [[ai-friendly-codebase-patterns]]

## Tags
#coding-guidelines #ai-agents