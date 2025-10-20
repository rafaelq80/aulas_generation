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

Vamos configurar o Spring para ler arquivos **.env**:

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

<h2>👣 Passo 04 - Configurar o Banco de dados</h2>



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

<h2>👣 Passo 05 - Criar a Classe DotenvConfig</h2>



A `DotenvConfig` é uma **classe de configuração** usada para **carregar variáveis de ambiente a partir de um arquivo `.env`** e disponibilizá-las para a aplicação Spring Boot.

**Função principal:**

- Lê o arquivo `.env` na inicialização da aplicação;
- Torna os valores acessíveis através de `System.getenv()` ou propriedades do Spring (`@Value("${VARIAVEL}")`);
- Evita que informações sensíveis fiquem no código-fonte.

Vamos criar a classe **DotenvConfig** dentro do pacote **configuration**:

1. Crie a classe **DotenvConfig** dentro do pacote **configuration**, como vemos na imagem abaixo:

<div align="center"><img src="https://imgur.com/nxyXhui.png" title="source: imgur.com" /></div>

2. Observe que será criado o pacote **com.generation.lojagames.configuration** e dentro dele, será criada a Classe **Dotenvconfig**:

<div align="center"><img src="https://imgur.com/ikISAdE.png" title="source: imgur.com" /></div>

3. Adicione o código abaixo dentro da classe **DotenvConfig** e salve o arquivo:

<div align="center"><img src="https://imgur.com/k68yHNo.png" title="source: imgur.com" /></div>

Na **linha 14**, a anotação **`@Configuration`** indica que a classe é uma **classe de configuração do Spring**, ou seja, ela pode definir beans e configurar componentes da aplicação de forma centralizada.

Na **linha 15**, a classe implementa a interface **`ApplicationContextInitializer`**, que permite **executar código durante a inicialização do contexto do Spring**, antes que todos os beans da aplicação — como entidades, services e controllers — sejam carregados. Isso é útil quando precisamos preparar ou modificar propriedades do ambiente antes do restante da aplicação ser inicializado.

Nas **linhas 17 e 18**, o método obrigatório da interface, **`initialize`**, é implementado. É dentro desse método que colocamos a lógica de carregamento das variáveis de ambiente.

Entre as **linhas 19 e 22**, é criada uma instância da classe **`Dotenv`**, responsável por **ler o arquivo `.env`**. O código está configurado para procurar o arquivo na **pasta raiz do projeto**, ignorar o erro caso ele não exista e carregar todas as variáveis definidas nesse arquivo.

Na **linha 24**, é obtido o **`ConfigurableEnvironment`** do Spring, que representa o ambiente configurável da aplicação. Isso permite que novas propriedades sejam adicionadas dinamicamente ao contexto da aplicação.

Na **linha 25**, é criada uma coleção **`Map`** vazia chamada `envMap`, que será usada para armazenar as variáveis carregadas do `.env`.

Entre as **linhas 27 e 29**, o código percorre todas as entradas do arquivo `.env` (cada variável definida como `chave=valor`) e adiciona cada par chave-valor ao `envMap`.

Por fim, nas **linhas 31 e 32**, o `envMap` é adicionado como uma **nova fonte de propriedades** ao Spring através de `MapPropertySource`. Ao usar `addFirst`, garantimos que essas variáveis tenham **prioridade máxima**, podendo **sobrescrever outras propriedades** definidas em `application.properties` ou em outras fontes de configuração do Spring.

<br />

<h2>👣 Passo 06 - Configurar a inicialização da Classe DotenvConfig</h2>



Vamos adicionar a Classe `DotenvConfig` para inicializar dentro da Classe principal da aplicação Spring Boot:

1. Abra a Classe principal da aplicação Spring. No projeto Loja de Games, a classe se chama **LojagamesApplication** e está localizada no pacote principal da aplicação - **com.generation.lojagames**, como vemos na imagem abaixo:

<div align="center"><img src="https://imgur.com/xxqe3da.png" title="source: imgur.com" /></div>

2. Localize o trecho indicado na imagem abaixo:

<div align="center"><img src="https://imgur.com/xX03lPT.png" title="source: imgur.com" /></div>

3. No local indicado, insira as linhas abaixo:

```java
Dotenv dotenv = Dotenv.load();

dotenv.entries().forEach(entry -> System.setProperty(entry.getKey(), entry.getValue()));
```

4. Na imagem abaixo, vemos o resultado:

<div align="center"><img src="https://imgur.com/ElnoVY6.png" title="source: imgur.com" /></div>

Na **linha 13**, é criada uma instância da classe **`Dotenv`**, que automaticamente **procura e carrega o arquivo `.env`** na raiz do projeto. Essa chamada lê todas as variáveis definidas no arquivo, tornando-as disponíveis para uso dentro da aplicação.

Na **linha 15**, o código **percorre todas as entradas do `.env`**, ou seja, cada variável definida como `chave=valor`. Para cada entrada, é chamado `System.setProperty`, que **adiciona a variável como uma propriedade do sistema Java**. Isso faz com que as variáveis possam ser acessadas a partir de qualquer ponto da aplicação, inclusive pelo Spring, usando métodos como `System.getProperty("NOME_DA_VARIAVEL")` ou através da anotação `@Value("${NOME_DA_VARIAVEL}")`.

Em resumo, essas duas linhas **carregam o `.env` e transformam suas variáveis em propriedades do sistema**, permitindo que a aplicação utilize essas informações sensíveis sem que elas precisem estar inseridas no código-fonte.

<br />

<h2>👣 Passo 07 - Executar e Testar o Projeto</h2>



1. Digite o comando abaixo para compilar e executar o projeto, caso não esteja em execução:

```bash
npm run start:dev
```

2. Teste a aplicação e verifique se tudo está funcionando.
