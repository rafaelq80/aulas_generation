<h1>Criando um Projeto .NET Console no VSCode</h1>



1. Crie uma pasta chamada **csharp** na **Área de Trabalho** (Windows) ou no seu **Home Directory** (Linux).
2. Abra o **VSCode**

<div align="center"><img src="https://i.imgur.com/QYvTz5z.png" title="source: imgur.com" /></div>

3. Na Barra de tarefas localizada no lado esquerdo da tela, clique na opção **Extensions**

<div align="center"><img src="https://i.imgur.com/v5nFOS5.png" title="source: imgur.com" /></div>

3. Localize a Extensão **C# - Base language support for C#** e clique no botão **install**

<div align="center"><img src="https://i.imgur.com/jQCG40D.png" title="source: imgur.com" /></div>

5. A Extensão do **C#** instalará uma segunda extensão. A Extensão **.NET Install Tool for Extension Authors**

<div align="center"><img src="https://i.imgur.com/0hNn0Bj.png" title="source: imgur.com" /></div>

6. No VSCode, clique no Menu **File 🡒 Open Folder** 

<div align="center"><img src="https://i.imgur.com/TgvVW26.png" title="source: imgur.com" /></div>

7. Localize a e abra a pasta **csharp**, clicando no botão **Selecionar pasta**

<div align="center"><img src="https://i.imgur.com/WySYlvd.png" title="source: imgur.com" /></div>

*A tela acima será um pouco diferente no Linux.*

8. No **VSCode**, clique no Menu **Terminal 🡒 New Terminal**

<div align="center"><img src="https://i.imgur.com/4rdobXK.png?1" title="source: imgur.com" /></div>

9. Será aberta a tela do **Terminal** na parte inferior da janela do **VSCode**.

<div><img src="https://i.imgur.com/CLuloLI.png" title="source: imgur.com" /></div>

<br />

Vamos criar o Projeto **Hello World**:

1. Digite o comando abaixo no **Terminal** para checar se o **.NET SDK** está instalado:

```bash
dotnet --info
```

2. O resultado do comando será semelhante a imagem abaixo:

<div><img src="https://i.imgur.com/exrpbGe.png" title="source: imgur.com" /></div>

3. Digite o comando abaixo no **Terminal** para **Criar um novo Projeto Console**:

```bash
dotnet new console --name helloworld --framework net7.0 --use-program-main
```

**--name:** Nome do Projeto

**--framework:** Define a versão do SDK do .NET

**--use-program-main:** Não utilizar instruções de nível superior

4. A saída do comando será semelhante ao conteúdo abaixo:

```bash
O modelo "Aplicativo do Console" foi criado com êxito.       

Processando ações pós-criação...
Restaurando C:\Users\rafae\OneDrive\Área de Trabalho\csharp\helloworld\helloworld.csproj:
  Determinando os projetos a serem restaurados...
  C:\Users\rafae\OneDrive\Área de Trabalho\csharp\helloworld
  \helloworld.csproj restaurado (em 229 ms).
A restauração foi bem-sucedida.
```

5. Caso seja exibida a mensagem abaixo, clique em **Yes**, para configurar o VSCode para executar um projeto C#.

<div align="center"><img src="https://i.imgur.com/SdoKM2q.png" title="source: imgur.com" /></div>

6. Observe na **Guia Explorer**, que o projeto foi criado:

<div align="center"><img src="https://i.imgur.com/FNHL7rm.png" title="source: imgur.com" /></div>

7. Abra a Classe **Program**. 

8. O código da Classe **Program** será semelhante ao exemplo abaixo:

```c#
namespace helloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

Código implementado, vamos executar a aplicação:

1. Digite o comando abaixo no **Terminal** para acessar a pasta **helloworld**:

```bash
cd helloworld
```

2. Digite o comando abaixo no **Terminal** para executar o projeto:

```bash
dotnet run
```

3. O resultado do comando será semelhante a imagem abaixo:

<div><img src="https://i.imgur.com/wqdZY2r.png" title="source: imgur.com" /></div>

3. Para criar um novo Projeto, utilize o comando abaixo para voltar para a pasta **csharp**:

```c#
cd ..
```

4. Observe que depois de de executar o comando acima, o Terminal indicará que você está dentro da pasta **csharp** 

<div><img src="https://i.imgur.com/dy85FZ4.png" title="source: imgur.com" /></div>

5. Crie o novo projeto seguindo os passos acima. Não se esqueça de ajustar o código ao novo projeto.
