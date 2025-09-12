<h1>Primeiro Projeto Java no STS</h1>

<br />

<h2>👣 Passo 1 - Criar uma nova Workspace</h2>



**Workspace (Espaço de Trabalho)** é a pasta onde você está  trabalhando dentro do STS, ou seja, a pasta onde todos os seus projetos criados no STS serão salvos. 

Quando você inicia o STS pela primeira vez , uma tela semelhante a imagem abaixo é exibida solicitando o caminho da pasta onde o seu  Workspace será criado.

<div align="center"><img src="https://i.imgur.com/S4ViZ95.png" title="source: imgur.com" /></div>

<br />

Para mantermos um padrão de organização, vamos criar uma nova Workspace no STS, onde manteremos os Exercícios desenvolvidos nas Live Codes e os Exercícios Práticos que você desenvolverá nos momentos assíncronos e entregará na Plataforma Canvas.

1. No STS, clique no Menu **File 🡪 Switch Workspace 🡪 Other...**

<div align="center"><img src="https://i.imgur.com/3vBXwwE.png" title="source: imgur.com" /></div>

2. Na janela **Spring Tools for Eclipse Launcher**, clique no botão **Browse...**

<div align="center"><img src="https://i.imgur.com/oY0Q9VT.png" title="source: imgur.com" /></div>

3. Crie a pasta **java** na **Área de Trabalho** e na sequência, clique no botão **Selecionar pasta**. 

<div align="center"><img src="https://i.imgur.com/QAlI5Es.png" title="source: imgur.com" /></div>

4. De volta a janela **Spring Tools for Eclipse Launcher**, no item **Copy Settings**, marque todas as opções, em especial, a opção **Preferences**, para copiar as configurações da Workspace atual para a nova Workspace. Clique no botão **Launch** para concluir.

<div align="center"><img src="https://i.imgur.com/0CPPAeU.png" title="source: imgur.com" /></div>

5. Aguarde o STS reiniciar.
6. O STS será inicializado em uma nova Workspace (pasta java), sem nenhum projeto.

<div align="center"><img src="https://i.imgur.com/RGhf4gP.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 2 - Criar o projeto Java</h2>



Vamos criar nosso primeiro Projeto Java, utilizando o STS:

1. Para criar um novo **Projeto Java**, clique no menu **File 🡪 New 🡪 Java Project**.

<div align="center">
  <img src="https://i.imgur.com/Mr41aZB.png" title="source: imgur.com" />
</div>

2. Será aberta a janela **New Java Project**, onde iremos escolher o nome do projeto. 

<div align="center">
  <img src="https://i.imgur.com/8IFebG8.png" title="source: imgur.com" />
</div>

3. O nosso primeiro projeto Java se chamará **helloworld**. 
3. Digite o nome do projeto no item **Project Name**, selecione o **JavaSE-17** na opção **Use an execution environment JRE**, marque a opção **Create separate folders for sources and class files** e desmarque a opção **Create module-info.java file** e clique em **Finish** para concluir.

<div align="center">
  <img src="https://i.imgur.com/I5od6Km.png" title="source: imgur.com" />
</div>


<br />

> [!TIP]
>
> Uma boa prática ao nomear projetos Java no STS é utilizar **apenas letras minúsculas, sem espaços em branco e caracteres acentuados**.

<br />

> [!IMPORTANT]
>
> O arquivo **module-info.java** é um **arquivo de configuração que define o módulo do seu projeto**. 
>
> Um **módulo** é como uma **caixa fechada** com partes do seu programa dentro (classes, pacotes, etc.). Ele **expõe apenas o que for necessário** para o mundo externo e **esconde o resto**. Isso ajuda a tornar os programas mais organizados, seguros e fáceis de manter.
>
> Este arquivo **não é obrigatório** em projetos pequenos, ele só é necessário quando você:
>
> - Deseja usar o **sistema de módulos do Java**;
> - Está trabalhando com aplicações **modulares**;
> - Quer um controle mais preciso sobre dependências e visibilidade de pacotes.
>
> Ao desmarcar esta opção durante a criação do projeto, nos próximos projetos, ela **não ficará mais habilitada por padrão**.

