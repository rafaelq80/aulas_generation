<h1>Instalação do Plugin Copilot4Eclipse - STS</h1>

<br />

O **Copilot4Eclipse** é o plugin oficial que integra o **GitHub Copilot** ao Eclipse IDE, permitindo receber sugestões de código geradas por IA diretamente enquanto você programa.

<img src="https://i.imgur.com/V5AvOqm.png" alt="https://i.imgur.com/V5AvOqm.png" />

O **GitHub Copilot** é um assistente de programação baseado em **inteligência artificial** criado pela **GitHub** em parceria com a **OpenAI**.

Ele funciona como um **“parceiro de programação”** que sugere automaticamente trechos de código, funções inteiras, comentários e até testes, com base no que você está digitando e no contexto do arquivo.

<br />

<h2>1. Principais Recursos</h2>



- **Autocompletar inteligente**: sugere trechos de código completos com base no que você digita.
- **Funções inteiras**: pode gerar métodos ou classes completos.
- **Explicação e refatoração**: ajuda a entender código e propor melhorias.
- **Testes automáticos**: sugere casos de teste unitários.
- **Contexto**: leva em conta o arquivo atual e até comentários que você escreve.

<br />

<h2>2. Vantagens</h2>



- **Produtividade**: acelera escrita de código e reduz erros de sintaxe.
- **Aprendizado**: ótimo para iniciantes, já que mostra diferentes formas de resolver um problema.
- **Integração nativa**: funciona como o auto completar tradicional do Eclipse, sem precisar abrir outra janela.
- **Versatilidade**: suporta várias linguagens (Java, Python, JS, entre outros.).

<br />

<h2>3. Eclipse Marketplace</h2>



Para instalar o **Copilot4Eclipse**, vamos utilizar a **Eclipse Marketplace**, que é a “loja de extensões” do **Eclipse IDE**.

