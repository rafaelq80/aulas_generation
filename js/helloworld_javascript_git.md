<h1>Enviando o Projeto JavaScript para o Github</h1>



Vamos configurar o Repositório Local do Git e conectá-lo ao Repositório Remoto no Github. Desta forma, simplificaremos o processo de enviar os códigos criados em aula para o Github.

<br />

<h2>👣 Passo 01 - Criar o ambiente JavaScript no Visual Studio Code</h2>



1. Crie uma pasta na **Área de Trabalho**, chamada **javascript**.
2. Abra o Visual Studio Code IDE através da caixa de pesquisa da sua barra de tarefas, ou através do menu iniciar do seu Sistema Operacional.
3. Ao iniciar o Visual Studio Code IDE, será aberta a tela abaixo, perguntando o que você deseja fazer?

<div align="center"><img src="https://i.imgur.com/AtTA7K4.png" title="source: imgur.com" /></div>

4. No **Visual Studio Code**, abra a pasta **javascript**, criada na **Área de Trabalho**, através do menu **File 🡪 Open Folder... (Arquivo 🡪 Abrir Pasta...)**

   <div align="center"><img src="https://i.imgur.com/TgvVW26.png" title="source: imgur.com" /></div>

5. Localize na **Área de Trabalho do seu Computador** a pasta **javascript** e na sequência, dê um duplo clique sobre a  pasta e clique no botão **Selecionar pasta**.

<div align="center">
  <img src="https://i.imgur.com/R0Wc4WE.png" title="source: imgur.com" />
</div>

6. Depois de abrir a pasta, abra o **Terminal** do Visual Studio Code através do menu **Terminal 🡪 New Terminal (Terminal 🡪 Novo Terminal)**

   <div align="center"><img src="https://i.imgur.com/4rdobXK.png?1" title="source: imgur.com" /></div>

7. Inicialmente, será aberta a tela do **Power Shell** na parte inferior da janela do Visual Studio Code.

   <div><img src="https://i.imgur.com/BYbZTqV.png" title="source: imgur.com" /></div>

8. Vamos alterar o Terminal padrão do Visual Studio Code para o **GitBash**. Ao lado do identificador do Terminal **powershell**, tem um botão com um sinal de + e uma seta apontando para baixo, como mostra a imagem abaixo:

   <div><img src="https://i.imgur.com/5oBDpyM.png" title="source: imgur.com" /></div>

9. Clique na seta apontando para baixo. Será aberto um Menu.
10. No Menu que será aberto, clique na opção **Select Default Profile**.

<div align="center"><img src="https://i.imgur.com/nlQYFaX.png" title="source: imgur.com" /></div>

11. Será aberto um menu suspenso, abaixo da **Barra de Menus** do Visual Studio Code. Clique na opção **Git Bash**.

<div align="center"><img src="https://i.imgur.com/81kHNE7.png" title="source: imgur.com" /></div>

12. Feche a Janela do Terminal e abra novamente através do menu **Terminal 🡪 New Terminal (Terminal 🡪 Novo Terminal)**. 
12. Observe que será aberta a janela do Terminal **Git Bash**, ao invés do **Powershell**.

   <div><img src="https://i.imgur.com/dclBNT6.png" title="source: imgur.com" /></div>

14. Antes de começarmos a criar o nosso primeiro projeto nesta pasta, vamos checar se o **Node** está instalado corretamente através do comando abaixo:

   ```bash
   node -v
   ```
   <div><img src="https://i.imgur.com/Jv03d8U.png" title="source: imgur.com" /></div>

15. Vamos verificar também se o **NPM** está instalado através do comando:

   ```bash
   npm -v
   ```

<div><img src="https://i.imgur.com/5DV9Cdf.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ATENÇÃO:** No momento em que este material foi escrito, a versão LTS mais atual do Node era a versão 18.18.2 LTS. Ao utilizar este material no futuro, pode ser que a versão mais atual seja outra.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Todos os projetos do Bloco 01 - JavaScript - Console, serão criados dentro desta pasta. Cada novo projeto que você criar, crie uma nova pasta dentro da pasta javascript.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>👣 Passo 02 - Criar o arquivo .gitignore</h2>



Vamos criar o arquivo **.gitignore** dentro da pasta **javascript**, que contêm os padrões, que serão comparados com nomes de arquivos e pastas dentro do seu repositório, para determinar se devem ou não ser ignorados pelo git, no momento do versionamento do seu código:

1. No terminal, dentro da pasta **javascript**, crie o arquivo **.gitignore**, através do comando abaixo:

```bash
touch .gitignore
```

2. Abra o arquivo  **.gitignore** no **Visual Studio Code**:

<div><img src="https://i.imgur.com/rMyOcWi.png" title="source: imgur.com" /></div>

