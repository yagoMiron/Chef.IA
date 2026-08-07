# ADR-002

## Título

Utilizar TypeORM para persistência server-side futura

## Contexto

O MVP utiliza IndexedDB através de repositories.

Quando a aplicação possuir backend remoto e persistência server-side, será necessário utilizar um ORM.

## Decisão

TypeORM será utilizado como ORM quando existir persistência server-side.

No MVP o TypeORM não será instalado.

Prisma não será utilizado.

## Motivos

- maior familiaridade da equipe;
- preferência arquitetural;
- menor dependência de geração automática de código.
