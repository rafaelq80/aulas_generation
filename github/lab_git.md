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

Nesta tarefa vamos criar o ambiente inicial do laboratório.

 1. Crie a pasta principal do laboratório (`aula_git`), dentro da pasta pessoal do usuário (`Home Directory`)

```bash
mkdir aula_git
```

2. Para validar a criação execute:

```bash
ls
```

3. Acesse a pasta criada

```bash
cd aula_git
```

4. Para validar execute:

```bash
pwd
```

5. Crie a estrutura inicial do projeto

```bash
mkdir src docs
```

6. Para validar execute:

```bash
ls
```

7. Resultado esperado:

```text
docs
src
```



## Tarefa 2 - Inicializar um repositório Git

Nesta tarefa vamos transformar a pasta do projeto em um repositório Git.

 1. Inicialize o repositório

```bash
git init
```

 2. Observe que ao lado do nome da pasta (`aula_git`), será exibida a palavra **`(main)`**, indicando que a pasta foi versionada pelo git  e você está na Branch Principal (`main`).

![](https://i.imgur.com/NnXve9T.png)

> Caso esteja aparecendo **`master`**, significa qe você esqueceu de configurar o nome da branch principal.
>
> Verifique o CookBook do Git e faça a alteração.

3. Verifique o status atual do repositório

```bash
git status
```

4. Visualize os arquivos ocultos do projeto

```bash
ls -la
```

Observe a existência da pasta `.git`.

```bash
./  ../  .git/  docs/  src/
```



## Tarefa 3 - Criar e versionar arquivos

Nesta tarefa vamos criar os primeiros arquivos do projeto e registrar alterações.

 1. Crie os arquivos iniciais

```bash
touch README.md
touch src/app.js
touch docs/manual.md
```

2. Para validar execute:

```bash
find .
```

3. Verifique o status do repositório

```bash
git status
```

4. Observe que você tem arquivos para serem versionados

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

5. Adicione todos os arquivos na área de preparação (Stage Area)

```bash
git add .
```

6. Verifique novamente o status

```bash
git status
```

7. Observe que os seus arquivos foram adicionados na área de preparação (Stage Area) e estão aguardando o commit:

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

8. Crie o primeiro commit

```bash
git commit -m "Meu Primeiro commit"
```

> [!NOTE]
>
> **-m** indica que você irá adicionar uma mensagem de identificação do commit

9. Consulte o histórico

```bash
git log
```

10. Observe que o commit foi criado:

```bash
commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit

```



## Tarefa 4 - Consultar histórico

Nesta tarefa vamos consultar os commits realizados.

 1. Liste o histórico completo

```bash
git log
```

 2. Liste o histórico resumido

```bash
git log --oneline
```

 3. Exiba o histórico em formato gráfico

```bash
git log --oneline --graph
```

 4. Exiba o histórico com informações adicionais

```bash
git log --oneline --decorate
```



## Tarefa 5 - Trabalhar com alterações

Nesta tarefa vamos modificar arquivos e acompanhar as alterações realizadas.

 1. Adicione conteúdo ao README.md

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

4. Observe que você tem arquivos atualizados para serem versionados

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

7. Adicione a alteração à área de preparação

```bash
git add README.md
```

8. Verifique o status do repositório

```bash
git status
```

9. Observe que as alterações foram adicionadas na área de preparação:

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." t
o unstage)
        modified:   README.md

```

> [!IMPORTANT]
>
> Desta vez não faremos o commit para entender como desfazer as alterações que ainda não foram adicionadas na área de preparação



## Tarefa 6 - Desfazer alterações com restore

Nesta tarefa vamos praticar formas seguras de desfazer alterações locais.

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
Linha temporária

```

4. Verifique o status do repositório

```bash
git status
```

5. Observe que agora temos a primeira alteração na área de preparação e a segunda alteração esperando para ser adicionada:

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

6. Desfaça as alterações realizadas no arquivo

```bash
git restore README.md
```

