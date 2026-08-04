# API

## Objetivo

Este documento define a interface pública do backend do Chef.IA.

A API representa os casos de uso da aplicação.

A implementação poderá utilizar REST, Server Actions, tRPC ou outra tecnologia, desde que mantenha as mesmas responsabilidades.

---

# Recursos

O sistema possui os seguintes recursos principais.

- Recipes
- Recipe Chat
- Pantry
- User Preferences
- AI

---

# Recipes

## Listar Receitas

GET /recipes

Retorna todas as receitas cadastradas.

---

## Buscar Receita

GET /recipes/{recipeId}

Retorna uma receita específica.

Caso a receita não exista, retornar erro de recurso não encontrado.

---

## Criar Receita

POST /recipes

Cria uma nova receita.

O corpo da requisição deve seguir o Recipe Model.

---

## Atualizar Receita

PUT /recipes/{recipeId}

Substitui completamente uma receita existente.

---

## Atualização Parcial

PATCH /recipes/{recipeId}

Atualiza apenas os campos enviados.

---

## Excluir Receita

DELETE /recipes/{recipeId}

Remove permanentemente uma receita.

---

# Recipe Chat

## Obter Conversa

GET /recipes/{recipeId}/chat

Retorna o histórico completo da conversa.

---

## Enviar Mensagem

POST /recipes/{recipeId}/chat/messages

Envia uma mensagem para a IA.

O sistema deverá:

- recuperar a receita;
- recuperar Pantry;
- recuperar User Preferences;
- recuperar o histórico da conversa;
- construir o contexto;
- consultar a IA;
- salvar a resposta.

Retorna a resposta gerada pela IA.

---

## Limpar Conversa

DELETE /recipes/{recipeId}/chat

Remove todas as mensagens da conversa.

A receita permanece inalterada.

---

# Pantry

## Consultar

GET /pantry

Retorna o conteúdo atual.

---

## Atualizar

PUT /pantry

Substitui completamente o conteúdo.

---

# User Preferences

## Consultar

GET /preferences

Retorna as preferências atuais.

---

## Atualizar

PUT /preferences

Atualiza completamente as preferências.

---

# Inteligência Artificial

## Gerar Receita

POST /ai/generate-recipe

Entrada:

- descrição do usuário

O sistema deverá:

- recuperar Pantry;
- recuperar User Preferences;
- construir o contexto;
- consultar a IA;
- validar a resposta.

A receita gerada não deve ser salva automaticamente.

---

## Modificar Receita

POST /ai/modify-recipe

Entrada:

- recipeId
- instrução

O sistema deverá:

- recuperar a receita;
- recuperar Pantry;
- recuperar User Preferences;
- construir o contexto;
- consultar a IA;
- validar a resposta.

A receita modificada não deve ser salva automaticamente.

---

# Validação

Toda entrada deve ser validada.

Dados inválidos nunca devem chegar à camada de domínio.

---

# Tratamento de Erros

Toda operação deve retornar erros consistentes.

Os erros devem conter:

- código;
- mensagem;
- detalhes quando aplicável.

Nunca retornar mensagens internas da aplicação.

---

# Autenticação

Não existe autenticação no MVP.

Todas as operações assumem um único usuário local.

---

# Persistência

No MVP toda persistência será local.

A API não deve depender da tecnologia de armazenamento.

A troca de IndexedDB por um banco remoto não deve alterar a interface pública da aplicação.