<br />

5. A janela **New Java Project** será fechada e voltaremos a tela padrão
6. Observe na janela **Package Explorer** que o projeto foi criado, como vemos na imagem abaixo:

<div align="center">
  <img src="https://i.imgur.com/1P37FC0.png" title="source: imgur.com" />
</div>


Um projeto Java é composto por vários elementos que ajudam na organização e execução do código. Veja abaixo os principais:

- **`aula_01/`**: É a **pasta principal do projeto**, onde ficam todos os arquivos e configurações. O nome pode variar conforme o nome escolhido ao criar o projeto.
- **`JRE System Library [JavaSE-17]`**:  Representa a **biblioteca padrão do Java**, também conhecida como **Java Runtime Environment (JRE)**. Ela contém todas as classes essenciais da linguagem (como `System`, `String`, `Math`, entre outras) que seu programa pode usar.
- **`src/`**: É a **Source Folder**, ou seja, a **pasta de código-fonte**. Nela ficam os **pacotes** e **arquivos `.java`** com o código fonte que você escreveu. É a principal área de desenvolvimento do projeto.

<br />

<h2>👣 Passo 3 - Criar a Classe main</h2>



Uma **classe** é uma **estrutura fundamental na programação orientada a objetos** que serve como um **modelo ou molde** para criar objetos. Ela define **propriedades (atributos)** e **comportamentos (métodos)** que os objetos criados a partir dela terão.

A **classe `Main`** é a **classe principal de um programa Java**, ou seja, aquela que **inicia a execução do sistema**. Ela **contém o método especial chamado `main`**, que o Java procura quando o programa é executado. Todo o projeto Java que precisa ser executado, obrigatoriamente deve ter uma classe main.

A classe main pode ter qualquer nome que você desejar, seguindo o padrão **Pascal Case**, mas ela obrigatoriamente  **deve conter o método `main`** com essa assinatura para que o programa possa ser executado.

<br />

> [!TIP]
>
> **Pascal Case** (também chamado de **Upper Camel Case**) é uma convenção de nomenclatura onde **todas as palavras começam com letra maiúscula**, e elas são unidas sem espaços — parecido com o Camel Case, mas a primeira letra também é maiúscula. Os **Nomes das classes da Linguagem Java** sempre usam o padrão Pascal Case para facilitar a identificação.
>
> **Exemplos de Pascal Case:**
>
> - `MinhaClasse`
> - `ContaBancaria`
> - `CalculadoraSimples`

<br />

Vamos criar a nossa primeira classe Java, chamada **HelloWorld**:

1. Clique com o botão direito do mouse sobre a pasta **src** e no menu que será aberto, clique na opção **New 🡪 Class**:

<div align="center">
  <img src="https://i.imgur.com/2349otR.png" title="source: imgur.com" />
</div>


2. Na janela **New Java Class**, no item **Name:** informe o nome da Classe: **HelloWorld** (indicado pela seta vermelha), marque a opção **public static void main(String[] args)** - (indicado pela seta azul), para criar o método `main` e clique no botão **Finish** para concluir.

<div align="center">
  <img src="https://i.imgur.com/EDhXtVt.png" title="source: imgur.com" />
</div>


3. Na janela **Package Explorer**, observe que o pacote, anteriormente vazio, mudou de cor, indicando que existe conteúdo em seu interior, no caso, a classe **HelloWorld**:

<div align="center">
  <img src="https://i.imgur.com/Mfe5qGt.png" title="source: imgur.com" />
</div>


4. Observe também que a Classe **HelloWorld** será aberta na Área de Edição do Código.

<div align="center">
  <img src="https://i.imgur.com/4Otj4rn.png" title="source: imgur.com" />
</div>


