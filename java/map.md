# Collection Map



A interface **Map** define uma estrutura de dados que armazena elementos no formato **chave e valor** (*key-value*).

Diferente das interfaces `List` e `Set`, que armazenam apenas valores, a `Map` utiliza um objeto como **chave** para recuperar outro objeto armazenado como **valor**.

```
Chave → Valor
```

Cada valor armazenado possui uma chave associada, que será utilizada para localizar esse dado posteriormente.

As chaves não podem se repetir, seguindo o mesmo princípio da interface `Set`, porém os valores podem ser duplicados para chaves diferentes.

Uma `Map` não possui necessariamente uma ordem definida para percorrer os elementos.

**Exemplo:**

```
Chave        Valor
----------------------
1            Rafael
2            Maria
3            João
```

Neste exemplo:

- A chave identifica o elemento armazenado.
- O valor representa a informação associada à chave.

<br />

### Principais Implementações da Interface Map

| Implementação   | Descrição                                                    |
| --------------- | ------------------------------------------------------------ |
| `HashMap`       | Armazena os objetos em formato chave-valor. Não mantém os elementos ordenados e não permite chaves duplicadas. |
| `LinkedHashMap` | Armazena os objetos em formato chave-valor e mantém a ordem de inserção dos elementos. Não permite chaves duplicadas. |
| `TreeMap`       | Armazena os objetos em formato chave-valor e mantém os elementos ordenados pela chave. Não permite chaves duplicadas. |
| `HashTable`     | Armazena objetos em formato chave-valor e utiliza o método `hashCode()` para encontrar a posição dos elementos. |

<br />

### Sintaxe:

```java
Map<K, V> usuarios = new HashMap<K, V>();
```

O construtor sem argumento padrão cria um Objeto da Classe `HashMap` novo e vazio.

Os itens **`<K, V>`** em Java representam **Java Type Generic**. Ele são utilizados para definir os tipos de Objetos que serão armazenados na Collection.

Diferente das Collections `List` e `Set`, a interface `Map` utiliza dois tipos genéricos:

- O **`<K>`** representa o tipo da **Chave** (*Key*).
- O segundo **`<V>`** representa o tipo do **Valor** (*Value*).

Os tipos de dados obrigatoriamente devem ser Objetos, podendo ser uma **Classe Wrapper** ou uma **Classe criada pela pessoa desenvolvedora**.

A busca dos valores na Collection Map não é feita pela posição, como acontece em um array ou `List`, mas sim pela chave.

<br />

### Principais Métodos da Interface Map

| Método                 | Descrição                                        |
| ---------------------- | ------------------------------------------------ |
| `put(Chave, Valor)`    | Adiciona um elemento na Collection Map.          |
| `get(Chave)`           | Recupera um valor utilizando uma chave.          |
| `remove(Chave)`        | Remove um elemento utilizando uma chave.         |
| `containsKey(Chave)`   | Verifica se uma determinada chave existe na Map. |
| `containsValue(Valor)` | Verifica se um determinado valor existe na Map.  |
| `keySet()`             | Retorna todas as chaves armazenadas na Map.      |
| `values()`             | Retorna todos os valores armazenados na Map.     |
| `entrySet()`           | Retorna os elementos no formato chave e valor.   |
| `size()`               | Retorna a quantidade de elementos armazenados.   |
| `clear()`              | Remove todos os elementos da Map.                |
| `isEmpty()`            | Retorna `true` se a Map estiver vazia.           |

<br />

## <img src="https://i.imgur.com/gsSDe7P.png" title="source: imgur.com" width="4%"/> Exemplo 01 - Collection HashMap:



No exemplo abaixo, vamos construir uma Collection `HashMap`, chamada `usuarios`, contendo uma lista de usuários identificados por um código numérico.

```java
package hashmap;

import java.util.HashMap;
import java.util.Map;

public class CollectionMap {

	public static void main(String[] args) {

		// Cria a Collection HashMap chamada usuarios
		Map<Integer, String> usuarios = new HashMap<Integer, String>();

		// Adiciona elementos utilizando chave e valor
		usuarios.put(1, "Rafael");
		usuarios.put(2, "Maria");
		usuarios.put(3, "João");

		// Mostra todos os usuários cadastrados
		System.out.println("\nUsuários cadastrados: " + usuarios);

		// Recupera um valor através da chave
		System.out.println("\nUsuário da chave 2: " 
				+ usuarios.get(2));

		// Verifica se uma chave existe
		System.out.println("\nA chave 1 existe? "
				+ usuarios.containsKey(1));

		// Verifica se um valor existe
		System.out.println("\nO usuário Maria existe? "
				+ usuarios.containsValue("Maria"));

		// Remove um elemento pela chave
		usuarios.remove(3);

		System.out.println("\nApós remover a chave 3: "
				+ usuarios);

		// Mostra todas as chaves
		System.out.println("\nChaves cadastradas: "
				+ usuarios.keySet());

		// Mostra todos os valores
		System.out.println("\nValores cadastrados: "
				+ usuarios.values());

		// Mostra o tamanho da Collection
		System.out.println("\nQuantidade de usuários: "
				+ usuarios.size());

	}

}
```

<img src="https://i.imgur.com/V2ReOnx.png" title="source: imgur.com" width="3%"/> **Resultado do Algoritmo:**

```bash
Usuários cadastrados: {1=Rafael, 2=Maria, 3=João}

Usuário da chave 2: Maria

A chave 1 existe? true

O usuário Maria existe? true

Após remover a chave 3: {1=Rafael, 2=Maria}

Chaves cadastradas: [1, 2]

Valores cadastrados: [Rafael, Maria]

Quantidade de usuários: 2
```

<br />

> [!IMPORTANT]
>
> As demais implementações da interface `Map`, como `LinkedHashMap`, `TreeMap` e `HashTable`, possuem uma sintaxe semelhante. A principal diferença entre elas está no comportamento de armazenamento e organização dos elementos, não na forma de declaração da Collection.

<br />

### Quando utilizar Map?



Utilize a Collection `Map` quando precisar:

✅ Associar uma informação a outra
✅ Buscar dados rapidamente através de uma chave
✅ Representar estruturas como cadastro, configurações e tabelas

**Exemplos reais:**

| Situação             | Chave       | Valor      |
| -------------------- | ----------- | ---------- |
| Cadastro de usuários | ID          | Usuário    |
| Estoque              | Produto     | Quantidade |
| Agenda telefônica    | Nome        | Telefone   |
| Configurações        | Propriedade | Valor      |

<br />

<div align="left"><img src="https://i.imgur.com/JSfXyzm.png" title="source: imgur.com" width="30px"/> <a href="https://docs.oracle.com/javase/8/docs/api/java/util/Map.html" target="_blank"><b>Documentação: Collection Map</b></a></div>

<br />
