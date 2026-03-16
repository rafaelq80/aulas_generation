<h1>Deploy do Backend no Render + Neon</h1>

<br />

<h2>1. O que é Deploy?</h2>



O verbo **deploy**, em inglês, significa **implantar**.

Em programação, seu sentido está intimamente relacionado à sua tradução literal: fazer um deploy, em termos práticos, significa colocar na nuvem, ou seja, publicar na Internet alguma aplicação que teve seu desenvolvimento concluído.
Quando um site é finalizado por uma pessoa desenvolvedora, ele passa pelos últimos testes e finalmente ele é hospedado na nuvem através do processo chamado deploy.
Do mesmo modo, quando um sistema sofre alguma melhoria ou alteração em seu código-fonte, implementar essa alteração ao sistema que está publicado (em Produção), também é chamado de deploy, só que incremental.

<br />

<h2>2. O que veremos por aqui?</h2>



Esse documento é um passo a passo para você enviar a sua aplicação NestJS, gratuitamente para a nuvem do Serviço de Hospedagem **Render**. Este processo irá gerar um link de acesso a sua aplicação, que poderá ser acessado de qualquer lugar, a partir de qualquer dispositivo com acesso a Internet. 
Para efetuar o Deploy vamos precisar fazer algumas modificações em nosso projeto, que serão detalhadas nos próximos passos.

<br />

<h2>👣 Passo 01 - Criar a Documentação da API</h2>



Para criar a Documentação da API no Swagger, caso você ainda não tenha criado, utilize o <a href="24.md" target="_blank">**Guia de Configuração do Swagger**</a>.

<br />

<h2 id="local">👣Passo 02 - Testar a API no seu computador</h2>



1. Execute a sua aplicação através do comando ***npm run start:dev***, para compilar e executar o projeto **blogpessoal**, caso não esteja em execução. 

```bash
npm run start:dev
```

2. Abra o Navegador da Internet de sua preferência e digite o endereço: **http://localhost:4000/**
3. Verifique se o **Swagger** está inicializando automaticamente, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/JKxWgN5.png?1" title="source: imgur.com" /></div>

4. Teste a sua aplicação através do **Insomnia** e verifique se tudo está funcionando. 
5. Em especial, verifique se o Método **cadastrar** está **criptografando a senha** e se o Método **logar** está devolvendo o **Token**.
6. Antes de continuar a configuração do projeto para efetuar o Deploy, não esqueça de **parar a execução do Projeto no Visual Studio Code**.
7. Para finalizar a execução do projeto, utilize as teclas **Ctrl + C** do teclado. 

<br />

> [!WARNING]
>
> **Lembre-se que antes de fazer o Deploy é fundamental que a API esteja funcionando e sem erros. Recomendamos que os testes sejam feitos através do Insomnia.**

<br />

<h2>👣 Passo 03 - Criar uma conta grátis no Render</h2>

<br />

<h3>3.1 O que é o Render?</h3>



O Render é uma plataforma unificada para criar e executar todos os seus aplicativos e sites. O Render permite criar e executar todos os seus aplicativos e sites com SSL gratuito, um CDN global, redes privadas e implantações automáticas do Git. 

> Uma **CDN** (Rede de Entrega de Conteúdo) é um grupo de servidores geograficamente distribuídos que aceleram a entrega do conteúdo da Web, aproximando-o de onde os usuários estão. 

O Render é classificado como um **PaaS** (plataforma como serviço), ou seja, é um conjunto de serviços para criar e gerenciar  aplicativos na nuvem. PaaS fornece os componentes de infraestrutura, que permitem que as pessoas Desenvolvedoras criem, integrem, migrem,   implementem, protejam e gerenciem aplicativos móveis e da web, de forma  simples e rápida.

> **Modelos de Serviços na Nuvem:**
>
> - **Plataforma como um serviço (PaaS):** Um provedor de  serviços oferece acesso a um ambiente baseado em cloud no qual os  usuários podem desenvolver e fornecer aplicativos. Além do **Render**, o **Render** e o **Azure** da Microsoft também utilizam este modelo.
> - **Infraestrutura como um serviço (IaaS):**  Um provedor de serviços fornece aos clientes acesso Pay As You Go (Pague pelo que  você usar), para  armazenamento, rede, servidores e outros recursos de  computação na  cloud. O **AWS da Amazon e a Digital Ocean** seguem este modelo.
> - **Software como um serviço (SaaS):** Um provedor de  serviços oferece softwares e aplicativos por meio da  Internet. Os  usuários subscrevem ao software e o acessam por meio da web ou de API's  do fabricante. o **Google Apps e do Microsoft Office 365** seguem este modelo.

