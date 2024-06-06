<h1>Criando um Projeto de Testes xUnit no VSCode</h1>



<h2>1. Criar e Configurar O Projeto de Testes do xUnit</h2>



1. Na **Área de Trabalho**, abra a pasta **aspnet**.

<div align="center"><img src="https://i.imgur.com/3LnSg06.png" title="source: imgur.com" /></div>

2. Clique com o botão direito do mouse sobre a pasta **blogpessoal** e clique na opção **Abrir com com Code**.

3. A pasta será aberta no **VSCode**, como mostra a figura abaixo e dentro dela veremos a pasta do projeto **blogpessoal**:

<div align="center"><img src="https://i.imgur.com/2DaDfYb.png" title="source: imgur.com" /></div>

4. Crie uma pasta chamada **blogpessoaltest** dentro da pasta **BLOGPESSOAL**. Após criar a pasta, o seu projeto estará semelhante a figura abaixo:

<div align="center"><img src="https://i.imgur.com/dm1pEPr.png" title="source: imgur.com" /></div>

5. Abra o Terminal, através do Menu **Terminal 🡒 New Terminal**

<div align="center"><img src="https://i.imgur.com/4rdobXK.png?1" title="source: imgur.com" /></div>

6. Será aberta a tela do **Terminal** na parte inferior da janela do **VSCode**.

<div><img src="https://i.imgur.com/FfXSnoB.png" title="source: imgur.com" /></div>

<br />

Agora vamos criar o Projeto **xUnit** para escrever os testes automatizados na nossa aplicação ASP.NET:

1. Digite o comando abaixo no **Terminal** para checar se o **.NET SDK** está instalado:

```bash
dotnet --info
```

2. O resultado do comando será semelhante a imagem abaixo:

<div><img src="https://i.imgur.com/qrZOleO.png" title="source: imgur.com" /></div>

3. Digite os comando abaixo no **Terminal** para acessar a pasta **blogpessoaltest**:

```bash
cd blogpessoal_test
```

4. Digite o comando abaixo no **Terminal** para **Criar um novo Projeto do xUnit** dentro da pasta **blogpessoaltest**:

```bash
dotnet new xunit
```

5. A saída do comando será semelhante ao conteúdo abaixo:

```bash
O modelo "xUnit Test Project" foi criado com êxito.

Processando ações pós-criação...
Restaurando C:\Users\rafae\OneDrive\Área de Trabalho\aspnet\blogpessoal\blogpessoal.csproj:
  Determinando os projetos a serem restaurados...
  C:\Users\rafae\OneDrive\Área de Trabalho\aspnet\blogpessoa
  l\blogpessoal.csproj restaurado (em 1,67 sec).
A restauração foi bem-sucedida.
```

6. Observe na **Guia Explorer**, que o projeto foi criado:

<div align="center"><img src="https://i.imgur.com/ONlftCM.png" title="source: imgur.com" /></div>

<br />

Vamos configurar o projeto removendo os arquivis desnecessários e adicionar o arquivo **.gitignore**:

1. Na **Guia Explorer** vamos excluir o arquivo **UnitTest1.cs**:

<div align="center"><img src="https://i.imgur.com/6OJ61H9.png" title="source: imgur.com" /></div>

2. Digite o comando abaixo no terminal para adicionar no projeto **blogpessoaltest** o arquivo **.gitignore**:

```bash
dotnet new gitignore
```

3. Observe na **Guia Explorer** que foi adicoonado ao projeto o arquivo **.gitignore**:

<div align="center"><img src="https://i.imgur.com/AzkPa0n.png" title="source: imgur.com" /></div>

<br />

Na sequência, vamos adicionar o projeto **blogpessoaltest** na solução **blogpessoal.sln**, localizada na pasta do projeto **blogpessoal**:

1. Acesse a pasta **blogpessoal** através dos comandos abaixo:

```bash
cd ..

cd blogpessoal
```

2. Digite o comando abaixo no terminal para adicionar o projeto **blogpessoaltest** na mesma solução do projeto **blogpessoal**:

