<h1>Deploy do Backend no Render + Neon</h1>

<br />

## 1. O que é Deploy?

<br />

> O verbo **deploy**, em inglês, significa **implantar**.

No contexto da programação, o termo está diretamente associado à sua tradução literal: **fazer um deploy** significa disponibilizar uma aplicação na Internet, ou seja, **publicá-la na nuvem** após a finalização do seu desenvolvimento.

Quando um site ou sistema é concluído por uma pessoa desenvolvedora, ele passa por testes finais e, em seguida, é **hospedado na nuvem por meio do processo de deploy**. Esse processo torna a aplicação acessível ao público ou aos usuários finais.

Além disso, quando uma aplicação já publicada (em **produção**) recebe melhorias ou alterações em seu código, a **atualização do sistema em produção também é considerada um deploy** — nesse caso, chamado de **deploy incremental**, pois consiste na entrega de uma nova versão da aplicação sem a necessidade de reconstruí-la por completo.

<br />

## 2. O que veremos por aqui?



Esse documento é um passo a passo para você enviar a sua aplicação Spring, gratuitamente para a nuvem. Este processo irá gerar um link de acesso a sua aplicação, que poderá ser acessado de qualquer lugar, a partir de qualquer dispositivo com acesso a Internet. 
Para efetuar o Deploy vamos precisar fazer algumas modificações em nosso projeto, que serão detalhadas nos próximos tópicos.

<br />

## 👣 Passo 01 - Criar a Documentação da API



Para criar a Documentação da API no Swagger, utilize o <a href="24.md" target="_blank">**Guia de Configuração do Springdoc**</a>.

<br />

## 👣 Passo 02 - Testar a API no seu computador



1. **Execute a sua aplicação localmente** utilizando o **STS**.

2. Acesse o endereço: **http://localhost:8080/** no seu navegador.

3. A aplicação deverá exibir a tela de **Login (Usuário e Senha)**. Utilize as credenciais criadas anteriormente:
   - **Usuário:** `root@root.com`
   - **Senha:** `rootroot`


<div align="center"><img src="https://i.imgur.com/mBRxYd8.png" title="source: imgur.com" width="50%"/></div>

4. Caso a aplicação **não solicite o login**, feche todas as janelas do seu navegador, abra novamente e acesse o endereço novamente.

   - Se o problema persistir, **verifique a configuração do Swagger**.
5. Após o login, **verifique se o Swagger está sendo carregado automaticamente**.
6. Caso ainda não tenha testado no **Insomnia**, realize os testes agora e verifique se a aplicação está respondendo corretamente.
7. Em especial, **confirme se o método `logar` está retornando o Token** de autenticação com sucesso.
8. **Antes de prosseguir com a configuração para o Deploy**, **lembre-se de parar a execução da aplicação no STS**.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **IMPORTANTE:**  **Não altere a senha do usuário `root@root.com`**. Os instrutores da sua turma utilizarão este usuário para abrir, testar e corrigir a sua aplicação. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ATENÇÃO:**  Antes de realizar o **Deploy**, é fundamental que a aplicação esteja **100% funcional e sem erros**. Realize todos os testes através o **Insomnia** para garantir que todos os endpoints estão funcionando corretamente.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 👣 Passo 03 - Criar uma conta grátis no Render

<br />

<h3>3.1 O que é o Render?</h3>



O **Render** é uma plataforma unificada para **criação, hospedagem e execução de aplicativos e sites** na nuvem. Ele oferece recursos como **SSL gratuito**, **CDN global**, **rede privada** e **implantações automáticas via Git**, simplificando o ciclo de desenvolvimento e publicação.

> Uma **CDN** (Content Delivery Network – Rede de Entrega de Conteúdo) é um conjunto de servidores distribuídos geograficamente que acelera a entrega de conteúdo na web, aproximando os dados dos usuários finais.

O Render é classificado como uma plataforma do tipo **PaaS (Platform as a Service)**, ou seja, fornece um conjunto de serviços prontos para que desenvolvedores possam criar, integrar, migrar, implantar, proteger e gerenciar aplicações web e móveis de maneira prática e eficiente.

<br />

<h3>3.2. Modelos de Serviços em Nuvem</h3>



- **PaaS (Plataforma como Serviço):** O provedor oferece um ambiente completo baseado em nuvem para o desenvolvimento e execução de aplicações. Exemplos: **Render**, **Heroku**, **Microsoft Azure**.
- **IaaS (Infraestrutura como Serviço):** Fornece recursos de infraestrutura (como servidores, rede e armazenamento) sob demanda. Exemplos: **Amazon Web Services (AWS)**, **DigitalOcean**.
- **SaaS (Software como Serviço):** O provedor disponibiliza softwares e serviços prontos via internet, geralmente sob forma de assinatura. Exemplos: **Google Workspace**, **Microsoft 365**.

<br />

<h3> 3.3. Diferenciais do Render</h3>



Um dos principais atrativos do Render é a oferta de um **plano gratuito**, que permite:

- Hospedar aplicações em diversas linguagens de programação;
- Criar **uma instância gratuita de banco de dados PostgreSQL**.

<br />

<h3> 3.4. Limitações do Plano Gratuito do Render</h3>



- A aplicação é finalizada automaticamente se ficar **15 minutos sem receber requisições**. Ela será reiniciada apenas na próxima solicitação.
- Os servidores estão localizados **apenas na Europa, Ásia e nos Estados Unidos**.
- Os recursos de **memória, CPU e armazenamento** são limitados, tornando-o mais adequado para projetos pequenos ou de testes.
- **Apenas um banco de dados PostgreSQL gratuito por conta** é permitido.
- O banco de dados gratuito **expira após 30 dias**. Um e-mail é enviado próximo da data de expiração.
- O uso total é limitado a **750 horas mensais** (aplicações + banco de dados). Ao ultrapassar esse limite, os serviços são suspensos até o próximo ciclo.
- Dependendo da linguagem utilizada, **o deploy pode exigir o uso de Docker**.

<br />

