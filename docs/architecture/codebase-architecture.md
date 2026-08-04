# Arquitetura da Base de Código

## Objetivo

Este documento define como o código-fonte do Chef.IA deve ser organizado.

O objetivo é garantir separação clara de responsabilidades, facilitar manutenção, reduzir acoplamento e permitir que a Inteligência Artificial trabalhe em partes isoladas do sistema.

Toda implementação deve respeitar esta organização.

---

# Princípios

A aplicação deve seguir os seguintes princípios:

- responsabilidade única;
- baixo acoplamento;
- alta coesão;
- separação entre domínio e infraestrutura;
- reutilização de código;
- composição em vez de duplicação.

Nenhuma regra de negócio deve ficar em componentes React.

---

# Camadas

A aplicação é dividida nas seguintes camadas.

```
UI

↓

Application

↓

Domain

↓

Infrastructure
```

Cada camada possui responsabilidades específicas.

---

# UI

Responsável apenas pela interface.

Inclui:

- páginas;
- layouts;
- componentes;
- hooks de interface;
- formulários.

A UI nunca deve:

- acessar banco de dados;
- construir prompts;
- chamar APIs externas diretamente;
- conter regras de negócio.

---

# Application

Responsável pelos casos de uso da aplicação.

Cada funcionalidade deve possuir seu próprio Use Case.

Exemplos:

- GenerateRecipe
- UpdateRecipe
- DeleteRecipe
- SendRecipeMessage

Os Use Cases coordenam o fluxo da aplicação.

Eles não implementam infraestrutura.

---

# Domain

Contém as regras de negócio.

Inclui:

- entidades;
- modelos;
- validações de domínio;
- regras de negócio.

O domínio não deve conhecer:

- React;
- IndexedDB;
- HTTP;
- OpenRouter;
- Gemini;
- qualquer tecnologia externa.

---

# Infrastructure

Responsável pela comunicação com recursos externos.

Inclui:

- armazenamento local;
- banco de dados;
- provedores de IA;
- APIs externas;
- serialização;
- persistência.

Mudanças nesta camada não devem impactar o domínio.

---

# Comunicação entre Camadas

A comunicação deve ocorrer apenas no sentido abaixo.

```
UI

↓

Application

↓

Domain

↓

Infrastructure
```

Camadas inferiores nunca dependem de camadas superiores.

---

# Use Cases

Cada funcionalidade deve possuir um caso de uso próprio.

Exemplos:

- GenerateRecipeUseCase
- ModifyRecipeUseCase
- UpdateRecipeUseCase
- DeleteRecipeUseCase
- SendRecipeMessageUseCase

Use Cases representam ações do usuário.

Eles coordenam toda a execução da funcionalidade.

---

# Services

Services representam comportamentos reutilizáveis.

Exemplos:

- AIService
- ContextBuilder
- PromptBuilder
- RecipeValidator

Services não devem conhecer componentes React.

---

# Repositories

Toda persistência deve ocorrer através de Repositories.

Exemplos:

- RecipeRepository
- ChatRepository
- PreferencesRepository
- PantryRepository

Nenhum Use Case deve acessar IndexedDB diretamente.

---

# Providers

Toda integração com serviços externos deve ser encapsulada em Providers.

Exemplos:

- OpenRouterProvider
- GeminiProvider
- OpenAIProvider

Trocar um provedor não deve exigir alterações na regra de negócio.

---

# Validação

Toda entrada deve ser validada antes de chegar ao domínio.

Toda resposta da IA deve ser validada antes de ser utilizada.

O domínio nunca deve assumir que dados externos são válidos.

---

# Estrutura Inicial

A estrutura inicial da aplicação deverá seguir o modelo abaixo.

```text
src/

app/

components/

application/
    use-cases/

domain/

infrastructure/
    repositories/
    providers/

lib/

types/

schemas/

hooks/

styles/
```

A estrutura poderá evoluir conforme a complexidade do projeto aumentar.

---

# Regras Gerais

- Componentes React não implementam regra de negócio.
- Toda comunicação com IA passa pelo AIService.
- Todo prompt é construído pelo PromptBuilder.
- Todo contexto é construído pelo ContextBuilder.
- Toda persistência ocorre através de Repositories.
- Todo caso de uso possui uma única responsabilidade.
- Nenhuma camada deve acessar diretamente uma camada não permitida.

---

# Objetivo Final

A arquitetura deve permitir que novas funcionalidades sejam adicionadas com o menor impacto possível nas partes já existentes da aplicação.

O código deve permanecer organizado, previsível e facilmente compreendido tanto por desenvolvedores quanto por ferramentas de Inteligência Artificial.
