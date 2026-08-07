# Recipe Schema

## Objetivo

Este documento define a estrutura oficial de uma receita utilizada pelo Chef.IA.

Toda receita gerada pela Inteligência Artificial, armazenada localmente ou manipulada pela aplicação deve seguir esta estrutura.

Este documento representa a fonte de verdade do domínio de receitas.

---

# Estrutura

Uma receita possui os seguintes campos:

| Campo       | Tipo         | Obrigatório |
| ----------- | ------------ | ----------- |
| id          | string       | Sim         |
| title       | string       | Sim         |
| servings    | number       | Sim         |
| ingredients | Ingredient[] | Sim         |
| steps       | RecipeStep[] | Sim         |

---

# Receita

## id

Identificador único da receita.

O ID deve ser uma string única gerada pela aplicação.

O MVP utilizará UUID como estratégia de geração de identificadores.

O ID é utilizado para:

- identificar uma receita de forma única;
- persistir a receita;
- recuperar uma receita específica;
- relacionar a receita ao seu chat.

O ID não deve ser alterado durante o ciclo de vida da receita.

---

## title

Nome da receita.

Exemplos:

- Lasanha à Bolonhesa
- Pizza Margherita
- Torta de Frango

Não deve ser vazio.

---

## servings

Quantidade aproximada de porções produzidas pela receita.

Exemplos:

- 2
- 4
- 8

O valor deve ser um número inteiro maior que zero.

---

## ingredients

Lista de ingredientes necessários para preparar a receita.

A ordem dos ingredientes deve respeitar a ordem natural de leitura da receita.

Uma receita deve possuir pelo menos um ingrediente.

---

# Ingredient

Cada ingrediente possui os seguintes campos:

| Campo    | Tipo   | Obrigatório |
| -------- | ------ | ----------- |
| name     | string | Sim         |
| quantity | number | Sim         |
| unit     | string | Sim         |

---

## name

Nome do ingrediente.

Exemplos:

- Farinha de trigo
- Leite
- Açúcar

Não deve ser vazio.

---

## quantity

Quantidade utilizada.

Exemplos:

- 1
- 2
- 0.5

Deve aceitar valores decimais.

Deve ser maior que zero.

---

## unit

Unidade de medida.

Exemplos:

- g
- kg
- ml
- L
- colher de sopa
- colher de chá
- xícara
- unidade
- pitada

A unidade deve ser armazenada como texto.

Não haverá enumeração fixa de unidades no MVP.

---

# steps

Lista ordenada contendo todas as etapas de preparo.

A ordem da lista representa a ordem de execução.

Uma receita deve possuir pelo menos uma etapa de preparo.

---

# RecipeStep

Cada etapa possui os seguintes campos:

| Campo       | Tipo   | Obrigatório |
| ----------- | ------ | ----------- |
| name        | string | Sim         |
| description | string | Sim         |

---

## name

Nome curto que identifica a etapa.

Exemplos:

- Preparar os ingredientes
- Fazer a massa
- Preparar o recheio
- Montar a receita
- Assar

Não deve ser vazio.

---

## description

Descrição detalhada da etapa.

Exemplo:

"Em uma tigela grande, misture a farinha, o açúcar e o fermento."

A descrição deve ser suficientemente clara para permitir que um usuário iniciante consiga executar a receita.

Não deve ser vazia.

---

# Ordem dos Dados

A ordem das listas deve ser preservada.

A ordem dos ingredientes representa a ordem natural de apresentação dos ingredientes.

A ordem dos passos representa a ordem de execução da receita.

Alterações nessas ordens representam mudanças na receita.

---

# Restrições

Toda receita deve possuir:

- um ID único;
- título não vazio;
- número de porções inteiro maior que zero;
- pelo menos um ingrediente;
- pelo menos uma etapa de preparo.

Todo ingrediente deve possuir:

- nome não vazio;
- quantidade maior que zero;
- unidade não vazia.

Toda etapa deve possuir:

- nome não vazio;
- descrição não vazia.

Não são permitidos:

- ingredientes sem nome;
- etapas sem nome;
- etapas sem descrição;
- quantidade negativa;
- quantidade igual a zero;
- listas de ingredientes vazias;
- listas de etapas vazias.

---

# Fora do Escopo do MVP

Os seguintes campos poderão ser adicionados futuramente:

- description
- images
- tags
- difficulty
- preparationTime
- cookingTime
- totalTime
- nutrition
- category
- cuisine
- notes
- source
- rating
- favorite
- visibility
- createdAt
- updatedAt
- version
- aiMetadata

# Relacionamentos

Uma receita possui um chat associado.

O relacionamento é:

Recipe 1 ───── 1 Chat

A referência do relacionamento é mantida através do campo `Chat.recipeId`.

O modelo da receita não precisa armazenar diretamente o `chatId`.