<div align="left"><img src="https://i.imgur.com/RjyAYeB.png" title="source: imgur.com" width="4%"/> <a href="https://render.com/docs/free" target="_blank"><b>Documentação: Render - Plano Gratuito</b></a></div>

<br />

<h3> 3.5. Limitações do Plano Gratuito do Render</h3>



Vamos criar uma conta gratuita no **Render** para fazermos o Deploy:

1) Acesse o endereço: **https://render.com**
1) Na página inicial do Render, clique no botão **Get Started**, localizado no canto direito superior da tela

<div align="center"><img src="https://i.imgur.com/FSXqGdA.png" title="source: imgur.com"/></div>

3. Será aberta a janela **Create an account**. Observe na imagem abaixo que existem diversas maneiras de criar uma nova conta no Render.

<div align="center"><img src="https://i.imgur.com/aaoTXu2.png" title="source: imgur.com" /></div>

4. Vamos criar uma nova conta no Render utilizando o Github. Clique no botão **GitHub**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/jBDiOq4.png" title="source: imgur.com" /></div>

5. Na próxima janela, caso você não esteja autenticado (logado) na sua conta do Github, será solicitado que você digite o seu usuário ou o endereço do e-mail cadastrado, além da senha da sua conta do Github, e em seguida clique no botão **Sign in**

<div align="center"><img src="https://i.imgur.com/McXaD9t.png" title="source: imgur.com" /></div>

6. Na próxima janela, autorize o Render a acessar a sua conta do Github, clicando no botão **Authorize Render**.

<div align="center"><img src="https://i.imgur.com/i9PbiwS.png" title="source: imgur.com" /></div>

7. Você será redirecionado para a tela do **Render Dashboard**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/4DPfwdN.png" title="source: imgur.com" /></div>

<br />

## 👣 Passo 04 - Adicionar a Dependência do PostgreSQL no pom.xml



A plataforma **Render**, em seu plano gratuito, oferece suporte ao Banco de dados Relacional **PostgreSQL** como sistema gerenciador de banco de dados (SGBD).

No **Bloco 02**, estamos utilizando o **MySQL** para desenvolver o projeto do **Blog Pessoal**. Ambos são bancos de dados relacionais, e, graças à abstração fornecida pelo **Spring Data JPA**, **não será necessário alterar o código da aplicação** para trocar o banco de dados.

A única modificação necessária será:

- **Adicionar a dependência do PostgreSQL no arquivo `pom.xml`**;
- **Configurar a conexão com o Banco de dados PostgreSQL hospedado na nuvem**.

Essa compatibilidade é possível porque o Spring Data JPA utiliza uma camada de abstração que permite trabalhar com diferentes bancos de dados relacionais com mínimas alterações na estrutura da aplicação, desde que as entidades e consultas estejam adequadas ao padrão JPA.

<br />

<div align="left"><img src="https://i.imgur.com/b3khcJI.png" title="source: imgur.com" width="25px"/> <a href="https://www.postgresql.org/" target="_blank"><b>Site Oficial: PostgreSQL</b></a></div>

<br />
	
No arquivo, **pom.xml**, vamos adicionar as linhas abaixo, com a dependência do **PostgreSQL**:

```xml
<!-- Dependência do Banco de dados PostgreSQL -->
<dependency>
	<groupId>org.postgresql</groupId>
	<artifactId>postgresql</artifactId>
</dependency> 
```

<br />

## 👣 Passo 05 - Configurar o Banco de Dados na Nuvem



A configuração do banco de dados **local** é diferente daquela que será utilizada na **plataforma Render**.

No passo anterior, adicionamos a dependência do **PostgreSQL** no arquivo `pom.xml`. Agora, vamos configurar a aplicação para acessar o banco de dados **remoto**, que será provisionado no **Render**.

Para facilitar esse processo, utilizaremos um recurso do Spring chamado **Profiles** (ou *perfis*), que permite definir diferentes arquivos de configuração para cada ambiente da aplicação. Assim, teremos:

- Um arquivo para o ambiente **local**, com o MySQL (`application-dev.properties`);
- E outro para o ambiente **de produção**, com o PostgreSQL na nuvem (`application-prod.properties`).

A principal vantagem dos **Spring Profiles** é justamente permitir alternar entre diferentes configurações — por exemplo, entre banco de dados local e remoto — de forma simples, sem a necessidade de alterar o código-fonte da aplicação.

1) Na Source Folder **src/main/resources**, crie os arquivos **application-dev.properties** (Configuração do Banco de dados local) e **application-prod.properties** (Configuração do Banco de dados na nuvem), como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/EKZASZm.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** Mantenha a atenção aos detalhes ao criar os arquivos application-dev.properties e application-prod.properties. Cuidado para não se equivocar ao nomear os arquivos ou criar os arquivos em outra Source Folder.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

2. Vamos criar o primeiro arquivo. No lado esquerdo superior, na **Guia Package explorer**, na Source Folder **src/main/resources**, clique com o botão direito do mouse e clique na opção **New 🡢 File**.

3) Em **File name**, digite o nome do primeiro arquivo (**application-dev.properties**) e clique no botão **Finish**.

<div align="center"><img src="https://i.imgur.com/Q1s30nm.png" title="source: imgur.com" /></div>

4. Vamos criar o segundo arquivo da mesma forma que criamos o primeiro.

5. Em **File name**, digite o nome do segundo arquivo (**application-prod.properties**) e clique no botão **Finish**.

<div align="center"><img src="https://i.imgur.com/pSiak7m.png" title="source: imgur.com" /></div>

Agora vamos configurar os 3 arquivos **.properties**:

<br />

<h3>5.1 Configuração do arquivo application.properties</h3>



1. Abra o arquivo **application.properties**, **apague todo o conteúdo do arquivo** e substitua pelas linhas abaixo  e salve o arquivo.

