<h1>Git - Commits Semânticos</h1>



Os **Commits Semânticos** são uma convenção que visa criar um histórico claro e estruturado, facilitando tanto a compreensão quanto a automação. Ao utilizar palavras-chave e emojis, eles indicam de forma explícita o tipo de alteração realizada no código.

Essa convenção estabelece um conjunto de regras para a criação de mensagens de commit bem definidas, o que facilita o desenvolvimento de ferramentas automatizadas.

<br />

<h2>1. Tipos e Descrições</h2>



O Commit Semântico é composto pelos seguintes elementos estruturais (tipos), que indicam claramente a intenção do seu commit para outros usuários do código:

| **Tipo**     | **Descrição**                                      |
| ------------ | -------------------------------------------------- |
| **feat**     | Adição de novos recursos.                          |
| **fix**      | Correção de bugs.                                  |
| **docs**     | Alterações na documentação.                        |
| **test**     | Modificações em testes unitários.                  |
| **build**    | Alterações de build e dependências.                |
| **perf**     | Melhorias de performance.                          |
| **style**    | Formatações (não código).                          |
| **refactor** | Refatoração sem alterar a funcionalidade.          |
| **chore**    | Atualizações administrativas (não código).         |
| **ci**       | Integração contínua.                               |
| **raw**      | Alterações em configurações e dados.               |
| **cleanup**  | Limpeza de código.                                 |
| **remove**   | Exclusão de arquivos ou funcionalidades obsoletas. |

<br />

<h3>1.1. Recomendações</h3>



- Adicione um **tipo** que seja consistente com o título do conteúdo.
- Recomendamos que a **primeira linha** tenha em média 4 palavras.
- **Use um emoji** no início da mensagem de commit para representar o tipo de alteração realizada.

<br />

<h2>2. Padrões de Emojis </h2>



| Tipo do commit                      | Emoji                  | Palavra-chave |
| ----------------------------------- | ---------------------- | ------------- |
| **Acessibilidade**                  | ♿ `:wheelchair:`       |               |
| **Adicionando um teste**            | ✅ `:white_check_mark:` | `test`        |
| **Alterações de revisão de código** | 👌 `:ok_hand:`          | `style`       |
| **Animações e transições**          | 💫 `:dizzy:`            |               |
| **Bugfix**                          | 🐛 `:bug:`              | `fix`         |
| **Comentários**                     | 💡 `:bulb:`             | `docs`        |
| **Commit inicial**                  | 🎉 `:tada:`             | `init`        |
| **Configuração**                    | 🔧 `:wrench:`           | `chore`       |
| **Deploy**                          | 🚀 `:rocket:`           |               |
| **Documentação**                    | 📚 `:books:`            | `docs`        |
| **Estilização de interface**        | 💄 `:lipstick:`         | `feat`        |
| **Infraestrutura**                  | 🧱 `:bricks:`           | `ci`          |
| **Mover/Renomear**                  | 🚚 `:truck:`            | `chore`       |
| **Novo recurso ou Feature**         | ✨ `:sparkles:`         | `feat`        |
| **Package.json em JS**              | 📦 `:package:`          | `build`       |
| **Performance**                     | ⚡ `:zap:`              | `perf`        |
| **Refatoração**                     | ♻️ `:recycle:`          | `refactor`    |
| **Limpeza de Código**               | 🧹 `:broom:`            | `cleanup`     |
| **Removendo um arquivo**            | 🗑️ `:wastebasket:`      | `remove`      |
| **Responsividade**                  | 📱 `:iphone:`           |               |
| **Revertendo mudanças**             | 💥 `:boom:`             | `fix`         |
| **Segurança**                       | 🔒️ `:lock:`             |               |
| **SEO**                             | 🔍️ `:mag:`              |               |
| **Tag de versão**                   | 🔖 `:bookmark:`         |               |
| **Testes**                          | 🧪 `:test_tube:`        | `test`        |
| **Texto**                           | 📝 `:pencil:`           |               |
| **Tipagem**                         | 🏷️ `:label:`            |               |
| **Tratamento de erros**             | 🥅 `:goal_net:`         |               |
| **Dados**                           | 🗃️ `:card_file_box:`    | `raw`         |

<br />

<h3>2.1. Exemplos Práticos</h3>



| **Comando Git**                                             | **Resultado**                         |
| ----------------------------------------------------------- | ------------------------------------- |
| `git commit -m ":tada: Commit inicial"`                     | 🎉 Commit inicial                      |
| `git commit -m ":sparkles: feat: Página de login"`          | ✨ feat: Página de login               |
| `git commit -m ":bug: fix: Corrigido loop infinito"`        | 🐛 fix: Corrigido loop infinito        |
| `git commit -m ":zap: perf: Melhoria no tempo de resposta"` | ⚡ perf: Melhoria no tempo de resposta |
| `git commit -m ":wastebasket: remove: Remoção de arquivos"` | 🗑️ remove: Remoção de arquivos         |

