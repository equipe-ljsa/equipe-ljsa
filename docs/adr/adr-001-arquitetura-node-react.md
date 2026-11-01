# ADR-001 — Adoção do template Node.js + React

## Status
Aceito.

## Contexto
O projeto Connexa precisa de uma base para desenvolver funcionalidades
com testes de aceitação, integração contínua e rastreabilidade entre
Azure Boards, commits e pull requests.

Na preparação do ambiente, buscamos aproveitar a infraestrutura
fornecida pela disciplina, evitando montar o projeto do zero.

## Decisão
Adotar o template `connexa-modelo-node`, com a arquitetura de monolito
modular com fatias verticais no back-end e SPA no front-end.

A stack adotada é:
- Back-end: Node.js 24, TypeScript e NestJS.
- Persistência: PostgreSQL 17 e Prisma, com Prisma Migrate.
- Front-end: React 19, TypeScript e Vite.
- Testes: Vitest e Supertest para aceitação na API;
  Vitest e Testing Library no front-end.
- Integração contínua: GitHub Actions.
- Ambiente de desenvolvimento: GitHub Codespaces.
- Integração do agente com Azure Boards: MCP.

## Justificativa
O template já fornece a estrutura modular, banco de dados,
migrações, testes, verificações de fronteiras, CI e configurações
de conexão do agente com o Azure Boards.

Reutilizar essa infraestrutura reduz o trabalho de preparação
e mantém o projeto alinhado ao roteiro da disciplina.

## Consequências
- Respeitar as fronteiras e APIs públicas dos módulos.
- Criar alterações no banco por migrações do Prisma.
- Manter AGENTS.md e .github/copilot-instructions.md idênticos.
- Executar ./verificar para conferir o projeto.
- Integrar alterações no main somente por pull requests
  revisados e com CI verde.
- Manter a autenticação real fora da Sprint 1,
  utilizando o estudante simulado fornecido pelo template.