5. Na sequência, adicione o código abaixo dentro das chaves do método **public static void main(String[ ] args)**: 

```java
System.out.println("Hello World");
```

6. Na imagem abaixo, você confere o código adicionado na classe **HelloWorld**:

<div align="center">
  <img src="https://i.imgur.com/yTo8THD.png" title="source: imgur.com" />
</div>


Vamos entender o código:

**Linha 01:** Define o **pacote** onde essa classe está. Um pacote é como uma "pasta" que ajuda a organizar o projeto.

**Linha 03:** Declara uma **classe pública** chamada `HelloWorld`. É a estrutura principal onde o programa será escrito. O nome segue o padrão **Pascal Case**, como é comum em nomes de classes em Java.

**Linha 05:** Esse é o **método `main`**, o **ponto de entrada** do programa Java. É onde a execução começa. Vamos quebrar a frase para uma melhor compreensão:

- `public`: qualquer parte do programa pode acessar esse método.
- `static`: pertence à classe e pode ser chamado sem criar um objeto.
- `void`: não retorna nenhum valor.
- `main`: nome especial reconhecido pela JVM.
- `String[] args`: permite passar argumentos de linha de comando ao executar o programa.

**Linha 06:** Exibe o texto **"Hello World"** no console. Esse comando imprime uma mensagem. O comando  `System.out.println()` vem da biblioteca padrão do Java e é usado para **mostrar saídas no terminal**.

**Linha 07:** Fecha o bloco do método `main`.

**Linha 08:** Fecha o bloco da classe `HelloWorld`.

7. Como fizemos uma alteração na classe, podemos notar que ao lado de seu nome existe um **asterisco(*)**, indicando que uma alteração foi feita e que ainda não foi salva. Feito isso, iremos salvar pressionando o atalho **CTRL + S**, ou **clicando no ícone Salvar na Barra de Ferramentas** (indicado em vermelho na imagem):

<div align="center">
  <img src="https://i.imgur.com/vRrzdwZ.png" title="source: imgur.com" />
</div>
<br />

<h2>👣 Passo 4 - Executar o projeto</h2>



Após salvarmos, observe que o asterisco desapareceu, indicando que nossa classe está pronta para ser testada com a modificação que fizemos anteriormente.

1. Para executarmos o Projeto, clique no botão <img src="https://i.imgur.com/t28CIT4.png" title="source: imgur.com" width="4%"/>**Run**, localizado na **Barra de Ferramentas** (indicado em vermelho na imagem):

<div align="center">
  <img src="https://i.imgur.com/iV0f13W.png" title="source: imgur.com" />
</div>
2. O STS exibirá a janela **Run As**, perguntando como o projeto será executado. Clique na opção **Java Application** e clique em **OK** para continuar:

<div align="center">
  <img src="https://i.imgur.com/oVWA2PX.png" title="source: imgur.com" />
</div>
3. Observe na Área de Saída, na guia **Console**, que será exibida a mensagem: **Hello World**.

<div align="center">
  <img src="https://i.imgur.com/24TktV3.png" title="source: imgur.com" />
</div>


Parabéns! Você criou seu primeiro projeto Java, contendo: um Pacote, uma Classe Java e executou este programa dentro do **STS**.

<br />

## <img src="https://i.imgur.com/T9MiDNG.png" title="source: imgur.com" width="5%"/> Exemplo 01 - Hello World

```java
package aula_01;

public class HelloWorld {

	public static void main(String[] args) {
		System.out.println("Hello World");
	}

}
```

<br />

<h2>👣 Passo 5 - Versionar a Workspace do projeto com o Git</h2>



Ao trabalhar com **Eclipse**, **Spring Tool Suite (STS)** ou qualquer outra IDE baseada em workspace, é comum centralizar diversos projetos Java dentro de uma mesma pasta chamada **workspace**. Isso facilita a organização, o carregamento automático pela IDE e o gerenciamento unificado dos projetos.

