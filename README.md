# Chef.IA

Chef.IA é uma Progressive Web App (PWA) desenvolvida para auxiliar usuários no gerenciamento de receitas culinárias utilizando Inteligência Artificial.

O projeto serve simultaneamente como uma aplicação de uso pessoal e como um projeto de estudo sobre desenvolvimento **AI-first**, aplicando princípios de Arquitetura de Software, Clean Architecture, testes automatizados e boas práticas de engenharia de software.

---

## Objetivos

- Gerar receitas utilizando IA.
- Organizar receitas em um livro digital.
- Permitir edição manual e assistida por IA.
- Manter um chat contextual para cada receita.
- Personalizar receitas com base em ingredientes disponíveis e preferências alimentares.

---

## Tecnologias

- Next.js
- React
- TypeScript
- Tailwind CSS
- shadcn/ui
- TypeORM
- PostgreSQL (futuro)
- IndexedDB (MVP)
- Zod
- pnpm

---

## Arquitetura

O projeto segue uma arquitetura em camadas:

```
UI
    ↓
Application
    ↓
Domain
    ↓
Infrastructure
```

Toda a documentação da arquitetura está disponível na pasta `docs/`.

---

## Estrutura da Documentação

```
docs/

architecture/
backend/
decisions/
domain/
features/
product/
```

A documentação representa a fonte de verdade do projeto.

Antes de implementar qualquer funcionalidade, consulte os documentos relevantes.

---

## Desenvolvimento

Instalar dependências:

```bash
pnpm install
```

Executar em modo de desenvolvimento:

```bash
pnpm dev
```

Executar lint:

```bash
pnpm lint
```

Executar testes:

```bash
pnpm test
```

> Os testes ainda serão implementados.

---

## Filosofia do Projeto

Este projeto utiliza Inteligência Artificial como ferramenta de desenvolvimento, porém todas as decisões arquiteturais permanecem sob controle do desenvolvedor.

A IA deve:

- respeitar toda a documentação presente em `docs/`;
- seguir os ADRs definidos;
- reutilizar código existente;
- evitar duplicação;
- não instalar dependências sem autorização;
- não alterar a arquitetura automaticamente.

---

## Roadmap

### MVP

- [ ] Gerar receitas com IA
- [ ] Livro de receitas
- [ ] Edição manual
- [ ] Modificação por IA
- [ ] Chat contextual por receita
- [ ] Preferências alimentares
- [ ] Minha Geladeira
- [ ] Persistência local
- [ ] PWA

### Futuro

- [ ] Autenticação
- [ ] Sincronização em nuvem
- [ ] PostgreSQL
- [ ] Compartilhamento de receitas
- [ ] Lista de compras
- [ ] Imagens das receitas
- [ ] Informações nutricionais

---

## Licença

Este projeto está sendo desenvolvido para fins de estudo e uso pessoal.
