<h1>Projeto Integrador - Criando Variáveis de Ambiente no Spring</h1>



Variáveis de ambiente são **valores externos ao código da aplicação**, usados para **armazenar informações sensíveis ou configuráveis**, como:

- credenciais (usuário e senha do banco);
- chaves de API;
- URLs de serviços externos;
- portas de rede.

Essas variáveis permitem que o mesmo código funcione em **diferentes ambientes** (desenvolvimento, teste, produção) sem precisar alterar o código-fonte.

O Spring Boot, por padrão, já lê variáveis de ambiente do sistema e do arquivo `application.properties`, mas, se quiser usar um **arquivo `.env`** (como no Node.js), para armazenar as variáveis e ocultar os valores no GitHub, é necessário adicionar a Dependência **Dotenv**.

A Dependência **Dotenv** permite:

- Ler automaticamente o arquivo `.env` na inicialização;
- Tornar essas variáveis disponíveis dentro do Spring.

Vamos configurar o **Projeto Loja de Games** para ler arquivos **.env**:

<br />

<h2>👣 Passo 01 - Adicionar a Dependência Dotenv</h2>



Vamos adicionar a Dependência **Dotenv** no arquivo **`pom.xml`**: 

1. Abra o arquivo **`pom.xml`**, através do STS
2. Localize o trecho de código indicado na imagem abaixo:

<div align="center"><img src="https://imgur.com/DUvbbop.png" title="source: imgur.com" /></div>

3. No local indicado, **cole o trecho de código abaixo** e **salve o arquivo `pom.xml`** para que o Spring Boot realize o **download automático da dependência Dotenv**.

```xml
<!-- Dependência para leitura de variáveis de ambiente-->
<dependency>
	<groupId>io.github.cdimascio</groupId>
	<artifactId>dotenv-java</artifactId>
	<version>3.0.0</version>
</dependency>
```

4. Na imagem abaixo, vemos o resultado:

<div align="center"><img src="https://imgur.com/UON3JJB.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> O código deve ser inserido **exatamente** como mostrado na imagem acima, respeitando as **identações** e o padrão de formatação do **XML**.

<br />

> [!WARNING]
>
> **Não insira a dependência Dotenv dentro de outra dependência**. Cada bloco `<dependency>` deve ser independente e corretamente fechado com a tag `</dependency>`.

<br />

<h2>👣 Passo 02 - Configurar o Package Explorer para exibir arquivos ocultos</h2>



O arquivo **`.env`**, que será criado no próximo passo, é um **arquivo oculto**, assim como o arquivo **`.gitignore`**, por exemplo. Por esse motivo, ele **não será exibido por padrão** na janela **Package Explorer** do STS.

Antes de criarmos o arquivo, vamos **configurar o Package Explorer do STS para exibir arquivos ocultos**, garantindo que o `.env` fique visível na estrutura do projeto.

1. Observe que na janela **Package Explorer**, existe um ícone com 3 pontos, como mostra a imagem abaixo:

<div align="center"><img src="https://imgur.com/GIMvPmh.png" title="source: imgur.com" /></div>

2. Clique nos 3 pontos e no menu que será aberto, clique na opção **Filters...**

<div align="center"><img src="https://imgur.com/AJ7wv9j.png" title="source: imgur.com" /></div>

3. Na janela **Java Element Filters**, desmarque a opção **`.*resources`** e clique em **OK** para concluir

<div align="center"><img src="https://imgur.com/mvIZoeG.png" title="source: imgur.com" /></div>

4. Observe que os arquivos ocultos ficarão visíveis, como o **.gitgnore**, por exemplo:

<div align="center"><img src="https://imgur.com/QRrsbSR.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 03 - Criar o arquivo .env</h2>



Para **proteger as informações sensíveis** da aplicação, como os **dados de conexão com o banco de dados** e a **chave de assinatura do token JWT (Secret)**, vamos **ocultar esses valores** utilizando **variáveis de ambiente**. Essas variáveis serão definidas no arquivo **`.env`**, que deverá ser criado na **pasta raiz do projeto Spring**.

1. **Selecione a pasta raiz do Projeto Spring**, clique com botão direito do mouse e clique na opção: **New 🡢 File**

<div align="center"><img src="https://imgur.com/MJ3Yfmp.png" title="source: imgur.com" /></div>

2. Na janela **Create New File**, no item **File name**, informe o nome do arquivo (**.env**), como mostra a imagem abaixo e clique no botão **Finish**.