Para ambientes educacionais ou de desenvolvimento integrado, uma prática comum e eficiente é aplicar o **versionamento em nível de workspace**, ou seja:

> ✅ **Todos os projetos dentro da mesma workspace serão versionados juntos, dentro de um único repositório Git.**

Essa abordagem permite:

- Rastrear todas as mudanças dos projetos em um só lugar.
- Compartilhar a workspace completa com outros desenvolvedores.
- Manter consistência e histórico centralizado.

A seguir, vamos configurar o versionamento local da **Workspace java**:

1. Acesse o Terminal do STS e verifique se o diretório atual está apontando para a pasta `Workspace java`, conforme mostrado na imagem abaixo. Essa verificação garante que todas as ações sejam executadas no local correto do projeto.

<div align="center">
  <img src="https://i.imgur.com/AQMkYsY.png" title="source: imgur.com" />
</div>


<br />

> [!TIP]
>
> Caso o Terminal do STS não tenha iniciado na pasta `Workspace java`, é provável que essa configuração não tenha sido feita durante a instalação do STS. Feche o Terminal do STS, acesse o *Guia de Instalação do STS*, localize o tópico **Configuração do Terminal** e siga as instruções para corrigir esse ajuste.

<br />

2. Inicialize o repositório Git através do comando abaixo:

```bash
git init
```

Esse comando cria um repositório Git na raiz da sua workspace, tornando possível versionar tudo que está dentro dela.

3. Crie o arquivo `.gitignore` através do comando abaixo:

```bash
touch .gitignore
```

4. Abra o arquivo `.gitignore` no **Notepad (Bloco de Notas)**, através do comando abaixo:

```bash
notepad .gitignore 
```

5. Adicione as regras as regras abaixo no arquivo e salve as alterações:

```gitignore
# ================================
# Arquivos comuns de Java
# ================================
*.class
*.jar
*.war
*.ear
*.log

# ================================
# Pastas de build/output
# ================================
bin/
build/
target/
out/

# ================================
# Eclipse / Spring Tool Suite (STS)
# ================================
.classpath
.project
.settings/
.springBeans
.factorypath
.metadata/

# ================================
# IntelliJ IDEA
# ================================
.idea/
*.iml
*.iws
*.ipr
out/

# ================================
# VS Code
# ================================
.vscode/

# ================================
# Arquivos de sistema (Windows / macOS / Linux)
# ================================
.DS_Store
Thumbs.db
ehthumbs.db
*.swp
*.swo
```

<br />

> O Git enxerga cada arquivo no seu repositório com um dos três estados abaixo:
>
> 1. **Rastreado** – Um arquivo que já passou pela área de staging ou já foi comitado.
> 2. **Não rastreado** – Um arquivo que *não* passou pela área de staging ou commit.
> 3. **Ignorado** – Um arquivo que o Git foi instruído a ignorar.
>
> Os arquivos ignorados costumam ser artefatos de desenvolvimento e arquivos gerados automaticamente, que podem ser derivados da fonte do seu repositório ou que não devem ser incluídos no controle de versão. O repositório criado na workspace Java, por exemplo, deve ignorar os seguintes arquivos e pastas:
>
> - `*.class`, `bin/`, `target/`: ignoram arquivos compilados e pastas de build.
> - `.classpath`, `.project`, `.settings/`: arquivos específicos do Eclipse/STS.
> - `.idea/`, `*.iml`: arquivos e pastas usados pelo IntelliJ.
> - `.vscode/`: configurações do VS Code.
> - `.DS_Store`, `Thumbs.db`: arquivos ocultos criados por sistemas operacionais.
>
> Os arquivos e pastas que devem ser ignorados são definidos em um arquivo especial chamado `.gitignore`, que deve estar localizado na raiz do repositório. **Não existe um comando específico `git ignore`**: é necessário criar, editar e versionar manualmente o arquivo `.gitignore` sempre que novos arquivos precisarem ser ignorados.
>
> Os arquivos `.gitignore` contêm padrões que são comparados com os nomes de arquivos do repositório para determinar se devem ou não ser ignorados. Por isso, adicionamos o arquivo `.gitignore` manualmente ao repositório e realizamos o commit, garantindo que essas regras sejam aplicadas a todos que utilizam o projeto.