Um grande diferencial do Render é que ele oferece **contas gratuítas**, com algumas limitações, que permitem hospedar aplicações desenvolvidas em diversas linguagens e **01 Banco de dados PostgreSQL**.

<br />

**Principais Limitações do Plano Gratuito:**

- Se a aplicação ficar **muito tempo sem receber nenhuma Requisição HTTP**, o aplicativo é finalizado e será reiniciado somente quando receber uma nova Requisição HTTP, para economizar os recursos da plataforma.
- Os servidores do Render estão disponíveis apenas na Europa, Ásia e nos Estados Unidos.
- Os recursos de Memória, Disco e Processamento são  limitados, logo a aplicação e principalmente o Banco de dados não podem  ser muito grandes.
- Aceita **apenas um Banco de dados por conta**;
- O **Banco de dados tem prazo de validade de 30 dias**. Ao completar os 30 dias você será notificado por e-mail da expiração do Banco de dados.
- O **tráfego mensal é limitado a 750 horas somando todas as aplicações e o Banco de dados**, ou seja, se ultrapassar este valor antes do mês acabar, sua conta ficará suspensa até o mês seguinte;
- Dependendo da linguagem, o Deploy da aplicação deverá ser realizado via Docker.

<br />

<div align="left"><img src="https://i.imgur.com/4jjzlmy.png" title="source: imgur.com" width="4%"/> <a href="https://render.com/docs/free" target="_blank"><b>Documentação: Render - Plano Gratuíto</b></a></div>

<br />

Vamos criar a conta no Render para fazermos o Deploy:

1) Acesse o endereço: **https://www.render.com** e clique na opção **Get Started**

<div align="center"><img src="https://i.imgur.com/RvNS3D0.png" title="source: imgur.com"/></div>

2. Existem diversas formas de criar uma conta no Render. Neste Guia utilizaremos a conta do Github. Clique no link **GitHub**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/f0IlI7J.png" title="source: imgur.com" /></div>

3. Na próxima janela, digite o endereço do e-mail e a senha da sua conta do Github, e em seguida clique no botão **Sign in**

<div align="center"><img src="https://i.imgur.com/twQ24M4.png" title="source: imgur.com" /></div>

4. Na próxima janela, autorize o Render a acessar a sua conta do Github, clicando no botão **Authorize Render**.

<div align="center"><img src="https://i.imgur.com/0egaZCm.png" title="source: imgur.com" /></div>

5. Na próxima janela, confirme se o endereço do e-mail está correto e clique no botão **COMPLETE SIGN UP**

6. Na próxima janela, será exibida uma mensagem solicitando que você verifique se recebeu uma mensagem no seu e-mail para validar a sua conta no Render. Abra a sua conta de e-mail e verifique se o e-mail foi recebido. Caso não tenha recebido, clique no botão **RESEND VERIFICATION EMAIL**.

7. Abra o e-mail enviado pelo Render (semelhante a imagem abaixo) e **clique no link para validar a sua conta**.

<div align="center"><img src="https://i.imgur.com/wlXD6G8.png" title="source: imgur.com" /></div>

8. Depois de clicar no link, sua conta será validada e será redirecionada para a tela do **Dashboard**.

<div align="center"><img src="https://i.imgur.com/gdzXBqU.png" title="source: imgur.com" /></div>

<br />

> [!WARNING]
>
> **Conclua todas etapas do processo de criação da conta no Render antes de avançar para o próximo passo do Deploy.**

<br />

<h2>👣 Passo 04 - Instalar o Pacote @nestjs/config</h2>



Vamos instalar o Pacote **@nestjs/config** através do NPM. Este pacote é responsável por gerenciar as configurações do Nest enviadas através das variáveis de ambiente. Como iremos configurar uma variável de ambiente no Render, vamos precisar deste Pacote.

1. Abra o **Terminal** do Visual Studio Code
2. Instale o **Pacote @nestjs/config**, através do comando abaixo:

```bash
npm install --save @nestjs/config
```

3. Ao concluir a instalação será exibida a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/Hkv3ous.png?1" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 05 - Instalar o Pacote do PostgreSQL</h2>



O Render, na sua versão gratuita, utiliza o **PostgreSQL** como **SGBD** (Sistema Gerenciador de Bando de dados). 

Até o momento estamos utilizando o **MySQL** para desenvolver o Blog Pessoal. Ambos são Banco de dados Relacionais e graças ao **TypeORM**, não será necessário realizar nenhuma alteração no código da nossa aplicação. A única mudança necessária, além de instalar **o pacote do PostgreSQL**, será necessário configurar a conexão com o Banco de dados PostgreSQL na nuvem. 

