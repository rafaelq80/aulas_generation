<h1>Criando Variáveis de Ambiente no Nest JS</h1>

Vamos configurar o Nest para trabalhar com variáveis de ambiente, com o objetivo de ocultar as configurações mais sensíveis da nossa aplicação (conexão com o banco de dados, secret, entre outras).

<br />

<h2>👣 Passo 01 - Instalar o Pacote @nestjs/config</h2>



Vamos instalar o Pacote **@nestjs/config** através do NPM. Este pacote é responsável por gerenciar as configurações do Nest enviadas através das variáveis de ambiente. 

1. Abra o **Terminal** do VSCode através do menu **Terminal 🡪 New Terminal**
2. Para instalar o **Pacote @nestjs/config**, digite o comando abaixo:

```
npm install --save @nestjs/config
```

<br />

<h2>👣 Passo 02 - Criar o arquivo .env</h2>



Para que ninguém saiba os dados de conexão com o Banco de dados e a Chave de Assinatura do Token JWT (Secret), vamos ocultar estes dados, através da criação de algumas Variáveus de Ambiente:

1. **Dentro da pasta raiz do Projeto Nest**, crie um arquivo com o nome **.env**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/E3Y58lq.png" title="source: imgur.com" /></div>

<br />

> [!CAUTION]
>
> Um Erro muito comum é criar o arquivo **.env** dentro de alguma pasta do projeto. O arquivo **.env**, **<u>obrigatoriamente deve estar na pasta raiz do seu projeto</u>**, como mostra a imagem acima. Caso contrário, o seu Backend deixará de funcionar.

<br />

2. Dentro desse arquivo, iremos adicionar as nossas variáveis de ambiente, que irão armazenar os dados de conexão com o Banco de dados e a Chave de Assinatura do Token JWT (Secret), conforme o exemplo abaixo:

```bash
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=root
DB_PASSWORD=root
DB_DATABASE=db_lojagames
JWT_SECRET=292d7161c76174f0784a14f860756497073fe5c187de42f87a2060c5f06c7877
```

<br />

> [!WARNING]
>
> Os nomes das variáveis devem ser escritos em letras maiúsculas e sem espaços em branco(**DB_HOST**).

<br />

<h2>👣 Passo 03 - Adicionar o arquivo .env no arquivo .gitignore</h2>



Vamos modiﬁcar o nosso arquivo **.gitignore**, para que o nosso arquivo **.env** não seja enviado para o Github, funcionando apenas no nosso computador, da seguinte forma:

1. Abra o arquivo **.gitignore**, localizado na pasta raiz do projeto:

<div align="center"><img src="https://i.imgur.com/uYWsDSJ.png" title="source: imgur.com" /></div>

2. Adicione a linha abaixo no arquivo **.gitignore**:

```tsx
.env
```

3. Após a alteração, o arquivo **.gitignore** ficará semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Ff9i0NM.png" title="source: imgur.com" /></div>

A linha adicionada pode ser colocada em qualquer ponto do arquivo, não precisa estar exatamente no mesmo local indicado na imagem acima.

<br />

<h2>👣 Passo 04 - Configurar o Banco de dados</h2>



Vamos configurar a conexão com o Banco de dados através das variáveis de ambiente criadas no arquivo **.env**:

1. Abra a **Classe AppModule** e localize o trecho de código abaixo:

<div align="center"><img src="https://i.imgur.com/iChheoQ.png" title="source: imgur.com" /></div>

2. Substitua o trecho de código acima, pelo trecho de código abaixo:

```ts
ConfigModule.forRoot({
      isGlobal: true,
    }),
    TypeOrmModule.forRoot({
        type: 'mysql',
        host: process.env.DB_HOST,
        port: parseInt(process.env.DB_PORT, 10),
        username: process.env.DB_USERNAME,
        password: process.env.DB_PASSWORD,
        database: process.env.DB_DATABASE,
        entities: [Produto, Categoria, Usuario],
        synchronize: true,
    }),
```