6. Adicione todos os arquivos que devem ser versionados através do comando abaixo:

```bash
git add .
```

Esse comando adiciona todos os arquivos (exceto os ignorados pelo `.gitignore`) para o controle de versão.

7. Faça o primeiro commit através do comando abaixo:

```bash
git commit -m ":tada: Commit inicial - Projeto Hello World"
```

👉 Neste commit, usamos o emoji `:tada:` para indicar que este é o primeiro commit do repositório, conforme o padrão de commits semânticos.

A sua **workspace Java** agora está versionada com Git, e todos os projetos contidos nela serão acompanhados por esse único repositório.

<br />

<h2>👣 Passo 6 - Enviar a Workspace para o Github</h2>



1. Acesse o seu **Github** e crie um novo **Repositório**, através da opção **New repository**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/NRl8O7Y.png" title="source: imgur.com" /></div>

2. Crie o **Repositório Remoto** chamado **java**:

<div align="center"><img src="https://i.imgur.com/jgNbYAy.png" title="source: imgur.com" /></div>

3. Clique no botão **Create Repository**, para criar o Repositório:

<div align="center"><img src="https://i.imgur.com/d9cRI9m.png" title="source: imgur.com" /></div>

4. Na próxima janela, copie o endereço **HTTPS do Repositório Remoto**, indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/pIfU6Sx.png" title="source: imgur.com" /></div>

5. Volte para o Terminal do STS e execute o comando abaixo para conectar o seu **Repositório Local** com o seu **Repositório Remoto**, onde o endereço **https**, será o endereço do seu **Repositório Remoto**.

```bash
git remote add origin https://github.com/rafaelq80/java.git
```

<br />

> [!IMPORTANT]
>
> Substitua o endereço: `https://github.com/rafaelq80/java.git` pelo endereço do seu repositório remoto.

<br />

6. Digite o comando abaixo para checar se o seu  **Repositório Local** está conectado com o seu **Repositório Remoto**:

```bash
git remote -v
```

7. Se estiver conectado, será exibida uma mensagem no console, semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Y0DNDic.png" title="source: imgur.com" /></div>

8. Na sequência, utilize o comando abaixo, para sincronizar o conteúdo do **Repositório Local** com o seu **Repositório Remoto**:

```bash
git push origin main
```

9. Volte para o Github, atualize a página do seu **Repositório Remoto** e verifique se ele está semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/5PNDqQ7.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 7 - Adicionar o README no Repositório</h2>



Vamos criar o arquivo `README.md`, que servirá como documento principal de apresentação do repositório. Esse procedimento é necessário apenas uma vez por repositório e será feito dentro da pasta versionada.

1. Acesse o terminal e verifique se ele está na pasta Workspace java, como vemos na imagem abaixo:

<div align="center">
  <img src="https://i.imgur.com/uqRsPgI.png" title="source: imgur.com" />
</div>

<br />

> [!TIP]
>
> Caso o Terminal do STS não tenha iniciado na pasta `Workspace java`, é provável que essa configuração não tenha sido feita durante a instalação do STS. Feche o Terminal, acesse o *Guia de Instalação do STS*, localize o tópico **Configuração do Terminal** e siga as instruções para corrigir esse ajuste.

<br />

2. Crie o arquivo `README.md` através do comando abaixo:

```bash
touch README.md
```

<br />

> [!WARNING]
>
> Certifique-se de digitar `README.md` exatamente como está no comando: o nome do arquivo em letras maiúsculas e a extensão em letras minúsculas.

<br />

3. Abra o arquivo `README.md` no **Notepad (Bloco de Notas)**, através do comando abaixo:

```bash
notepad README.md
```

