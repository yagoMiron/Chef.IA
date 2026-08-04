# Arquitetura

## Objetivos

- Alta legibilidade
- Baixo acoplamento
- Alta coesão
- Fácil manutenção
- Fácil evolução

---

## Princípios

- SOLID
- DRY
- KISS
- YAGNI
- Composition over Inheritance

---

## Organização

A aplicação deve separar claramente:

- Interface
- Regras de negócio
- Serviços
- Persistência
- Integrações externas

Nenhuma regra de negócio deve existir dentro de componentes React.

---

## IA

Toda comunicação com modelos de IA deve passar exclusivamente pelo AIService.

É proibido realizar chamadas diretas para APIs de IA fora desse serviço.

---

## Persistência

Todo acesso ao armazenamento deve ocorrer através de serviços próprios.

Componentes React nunca acessam IndexedDB diretamente.
