# F007 - Construção de Contexto para IA

## Objetivo

Centralizar a construção do contexto enviado para qualquer modelo de IA utilizado pela aplicação.

---

## Contexto enviado

Sempre que possível, o sistema deve enviar:

- solicitação do usuário;
- preferências alimentares;
- informações da geladeira;
- receita atual (quando existir);
- histórico do chat (quando existir).

---

## Responsabilidades

O sistema é responsável por construir o contexto.

As telas nunca devem montar prompts diretamente.

Toda comunicação com a IA deve utilizar este mecanismo.

---

## Regras

O formato do contexto deve ser consistente em toda a aplicação.

Mudanças no formato devem ocorrer em apenas um local do código.

---

## Critérios de Aceitação

Todas as funcionalidades que utilizam IA reutilizam o mesmo mecanismo de construção de contexto.