<div align="center"><img src="https://imgur.com/u1pLxYo.png" title="source: imgur.com" /></div>

<br />

> [!CAUTION]
>
> Um erro muito comum é **criar o arquivo `.env` dentro de alguma pasta interna do projeto**.
>
> O arquivo **`.env` deve estar obrigatoriamente na pasta raiz do projeto**, conforme indicado na estrutura do projeto, na imagem abaixo. Caso seja criado em outro local, **a aplicação não conseguirá localizar as variáveis de ambiente**, e recursos como a **conexão com o banco de dados** deixarão de funcionar corretamente.

<br />

<div align="center"><img src="https://imgur.com/XmNiP8L.png" title="source: imgur.com" /></div>

3. Dentro desse arquivo, iremos adicionar as nossas variáveis de ambiente, que irão armazenar os dados de conexão com o Banco de dados e a Chave de Assinatura do Token JWT (Secret), conforme o exemplo abaixo:

```bash
MYSQLHOST=localhost
MYSQLPORT=3306
MYSQLDATABASE=db_lojagames
MYSQLUSER=root
MYSQLPASSWORD=root
JWT_SECRET=292d7161c76174f0784a14f860756497073fe5c187de42f87a2060c5f06c7877
```

<br />

> [!WARNING]
>
> Os nomes das variáveis devem ser escritos em letras maiúsculas e sem espaços em branco(**MYSQLHOST**).

<br />

4. Adicione o conteúdo acima, **ajustando os valores conforme as configurações da sua máquina**, e **salve o arquivo**.

<br />

<h2>👣 Passo 04 - Adicionar o arquivo .env no arquivo .gitignore</h2>



Vamos modiﬁcar o nosso arquivo **.gitignore**, para que o nosso arquivo **.env** não seja enviado para o Github, funcionando apenas no nosso computador, da seguinte forma:

1. Abra o arquivo **.gitignore**, localizado na pasta raiz do projeto:

<div align="center"><img src="https://imgur.com/QRrsbSR.png" title="source: imgur.com" /></div>

2. Adicione a linha abaixo no arquivo **.gitignore**:

```bash
### Variáveis de Ambiente ###
.env
```

3. Após a alteração, o arquivo **.gitignore** ficará semelhante a imagem abaixo:

<div align="center"><img src="https://imgur.com/UjTeOmn.png" title="source: imgur.com" /></div>

A linha adicionada pode ser colocada em qualquer ponto do arquivo, não precisa estar exatamente no mesmo local indicado na imagem acima.

<br />

<h2>👣 Passo 05 - Configurar o Banco de dados</h2>



Vamos configurar a conexão com o Banco de dados através das variáveis de ambiente criadas no arquivo **.env**:

1. Abra o arquivo **application.properties** e substitua o seu conteúdo pelo trecho de código abaixo:

```properties
spring.application.name=lojagames

spring.jpa.hibernate.ddl-auto=update

spring.datasource.url=jdbc:mysql://${MYSQLHOST}:${MYSQLPORT}/${MYSQLDATABASE}?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSl=false
spring.datasource.username=${MYSQLUSER}
spring.datasource.password=${MYSQLPASSWORD}
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.show-sql=true
spring.jpa.open-in-view=true
spring.jpa.properties.hibernate.jdbc.time_zone=America/Sao_Paulo

spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=America/Sao_Paulo
spring.jackson.serialization.write-dates-as-timestamps=false
```

Observe que **todas as configurações do banco de dados foram substituídas pelas variáveis de ambiente**.
 Note que **cada variável foi inserida no código utilizando a sintaxe** `${NOME_DA_VARIAVEL}`.

<br />

<h2>👣 Passo 06 - Configurar a inicialização da Dependência Dotenv</h2>



Vamos configurar a inicialização da Deepndência `Dotenv` dentro da Classe principal da aplicação Spring Boot:

1. Abra a Classe principal da aplicação Spring. No projeto Loja de Games, a classe se chama **LojagamesApplication** e está localizada no pacote principal da aplicação - **com.generation.lojagames**, como vemos na imagem abaixo:

<div align="center"><img src="https://imgur.com/xxqe3da.png" title="source: imgur.com" /></div>

2. Localize o trecho indicado na imagem abaixo:

<div align="center"><img src="https://imgur.com/xX03lPT.png" title="source: imgur.com" /></div>

3. No local indicado, insira as linhas abaixo:

```java

try {
	Dotenv dotenv = Dotenv.configure().ignoreIfMissing().load();

	dotenv.entries().forEach(entry -> System.setProperty(entry.getKey(), entry.getValue()));
} catch (Exception e) {
	System.out.println("Running without .env file - using environment variables");
}
```