```properties
spring.profiles.active=prod

springdoc.api-docs.path=/v3/api-docs
springdoc.swagger-ui.path=/swagger-ui.html
springdoc.swagger-ui.operationsSorter=method
springdoc.swagger-ui.disable-swagger-default-url=true
springdoc.swagger-ui.use-root-path=true
springdoc.packagesToScan=com.generation.blogpessoal.controller
```

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** Mantenha a atenção aos detalhes ao configurar o arquivo application.properties. Verifique se o valor atribuído à propriedade **`springdoc.packagesToScan`** corresponde exatamente aos **pacotes da sua aplicação** onde estão localizadas as classes `@RestController`. Caso esteja diferente, **ajuste o nome do pacote** conforme a estrutura do seu projeto. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>5.2 Configuração do arquivo application-dev.properties</h3>



1. Abra o arquivo **application-dev.properties**, insira as linhas abaixo (a primeira configuração do arquivo  **application.properties**) e salve o arquivo. 

```properties
spring.application.name=blogpessoal
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database=mysql
spring.datasource.url=jdbc:mysql://localhost/db_blogpessoal?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSl=false
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQLDialect

spring.jpa.properties.jakarta.persistence.sharedCache.mode=ENABLE_SELECTIVE

spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=America/Sao_Paulo
spring.jackson.serialization.write-dates-as-timestamps=false
spring.jackson.serialization.fail-on-empty-beans=false
spring.jackson.serialization.fail-on-self-references=false
```

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="180px"/> | <p align="justify"> **ALERTA DE BSM:** Mantenha a atenção aos detalhes ao configurar o arquivo application-dev.properties. Não esqueça de alterar a senha do usuário root caso a sua senha do MySQL não seja root. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>5.3 Configuração do arquivo application-prod.properties</h3>



1. No arquivo, **application-prod.properties**,  insira as linhas abaixo e salve o arquivo:

```properties
spring.application.name=blogpessoal
spring.datasource.url=jdbc:postgresql://${POSTGRESHOST}:${POSTGRESPORT}/${POSTGRESDATABASE}
spring.datasource.username=${POSTGRESUSER}
spring.datasource.password=${POSTGRESPASSWORD}
spring.datasource.driver-class-name=org.postgresql.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.open-in-view=true

spring.jpa.properties.jakarta.persistence.sharedCache.mode=ENABLE_SELECTIVE

spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=America/Sao_Paulo
spring.jackson.serialization.write-dates-as-timestamps=false
spring.jackson.serialization.fail-on-empty-beans=false
spring.jackson.serialization.fail-on-self-references=false
```

Observe que, nas configurações referentes ao acesso ao banco de dados na nuvem (como endereço, nome de usuário, senha, entre outros), utilizamos **variáveis de ambiente**. Essas variáveis serão definidas diretamente na plataforma **Render**, contendo os dados de acesso ao banco PostgreSQL provisionado.

O uso de variáveis de ambiente é uma prática recomendada para manter as credenciais e configurações sensíveis fora do código-fonte. No Render, elas podem ser definidas no painel do serviço e serão automaticamente disponibilizadas para a aplicação em tempo de execução.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ATENÇÃO:** *Depois de finalizar as configurações dos 3 arquivos, recomendamos executar o comando Update Project do STS para atualizar as configurações do projeto.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>5.4 Alternando entre os perfis no arquivo application.properties</h3>



Para alternar entre as configurações Local e Remota, abra o arquivo **application.properties** e utilize uma das 2 opções abaixo:

- `spring.profiles.active=dev` 🡢 O Spring executará a aplicação com a configuração do Banco de dados local (MySQL)
- `spring.profiles.active=prod` 🡢 O Spring executará a aplicação com a configuração do Banco de dados na nuvem (Render)

Para o Deploy, devemos deixar a linha `spring.profiles.active` configurada com a opção **prod**.

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao criar os perfis do Banco de Dados. Um erro muito comum é tentar executar o seu projeto no STS com o Perfil prod habilitado no arquivo application.properties. Com o perfil prod habilitado, a aplicação não será executada corretamente.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 👣 Passo 06 - Criar o arquivo Dockerfile



O Render não possui nativamente o suporte ao Java. Como opção para fazer o Deploy de aplicações Java, o Render oferece a possibilidade de utilizar o **Docker**, como alternativa para efetuar o deploy de aplicações que ele não oferece suporte nativo.

O **Docker** é um projeto para automatizar a implantação de aplicativos como **Containers** autossuficientes e portáteis, que podem ser executados na nuvem ou localmente, a partir de **imagens** contendo o ambiente mínimo para executar uma aplicação. 

Uma **Imagem** nada mais é do que uma **representação imutável** de como será efetivamente construído um container. **Exemplo:** uma imagem contendo o Ubuntu Linux, uma imagem contendo o compilador Java, entre outros. 

Como uma imagem é imutável, nós não podemos executar a imagem de forma direta, nós fazemos isso através de um **Container**, que é uma tecnologia que permite empacotar e isolar aplicações com  o seu  ambiente de tempo de execução, ou seja, com todos os arquivos  necessários para executar. Na imagem abaixo vemos uma representação gráfica do ambiente Docker:

<div align="center"><img src="https://i.imgur.com/6INLTtc.png" title="source: imgur.com" /></div>

> Na imagem acima vemos os principais elementos do ambiente Docker:
>
> 1) **Infraestrutura (Servidor - Hardware):** É a base de tudo — seu computador ou servidor com CPU, memória, armazenamento e rede.
> 2) **Sistema Operacional Host:** O sistema operacional que está instalado no hardware, como Linux, Windows ou macOS. Ele gerencia os recursos do hardware.
> 3) **Docker Engine (Container Engine):** Esse é o programa que roda no sistema operacional host. Ele é o responsável por criar e controlar os **containers**.
> 4) **Containers:** Como mostra a imagem, o Docker cria vários containers — pequenas “caixas” isoladas que contém as aplicações e as respectivas bibliotecas (no caso do Spring, as Dependências. Cada container compartilha o kernel do sistema operacional, mas mantém seu ambiente separado dos demais.
> 5) **Imagens Docker:** embora não esteja explicitamente representado na imagem acima, as imagens Docker são os “modelos” ou “receitas” usadas para criar os containers. A imagem inclui tudo o que a aplicação precisa para rodar, como código, bibliotecas e configurações.

