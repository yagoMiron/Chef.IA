# Application Use Cases

## Objetivo

Este documento define os casos de uso principais da aplicação Chef.IA.

Um caso de uso representa uma ação que o usuário pode executar no sistema.

Os casos de uso pertencem à camada `application/` e não devem depender de detalhes de:

- interface;
- React;
- persistência;
- banco de dados;
- provedores específicos de Inteligência Artificial.

---

# Arquitetura do MVP

No MVP, a aplicação utiliza uma arquitetura local-first.

Fluxo principal:

```
User Interface
      |
      ↓
Application Use Case
      |
      ↓
Domain Rules
      |
      ↓
Infrastructure
      |
      ↓
Local Storage / External Services
```

Não existe uma API HTTP pública no MVP.

A comunicação entre frontend e aplicação ocorre através de chamadas diretas aos casos de uso.

---

# Generate Recipe

## Objetivo

Gerar uma nova receita utilizando Inteligência Artificial a partir de uma descrição fornecida pelo usuário.

---

## Entrada

```ts
{
  prompt: string;
}
```

Exemplo:

```text
"Torta de frango cremosa"
```

---

## Processo

O caso de uso deve:

1. receber a descrição do usuário;
2. coletar contexto relevante:
   - preferências alimentares;
   - informações da geladeira;
3. construir o prompt para o provedor de IA;
4. solicitar a geração da receita;
5. validar a resposta utilizando o schema da receita;
6. retornar uma receita válida.

---

## Saída

```ts
Recipe;
```

A receita retornada ainda não está persistida.

O usuário deve confirmar antes de salvar.

---

# Create Recipe

## Objetivo

Salvar uma nova receita no armazenamento local.

---

## Entrada

```ts
Recipe;
```

---

## Processo

O caso de uso deve:

1. validar a receita;
2. gerar um ID caso necessário;
3. persistir a receita;
4. criar o chat associado à receita.

---

## Saída

```ts
Recipe;
```

persistida.

---

# Update Recipe

## Objetivo

Atualizar uma receita existente.

---

## Entrada

```ts
Recipe;
```

---

## Processo

O caso de uso deve:

1. validar os dados;
2. localizar a receita existente;
3. substituir a versão atual;
4. manter o histórico do chat.

No MVP não existe versionamento de receitas.

---

# Modify Recipe With AI

## Objetivo

Solicitar uma alteração em uma receita utilizando Inteligência Artificial.

---

## Entrada

```ts
{
  recipeId: string,
  instruction: string
}
```

Exemplo:

```text
"Substitua o leite por uma opção sem lactose"
```

---

## Processo

O caso de uso deve:

1. recuperar a receita;
2. adicionar contexto da receita;
3. enviar instrução para IA;
4. validar a nova receita;
5. retornar uma sugestão.

A receita atual não deve ser sobrescrita automaticamente.

---

## Saída

```ts
Recipe;
```

como sugestão.

O usuário decide se deseja salvar.

---

# Send Recipe Message

## Objetivo

Enviar uma mensagem para a Inteligência Artificial relacionada a uma receita.

---

## Entrada

```ts
{
  recipeId: string,
  message: string
}
```

---

## Processo

O caso de uso deve:

1. recuperar a receita;
2. recuperar histórico do chat;
3. construir contexto;
4. enviar mensagem para IA;
5. salvar mensagem do usuário;
6. salvar resposta da IA.

---

## Saída

```ts
Message;
```

---

# Get Recipes

## Objetivo

Recuperar receitas salvas.

---

## Entrada

Opcional:

```ts
{
  search?: string
}
```

---

## Saída

```ts
Recipe[]
```

---

# Get Recipe

## Objetivo

Recuperar uma receita específica.

---

## Entrada

```ts
{
  recipeId: string;
}
```

---

## Saída

```ts
Recipe;
```

---

# Save User Context

## Objetivo

Salvar informações utilizadas como contexto pela IA.

Inclui:

- Minha Geladeira;
- Preferências Alimentares.

---

## Entrada

```ts
{
  pantryContext?: string,
  foodPreferences?: string
}
```

---

# Futuro: API HTTP

Quando o sistema possuir:

- autenticação;
- múltiplos usuários;
- armazenamento remoto;
- backend próprio;

os casos de uso poderão ser expostos através de uma API HTTP.

Possível arquitetura futura:

```
Frontend
    |
    ↓
HTTP API
    |
    ↓
Application Layer
    |
    ↓
Domain
    |
    ↓
Infrastructure
```

A existência de uma API HTTP futura não deve alterar as regras de negócio do domínio.
