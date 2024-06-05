<h1>Debug de código JavaScript no Visual Studio Code</h1>



*O Debug (depuração)* de código permite executar um programa de forma interativa enquanto a pessoa desenvolvedora observa o código-fonte e as mudanças que as variáveis sofrem durante a execução.

Um *Breakpoint (ponto de interrupção)* no código-fonte especifica onde a execução do programa deve parar durante a depuração. Uma vez que a execução para o programa no ponto indicado, você pode executar linha a linha, passo a a passo e investigar variáveis, alterar seu conteúdo, entre outros.

Para exemplificar o funcionamento do Debug, crie uma pasta chamada **debug**, na pasta **javascript**. 

Na sequência crie o arquivo Debug.js, dentro da pasta **debug** e insira o código abaixo:

```js
const leia = require('readline-sync');

		let vetorInteiros = new Array(5);

        for (let indice = 0; indice < vetorInteiros.length; indice++) {
			
			vetorInteiros[indice] = leia.questionInt("Digite um valor para a posicao [" + indice + "]: ");
		}

		for (let contador = 0; contador < vetorInteiros.length; contador++)
			console.log("posição " + contador + " = " + vetorInteiros[contador]);
		
```

Se você executar o código acima pelo modo tradicional, você observará que será solicitada a entrada de dados no vetor e ao final, será exibido todos os dados inseridos no vetor, como vemos abaixo: 

```bash
Digite um valor para a posição [0]
10
Digite um valor para a posição [1]
20
Digite um valor para a posição [2]
30
Digite um valor para a posição [3]
40
Digite um valor para a posição [4]
50
posição 0 = 10
posição 1 = 20
posição 2 = 30
posição 3 = 40
posição 4 = 50
```

<br />

<h2>1. Configurando o Debug no VSCode</h2>



Primeiro precisamos configurar o Debug do JavaScript no VSCode:

1. Abra a pasta **.vscode**, localizada na pasta **javascript**:

<div align="center"><img src="https://i.imgur.com/wO9ZFYp.png" title="source: imgur.com" /></div>

2. Adicione o código abaixo no arquivo **launch.json**:

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node-terminal",
            "name": "Debug Current JS File (node)",
            "request": "launch",
            "command": "node -- ${fileBasenameNoExtension}",
            "cwd": "${fileDirname}"
        },
        {
            "type": "node-terminal",
            "name": "Debug Current TS File (ts-node)",
            "request": "launch",
            "command": "ts-node -- ${fileBasenameNoExtension}",
            "cwd": "${fileDirname}"
        },
        {
            "type": "node-terminal",
            "name": "Debug Current Test File (npm run test)",
            "request": "launch",
            "command": "npm run test -- ${fileBasenameNoExtension}",
            "cwd": "${fileDirname}"
        }
    ]
}
```

Esta configuração, criará 3 formas de executar o Debug:

1. Debug para códigos JavaScript
2. Debug para códigos TypeScript
3. Debug para executar Testes

<br />

<h2>2. Executando o código no Debug</h2>



Primeiro precisamos definir um Breakpoint, ou seja um ponto de parada, para acompanharmos a execução passo a passo. Vamos inserir um Breakpoint na linha 5, ou seja, no Laço de Repetição responsável por inserir dados no vetor:

1. Na linha 05, em cima do número 05, clique com o botão direito do mouse. 

<div align="center"><img src="https://i.imgur.com/yrz2Srr.png" title="source: imgur.com" /></div>

2. No menu que será aberto, clique na opção **Add Breakpoint**.

<div align="center"><img src="https://i.imgur.com/f6Ryeim.png" title="source: imgur.com" /></div>

3. Observe que será adicionada uma bolinha vermelha ao lado do número 05, indicando que o Breakpoint foi adicionado.

<div align="center"><img src="https://i.imgur.com/MCvcpVP.png" title="source: imgur.com" /></div>

<br />

Na sequência, vamos executar o código em modo **Debug**:

1. Na **Barra de atividades (Activity Bar)**, localizada no lado esquerdo da tela do Visual Studio Code, clique no ícone <img src="https://i.imgur.com/65Nk3Dh.png" title="source: imgur.com" width="4%"/> **Run and Debug**:

2. Será aberta a janela abaixo:

<div align="center"><img src="https://i.imgur.com/pGZOa20.png" title="source: imgur.com" /></div>

- A Guia **VARIABLES**, permite visualizar as variáveis do seu código.
- A Guia **WATCH**, permite adicionar variáveis e objetos para serem monitorados durante o Debug.
- A Guia **CALL STACK**, permite visualizar o script que está sendo executado no Debug.

3. Na parte superior da tela, clique no **menu** (indicado na imagem abaixo), para escolher o tipo de Debug que será executado:

<div align="center"><img src="https://i.imgur.com/OSXwbsp.png" title="source: imgur.com" /></div>

4. No menu, selecione a opção **Debug Current JS (node)**:

<div align="center"><img src="https://i.imgur.com/6qJyMYp.png" title="source: imgur.com" /></div>

5. Na Guia **WATCH**, clique no botão **+**, para adicionar uma variável no monitoramento do Debug:

<div align="center"><img src="https://i.imgur.com/LHRWFaA.png" title="source: imgur.com" /></div>

6. Vamos adicionar o nosso vetor **vetorInteiros**:

<div align="center"><img src="https://i.imgur.com/Mke9lA3.png" title="source: imgur.com" /></div>

7. Para executar o Debug, Na parte superior da tela do Debug, clique no botão  **Start Debug** (indicado na imagem abaixo):

<div align="center"><img src="https://i.imgur.com/slZg10J.png" title="source: imgur.com" /></div>

8. O VSCode fornece uma Barra de Ferramentas (veja na imagem abaixo), na parte superior da tela, para controlar a execução do programa que você está depurando. Normalmente, é mais fácil usar as teclas de atalho correspondentes para controlar essa execução.

<div align="center"><img src="https://i.imgur.com/U8SFoPl.png" title="source: imgur.com" /></div>

| Tecla             | Comando       | Descrição                                                    |
| ----------------- | ------------- | ------------------------------------------------------------ |
|                   | **Run/Pause** | Executa ou Pausa o Debug.                                    |
| **F5**            | **Step Into** | Executa a linha atualmente selecionada e vai para a próxima linha em seu programa. Se a linha selecionada for um método, ele executará todas as etapas do depurador no código associado. |
| **F6**            | **Step Over** | Passa por cima da chamada, ou seja, executa um método sem depurar. |
| **F7**            | **Step Out**  | Avança para o chamador do método atualmente executado. Isso finaliza a execução do método atual e retorna ao chamador desse método. |
| **CTRL SHIFT F5** | **Restart**   | Reinicia o Depurador.                                        |
| **CTRL F2**       | **Stop**      | Finaliza o Depurador.                                        |

9. Na animação abaixo, veremos a execução do nosso código no Debug. Observe que foi utilizado o comando F6 (Step Over), para executar o código passo a passo a partir do Breakpoint:

<div align="center"><img src="https://ik.imagekit.io/vzr6ryejm/debug.gif?updatedAt=1711113244164f" /></div>

Observe na animação acima, na Guia **WATCH**, que a cada número digitado, uma nova posição do vetor é preenchida.

