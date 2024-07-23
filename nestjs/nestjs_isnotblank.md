<h1>O Pacote Class Transformer</h1>



O Pacote **Class Validator**, possui diversos Decoradores que oferecem diversas regras de validação para atributos da Classe Model (Entidade), entretanto, em algumas situações pode ser necessário criar uma regra de validação personalizada. Além do Pacote **Class Validator** oferecer esta possibilidade, também podemos utilizar o Pacote **Class Transformer**, que permite modificar os atributos através de funções TypeScript.

Antes de continuarmos, precisamos diferenciar os tipos objetos disponíveis no TypeScript. Os Objetos no TypeScript são classificados em 2 categorias:

- Objetos Simples
- Objetos de Classe

Os **Objetos Simples**, também chamados de **Objetos Literais**, são objetos criados de forma direta, através de um par de chaves `{}` ou através de uma Interface, geralmente utilizados para a validação de um tipo de dado, sem o uso de uma Classe. 

Os **Objetos de Classe** são instâncias de uma classe, que possui método construtor, atributos e métodos definidos.

Em algumas situações, pode ser necessário transformar um Objeto **Simples** em um Objeto de **Classe**, para efetuar algum processamento. Um bom exemplo disso é quando a nossa API recebe um JSON, para persistir os dados de um Objeto no Banco de dados. O JSON é um Objeto Simples, enviado no Corpo da Requisição HTTP e não uma instância de uma Classe. Uma API, ao receber um Objeto simples no formato JSON, tenta converter em um Objeto de uma Classe e só então persiste os dados no Banco de dados.

Em situações que você precise criar uma validação personalizada para um ou mais atributos do Objeto, antes dele ser persistido, pode ser necessário executar uma transformação, antes de aplicar a validação. Para executar esta transformação, utilizaremos o pacote **Class Transformer**. O objetivo desta biblioteca é mapear os seus Objetos  Simples em Objetos de Classe, permitindo que sejam aplicadas as transformações necessárias, através de funções TypeScript.

>A Biblioteca **Class Transformer** trabalha em conjunto com a Biblioteca **Class Validator**, com os Pipes.
>
>**Pipes** no NestJS são o canivete suíço do processamento de dados. Eles facilitam a transformação, a sanitização (higienização) e a validação contínua dos dados recebidos à medida que eles atravessam várias partes do seu aplicativo. Isso garante que os dados estejam em conformidade com requisitos especificados na Classe Entidade antes de serem usados nas Classes Controladoras ou enviados de volta como Respostas das Requisições.

O decorador **@Transform** permite realizar transformações nos dados, recebendo o Objeto Simples, convertendo em Objeto de Classe e aplicando transformações necessárias através de Arrow Functions. O decorador **@Transform** recebe 5 atributos, que permitiem que você faça praticamente qualquer tipo de  transformação:

**Sintaxe:**

```ts
@Transform(({ valor, chave, obj, tipo, options }) => valor)
```

**Onde:**

| Atributo  | Descrição                                                  |
| --------- | ---------------------------------------------------------- |
| `value`   | O valor da propriedade antes da transformação.             |
| `key`     | O nome da propriedade transformada.                        |
| `object`  | O objeto de origem da transformação.                       |
| `type`    | O tipo de transformação.                                   |
| `options` | O objeto de opções passado para o método de transformação. |

No projeto Blog Pessoal, vamos criar uma regra de validação para impedir que o usuário crie uma postagem com o título e/ou texto com espaços em branco, através do pacote **Class Transformer**. Vamos adicionar o decorador **@Transform** nos atributos **titulo** e **texto** da Classe Postagem, com a seguinte configuração:

```ts
@Transform(({ value }: TransformFnParams) => value?.trim())
```

Como precisamos validar apenas o valor do atributo (value), utilizamos um recurso do TypeScript chamado  **desestruturação do Objeto**. Note que selecionamos apenas o argumento **value** do objeto da Interface **TransformFnParams**. 

A Interface **TransformFnParams** é a Interface que define o modelo do Objeto (um objeto composto pelos 5 atributos descritos na tabela acima), recebido pelo decorador **@Transform**, ou seja, é a tipagem utilizada pelo TypeScript para receber o objeto enviado para o decorador **@Transform**.

> **Atribuição por Desestruturação** é uma expressão do TypeScript que torna possível  "desembalar" os valores de um array ou as propriedades de um Objeto em variáveis distintas. Em outras palavras, podemos extrair dados específicos de um array ou atributos específicos de um objeto e atribuí-los a variáveis. 
>
> **Exemplo:** 
>
> ```ts
> // Objeto pessoa
> let pessoa = {
> nome: "Sarah", 
> pais: "Nigéria", 
> profissao: "Desenvolvedora Fullstack", 
> amigas: ["Annie", "Becky"]
> };
> 
> // Atribuição por Desestruturação
> let {nome, amigas} = pessoa;
> ```
>
> Observe que não foi necessário criar individualmente as variáveis **nome** e **amigas**. Apenas adicionamos as variáveis dentro das Chaves **{ }** e atribuímos o Objeto **pessoa**. Através da desestruturação, o JavaScript/TypeScript compreende que as variáveis **nome** e **amigas** devem receber os valores armazenados nos atributos  **nome** e **amigas** do Objeto **pessoa**.
>
> <br />
>
> <div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="4%"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment" target="_blank"><b>JavaScript - Atribuição por Desestruturação</b></a></div>
>
> <br />

Na sequência, através de uma Arrow Function, executamos o método **trim()**, (método para manipular string), para remover todos os os espaços em branco do valor do atributo. Note que ao lado da propriedade value foi adicionada uma interrogação (?), que significa que a propriedade pode ter um valor ou não.

Caso o usuário digite apenas espaços em branco, o valor da propriedade será **null** porque o método **trim()** removerá todos os espaços em branco. Segundo as regras de validação da entidade Postagem, **o valor dos atributos titulo e texto não podem ser nulos**, desta forma, o objeto postagem não será persistido até que seja inserido um valor válido para os respectivos atributos.  

Veja o código da Classe Postagem, com a validação para espaços em branco:

```ts
import { Transform, TransformFnParams } from "class-transformer";
import { IsNotEmpty } from "class-validator";
import { Column, Entity, PrimaryGeneratedColumn, UpdateDateColumn } from "typeorm";

@Entity({name: "tb_postagens"})
export class Postagem{

    @PrimaryGeneratedColumn() // Chave Primária e Auto_Increment
    id: number;

    // Validação para espaços em branco
    @Transform(({ value }: TransformFnParams) => value?.trim()) 
    @IsNotEmpty()
    @Column({length: 100, nullable: false})
    titulo: string;

    // Validação para espaços em branco
    @Transform(({ value }: TransformFnParams) => value?.trim())
    @IsNotEmpty()
    @Column({length: 1000, nullable: false})
    texto: string;

    @UpdateDateColumn()
    data: Date;

}
```

Faça o Teste no Insomnia e tente cadastrar uma nova postagem, adicionando um espaço em branco no título ou no texto da postagem:

<div align="center"><img src="https://i.imgur.com/YgFvK1h.png" title="source: imgur.com" /></div>

Você receberá o HTTP Status  400, como mostra imagem abaixo:

<div align="center"><img src="https://i.imgur.com/4Go96dH.png" title="source: imgur.com" /></div>
