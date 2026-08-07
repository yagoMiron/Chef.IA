# ADR-006 - AI Provider Strategy

## Status

Accepted

---

## Context

O Chef.IA depende de modelos de Inteligência Artificial para funcionalidades como:

- geração de receitas;
- modificação de receitas;
- conversas relacionadas a receitas;
- sugestões culinárias.

O projeto não deve possuir acoplamento direto com um único modelo ou fornecedor de IA.

A troca de fornecedor ou modelo deve exigir o mínimo possível de alterações na aplicação.

---

## Decision

Toda comunicação com modelos de Inteligência Artificial deverá ocorrer através de uma camada de abstração de provedor de IA.

A aplicação não deve depender diretamente de SDKs ou APIs específicas de fornecedores dentro das regras de negócio.

Arquitetura esperada:

```
Application
|
↓
AI Provider Interface
|
↓
AI Provider Implementation
|
↓
OpenRouter
```

---

## MVP Provider

No MVP, o provedor utilizado será o OpenRouter.

O OpenRouter será responsável por intermediar acesso a diferentes modelos de linguagem.

A escolha do modelo específico poderá evoluir futuramente sem alterar a arquitetura da aplicação.

---

## API Key Strategy

No MVP, o usuário será responsável por fornecer sua própria chave de API.

A chave:

- pertence ao usuário;
- não será armazenada em servidores da aplicação;
- será armazenada somente localmente no dispositivo do usuário;
- poderá ser removida pelo usuário a qualquer momento.

Nenhum dado sensível do usuário deverá ser enviado para servidores próprios.

---

## Provider Independence

A aplicação deve permitir futuramente a criação de novos providers.

Exemplos:

- OpenAI;
- Google Gemini;
- Anthropic;
- outros fornecedores compatíveis.

A inclusão de um novo provider não deve exigir alterações nos casos de uso ou nas regras de negócio.

---

## Prompt Management

Prompts utilizados pela aplicação devem permanecer separados da lógica de negócio.

A construção de prompts deve ser realizada através de uma camada própria responsável por:

- composição de contexto;
- formatação das mensagens;
- definição das instruções para o modelo;
- controle de versões futuras de prompts.

---

## Consequences

### Positivas

- menor acoplamento com fornecedores;
- facilidade para trocar modelos;
- possibilidade de utilizar modelos diferentes conforme custo e qualidade;
- melhor organização do código.

### Negativas

- maior complexidade inicial;
- necessidade de criar abstrações antes de utilizar a IA diretamente.

---

## Alternatives Considered

### Acesso direto ao fornecedor

Exemplo:

```
Use Case
|
↓
OpenRouter SDK
```

Não escolhido.

Motivo:

- cria acoplamento;
- dificulta troca de fornecedor;
- mistura regra de negócio com infraestrutura.

---

### Backend próprio intermediando IA

Exemplo:

```
Frontend
|
↓
Backend
|
↓
AI Provider
```

Não utilizado no MVP.

Pode ser adotado futuramente quando existirem:

- usuários autenticados;
- cobrança por uso;
- controle de custos;
- necessidade de proteção de chaves.
