# Conversão de Tipos de Dados em Java



Durante o desenvolvimento de aplicações Java, é comum trabalhar com diferentes tipos de dados, como números, textos, datas e valores booleanos. Em muitos cenários, esses dados precisam ser convertidos de um tipo para outro para que possam ser utilizados corretamente em operações, cálculos ou integrações com outros sistemas.

A conversão de tipos de dados é uma prática fundamental na programação, pois permite que informações sejam manipuladas de forma compatível com as regras e requisitos de cada contexto. Sem essas conversões, diversas operações simples do dia a dia não poderiam ser realizadas.

Na prática, as conversões acontecem com frequência em situações como:

- Leitura de dados digitados pelo usuário no formato texto (`String`);
- Consumo de APIs, que geralmente enviam e recebem informações em formato textual, como JSON;
- Manipulação de dados provenientes de bancos de dados;
- Realização de cálculos matemáticos que exigem tipos numéricos, como `int`, `long`, `float` e `double`;
- Formatação de informações para exibição em telas, relatórios e arquivos;
- Integração entre métodos e bibliotecas que exigem tipos de dados específicos.

O Java oferece diferentes mecanismos para realizar essas conversões, desde conversões automáticas entre tipos compatíveis até métodos especializados fornecidos pelas classes Wrapper e pela própria linguagem. Conhecer essas técnicas é essencial para desenvolver aplicações mais seguras, eficientes e livres de erros relacionados à incompatibilidade de tipos.

Neste capítulo, você conhecerá os principais métodos de conversão de tipos de dados utilizados no desenvolvimento Java e aprenderá quando utilizar cada um deles por meio de exemplos práticos.

<br />

## 1. Conversão Implícita (Widening Primitive Conversion)



A conversão implícita, também conhecida como **Widening Conversion**, ocorre automaticamente quando um valor é atribuído a um tipo capaz de armazenar todos os valores do tipo original. Como não há risco de perda de informação, o compilador realiza a conversão sem a necessidade de intervenção do programador.

Segundo a especificação da linguagem Java, as conversões implícitas seguem a seguinte ordem:

