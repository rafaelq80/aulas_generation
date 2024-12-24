<h1>Git - Branches Semânticas</h1>



As **Branches Semânticas** são uma prática adotada em projetos de software, especialmente os grandes projetos, para criar ramificações (branches) de código que sigam uma convenção de nomenclatura consistente e que descrevam claramente o objetivo da alteração que está sendo feita. Essa abordagem facilita a colaboração, o entendimento do código e a automação de processos, como integração contínua (CI) e deployment contínuo (CD).

> **Integração Contínua (CI)** é a prática de automatizar o processo de integração de código em um repositório compartilhado, garantindo que as alterações sejam testadas e validadas de forma contínua, minimizando erros e conflitos.
>
> **Deployment Contínuo (CD)** vai além da integração, automatizando o processo de entrega do código para ambientes de produção. Após a validação da CI, as alterações são automaticamente implantadas, garantindo que o código mais recente esteja sempre disponível para os usuários.

O principal objetivo das branches semânticas é garantir que qualquer desenvolvedor ou colaborador consiga entender facilmente o propósito de cada ramificação do projeto. As convenções de nomenclatura semântica ajudam a garantir que as branches sejam nomeadas de forma consistente e padronizada.

<br />

<h2>1. Estrutura das Branches Semânticas</h2>



O nome das branches semânticas geralmente segue um padrão que envolve um **tipo** de alteração seguido de um **nome** que descreve a mudança de forma específica. Exemplos comuns de tipos incluem:

Aqui está a tabela com os tipos de branches semânticas:

| **Tipo**    | **Descrição**                                                | **Exemplo**                                                  |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `feat/`     | Para novas funcionalidades ou recursos.                      | `feat/login` (adicionando funcionalidade de login)           |
| `fix/`      | Para correção de bugs.                                       | `fix/boleto-erro-validacao` (corrigindo erro de validação no boleto) |
| `docs/`     | Para alterações na documentação do projeto.                  | `docs/atualizacao-readme` (atualizando o arquivo README)     |
| `test/`     | Para mudanças ou adições de testes unitários.                | `test/cenario-login` (adicionando testes para o cenário de login) |
| `style/`    | Para ajustes de estilo (sem alteração de funcionalidade).    | `style/ajustes-layout` (ajustes no layout da página)         |
| `refactor/` | Para refatoração de código sem mudança de funcionalidade.    | `refactor/otimizacao-funcoes` (refatorando funções para melhorar a performance) |
| `chore/`    | Para tarefas administrativas ou de manutenção do código, como atualização de dependências. | `chore/atualizar-dependencias` (atualizando dependências do projeto) |
| `ci/`       | Para mudanças na configuração de integração contínua (CI).   | `ci/ajustes-pipeline` (ajustes no pipeline de CI)            |

<br />

<h3>1.1. Benefícios das Branches Semânticas</h3>



1. **Facilidade de entendimento**: O nome da branch descreve o que está sendo feito, tornando mais fácil para qualquer desenvolvedor saber o que está sendo alterado sem precisar abrir o código.
2. **Organização e padronização**: Usar uma convenção de nomenclatura semântica ajuda a manter o repositório organizado, especialmente em equipes grandes, onde múltiplos desenvolvedores estão trabalhando simultaneamente.
3. **Automação**: Com uma convenção semântica, ferramentas de integração contínua (CI) e deployment contínuo (CD) podem ser configuradas para automatizar processos, como testes, builds e deploys, com base no tipo de branch.
4. **Histórico de alterações mais claro**: Quando as branches seguem um padrão, fica mais fácil entender o histórico do projeto, o que foi adicionado, corrigido, ou alterado em cada fase do desenvolvimento.

<br />

<h3>1.2. Exemplos de Nomes de Branches Semânticas</h3>



| **Branch**                    | **Descrição**                                      |
| ----------------------------- | -------------------------------------------------- |
| `feat/cadastro-usuario`       | Adicionando funcionalidade de cadastro de usuário. |
| `fix/corrigir-bug-login`      | Corrigindo o bug no processo de login.             |
| `docs/atualizar-readme`       | Atualizando a documentação no README.              |
| `test/adicionar-testes-login` | Adicionando testes para o sistema de login.        |
| `chore/limpeza-codigo`        | Realizando limpeza de código.                      |

Com essa prática, equipes podem manter a base de código mais organizada e facilitar o processo de desenvolvimento colaborativo.