> O Git enxerga cada arquivo no seu Repositório Remoto com um dos três estados abaixo:
>
> 1. **Rastreado** – Um arquivo que já passou pelo staging ou commit;
> 2. **Não Rastreado** – Um arquivo que *não* passou pelo staging ou commit;
> 3. **Ignorado** – Um arquivo que o Git foi forçado a ignorar.
>
> Os arquivos ignorados costumam ser artefatos de  desenvolvimento e  arquivos gerados por máquina que podem ser derivados  da fonte do seu  repositório ou que não devem passar por commit.  Exemplos comuns incluem:
>
> - caches de dependência, como o conteúdo de `/node_modules` ou `/packages`
> - código compilado, como arquivos `.o`, `.pyc` e `.class`
> - diretórios de saída de build, como `/bin`, `/out` ou `/target`
> - arquivos gerados no período de execução, como `.log`, `.lock` ou `.tmp`
> - arquivos de sistema ocultos, como `.DS_Store` ou `Thumbs.db`
> - arquivos pessoais de configuração do IDE, como `.idea/workspace.xml`
>
> Os arquivos ignorados são rastreados em um arquivo especial chamado `.gitignore`, que é verificado na origem do seu repositório. Não há nenhum comando  git ignore explícito: é preciso editar e fazer commit do arquivo `.gitignore` à mão quando você tiver novos arquivos que quer ignorar. Os arquivos `.gitignore` contêm padrões que são comparados com nomes de arquivos em seu  repositório para determinar se devem ou não ser ignorados. Por isso  adicionamos o arquivo .gitignore manualmente.

3. Adicione o código abaixo dentro do arquivo  **.gitignore** e salve o arquivo:

```bash
# compiled output
/dist
/node_modules
nodemon.json

# Logs
logs
*.log
npm-debug.log*
pnpm-debug.log*
yarn-debug.log*
yarn-error.log*
lerna-debug.log*

# OS
.DS_Store

# Tests
/coverage
/.nyc_output

# IDEs and editors
/.idea
.project
.classpath
.c9/
*.launch
.settings/
*.sublime-workspace

# IDE - Visual Studio Code
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
```

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="100px"/> | <div align="left">**DICA:** *Habilite a opção Auto Save, através do menu File 🡪 Auto Save. Desta forma, não será mais necessário se preocupar em Salvar os arquivos criados no Visual Studio Code.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>👣 Passo 03 - Instalar a Biblioteca Readline-Sync</h2>



Vamos instalar a Biblioteca **Readline-Sync**, que nos permitirá fazer a leitura de dados via teclado nos próximos projetos, que serão criados na pasta **javascript**:

1. Vamos instalar o **Pacote Readline-Sync** através do comando abaixo:

```bash
npm install readline-sync
```

2. Verifique se o **Pacote Readline-Sync** foi instalado corretamente através do comando abaixo:

```bash
npm list
```

3. Será exibida a lista de pacotes instalados. Verifique se o **Pacote Readline-Sync** está instalado no seu projeto:

<div><img src="https://i.imgur.com/zJt3v3D.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 04 - Criando o Projeto Hello World</h2>



1. Na **Barra Explorer**, selecione a pasta **javascript** e clique no botão **New Folder** (Nova Pasta), indicado na imagem abaixo: 

<div align="center"><img src="https://i.imgur.com/1uHrNDS.png" title="source: imgur.com" /></div>

2. O nome da pasta será **helloworld**, como mostra a imagem abaixo. Após digitar o nome da pasta, pressione a tecla **enter** do seu teclado para concluir. 

<div align="center"><img src="https://i.imgur.com/z2RBahA.png" title="source: imgur.com" /></div>

Na sequência, vamos criar o arquivo **HelloWorld.js**, dentro da nossa pasta **helloworld**:

1. Selecione a pasta **helloworld** e clique no botão **New File** (Novo Arquivo), indicado na imagem abaixo:  

<div align="center"><img src="https://imgur.com/rRdQ9Kt.png" title="source: imgur.com" /></div>

2. O nome do arquivo será **HelloWorld.js**, como mostra a figura abaixo. Após digitar o nome do arquivo, pressione a tecla **enter** do seu teclado para concluir. 

<div align="center"><img src="https://i.imgur.com/kqxBqrQ.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 05 - Escrever o Código JavaScript</h2>



1. Insira o código abaixo no arquivo **HelloWorld.js**:

```js
console.log("Hello World!");
```

O Comando **console.log()** exibirá uma mensagem no Terminal.

<br />

<h2>👣 Passo 06 - Instalar a extensão Code Runner</h2>



