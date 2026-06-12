# Laboratório Prático de Git e GitHub com Git Bash

## Introdução

Neste laboratório você utilizará o Git Bash para praticar os principais comandos do Git e compreender o fluxo básico de versionamento utilizado em projetos de software.

Todas as atividades serão realizadas dentro da pasta `aula_git`, evitando alterações em outros projetos existentes na máquina.

Ao final deste laboratório você terá criado um repositório Git local, realizado commits, trabalhado com branches, utilizado recursos de restauração, integrado o projeto ao GitHub e sincronizado alterações entre repositórios locais e remotos.



## Pré-requisitos

* Windows com Git Bash instalado.
* Conta no GitHub.
* Conhecimentos básicos de navegação em diretórios.
* Conexão com a internet para as atividades envolvendo o GitHub.



## Tarefa 1 - Criar a estrutura do laboratório

Nesta tarefa vamos criar o ambiente inicial do laboratório, como vemos no diagrama abaixo:

```
📦aula_git
 ┣ 📂docs
 ┗ 📂src
```

 1. Crie a pasta principal do laboratório (`aula_git`), dentro da pasta pessoal do usuário (`Home Directory`)

```bash
mkdir aula_git
```

2. Acesse a pasta criada

```bash
cd aula_git
```

3. Crie a estrutura inicial do projeto

```bash
mkdir src docs
```

4. Para validar execute:

```bash
ls
```

5. Resultado esperado:

```bash
docs/  src/
```



## Tarefa 2 - Inicializar um repositório Git

Nesta tarefa vamos transformar a pasta do projeto em um repositório Git.

 1. Inicialize o repositório

```bash
git init
```

 2. Observe que ao lado do nome da pasta (`aula_git`), será exibida a palavra **`(main)`**, indicando que a pasta foi versionada pelo git  e você está na Branch Principal (`main`).

![](https://i.imgur.com/NnXve9T.png)

> [!TIP]
>
> Caso esteja aparecendo **`master`** em vez de **`main`**, provavelmente o nome da branch principal ainda não foi configurado. 
>
> 1. Para configurar o nome da branch principal como main, utilize o comando abaixo:
>
> ```bash
> git config --global init.defaultBranch main
> ```
>
> 2. Esta alteração será aplicada nos próximos repositórios que você criar.
> 3. Para renomear a branch master para main, utilize o comando abaixo:
>
> ```bash
> git branch -m main
> ```

3. Verifique o status atual do repositório

```bash
git status
```

4. Observe que neste momento você não possui arquivos para serem versionados

```bash
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

5. Visualize os arquivos ocultos do projeto

```bash
ls -la
```

6. Observe a existência da pasta oculta `.git`:

```bash
./  ../  .git/  docs/  src/
```

> [!WARNING]
>
> **Não modifique, renomeie ou exclua a pasta `.git`.**
>
> Ela contém todas as informações de controle de versão do repositório. Alterações indevidas podem comprometer o funcionamento do Git e causar perda do histórico do projeto.



## Tarefa 3 - Criar e versionar arquivos

Nesta tarefa vamos criar os primeiros arquivos do projeto e registrar alterações, como vemos no diagrama abaixo:

```
📦aula_git
 ┣ 📂docs
 ┃ ┗ 📜manual.md
 ┣ 📂src
 ┃ ┗ 📜app.js
 ┗ 📜README.md
```

 1. Crie os arquivos iniciais

```bash
touch README.md src/app.js docs/manual.md
```

2. Para validar execute:

```bash
find . -not -path '*/.*'
```

> [!NOTE]
>
> A opção `-not -path '*/.*'`, utilizada no comando `find`, exclui da busca arquivos e diretórios ocultos, como a pasta `.git`, exibindo apenas os elementos visíveis da estrutura.

3. Observe que os 3 arquivos foram criados nas respectivas pastas

```bash
.
./README.md
./docs
./docs/manual.md
./src
./src/app.js
```

4. Verifique o status do repositório

```bash
git status
```

5. Observe que o Git identificou arquivos que podem ser adicionados à Área de Preparação (Staging Area) para posterior versionamento:

```bash
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in
what will be committed)
        README.md
        docs/
        src/

