# ADR-005 - Persistence Strategy

## Status

Accepted

---

## Context

O MVP funcionará completamente offline.

No futuro a aplicação possuirá autenticação e sincronização entre dispositivos.

A arquitetura deve permitir essa evolução sem alterações significativas na regra de negócio.

---

## Decision

O domínio da aplicação nunca deve conhecer a tecnologia utilizada para persistência.

Toda persistência ocorrerá através de Repositories.

No MVP será utilizado IndexedDB.

Em versões futuras, a persistência será migrada para PostgreSQL sem alterar o domínio da aplicação.

---

## Repositories

Toda leitura e escrita de dados deverá ocorrer através de interfaces.

Nenhum Use Case poderá acessar diretamente IndexedDB.

---

## Consequences

A implementação inicial exige maior abstração.

Entretanto, futuras migrações de banco tornam-se significativamente mais simples.
