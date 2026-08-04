# ADR-006 - AI Provider

## Status

Accepted

---

## Context

O Chef.IA depende de um Large Language Model para geração e modificação de receitas.

O projeto não deve depender de um único fornecedor de IA.

---

## Decision

Toda comunicação com modelos de IA será realizada através do OpenRouter.

O usuário fornecerá sua própria chave de API.

O sistema nunca armazenará essa chave em servidores.

Toda comunicação ocorrerá diretamente entre a aplicação e o provedor escolhido.

---

## Objetivos

- independência de fornecedor;
- facilidade para trocar modelos;
- menor custo;
- suporte a múltiplos modelos.

---

## Consequences

Novos modelos poderão ser utilizados sem alterar a arquitetura da aplicação.
