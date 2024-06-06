<h1>Trabalhando em equipe no Git - Fluxo Git</h1>

Um Fluxo de trabalho do Git é uma receita ou recomendação sobre como usar o Git para realizar o trabalho de maneira consistente e produtiva. Os fluxos de trabalho do Git incentivam os usuários a aproveitar o Git de modo eficiente e consistente.

<h2>1) O que é um fluxo de trabalho bem-sucedido do Git?</h2>

Ao avaliar um fluxo de trabalho para sua equipe, o mais importante é entender a cultura da equipe. O fluxo de trabalho tem como objetivo melhorar a eficácia da equipe e não ser uma carga que limita a produtividade da equipe.

Algumas coisas importantes devem ser questionadas ao avaliar a eficiência de um fluxo de trabalho do Git, entre elas:

- O fluxo de trabalho é dimensionado com o tamanho da equipe?

- O fluxo de trabalho simplifica o processo de desfazer erros?

- O fluxo de trabalho impõe alguma nova sobrecarga cognitiva desnecessária à equipe?
  
<h3>1.1) Tipos de Fluxo </h3>

-   **Fluxo de trabalho centralizado:** A ideia central por trás do Fluxo de trabalho centralizado é que todo o desenvolvimento de recursos deve ocorrer na branch main.

<div align="center"><img src="https://i.imgur.com/hwksZ3o.png" title="source: imgur.com" /></div>

-   **Fluxo de trabalho de ramificação de recurso:**  A ideia central por trás do Fluxo de trabalho de ramificação de recursos é que cada feature deve ocorrer em uma Branch dedicada, que só é enviada para a Branch Main quando se torna parte de uma nova versão.

<div align="center"><img src="https://i.imgur.com/nmRQnQc.png" title="source: imgur.com" /></div>

-   **Fluxo de trabalho Gitflow:** Define um modelo de ramificação rigoroso projetado com base no lançamento do projeto oferecendo uma estrutura robusta para gerenciar grandes projetos. 

<div align="center"><img src="https://i.imgur.com/ia9GWIP.png" title="source: imgur.com" /></div>

<br />

<img width="30px" src="https://i.imgur.com/GQKtp6q.png" title="source: imgur.com" />  Para saber mais sobre o GitFlow, assista ao vídeo *Trabalhando em equipe com Git Flow* clicando neste [link](https://www.youtube.com/watch?v=394mc6PV8t8)

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="80px"/> | <div align="left"> **DICA:** *Existem outros Modelos de Fluxo Git. Os 3 citados acima são os mais populares.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

No projeto Integrador, utilizaremos o modelo <b>Fluxo de trabalho de Ramificação de recurso</b>, conforme a estrutura detalhada nas figuras abaixo, onde cada <b>Task</b> do Projeto Integrador será uma <b>Feature Branch</b> no Repositório Remoto no Github.

<div align="center"><img src="https://i.imgur.com/59o9NhC.png" title="source: imgur.com" width="95%"/></div>

<i>Fluxo de trabalho do Bloco 02 - Backend</i>

<div align="center"><img src="https://i.imgur.com/Ig34RBB.png" title="source: imgur.com" width="95%"/></div>

<i>Fluxo de trabalho do Bloco 03 - Frontend</i>

O Fluxo do Backend acontecerá no repositório do Backend, enquanto o fluxo do Frontend acontecerá no repositório do Frontend. 

<br />

<h3>1.1. Organização dos Repositórios Remotos na Organização</h3>

<table border="1" width="100%">
	<tr>
		<td><b>Repositório</b></td>
		<td><b>Conteúdo</b></td>
	</tr>
	<tr>
		<td><b>Docs</b></td>
		<td>Arquivos contendo a documentação da API: <br />
		- Documentação  do Banco de Dados (DER, SQL e Dicionário de dados)<br />
		- Documentação do Backend (Abertura de projeto e Dicionário de Atributos)<br />
		- Documentação do Frontend (Wireframe)
		</td>
	</tr>
	<tr>
		<td><b>Backend</b></td>
		<td>Projeto ASP.NET completo (Bloco 02)</td>
	</tr>
	<tr>
		<td><b>Frontend</b></td>
		<td>Projeto React Completo (Bloco 03)</td>
	</tr>
</table>

<br />

<h2>2) Insights</h2>

Um recurso interessante do Github é o **Insights**. Com ele é possível acompanhar através de gráficos e dados estatísticos a colaboração de cada membro da equipe com o projeto e os dados estatísticos do repositório como um todo.