<br />

<div align="left"><img src="https://i.imgur.com/b3khcJI.png" title="source: imgur.com" width="25px"/> <a href="https://www.postgresql.org/" target="_blank"><b>Site Oficial: PostgreSQL</b></a></div>

<br />
	
Vamos instalar o Pacote do PostgreSQL através do NPM.

1. Para instalar o **Pacote do PostgreSQL**, digite o comando abaixo no Terminal:

```bash
npm install --save pg
```

4. Ao concluir a instalação será exibida a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/GlhxRBM.png?1" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 06 - Configurar o Banco de Dados na Nuvem</h2>



A Configuração do Banco de dados Local é diferente da configuração que será utilizada na nuvem pelo Render. 

No passo anterior, instalamos a Biblioteca do PostgreSQL, neste passo vamos configurar a aplicação para acessar o Banco de dados remoto no Render.

Para simplificar o processo, vamos utilizar um recurso do Nest chamado **Config Service** (Serviço de Configurações), que foi instalado na nossa aplicação no Passo 04, que nada mais é do que criar uma Classe de Serviço, contendo as configurações necessárias para cada ambiente de execução, ou seja, uma configuração para usar localmente com o MySQL e outra configuração para usar na Nuvem com o Postgres SQL. 

As Classes de Configuração do Banco de dados, irão implementar a Interface **TypeOrmOptionsFactory**, que permite configurar dinamicamente a conexão com o Banco de dados através do TypeORM. 

O grande benefício **Config Service** é simplificar a troca entre a configuração Local (**MySQL**) e a configuração Remota do Render (**PostgreSQL**), na hora de executar a aplicação. 

Vamos começar criando o Recurso **Data**, onde serão implmentadas as duas Classes de Serviço, contendo as respectivas configurações do Banco de dados Local (MySQL) e do Banco de na Nuvem (Postgres SQL):

1. Na pasta **src**, crie a pasta **data**
2. Dentro da pasta **data**, crie a pasta **services**
3. Dentro da pasta Services, vamos criar 2 Classes de Serviço:

- **DevService (dev.service.ts)**
- **ProdService (prod.service.ts)**

4. Veja na imagem abaixo, o resultado esperado:

<div align="center"><img src="https://i.imgur.com/dK843sA.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="80px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao criar as Classes de Serviço. Cuidado para não se equivocar ao nomear os arquivos ou criar em uma pasta diferente.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h3>6.1. Classe DevService</h3>



Na Classe **DevService** vamos implementar as configurações da Conexão com o Banco de dados Local - MySQL. Adicione o código abaixo na Classe **DevService**:

```ts
import { Injectable } from "@nestjs/common";
import { TypeOrmModuleOptions, TypeOrmOptionsFactory } from "@nestjs/typeorm";
import { Postagem } from "../../postagem/entities/postagem.entity";
import { Tema } from "../../tema/entities/tema.entity";
import { Usuario } from "../../usuario/entities/usuario.entity";

@Injectable()
export class DevService implements TypeOrmOptionsFactory {

    createTypeOrmOptions(): TypeOrmModuleOptions {
        return {
            type: 'mysql',
            host: 'localhost',
            port: 3306,
            username: 'root',
            password: 'root',
            database: 'db_blogpessoal',
            entities: [Postagem, Tema, Usuario],
            synchronize: true,
    };
  }
}
```

Vamos analisar o código:

<div align="center"><img src="https://i.imgur.com/gERlQZa.png" title="source: imgur.com" /></div>

**Linhas 01 a 05:** Importamos todas as Classes necessárias.

**Linha 08:** Assinamos a Classe DevService implementando a Interface **TypeOrmOptionsFactory**

**Linhas 10 a 20:** Implementamos o método **createTypeOrmOptions()**, da Interface **TypeOrmOptionsFactory**, que retornará um Objeto Type do tipo **TypeOrmModuleOptions**. 

O Type **TypeOrmModuleOptions** é um Objeto que contém as propriedades da conexão com o Banco de dados. Observe que copiamos as mesmas configurações do MySQL, que foram inseridas na Classe Módulo **AppModule**.

> **Type:** A palavra-chave type no TypeScript nos permite definir aliases (apelidos) para um tipo de dado personalizado. Ele fornece uma maneira de criar novos nomes para tipos existentes.
> Os aliases de tipo não introduzem novos tipos; em vez disso, eles fornecem nomes alternativos para os tipos já existentes.

<br />

<h3>6.2. Classe ProdService</h3>



Na Classe **ProdService** vamos implementar as configurações da Conexão com o Banco de dados na Nuvem - Postgres SQL. Adicione o código abaixo na Classe **ProdService**:

```ts
import { Injectable } from "@nestjs/common";
import { ConfigService } from "@nestjs/config";
import { TypeOrmModuleOptions, TypeOrmOptionsFactory } from "@nestjs/typeorm";

@Injectable()
export class ProdService implements TypeOrmOptionsFactory {

  createTypeOrmOptions(): TypeOrmModuleOptions {
    return {
      type: 'postgres',
      url: process.env.DATABASE_URL,
      logging: false,
      dropSchema: false,
      ssl: {
        rejectUnauthorized: false,
      },
      synchronize: true,
      autoLoadEntities: true,
    };
  }
}
```

Vamos analisar o código:

<div align="center"><img src="https://i.imgur.com/ptdrl91.png" title="source: imgur.com" /></div>

**Linhas 01 a 03:** Importamos todas as Classes necessárias.

**Linha 08:** Assinamos a Classe ProdService implementando a Interface **TypeOrmOptionsFactory**

**Linhas 10 a 20:** Implementamos o método **createTypeOrmOptions()**, da Interface **TypeOrmOptionsFactory**, que retornará um Objeto Type do tipo **TypeOrmModuleOptions**. 

O Type **TypeOrmModuleOptions** é um Objeto que contém as propriedades da conexão com o Banco de dados. 

A configuração do Banco de dados na nuvem será um pouco diferente da Configuração Local, porque os dados da conexão serão obtidos através de uma variável de Ambiente, que será adicionada no Render, durante a configuração do Deploy.

**Linha 10:** A propriedade **type** define o tipo do Banco de dados (PostgreSQL).

**Linha 11:** A propriedade **url** define o endereço do servidor, a porta, o usuário, a senha e o nome do Banco de dados. Essa **url** será enviada pelo Render, por isso ela está passada por meio de uma variável de ambiente.

**Linha 12:** A propriedade **logging** definida como false desabilita a exibição dos erros de SQL no console (Terminal)

**Linha 13:** A propriedade **dropSchema** foi definida como false para impedir que todas as tabelas do Banco de dados sejam apagadas (DROP TABLE) e recriadas todas as vezes que a aplicação for reiniciada.

**Linhas 14 e 15:** Configura a segurança da conexão com Banco de dados na nuvem. A propriedade **rejectUnauthorized** foi configurada como **false** para desabilitar o SSL na comunicação com o Banco de dados.

> **SSL** é um certificado digital que autentica a identidade de  um site e possibilita uma conexão criptografada. O termo "SSL" significa "Secure Sockets Layer" (camada de soquete seguro), um protocolo de  segurança que cria um link criptografado entre um servidor Web e um  navegador Web.

**Linha 17:** A propriedade **synchronize** definida como true indica que as tabelas do Banco de dados serão criadas/atualizadas automaticamente em cada inicialização da aplicação. Essa criação/atualização está relacionada a estrutura das tabelas e não aos dados.

**Linha 18:** A propriedade **autoLoadEntities** carregará todas as Classes Entidades, ou seja, ele procura todas Classes Entidade Registradas na **Classe AppModule** e cria as respectivas tabelas no Banco de dados na nuvem.

<br />

<h3>6.3. Atualização da Classe AppModule</h3>



Na Classe **AppModule**, vamos indicar qual Classe de Serviço iremos utilizar para conectar ao Banco de dados. Para rodar a aplicação na sua máquina, utilizaremos a Classe **DevService**, enquanto para rodar a aplicação na Nuvem, utilizaremos a Classe **ProdService**:

1) Abra a Classe **app.module.ts**
2) O código da Classe estará semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/kw7l7w4.png" title="source: imgur.com" /></div>

3. Primeiro vamos **apagar** todas as linhas da configuração do Banco de dados local (**Linhas 15 a 24**). 
4. Na sequência, vamos substituir as linhas apagadas, pelo trecho de código abaixo:

```typescript
ConfigModule.forRoot(),
TypeOrmModule.forRootAsync({
	useClass: ProdService,
    imports: [ConfigModule],
}),
```

5. Na imagem abaixo, você confere como ficou o código da Classe depois das alterações:

<div align="center"><img src="https://i.imgur.com/ht2Rm8f.png" title="source: imgur.com" /></div>

Vamos analisar o código:

**Linha 13:** O método **ConfigModule.forRoot()** registra o provedor **ConfigService**, que fornece os métodos necessários para ler variáveis de Ambiente e Classes de Configuração.