7. Para validar execute:

```bash
cat README.md
```

> [!NOTE]
>
> A segunda linha adicionada no arquivo **README.md** será apagada e o arquivo voltará a ter apenas uma linha

<br />

> [!TIP]
>
> O comando `git restore` descarta alterações que ainda não foram adicionadas à área de preparação.

<br />

8. Adicione uma nova alteração ao README.md

```bash
echo "Nova alteração" >> README.md
```

9. Adicione o arquivo à área de preparação

```bash
git add README.md
```

10. Verifique o status do repositório

```bash
git status
```

11. Remova o arquivo da área de preparação

```bash
git restore --staged README.md
```

12. Para validar execute:

```bash
git status
```

> [!NOTE]
>
> O comando remove o arquivo da área de preparação, mas mantém as alterações no arquivo.

13. Adicione novamente o arquivo à área de preparação

```bash
git add README.md
```

14. Crie um commit

```bash
git commit -m "Atualização - README"
```

 10. Consulte o histórico

```bash
git log
```

11. Observe que agora você possui 2 commits:

```bash
commit 40fd49b905d33c6bc7e0349dd5ea06f1ed
5b6881 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:53:02 2026 -0300

    Atualização - README

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
echo "Manual do Git" > docs/manual.md
```

2. Para validar execute:

```bash
 cat docs/manual.md
```

3. Verifique o status do repositório

```bash
git status
```

4. Observe que você tem arquivos atualizados para serem versionados
5. Adicione a alteração à área de preparação

```bash
git add .
```

> [!TIP]
>
> Ao utilizar o ponto no final do comando `git add`, você está informando que todos os arquivos criados ou atualizados dentro do repositório devem ser adicionados na área de preparação.

6. Verifique o status do repositório

```bash
git status
```

7. Observe que o arquivo **manual.md** foi adicionado na área de preparação (Stage Area) e está aguardando o commit.
8. Faça o commit 

```bash
git commit -m "Atualização - manual.md"
```

9. Consulte o histórico

```bash
git log
```

10. Observe que agora você possui 3 commits:

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

    Atualização - README

commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

```

> [!TIP]
>
> Para sair do `git log`, pressione a tecla **q** do seu teclado



### 7.1. Desfazer um commit no modo Soft



11. Desfaça o último commit mantendo as alterações preparadas

```bash
git reset --soft HEAD~1
```

12. Para validar execute:

```bash
git status
```

13. Observe que o arquivo **manual.md** voltou para a área de preparação (Stage Area) e está aguardando o commit novamente.
14. Consulte o histórico

```bash
git log
```

15. Observe que o repositório voltou a ter apenas 2 commits:

```bash
commit 40fd49b905d33c6bc7e0349dd5ea06f1ed
5b6881 (HEAD -> main)
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:53:02 2026 -0300

    Atualização - README

commit cc0aac5ea06bf70feec3cd15858aac9621
4e6280
Author: Rafael Queiroz <rafaelproinfo@gma
il.com>
Date:   Wed Jun 10 02:35:11 2026 -0300

    Meu Primeiro commit

```



### 7.2. Desfazer um commit removendo da Stage Area



16. Crie novamente o commit

```bash
git commit -m "Atualização - manual.md"
```

17. Desfaça o último commit removendo-o da área de preparação

```bash
git reset HEAD~1
```

18. Para validar execute:

```bash
git status
```

19. Observe que além de desfazer o commit, o arquivo saiu da área de preparação:

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



20. Adicione e Crie novamente o commit

```bash
git commit -a -m "Atualização - manual.md"
```

> [!NOTE]
>
> A opção **-a** incorpora o `git add` ao comando `git commit`. Esta opção aplica-se apenas a arquivos já rastreados pelo Git (arquivos existentes), não funcionando para novos arquivos.

21. Desfaça o último commit desfazendo todas as alterações

```bash
git reset --hard HEAD~1
```

22. Para validar execute:

```bash
git status
```

23. Observe que, além de remover o commit do histórico, todas as alterações foram descartadas, restaurando o repositório exatamente ao estado do segundo commit.
24. Para validar, execute o comando:

```bash
 cat docs/manual.md
