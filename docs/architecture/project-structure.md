# Estrutura do Projeto

## Objetivo

A estrutura do projeto deve separar claramente:

- interface e apresentação;
- aplicação e casos de uso;
- domínio e regras de negócio;
- infraestrutura e integrações externas.

A estrutura deve favorecer:

- baixo acoplamento;
- alta coesão;
- reutilização;
- testabilidade;
- manutenção;
- facilidade de evolução da aplicação.

A estrutura física das pastas deve refletir as responsabilidades arquiteturais do sistema.

---

# Estrutura Geral

```text
src/
├── app/
├── components/
├── application/
├── domain/
├── infrastructure/
├── hooks/
├── store/
├── schemas/
├── lib/
├── utils/
├── tests/
└── assets/
```

---

# app/

Responsável exclusivamente pela camada de apresentação e integração com o Next.js App Router.

Pode conter:

- páginas;
- layouts;
- loading;
- error;
- not-found;
- templates;
- route handlers, quando aplicável;
- metadata;
- configuração específica do App Router.

A pasta `app/` **não deve conter regras de negócio**.

As páginas devem orquestrar a interface e delegar operações da aplicação para a camada `application/`.

---

# components/

Contém componentes React reutilizáveis de apresentação.

Exemplos:

- componentes de interface;
- componentes de formulário;
- componentes visuais específicos de uma funcionalidade;
- componentes compostos reutilizáveis.

Componentes devem, sempre que possível:

- receber dados através de props;
- emitir eventos através de callbacks;
- permanecer independentes de infraestrutura;
- evitar acesso direto a persistência;
- evitar chamadas diretas a serviços externos.

Componentes não devem conter regras de negócio complexas.

Componentes altamente específicos de uma única funcionalidade podem ser organizados em subpastas relacionadas àquela funcionalidade.

---

# application/

Contém os casos de uso da aplicação.

Essa camada representa **o que o sistema faz**.

Exemplos:

```text
application/
└── use-cases/
    ├── create-recipe/
    ├── update-recipe/
    ├── generate-recipe/
    ├── modify-recipe/
    └── send-recipe-message/
```

Casos de uso devem:

- coordenar operações da aplicação;
- utilizar entidades e regras do domínio;
- depender de abstrações, não de implementações concretas;
- ser independentes de componentes React;
- ser independentes de detalhes de infraestrutura sempre que possível;
- ser facilmente testáveis.

A camada `application/` não deve conhecer detalhes específicos de:

- IndexedDB;
- PostgreSQL;
- TypeORM;
- OpenRouter;
- APIs externas;
- componentes React.

Quando precisar dessas capacidades, deve depender de abstrações definidas pelo domínio ou pela própria camada de aplicação.

---

# domain/

Contém o núcleo do domínio da aplicação.

Essa é a camada que representa **o que o sistema é** e suas regras de negócio.

Pode conter:

```text
domain/
├── entities/
├── value-objects/
├── repositories/
├── services/
└── errors/
```

## entities/

Entidades do domínio.

Exemplos:

- Recipe;
- Ingredient;
- PreparationStep;
- Chat;
- Message.

As entidades devem representar conceitos do domínio e suas regras, não detalhes de persistência ou apresentação.

---

## value-objects/

Valores que possuem significado próprio no domínio e não precisam possuir identidade independente.

Esta pasta pode permanecer vazia enquanto o domínio não justificar a criação de Value Objects.

Não criar abstrações apenas por antecipação.

---

## repositories/

Interfaces que representam as necessidades de persistência do domínio.

Exemplo conceitual:

```text
RecipeRepository
```

A interface define **o que a aplicação precisa fazer**, não como isso será feito.

Implementações concretas pertencem à camada `infrastructure/`.

---

## services/

Serviços de domínio devem existir somente quando uma regra de negócio não pertencer naturalmente a uma entidade ou Value Object.

Não utilizar Domain Services apenas para agrupar funções arbitrariamente.

---

## errors/

Erros específicos do domínio.

Erros devem representar situações relevantes para as regras de negócio.

---

# infrastructure/

Contém implementações concretas de recursos externos e detalhes técnicos.

Exemplos:

```text
infrastructure/
├── persistence/
├── ai/
└── external/
```

---

## persistence/

Implementações concretas de persistência.

No MVP, a persistência será local.

Exemplo:

```text
infrastructure/
└── persistence/
    └── indexed-db/
```

Futuramente, quando o armazenamento remoto for introduzido, poderão existir implementações utilizando PostgreSQL e TypeORM.

A aplicação não deve depender diretamente dessas implementações.

---

## ai/

Implementações relacionadas aos provedores de Inteligência Artificial.

Exemplo:

```text
infrastructure/
└── ai/
    └── openrouter/
```

O restante da aplicação não deve depender diretamente da implementação do OpenRouter.

A infraestrutura deve implementar as abstrações necessárias para que a aplicação utilize serviços de IA sem conhecer os detalhes do provedor.

---

## external/

Integrações externas que não se enquadram em persistência ou IA.

Exemplos futuros podem incluir:

- serviços externos;
- APIs de terceiros;
- integrações específicas.

---

# hooks/

Contém React Hooks reutilizáveis relacionados à interface.

Hooks podem:

- controlar estado de interface;
- encapsular comportamento de componentes;
- coordenar interações entre componentes e a camada de aplicação.

Hooks não devem:

- implementar regras de negócio complexas;
- acessar diretamente bancos de dados;
- acessar diretamente IndexedDB;
- realizar chamadas diretas para provedores externos;
- duplicar lógica existente em casos de uso.

Quando um hook precisar executar uma operação de negócio, deve utilizar a camada `application/`.

---

# store/

Contém estado global de interface ou estado compartilhado entre componentes.

O estado global não deve ser utilizado como substituto para:

- entidades de domínio;
- casos de uso;
- persistência;
- repositories.

Regras de negócio complexas não devem ser implementadas dentro do store.

A necessidade de uma biblioteca de gerenciamento de estado global deve ser avaliada antes de adicionar uma dependência.

---

# schemas/

Contém schemas de validação utilizados pela aplicação.

O projeto utiliza Zod para validação de dados externos e contratos que necessitem de validação em runtime.

Exemplos:

- respostas de provedores de IA;
- dados provenientes de formulários;
- dados provenientes de APIs;
- dados recuperados de persistência quando necessário.

Schemas relacionados diretamente a uma entidade ou contrato podem ser organizados em subpastas.

Schemas não devem conter regras de negócio complexas.

---

# lib/

Contém configurações e abstrações técnicas compartilhadas que não pertencem diretamente a uma camada arquitetural específica.

Exemplos possíveis:

- configuração de bibliotecas;
- configuração de ambiente;
- helpers de integração;
- configurações do framework;
- abstrações técnicas pequenas e compartilhadas.

`lib/` não deve se tornar uma pasta genérica para código que não possui uma responsabilidade clara.

Antes de adicionar algo a `lib/`, deve ser avaliado se o código pertence a:

- `domain/`;
- `application/`;
- `infrastructure/`;
- `utils/`;
- ou outra pasta específica.

---

# utils/

Contém funções utilitárias genéricas e puras.

Características esperadas:

- baixo acoplamento;
- sem regras de negócio específicas;
- sem acesso a banco;
- sem acesso a APIs externas;
- sem efeitos colaterais quando possível.

Não utilizar `utils/` como depósito genérico para funções cuja responsabilidade pertença a outra camada.

---

# tests/

Contém infraestrutura e testes que não estejam próximos do código testado.

Estrutura:

```text
tests/
├── unit/
├── integration/
└── e2e/
```

## unit/

Testes unitários de unidades isoladas.

Devem ser rápidos e independentes de infraestrutura externa.

---

## integration/

Testes que verificam a interação entre múltiplos componentes ou camadas.

Podem envolver:

- repositories;
- persistência;
- adapters;
- casos de uso;
- integrações controladas.

---

## e2e/

Testes de fluxo completo da aplicação através da perspectiva do usuário.

Devem validar comportamentos importantes da aplicação, não detalhes internos de implementação.

---

# assets/

Contém recursos estáticos utilizados pelo projeto.

Exemplos:

- imagens;
- ícones;
- fontes locais;
- arquivos estáticos específicos da aplicação.

Recursos públicos que precisam ser servidos diretamente pelo Next.js devem permanecer em `public/`, conforme as convenções do framework.

---

# Dependências entre Camadas

As dependências devem seguir, sempre que possível, a seguinte direção:

```text
Presentation
    ↓
Application
    ↓
Domain
    ↑
Infrastructure
```

Uma representação mais precisa:

```text
┌─────────────────────┐
│       app/          │
│    components/      │
│      hooks/         │
└──────────┬──────────┘
           │
           ↓
┌─────────────────────┐
│    application/     │
└──────────┬──────────┘
           │
           ↓
┌─────────────────────┐
│       domain/       │
└─────────────────────┘
           ↑
           │
┌─────────────────────┐
│   infrastructure/   │
└─────────────────────┘
```

A infraestrutura pode implementar interfaces definidas pelo domínio ou pela aplicação.

O domínio não deve depender da infraestrutura.

---

# Regras Gerais

## 1. Não criar pastas sem responsabilidade definida

Toda nova pasta deve representar uma responsabilidade arquitetural clara.

---

## 2. Não duplicar responsabilidades

Antes de criar uma nova função, serviço, componente, hook ou abstração, procurar primeiro por uma implementação existente.

---

## 3. Não criar abstrações prematuramente

Não criar camadas, interfaces ou padrões apenas porque podem ser úteis no futuro.

A abstração deve resolver uma necessidade real do projeto.

---

## 4. Não misturar responsabilidades

Um arquivo não deve acumular responsabilidades de diferentes camadas apenas por conveniência.

---

## 5. Infraestrutura deve ser substituível

Detalhes como:

- banco de dados;
- mecanismo de persistência;
- provedor de IA;
- APIs externas;

não devem contaminar as regras centrais do domínio.

---

## 6. A estrutura deve evoluir com o projeto

A estrutura definida neste documento representa a arquitetura atual.

Quando o sistema crescer, novas subpastas podem ser introduzidas quando houver necessidade real.

Mudanças estruturais relevantes devem ser documentadas através de uma Architecture Decision Record (ADR).

---

# Estrutura Inicial Esperada

No início do desenvolvimento, a estrutura pode ser mínima.

Não é necessário criar todas as pastas imediatamente.

Por exemplo:

```text
src/
├── app/
├── application/
├── domain/
├── infrastructure/
├── components/
├── hooks/
├── schemas/
├── lib/
├── store/
├── utils/
├── tests/
└── assets/
```

Subdiretórios devem ser criados conforme suas responsabilidades forem necessárias.

A ausência de uma pasta vazia não constitui violação desta arquitetura.
