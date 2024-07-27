<h1>Projeto Integrador - Curtir</h1>



Vamos criar um método no Projeto Loja de Games, que simulará a opção **curtir**, onde cada vez que um usuário clicar no botão curtir no Frontend, o Backend armazenará o numero de curtidas que o produto recebeu.

<br />

> [!WARNING]
>
> **Este conteúdo apresentará como criar um Simulador bem simples da função Curtir produtos. Para criar um Curtir Produtos Real, seria  necessário fazer algumas mudanças no Backend do projeto, como criar uma nova tabela no Banco de dados para guardar se o usuário já curtiu o produto. Neste simulador, iremos criar um contador simples, que armazenará no banco de dados quantas curtidas o produto recebeu, sem controlar se um usuário curtiu uma ou mais vezes o mesmo produto.**

<br/>

<h2>👣 Passo 01 - Criar o Atributo curtir na Classe Entidade (Model) Produto</h2>



1. Abra a Classe Produto e adicione o trecho de código abaixo, antes do atributo **categoria**:

```typescript
@Column({ type: "int", nullable: true, default: 0 })
curtir: number
```

2. Na imagem abaixo você confere a alteração:

<div align="center"><img src="https://i.imgur.com/m4LKAby.png" title="source: imgur.com" /></div>

Vamos analisar o trecho de código destacado na imagem acima:

**linha 21:** Através do decorador **@Column**, definimos as configurações do atributo curtir no Banco de dados.

- O tipo de dado que será armazenado será um numero inteiro
- O valor do atributo pode ser nulo, ou seja, o preenchimento não é obrigatório.
- O valor padrão (default) será 0, ou seja, ao cadastrar um novo produto não será necessário preencher o valor do atributo curtir, porque será atribuído automaticamente o valor zero.

**linha 22:** Definimos o atributo curtir com o tipo number.

<br/>

<h2>👣 Passo 02 - Criar o Método curtir na Classe ProdutoService</h2>



1. Abra a Classe ProdutoService e adicione o trecho de código abaixo, na sequência do ultimo método:

```typescript
    async curtir(id: number): Promise<Produto> {

        let buscaProduto = await this.findById(id);

        if (!buscaProduto)
            throw new HttpException('Produto não encontrado!', HttpStatus.NOT_FOUND);

        let novaCurtida = buscaProduto.curtir + 1;

        return await this.produtoRepository.save({
            ...buscaProduto,
            curtir: novaCurtida
        });
    }
```

2. Na imagem abaixo você confere a alteração:

<div align="center"><img src="https://i.imgur.com/wG6cL99.png" title="source: imgur.com" /></div>

Vamos analisar o trecho de código da imagem acima:

**linha 2:** Criamos a assinatura do Método curtir, com o parâmetro id, do tipo number, que receberá o id do Produto que receberá a curtida.

**linha 4:** Criamos um Objeto da Classe Produto, chamado **buscaProduto**, para receber o resultado da execução do Método **findById(id: number)**, da Classe **ProdutoService**. O objetivo é checar se o Produto que será curtido existe, através da busca pelo id.

**linhas 6 e 7:** Verifica se **buscaProduto é nulo**, ou seja, se o **id do produto é nulo**. Caso seja informado um id que não existe, o Objeto buscaProduto será nulo, retornando o HTTP Status **NOT FOUND 🡪 404** (Não Encontrado!).

**linha 9:** Cria uma variável, chamada **novaCurtida**, que receberá o valor atual do atributo curtir do produto e somará 1 a este valor, indicando que houve uma nova curtida.

**linhas 11 a 14:** Retorna a execução do Método **save()**, do objeto **produtoRepository**. O resultado da execução do Método **save()**, será um Objeto da Classe Produto, que será atualizado apenas o atributo **curtir** no Banco de dados, na tabela **tb_produtos**.

Observe que utilizamos o **Spread Operator** para fazer esta atualização, onde na **linha 12**, estamos indicando para manter todas as propriedades do Objeto produto exatamente como estão. Na **linha 13**, estamos indicando para **atualizar apenas o atributo curtir**, com o valor armazenado na variável **novaCurtida**.

> O **Spread Operator** (Operador de Espalhamento) é uma sintaxe do JavaScript/TypeScript, que permite a expansão de arrays e objetos iteráveis em vários elementos. A sintaxe do Operador Spread utiliza três pontos consecutivos (...) ao lado do array ou do objeto e pode ser usado de várias maneiras. 
>
> O **Operador Spread** nos permite copiar rapidamente todo ou parte de objeto existente para um novo objeto, além de permitir a combinação de vários objetos em um único objeto. Um uso muito comum do Operador Spread é criar novos objetos, baseados em objetos existentes, com algumas alterações em relação aos objetos originais.
>
> **Exemplo:**
>
> ```typescript
> let pessoa = {
> nome: 'John',
> idade: 30
> };
> 
> let {nome, idade} = {...person};
> console.log(nome); // John
> console.log(idade); // 30
> ```
>
> *No exemplo acima, "espalhamos" os atributos do objeto pessoa em variáveis individuais.*
>
> <br />
>
> <div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="4%"/> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax" target="_blank"><b>JavaScript - Operador Spread</b></a></div>
>
> <br />

<br/>

<h2>👣 Passo 03 - Criar o Método curtir na Classe ProdutoController</h2>



1. Abra a Classe ProdutoController e adicione o trecho de código abaixo, na sequência do ultimo método:

```typescript
@Put('/curtir/:id')
@HttpCode(HttpStatus.OK)
curtir(@Param('id') id: number): Promise<Produto> {
	return this.produtoService.curtir(id);
}
```