A imagem acima resume os principais componentes que formam o ambiente Docker. No nosso contexto — deploy da aplicação Spring no Render via Docker — precisamos compreender que o processo é dividido em três etapas, conforme ilustrado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/7jQda72.png" title="source: imgur.com" /></div>

1. **Dockerfile:** Você escreve um arquivo chamado **Dockerfile** que contém as instruções para montar a **imagem Docker** da sua aplicação. Esse arquivo define qual sistema base será usado, quais dependências instalar, qual comando executar para rodar a aplicação, entre outras configurações.
2. **Imagem Docker:**  A partir do Dockerfile, o Render **constrói a imagem**. A imagem é como um “pacote pronto” contendo tudo que sua aplicação precisa para rodar: código, bibliotecas, configurações, etc. Ela é estática, ou seja, não está em execução.
3. **Container:** Quando a imagem está pronta, o Render cria um **container** a partir dela. O container é a instância em execução da imagem — é onde sua aplicação realmente roda, respondendo a requisições e executando tarefas.

No Projeto Blog Pessoal nós iremos **construir o Dockerfile e o Render se encarregará de construir a Imagem e o Container com o ambiente necessário para executar o projeto Blog Pessoal**.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ATENÇÃO:** *O nosso foco não é estudar o Docker. O foco neste momento é compreender como criaremos o Dockerfile necessário para efetuarmos o Deploy da nossa aplicação no Render*.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

Veja na tabela abaixo os comandos do **Dockerfile** que vamos utilizar:

| Comando        | Descrição Validada                                           |
| -------------- | ------------------------------------------------------------ |
| **FROM**       | Define a imagem base a partir da qual a nova imagem será construída. Deve ser a primeira instrução em um Dockerfile (exceto quando precedida por `ARG`). É possível utilizar imagens oficiais, como `openjdk` ou `ubuntu`, como ponto de partida para a construção da imagem personalizada. |
| **RUN**        | Executa comandos durante o processo de construção da imagem. Cada instrução `RUN` cria uma nova camada na imagem. É utilizada para instalar pacotes, compilar código ou realizar outras tarefas necessárias para preparar o ambiente da aplicação. |
| **COPY**       | Copia arquivos ou diretórios do sistema de arquivos do host para o sistema de arquivos da imagem. É usada para incluir o código-fonte da aplicação, arquivos de configuração ou outros recursos necessários dentro da imagem. |
| **VOLUME**     | Cria um ponto de montagem que permite que dados sejam persistidos fora do ciclo de vida do container. Define um diretório dentro do container que será armazenado em um volume gerenciado pelo Docker, permitindo que os dados persistam mesmo após o container ser removido. |
| **WORKDIR**    | Define o diretório de trabalho para as instruções subsequentes no Dockerfile, como `RUN`, `CMD`, `ENTRYPOINT`, `COPY` e `ADD`. Se o diretório especificado não existir, ele será criado automaticamente. |
| **ENTRYPOINT** | Especifica o comando que será executado quando um container for iniciado a partir da imagem. Diferente do `CMD`, o `ENTRYPOINT` não pode ser sobrescrito ao passar argumentos na linha de comando durante a execução do container. Ele é ideal para definir o comportamento principal do container. |
| **ARG**        | Define variáveis que podem ser passadas durante o processo de construção da imagem com o comando `docker build`. Essas variáveis estão disponíveis apenas durante o tempo de construção e não persistem na imagem final. |