**Linha 14:** Como estamos utilizando a Interface **TypeOrmOptionsFactory** para definir as configurações do Banco de dados nas 2 Classes de Serviço, precisamos adicionar as Classes na Configuração do **AppModule** de forma assíncrona. Por isso vamos utilizar o método **forRootAsync()**, ao invés do método **forRoot()**.  O método **forRootAsync()** fornece diversas maneiras de lidar com a configuração assíncrona.

**Linha 15:** Informamos através da propriedade **useClass**, qual Classe de Serviço de Configuração vamos utilizar. Como vamos fazer o Deploy no Render, utilizaremos a Classe **ProdService**. Para executar a aplicação localmente, precisamos alterar esta linha para a Classe **DevService**.

**Linha 16:** Importamos o **Módulo ConfigModule**, para permitir que a configuração dinâmica funcione.

<br />

<h3>6.4. Alternando entre as Configurações DEV e PROD</h3>



Para alternar entre as configurações Local e Remota, na Classe **AppModule**, na propriedade **useClass**, utilize uma das 2 opções abaixo:

<b><code>useClass: DevService</code> </b> 🡢 O Nest executará a aplicação com a configuração do Banco de dados local (MySQL)

<b><code>useClass: ProdService</code> </b> 🡢 O Nest executará a aplicação com a configuração do Banco de dados na nuvem (Render)

Para o Deploy, vamos deixar a configuração **useClass: ProdService**.

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes ao executar a aplicação. Um erro muito comum é tentar executar o seu projeto no Visual Studio Code com a Classe ProdService habilitada na propriedade useClass. Com a Classe ProdService habilitada, o projeto não será inicializado localmente, apenas nuvem.* </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<div align="left"><img src="https://i.imgur.com/O6PILGE.png" title="source: imgur.com" width="25px"/> <a href="https://docs.nestjs.com/techniques/configuration" target="_blank"><b>Documentação: <i>Config Service</i></b></a></div>

<div align="left"><img src="https://i.imgur.com/O6PILGE.png" title="source: imgur.com" width="25px"/> <a href="https://docs.nestjs.com/techniques/database" target="_blank"><b>Documentação: <i>Configuração - Banco de dados</i></b></a></div>

<br />

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/rafaelq80/backend_blogpessoal_nest/blob/16_Deploy_Heroku/blogpessoal/src/app.module.ts" target="_blank"><b>Código fonte: Classe AppModule</b></a></div>

<div align="left"><img src="https://i.imgur.com/JACNZiR.png" title="source: imgur.com" width="30px"/> <a href="https://github.com/rafaelq80/backend_blogpessoal_nest/tree/16_Deploy_Heroku" target="_blank"><b>Código fonte: Projeto finalizado</b></a></div>

<br />

<h2>👣 Passo 07 - Atualizar o Repositório do projeto no Github</h2>




1. Envie as atualizações do seu projeto para o repositório do  Github, através do **Git Bash**, utilizando os comandos abaixo:

   ```bash
    git add .
    
    git commit -m “Deploy do Projeto Blog Pessoal”
    
    git push origin main
   ```

<br />

> [!CAUTION]
>
> **Para efetuar o Deploy, o projeto Nest <u>OBRIGATORIAMENTE</u> precisa estar em um Repositório <u>EXCLUSIVO</u> e não deve estar <u>DENTRO DE UMA PASTA</u>, ou seja, ao abrir o repositório do projeto no Github, o conteúdo exibido será semelhante ao da imagem abaixo. Se estiver diferente da imagem abaixo será necessário refazer o Repositório do Github.**

<br />

<div align="center"><img src="https://i.imgur.com/g5ao5b2.png" title="source: imgur.com" /></div>

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
8. Não feche a próxima tela, porque vamos precisar do endereço de conexão, disponibilizado abaixo:

<div align="center"><img src="https://i.imgur.com/6VjDWxR.pngg" title="source: imgur.com" /></div>

<br />

> [!TIP]
>
> Caso você tenha fechado, é possível abrir esta janela novamente, clicando no botão **Connect**, da janela Project Dashboard, como mostra a imagem abaixo:
>
> <div align="center"><img src="https://i.imgur.com/4fXlPUE.png" title="source: imgur.com" /></div>

<br />

> [!WARNING]
>
> **O processo do Deploy enviará apenas a sua aplicação para a nuvem, logo o Banco de dados que acabou de ser criado nesta etapa estará completamente vazio, inclusive sem as tabelas, que serão criadas somente depois que a aplicação for inicializada pela primeira vez.**

<br />

<h2>👣 Passo 09 - Criar o Web Service no Render</h2>



1. Para criar um novo Webservice, na barra de Navegação do Render, clique no botão **+ New** e em seguida clique na opção **Web Service**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/EjNU1FE.png" title="source: imgur.com" /></div>