```bash
dotnet sln blogpessoal.sln add ../blogpessoaltest/blogpessoaltest.csproj
```

3. A saída do comando será semelhante ao conteúdo abaixo:

```bash
O projeto ‘..\blogpessoaltest\blogpessoaltest.csproj’ foi adicionado à solução.
```

<br />

Na sequência, vamos configurar o projeto **blogpessoaltest** como um projeto de testes do projeto **blogpessoal**:

1. Acesse a pasta **blogpessoaltest** através dos comandos abaixo:

```bash
cd ..

cd blogpessoaltest
```

2. Digite o comando abaixo no terminal para adicionar o projeto **blogpessoal** como referência do projeto **blogpessoaltest**:

```bash
dotnet add blogpessoal_test.csproj reference ../blogpessoal/blogpessoal.csproj
```

3. A saída do comando será semelhante ao conteúdo abaixo:

```bash
A referência ‘..\blogpessoal\blogpessoal.csproj’ foi adicionada ao projeto.
```

4. A partir deste ponto, siga as instruções do Cookbook a partir do **Passo 03 - Instalar os pacotes**.

<br />

<h2>2. Executar o Projeto de Testes do xUnit</h2>



Vamos instalar a Extensão **.NET Core Test Explorer**, para que o VSCode reconheça o projeto de testes do xUnit:

1. Na Barra de tarefas localizada no lado esquerdo da tela, clique na opção **Extensions**

<div align="center"><img src="https://i.imgur.com/v5nFOS5.png" title="source: imgur.com" /></div>

3. Localize a Extensão **.NET Core Test Explorer** e clique no botão **install**:

<div align="center"><img src="https://i.imgur.com/ZiN1Ct0.png" title="source: imgur.com" /></div>

<br />

Na sequência, vamos executar os testes escritos no projeto **blogpessoaltest**:

1. Na Barra de tarefas localizada no lado esquerdo da tela, clique na opção **Testing**

<div align="center"><img src="https://i.imgur.com/6u2VuyI.png" title="source: imgur.com" /></div>

2. Na guia **Test Explorer** será exibida a lista com todos os testes que foram escritos:

<div align="center"><img src="https://i.imgur.com/wMTinGp.png" title="source: imgur.com" /></div>

3. Para executar todos os testes de uma única vez, clique no botão <img src="https://i.imgur.com/LJtOgp2.png" title="source: imgur.com" width="3%"/> **Run Tests**:

<div align="center"><img src="https://i.imgur.com/fVEaECF.png" title="source: imgur.com" /></div>

4. Aguarde a execução dos testes
5. Caso o teste seja aprovado, será exibido ao lado do teste um <img src="https://i.imgur.com/5KUWCAE.png" title="source: imgur.com" width="3%"/> **check verde** como vemos na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/9vs8N9E.png" title="source: imgur.com" /></div>

6. Caso o teste seja reprovado, será exibido ao lado do teste um <img src="https://i.imgur.com/YMiVJw1.png" title="source: imgur.com" width="3%"/> **fail vermelho** como vemos na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/wDg3phJ.png" title="source: imgur.com" /></div>

7. Para identificar a falha que ocorreu no teste, ao lado da **Guia Debug Console**, clique na **Guia Test Results**. Na sequência, clique sobre o teste que falhou e verifique o motivo da falha, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/B3fdgdU.png" title="source: imgur.com" /></div>

8. Faça as devidas correções no Teste ou no Código da aplicação, dependendo da falha.
9. Na guia **Test Explorer**, clique sobre o teste que falhou e execute somente ele clicando no botão <img src="https://i.imgur.com/GXzpQnZ.png" title="source: imgur.com" width="3%"/> **Run**.

<div align="center"><img src="https://i.imgur.com/QjPwyLx.png" title="source: imgur.com" /></div>

10. Caso o teste seja aprovado, será exibido ao lado do teste um <img src="https://i.imgur.com/5KUWCAE.png" title="source: imgur.com" width="3%"/> **check verde** como vemos na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/9vs8N9E.png" title="source: imgur.com" /></div>

<br />

<br />