1. Para acessar, clique no link <img width="75px" src="https://i.imgur.com/B2TmWS9.png" title="source: imgur.com" /> do repositório remoto no github. 

2. Na próxima janela, clique em **Contributors**. Você verá uma janela semelhante a figura abaixo:

<div align="center"><img src="https://i.imgur.com/7QDsSko.png" title="source: imgur.com" /></div>

Observe que cada usuário adicionado como colaborador do repositório remoto possui o seu gráfico de colaboração no repositório, baseado no commits.

<br />

<h2>3) Configurando o VSCode como Editor Oficial do Git</h2>



Vamos configurar o Microsoft VIsual Studio Code como a IDE padrão do Git, caso você ainda não tenha feito este passo na sessão sobre Git do Bloco 01, desta forma poderemos utilizar os recursos que o VSCode oferece para resolução de conflitos.

1.  Verifique se o **VSCode** está instalado na sua máquina 

2.  Caso não esteja instalado, faça a instalação seguindo o **Guia de Instalação do VSCode** clicando neste <a href="https://github.com/conteudoGeneration/cookbook_csharp/blob/main/00_ambiente/05_install_vscode.md">link</a>.

3.  Após confirmar ou instalar o VSCode, abra **o Git Bash**

4.  Configure o VSCode como o Editor padrão do Git através do comando abaixo:

```bash
git config --global core.editor 'code --wait'
```

<br />

<h2>4) Iniciando um Fluxo de Trabalho Git</h2>



Antes de começarmos, todos os integrantes do grupo devem criar uma pasta na Área de Trabalho, que será utilizada como Repositório Local do Projeto do Backend no seu computador, conectada ao Repositório Remoto no Github. 

<br />

<h3>4.1. Criar e inicializer o Repositório Local - Backend (Todos)</h3>



1. Crie uma pasta na **Área de trabalho** chamada **projeto_integrador** 
1. Dentro da pasta  **projeto_integrador**, crie uma pasta chamada **backend**

<div align="center"><img src="https://i.imgur.com/2PDqnNT.png" title="source: imgur.com" /></div>

3. Clique com o botão direito do mouse sobre a pasta **backend** e no menu que será aberto, clique na opção: **Git Bash Here**
4. No **Git Bash**, execute a sequência de comandos abaixo para conectar  a sua pasta **backend** com o Repositório Remoto **backend**, criado dentro da Organização do Projeto.

```bash
git init
 
git remote add origin endereço_remoto
 
git remote -v
```

Onde:

| **Comando**                             | **Descrição**                                                |
| --------------------------------------- | ------------------------------------------------------------ |
| *git init*                              | Inicializa um repositório git local dentro da pasta blogpessoal. |
| *git remote add origin endereço_remoto* | Associa o repositório local ao repositório remoto. O endereço_remoto será o endereço do repositório remoto da organização. |
| *git remote -v*                         | Checa se o seu repositório local está conectado ao repositório remoto |

5. Para obter o endereço Remoto do seu Repositório basta copiar o endereço disponível no item **HTTPS** do novo Repositório, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/7W4HJOF.png" title="source: imgur.com" /></div>

6. Feche o Git Bash

<br />

<h3>4.2) Criar o projeto ASP.NET (Product Owner)</h3>




1. 
   Ao iniciar o Visual Studio IDE, será aberta a tela abaixo, perguntando que você deseja fazer. Para Criar um novo Projeto, clique na opção **Criar um projeto**. 

<div align="center">
  <img src="https://i.imgur.com/pc8tgWi.png" title="source: imgur.com" />
</div>

2. Na próxima tela, selecione o tipo de projeto que será criado. Selecione a opção **API Web do ASP.NET Core** e clique em **Próximo** para continuar.

<div align="center">
  <img src="https://i.imgur.com/7316dEQ.png" title="source: imgur.com" />
</div>

3. Na próxima tela, vamos configurar o nosso projeto. No item **Nome do projeto**, informe o nome do projeto: **projeto_integrador**. 

<div align="center">
  <img src="https://i.imgur.com/TQGrjl1.png" title="source: imgur.com" />
</div>
4. No item **Local**, **clique no botão com 3 pontos** <img src="https://i.imgur.com/RVKkHqy.png" title="source: imgur.com" width="4%"/>para selecionar a pasta onde o Projeto será criado.

<div align="center">
  <img src="https://i.imgur.com/6GhlJ1J.png" title="source: imgur.com" />