2. No item **GitHub**, clique no link **+ Connect account**, para conectar a sua conta do Render com a sua Conta do Github.

<div align="center"><img src="https://i.imgur.com/xaffIQz.png" title="source: imgur.com" /></div>

3. Na tela, **Install Render**, clique no seu usuário do Github (no exemplo, rafaelproinfo), como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/ZkwMUEp.png" title="source: imgur.com" /></div>

4. Na próxima tela, clique no botão **Install**, para concordar que o Render acesse a sua Conta do Github.

<div align="center"><img src="https://i.imgur.com/ucaK7wA.png" title="source: imgur.com" /></div>

5. Selecione o Repositório onde você enviou o **Blog Pessoal** e clique no botão **Connect**, para conectar o Web Service ao Repositório do Github .

<div align="center"><img src="https://i.imgur.com/AYXxYVM.png" title="source: imgur.com" /></div>

6. Na próxima tela, informe o nome da sua aplicação na propriedade **Name** (**blogpessoal**).

<div align="center"><img src="https://i.imgur.com/xFSci7m.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> **O NOME DO PROJETO NÃO PODE CONTER <u>LETRAS MAIUSCULAS</u>, <u>APENAS NUMEROS</u> OU <u>CARACTERES ESPECIAIS</u>.**

<br />

7. Role a tela para baixo e verifique se a propriedade **Environment** está com a opção **Node** selecionada.

<div align="center"><img src="https://i.imgur.com/kazoMSr.png" title="source: imgur.com" width="90%"/></div>

8. Role a tela para baixo e verifique se o Plano Gratuito (**Free**) está selecionado.

<div align="center"><img src="https://i.imgur.com/GenKLYn.png" title="source: imgur.com" /></div>

<br />

> [!WARNING]
>
> **Caso seja selecionado um plano diferente, o Render exigirá o Cartão de Crédito para emitir a fatura do serviço.**

<br />

<h2>👣Passo 10 - Configurar a Variável de Ambiente</h2>



Depois de definir o tipo de serviço no item **Instance Type**, vamos configurar uma variável de ambiente, que armazenará a string de conexão com o Banco de dados no item **Environment Variables**:

1. Role a tela a para abaixo e localize a opção **Environment Variables**.

<div align="center"><img src="https://i.imgur.com/nZtUEtg.png" title="source: imgur.com" /></div>

<br />

> As **variáveis de ambiente** são configurações que afetam o comportamento do sistema operacional e dos programas em seu computador. Elas podem ser usadas para apontar diretórios importantes, definir informações específicas ou personalizar certos aspectos do sistema, como por exemplo, a string de conexão com o Banco de dados de uma aplicação. 

<br />

2. No item **NAME_OF_VARIABLE**, vamos definir o nome da nossa variável de ambiente (**DATABASE_URL**):

<div align="center"><img src="https://i.imgur.com/GVhz93Q.png" title="source: imgur.com" /></div>

3. Volte na página de **Comexão do Neon**, clique no botão **Copy code**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/OCSJ5Zz.png" title="source: imgur.com" /></div>

4. Volte para o render e cole o conteúdo copiado no item **value** da Variável de Ambiente **DATABASE_URL**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/UrvNI9C.png" title="source: imgur.com" /></div>

5. Clique no botão **Deploy Web Service** para criar o Web Service e iniciar o Deploy.

<div align="center"><img src="https://i.imgur.com/oh39h2L.png" title="source: imgur.com" /></div>

7. Acompanhe o processo do Deploy no **Log do Web Service**

<div align="center"><img src="https://i.imgur.com/VGYv8H6.png" title="source: imgur.com" /></div>

8. Ao finalizar o Deploy, será exibida a mensagem: **Build sucessful** e na sequência a aplicação será iniciada.

<div align="center"><img src="https://i.imgur.com/Y0QAS8G.png" title="source: imgur.com" /></div>

9. Observe na imagem abaixo, que a mensagem informando que a aplicação está em execução é igual a mensagem exibida no Console do Visual Studio Code.

<div align="center"><img src="https://i.imgur.com/oK9ZSJt.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> **Caso o Servidor do Render esteja sobrecarregado, o console pode não exibir todo o processo. Fique atento a mensagem de status localizada acima do console. Caso a mensagem de status fique verde com a palavra Live, como vemos na imagem abaixo, significa que o Deploy foi finalizado com sucesso!**

<br />

<div align="center"><img src="https://i.imgur.com/OKl7yI3.png" title="source: imgur.com" /></div>