3. O resultado você confere na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/5eiMvcC.png" title="source: imgur.com" /></div>

**Linhas 14 a 16:** O método **ConfigModule.forRoot()** registra o provedor **ConfigService**, que fornece os métodos necessários para ler variáveis de Ambiente e Classes de Configuração. A propriedade **isGlobal** estabelece que as variáveis de Ambiente e Classes de Configuração estarão disponíveis em toda a aplicação.

**Linhas 17 a 26:** Configuramos a conexão com o Banco de dados utilizando as variáveis criadas no arquivo .env.

<br />

<h2>👣 Passo 05 - Configurar a Secret na Classe AuthModule</h2>



Vamos configurar a Chave de assinatura do Token JWT (Secret), na Classe **AuthModule**, através da variável de ambiente criada no arquivo **.env**:

1. Abra a **Classe AuthModule** e localize o trecho de código abaixo:

<div align="center"><img src="https://i.imgur.com/gSp82xo.png" title="source: imgur.com" /></div>

2. Substitua o trecho de código acima, pelo trecho de código abaixo:

```ts
JwtModule.registerAsync({
      imports: [ConfigModule],
      useFactory: async (configService: ConfigService) => ({
        secret: configService.get<string>('JWT_SECRET'),
        signOptions: {
          expiresIn: '1h',
        },
      }),
      inject: [ConfigService],
    }),
```

3. O resultado você confere na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/dDE0z7X.png" title="source: imgur.com" /></div>

**Linha 16:** O Módulo **JwtModule** foi importado no array **imports**. Precisamos do Módulo JwtModule para criar o Token JWT. Além de importar o Módulo JwtModule, será necessário executar o Método **registerAsync()** para configurar algumas propriedades dentro do Módulo.

**Linha 17:** Importamos o Módulo **ConfigModule**, que oferece o provedor **ConfigService**, que fornece os métodos necessários para ler variáveis de Ambiente e Classes de Configuração. 

**Linha 18:** Criamos uma Injeção de Dependência da **Classe ConfigService** para termos acesso aos métodos da Classe ConfigService.

**Linha 19:** Adicionamos a variável de ambiente **JWT_SECRET** na propriedade **secret** (chave de assinatura do token JWT) através do Método **get()**.

**Linhas 20 a 23:** Configura a propriedade **signOptions** (opções do processo de criação do token). Observe que dentro desta  propriedade temos um array com as propriedades específicas do Método **sign()**, da **Classe JwtService**, do **Módulo JwtModule**. Vamos configurar a propriedade **expiresIn** (tempo de duração do Token JWT), com o valor **1h**. O Token gerado terá validade de 1 hora, após este período será necessário gerar um novo.

**Linha 24:** Injetamos a **Classe ConfigService** dentro da propriedade **inject**.

**Linha 29:** Além da alteração do trecho de código mencionado acima, observe que adicionamos no array **exports** a Classe **JwtModule**, tornando a acessível em toda a aplicação.

<br />

<h2>👣 Passo 06 - Configurar a Secret na Classe JwtStrategy</h2>



Vamos configurar a Chave de assinatura do Token JWT (Secret), na Classe **JwtStrategy**, através da variável de ambiente criada no arquivo **.env**:

1. Abra a **Classe JwtStrategy** e altere as linhas indicadas na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3tzKFOS.png" title="source: imgur.com" /></div>

**Linha 8:** Criamos uma Injeção de Dependência da **Classe ConfigService** nos parâmetros do Método Construtor (constructor), para termos acesso aos métodos da Classe ConfigService.

**Linha 12:** Adicionamos a variável de ambiente **JWT_SECRET** na propriedade **secretOrKey** (chave de assinatura do token JWT) através do Método **get()**.

<br />

<h2>👣 Passo 07 - Executar e Testar o Projeto</h2>



1. Digite o comando abaixo para compilar e executar o projeto, caso não esteja em execução:

```bash
npm run start:dev
```

2. Teste a aplicação e verifique se tudo está funcionando.