</div>
5. Na **Área de Trabalho do seu Computador** dentro da pasta **projeto_integrador**, selecione a pasta **backend** e clique no botão **Selecionar pasta**.

<div align="center">
  <img src="https://i.imgur.com/YiFp12I.png" title="source: imgur.com" />
</div>

6. Mantenha o item **Colocar a solução e o projeto no mesmo diretório** selecionado, como mostra a imagem abaixo e clique em **Próximo** para continuar.

<div align="center">
  <img src="https://i.imgur.com/ZAwm9lX.png" title="source: imgur.com" />
</div>
7. Na próxima tela, mantenha o item **configure igual** a imagem abaixo e clique no botão **Criar**. 

<div align="center">
  <img src="https://i.imgur.com/1cVrG9Q.png" title="source: imgur.com" />
</div>
8. Será aberta a janela abaixo, com o projeto criado:

<div align="center"><img src="https://i.imgur.com/hW5M6vh.png" title="source: imgur.com" /></div>

9. Adicione o arquivo **.gitignore** no projeto.

<br />

<h3>4.3) Enviar o projeto para o Github (Product Owner)</h3>



1. Abra o Terminal do **Visual Studio**, clicando no menu **Exibir 🡢 Terminal**.
2. No **Terminal**, execute a sequência de comandos abaixo para conectar  a sua pasta **backend** com o Repositório Remoto **backend**.

```bash
 cd ..
 
 git add .
 
 git commit -m "Criar o Projeto ASP.NET"
 
 git push origin main
```

3. Caso seja exibida a mensagem abaixo, significa que o seu usuário não foi adicionado como colaborador do Repositório.

```bash
remote: Permission to Projeto-Integrador-Modelo/backend.git denied to rafaelq80.
fatal: unable to access 'https://github.com/Projeto-Integrador-Modelo/backend.git/': The requested URL returned error: 403
```

4. Verifique se o Repositório Remoto no Github foi atualizado. O Repositório estará semelhante a imagem abaixo: 

<div align="center"><img src="https://i.imgur.com/fUMbsvf.png" title="source: imgur.com" /></div>

<br />

<h3>4.4) Criar a Branch Task 03 (Product Owner)</h3>



Antes de criar a primeira Classe Model do Projeto, vamos criar a nossa primeira **Branch**, onde será desenvolvida a **Task3** do **Projeto Integrador**. 

1. No Terminal do **Visual Studio**, crie uma nova Branch com o nome **task3**, através do comando abaixo:

```bash
 git checkout -b task3
```

2. Na sequência, execute o comando abaixo para enviar a **Branch Task 03** para o Repositório Remoto **backend**.

```bash
 git push origin task3
```

6. Verifique se o repositório remoto no Github foi atualizado e possui **2 Branches**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/zqYEDqz.png" title="source: imgur.com" /></div>

<br />

<h3>4.5) Atualizar o Repositório Local (Scrum Master, Developers e Tester)</h3>



As Pessoas Desenvolvedoras, o Scrum Master e o Tester, antes de começarem a implementar o código da primeira Model, deverão atualizar o Repositório Local com todas as alterações do Repositório Remoto.

1.  Clique com o botão direito do mouse sobre a pasta **backend**, localizada dentro da pasta **projeto_integrador** e no menu que será aberto, clique na opção: **Git Bash Here**
1.  No **Git Bash**, execute a sequência de comandos abaixo para atualizar o seu repositório **local** com o conteúdo do repositório remoto **backend**. Desta forma o seu repositório local receberá todo o conteúdo das 2 Branches.

```bash
git pull origin main

git pull origin task3

git checkout task3
```

3. Abra o projeto no Visual Studio

<br />

<h3>4.6) Criar a Primeira Classe (Developers)</h3>



As pessoas Desenvolvedoras, estão prontas para trabalhar no código.

1. Verifique no Gitbash se a Branch atual é a Branch **task3**

<div align="left"><img src="https://i.imgur.com/CyHb0KE.png" title="source: imgur.com" /></div>

