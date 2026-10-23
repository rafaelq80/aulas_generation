# Atividade Prática: Git no Terminal Git Bash



**Objetivo:** Criar um projeto na pasta *Documentos*, versionar arquivos, desfazer commits com segurança, enviar ao GitHub, baixar alterações remotas, clonar um repositório e navegar pelo histórico de commits.

**Pré-requisitos:**

- Windows 10 ou 11.
- Visual Studio Code
- Git instalado (caso não tenha, baixe em [git-scm.com](https://git-scm.com/)).
- Conta no GitHub (caso não tenha, crie a sua conta em [github.com](https://github.com))

<br />

## Visual Studio Code (VSCode)



O **Visual Studio Code (VS Code)** é um editor de código amplamente utilizado no desenvolvimento de aplicações com diversas linguagens de programação, incluindo Python. 



<br />

## Git Bash



O Git for Windows fornece uma emulação do **Terminal BASH - Terminal padrão do Linux**, chamado de **Git Bash**, para executar os comandos Git a partir da linha de comando do Linux. O Git Bash se comporta exatamente como o Terminal BASH do ambientes LINUX. Na imagem abaixo, temos a tela do Git Bash:

<div align="center"><img src="https://i.imgur.com/6zzIwgN.png" title="source: imgur.com" width="90%"/></div>

Observe que o prompt do Git Bash é diferente do Git Bash.

---

## Passo 1: Configuração Inicial do Git



1. Abra o **Visual Studio Code - VSCode**
2. Crie a pasta **aula_git** dentro da pasta **Documentos (Documents)**

> 1. No Visual Studio Code, clique na opção **File 🡪 Open Folder... (Arquivo 🡪 Abrir Pasta...)**
>
> <div align="center"><img src="https://i.imgur.com/TgvVW26.png" title="source: imgur.com" /></div>
>
> 2. Localize a pasta **Documentos (Documents)** 
>
> <div align="center">
>   <img src="https://i.imgur.com/5NoqaQO.png" title="source: imgur.com" />
> </div>
>
> 3. Crie a pasta **aula_git**, clicando no botão **Nova pasta**
>
>    ![](https://i.imgur.com/jUxYGVp.png)
>
> 4. Mantenha a pasta **aula_git** selecionada e clique no botão **Selecionar pasta (Select folder)**
>
> ![](https://i.imgur.com/Tz6eXBr.png)

3. Abra o Terminal **Git Bash** no Visual Studio Code. 

> [!WARNING]
>
> O **Git Bash é necessário apenas no Windows** para fornecer um ambiente Bash compatível. No **macOS e no Linux**, o sistema já possui um Terminal com Bash ou outro shell compatível, portanto, **não é necessário utilizar o Git Bash**, apenas abra o terminal.

> 1. Depois de abrir a pasta, abra o **Terminal** do Visual Studio Code através do menu **Terminal 🡪 New Terminal (Terminal 🡪 Novo Terminal)** ou através do atalho **CTRL + ' (Control + Aspas)**
>
> <div align="center"><img src="https://i.imgur.com/4rdobXK.png?1" title="source: imgur.com" /></div>
>
> 2. Será aberta a tela do **Power Shell** na parte inferior da janela do Visual Studio Code.
>
> <div><img src="https://i.imgur.com/K61VbPb.png" title="source: imgur.com" /></div>
>
> 3. Para alterar o Terminal padrão do Visual Studio Code para o **GitBash**, observe que ao lado do identificador do Terminal **powershell**, existe um botão com um sinal de **+** e uma **seta** apontando para baixo, como mostra a imagem abaixo:
>
> <div><img src="https://i.imgur.com/JbLTaUI.png" title="source: imgur.com" /></div>
>
> 4. Clique na seta apontando para baixo. Será aberto um Menu.
> 5. No Menu que será aberto, clique na opção **Select Default Profile (Selecionar o Perfil Padrão)**.
>
> <div align="center"><img src="https://i.imgur.com/nlQYFaX.png" title="source: imgur.com" /></div>
>
> 6. Será aberto um menu suspenso, abaixo da **Barra de Menus** do Visual Studio Code. Clique na opção **Git Bash**.
>
> <div align="center"><img src="https://i.imgur.com/81kHNE7.png" title="source: imgur.com" /></div>
>
> 7. Feche a Janela do Terminal e abra novamente através do menu **Terminal 🡪 New Terminal**. Observe que será aberta a janela do Terminal **Git Bash**, ao invés do Powershell.
>
>    <div><img src="https://i.imgur.com/hmyamcU.png" title="source: imgur.com" /></div>

4. Para verificar se o Git está instalado no sistema e qual é a versão, digite o comando:

```bash
git version
```

5. Para listar todas as configurações do Git, digite o comando:

```bash
git config --list
```

> 💡 Para sair da listagem do comando, caso seja necessário, pressione a letra **q** do seu teclado.

<br />

> [!WARNING]
>
> *Caso não apareça nenhuma configuração, significa que você ainda não configurou o seu Git.*

<br />

6. Para configurar o seu **nome** no Git, digite o comando:

```bash
git config --global user.name "seu_nome"
```

> *Substitua seu_nome, pelo seu nome completo.*

7. Para verificar se o seu **nome** foi configurado corretamente no Git, digite o comando:

```bash
git config user.name
```

8. Para configurar o seu **e-mail** no Git, digite o comando:

```bash
git config --global user.email "seu_email@email.com"
```

> *Substitua seu_email, pelo e-mail que você utilizou para criar a sua conta no GitHub.*

9. Para verificar se o seu **e-mail** foi configurado corretamente no Git, digite o comando:

```bash
git config user.email
```

10. Para configurar o **nome padrão da branch principal** do repositório Git, digite o comando:

```bash
git config --global init.defaultBranch main
```

> Essa configuração é importante para garantir que, em todos os seus repositórios, a branch principal seja criada automaticamente com o nome **main**, substituindo o antigo padrão **master**.

11. Para verificar se o **nome padrão da branch principal** foi configurado como main, digite o comando:

```bash
git config init.defaultBranch
```

12. Para utilizar a estratégia de mesclagem padrão ao invés do **rebase**, execute o comando:

```bash
git config --global pull.rebase false
```

<br />

> [!WARNING]
>
> Quando o repositório local e o remoto divergem, o `git pull` precisa de uma estratégia. O **merge** preserva o histórico como ele aconteceu e é mais simples para quem está começando. O rebase reescreve commits locais e fica para um estudo futuro.
>
> O comando acima desativa o rebase como comportamento padrão para todos os seus repositórios.

---

## Passo 2: Criando a Estrutura de Pastas e Arquivos



1. Crie a pasta **docs** dentro da pasta **aula_git**, clicando no botão **Nova pasta (New folder)**

![](https://i.imgur.com/cP80YvA.png)

2. Crie o arquivo **Turma.py**, clicando no botão **Novo arquivo (New file)**

![](https://i.imgur.com/88iGsVG.png)

3. Insira dentro do arquivo **Turma.py** o seguinte conteúdo:

```python
print("A turma NN é TOP!")
```

> Substitua **NN** pelo nome e número da sua turma

---

## Passo 3: Inicializando o Repositório e Primeiro Commit



1. Para **Inicializar o repositório Git**, utilize o comando:

   ```bash
   git init
   ```

> Observe que aparece a mensagem **(main)** no prompt do Git Bash, indicando que a pasta `aula_git` se tronou um repositório git.
>
> ![](https://i.imgur.com/URJXI7T.png)

2. **Verifique o status do repositório:**

   ```bash
   git status
   ```

   > *Observe que o arquivo  `Turma.py` aparecem em vermelho como "untracked".*
   >
   > ![](https://i.imgur.com/tOgouzw.png)
   >
   > Note que apareceu uma letra **U** ao lado do arquivo **Turma.py**, indicando que se trata de um novo arquivo, que ainda não foi versionado (**Untracked**)
   >
   > ![](https://i.imgur.com/aj6NITj.png)

3. **Adicione os arquivos para a Staging Area:**

   ```bash
   git add .
   ```

4. **Verifique o status novamente:**

   ```bash
   git status
   ```

   > *O arquivo agora aparece em verde, prontos para o commit.*
   >
   > ![](https://i.imgur.com/ZMxUp5R.png)

5. **Faça o primeiro commit:**

   ```bash
   git commit -m "Commit inicial: arquivo Turma.py"
   ```

<br />

> [!NOTE]
>
> ### Tipos de Commits
>
> | **Tipo**               | **Descrição**                                                | **Exemplo de Mensagem**                                      |
> | ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
> | **`init` / `initial`** | **Commit Inicial:** Cria a estrutura base do projeto, o repositório do zero e os arquivos fundamentais inicializadores. | `init: commit inicial do projeto` *ou* `feat: initial commit` |
> | **`feat`**             | **Funcionalidade:** Adiciona um novo recurso ou funcionalidade ao sistema. | `feat: adiciona autenticação por token JWT`                  |
> | **`fix`**              | **Correção:** Corrige um erro, falha ou bug no código.       | `fix: corrige validação de e-mail no formulário`             |
> | **`docs`**             | **Documentação:** Alterações exclusivamente na documentação (ex: README.md, wiki). | `docs: atualiza instruções de instalação no README`          |
> | **`style`**            | **Estilização/Formatação:** Mudanças de formatação que não alteram a lógica do código (espaços, indentação, ponto e vírgula). | `style: ajusta indentação do arquivo main.py`                |
> | **`refactor`**         | **Refatoração:** Mudança de estrutura do código sem alterar seu comportamento nem corrigir bugs. | `refactor: simplifica lógica da função de cálculo`           |
> | **`test`**             | **Testes:** Adição, alteração ou criação de testes automatizados. | `test: adiciona testes unitários para rota de login`         |
> | **`chore`**            | **Tarefas Diversas:** Atualizações de dependências, tarefas de build, ajustes de `.gitignore` ou configurações gerais. | `chore: atualiza dependências do arquivo requirements.txt`   |
> | **`perf`**             | **Performance:** Alterações focadas estritamente em melhorar o desempenho do código. | `perf: otimiza consulta SQL da busca de usuários`            |
> | **`ci`**               | **Integração Contínua:** Modificações nos fluxos de automação/CI/CD (ex: GitHub Actions, GitLab CI). | `ci: adiciona pipeline de teste automatizado`                |
> | **`revert`**           | **Reversão:** Desfaz/reverte um commit que foi realizado anteriormente. | `revert: desfaz commit de funcionalidade de relatórios`      |

<br />

6. Digite o comando abaixo para visualizar o histórico de commits:

```bash
git log
```

> *Será exibida a lista de commits do repositório:*
>
> ![](https://i.imgur.com/il77UgH.png)

---

## Passo 4: Modificando Arquivos e Visualizando Alterações

1. Adicione uma nova linha ao arquivo `Turma.py`:

   ```python
   print("Nova funcionalidade adicionada")
   ```

2. **Compare as alterações feitas em relação ao último commit:**

   ```bash
   git diff
   ```

   > Na imagem abaixo, vemos o antes e o depois das alterações:
   >
   > ![](https://i.imgur.com/agvVUv4.png)

3. Adicione o arquivo modificado na ***Stage Area*** e faça um novo commit:

   ```bash
   git add Turma.py
   git commit -m "feat: adiciona mensagem de nova funcionalidade no arquivo Turma.py"
   ```

4. Digite o comando abaixo para visualizar o histórico de commits:

```bash
git log
```

> *Será exibida a lista atualizada de commits do repositório:*
>
> ![](https://i.imgur.com/yiXL8Hr.png)

---

## Passo 5: Desfazendo um Commit com `git revert`

Às vezes um commit já foi feito e depois percebemos que ele estava errado. O `git revert` desfaz o efeito desse commit **criando um novo commit** com a alteração inversa. 

O commit original continua no histórico, e por isso o `revert` é a forma segura de desfazer algo, inclusive depois de enviar o código ao GitHub.

### 5.1 Criando um commit com erro

1. Adicione uma linha indesejada ao `Turma.py` 

```python
print("Linha com erro")
```

2. faça o commit junto com o add:

```bash
git commit -a -m "feat: adiciona linha com erro no arquivo Turma.py"
```

>  a opção `-a` funciona apenas para arquivos que já estão sendo versionados e foram modificados ou excluídos. Para adicionar **arquivos novos** ao staging, é necessário utilizar `git add`.

3. Veja o histórico de forma compacta:

```bash
git log --oneline
```

> *O commit "adiciona linha com erro" aparece no topo da lista. Para sair da listagem, caso seja necessário, pressione **q**.*
>
> ![](https://i.imgur.com/XAVAWVG.png)

### 5.2 Revertendo o commit

1. Desfaça o último commit:

   ```bash
   git revert HEAD --no-edit
   ```

   > *`HEAD` representa o commit mais recente. A opção `--no-edit` aceita a mensagem automática e evita que o Git abra um editor de texto.*
   
2. Confira o resultado:

   ```bash
   type main.py
   git log --oneline
   ```

   > *A linha com erro desapareceu do arquivo. No histórico, o commit original continua lá e acima dele surgiu um novo commit com a mensagem `Revert "feat: adiciona linha com erro no arquivo Turma.py"`.*
   >
   > ![](https://i.imgur.com/ZYIVAFC.png)

### 5.3 Revertendo um commit mais antigo

Para desfazer um commit que não é o último, informe o identificador (hash) dele, que aparece no `git log --oneline`:

```bash
git revert <hash> --no-edit
```

> *Substitua `<hash>` pelos primeiros caracteres do commit, por exemplo `fa6f16f`, destacado na imagem abaixo.*
>
> ![](https://i.imgur.com/EoWfKsr.png)

<br />

> [!NOTE]
>
> - O `revert` **não apaga** o histórico. Ele acrescenta um novo commit, o que o torna seguro em repositórios compartilhados.
> - Se alterações posteriores mexerem nas mesmas linhas do commit revertido, o Git pode pedir que o conflito seja resolvido manualmente. Isso fica para uma próxima etapa.
> - Esse é o tipo `revert` da tabela "Tipos de Commits".

### Resumo

| Situação                          | Comando                      | O que acontece                                   |
| :-------------------------------- | :--------------------------- | :----------------------------------------------- |
| Desfazer o **último** commit      | `git revert HEAD --no-edit`  | Cria um novo commit que anula o anterior.        |
| Desfazer um commit **específico** | `git revert <hash> --no-edit`| Cria um novo commit que anula o commit indicado. |

---

## Passo 6: Conectando com o GitHub e Enviando o Código

1. Acesse a sua conta no **GitHub**, clique no botão **"+"** (canto superior direito) → **New repository**.

![](https://i.imgur.com/WJT0B3Y.png)

2. Dê o nome de `aula_git`. **Não** marque as opções de criar README, .gitignore ou Licença. Clique em **Create repository**.

![](https://i.imgur.com/VaFxHmC.png)

3. Copie a URL do repositório gerado (exemplo: `https://github.com/seu-usuario/aula_git.git`).

![](https://i.imgur.com/1hxmhAo.png)

4. Volte ao Git Bash e vincule o repositório local ao remoto:

```bash
git remote add origin https://github.com/seu-usuario/aula_git.git
```

> *Substitua `seu-usuario` pelo seu usuário do GitHub.*

5. Para confirmar o vínculo, utilize o comando abaixo:

```bash
git remote -v
```

> Será exibida a mensagem abaixo, confirmando a conexão com o repositório remoto:
>
> ![](https://i.imgur.com/thksDnr.png)

6. **Envie os dados ao GitHub:**

```bash
git push origin main
```

> *Na primeira vez, o Windows abrirá a janela abaixo pedindo para autenticar sua conta do GitHub.*
>
> ![](https://i.imgur.com/B2gBUFM.png)
>
> 1. Clique no botão **Sign in with your browser** 
> 2. Você será redirecionado para o navegador 
> 3. Informe suas credenciais (usuário e senha) 
> 4. Autorize a conexão da sua máquina com o GitHub
> 5. Após concluir o processo de autenticação e autorizar o acesso ao repositório, volte para o terminal e refaça push.

7. Digite o comando abaixo para visualizar o histórico de commits atualizados:

```bash
git log --oneline
```

> *O histórico enviado inclui todos os commits, inclusive o commit de reversão.*

8. Volte no repositório do GitHub e atualize a página para visualizar os arquivos enviados.

<br />

> [!WARNING]
>
> Observe que a pasta `docs` não foi versionada porque ela está vazia. O Git versiona apenas pastas com conteúdo.

<br />

---

## Passo 7: Simulando Alterações Remotas e Baixando com `git pull`

1. No **GitHub**, abra o arquivo `Turma.py` em modo de edição, clicando no **lápis (Edit)**:

2. Adicione a linha: `print("Atualização Remota!")` no final do arquivo e faça o commit direto pelo site no botão **Commit changes...**.

3. O **GitHub** irá sugerir uma mensagem para o seu commit. Clique em **Commit changes** para concluir

4. Volte ao seu **Git Bash** e atualize o seu repositório local com as alterações realizadas no GitHub:

```bash
git pull origin main
```

5. Visualize o conteúdo do arquivo `Turam.py` no VSCode e observe que ele foi atualizado com sucesso.

6. Digite o comando abaixo para visualizar o histórico de commits atualizados:

```bash
git log --oneline
```

> Observe que o commit feito no GitHub agora faz parte do histórico do seu repositório local
>

---

## Comandos Utilizados

| Comando                       | Descrição                                                    |
| :---------------------------- | :----------------------------------------------------------- |
| `git version`                 | Exibe a versão do Git instalada.                             |
| `git config`                  | Consulta e define as configurações do Git (nome, e-mail, branch padrão e estratégia de pull). |
| `git init`                    | Inicializa o repositório Git local.                          |
| `git status`                  | Exibe o estado atual dos arquivos (modificados, staged, untracked). |
| `git add <arquivo>`           | Adiciona alterações à área de preparação (Staging Area).     |
| `git commit -m "msg"`         | Salva as alterações na linha do tempo local com uma mensagem. |
| `git diff`                    | Mostra as alterações feitas desde o último commit.           |
| `git log`                     | Exibe o histórico de commits.                                |
| `git log --oneline`           | Exibe o histórico de commits de forma compacta.              |
| `git revert <hash>`           | Desfaz um commit criando um novo commit com a alteração inversa. |
| `git remote add origin <url>` | Conecta o repositório local ao repositório remoto no GitHub. |
| `git remote -v`               | Lista os repositórios remotos vinculados.                    |
| `git push origin main`        | Envia os commits locais para o servidor remoto no GitHub.    |
| `git pull origin main`        | Baixa e aplica as alterações do repositório remoto na máquina local. |
