# Modelo de Domínio

## Objetivo

Este documento define os objetos de domínio do Chef.IA e suas responsabilidades.

O domínio representa as regras de negócio da aplicação, sendo independente da implementação do frontend, backend, banco de dados ou provedor de Inteligência Artificial.

Toda funcionalidade da aplicação deve ser construída a partir deste modelo.

---

# Visão Geral

O domínio do Chef.IA é composto pelos seguintes objetos.

```
Recipe
├── Ingredient
├── RecipeStep
└── RecipeChat
    └── Message

Pantry

UserPreferences
```

---

# Recipe

Representa uma receita cadastrada pelo usuário.

É a principal entidade da aplicação.

## Responsabilidades

- armazenar as informações da receita;
- permitir edição manual;
- permitir modificações por IA;
- servir como contexto para o chat.

## Relacionamentos

Uma receita possui:

- vários ingredientes;
- vários passos de preparo;
- um chat associado.

---

# Ingredient

Representa um ingrediente utilizado em uma receita.

Um ingrediente não possui existência própria.

Ele sempre pertence a uma única receita.

## Responsabilidades

- informar o ingrediente utilizado;
- informar quantidade;
- informar unidade de medida.

---

# RecipeStep

Representa uma etapa do preparo.

Cada etapa pertence exclusivamente a uma receita.

A ordem dos passos faz parte da receita.

## Responsabilidades

- descrever uma etapa do preparo;
- manter a sequência correta do preparo.

---

# RecipeChat

Representa a conversa entre o usuário e a Inteligência Artificial referente a uma receita.

Cada receita possui exatamente um chat.

## Responsabilidades

- armazenar o histórico da conversa;
- manter o contexto da conversa;
- fornecer contexto para novas perguntas.

---

# Message

Representa uma mensagem dentro de um chat.

Uma mensagem pode ter origem:

- usuário;
- inteligência artificial.

## Responsabilidades

- armazenar o histórico da conversa;
- preservar a ordem cronológica das mensagens.

---

# Pantry

Representa as informações sobre ingredientes disponíveis ao usuário.

Seu conteúdo é utilizado exclusivamente como contexto para a Inteligência Artificial.

Não representa controle de estoque.

O sistema não controla quantidades.

O usuário apenas informa livremente quais ingredientes costuma possuir.

## Responsabilidades

- armazenar ingredientes disponíveis;
- armazenar observações relevantes para geração de receitas.

---

# UserPreferences

Representa as preferências culinárias do usuário.

As informações são utilizadas apenas para personalizar o comportamento da IA.

## Exemplos

- evitar determinados ingredientes;
- receitas econômicas;
- receitas fitness;
- receitas italianas;
- reduzir uso de óleo.

## Responsabilidades

- armazenar preferências;
- fornecer contexto para geração e modificação de receitas.

---

# Relacionamentos

```
Recipe

├── Ingredient (1:N)

├── RecipeStep (1:N)

└── RecipeChat (1:1)

        └── Message (1:N)
```

Pantry e UserPreferences são independentes.

Ambos são utilizados como contexto para todas as interações com a IA.

---

# Objetos Persistidos

No MVP serão persistidos localmente:

- Recipe
- RecipeChat
- Pantry
- UserPreferences

Ingredient e RecipeStep são persistidos como parte da Recipe.

Message é persistida como parte do RecipeChat.

---

# Objetos Transitórios

Durante o funcionamento da aplicação poderão existir objetos temporários.

Exemplos:

- Prompt para IA;
- Resposta da IA;
- Contexto consolidado;
- Receita em geração.

Esses objetos não fazem parte do domínio persistido.

---

# Regras Gerais

Uma receita sempre possui:

- pelo menos um ingrediente;
- pelo menos um passo de preparo.

Toda receita pode ser editada manualmente.

Toda receita pode ser modificada pela IA.

Toda receita possui exatamente um chat.

Pantry e UserPreferences são globais para toda a aplicação.

---

# Fora do Escopo do MVP

Os seguintes objetos poderão ser adicionados futuramente:

- User
- Authentication
- RecipeVersion
- Category
- Tag
- ShoppingList
- Favorites
- Image
- Notification
- CloudSync
