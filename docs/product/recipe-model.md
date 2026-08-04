# Recipe Schema

## Objetivo

Este documento define a estrutura oficial de uma receita utilizada pelo Chef.IA.

Toda receita gerada pela Inteligência Artificial, armazenada localmente ou manipulada pela aplicação deve seguir exatamente esta estrutura.

Este documento representa a fonte de verdade do domínio de receitas.

---

# Estrutura

Uma receita é composta pelos seguintes campos.

| Campo       | Tipo         | Obrigatório |
| ----------- | ------------ | ----------- |
| title       | string       | Sim         |
| servings    | number       | Sim         |
| ingredients | Ingredient[] | Sim         |
| steps       | RecipeStep[] | Sim         |

---

# Receita

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

---

## Ingredient

Cada ingrediente possui os seguintes campos.

| Campo    | Tipo   | Obrigatório |
| -------- | ------ | ----------- |
| name     | string | Sim         |
| quantity | number | Sim         |
| unit     | string | Sim         |

---

### name

Nome do ingrediente.

Exemplos:

- Farinha de trigo
- Leite
- Açúcar

---

### quantity

Quantidade utilizada.

Exemplos:

- 1
- 2
- 0.5

Deve aceitar valores decimais.

---

### unit

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

Não haverá enumeração fixa no MVP.

---

# steps

Lista ordenada contendo todas as etapas de preparo.

A ordem da lista representa a ordem de execução.

---

## RecipeStep

Cada etapa possui os seguintes campos.

| Campo       | Tipo   | Obrigatório |
| ----------- | ------ | ----------- |
| description | string | Sim         |

---

### description

Descrição detalhada da etapa.

Exemplo:

"Em uma tigela grande, misture a farinha, o açúcar e o fermento."

A descrição deve ser suficientemente clara para permitir que um usuário iniciante consiga executar a receita.

---

# Ordem dos Dados

A ordem das listas deve ser preservada.

Alterações na ordem representam mudanças na receita.

---

# Restrições

Toda receita deve possuir:

- pelo menos um ingrediente;
- pelo menos uma etapa de preparo.

Não são permitidos:

- ingredientes sem nome;
- etapas vazias;
- quantidade negativa;
- quantidade igual a zero.

---

# Fora do Escopo do MVP

Os seguintes campos poderão ser adicionados futuramente:

- id
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