O Render ao receber o Dockerfile através do repositório do Github, vai gerar a Imagem e o Container automaticamente, e caso não aconteça nenhum erro, a sua aplicação será implantada na nuvem e o Render lhe oferecerá um endereço (https://meuprojeto.onrender.com) para acessar externamente. Veja um resumo do processo na imagem abaixo:

<div align="center"><img src=https://i.imgur.com/bNzChTJ.png" title="source: imgur.com" /></div>

Vamos criar o arquivo **Dockerfile** no projeto Blog Pessoal:

1. Na **raiz do seu projeto**, na pasta **blogpessoal** (como mostra a figura abaixo), crie o arquivo **Dockerfile**.

<div align="center"><img src="https://i.imgur.com/iOdo9rb.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="250px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao criar o arquivo Dockerfile. Um erro muito comum é não criar o arquivo na pasta raíz do projeto. Outro erro comum é digitar o nome do arquivo com letras minúsculas. Observe que o arquivo inicia com letra maiúscula.*</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

2. Na Guia **Package Explorer**, clique com o botão direito do mouse sobre a pasta do projeto (indicada em azul) e clique na opção **New 🡢 File**.

<div align="center"><img src="https://i.imgur.com/ykiTjTa.png" title="source: imgur.com" /></div>

3. Em **File name**, digite: **Dockerfile** e clique no botão **Finish**.

<div align="center"><img width="55%" src="https://i.imgur.com/nCpNXbO.png" title="source: imgur.com" /></div>

4. Copie o código abaixo dentro do arquivo **Dockerfile** que você criou:

```dockerfile
FROM eclipse-temurin:17-jdk AS build

WORKDIR /workspace/app

COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .
COPY src src

RUN chmod -R 777 ./mvnw

RUN ./mvnw install -DskipTests

RUN mkdir -p target/dependency && (cd target/dependency; jar -xf ../*.jar)

FROM eclipse-temurin:17-jdk

VOLUME /tmp

ARG DEPENDENCY=/workspace/app/target/dependency

COPY --from=build ${DEPENDENCY}/BOOT-INF/lib /app/lib
COPY --from=build ${DEPENDENCY}/META-INF /app/META-INF
COPY --from=build ${DEPENDENCY}/BOOT-INF/classes /app

ENTRYPOINT ["java","-cp","app:app/lib/*","com.generation.blogpessoal.BlogpessoalApplication"]
```

Vamos entender o código:

<div align="center"><img src="https://i.imgur.com/XA3Ap0P.png" title="source: imgur.com" /></div>

A Criação do Container é dividida em 2 estágios:

1. Criar o Build da aplicação, ou seja, gerar o arquivo JAR.
2. Executar a Aplicação dentro do Container

> Um arquivo **JAR** é um **formato de arquivo compactado** usado para distribuir aplicações Java e suas dependências em um único pacote. Essencialmente um arquivo JAR é um arquivo ZIP que contém:
>
> - Classes Java compiladas (.class)
> - Recursos da aplicação (imagens, arquivos de configuração, etc.)
> - Metadados (arquivo MANIFEST.MF)
> - Bibliotecas e dependências
>
> O arquivo JAR facilita a distribuição e execução de aplicações Java, empacotando tudo que é necessário em um único arquivo.

Vamos detalhar as etapas:

**Etapa 01 - Build da aplicação**

**Linha 1:** Estamos indicando que o Build da aplicação será gerado a partir de uma imagem contendo a versão 17 do Java, rodando sobre o Linux numa versão minimalista, ou seja, apenas o necessário para executar o Java 17. Neste momento será feito o download da imagem contendo o Java 17. Observe que no final do nome da imagem, temos o alias **as build**, indicando que o Java 17 será executado nesta etapa em modo Build.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Caso o seu projeto esteja utilizando outra versão do Java (21, 24, entre outras), modifique a versão do Java na imagem para a mesma versão do seu projeto. Exemplo: eclipse-temurin:21-jdk (Java 21)*.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

**Linha 3:** Estamos indicando que dentro do nosso container, o Build da nossa aplicação será gerado dentro da pasta **/workspace/app**.

**Linha 5 a 8:** Copia o projeto do **Repositório do Github** para a pasta **/workspace/app**.

**Linha 10:** Autoriza a execução do **Maven** (mvnw) dentro da pasta **/workspace/app**. Sem este comando, o Render devolverá o erro: **Permission Denied! (Permissão negada)**

**Linha 12:** Gera o Build da nossa aplicação, excluindo os testes, porquê em produção eles são desnecessários. Neste momento será feito o download de todas as dependências do projeto do Repositório central do Maven e o arquivo JAR será criado.

**Linha 14:** Cria a pasta **target/dependency** e descompacta o arquivo JAR gerado pelo Maven. Ao descompactar o JAR do Spring Boot, são extraídos e organizados os componentes da aplicação: as classes compiladas da aplicação, as bibliotecas de dependências e os arquivos de metadados, preparando-os para serem copiados de forma otimizada para a imagem final de execução.

> No contexto de uma aplicação Spring Boot e arquivos JAR, os **metadados** são informações descritivas sobre a aplicação e sua estrutura, tais como:
>
> - Informações sobre a versão da aplicação;
> - Classe principal (Main-Class) a ser executada;
> - Versão do Java utilizada;
> - Informações sobre o Spring Boot;
> - Entre outras.

<br />

**Etapa 02 - Executar aplicação**

**Linha 16:** Indica que a nossa aplicação será executada através da imagem da versão 17 do Java, que já foi obtida via download.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *Caso o seu projeto esteja utilizando outra versão do Java (21, 24, entre outras), modifique a versão do Java na imagem para a mesma versão do seu projeto. Exemplo: eclipse-temurin:21-jdk (Java 21)*.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

**Linha 18:** Cria um volume chamado **/tmp** para armazenar os arquivos temporários.

**Linha 20:** Define uma variável chamada **DEPENDENCY** que aponta para o caminho **/workspace/app/target/dependency**, onde estão localizados os componentes extraídos do JAR na etapa de build.

**Linha 22 a 24:** Copia os componentes da aplicação do estágio de build para a imagem final: as dependências JAR vão para **/app/lib**, os metadados para **/app/META-INF** e as classes compiladas da aplicação para **/app**, organizando a estrutura necessária para executar a aplicação.

**Linha 26:** Executa o projeto Blog Pessoal. 

**Importante:** A instrução "**com.generation.blogpessoal.BlogpessoalApplication**" deve ser igual ao caminho da Classe Main da aplicação, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/dPmctx5.png" title="source: imgur.com" /></div>

Observe na imagem acima que:

- **com.generation.blogpessoal** 🡢 Pacote principal da aplicação.
- **BlogpessoalApplication** 🡢 Nome da Classe que contém o método **main()**.

Salve o arquivo antes de continuar.

<br />

<div align="left"><img src="https://i.imgur.com/1fDswF4.png" title="source: imgur.com" width="30px"/> <a href="https://docs.docker.com/engine/reference/builder/" target="_blank"><b>Documentação: Dockerfile</b></a></div>

<div align="left"><img src="https://i.imgur.com/S4GYUIM.png" title="source: imgur.com" width="30px"/> <a href="https://maven.apache.org/wrapper/" target="_blank"><b>Documentação: Maven Wrapper - MVNW</b></a></div>

<div align="left"><img src="https://i.imgur.com/PuWeuww.png" title="source: imgur.com" width="30px"/> <a href="https://www.guiafoca.org/guiaonline/iniciante/ch11s07.html" target="_blank"><b>Documentação: Linux - CHMOD</b></a></div>

<br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/rafaelq80/backend_blogpessoal_v3/tree/18_Deploy" target="_blank"><b>Código fonte do Projeto finalizado</b></a></div>

<br />

## 👣 Passo 07 - Atualizar o repositório do projeto no Github



1. Envie as atualizações do seu projeto para o repositório do  Github, através do **Git Bash**, utilizando os comandos abaixo:

   ```bash
    git add .
    
    git commit -m “:rocket: Deploy do Projeto Blog Pessoal”
    
    git push origin main
    
   ```

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="400px"/> | <div align="left"> **ATENÇÃO:** *Para efetuar o Deploy, o projeto Spring OBRIGATORIAMENTE precisa estar em um Repositório EXCLUSIVO e não pode estar DENTRO DE UMA PASTA, ou seja, ao abrir o repositório do projeto no Github, o conteúdo exibido será semelhante ao da imagem abaixo. Outro ponto importante é que o arquivo Dockerfile deve estar na raiz do projeto*.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<div align="center"><img src="https://i.imgur.com/hPHv0ye.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 08 - Criar o Banco de dados no Neon</h2>



O **Neon** é um serviço de banco de dados moderno, baseado na nuvem, que utiliza o PostgreSQL como tecnologia principal. Projetado especialmente para desenvolvedores, o Neon combina a robustez do PostgreSQL com uma arquitetura de banco de dados altamente escalável e eficiente, oferecendo uma experiência otimizada para aplicações web e móveis.

<br />

<h3>Principais Características do Neon</h3>



1. **Compatibilidade com PostgreSQL**: O Neon é 100% compatível com PostgreSQL, garantindo que os desenvolvedores possam aproveitar toda a flexibilidade, extensibilidade e recursos avançados desse banco de dados amplamente utilizado.
2. **Escalabilidade Automática**: O serviço ajusta automaticamente os recursos para atender a cargas variáveis de trabalho, evitando desperdício de recursos e custos desnecessários.
3. **Snapshots e Backups Contínuos**: O Neon oferece backups automáticos e contínuos, garantindo que os dados estejam sempre seguros e disponíveis em caso de falhas.
4. **Desligamento Automático em Estado Ocioso**: O Neon pode pausar automaticamente os recursos de computação quando o banco de dados não está em uso, economizando custos no plano pago.
5. **Interface Simples e Intuitiva**: A interface do Neon é projetada para ser amigável, facilitando a criação, gerenciamento e monitoramento de bancos de dados.

<br />

<h3>Benefícios do Plano Gratuito</h3>



O Neon oferece um plano gratuito bastante generoso, ideal para desenvolvedores, startups e projetos de pequeno porte que desejam começar sem custos iniciais. Entre os benefícios do plano free, destacam-se:

- **Até 10 GB de Armazenamento**: Espaço suficiente para aplicações iniciais ou em desenvolvimento.
- **100.000 Requisições Mensais**: Suporte para um bom volume de acessos e operações no banco de dados.
- **2 CPUs e 256 MB de RAM**: Recursos de computação ideais para projetos de menor escala ou protótipos.
- **Backups Automáticos**: Garantia de segurança e recuperação de dados sem custo adicional.
- **Sem Limite de Tempo**: O plano gratuito pode ser usado indefinidamente, desde que o consumo permaneça dentro dos limites oferecidos.

<br />

Vamos criar a conta no Neon:

1. Acesse o site do **Neon** (https://neon.tech/)
2. Clique no botão **Get Started** para iniciar

<div align="center"><img src="https://i.imgur.com/Z2gtHcP.png" title="source: imgur.com" /></div>

3. Clique no botão **Github** para criar a sua conta gratuita, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/iMpemhL.png" title="source: imgur.com" /></div>

4. Na próxima tela, clique no botão **Authorize neondatabase**, para concordar que o Neon crie uma conta, através da sua Conta do Github.

<div align="center"><img src="https://i.imgur.com/PWrLYpz.png" title="source: imgur.com" /></div>

5. Na janela **Get started with Neon for Free**, vamos criar o banco de dados. No item **Project name**, informe o nome do banco de dados (**blogpessoal**), como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/gK3FtzD.png" title="source: imgur.com" /></div>

6. Na opção **Cloud Service Provider**, selecione a opção **AWS**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/FXeFbmx.png" title="source: imgur.com" /></div>

7. Na sequência, clique no botão **Create project** para criar o banco de dados.
8. Caso a janela abaixo seja exibida, pode fechar no botão **X**

<div align="center"><img src="https://i.imgur.com/6VjDWxR.png" title="source: imgur.com" /></div>

9. Será aberta a janela **Project Dashboard**, como vemos na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/K6hm8Ih.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="150px"/> | <p align="justify"> **ATENÇÃO:** **O processo do Deploy enviará apenas a sua aplicação para a nuvem, logo o Banco de dados que acabou de ser criado nesta etapa estará completamente vazio, inclusive sem as tabelas, que serão criadas somente depois que a aplicação for inicializada pela primeira vez.** </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 👣 Passo 09 - Criar o Web Service no Render



1. Volte para o **Dashboard** do Render, clicando no logo do Render, localizado no lado esquerdo da Barra de navegação superior, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/C0qs5WO.png" title="source: imgur.com" /></div>

2. Será aberta a janela **Projects** dentro do **Dashboard**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Egr7DfO.png" title="source: imgur.com" /></div>

3. Para adicionar um novo **Web Service**, no **Dashboard** do Render, clique no botão **+ Add new**, localizado no canto superior esquerdo, e em seguida clique na opção **Web Service**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/CZ9YmcY.png" title="source: imgur.com" /></div>

4. Na janela **You are deploying a Web Service**, clique no botão **GitHub**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/7qiuwnM.png" title="source: imgur.com" /></div>

5. Será aberto um popup com a tela **Install Render**, clique no botão **Install**, para concordar que o Render acesse a sua Conta do Github.

<div align="center"><img src="https://i.imgur.com/LfygIY2.png" title="source: imgur.com" /></div>

6. Na janea **Confirm access**, digite a sua senha do Github para confirmar e clique no botão **Confirm**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/XYHRcu9.png" title="source: imgur.com" /></div>

7. De volta a janela **You are deploying a Web Service**, clique sobre o Repositório onde você enviou o **Projeto Blog Pessoal**, para selecioná-lo e configurar o deploy, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/n174hmO.png" title="source: imgur.com" /></div>

8. Role para baixo e informe o nome da sua aplicação na propriedade **Name** (blogpessoal), como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/gFbZ8D5.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ATENÇÃO:** O NOME DO PROJETO NÃO PODE CONTER LETRAS MAIUSCULAS, NUMEROS OU CARACTERES ESPECIAIS. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

9. Role para baixo e verifique se a propriedade **Language** está com a opção **Docker** selecionada, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/IyHWJwc.png" title="source: imgur.com" /></div>

10. Role a tela para baixo, localize o item **Instance Type** e verifique se o Plano Gratuito (**Free**) está selecionado, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/qj1HUg2.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <p align="justify"> **ATENÇÃO:** Caso seja selecionado um plano diferente, o Render exigirá o Cartão de Crédito para emitir a fatura do serviço. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 👣 Passo 10 - Configurar as Variáveis de Ambiente



Nesta etapa, serão criadas 5 variáveis de ambiente, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/pLa3OXo.png" title="source: imgur.com" /></div>

Estas 5 Variáveis de Ambiente serão utilizadas para conectar a aplicação com o Banco de dados do Neon.

Antes de criarmos as variáveis, precisamos identificar os dados que serão inseridos nestas variáveis, que estão disponíveis no **Banco de dados** criado no passo anterior. 

1. Volte para a Guia do Navegador onde está a página **Project Dashboard** do Neon e clique no botão **Connect**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/4fXlPUE.png" title="source: imgur.com" /></div>

2. Será aberta a janela **Connect to your database**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/rLOaTyk.png" title="source: imgur.com" /></div>

3. Localize o item: **Connection string** e mude para **Parameters only**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/VnzI588.png" title="source: imgur.com" /></div>

4. Observe que serão exibidos os parâmetros de conexão com o Banco de dados Postgres:

<div align="center"><img src="https://i.imgur.com/7hkecKZ.png" title="source: imgur.com" /></div>

5. Na tabela abaixo, está indicada qual variável de ambiente do Render receberá cada variável do Neon:

| Variável de Ambiente - Render | Variável do Neon |
| ----------------------------- | ---------------- |
| **POSTGRESHOST**              | PGHOST           |
| **POSTGRESPORT**              | *5432*           |
| **POSTGRESDATABASE**          | PGDATABASE       |
| **POSTGRESUSER**              | PGUSER           |
| **POSTGRESPASSWORD**          | PGPASSWORD       |

6. No exemplo acima, a configuração ficou da seguinte forma:

| Variável             | Conteúdo                                                 |
| -------------------- | -------------------------------------------------------- |
| **POSTGRESHOST**     | *ep-broad-queen-a6lrlmds-pooler.us-west-2.aws.neon.tech* |
| **POSTGRESPORT**     | *5432*                                                   |
| **POSTGRESDATABASE** | *neondb*                                                 |
| **POSTGRESUSER**     | *neondb_owner*                                           |
| **POSTGRESPASSWORD** | *senha do banco de dados*                                |

Agora vamos criar as variáveis:

1. Volte para a Guia do Navegador onde o **Web Service** está sendo criado, role a tela para baixo e localize o item **Environment Variables**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/VL0Hn8o.png" title="source: imgur.com" /></div>

2. Na propriedade **NAME_OF_VARIABLE**, informe o nome da 1ª variável: **POSTGRESHOST**

<div align="center"><img src="https://i.imgur.com/ElwSZvM.png" title="source: imgur.com" /></div>

3. Na propriedade **Value** da Variável de Ambiente **POSTGRESHOST**, cole o Hostname do Banco de dados, conforme detalhado nos itens acima, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/D6wpn0h.png" title="source: imgur.com" /></div>

4. Para adicionar uma nova variável de ambiente, clique no botão **+ Add Environment Variable**

<div align="center"><img src="https://i.imgur.com/B4AIoFR.png" title="source: imgur.com" /></div>

5. **Repita os passos 2 a 4** para criar as demais variáveis.
6. Ao final, você terá as 5 Variáveis de Ambiente Configuradas, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/pLa3OXo.png" title="source: imgur.com" /></div>

7. Depois de criar as Variaveis de Ambiente, role a tela para baixo e clique no botão **Create Web Service** para criar o Web Service e iniciar o Deploy.

<div align="center"><img src="https://i.imgur.com/n5iz2v5.png" title="source: imgur.com" /></div>

8. Na próxima janela, você pode acompanhar o processo do Deploy através da janela do **Log do Web Service**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/LxGwAcp.png" title="source: imgur.com" /></div>

9. Ao terminar o deploy, a aplicação será inicializada, de forma semelhante ao STS. Observe se a aplicação inicializa sem erros e se no final será exibida a mensagem informando que a aplicação está em execução. 

<div align="center"><img src="https://i.imgur.com/pw49VtD.png" title="source: imgur.com" /></div>

10. Para **confirmar que o Deploy foi concluído com êxito**, verifique na parte superior da tela de **Log do Webservice**, se apareceu a mensagem **Live**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/HGqhAh4.png" title="source: imgur.com" /></div>

11. Se apareceu esta mensagem, o Deploy foi finalizado com sucesso!
12. Para abrir a aplicação no Navegador da Internet, clique no link da aplicação, indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/1FTvC99.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ATENÇÃO:** Ao clicar no link da aplicação, o projeto pode não abrir automaticamente no navegador. Como o Docker precisa finalizar alguns processos, ele pode demorar alguns minutos para abrir. O tempo médio do processo de deploy completo do Blog Pessoal pode demorar um pouco.</p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Caso o nome do projeto já seja um endereço em uso no Render, ele acrescentará caracteres aleatórios depois do nome do projeto ao criar o endereço da aplicação. Exemplo: blogpessoal-wrtc.onrender.com*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 👣 Passo 11 - Abrir o Deploy no Navegador



1. Ao abrir a sua aplicação no Navegador, será exibida a tela de login abaixo. Como o Banco de dados criado no Render está vazio, precisamos criar uma conta de usuário e efetuar o login com esta conta antes de exibir a sua documentação no Swagger. 

<div align="center"><img src="https://i.imgur.com/MTFkYZb.png" title="source: imgur.com" /></div>

2. Abra o **Insomnia** e acesse a Collection **Blog Pessoal**.

3. Dentro da Collection  **Blog Pessoal**, crie uma pasta chamada **Local** e arraste as 3 pastas (Postagem, Tema e Usuario) para dentro dela, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/FYnkUBn.png" title="source: imgur.com" /></div>

4. Na sequência, Duplique a pasta **Local**, clicando na seta ao lado da pasta

<div align="center"><img src="https://i.imgur.com/u8HBMke.png" title="source: imgur.com" /></div>

5. Ao clicar nesta pasta, será aberto um menu. Clique na opção **Duplicate**:

<div align="center"><img src="https://i.imgur.com/4aL9wKD.png" title="source: imgur.com" /></div>

6. Na janela **Duplicate Folder**, defina o nome da nova pasta como **Render**.

<div align="center"><img src="https://i.imgur.com/X3z2qD7.png" title="source: imgur.com" /></div>

7. Abra a requisição **Cadastrar Usuário** da pasta **Render**.
8. Altere o endereço local (URL) atual: **http://localhost:8080/usuarios/cadastrar** 

<div align="center"><img src="https://i.imgur.com/0zGznXO.png" title="source: imgur.com" /></div>

9. Para o endereço do Render (Remoto) do seu Deploy: https://meuprojeto.onrender.com/usuarios/cadastrar (No exemplo acima: https://blogpessoal.onrender.com/usuarios/cadastrar)

<div align="center"><img src="https://i.imgur.com/HmopPqF.png" title="source: imgur.com" /></div>

10. Após efetuar as alterações, crie o usuário **root@root.com** com os dados da imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3GD5gh1.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Crie o usuário root exatamente como mostra a figura acima. Será através deste usuário que os Instrutores da sua turma irão corrigir o seu projeto*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

11. Volte para o Navegador da Internet e efetue o login com o usuário **root@root.com**.

<div align="center"><img src="https://i.imgur.com/A3NXaGE.png" title="source: imgur.com" /></div>

12. A Documentação no Swagger será exibida como a página inicial.

<div align="center"><img src="https://i.imgur.com/SJHPYNu.png" title="source: imgur.com"/></div>

<br />

## 👣 Passo 12 - Testar o Deploy no Insomnia



1. Volte para o **Insomnia** 

2. **Atualize o Endereço de todas as Requisições** da pasta **Render**, assim como foi feito na requisição **Cadastrar Usuário**

3. Antes de começar a testar todas Requisições do Deploy no Render, Faça o login utilizando o usuário cadastrado **root@root.com**, através da Requisição **Autenticar Usuário**, da pasta **Render**, para obter o Token.

4. **Atualize o Token de todas as Requisições protegidas**. 

5. Teste todas Requisições.

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes e a persistência. Insira dados na API através do Insomnia em todos os recursos (Postagem, Tema e Usuario) e teste todos os Endpoints. No recurso Postagem, não esqueça de testar o Relacionamento entre as Classes Postagem, Tema e Usuario*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

## 3. O Deploy Falhou!

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="80px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Este item você utilizará apenas se o seu Deploy falhar*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

### 3.1. O Deploy não abre no Navegador

-  Se o **Console** indica que a aplicação subiu, S**tarted BlogpessoalApplication in 15.456 seconds (JVM running for 20.59)**, mas ao abrir a aplicação no Navegador aparece a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/AlKoYkc.png" title="source: imgur.com" /></div>

- Clique no botão **Manual Deploy** e em seguida, clique na opção **Clear build cache & deploy** para refazer o deploy, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/xngS8Aq.png" title="source: imgur.com" /></div>

- Aguarde a conclusão e tente abrir novamente

<br />

### 3.2. O Deploy Falhou

- Se aparecer a mensagem **Failed**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/7SaAc4l.png" title="source: imgur.com" /></div>

- Caso não tenha aparecido mensagens de erro no **Console, na tela Log do Webservice** (O projeto Spring inicializou, mas o deploy falhou), clique no botão **Manual Deploy** e em seguida, clique na opção **Clear build cache & deploy** para refazer o deploy, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/xngS8Aq.png" title="source: imgur.com" /></div>

- Se o erro persistir, verifique se as **Variáveis de Ambiente estão configuradas corretamente**. Caso seja necessário atualizar o valor de qualquer Variável de ambiente, o Render iniciará um novo Deploy automaticamente após a atualização;
- Caso tenha aparecido algum erro no **Log do Web Service**, identifique o tipo do erro:
  - Se for erro no **Dockerfile**, corrija o erro e atualize o seu repositório no Github;
  - Se for erro de código (erro do Spring), siga as instruções do tópico: <a href="#update">**3. Como atualizar o Deploy no Render?**</a> e corrija o erro.

<br />

## 4. Como atualizar o Deploy no Render?

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Este item você utilizará apenas se você precisar alterar alguma coisa no seu projeto Spring e atualizar  a aplicação na nuvem*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

1. Para fazer alterações no código do projeto e executar localmente, volte para o **STS** e altere a primeira linha do arquivo, **application.properties** conforme o código abaixo:

```properties
spring.profiles.active=dev
```

2. Faça as alterações necessárias no código do seu projeto, execute localmente e verifique se está tudo funcionando **sem erros**.

3. Antes de refazer o Deploy, altere novamente a primeira linha do arquivo, **application.properties** conforme o código abaixo:

```properties
spring.profiles.active=prod
```

4.  Envie as atualizações do seu projeto para o repositório do  Github, através do **Git Bash**, utilizando os comandos abaixo: 

```bash
git add .
git commit -m “Atualização do Deploy - Blog Pessoal”
git push origin main
```

5. Ao finalizar o **git push**, o Render começará a refazer o Deploy. Acompanhe o processo pelo **Dashboard do Render**. 

<div align="center"><img src="https://i.imgur.com/mCxUqQy.png" title="source: imgur.com" /></div>

6. Verifique se a Aplicação abre no Navegador e faça os testes no Insomnia.

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>







> Caso você tenha fechado a janela anterior, é possível abrir esta janela novamente, clicando no botão **Connect**, da janela Project Dashboard, como mostra a imagem abaixo:
>
> <div align="center"><img src="https://i.imgur.com/4fXlPUE.png" title="source: imgur.com" /></div>

<br />