4. Na sequência, insira o código disponível no arquivo **Modelo README** (link para download abaixo), personalizando as informações com os seus dados (usuario do github, nome do repositório, entre outros):

<img src="https://i.imgur.com/dAhbLLw.png" title="source: imgur.com" width="7%" />[**Download - Modelo README**](https://github.com/conteudoGeneration/cookbook_java_fullstack/blob/main/arquivos/modelo_readme_b1_java.md) 

<br />

> [!IMPORTANT]
>
> **Não se esqueça de personalizar o `README.md` do seu repositório. É fundamental ajustar as informações para refletir corretamente o seu projeto. Atente-se especialmente aos seguintes pontos:**
>
> - 🔁 **Atualize o nome do seu usuário do GitHub** nos *badges* e links;
> - 📁 **Substitua o nome do repositório** nos *badges, links* e nos comandos como `git clone`;
>
> Essas alterações garantem que as informações exibidas estejam corretas e vinculadas ao seu repositório.

<br />

> [!TIP]
>
> Para facilitar o processo de edição do arquivo Markdown, utilize o Editor online **Stack Edit**. 
>
> <div align="left"><img src="https://i.imgur.com/PAuGwNi.png" title="source: imgur.com" width="4%"/> <a href="https://stackedit.io/app" target="_blank"><b>Stack Edit</b></a></div>

<br />

<h2>👣 Passo 8 - Atualizar o Repositório Local e Remoto</h2>



Ao longo das sessões do Bloco 01, diversos projetos serão criados dentro da pasta `Workspace java`. Para mantê-los documentados e versionados, você \**não precisará criar um novo repositório\** a cada novo projeto. Assim como faremos a atualização do `README.md`, também atualizaremos o repositório com os novos projetos adicionados.

Em vez de repetir todo o processo de criação de repositório, basta seguir os passos abaixo para atualizar o repositório local e remoto já existente:

1. Digite o comando abaixo para adicionar as alterações na **Stage Area** do Git:

```bash
git add .
```

2. Na sequência, faça o commit das alterações, através do comando abaixo:

```bash
git commit -m ":books: Criação do README.md do repositório"
```

👉 Neste commit, usamos o emoji `:books:` para indicar uma alteração relacionada à documentação, conforme o padrão de commits semânticos.

3. Na sequência, utilize o comando abaixo, para sincronizar o conteúdo do **Repositório Local** com o seu **Repositório Remoto**:

```bash
git push origin main
```

4. Volte para o Github, atualize a página do seu **Repositório Remoto** e verifique se ele foi atualizado com a adição do **README** do projeto, semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Vys2Kao.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> Ao criar um **novo projeto** dentro da pasta `Workspace java`, a mensagem de commit deve seguir os padrões dos commits semânticos, usando um emoji que represente a adição de algo novo.
>
> Use o emoji `:sparkles:` para indicar a criação de um projeto, como neste exemplo:
>
> ```bash
> git commit -m ":sparkles: Criação do projeto NomeDoProjeto"
> ```
>
> Já para atualizar um **projeto existente** no repositório — seja para adicionar funcionalidades, corrigir erros ou ajustar o código — use emojis que indiquem claramente o tipo de mudança feita.
>
> Aqui estão alguns exemplos comuns:
>
> - `:sparkles:` para **novas funcionalidades**:
>
>   ```bash
>   git commit -m ":sparkles: Criação da classe Calculadora"
>   ```
>
> - `:bug:` para **correção de erros**:
>
>   ```bash
>   git commit -m ":bug: Correção do método calcularRaiz da classe Calculadora"
>   ```
>
> - `:recycle:` para **refatoração** (melhorias no código sem alterar seu funcionamento):
>
>   ```bash
>   git commit -m ":recycle: Refatoração do método cadastrarConta da classe Conta"
>   ```
>
> - `:art:` para **melhorias visuais ou de formatação**:
>
>   ```bash
>   git commit -m ":art: Ajustes na identação e organização do código"
>   ```

<br />