2. Conclua a configuração do Projeto, seguindo o conteúdo do **[Cookbook 04](https://github.com/conteudoGeneration/cookbook_csharp/blob/main/04_aspnet/04.md)**

3. Configure a conexão com o Banco de dados e crie a Classe **AppDbContext** , seguindo o conteúdo do **[Cookbook 05](https://github.com/conteudoGeneration/cookbook_csharp/blob/main/04_aspnet/05.md)**

4. Crie a primeira **Classe Model** na pasta **Model** e a Classe de **Validação da primeira Classe Model** na pasta **Validation**, seguindo o conteúdo do **[Cookbook 06](https://github.com/conteudoGeneration/cookbook_csharp/blob/main/04_aspnet/06.md)**

5. Caso a sua Model possua o atributo Data de Criação/Atualização, crie a Classe **Auditable** na pasta **Model** e registre na **Classe AppDbContext**.

7. Execute a aplicação e verifique se o Banco de dados e a primeira Tabela foram criadas no **SQL Server**.

11. No Gitbash, execute a sequência de comandos abaixo para enviar a Tarefa para o **Repositório Remoto backend**:

```bash
git add .
    
git commit -m "Task 03 - Criar a primeira Classe Model"
    
git push origin task3
```

8. Observe que a **Classe Model** estará disponível apenas na **Branch Task 03**.

<div align="center"><img src="https://i.imgur.com/NcPCNQt.png" title="source: imgur.com" /></div>

<br />

<h3>4.7) Testes da Aplicação (Tester)</h3>



Quando as Pessoas Desenvolvedoras finalizarem o código, o Tester deverá atualizar o seu Repositório Local e testar a aplicação.

1.  Clique com o botão direito do mouse sobre a pasta **backend**, localizada dentro da pasta **projeto_integrador** e no menu que será aberto, clique na opção: **Git Bash Here**
2.  No **Git Bash**, execute a sequência de comandos abaixo para atualizar  o Repositório Local com as atualizações do Repositório Remoto **backend**.

```bash
git pull origin main

git pull origin task3

git checkout task3 
```

3. Abra o projeto no Visual Studio e execute o projeto.
4. Faça todos os testes necessários. Dependendo da Tarefa, utilize o **Insomnia** para criar as requisições HTTP.
5. Ao concluir, se todos os testes passaram, avise ao Product Owner para ele fazer a Integração.
6. Se algum teste não passou, comunique as Pessoas Desenvolvedoras e solicite a correção do código.

<br />

| <img src="https://i.imgur.com/RfjtOFi.png" title="source: imgur.com" width="100px"/> | <div align="left">**DICA:** *Exporte as Requisições HTTP criadas no Insomnia para um arquivo JSON. Desta forma o próximo Tester não precisará recriar todas as Requisições novamente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>4.8) Integrando a Branch Task 03 com a Branch Main (Product Owner)</h3>



Agora vamos finalizar a **Branch Task 03**, ou seja, após finalizar e testar todos os códigos implementados na Task 03, vamos integrar todo o conteúdo da Branch Task 03 com a Branch Main através do comando **git merge**.

1. Clique com o botão direito do mouse sobre a pasta **backend**, localizada dentro da pasta **projeto_integrador** e no menu que será aberto, clique na opção: **Git Bash Here**
1. No Gitbash, execute a sequência de comandos abaixo para atualizar o Repositório Local


```bash
git pull origin main

git pull origin task3

git checkout main 
```

2. Atualize a Branch Main com o conteúdo da Branch Task 03, através do comando **Merge**

```bash
 git merge task3
```
4. Envie as atualizações para o Repositório Remoto no Github

```bash
 git push origin main
```

5. Observe que a **branch main** agora possui o mesmo conteúdo da **branch task3**

<div align="left"><img src="https://i.imgur.com/k4VagkV.png" title="source: imgur.com" /></div>

6. Após a Integração, todes os Integrantes do grupo, exceto o Product Owner devem executar o comando **git pull** para atualizar o Repositório Local.

```bash
git pull origin task3

git pull origin main 
```

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="300px"/> | <div align="left"> **ALERTA DE BSM:** *Antes de começar a implementar um novo código em um projeto em grupo, não esqueça de executar o comando, git pull em todas as Branches atualizadas. Desta forma você estará evitando os famosos Conflitos Git, além de ter a certeza que você estará trabalhando em cima da última versão funcional do Projeto * </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>5) Comandos úteis</h2>



  1. Criar uma Branch no Github
```bash
git push origin task3:new-branch
```

 2. Apagar uma Branch no github
```bash
git push origin:task3
```

 3. Renomear uma Branch
```bash
git branch -m novonome
```
4. Apagar uma Branch no Repositório Local

```bash
git branch -d nome_da_branch
```

5. Clonar um Repositório Remoto

```bash
git clone https://github.com/rafaelproinfo/projeto_integrador.git
```

6. Forçar uma atualização no Repositório Remoto

```bash
git push -f origin main
```

7. Forçar uma atualização no Repositório Local

```bash
git pull -f origin main
```

<br /><br />
