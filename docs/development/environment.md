# Development Environment

## Objetivo

Este documento define o ambiente oficial de desenvolvimento do Chef.IA.

Todos os desenvolvedores e ferramentas de Inteligência Artificial devem seguir estas definições.

---

# Runtime

## Node.js

Versão utilizada:
`Node.js v24.19.0`

A versão do Node.js deve ser mantida compatível com a versão definida neste documento.

---

# Package Manager

O projeto utiliza pnpm.

Não utilizar:

- npm;
- yarn;
- bun;

para instalação de dependências.

Comandos oficiais:

```bash
pnpm install
pnpm dev
pnpm build
pnpm lint
pnpm test
```

---

# Framework

O projeto utiliza:

- Next.js;
- App Router;
- React;
- TypeScript.

A estrutura deve seguir as convenções modernas do Next.js.

---

# TypeScript

Configuração obrigatória:

- strict mode habilitado;
- evitar `any`;
- tipos explícitos quando necessário;
- interfaces e tipos compartilhados devem permanecer centralizados.

---

# Code Formatting

Ferramenta:

- Prettier

Todos os arquivos devem seguir a formatação definida pelo projeto.

A IA não deve alterar regras de formatação sem autorização.

---

# Linting

Ferramenta:

- ESLint

O ESLint deve ser executado antes de alterações importantes.

Problemas identificados pelo ESLint devem ser corrigidos antes da finalização de uma tarefa.

---

# Environment Variables

Variáveis sensíveis nunca devem ser commitadas.

Arquivos `.env` devem permanecer fora do controle de versão.

Exemplo:

`.env.local`

---

# Scripts Obrigatórios

O projeto deve possuir scripts para:

---

## Desenvolvimento

`pnpm dev`

Inicia o ambiente local.

---

# Build

`pnpm build`

Valida se a aplicação pode ser compilada.

---

# Lint

`pnpm lint`

Executa análise estática.

---

# Testes

`pnpm test`

Executa testes automatizados.

---

# Dependências

A instalação de novas bibliotecas exige aprovação prévia.

Antes de adicionar uma dependência, deve ser documentado:

- problema resolvido;
- alternativas avaliadas;
- impacto no projeto.
