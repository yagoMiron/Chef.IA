# Estrutura do Projeto

## Visão Geral

```
src/
├── app/
├── components/
├── hooks/
├── services/
├── lib/
├── types/
├── schemas/
├── store/
├── utils/
├── tests/
└── assets/
```

---

## app/

Contém apenas:

- páginas
- layouts
- loading
- error
- templates

Não deve conter regra de negócio.

---

## components/

Componentes reutilizáveis.

Não devem conhecer regras de negócio.

Sempre que possível devem receber dados via props.

---

## hooks/

Hooks React reutilizáveis.

Nunca conter lógica de persistência.

Nunca realizar chamadas diretas para APIs.

---

## services/

Serviços da aplicação.

Responsável por:

- IA
- armazenamento
- APIs futuras

Toda comunicação externa passa por esta pasta.

---

## lib/

Bibliotecas e abstrações compartilhadas.

Exemplos:

- IndexedDB
- utilitários de autenticação
- configuração de providers

---

## schemas/

Schemas do Zod.

Toda validação da aplicação deve estar aqui.

---

## store/

Estado global da aplicação.

Não colocar regras de negócio complexas.

---

## types/

Tipos compartilhados.

Evitar duplicação de interfaces.

---

## utils/

Funções utilitárias puras.

Não acessar banco.

Não acessar APIs.

Sem efeitos colaterais.

---

## tests/

Infraestrutura de testes.

Organizar por tipo:

- unit
- integration
- e2e