10. Para abrir a aplicação no Navegador da Internet, clique no link da aplicação, indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/KdRorYF.png" title="source: imgur.com" /></div>

11. Outra forma de abrir a aplicação é digitando o endereço: **https://nomedoprojeto.onrender.com** no navegador. (No exemplo acima: https://blogpessoal.onrender.com)

<br />

> [!IMPORTANT]
>
> **Ao clicar no link da aplicação, pode acontecer do projeto não abrir automaticamente no navegador. Como o Render precisa finalizar alguns processos, ele pode demorar alguns minutos para abrir a aplicação no Navegador WEB.**

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Caso o nome do projeto já seja um endereço em uso no Render, ele acrescentará caracteres aleatórios depois do nome do projeto ao criar o endereço da aplicação. Exemplo: blogpessoal-wrtc.onrender.com*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>❌ O Deploy não Abriu!</h2>



Se o **Deploy no Render não abrir** e/ou aparecer a mensagem **Failed**, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/7SaAc4l.png" title="source: imgur.com" /></div>

- Caso não tenha aparecido mensagens de erro no **Console, na janela chamada Log do Webservice**, clique no botão **Manual Deploy** e em seguida, clique na opção **Clear build cache & deploy** para refazer o deploy manualmente, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/dRdNYQ7.png" title="source: imgur.com" /></div>

- Se o erro persistir, verifique se a **Variável de Ambiente está configurada corretamente**. 

- Caso seja necessário atualizar o valor de qualquer Variável de Ambiente, o Render iniciará um novo Deploy automaticamente após a atualização.

- Caso tenha aparecido algum erro no **Log do Web Service**, identifique o tipo do erro:
  - Se for erro de código (Erro do Framework Nest ou Erro no código TypeScript), siga as instruções do tópico: <a href="#update">**3. Como atualizar o Deploy no Render?**</a>, corrija o erro localmente, faça os respectivos testes e atualize o Repositório do Github do Projeto.
  
- Caso o Deploy exiba a mensagem de concluído com sucesso, entretanto ao tentar abrir no navegador não aparece nada na tela, experimente refazer o Deploy manualmente.

- Caso o mesmo erro persista, recrie o Webservice da aplicação, só que desta vez trocando o servidor (**Region**) de hospedagem. O Render possui 5 servidores (Oregon, Ohio, Frankfurt, Virginia e Singapore), como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/75v6aQq.png" title="source: imgur.com" /></div>

- Apague e refaça o WebService da aplicação (Passos 09 e 10), mas desta vez alterando servidor. Dê a preferência para os Servidores Americanos (Oregon, Ohio e Virginia), por serem mais próximos do Brasil. Lembre-se que Singapore (Ásia) e Frankfurt (Europa) estão mais distantes do Brasil.

<br />

<h2>👣 Passo 11 - Abrir o Deploy no Navegador</h2>



1. Ao abrir a sua aplicação no Navegador, será exibida a tela abaixo:

<div align="center"><img src="https://i.imgur.com/JKxWgN5.png?1" title="source: imgur.com" /></div>

2. Observe que o endereço do deploy será composto pelo **https://nomedoseuprojeto.onrender.com**. No Deploy exemplo, o link ficou: **https://blogpessoal.onrender.com**, como mostra a imagem abaixo. 

<div align="center"><img src="https://i.imgur.com/Bsf7inS.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> **Note que o Render tem como política de segurança padrão o uso <u>OBRIGATÓRIO</u> do protocolo https (protocolo http com a camada segurança - SSL), nos endereços das aplicações hospedadas nos seus servidores.**

<br />

Como o Banco de dados e as tabelas da aplicação acabaram de ser criadas no Render, elas estão completamente vazias, logo precisamos adicionar dados para testarmos a aplicação na nuvem. Para testarmos a aplicação, precisamos criar uma conta de usuário e efetuar o login com esta conta para obter o token JWT e habilitarmos o Swagger, que também está protegido pelo Passport. 

1. Abra o **Insomnia** e acesse a Collection **Blog Pessoal**.
2. Crie uma pasta chamada **Blog Pessoal** e arraste as 3 pastas (**Postagem, Tema e Usuario**) para dentro dela.
3. Duplique a pasta **Blog Pessoal** clicando sobre a pasta com o botão direito do mouse e clicando na opção **Duplicate** do menu que será aberto.
4. Na próxima janela, defina o nome da nova pasta como **Blog Pessoal - Render**.

<div align="center"><img src="https://i.imgur.com/hE8xkGA.png" title="source: imgur.com" /></div>

5. Abra a requisição **Cadastrar Usuário** na pasta **Blog Pessoal - Render**.

6. Altere o caminho atual: **http://localhost:4000/usuarios/cadastrar** 

