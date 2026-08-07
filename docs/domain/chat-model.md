# Chat Model

## Objetivo

Este documento define a estrutura oficial dos chats utilizados pelo Chef.IA.

Um chat representa uma conversa entre o usuário e a Inteligência Artificial relacionada a uma receita específica.

O chat existe para manter contexto durante interações relacionadas a uma receita.

Este documento representa a fonte de verdade do domínio de conversas.

---

# Estrutura

Um chat possui os seguintes campos:

| Campo    | Tipo      | Obrigatório |
| -------- | --------- | ----------- |
| id       | string    | Sim         |
| recipeId | string    | Sim         |
| messages | Message[] | Sim         |

---

# Chat

## id

Identificador único do chat.

O ID deve ser uma string única gerada pela aplicação utilizando UUID.

O ID não deve ser alterado durante o ciclo de vida do chat.

---

## recipeId

Identificador da receita associada ao chat.

Cada chat pertence a exatamente uma receita.

A receita é responsável por fornecer o contexto principal utilizado pela Inteligência Artificial durante a conversa.

---

## messages

Lista ordenada contendo todas as mensagens da conversa.

A ordem das mensagens representa a sequência cronológica da interação.

Novas mensagens devem ser adicionadas ao final da lista.

---

# Message

Cada mensagem possui os seguintes campos:

| Campo     | Tipo        | Obrigatório |
| --------- | ----------- | ----------- |
| id        | string      | Sim         |
| role      | MessageRole | Sim         |
| content   | string      | Sim         |
| createdAt | string      | Sim         |

---

# MessageRole

O campo `role` representa quem enviou a mensagem.

Valores possíveis no MVP:

```text
user
assistant
```

---

## user

Mensagem enviada pelo usuário.

Exemplos:

- "Posso substituir o leite por creme de leite?"
- "Como posso deixar essa receita mais barata?"

---

## assistant

Mensagem gerada pela Inteligência Artificial.

Exemplos:

- Respostas;
- Explicações;
- Sugestões;
- Modificações solicitadas pelo usuário.

---

# content

Texto da mensagem.

Não deve ser vazio.

No MVP as mensagens serão exclusivamente texto.

Mensagens com imagens, arquivos ou outros tipos de conteúdo estão fora do escopo.

---

# createdAt

Data e hora de criação da mensagem.

Deve ser armazenada em formato compatível com ISO 8601.

Exemplo:

```text
2026-08-07T15:00:00.000Z
```

---

# Relacionamento com Recipe

O relacionamento entre Recipe e Chat é:

```text
Recipe 1 ───── 1 Chat
```

Uma receita possui no máximo um chat associado.

O chat possui uma referência para a receita através de `recipeId`.

---

# Restrições

Todo chat deve possuir:

- um ID único;
- uma receita associada;
- uma lista de mensagens válida.

Toda mensagem deve possuir:

- um ID único;
- um remetente válido;
- conteúdo não vazio;
- data de criação.

---

# Fora do Escopo do MVP

Os seguintes recursos poderão ser adicionados futuramente:

- múltiplos chats por receita;
- títulos de conversa;
- mensagens com imagens;
- mensagens com áudio;
- anexos;
- exclusão individual de mensagens;
- busca no histórico;
- resumo automático de conversas;
- limite inteligente de contexto para modelos de IA;
- compartilhamento de conversas;
- histórico de versões do chat.