nothing added to commit but untracked fil
es present (use "git add" to track)

```

6. Adicione todos os arquivos na área de preparação (Stage Area)

```bash
git add .
```

7. Verifique novamente o status

```bash
git status
```

8. Observe que os arquivos foram adicionados à **Área de Preparação (Staging Area)** e estão prontos para serem incluídos no próximo commit:

```bash
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to uns
tage)
        new file:   README.md
        new file:   docs/manual.md
        new file:   src/app.js

```

9. Crie o primeiro commit

```bash
git commit -m "Meu Primeiro commit"
```

> [!NOTE]
>
> **-m** indica que você irá adicionar uma mensagem de identificação do commit

<br />

> [!TIP]
>
> Caso seja exibida a mensagem abaixo, informando que as credenciais da sua conta no GitHub não foram configuradas:
>
> ```bash
> Author indentity unknown
> 
> *** Please tell me who you are.
> 
> Run
> 
> 	git config --global user.email "you@example.com"
> 	git config --global user.name "Your Name"
> 
> to set your account's default identity.
> Omit --global to set the identity only in this repository.
> 
> fatal: unable to auto-detect email address (got 'rafae@DESKTOP-5GMTGK4.(none)')
> ```
>
> 1. Configure o seu **nome** no Git, através do comando:
>
> ```bash
> git config --global user.name "seu_mome"
> ```
>
> > *Substitua seu_nome, pelo seu nome completo. Exemplo: João da Silva*
>
> 2. Configure o seu **e-mail** no Git, através do comando:
>
> ```
> git config --global user.email "seu_email@email.com"
> ```
>
> > *Substitua seu_email, pelo endereço do e-mail que você utilizou para criar a sua conta no Github. Exemplo: **joao@email.com.br***
>
> 3. Para checar se as configurações foram efetuadas com sucesso, digite o comando:
>
> ```
> git config --list 
> ```
>
> > 💡 Para sair da listagem do comando, caso seja necessário, pressione a letra **q** do seu teclado.
>
> 4. Na sequência, refaça o commit!

10. Consulte o histórico

```bash
git log
```

11. Observe que o primeiro commit foi criado:

```bash
commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit

```



## Tarefa 4 - Trabalhar com alterações

Nesta tarefa vamos modificar um arquivo e acompanhar as alterações realizadas.

 1. Adicione conteúdo no arquivo README.md

```bash
echo "# Projeto Git" > README.md
```

2. Para validar execute:

```bash
cat README.md
```

3. Verifique o status do repositório

```bash
git status
```

4. Observe que o Git identificou arquivos atualizados que podem ser adicionados à Área de Preparação (Staging Area) para posterior versionamento:

```bash
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what
 will be committed)
  (use "git restore <file>..." to discard
 changes in working directory)
        modified:   README.md

no changes added to commit (use "git add"
 and/or "git commit -a")

```

5. Visualize as alterações realizadas

```bash
git diff
```

6. Observe que o comando `git diff` mostra todas as alterações que foram realizadas em relação ao ultimo commit:

```bash
warning: in the working copy of 'README.m
d', LF will be replaced by CRLF the next
time Git touches it
diff --git a/README.md b/README.md
index e69de29..777c2ce 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# Projeto Git

```

7. Adicione o arquivo à área de preparação

```bash
git add README.md
```

8. Verifique o status do repositório

```bash
git status
```

9. Observe que todos os arquivos foram adicionadas na área de preparação:

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." t
o unstage)
        modified:   README.md

```

> [!IMPORTANT]
>
> Desta vez não criaremos um commit. Antes disso, vamos entender como desfazer alterações que ainda não foram registradas no histórico do repositório.



