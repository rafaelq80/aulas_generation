<h1>Criando um Projeto .NET WEB API ASP.NET no VSCode</h1>



1. Crie uma pasta chamada **aspnet** na **Área de Trabalho** (Windows) ou no seu **Home Directory** (Linux).
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

7. Localize a e abra a pasta **aspnet**, clicando no botão **Selecionar pasta**

<div align="center"><img src="https://i.imgur.com/OV7U321.png" title="source: imgur.com" /></div>

*A tela acima será um pouco diferente no Linux.*

8. No **VSCode**, clique no Menu **Terminal 🡒 New Terminal**

<div align="center"><img src="https://i.imgur.com/4rdobXK.png?1" title="source: imgur.com" /></div>

9. Será aberta a tela do **Terminal** na parte inferior da janela do **VSCode**.

<div><img src="https://i.imgur.com/TlUpHOj.png" title="source: imgur.com" /></div>

<br />

Vamos criar o Projeto **Hello World**:

1. Digite o comando abaixo no **Terminal** para checar se o **.NET SDK** está instalado:

```bash
dotnet --info
```

2. O resultado do comando será semelhante a imagem abaixo:

<div><img src="https://i.imgur.com/ZXkgzPy.png" title="source: imgur.com" /></div>

3. Digite o comando abaixo no **Terminal** para **Criar um novo Projeto Console**:

```bash
dotnet new webapi -o helloworld --framework net7.0
```

**-o:** Nome do Projeto

**--framework:** Define a versão do SDK do .NET

4. A saída do comando será semelhante ao conteúdo abaixo:

```bash
O modelo "API Web do ASP.NET Core" foi criado com êxito.

Processando ações pós-criação...
Restaurando C:\Users\rafae\OneDrive\Área de Trabalho\aspnet\helloworld\helloworld.csproj:
  Determinando os projetos a serem restaurados...
  C:\Users\rafae\OneDrive\Área de Trabalho\aspnet\helloworld\helloworld.csproj 
  restaurado (em 430 ms).
A restauração foi bem-sucedida.
```

5. Observe na **Guia Explorer**, que o projeto foi criado:

<div align="center"><img src="https://i.imgur.com/FM5ofd3.png" title="source: imgur.com" /></div>

6. Caso seja exibida a mensagem abaixo, clique em **Yes**, para configurar o VSCode para executar um projeto ASP.NET.

<div align="center"><img src="https://i.imgur.com/SzoLNP6.png" title="source: imgur.com" /></div>

7. Para não ficarmos com vários projetos abertos no VSCode, vamos abrir apenas pasta **helloworld**, através do menu **File 🡪 Open Folder...** (Abrir Pasta...)

<div align="center"><img src="https://i.imgur.com/TgvVW26.png" title="source: imgur.com" /></div>

8. Selecione a pasta **helloworld** que foi criada dentro da pasta **aspnet** e clique no botão **Selecionar pasta**.

<div align="center"><img src="https://i.imgur.com/WtaXbWJ.png" title="source: imgur.com" /></div>

9. Observe que na **Guia Explorer** (lado esquerdo da tela) ficará visível apenas o projeto **Hello World**.

<div align="center"><img src="https://i.imgur.com/gWyyzJ4.png" title="source: imgur.com" /></div>

Vamos excluir alguns arquivos e pastas do nosso projeto, ante de prosseguirmos:

1. Na **Guia Explorer** vamos excluir o arquivo **WeatherForecast.cs**:

<div align="center"><img src="https://i.imgur.com/eHQxSak.png" title="source: imgur.com" /></div>

2. Ainda na **Guia Explorer**, dentro da pasta **Controllers**, vamos excluir a Classe **WeatherForecastController.cs**:

<div align="center"><img src="https://i.imgur.com/CnN43V6.png" title="source: imgur.com" /></div>

3. Depois de excluir os arquivos e pastas, o projeto ficará com a estrutura semelhante ao da imagem abaixo:

<div align="center"><img src="https://i.imgur.com/tnKo0qS.png" title="source: imgur.com" /></div>

<br />

Na sequência, vamos configurar o Ambiente de Execução:

1. No **Gerenciador de Soluções** abra o arquivo **launchSettings.json**, localizado na pasta **Properties**:

<div align="center"><img src="https://i.imgur.com/D7rfHmz.png" title="source: imgur.com" /></div>

2. Localize o trecho de código abaixo:

<div align="center"><img src="https://i.imgur.com/yxdtjy7.png" title="source: imgur.com" /></div>

3. No perfil **http**, na linha 17 (**applicationUrl**), altere o endereço da porta. No exemplo abaixo, **altere a porta 5206 para 5000** e na linha 16, modifique o valor da propriedade **launchUrl** para vazio, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/lOrHQyd.png" title="source: imgur.com" /></div>

4. Veja abaixo o código completo do arquivo **launchSettings.json** após a alteração:

```json
{
  "$schema": "https://json.schemastore.org/launchsettings.json",
  "iisSettings": {
    "windowsAuthentication": false,
    "anonymousAuthentication": true,
    "iisExpress": {
      "applicationUrl": "http://localhost:29699",
      "sslPort": 44338
    }
  },
  "profiles": {
    "http": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "launchUrl": "",
      "applicationUrl": "http://localhost:5000",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "https": {
      "commandName": "Project",
      "dotnetRunMessages": true,
      "launchBrowser": true,
      "launchUrl": "swagger",
      "applicationUrl": "https://localhost:7267;http://localhost:5230",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    },
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "launchUrl": "swagger",
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development"
      }
    }
  }
}
```

<br />

Vamos criar a **Classe HelloController** na pasta **Controllers**:

1. Clique com o botão direito do mouse sobre a **pasta Controllers** e na sequência, clique na opção **New File**.

2. No item **Nome**, digite o nome da Classe (**HomeController.cs**)

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao criar uma nova Classe no VSCode. Diferente do Visual Studio, no VSCode é obrigatório adicionar a extensão do arquivo (.cs).* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

3. A **Guia Explorer** da aplicação ficará semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/9uPJb14.png" title="source: imgur.com" /></div>

Agora vamos criar o código da Classe **HelloController**. Implemente o código abaixo:

```c#
using Microsoft.AspNetCore.Mvc;

namespace helloworld.Controllers
{
    [Route("~/")]
    [ApiController]
    public class HelloController
    {
        [HttpGet]
        public string Hello()
        {
            return "Hello World!";
        }
    }
}
```

Código implementado, vamos executar a aplicação:

1. Digite o comando abaixo no **Terminal** para executar o projeto:

```bash
dotnet run
```

2. O resultado do comando será semelhante a imagem abaixo:

<div><img src="https://i.imgur.com/Ff7ry3d.png" title="source: imgur.com" /></div>

3. Abra o endereço indicado pela seta verde (**http://localhost:5000**) no Navegador da Internet. O resultado será semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/DUtpvJL.png" title="source: imgur.com" /></div>

4. Para finalizar a execução do Projeto, utilize a combinação de teclas **CTRL + C**
5. Para criar novos projetos, siga os passos acima.

