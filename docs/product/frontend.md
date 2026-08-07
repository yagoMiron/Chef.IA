# Frontend

## Objetivos

O frontend deve priorizar:

- simplicidade;
- rapidez;
- acessibilidade;
- legibilidade;
- experiência mobile.

A interface deve minimizar distrações e permitir que o usuário encontre rapidamente suas receitas.

A aplicação deve priorizar uma experiência simples para usuários iniciantes em culinária.

---

# Home

A Home é o ponto de entrada principal da aplicação.

Componentes principais:

- Botão Nova Receita;
- Botão Livro de Receitas;
- Botão Minha Geladeira;
- Botão Preferências Alimentares.

A Home deve apresentar as principais ações da aplicação de forma clara e direta.

---

# Nova Receita

Permite ao usuário solicitar a criação de uma nova receita através da Inteligência Artificial.

Componentes:

- Campo de descrição da receita desejada;
- Botão Gerar Receita;
- Indicador de carregamento;
- Visualização da receita gerada;
- Botão Salvar;
- Botão Descartar;
- Botão Gerar Novamente.

O usuário deve conseguir revisar a receita gerada antes de salvá-la.

A receita gerada deve seguir o schema definido em `recipe-model.md`.

---

# Livro de Receitas

Exibe as receitas salvas pelo usuário.

Componentes:

- Campo de pesquisa;
- Lista de receitas;
- Item de receita;
- Estado para livro vazio.

Filtros por categoria estão fora do escopo do MVP.

A pesquisa deve permitir localizar receitas pelo título.

---

# Receita

Exibe uma receita individual.

Componentes:

- Título;
- Quantidade de porções;
- Lista de ingredientes;
- Modo de preparo;
- Botão Editar;
- Botão Modificar com IA;
- Área de Chat.

O ID da receita é utilizado internamente para identificar a receita, mas não deve ser apresentado ao usuário como conteúdo da receita.

---

# Edição da Receita

Permite ao usuário modificar manualmente uma receita existente.

O formulário deve permitir editar:

- título;
- quantidade de porções;
- ingredientes;
- etapas de preparo.

A edição deve preservar a estrutura definida em `recipe-model.md`.

Não haverá versionamento de receitas no MVP.

Salvar uma edição substitui a versão atual da receita.

---

# Modificação com IA

Permite ao usuário solicitar alterações em uma receita utilizando a Inteligência Artificial.

Exemplos:

- substituir um ingrediente;
- alterar a quantidade de porções;
- adaptar a receita aos ingredientes disponíveis;
- simplificar o preparo.

A alteração gerada pela IA deve ser apresentada ao usuário antes de substituir a receita atual.

A receita atual não deve ser sobrescrita automaticamente sem confirmação do usuário.

---

# Chat da Receita

Permite ao usuário conversar com a Inteligência Artificial sobre uma receita específica.

O chat deve manter relação com uma única receita.

Exemplos de perguntas:

- "Posso substituir o leite?"
- "Como sei que está assado?"
- "Posso preparar isso sem forno?"
- "Posso congelar essa receita?"

O contexto da receita deve estar disponível para a Inteligência Artificial durante a conversa.

---

# Minha Geladeira

Permite ao usuário fornecer informações sobre os ingredientes que possui ou costuma possuir.

Componentes:

- Área de texto;
- Botão Salvar.

O MVP utilizará texto livre.

Exemplo:

"Tenho frango, arroz, tomate e cebola. Normalmente tenho alho e alguns temperos."

Esse conteúdo será utilizado como contexto para funcionalidades de Inteligência Artificial.

O MVP não terá controle estruturado de estoque ou quantidade de ingredientes.

---

# Preferências Alimentares

Permite ao usuário informar preferências e restrições relacionadas à alimentação.

Componentes:

- Área de texto;
- Botão Salvar.

O MVP utilizará texto livre.

O usuário poderá informar, por exemplo:

- alimentos que não gosta;
- ingredientes que deseja evitar;
- restrições alimentares;
- preferência por refeições mais econômicas;
- preferência por determinados estilos alimentares.

Esse conteúdo será utilizado como contexto para funcionalidades de Inteligência Artificial.

---

# Responsividade

A aplicação deve funcionar em:

- Desktop;
- Tablet;
- Smartphone.

Como trata-se de um PWA, a experiência mobile possui prioridade.

A interface deve utilizar abordagem mobile-first sempre que apropriado.

---

# Acessibilidade

Toda interface deve:

- possuir contraste adequado;
- permitir navegação por teclado;
- utilizar HTML semântico;
- possuir estados de foco visíveis;
- possuir labels associados aos campos de formulário;
- fornecer textos alternativos quando necessário;
- comunicar estados de carregamento e erro de maneira acessível.

A acessibilidade deve ser considerada durante a implementação, não adicionada posteriormente como etapa isolada.

---

# Estados da Interface

As telas que dependem de operações assíncronas devem considerar pelo menos:

- estado normal;
- carregamento;
- sucesso;
- erro;
- estado vazio.

Operações envolvendo Inteligência Artificial devem apresentar feedback visual durante o processamento.

Erros não devem resultar em telas quebradas ou perda silenciosa de dados.

---

# Princípios de Interface

A interface deve:

- evitar complexidade desnecessária;
- priorizar ações importantes;
- utilizar componentes consistentes;
- evitar informações redundantes;
- manter hierarquia visual clara;
- utilizar linguagem simples;
- priorizar legibilidade em dispositivos móveis.