<div align="center"><img src="https://i.imgur.com/mxpZa0m.png" title="source: imgur.com" /></div>

7. Para o endereço do seu Deploy no Render: **https://meuprojeto.onrender.com/usuarios/cadastrar** (No exemplo acima: **https://blogpessoal.onrender.com/usuarios/cadastrar**)

<div align="center"><img src="https://i.imgur.com/HmopPqF.png" title="source: imgur.com" /></div>

8. Após efetuar as alterações, crie o usuário **root@root.com** com os dados da imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3GD5gh1.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Crie o usuário root exatamente como mostra a figura acima. Será através deste usuário que os Instrutores da sua turma irão corrigir o seu projeto*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

9. Faça login com este usuário para obter o Token. Não esqueça de alterar o endereço da Requisição, assim como foi feito na Requisição **Cadastrar Usuário**.

<div align="center"><img src="https://i.imgur.com/d3H9BEl.png" title="source: imgur.com" /></div>

10. Copie apenas a parte codificada do token, ou seja, tudo menos a palavra **Bearer**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/9ZXB79L.png" title="source: imgur.com" /></div>

11. Volte para o Swagger e clique no botão **Authorize**, localizado no lado direito da tela.

<div align="center"><img src="https://i.imgur.com/8YmwsLv.png" title="source: imgur.com" /></div>

12. Cole o token no campo **Value** e clique no botão **Authorize**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/R6onfh2.png" title="source: imgur.com" /></div>

13. Será exibida a mensagem **Authorized** (Autorizado!). Clique no botão **Close**.

<div align="center"><img src="https://i.imgur.com/suHAPUF.png" title="source: imgur.com" /></div>

14. O Swagger está desbloqueado e pronto para uso. Observe que os cadeados estão todos na cor preta (desbloqueados).

<div align="center"><img src="https://i.imgur.com/RSqkqzk.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <div align="left"> **IMPORTANTE:** O Token está configurado para durar 1h, ou seja, daqui a 1h você terá que repetir o processo acima para desbloquear o Swagger novamente.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>👣 Passo 12 - Testar o Deploy no Insomnia</h2>



1. Volte para o **Insomnia** .
2. Atualize o endereço de todas requisições da pasta **Blog Pessoal - Render**, assim como foi feito nas requisições **Cadastrar Usuário e Login**.
3. Atualize o Token em todas as Requisições, exceto **Cadastrar Usuário e Login**. Lembre-se que o token dura apenas 1 hora!

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes e a persistência. Insira dados na API através do Insomnia em todos os recursos (Postagem, Tema e Usuario). No recurso Postagem, não esqueça de testar o Relacionamento entre as 3 Classes*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2 id="update">3. Como atualizar o Deploy no Render? </h2>

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ALERTA DE BSM:** *Mantenha a atenção aos detalhes. Este item você utilizará apenas se você precisar alterar alguma coisa no seu projeto Nest ou efetuar alguma atualização na aplicação na nuvem*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

1. Para fazer alterações no código do projeto e executar localmente, no **Visual Studio Code**, abra a **Classe AppModule**, localizada na pasta **src** e **localize a linha indicada na imagem abaixo, que contém a chamada para a Classe ProdService com a configuração do Banco de dados na nuvem**.

<div align="center"><img src="https://i.imgur.com/bdvbvCe.png" title="source: imgur.com" /></div>

2. Na sequência, substitua a **Classe ProdService** (configuração do Banco de dados da nuvem), pela **Classe DevService** (configuração do Banco de dados local), indicada na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/ZJcWThI.png" title="source: imgur.com" /></div>

3. Faça as alterações necessárias no código do seu projeto, execute localmente e verifique se está tudo funcionando **sem erros**.
4. Antes de atualizar o seu repositório no Github e refazer o Deploy, pare a aplicação e substitua a **Classe DevService** (configuração do Banco de dados local), pela **Classe ProdService** (configuração do Banco de dados da nuvem), indicada na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/bdvbvCe.png" title="source: imgur.com" /></div>

5. Envie as atualizações do seu projeto para o repositório do  Github, utilizando os comandos abaixo: 

```bash
git add .
git commit -m “Atualização do Deploy - Blog Pessoal”
git push origin main
```

6. Ao finalizar o **git push**, o Render começará a refazer o Deploy automaticamente. Acompanhe o processo pelo **Dashboard do Render**. 

<div align="center"><img src="https://i.imgur.com/aOOoFdT.png" title="source: imgur.com" /></div>

7. Após a conclusão, verifique se a Aplicação abre no Navegador e faça todos os testes no Insomnia.

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