A extensão **Code Runner**, simplifica o processo de execução do código, criando um botão no Visual Studio Code, que permite executar o código sem a necessidade de digitar comandos no Terminal:

1. Na **Barra de atividades (Activity Bar)**, localizada no lado esquerdo da tela do Visual Studio Code, clique no ícone <img src="https://i.imgur.com/yW9M2ET.png" title="source: imgur.com" width="4%"/> **Extensions (Extensões)**
2. Localize e Instale a extensão **Code Runner**, clicando no botão **Install (Instalar)**.

<div align="center"><img src="https://i.imgur.com/MBBmCSA.png" title="source: imgur.com" /></div>

3. Após a instalação, abra a página da extensão **Code Runner** e clique no botão <img src="https://i.imgur.com/8qfoVTi.png" title="source: imgur.com" width="4%"/> **Manager** para configurar o **Code Runner**, como mostra  a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/LrTwPpA.png" title="source: imgur.com" /></div>

4. Na sequência, clique na opção **Extension Settings**, no menu que será aberto:

<div align="center"><img src="https://i.imgur.com/fqvpHzZ.png" title="source: imgur.com" /></div>

5. Localize a opção **Code-runner: Run In Terminal** e marque a opção: **Whether to run code in Integrated Terminal**:

<div align="center"><img src="https://i.imgur.com/X1HBobC.png" title="source: imgur.com" /></div>

6. Volte para o o projeto **HelloWorld** e clique no botão <img src="https://i.imgur.com/dGcYxli.png" title="source: imgur.com" width="4%"/>**Run Code** para executar o código:

<div align="center"><img src="https://i.imgur.com/4rVxyc6.png" title="source: imgur.com" /></div>

<br />

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Código:**

```bash
Hello World!
```

7. O resultado acima será exibido no Terminal.

<br />

<h2>👣 Passo 07 - Enviar para o Github</h2>



1. De volta ao **Terminal**, dentro da pasta **javascript**, digite o comando abaixo para criar o Repositório Local dentro da pasta **javascript**.

```bash
git init
```

2. Digite o comando abaixo para adicionar o Projeto na **Stage Area** do Git:


```bash
git add .
```

3. Na sequência, faça o commit do Projeto, através do comando abaixo:

```bash
git commit -m "Projeto Hello World"
```

4. Acesse o seu **Github** e crie um novo **Repositório**, através da opção **New repository**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/GncQ1uf.png" title="source: imgur.com" /></div>

5. Crie o **Repositório Remoto** chamado **javascript**:

<div align="center"><img src="https://i.imgur.com/zihtu4X.png" title="source: imgur.com" /></div>

6. Clique no botão **Create Repository**, para criar o Repositório:

<div align="center"><img src="https://i.imgur.com/d9cRI9m.png" title="source: imgur.com" /></div>

7. Na próxima janela, copie o endereço **HTTPS do Repositório Remoto**, indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/heL37RP.png" title="source: imgur.com" /></div>

8. Volte para o **Terminal** e execute o comando abaixo para conectar o seu **Repositório Local** com o seu **Repositório Remoto**, onde o endereço **https**, será o endereço do seu **Repositório Remoto**.

```bash
git remote add origin https://github.com/rafaelq80/javascript.git
```

9. Digite o comando abaixo para checar se o seu  **Repositório Local** está conectado com o seu **Repositório Remoto**:

```bash
git remote -v
```

10. Se estiver conectado, será exibida uma mensagem, semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/5dXEKTl.png" title="source: imgur.com" /></div>

11. Na sequência, utilize o comando abaixo, para sincronizar o conteúdo do **Repositório Local** com o seu **Repositório Remoto**:

```bash
git push origin main
```

12. Volte para o Github, atualize a página do seu **Repositório Remoto** e verifique se ele está semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Nn5wUkK.png" title="source: imgur.com" /></div>

<br />

<h2>Criei um novo Projeto na pasta javascript. Como enviar para o Github?</h2>



No decorrer das aulas, serão criados vários projetos dentro da pasta javascript. Para atualizar os Repositórios Local e Remoto, não será necessário criar um novo Repositório e fazer todo o processo acima. Para atualizar o Repositório atual, siga os passos abaixo:

1. Depois de criar e finalizar o seu projeto, digite o comando abaixo para adicionar os novos Projetos na **Stage Area** do Git:


```bash
git add .
```

2. Na sequência, faça o commit do arquivo, através do comando abaixo:

```bash
git commit -m "Nome do Projeto"
```

3. Na sequência, utilize o comando abaixo, para sincronizar o conteúdo do **Repositório Local** com o seu **Repositório Remoto**:

```bash
git push origin main
```

4. Volte para o Github, atualize a página do seu **Repositório Remoto** e verifique se ele foi atualizado.

<br />