## Tarefa 5 - Desfazer alterações com restore

Nesta tarefa vamos praticar formas seguras de desfazer alterações locais antes que elas sejam registradas em um commit.

 1. Adicione uma nova linha ao README.md

```bash
echo "Linha temporária" >> README.md
```

2. Para validar execute:

```bash
cat README.md
```

3. Observe que a nova linha foi adicionada logo abaixo da primeira linha:

```bash
# Projeto Git
## Linha temporária
```

4. Verifique o status do repositório

```bash
git status
```

5. Observe que o arquivo possui duas alterações em estados diferentes: 
   - A primeira, já foi adicionada à **Área de Preparação (Staging Area)**
   - A segunda continua apenas no diretório de trabalho aguardando ser adicionada na **Área de Preparação (Staging Area)**.

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." t
o unstage)
        modified:   README.md

Changes not staged for commit:
  (use "git add <file>..." to update what
 will be committed)
  (use "git restore <file>..." to discard
 changes in working directory)
        modified:   README.md

```

6. Descarte as alterações efetuadas no arquivo README.md, que ainda não foram adicionadas à Área de Preparação (Staging Area).

```bash
git restore README.md
```

7. Para validar execute:

```bash
cat README.md
```

8. Observe que o comando restaurou o arquivo para o estado presente na Área de Preparação.

```bash
# Projeto Git
```

> [!TIP]
>
> O comando `git restore` descarta alterações que ainda não foram adicionadas à área de preparação.

9. Verifique o status do repositório

```bash
git status
```

10. Observe que a primeira alteração foi mantida na **Área de Preparação (Staging Area)**, enquanto a segunda alteração, que ainda não havia sido adicionada à área de preparação, foi descartada.

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." t
o unstage)
        modified:   README.md

```

11. Adicione uma nova alteração no arquivo README.md

```bash
echo "## Funcionalidades do Projeto" >> README.md
```

12. Adicione novamente o arquivo à **Área de Preparação (Staging Area)**

```bash
git add README.md
```

13. Remova o arquivo da **Área de Preparação (Staging Area)**, mantendo as alterações realizadas no arquivo.

```bash
git restore --staged README.md
```

14. Para validar execute:

```bash
git status
```

15. Observe que o arquivo foi removido da **Área de Preparação (Staging Area)**, porém as alterações continuam disponíveis e podem ser adicionadas novamente quando necessário.

```bash
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be
committed)
  (use "git restore <file>..." to discard changes
in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "
git commit -a")
```



## Tarefa 6 - Alterar múltiplos arquivos

Nesta tarefa vamos modificar vários arquivos e acompanhar as alterações realizadas.

1. Adicione uma alteração no arquivo manual.md

```bash
echo "# Manual do Projeto Git" > docs/manual.md
```

2. Adicione uma alteração no arquivo app.js

```bash
echo "console.log('Hello World')" > src/app.js
```

3. Adicione os arquivos à área de preparação

```bash
git add .
```
> [!TIP]
>
> Ao utilizar o ponto no final do comando `git add`, você está informando que todos os arquivos criados, atualizados ou removidos do repositório (incluindo as subpastas) devem ser adicionados na área de preparação.
> 

4. Verifique o status do repositório

```bash
git status
```

5. Observe que as alterações realizadas nos três arquivos foram adicionadas à **Área de Preparação (Staging Area)** e estão prontas para serem incluídas no próximo commit.

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage
)
        modified:   README.md
        modified:   docs/manual.md
        modified:   src/app.js
```

6. Faça o commit

```bash
git commit -m "Atualização dos arquivos: README.md manual.md e app.js"
```

7. Consulte o histórico

```bash
git log
```

8. Observe que agora você possui 2 commits:

```bash
commit 40fd49b905d33c6bc7e0349dd5ea06f1ed
5b6881 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:53:02 2026 -0300

     Atualização dos arquivos: README.md manual.md
