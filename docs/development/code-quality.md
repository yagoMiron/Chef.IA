# Code Quality Guidelines

## Objetivo

Definir padrões de qualidade para manter o código sustentável durante desenvolvimento assistido por Inteligência Artificial.

---

# TypeScript

Obrigatório:

- TypeScript strict;
- tipos explícitos;
- evitar `any`;
- evitar casts desnecessários.

Não utilizar:

```ts
any;
```

sem justificativa documentada.

---

# Arquitetura

O código deve respeitar a separação:

```
Presentation
    ↓
Application
    ↓
Domain
    ↓
Infrastructure
```

Cada camada possui responsabilidades próprias.

---

# DRY

Duplicação de código deve ser evitada.

Antes de criar uma nova função, componente ou serviço:

- procurar implementações existentes;
- reutilizar quando possível;
- abstrair apenas quando existir necessidade real.

---

# SOLID

O código deve seguir princípios SOLID.

Especialmente:

## Single Responsibility

Cada módulo deve possuir uma responsabilidade clara.

## Dependency Inversion

Regras de negócio não devem depender de implementações externas.

---

# Componentes React

Componentes devem:

- possuir responsabilidade única;
- evitar lógica de negócio;
- receber dados via props quando possível.

Componentes grandes devem ser divididos.

---

# Hooks

Hooks devem:

- encapsular lógica reutilizável;
- evitar acesso direto a APIs externas;
- evitar conter regras de domínio.

---

# Services

Serviços devem encapsular:

- integrações externas;
- comunicação com providers;
- operações de infraestrutura.

---

# Refatorações

A IA nunca deve realizar grandes refatorações automaticamente.

Antes de uma refatoração estrutural:

- explicar o problema;
- apresentar proposta;
- aguardar aprovação.

---

# Dependências

Nenhuma biblioteca nova deve ser instalada sem aprovação.

A IA deve justificar:

- necessidade;
- alternativas;
- impacto.

---

# Documentação

Decisões arquiteturais devem ser registradas em:

`docs/decisions/`

A documentação possui prioridade sobre sugestões automáticas da IA.
