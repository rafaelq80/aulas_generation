# StringBuilder



A classe **StringBuilder** é utilizada para criar e manipular objetos do tipo `String` de forma mais eficiente.

Em Java, objetos da classe `String` são **imutáveis**, ou seja, após sua criação, seu valor não pode ser alterado.

**Exemplo:**

```java
String texto = "Java";

texto = texto + " Full Stack";
```

Neste caso, o Java não altera a String original. Ele cria um novo objeto na memória contendo o novo valor.

Quando realizamos muitas alterações em uma String, como concatenações dentro de laços de repetição, esse processo pode gerar vários objetos desnecessários.

Para esses cenários, utilizamos a classe **StringBuilder**.

<br />

### Diferença entre String e StringBuilder

| String                                          | StringBuilder                               |
| ----------------------------------------------- | ------------------------------------------- |
| É imutável                                      | É mutável                                   |
| Cada alteração cria um novo objeto              | Altera o mesmo objeto                       |
| Melhor para textos que não mudam                | Melhor para manipulação frequente de textos |
| Possui menor desempenho em muitas concatenações | Possui melhor desempenho em concatenações   |

<br />

### Sintaxe:



A criação de um objeto `StringBuilder` pode ser feita utilizando o construtor padrão:

```java
StringBuilder texto = new StringBuilder();
```

Também é possível iniciar com um valor:

```java
StringBuilder texto = new StringBuilder("Java");
```

<br />

### Principais Métodos da Classe StringBuilder

| Método           | Descrição                                     |
| ---------------- | --------------------------------------------- |
| `append()`       | Adiciona conteúdo ao final da StringBuilder   |
| `insert()`       | Insere conteúdo em uma determinada posição    |
| `delete()`       | Remove caracteres de um intervalo informado   |
| `deleteCharAt()` | Remove um caractere de uma posição específica |
| `replace()`      | Substitui uma sequência de caracteres         |
| `reverse()`      | Inverte a ordem dos caracteres                |
| `length()`       | Retorna a quantidade de caracteres            |
| `charAt()`       | Retorna o caractere de uma posição específica |
| `toString()`     | Converte um StringBuilder em String           |

<br />

## <img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="4%"/> Exemplo 01 - StringBuilder:



No exemplo abaixo, vamos utilizar os principais métodos da classe `StringBuilder`.

```java
package stringbuilder;

public class ExemploStringBuilder {

	public static void main(String[] args) {

		// Cria um StringBuilder
		StringBuilder texto = new StringBuilder("Java");

		// Adiciona conteúdo no final
		texto.append(" Full Stack");

		System.out.println("Após append: " + texto);

		// Insere conteúdo em uma posição específica
		texto.insert(5, "Developer ");

		System.out.println("Após insert: " + texto);

		// Substitui uma parte do texto
		texto.replace(0, 4, "Java 21");

		System.out.println("Após replace: " + texto);

		// Remove caracteres
		texto.delete(8, 17);

		System.out.println("Após delete: " + texto);

		// Inverte o conteúdo
		texto.reverse();

		System.out.println("Após reverse: " + texto);

		// Retorna o tamanho do texto
		System.out.println("Quantidade de caracteres: "
				+ texto.length());

		// Converte StringBuilder para String
		String resultado = texto.toString();

		System.out.println("String final: " + resultado);

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/> **Resultado do Algoritmo:**

```bash
Após append: Java Full Stack
Após insert: Java Developer Full Stack
Após replace: Java 21 Developer Full Stack
Após delete: Java 21  Full Stack
Após reverse: kcatS lluF  12 avaJ
Quantidade de caracteres: 19
String final: kcatS lluF  12 avaJ
```

<br />

### Quando utilizar StringBuilder?



Utilize `StringBuilder` quando precisar realizar várias alterações em uma String, como:

- Construção de mensagens grandes;
- Geração de relatórios;
- Montagem de textos em laços de repetição;
- Manipulação de Strings em algoritmos;
- Processamento de arquivos.

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html" target="_blank"><b>Documentação: StringBuilder</b></a></div>

<br />