4. Na imagem abaixo, vemos o resultado:

<div align="center"><img src="https://imgur.com/6VmNHlE.png" title="source: imgur.com" /></div>

Na **linha 13**, o código entra em um **bloco `try`**, que serve para **tentar executar o carregamento do arquivo `.env`** e capturar qualquer exceção caso o arquivo não exista ou ocorra algum erro durante o processo.

Na **linha 15, é criada uma instância da classe **`Dotenv`**utilizando **`Dotenv.configure().ignoreIfMissing().load()`**. Essa chamada faz com que a aplicação **procure automaticamente pelo arquivo `.env` na raiz do projeto**. 

O parâmetro **`ignoreIfMissing()`** garante que, se o arquivo não existir, **nenhum erro será lançado**, permitindo que a aplicação continue rodando normalmente.

Na **linha 17**, o código **percorre todas as entradas do arquivo `.env`** — ou seja, cada variável definida no padrão `chave=valor`. Para cada entrada, é chamado **`System.setProperty(entry.getKey(), entry.getValue())`**, que **adiciona a variável como propriedade do sistema Java**.

Dessa forma, essas variáveis ficam **disponíveis em toda a aplicação**, podendo ser acessadas via `System.getProperty("NOME_DA_VARIAVEL")` ou usando **Spring** com `@Value("${NOME_DA_VARIAVEL}")`.

Na **linha 18**, o bloco `catch` captura qualquer exceção lançada durante o processo de leitura do arquivo `.env`. Se ocorrer um erro, a aplicação **exibe uma mensagem no console**: `"Running without .env file - using environment variables"`. Isso indica que a aplicação continuará funcionando, **utilizando apenas as variáveis de ambiente do sistema**, sem depender do `.env`.

✅ **Resumo:** Esse trecho **carrega variáveis do arquivo `.env` e as transforma em propriedades do sistema**, garantindo que a aplicação possa acessar informações sensíveis sem incluí-las diretamente no código-fonte, e **trata a ausência do arquivo de forma segura**.

<br />

<h2>👣 Passo 07 - Adicionar a variável JWT_SECRET no arquivo application.properties</h2>



Depois de configurar a Spring Security, podemos ocultar a `secret` através de variáveis de ambientes. Vamos adicionar a variável **`JWT_SECRET`** dentro do arquivo **`application.properties`**:

1. Abra o arquivo **application.properties** e adicione no final do seu conteúdo o trecho de código abaixo:

```
jwt.secret=${JWT_SECRET}
```

2. Ao adicionar a variável, note que será exibida uma mensagem de **warning**, como vemos na imagem abaixo:

<div align="center"><img src="https://imgur.com/fSXkXoL.png" title="source: imgur.com" /></div>

3. Passe o mouse sobre a variável (`jwt.secret`) e observe que será exibida a mensagem abaixo, pedindo para criar um metadata para a variável de ambiente.

<div align="center"><img src="https://imgur.com/ggge7KC.png" title="source: imgur.com" /></div>

4. Clique no link **Create metadata for** e observe que o warning desaparecerá.

> No contexto do STS/Eclipse, o **metadata** é apenas um **registro descritivo da propriedade**. Ele não altera o comportamento do Spring Boot nem do JWT; serve apenas para **melhorar o suporte da IDE**, autocomplete e documentação interna.

<br />

<h2>👣 Passo 08 - Configurar a Secret na Classe JwtService</h2>



Vamos configurar a Chave de assinatura do Token JWT (Secret), na Classe **JwtService**, através da variável de ambiente criada no arquivo **.env**:

1. Abra a **Classe JwtService**, localizada no pacote **security**
2. localize a linha indicada na imagem abaixo:

<div align="center"><img src="https://imgur.com/bpmnrSq.png" title="source: imgur.com" /></div>

3. Substitua esta linha pelo trecho de código abaixo:

```java
@Value("${jwt.secret}")
private String secret;
```

4. O resultado da alteração você confere abaixo:

<div align="center"><img src="https://imgur.com/5c9LaMN.png" title="source: imgur.com" /></div>

**linha 18:** A anotação **`@Value("${jwt.secret}")`** no Spring Boot **injeta o valor da propriedade `jwt.secret`** do `application.properties` ou das variáveis de ambiente diretamente em um **atributo da classe**, permitindo que você use essa configuração no código.

Execute o o seu projeto e verifique se tudo está funcionando!