2. Na imagem abaixo você confere a alteração:

<div align="center"><img src="https://i.imgur.com/IDvdFVb.png" title="source: imgur.com" /></div>

Vamos analisar o trecho de código da imagem acima:

**Linha 2:** O decorador **@Put()** mapeia todas as Requisições **HTTP PUT**, enviadas para o endereço **http://localhost:4000/produtos/curtir/:id**.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="150px"/> | <div align="left"> **ATENÇÃO:** *O Endereço deste Endpoint será composto pelo Endereço /produtos/curtir/ + a variável de caminho indicada no decorador @Put (:id), que será utilizado para identificar o produto que receberá a curtida.</div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

**Linha 3:** O decorador **@HttpCode(HttpStatus.OK)** indica que o Método **curtir** terá como **Resposta HTTP** padrão **OK 🡪 200**, ou seja, quando a Resposta da Requisição for positiva, será retornado o **HTTP Status OK 🡪 200**. Caso a Resposta seja negativa (algo deu errado), a Resposta dependerá do erro.

- **HTTP Status NOT FOUND 🡪 404**, caso o objeto não seja encontrado
- **HTTP Status INTERNAL SERVER ERROR 🡪 500**, caso ocorra algum erro no código ou no servidor

**Linha 4:** Criamos o Método **curtir(@Param('id', ParseIntPipe) id: number)**, que promete retornar uma **Promise** (que será resolvida pela Classe ProdutoService), com um Objeto da Classe Produto, com o atributo curtir atualizado. 

**@Param('id'):** Este decorador **insere o valor enviado na variável de caminho id (:id)**, no parâmetro do Método **curtir( @Param('id') id: number )**;

**Exemplo:**

http://localhost:4000/produtos/curtir/1

Neste exemplo, o parâmetro **id: number**, do Método  **curtir( @Param('id') id: number )**, receberá o valor 1 (Id que será procurado na tabela tb_produtos), que foi enviado na variável de caminho **/:id**.

A instrução **ParseIntPipe** converte o valor da variável de caminho id (inicialmente uma string) em um numero. Caso não seja possível converter (o usuário digitou algo diferente de um numero), ele retorna uma mensagem de erro de validação, informando que estava esperando por um numero e recebeu uma string, além do HTTP Status **BAD REQUEST 🡪 400** (Erro no conteúdo da  Requisição), como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Zetp0hh.png" title="source: imgur.com" /></div>

**Linha 5:** Executa o método **curtir( @Param('id') id: number )**, **Método da Classe ProdutoService**, que retornará **o Objeto da Classe Produto** atualizado no Banco de dados. 

<br/>

<h2>👣 Passo 04 - Testar no Insomnia</h2>



Agora vamos criar a Requisição para o Método **curtir( id: number )**:

1. Clique com o botão direito do mouse sobre a **Pasta Produtos** para abrir o menu e clique na opção **New HTTP Request**.

<div align="center"><img src="https://i.imgur.com/KvRI8b2.png" title="source: imgur.com" /></div>

2. Será criada uma nova Requisição (New Request) dentro da pasta **Produtos**.

   <div align="center"><img src="https://i.imgur.com/eBeNo4G.png" title="source: imgur.com" /></div>

3. Dê um duplo clique sobre a nova requisição (**New Request**), informe o nome da requisição (indicado na imagem abaixo na cor amarela) e pressione a tecla **enter** do seu teclado.

<div align="center"><img src="https://i.imgur.com/zP4ykH8.png" title="source: imgur.com" /></div>

4. Selecione o Método HTTP que será utilizado (**PUT**) na requisição, indicado na imagem abaixo na cor verde. 

<div align="center"><img src="https://i.imgur.com/z6dWHYj.png" title="source: imgur.com" /></div>

5. Configure a requisição conforme a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/2DuaaJN.png" title="source: imgur.com" /></div>

6. No item marcado em amarelo na imagem acima, informe o endereço (endpoint) da Requisição. A requisição **Curtit** foi configurada da seguinte maneira:

- A primeira parte do endereço (http://localhost:4000) é o endereço do nosso servidor local. Quando a aplicação estiver na nuvem, ele será substituído pelo endereço da nuvem.
- A segunda parte do endereço é o **endpoint** configurado no decorador ***@Controller***, em nosso caso **/produtos**.  
- A terceira parte (**/curtir/1**), curtir é apenas um indicativo do conteúdo da variável que deverá ser preenchida. O numero ***1*** é o conteúdo da variável de caminho id (**@Param('id') id: number**). Aqui será informado o id do produto que será curtido.

7. Para testar a requisição, com a aplicação rodando, clique no botão <img src="https://i.imgur.com/sy0V8Nx.png" title="source: imgur.com" width="60px"/>.

8. O resultado da requisição você confere na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/eRFxATr.png" title="source: imgur.com" /></div>

9. Observe que a aplicação quando encontra o Objeto no Banco de dados, além de exibir os dados do Objeto no Corpo da Resposta, respeitando o critério informado na consulta (id = 1), ela também retorna um **HTTP Status 200 🡪 OK** (indicado em verde na imagem acima), informando que a Requisição foi bem sucedida. Note que o atributo curtir (indicado pela seta azul), também foi incrementado.

10. Caso o Objeto Produto não seja encontrado, a aplicação retornará o **HTTP Status 404 🡪 NOT FOUND** (Não encontrado), marcado em laranja na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/5lCAhBv.png" title="source: imgur.com" /></div>

11. Caso o Projeto Nest não esteja em Execução, o Insomnia retornará a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/Y2iNu9v.png" title="source: imgur.com" /></div>

12. Execute o seu Projeto e teste novamente!

<br /><br />

