<h1>Numeric Transformer</h1>



O NestJS, assim como o TypeScript em geral, tende a exibir números decimais como strings dentro de objetos JSON. Isso ocorre devido à forma como o JSON serializa números de ponto flutuante (float) e à maneira como o TypeScript lida com a precisão numérica.

Existem algumas razões para isto:

1. **Precisão Numérica**:

- JavaScript usa números de ponto flutuante de 64 bits (IEEE 754)
- Pode haver perda de precisão com números decimais
- Para preservar a precisão exata, o Banco de dados e o ORM (TypeORM) podem optar por retornar como string

2. **Serialização JSON**:

- O JSON.stringify() pode converter números decimais para string para manter a precisão
- Valores numéricos muito grandes também são convertidos para string

Para resolver este problema, vamos utilizar o **Pacote Class Transformer**, que permite modificar os atributos através de funções TypeScript.

<br />

<h2>1.Classe Numeric Transformer</h2>



Vamos criar uma Classe chamada **numerictransformer**, que será responsável por fazer a conversão dos dados:

1. Na pasta **src**, crie uma pasta chamada **util**
2. Dentro da pasta **util**, crie a Classe **numerictransformer.ts**
3. Na sequência, adicione na Classe **NumericTranformer** o código abaixo:

```typescript
export class NumericTransformer {
    to(data: number): number {
        return data;
    }
    from(data: string): number {
        return parseFloat(data);
    }
}
```

A Classe **NumericTransformer** possui dois métodos principais:

1. **to(data: number): number**
   - Este método será chamado quando os dados estiverem sendo enviados PARA o Banco de dados
   - Ele recebe um número da sua aplicação e retorna o valor que será salvo no Banco de dados
   - O método apenas retornará o mesmo número sem modificações
2. **from(data: string): number**
   - Este método será chamado quando os dados estiverem vindo DO Banco de dados, ou seja, o resultado de uma consulta
   - Ele recebe uma string do Banco de dados e converte esta string para um número float, usando o método de conversão **parseFloat()**
   - O método retornará a string convertida em um número decimal, que será usado na sua aplicação

<br />

<h2>2. Utilizando a Classe no atributo</h2>



Vamos utilizar o método na Classe Entidade **Produto**, no atributo **preco**:

1. Abra a Classe Entidade **Produto**
2. Substitua o código do atributo **preco** pelo trecho de código abaixo:

```typescript
    @IsNumber({ maxDecimalPlaces: 2 })
    @IsNotEmpty()
    @IsPositive()
    @Column({ type: "decimal", precision: 10, scale: 2, transformer: new NumericTransformer() })
    preco: number
```

Observe que a Classe **NumericTransformer** foi inserida dentro do decorador **@Column**, na propriedade **transformer**, que especifica um transformador de valor, que deve ser usado nesta coluna ao converter os dados do objeto em um JSON e vice-versa, sempre que for ler ou gravar os dados no Banco de dados.

Desta forma, ao efetuar uma consulta, o atributo **preco** será exibido no JSON como um número decimal, ao invés de ser exibido como uma string (entre aspas).
