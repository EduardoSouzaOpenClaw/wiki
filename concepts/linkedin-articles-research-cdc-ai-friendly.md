---
title: "LinkedIn Articles Research — CDC & AI-Friendly Architecture"
sources: [raw/articles/brave-search-cdc_ai-2026-05-23.md, raw/articles/brave-search-ai_friendly-2026-05-23.md, raw/articles/brave-search-pact_specific-2026-05-23.md, raw/articles/brave-search-vsa_specific-2026-05-23.md, raw/articles/brave-search-multi_agent_specific-2026-05-23.md]
created: 2026-05-23
tags: [linkedin, articles, research, cdc, ai-friendly, content]
---

# LinkedIn Articles Research — CDC & AI-Friendly Architecture

> Processado em: 2026-05-23

## Overview

10 artigos coletados via Brave Search API sobre dois tópicos:
1. Contract Driven Development (CDC) with AI Agents
2. AI-Friendly Architecture

---

## Tópico 7: CDC with AI Agents

### State of the Art

CDC com AI agents é **área emergente** — literatura fragmentada, quase tudo é experiência prática ou blog posts. Não há livro branco consolidado ainda.

### Frameworks/Tools consolidados

| Tool | O que faz | Relevância |
|------|----------|------------|
| **PactFlow** | Contract testing commercial com MCP server | AI agents podem verificar contracts via IDE |
| **SmartBear MCP** | `contract-testing_*` tools expostas para AI | Gera/revisa/maintains Pact tests automaticamente |
| **Signadot SmartTests** | "Smart Diff" — AI compara baseline vs new responses | Distingue breaking changes reais de ruído |
| **MCP** | Schema-validated messages entre agents | Reduz misinterpretation em multi-agent |

### Problema central (o que você pode abordar)

O **"stale snapshot problem"**: quando múltiplos AI agents modify services simultaneamente, Agent B pode estar working com snapshot desatualizada do schema do serviço que Agent A acabou de mudar.

### Artigos específicos para ler

1. **"How LLMs Are Breaking the API Contract"** — Nordic APIs
   - URL: https://nordicapis.com/how-llms-are-breaking-the-api-contract-and-why-that-matters/
   - Foco: LLMs quebram contratos durante code generation; riscos segurança/governança

2. **"Multi-agent workflows often fail"** — GitHub Blog
   - URL: https://github.blog/ai-and-ml/generative-ai/multi-agent-workflows-often-fail-heres-how-to-engineer-ones-that-dont/
   - Foco: Tratar schema violations como contract failures, retry/repair antes de propagar

3. **"Agent Contracts: A Formal Framework"** — arXiv
   - URL: https://arxiv.org/html/2601.08815v1
   - Foco: Framework formal com limites de recurso; denso mas authoritative

4. **"Data Contracts for Agents"** — Medium
   - URL: https://medium.com/@deolesopan/data-contracts-for-agents-keep-tools-and-schemas-stable-as-systems-evolve-8af6f3e024ba
   - Foco: Breaking changes = new major version; duas versões ativas durante migration

### Conceitos-chave para o artigo

- **Schema-first validation** em todo boundary
- **Breaking changes requerem nova versão major**
- **Feedback loops** — AI agent precisa saber quando quebrou contrato
- **CDC + AI = PactFlow MCP Server** — caso de uso concreto

---

## Tópico 10: AI-Friendly Architecture

### Framework dominante: Vertical Slice Architecture (VSA)

VSA emerge como consenso entre múltiplas fontes como a arquitetura mais AI-friendly.

**Por que funciona para AI:**
- Context completo de cada feature em um lugar
- Não precisa navegar entre camadas (controllers/services/repositories)
- Feature changes são autocontidas
- AI infere onde colocar novo código com menos ambiguidade

**Trade-off:** duplicação controlada de código (acceptable para AI readability)

### Artigos específicos para ler

1. **"AI-Ready Codebase Guide 2025"** — LLMx
   - URL: https://llmx.tech/blog/ai-ready-codebase-claude-cursor-integration-guide/
   - Foco: Templates CLAUDE.md, VSA, 80% melhoria em AI code generation

2. **"Keep the AI Vibe"** — Rick Hightower (Medium)
   - URL: https://medium.com/@richardhightower/ai-optimizing-codebase-architecture-for-ai-coding-tools-ff6bb6fdc497
   - Foco: Comparação de arquiteturas para AI coding tools

3. **"Coding Guidelines for Your AI Agents"** — JetBrains IDEA Blog
   - URL: https://blog.jetbrains.com/idea/2025/05/coding-guidelines-for-your-ai-agents/
   - Foco: Criar guidelines.md documentando convenções do projeto

4. **"A Deeper Dive When the Vibe Dies"** — Cloudurable
   - URL: https://cloudurable.com/blog/a-deeper-dive-when-the-vibe-dies-comparing-codebase-architectures-for-ai-tools/
   - Foco: VSA vs Atomic Composable vs Pipeline — trade-offs detalhados

5. **"Vertical Slice Architecture for Claude Code"** — Vladyslav Furdak
   - URL: https://www.furdak.net/articles/dotnet-vsa-webapi-skill
   - Foco: Skill prático para aplicar VSA com Claude Code em .NET

### 5 Patterns de AI-Friendly Codebases

1. **Explicit over Implicit** — DI explícito, funções puras, sem side effects ocultos
2. **Flat over Nested** — estrutura rasa com nomes descritivos > pastas profundas crípticas
3. **Tests as Documentation** — AI usa tests como source of truth; nome de teste = intent
4. **Bounded Contexts Claros** — fronteiras bem definidas = AI faz reasoning sem contexto extra
5. **Types Explícitos** — TypeScript/Python com types forts; evitar `any`

### Para aplicar no Invaice

1. Criar `CLAUDE.md` na root do projeto com convenções do Invaice (stack NestJS+Vue)
2. Considerar Vertical Slice ao organizar módulos do backend
3. Adicionar types explícitos (já é TypeScript — usar com rigor)
4. Documentar API contracts com schemas (OpenAPI/JSON Schema)

---

## Conclusão

**CDC com AI agents** é área quente com material esparso — oportunidade para Eduardo ser early voice se tiver experiência prática com multi-agent.

**AI-Friendly Architecture** está mais consolidado, especialmente VSA como padrão recommended.

**Próximo passo sugerido:** outline de artigo para um dos dois tópicos, com ângulo técnico específico.