e app.js

commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit

```



## Tarefa 7 - Desfazer commits

Nesta tarefa vamos conhecer formas de desfazer commits locais.

  1. Adicione conteúdo no arquivo manual.md, localizado na pasta docs

```bash
echo "## Introdução" >> docs/manual.md
```

2. Adicione a alteração à área de preparação

```bash
git add .
```

3. Faça o commit 

```bash
git commit -m "Atualização do arquivo manual.md"
```

4. Consulte o histórico

```bash
git log
```

5. Observe que agora você possui 3 commits:

```bash
commit b2cfc8e9aa247e1729f520ef0b20945467
64a03f (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 03:03:50 2026 -0300

    Atualização - manual.md

commit 40fd49b905d33c6bc7e0349dd5ea06f1ed
5b6881 
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:53:02 2026 -0300

     Atualização dos arquivos: README.md manual.md
e app.js

commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit
```

> [!TIP]
>
> O comando `git log` abre um visualizador interativo. Caso você não consiga retornar ao terminal após executar o comando, pressione a tecla **q** para sair da visualização.



### 7.1. Desfazer um commit no modo Soft

Nesta etapa vamos aprender como desfazer um commit sem perder o trabalho realizado.

1. Desfaça o último commit mantendo todas as alterações na **Área de Preparação (Staging Area)**

```bash
git reset --soft HEAD~1
```

> [!TIP]
>
> A flag `HEAD` representa o commit atual, ou seja, o ponto em que o repositório se encontra no momento.
>
> A notação `~` permite navegar pelos commits anteriores:
>
> - `HEAD~1` → commit imediatamente anterior ao atual.
> - `HEAD~2` → dois commits antes do atual.
> - `HEAD~3` → três commits antes do atual.
> - `HEAD~4` → quatro commits antes do atual.

<br />

> [!WARNING]
>
> Na maioria dos cenários do dia a dia, **o mais adequado é utilizar `HEAD~1`, revertendo apenas o último commit**. A reversão de múltiplos commits deve ser realizada com cautela, pois pode impactar diversas alterações e dificultar a reorganização do histórico.

2. Para validar execute:

```bash
git status
```

3. Observe que o arquivo **manual.md** foi adicionado novamente à **Área de Preparação (Staging Area)** e está pronto para ser incluído no próximo commit.

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage
)
        modified:   docs/manual.md
```

4. Consulte o histórico

```bash
git log
```

5. Observe que o repositório voltou a ter apenas 2 commits:

```bash
commit 40fd49b905d33c6bc7e0349dd5ea06f1ed
5b6881 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:53:02 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit

```



### 7.2. Desfazer um commit removendo da Stage Area

Nesta etapa vamos aprender como desfazer um commit e retornar as alterações para o diretório de trabalho, permitindo que elas sejam revisadas antes de um novo commit.

1. Refaça o commit anterior

```bash
git commit -m "Atualização do arquivo manual.md"
```

2. Desfaça o último commit removendo-o da **Área de Preparação (Staging Area)**

```bash
git reset HEAD~1
```

3. Para validar execute:

```bash
git status
```

4. Observe que, além de desfazer o commit, o arquivo foi removido da **Área de Preparação (Staging Area)**. As alterações foram preservadas no diretório de trabalho e poderão ser adicionadas novamente antes da criação de um novo commit.

```bash
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what
 will be committed)
  (use "git restore <file>..." to discard
 changes in working directory)
        modified:   docs/manual.md

no changes added to commit (use "git add"
 and/or "git commit -a")
```



### 7.3. Desfazer um commit no modo Hard

Nesta etapa vamos aprender como desfazer um commit e descartar completamente as alterações realizadas, retornando o repositório ao estado em que se encontrava antes do commit.

1. Adicione e Crie novamente o commit

```bash
git commit -a -m "Atualização do arquivo manual.md"
```

> [!NOTE]
>
> A opção **-a** incorpora o `git add` ao comando `git commit`. Esta opção **aplica-se apenas a arquivos já rastreados pelo Git (arquivos existentes), não funcionando para novos arquivos**.

2. Desfaça o último commit e descarte todas as alterações realizadas.

```bash
git reset --hard HEAD~1
```

3. Para validar execute:

```bash
git status
```

4. Observe que, além de remover o commit do histórico, todas as alterações realizadas foram descartadas. Com isso, o repositório retornou exatamente ao estado em que se encontrava após o segundo commit.

```bash
On branch main
nothing to commit, working tree clean
```

5. Para validar, execute o comando:

```bash
 cat docs/manual.md
```

6. Observe que o arquivo **manual.md** está com apenas uma linha

```bash
# Manual do Projeto Git
```

> [!WARNING]
>
> Evite utilizar `git reset` em commits que já foram enviados para repositórios compartilhados.



### 7.4. Desfazer um commit e registrar a reversão no histórico

Nesta etapa vamos aprender como desfazer os efeitos de um commit sem alterar o histórico do repositório. Para isso, utilizaremos o comando `git revert`, que cria um novo commit responsável por reverter as alterações realizadas anteriormente, mantendo um histórico completo e rastreável.

1. Adicione conteúdo no arquivo manual.md, localizado na pasta docs

```bash
echo "Laboratório Prático com os principais comandos do Git." >> README.md
```

2. Adicione a alteração à área de preparação

```bash
git add .
```

3. Faça o commit 

```bash
git commit -m "Nova atualização do arquivo README.md"
```

4. Desfaça o último commit e registre no histórico.

```bash
git revert HEAD
```

> [!TIP]
>
> Diferentemente do comando `git reset`, o comando `git revert` normalmente é utilizado apenas com `HEAD`, pois seu objetivo é desfazer o último commit por meio da criação de um novo commit de reversão.
>
> ```bash
> git revert HEAD
> ```
>
> A utilização da notação `~` é opcional e serve para indicar commits anteriores:
>
> - `HEAD` → último commit.
> - `HEAD~1` → penúltimo commit.
> - `HEAD~2` → antepenúltimo commit.
>
> Na maioria dos cenários, utiliza-se `git revert HEAD`, pois o objetivo geralmente é desfazer apenas o último commit sem alterar o histórico do repositório.

5. Será aberta uma janela do **Visual Studio Code** ou do editor padrão configurado no Git contendo a mensagem do commit de reversão. Revise a mensagem, salve o arquivo e feche o editor para concluir a operação.

```bash
Revert "Nova atualização do arquivo README.md"

This reverts commit f32edf69366235fc83ada4a2303a4369d57ad12e.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch main
# Changes to be committed:
#	modified:   README.md
#
```

> [!IMPORTANT]
>
> Enquanto a janela do do **Visual Studio Code** ou do editor padrão do Git não for fechada, o terminal ficará bloqueado aguardando a conclusão do commit de revrsão.

6. Para validar execute:

```bash
git status
```

7. Observe que o commit original foi mantido no histórico e um novo commit foi criado para registrar a reversão das alterações realizadas anteriormente.

```bash
On branch main
nothing to commit, working tree clean
```

8. Para validar, execute o comando:

```bash
 cat README.md
```

9. Observe que o arquivo **manual.md** está com apenas duas linhas

```bash
# Projeto Git
## Funcionalidades do Projeto
```

10. Consulte o histórico

```bash
git log
```

11. Observe que, diferentemente do git reset, o commit original foi mantido no histórico. Note que foi criado um novo commit que registra a reversão das alterações realizadas no terceiro commit.

```bash
commit 8a2fb1209d84596ae3af44083bc89e03c79f6eca (H
EAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:40:54 2026 -0300

    Revert "Nova atualização do arquivo README.md"

    This reverts commit f32edf69366235fc83ada4a230
3a4369d57ad12e.

commit f32edf69366235fc83ada4a2303a4369d57ad12e
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:34:32 2026 -0300

    Nova atualização do arquivo README.md

commit 8cc32bdba85d8319105fad43ad443f7741faac1d
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 00:57:54 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit 1a339aa485e68cf4b447389cbe31dcd886d00dc1
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Thu Jun 11 16:03:56 2026 -0300

    Meu Primeiro commit
```

> [!NOTE]
>
> ### Quando usar cada um?
>
> **Use `git revert` quando:**
>
> - O commit já foi enviado para o GitHub (`git push`).
> - Outras pessoas podem ter baixado o commit.
> - Você deseja preservar o histórico completo.
>
> **Use `git reset` quando:**
>
> - O commit ainda está apenas no seu repositório local.
> - Você deseja reescrever o histórico.
> - Está corrigindo erros antes de enviar para o GitHub.
>
> **Boa Prática**
>
> - Antes do **`git push`**, normalmente utiliza-se **`git reset`**. 
> - Após o **`git push`**, normalmente utiliza-se **`git revert`**.



## Tarefa 8 - Trabalhar com branches

Nesta tarefa vamos criar e utilizar branches.

 1. Liste as branches existentes

```bash
git branch
```

 2. Observe que o repositório possui apenas a branch **main**

```bash
* main
```

3. Crie uma branch chamada **nova_feature**

```bash
git checkout -b nova_feature
```

> [!TIP]
>
> O comando `git checkout -b` cria uma nova branch e, em seguida, realiza automaticamente a troca para ela, tornando-a a branch ativa do repositório.

4. Observe no prompt que a branch atual foi alterada para **nova_feature**

![](https://i.imgur.com/SOOdLvw.png)

5. Crie um novo arquivo dentro da branch **nova_feature**

```bash
touch src/config.js
```

6. Adicione o conteúdo abaixo no arquivo config.js

```bash
echo "const PORT=8080" > src/config.js
```

7. Adicione as alterações

```bash
git add .
```

8. Crie um commit

```bash
git commit -m "Construção do arquivo config.js"
```

9. Consulte o histórico

```bash
git log
```

10. Observe que as alterações foram realizadas apenas na branch **nova_feature**. A branch **main** permanece inalterada, apontando para o commit anterior e sem acesso às novas modificações.

```bash
commit 8141c1d3a4c74a9324d74e62057e12d533ad16a7 (H
EAD -> nova_feature)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 02:07:05 2026 -0300

    Construção do arquivo config.js

commit 8a2fb1209d84596ae3af44083bc89e03c79f6eca (m
ain)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:40:54 2026 -0300

    Revert "Nova atualização do arquivo README.md"

    This reverts commit f32edf69366235fc83ada4a230
3a4369d57ad12e.

commit f32edf69366235fc83ada4a2303a4369d57ad12e
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:34:32 2026 -0300

    Nova atualização do arquivo README.md

commit 8cc32bdba85d8319105fad43ad443f7741faac1d
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 00:57:54 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit 1a339aa485e68cf4b447389cbe31dcd886d00dc1
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Thu Jun 11 16:03:56 2026 -0300

    Meu Primeiro commit

```



## Tarefa 9 - Realizar merge

Nesta tarefa vamos integrar as alterações realizadas em uma branch à branch principal por meio de uma operação de merge.

 1. Retorne para a branch principal

```bash
git checkout main
```

 2. Liste o conteúdo da pasta src

```bash
ls src
```

3. Observe que na branch main não existe o arquivo `config.js`

```bash
app.js
```

4. Realize o merge da branch main com a branch **nova_feature**

```bash
git merge nova_feature
```

5. Consulte o histórico

```bash
git log
```

6. Observe que, após o merge, as branches **main** e **nova_feature** passaram a apontar para o mesmo commit, indicando que as alterações realizadas na branch **nova_feature** foram incorporadas à branch **main**.

```bash
commit 8141c1d3a4c74a9324d74e62057e12d533ad16a7 (H
EAD ->  main, nova_feature)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 02:07:05 2026 -0300

    Construção do arquivo config.js

commit 8a2fb1209d84596ae3af44083bc89e03c79f6eca 
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:40:54 2026 -0300

    Revert "Nova atualização do arquivo README.md"

    This reverts commit f32edf69366235fc83ada4a230
3a4369d57ad12e.

commit f32edf69366235fc83ada4a2303a4369d57ad12e
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:34:32 2026 -0300

    Nova atualização do arquivo README.md

commit 8cc32bdba85d8319105fad43ad443f7741faac1d
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 00:57:54 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit 1a339aa485e68cf4b447389cbe31dcd886d00dc1
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Thu Jun 11 16:03:56 2026 -0300

    Meu Primeiro commit

```

7. Liste o conteúdo da pasta src

```bash
ls src
```

8. Note que o arquivo `config.js` foi criado na branch main

```bash
app.js  config.js
```



## Tarefa 10 - Trabalhar com repositórios remotos

Nesta tarefa vamos conectar o projeto ao GitHub.

  1. Crie um repositório vazio e público na sua conta do GitHub chamado **aula_git**.

![](https://i.imgur.com/hT7zzN6.png)

2. Copie o endereço **https** do repositório remoto

![](https://i.imgur.com/xFx4dYc.png)

3. Conecte o repositório local com o repositório remoto. 

```bash
git remote add origin https://github.com/rafaelq80/aula_git.git
```

> Substitua a URL **https://github.com/rafaelq80/aula_git.git** pela URL copiada do seu repositório no GitHub.

4. Verifique os repositórios remotos configurados

```bash
git remote -v
```

5. O resultado será:

```bash
origin  https://github.com/rafaelq80/aula_git.git
(fetch)
origin  https://github.com/rafaelq80/aula_git.git
(push)
```



## Tarefa 11 - Enviar alterações para o GitHub

Nesta tarefa vamos publicar o projeto no GitHub.

 1. Envie os commits para o repositório remoto

```bash
git push origin main
```

> [!NOTE]
>
> Observe que será enviado apenas o conteúdo da branch **main**. Para enviar a branch **nova_feature**, execute o comando:
>
> ```bash
> git push origin nova_feature
> ```

<br />

> [!TIP]
>
> Caso o Git ainda não esteja autenticado no GitHub, uma janela de login poderá ser exibida durante a execução do comando `git push`. 
>
> ![](https://i.imgur.com/vsRTAyD.png)
>
> 1. Clique no botão **Sign in with your browser** 
> 2. Você será redirecionado para o navegador 
> 3. Informe suas credenciais (usuário e senha) 
> 4. Autorize a conexão da sua máquina com o GitHub
> 5. Após concluir o processo de autenticação e autorizar o acesso ao repositório, volte para o terminal e refaça push.

  2. Volte no repositório no GitHub, atualize a página e verifique se os arquivos foram enviados corretamente.

![](https://i.imgur.com/2uu3EaI.png)

3. Consulte o histórico

```bash
git log
```

4. Observe que ambos os repositórios estão apontando para o mesmo commit

```bash
commit 8141c1d3a4c74a9324d74e62057e12d533ad16a7 (H
EAD ->  main,  origin/main, nova_feature)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 02:07:05 2026 -0300

    Construção do arquivo config.js

commit 8a2fb1209d84596ae3af44083bc89e03c79f6eca 
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:40:54 2026 -0300

    Revert "Nova atualização do arquivo README.md"

    This reverts commit f32edf69366235fc83ada4a230
3a4369d57ad12e.

commit f32edf69366235fc83ada4a2303a4369d57ad12e
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:34:32 2026 -0300

    Nova atualização do arquivo README.md

commit 8cc32bdba85d8319105fad43ad443f7741faac1d
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 00:57:54 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit 1a339aa485e68cf4b447389cbe31dcd886d00dc1
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Thu Jun 11 16:03:56 2026 -0300

    Meu Primeiro commit
```



## Tarefa 12 - Atualizar o repositório local

Nesta tarefa vamos obter alterações realizadas no GitHub.

  1. No repositório remoto, edite o arquivo README.md clicando no lápis

![](https://i.imgur.com/IWvE1Zr.png)

2. Adicione uma nova linha no arquivo

![](https://i.imgur.com/TdzYaRh.png)

3. Faça o commit

![](https://i.imgur.com/dd1D9TZ.png)

4. Observe que o arquivo README foi alterado

![](https://i.imgur.com/CKmoI01.png)

5. Para baixa as atualizações do repositório remoto sem aplicá-las localmente, execute o comando abaixo:

```bash
git fetch
```

6. Para visualizar as alterações, utilize o comando abaixo

```bash
git diff main origin/main
```

7. Observe que foi adicionada uma nova linha no arquivo README.md (`+## Requisitos do Projeto`):

```bash
diff --git a/README.md b/README.md
index 0a988cc..f39827d 100644
--- a/README.md
+++ b/README.md
@@ -1,3 +1,3 @@
 # Projeto Git
 ## Funcionalidades do Projeto
+## Requisitos do Projeto
```

8. Atualize o repositório local

```bash
git pull origin main
```

9. Consulte o histórico

```bash
git log
```

10. Observe que o novo commit criado no repositório remoto foi sincronizado com o repositório local, passando a fazer parte do histórico do projeto local.

```bash
commit 3a7391813918893e65fa69e3176acabac09db14c (H
EAD -> main, origin/main)
Author: Rafael Queiróz <60499241+rafaelq80@users.n
oreply.github.com>
Date:   Fri Jun 12 02:45:38 2026 -0300

    Atualização remota do README

commit 8141c1d3a4c74a9324d74e62057e12d533ad16a7 (nova_feature)
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 02:07:05 2026 -0300

    Construção do arquivo config.js

commit 8a2fb1209d84596ae3af44083bc89e03c79f6eca 
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:40:54 2026 -0300

    Revert "Nova atualização do arquivo README.md"

    This reverts commit f32edf69366235fc83ada4a230
3a4369d57ad12e.

commit f32edf69366235fc83ada4a2303a4369d57ad12e
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 01:34:32 2026 -0300

    Nova atualização do arquivo README.md

commit 8cc32bdba85d8319105fad43ad443f7741faac1d
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Fri Jun 12 00:57:54 2026 -0300

    Atualização dos arquivos: README.md manual.md
e app.js

commit 1a339aa485e68cf4b447389cbe31dcd886d00dc1
Author: Rafael Queiroz <rafaelproinfo@gmail.com>
Date:   Thu Jun 11 16:03:56 2026 -0300

    Meu Primeiro commit
```

11. Visualize o conteúdo atualizado

```bash
cat README.md
```

12. Observe que o conteúdo do arquivo README.md foi atualizado

```bash
# Projeto Git
## Funcionalidades do Projeto
## Requisitos do Projeto
```



## Tarefa 13 - Clonar um repositório

Nesta tarefa vamos criar uma cópia local de um repositório existente.

 1. Retorne para o diretório do usuário

```bash
cd ~
```

 2. Clone um repositório do GitHub. 

```bash
git clone https://github.com/rafaelq80/clone_github.git
```

 3. Liste os diretórios disponíveis

```bash
ls
```

 4. Acesse o diretório clonado

```bash
cd clone_github
```

 5. Verifique o status do repositório

```bash
git status
```

6. abra a página **index.html** no navegador (somente Windows):

```bash
start index.html
```

7. Você verá no seu navegador o site abaixo:

![](https://i.imgur.com/lcBqr86.png)