```

25. Observe que o arquivo **manual.md** está vazio!

> [!WARNING]
>
> Evite utilizar `git reset` em commits que já foram enviados para repositórios compartilhados.



## Tarefa 8 - Trabalhar com branches

Nesta tarefa vamos criar e utilizar branches.

 1. Liste as branches existentes

```bash
git branch
```

 2. Crie uma branch chamada desenvolvimento

```bash
git branch desenvolvimento
```

 3. Liste novamente as branches

```bash
git branch
```

 4. Acesse a branch desenvolvimento

```bash
git checkout desenvolvimento
```

 5. Verifique a branch atual

```bash
git branch
```

 6. Crie um novo arquivo

```bash
touch src/config.js
```

7. Para validar execute:

```bash
ls src
```

8. Adicione as alterações

```bash
git add .
```

9. Crie um commit

```bash
git commit -m "Adiciona config.js"
```



## Tarefa 9 - Realizar merge

Nesta tarefa vamos unir alterações entre branches.

 1. Retorne para a branch principal

```bash
git checkout main
```

> [!NOTE]
>
> Caso sua branch principal seja `master`, utilize:
>
> ```bash
> git checkout master
> ```

 2. Realize o merge da branch desenvolvimento

```bash
git merge desenvolvimento
```

 3. Consulte o histórico em formato gráfico

```bash
git log --oneline --graph
```

 4. Verifique os arquivos do projeto

```bash
find .
```



## Tarefa 10 - Trabalhar com repositórios remotos

Nesta tarefa vamos conectar o projeto ao GitHub.

 1. Crie um repositório vazio no GitHub chamado **aula_git**. Não marque nenhuma opção de inicialização.

 2. Adicione o repositório remoto. Substitua a URL abaixo pela URL do seu repositório.

```bash
git remote add origin https://github.com/usuario/repositorio.git
```

 3. Verifique os repositórios remotos configurados

```bash
git remote -v
```



## Tarefa 11 - Enviar alterações para o GitHub

Nesta tarefa vamos publicar o projeto no GitHub.

 1. Envie os commits para o repositório remoto

```bash
git push origin main
```

> [!NOTE]
>
> Caso utilize a branch `master`, substitua `main` por `master`.

 2. Consulte o repositório no GitHub. Verifique se os arquivos foram enviados corretamente.

 3. Consulte o histórico local

```bash
git log --oneline
```



## Tarefa 12 - Atualizar o repositório local

Nesta tarefa vamos obter alterações realizadas no GitHub.

 1. Realize uma alteração diretamente no GitHub. Edite o arquivo README.md pela interface web.

 2. Atualize o repositório local

```bash
git pull
```

 3. Consulte o histórico

```bash
git log --oneline
```

 4. Visualize o conteúdo atualizado

```bash
cat README.md
```

> [!NOTE]
>
> O comando `git pull` executa internamente um `git fetch` seguido de um `git merge`.



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
explorer index.html
```

7. Você verá no seu navegador o site abaixo:

![](https://i.imgur.com/lcBqr86.png)



## Desafio Final

Nesta atividade você deverá criar um novo projeto aplicando os conceitos aprendidos.

 1. Crie uma pasta chamada projeto_final, na pasta do usuário

 2. Inicialize um repositório Git

 3. Crie os diretórios

```text
src
docs
tests
```

 4. Crie os arquivos

```text
README.md
src/app.js
docs/manual.md
tests/app.test.js
```

 5. Realize o primeiro commit

 6. Crie uma branch chamada feature-login

 7. Adicione um arquivo chamado login.js

 8. Realize um commit na branch feature-login

 9. Faça merge da branch feature-login na branch principal

 10. Envie o projeto para um repositório GitHub

 11. Consulte o histórico em formato gráfico





