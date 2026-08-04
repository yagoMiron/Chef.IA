# Chef.IA

## Objetivo

Chef.IA é uma aplicação Web Fullstack PWA que funciona como um assistente culinário inteligente.

O objetivo é permitir que o usuário mantenha um livro de receitas vivo, utilizando Inteligência Artificial para criar receitas, modificá-las, tirar dúvidas e adaptar o conteúdo às suas preferências alimentares.

A IA deve atuar como um assistente, enquanto o usuário mantém total controle sobre seus dados.

---

## Público-alvo

Pessoas que gostam de cozinhar e desejam organizar receitas de forma inteligente.

---

## MVP

A primeira versão deve ser totalmente local.

Não haverá autenticação nem backend remoto.

Todos os dados serão armazenados no dispositivo do usuário.

---

## Funcionalidades

### Gerar Receita

O usuário descreve a receita desejada.

A IA gera uma receita estruturada seguindo um JSON pré-defabelecido.

Após confirmação, a receita é salva.

---

### Livro de Receitas

CRUD completo de receitas.

Cada receita pode ser:

- visualizada
- editada manualmente
- modificada pela IA

---

### Chat da Receita

Cada receita possui um chat próprio.

A IA responde utilizando:

- conteúdo da receita
- preferências do usuário
- informações da geladeira

---

### Minha Geladeira

O usuário informa ingredientes disponíveis.

Esse contexto deve ser utilizado pela IA.

---

### Preferências Alimentares

O usuário informa:

- restrições
- ingredientes indesejados
- preferências alimentares

Essas informações fazem parte do contexto enviado à IA.

---

## Fora do escopo do MVP

- Login
- Sincronização em nuvem
- Compartilhamento de receitas
- Geração de imagens
- Upload de imagens