![https://i.imgur.com/wrApdlB.png](https://i.imgur.com/wrApdlB.png)

Nela você encontra **plugins e ferramentas** (gratuitas e pagas) para adicionar novas funcionalidades ao Eclipse/STS, como:

- Suporte a novas linguagens,
- Integrações com frameworks,
- Temas,
- E até assistentes de IA como **Copilot4Eclipse**.

<br />

<h2>4. Instalação no Eclipse/STS</h2>



1. No Eclipse/STS, abra o **Eclipse Marketplace** através do menu: **Help 🡢 Eclipse Marketplace**

![https://i.imgur.com/EIwJsqK.png](https://i.imgur.com/EIwJsqK.png)

2. Será aberta a janela do **Eclipse Marketplace**

![https://i.imgur.com/X94rnWw.png](https://i.imgur.com/X94rnWw.png)

3. No item **Find**, digite **Copilot4Eclipse** e clique no botão **Go** para localizar o plugin.

![https://i.imgur.com/WBjlgyl.png](https://i.imgur.com/WBjlgyl.png)

4. Para instalar o plugin **Copilot4Eclipse**, clique no botão **Install** do plugin.

![https://i.imgur.com/ZCRMZhx.png](https://i.imgur.com/ZCRMZhx.png)

5. Será exibida a janela **Review Licenses**. Marque a opção **I accept the terms of the license agreement** e clique no botão **Finish**.

![https://i.imgur.com/klQ6JoY.png](https://i.imgur.com/klQ6JoY.png)

6. Será exibida a janela **Trust Authorithies**. Marque o link **https://downloads.genuitec.com** e clique no botão **Trust Selected**.

![https://i.imgur.com/ccWdmFi.png](https://i.imgur.com/ccWdmFi.png)

7. Aguarde a conclusão da instalação.
8. Ao final será exibida mensagem abaixo, pedindo para reiniciar o Eclipse/STS. Clique no botão **Restart Now**

![https://i.imgur.com/RqF5BRB.png](https://i.imgur.com/RqF5BRB.png)

9. Aguarde o Eclipse/STS reiniciar.

<br />

<h2>5. Ativação do Plugin Copilot4Eclipse</h2>



1. Após o Eclipse/STS reiniciar, note que o logo do plugin **Copilot4Eclipse** será exibido no canto inferior direito (indicado na imagem abaixo)

![https://i.imgur.com/VKvzvjh.png](https://i.imgur.com/VKvzvjh.png)

2. Clique no logo e no menu que será aberto escolha a opção **Sign In to GitHub Copilot**, para autorizar o uso do **GitHub Copilot Free** na sua conta do GitHub.

![https://i.imgur.com/p8AtjY0.png](https://i.imgur.com/p8AtjY0.png)

3. Será exibida a janela **GitHub Copilot Authorization**, contendo a Chave de Autorização do dispositivo (Device Code). Esta chave tem validade de 60 segundos. Caso ela não seja inserida no GitHub dentro do prazo, será necessário refazer o processo. Clique no botão **Copy Code and Open**

![https://i.imgur.com/uMAN3Ez.png](https://i.imgur.com/uMAN3Ez.png)

4. Você será redirecionado para o seu navegador, na tela **Device Activation**, caso você esteja logado na sua conta do GitHub. Caso não esteja, será solicitado o seu login antes de exibira a tela abaixo. Clique no botão **Continue**

![https://i.imgur.com/xUrx15v.png](https://i.imgur.com/xUrx15v.png)

5. Na próxima tela, cole o código de ativação, que foi copiado anteriormente do Eclipse/STS e clique no botão **Continue**

![https://i.imgur.com/K133bUL.png](https://i.imgur.com/K133bUL.png)

6. Na próxima tela, autorize o uso do **GitHub Copilot** na sua conta do GitHub clicando no botão **Authorize GitHub Copilot IDE Plugin**

![https://i.imgur.com/ePk0gGC.png](https://i.imgur.com/ePk0gGC.png)

7. Ao final será exibida a mensagem de confirmação abaixo:

![https://i.imgur.com/h9PHMuk.png](https://i.imgur.com/h9PHMuk.png)

8. Ao retornar para o Eclipse/STS será exibida uma mensagem de confirmação da instalação
9. Clique no logo do **Copilot4Eclipse** e no menu que será aberto, observe que na opção **Status** será exibida a mensagem: **Copilot4Eclipse ready**, indicando que o plugin está ativado e pronto para uso.

![https://i.imgur.com/CteGvdk.png](https://i.imgur.com/CteGvdk.png)

10. Caso a opção **Status** ainda esteja exibindo a mensagem: **GitHub Copilot sign in required**, reinicie o Eclipse/STS e verifique se o Status foi atualizado.

<br />

<h2>6. Utilizando o Plugin Copilot4Eclipse no Eclipse/STS</h2>



Para utilizar o **Copilot4Eclipse** no Eclipse/STS é necessário estar com pelo menos uma Classe de um Projeto aberta. O plugin oferece 2 recursos essenciais:

- **Autocomplete**: o Copilot sugere automaticamente trechos de código enquanto você digita (desde uma linha até funções inteiras), parecido com o auto completar do Eclipse, mas muito mais inteligente, porque entende o contexto e comentários.
- **Chat**: você pode conversar com o Copilot dentro do Eclipse, pedindo explicações de código, refatorações, geração de testes ou alternativas de solução, como se fosse um assistente interativo integrado à IDE.

A opção **auto completar** é habilitada durante a instalação. O **chat**, precisa ser aberto dentro do Eclipse/STS

1. Para **desabilitar o auto completar**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Disable Completions**  ou **Disable Completions For Java**.

![https://i.imgur.com/AtVJ9ei.png](https://i.imgur.com/AtVJ9ei.png)

2. Para **habilitar o auto completar**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Enable Completions**.

![https://i.imgur.com/dqkkEwt.png](https://i.imgur.com/dqkkEwt.png)

3. Para **abrir o chat**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Open Chat Panel**.

![https://i.imgur.com/4tNt92t.png](https://i.imgur.com/4tNt92t.png)

4. O Chat será exibido no lado direito da tela, como vemos na imagem abaixo:

![https://i.imgur.com/EMosfQ8.png](https://i.imgur.com/EMosfQ8.png)
