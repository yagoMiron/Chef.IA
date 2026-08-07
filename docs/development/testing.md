# Testing Strategy Implementation

## Objetivo

Este documento define como os testes automatizados devem ser implementados no Chef.IA.

A estratégia principal é garantir segurança durante evolução rápida utilizando Inteligência Artificial.

---

# Princípios

Todo código deve ser desenvolvido considerando testes.

Correções de bugs devem gerar testes de regressão quando aplicável.

Novas funcionalidades devem possuir testes cobrindo seus comportamentos esperados.

---

# Tipos de Teste

O projeto utiliza três níveis:

- Unitários;
- Integração;
- End-to-End.

---

# Testes Unitários

Ferramenta:

- Vitest

Utilizados para:

- regras de domínio;
- funções puras;
- validações;
- casos de uso isolados.

Exemplos:

- validação de receita;
- cálculo de valores;
- transformação de dados.

---

# Testes de Integração

Utilizados para validar comunicação entre camadas.

Exemplos:

- Use Case + Repository;
- Application + Infrastructure;
- validação de persistência local.

---

# Testes End-to-End

Ferramenta:

- Playwright

Utilizados para validar fluxos completos do usuário.

Exemplos:

- criar receita;
- editar receita;
- conversar com IA;
- salvar preferências.

---

# Organização

Os testes devem ser organizados por tipo:

tests/
├── unit/
├── integration/
└── e2e/

---

# Cobertura

A métrica de cobertura não deve ser utilizada isoladamente como indicador de qualidade.

A prioridade é:

1. Regras de negócio;
2. Casos de uso;
3. Fluxos críticos;
4. Integrações importantes.

---

# Regras para IA

A IA deve:

- criar testes junto com novas funcionalidades;
- criar testes de regressão para bugs corrigidos;
- não remover testes existentes sem justificativa;
- não reduzir cobertura para facilitar implementação.
