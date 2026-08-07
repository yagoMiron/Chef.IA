# ADR-007 - Validation Strategy

## Status

Accepted

---

## Context

A aplicação recebe dados de diversas origens.

Entre elas:

- usuário;
- armazenamento;
- Inteligência Artificial.

Nenhuma dessas fontes deve ser considerada confiável.

---

## Decision

Toda validação será realizada utilizando Zod.

Cada entidade do domínio deverá possuir seu próprio Schema.

Dados inválidos nunca deverão alcançar a camada de domínio.

Respostas produzidas pela IA deverão ser validadas antes de qualquer processamento.

Schemas Zod validam dados de entrada.

Regras de negócio pertencem ao domínio e não devem ser substituídas por validações Zod.

---

## Objetivos

- garantir integridade dos dados;
- reduzir erros em tempo de execução;
- facilitar manutenção.

---

## Consequences

Existe um pequeno custo adicional de validação.

Em contrapartida, a aplicação torna-se significativamente mais segura e previsível.
