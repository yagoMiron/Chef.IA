# ADR-009 - IndexedDB Library

## Status

Accepted

---

## Context

O MVP do Chef.IA funcionará localmente no dispositivo do usuário.

A aplicação precisa armazenar:

- receitas;
- chats;
- preferências alimentares;
- informações da geladeira.

A persistência deve permitir uma futura migração para backend remoto sem alterar regras de negócio.

---

## Decision

O armazenamento local será implementado utilizando IndexedDB.

A aplicação utilizará Dexie como abstração sobre IndexedDB.

Nenhum Use Case poderá acessar diretamente IndexedDB.

Toda persistência deverá ocorrer através de repositories.

---

## Architecture

Fluxo:

Application
|
↓
Repository Interface
|
↓
Dexie Implementation
|
↓
IndexedDB

---

## Reasons

Dexie foi escolhido por:

- possuir suporte maduro a IndexedDB;
- possuir integração com TypeScript;
- reduzir complexidade da API nativa;
- facilitar manutenção.

---

## Consequences

### Positivas

- menor quantidade de código de infraestrutura;
- melhor experiência de desenvolvimento;
- tipagem mais segura;
- fácil substituição futura por outro armazenamento.

### Negativas

- dependência adicional;
- necessidade de aprender uma abstração externa.

---

## Alternatives Considered

### IndexedDB API nativa

Não escolhido.

Motivo:

- maior complexidade;
- maior quantidade de código;
- menor produtividade.

---

### Outros wrappers IndexedDB

Não escolhidos neste momento.
