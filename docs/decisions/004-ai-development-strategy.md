# ADR-004 - AI Development Strategy

## Status

Accepted

---

## Context

O Chef.IA será desenvolvido utilizando Inteligência Artificial como ferramenta principal de desenvolvimento.

Entretanto, a IA não deve tomar decisões arquiteturais de forma autônoma.

O projeto deve permanecer totalmente compreensível e controlado por um desenvolvedor humano.

---

## Decision

A Inteligência Artificial deve seguir as seguintes regras durante todo o desenvolvimento.

### Arquitetura

A IA nunca deve:

- alterar a arquitetura da aplicação;
- alterar a estrutura de pastas;
- alterar convenções do projeto;
- modificar decisões documentadas.

Mudanças arquiteturais sempre devem ser aprovadas pelo desenvolvedor.

---

### Dependências

A IA nunca deve instalar novas bibliotecas sem autorização.

Caso uma biblioteca seja necessária, ela deve justificar:

- problema que resolve;
- vantagens;
- alternativas;
- impacto na aplicação.

A decisão final pertence ao desenvolvedor.

---

### Reutilização

Antes de criar qualquer código, a IA deve procurar implementações existentes.

É obrigatório reutilizar código sempre que possível.

Duplicação de código deve ser evitada.

---

### Documentação

Toda decisão presente na pasta docs possui prioridade sobre sugestões da IA.

Caso exista conflito entre documentação e boas práticas sugeridas pelo modelo, a documentação deve prevalecer.

---

### Refatoração

A IA nunca deve realizar grandes refatorações automaticamente.

Refatorações estruturais devem ser propostas antes da implementação.

---

## Consequences

A velocidade de desenvolvimento pode ser ligeiramente reduzida.

Em compensação, o projeto permanece consistente, previsível e facilmente mantido.

---

### Código existente

Antes de criar uma nova implementação, a IA deve analisar código existente relacionado.

A IA deve preferir modificar uma implementação existente ao invés de criar uma nova.
