<h1>Enviando o Projeto ASPNET para o Github</h1>



Este guia irá auxiliar no processo de criação e inicialização da pasta que será utilizada para criar o projeto Blog Pessoal.

<br />

<h2>👣 Passo 01 - Criar o Repositório Remoto no Github</h2>



Vamos criar o Repositório Remoto no Github:

 1. Acesse a sua conta no Github (**https://github.com**).

 2. Na tela inicial do seu Github, clique no link <img src="https://i.imgur.com/YZktqfP.png?1" title="source: imgur.com" />, 

 3. Em **Repositories**, clique no botão **New** para adicionar um novo Repositório.

    <div align="center"><img src="https://i.imgur.com/I8fT17R.png" title="source: imgur.com" /></div>

 4. Crie um **Repositório Público**, chamado **blogpessoal**, como mostra a figura abaixo. 

<div align="center"><img src="https://i.imgur.com/ggpjGL0.png" title="source: imgur.com" /></div>

5. Em seguida clique no botão **Create Repository**.

<div align="center"><img src="https://i.imgur.com/VoSoY9B.png" title="source: imgur.com" /></div>

6. Repositório Criado!

<div align="center"><img src="https://i.imgur.com/AqP0SSo.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 02 - Criar o Repositório Local</h2>



1. Abra a pasta **aspnet**, que foi criada na **Área de Trabalho**
2. Dentro da pasta **aspnet**, crie a pasta **blogpessoal**

<div align="center"><img src="https://i.imgur.com/LtrovoI.png" title="source: imgur.com" /></div>

3. Clique com o botão direito do mouse sobre a pasta **blogpessoal** e no menu que será aberto, clique na opção: **Git Bash Here**
4. No **Git Bash**, execute a sequência de comandos abaixo para conectar  a sua pasta **blogpessoal** com o Repositório Remoto **blogpessoal**.

```
git init
 
git remote add origin https://github.com/rafaelq80/blogpessoal.git
 
git remote -v
```

Onde:

| **Comando**                             | **Descrição**                                                |
| --------------------------------------- | ------------------------------------------------------------ |
| *git init*                              | Inicializa um repositório git local dentro da pasta blogpessoal. |
| *git remote add origin endereço_remoto* | Associa o repositório local ao repositório remoto. O endereço_remoto será o endereço do seu repositório. |
| *git remote -v*                         | Checa se o seu repositório local está conectado ao repositório remoto |

5. Para obter o endereço Remoto do seu Repositório basta copiar o endereço disponível no item **HTTPS** do novo Repositório, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/AqP0SSo.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *A criação e inicialização desta pasta como um Repositório Git Local é muito importante. Caso contrário, quando estivermos trabalhando com Testes de Software, o projeto de testes não será enviado para o Repositório Remoto* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>👣 Passo 03 - Criar o Projeto ASP.NET</h2>



Siga as instruções da Live Code e/ou do Cookbook.

<br />

<h2>👣 Passo 04 - Enviar o Projeto para o Repositório Remoto</h2>



1. Abra o Terminal do **Visual Studio**, clicando no menu **Exibir 🡢 Terminal**.
2. Execute o comando abaixo para retornar para a pasta **blogpessoal**, criada no Passo 02, que é o Repositório Local.

```bash
cd ..
```

3. Execute o comando abaixo para confirmar que você está na pasta do Repositório Local.

```bash
ls -a
```

4. Se a pasta estiver correta, você verá a pasta **.git**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/zVroJ32.png" title="source: imgur.com" /></div>

5. Execute a sequência de comandos abaixo para enviar o conteúdo para o Repositório Remoto:

```bash
 git add .
 
 git commit -m “Criar o Projeto ASP.NET”
 
 git push -u origin main
```

6. Verifique se o Repositório Remoto no Github foi atualizado. O Repositório estará semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/KMU8UT7.png" title="source: imgur.com" /></div>
