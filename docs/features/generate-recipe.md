# F001 - Gerar Receita

## Objetivo

Permitir que o usuário gere uma nova receita utilizando Inteligência Artificial a partir de uma descrição em linguagem natural.

---

## Fluxo

1. O usuário acessa a tela "Nova Receita".
2. O usuário descreve a receita desejada.
3. O sistema reúne o contexto disponível:
   - descrição fornecida;
   - ingredientes da geladeira;
   - preferências alimentares.
4. O sistema envia a solicitação para a IA.
5. A IA retorna uma receita estruturada.
6. O usuário visualiza o resultado.
7. O usuário pode:
   - salvar;
   - descartar;
   - gerar novamente.

---

## Regras

- A receita nunca deve ser salva automaticamente.
- A IA deve retornar uma estrutura compatível com o modelo definido pelo sistema.
- Caso a resposta seja inválida, o sistema deve informar o erro ao usuário.
- O usuário poderá editar qualquer informação antes de salvar.

---

## Critérios de Aceitação

- O usuário consegue gerar uma receita.
- O usuário consegue visualizar a receita antes de salvar.
- O usuário consegue descartar a geração.