![](https://i.imgur.com/xAEGMeY.png)

> [!IMPORTANT]
>
> O tipo `char` possui regras próprias de conversão. Embora possa ser promovido automaticamente para `int`, `long`, `float` e `double`, não existe conversão implícita entre `char` e `short`, mesmo ambos possuindo 16 bits de armazenamento.

<br />

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 01 - Conversão Implícita (Atribuição de valor)**

```java
package conversores;

public class ConversaoImplicita {

	public static void main(String[] args) {
		
		int numero = 10;
		double valorDouble = numero;

		System.out.println(valorDouble);
		
		long valorLong = 100;
		float valorFloat = valorLong;

		System.out.println(valorFloat); 

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
10.0
100.0
```

Esse tipo de conversão é comum em operações matemáticas, atribuições e chamadas de métodos que esperam tipos maiores que o valor fornecido.

> [!WARNING]
>
> Embora a conversão seja considerada segura pela linguagem, valores inteiros muito grandes convertidos para `float` podem sofrer perda de precisão devido às limitações de representação desse tipo.

<br />

## 2. Conversão Explícita (Narrowing Conversion ou Casting)



A conversão explícita, conhecida como **Casting**, é necessária quando um valor é convertido para um tipo com menor capacidade de armazenamento.

Nesses casos, o compilador exige que o programador informe explicitamente que está ciente da possível perda de dados.

**Sintaxe**

```java
(tipoDestino) valor
```

<br />

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 02 - Conversão via Casting**

```java
package conversores;

public class Exemplo02 {

	public static void main(String[] args) {
		
		double nota = 9.8;
		int notaInteira = (int) nota;

		System.out.println("Nota convertida para inteiro: " + notaInteira);
		
		long valorLong = 1000L;
		int valorInteiro = (int) valorLong;
		
		System.out.println("Valor Long convertido para inteiro: " + valorInteiro);
		
	}
}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
9
1000
```

<br />

> [!WARNING]
>
> Ao realizar um casting:
>
> - A parte decimal é descartada;
> - Não ocorre arredondamento automático;
> - Pode haver perda de precisão;
> - Valores muito grandes podem sofrer truncamento ou overflow.
>
> <img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 03 - Erro na Conversão via Casting**
>
> ```java
> package conversores;
> 
> public class Exemplo03 {
> 
> 	public static void main(String[] args) {
> 		
> 		long numero = 3000000000L;
> 		int resultado = (int) numero;
> 		
> 		System.out.println("Numero long convertido para inteiro: " + resultado);
> 
> 	}
> }
> ```
>
> <img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**
>
> ```bash
> Numero long convertido para inteiro: -1294967296
> ```
>
> O valor `3000000000L` é maior que o limite máximo suportado pelo tipo `int` (`2.147.483.647`). Ao realizar o casting de `long` para `int`, o Java não verifica se o valor cabe no tipo de destino; ele simplesmente descarta os bits excedentes. Como resultado, ocorre um **overflow**, fazendo com que o padrão de bits restante seja interpretado como um número negativo. Por isso, a conversão de `3000000000L` para `int` resulta em `-1294967296`.

<br />

## 3. Conversão de String para Tipos Numéricos e Não Numéricos



Em aplicações reais, é muito comum receber dados em formato textual por meio de formulários, arquivos, APIs e bancos de dados.

Para utilizar esses valores em cálculos, é necessário convertê-los para tipos numéricos.

As classes Wrapper oferecem métodos específicos para essa finalidade.

### Métodos mais utilizados

| De String para | Método                   | Exemplo                                     |
| :------------- | :----------------------- | :------------------------------------------ |
| `int`          | `Integer.parseInt()`     | `int i = Integer.parseInt("123");`          |
| `double`       | `Double.parseDouble()`   | `double d = Double.parseDouble("45.67");`   |
| `long`         | `Long.parseLong()`       | `long l = Long.parseLong("999");`           |
| `float`        | `Float.parseFloat()`     | `float f = Float.parseFloat("3.14");`       |
| `boolean`      | `Boolean.parseBoolean()` | `boolean b = Boolean.parseBoolean("true");` |

<br />

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 04 - Conversão de String para Tipos Numéricos e Não Numéricos:**

```java
package conversores;

public class Exemplo04 {

	public static void main(String[] args) {

		String idadeTexto = "25";
		int idade = Integer.parseInt(idadeTexto);

		String salarioTexto = "3500.75";
		double salario = Double.parseDouble(salarioTexto);

		String populacaoTexto = "2147483648";
		long populacao = Long.parseLong(populacaoTexto);

		String temperaturaTexto = "28.5";
		float temperatura = Float.parseFloat(temperaturaTexto);

		String ativoTexto = "true";
		boolean ativo = Boolean.parseBoolean(ativoTexto);

		System.out.println("Idade: " + idade);
		System.out.println("Salário: " + salario);
		System.out.println("População: " + populacao);
		System.out.println("Temperatura: " + temperatura);
		System.out.println("Usuário ativo? " + ativo);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Idade: 25
Salário: 3500.75
População: 2147483648
Temperatura: 28.5
Usuário ativo? true
```

<br />

> [!WARNING]
>
> Antes de converter uma String para qualquer outro formato é recomendável validar os dados antes da conversão. Caso o conteúdo da String não represente um valor válido, será lançada uma exceção, como vemos no exemplo abaixo:
>
> <img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 05 - Erro de Conversão**
>
> ```java
> package conversores;
> 
> public class Exemplo05 {
> 
> 	public static void main(String[] args) {
> 
> 		String idadeTexto = "ABC";
> 		int idade = Integer.parseInt(idadeTexto);
> 
> 		System.out.println("Idade: " + idade);
> 		
> 	}
> 
> }
> ```
>
> <img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**
>
> ```bash
> Exception in thread "main" java.lang.NumberFormatException: For input string: "ABC"
> 	at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)
> 	at java.base/java.lang.Integer.parseInt(Integer.java:668)
> 	at java.base/java.lang.Integer.parseInt(Integer.java:786)
> 	at conversores.Exemplo05.main(Exemplo05.java:8)
> ```
>

<br />

> [!IMPORTANT]
>
> **Separador Decimal**
>
> Os métodos `Double.parseDouble()` e `Float.parseFloat()` seguem o padrão internacional de representação numérica e aceitam apenas o ponto (`.`) como separador decimal. 
>
> Em países como o Brasil, é comum que valores sejam digitados utilizando vírgula (`,`), como `"1500,50"`. Nesses casos, a conversão gerará uma exceção do tipo `NumberFormatException`. Para evitar esse problema, substitua a vírgula por ponto antes de realizar a conversão, através do método da Classe String `replace()`:
>
> ```java
> String valorTexto = "1500,50";
> 
> double valor = Double.parseDouble(
>     valorTexto.replace(",", ".")
> );
> ```
>
> Essa prática é especialmente útil ao processar dados provenientes de formulários, planilhas, arquivos CSV ou entradas fornecidas pelo usuário. 

<br />

## 4. Conversão de Números para String



A conversão de valores numéricos para texto é muito utilizada para exibir informações em interfaces gráficas, relatórios, logs e mensagens ao usuário.

O método recomendado pela documentação é:

```java
String.valueOf()
```

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 06 - Conversão Número para String**

```java
package conversores;

public class Exemplo06 {

	public static void main(String[] args) {

		int idade = 30;
		String textoIdade = String.valueOf(idade);
		
		System.out.println("Idade: " + textoIdade);
		
		double preco = 99.90;
		String textoPreco = String.valueOf(preco);
		
		System.out.println("Preço: " + textoPreco);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Idade: 30
Preço: 99.9
```

**Vantagens**

- Código mais legível;
- Funciona com qualquer tipo primitivo;
- Evita ambiguidades causadas por concatenações.

<br />

## 5. Conversões Comuns entre Tipos Primitivos



Além das conversões envolvendo `String`, é muito comum converter valores entre tipos primitivos durante cálculos, processamento de dados e integração com bibliotecas e APIs.

Embora algumas conversões sejam realizadas automaticamente pelo Java, outras exigem o uso de **casting explícito**, principalmente quando existe risco de perda de precisão ou de dados.



### 5.1. double para float



O tipo `double` possui maior precisão e capacidade de armazenamento que o tipo `float`. Por esse motivo, a conversão exige casting explícito.

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 07 - Conversão - double para float**

```java
package conversores;

public class Exemplo07 {

	public static void main(String[] args) {

		double numeroDouble = 10.5;
		float numeroFloat = (float) numeroDouble;
		
		System.out.println("Número com poucas casas decimais: " + numeroFloat);
		
		double valor = 123.456789123;
		float resultado = (float) valor;

		System.out.println("Número com muitas casas decimais: " + resultado);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Número com poucas casas decimais: 10.5
Número com muitas casas decimais: 123.45679
```

Observe que, na segunda conversão, o valor original não foi preservado com exatidão. Isso ocorre porque o tipo `float` possui menor precisão e capacidade de armazenamento do que o tipo `double`. Como consequência, ao converter um número com muitas casas decimais, parte dessas informações pode ser perdida ou arredondada, resultando em um valor ligeiramente diferente do original. Esse comportamento é esperado e deve ser considerado sempre que houver conversão de um tipo mais preciso para outro menos preciso.

Essa conversão é muito comum quando trabalhamos com bibliotecas gráficas, jogos ou APIs que exigem valores do tipo `float`.



### 5.2. long para int



O tipo `long` ocupa 64 bits, enquanto o tipo `int` ocupa apenas 32 bits. Por isso, a conversão exige casting.

**<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>Exemplo 08 - Conversão - long para int**

```java
package conversores;

public class Exemplo08 {

	public static void main(String[] args) {

		long numeroLong = 100000L;
		int numeroInt = (int) numeroLong;
		
		System.out.println("Número pequeno: " + numeroInt);
		
		long valor = 3000000000L;
		int resultado = (int) valor;

		System.out.println("Número grande: " + resultado);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
Número com poucas casas decimais: 100000
Número com muitas casas decimais: -1294967296
```

Observe que, na segunda conversão, o valor original não foi preservado. Isso acontece porque o número armazenado em `long` ultrapassa o limite máximo suportado pelo tipo `int`. Como consequência, ocorre um **overflow**, fazendo com que parte dos bits do valor original seja descartada durante a conversão. O resultado é um número completamente diferente do esperado, que pode inclusive ser negativo. Esse comportamento é esperado quando um valor maior é convertido para um tipo que não possui capacidade suficiente para armazená-lo integralmente.

<br />

## 6. Conversões com o tipo char



Os computadores não armazenam caracteres como letras, números ou símbolos da mesma forma que os enxergamos. Internamente, cada caractere é representado por um valor numérico. 

Quando escrevemos um caractere como `'A'`, por exemplo, o computador o associa ao número **65**. Essa associação é definida por tabelas de codificação de caracteres, sendo a mais conhecida a **ASCII (American Standard Code for Information Interchange)**, que estabelece códigos numéricos para letras, dígitos, sinais de pontuação e caracteres de controle. 

Em Java, o tipo `char` utiliza o padrão **Unicode**, que é uma evolução do ASCII e inclui milhares de caracteres de diferentes idiomas e símbolos utilizados em todo o mundo. Graças a essa representação numérica, é possível converter caracteres em números e vice-versa, permitindo a manipulação de textos por meio de operações matemáticas e lógicas.

**Exemplos de códigos ASCII**

| Caractere | Código |
| --------- | ------ |
| A         | 65     |
| B         | 66     |
| C         | 67     |
| a         | 97     |
| b         | 98     |
| c         | 99     |
| 0         | 48     |
| 1         | 49     |
| 2         | 50     |

Embora o Java utilize Unicode, os primeiros 128 caracteres da tabela Unicode correspondem exatamente aos caracteres definidos pela tabela ASCII, garantindo compatibilidade com sistemas mais antigos.

<br />

🔗 [Tabela de Caracteres ASCII](https://github.com/rafaelq80/aulas_generation/blob/main/java/tabela_ascii.md)

🔗 [Tabela de Carcateres Unicode](https://symbl.cc/pt/unicode-table/)

<br />

### char para int



O tipo `char` representa um caractere Unicode e pode ser convertido automaticamente para `int`, pois todo valor válido de `char` cabe em um inteiro.

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 09 - Conversão - char para int**

```java
package conversores;

public class Exemplo09 {

	public static void main(String[] args) {

		char letra = 'A';
		int codigo = letra;

		System.out.println("Código Unicode: " + codigo);

		char simbolo = '€';
		int resultado = simbolo;

		System.out.println("Código Unicode: " + resultado);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```java
Código Unicode: 65
Código Unicode: 8364
```

O valor retornado corresponde ao código Unicode associado ao caractere.

Essa conversão é frequentemente utilizada em algoritmos que realizam manipulação de caracteres, validações ou operações envolvendo tabelas Unicode.



### int para char



A conversão de `int` para `char` exige casting explícito, pois nem todo valor inteiro pode ser representado por um caractere Unicode.

<img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="3%"/>**Exemplo 10 - Conversão - int para char**

```java
package conversores;

public class Exemplo10 {

	public static void main(String[] args) {

		int codigo = 65;
		char letra = (char) codigo;

		System.out.println(letra);

		for (int i = 65; i <= 90; i++) {
		    System.out.print((char) i + " ");
		}

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/>**Resultado do Algoritmo:**

```bash
A
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z 
```

Essa conversão é bastante utilizada quando desejamos obter um caractere a partir de seu código Unicode.

<br />

## 7. Boas Práticas e Cuidados



Ao trabalhar com conversões de tipos de dados, considere as seguintes recomendações:

- Utilize conversões implícitas sempre que possível;
- Faça casting apenas quando realmente necessário;
- Prefira `String.valueOf()` para converter valores em texto;
- Valide Strings antes de utilizar métodos como `parseInt()` e `parseDouble()`;
- Lembre-se de que casting não realiza arredondamento;
- Utilize `Math.round()` quando precisar arredondar números;
- Tenha atenção à perda de precisão em conversões de tipos maiores para menores;
- Ao utilizar classes Wrapper, lembre-se de que valores `null` podem gerar exceções durante processos de autoboxing e unboxing.

