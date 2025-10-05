<h1>Instalação do Plugin Copilot4Eclipse - STS</h1>

<br />

O **Copilot4Eclipse** é o plugin oficial que integra o **GitHub Copilot** ao Eclipse IDE, permitindo receber sugestões de código geradas por IA diretamente enquanto você programa.

<div align="center"><img src="https://i.imgur.com/V5AvOqm.png" alt="https://i.imgur.com/V5AvOqm.png" /></div>

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

<div align="center"><img src="https://i.imgur.com/wrApdlB.png" alt="https://i.imgur.com/wrApdlB.png" /></div>

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

<div align="center"><img src="https://i.imgur.com/X94rnWw.png" alt="https://i.imgur.com/X94rnWw.png" /></div>

3. No item **Find**, digite **Copilot4Eclipse** e clique no botão **Go** para localizar o plugin.

<div align="center"><img src="https://i.imgur.com/WBjlgyl.png" alt="https://i.imgur.com/WBjlgyl.png" /></div>

4. Para instalar o plugin **Copilot4Eclipse**, clique no botão **Install** do plugin.

<div align="center"><img src="https://i.imgur.com/ZCRMZhx.png" alt="https://i.imgur.com/ZCRMZhx.png" /></div>

5. Será exibida a janela **Review Licenses**. Marque a opção **I accept the terms of the license agreement** e clique no botão **Finish**.

<div align="center"><img src="https://i.imgur.com/klQ6JoY.png" alt="https://i.imgur.com/klQ6JoY.png" /></div>

6. Será exibida a janela **Trust Authorithies**. Marque o link **https://downloads.genuitec.com** e clique no botão **Trust Selected**.

<div align="center"><img src="https://i.imgur.com/ccWdmFi.png" alt="https://i.imgur.com/ccWdmFi.png" /></div>

7. Aguarde a conclusão da instalação.
8. Ao final será exibida mensagem abaixo, pedindo para reiniciar o Eclipse/STS. Clique no botão **Restart Now**

<div align="center"><img src="https://i.imgur.com/RqF5BRB.png" alt="https://i.imgur.com/RqF5BRB.png" /></div>

9. Aguarde o Eclipse/STS reiniciar.

<br />

<h2>5. Ativação do Plugin Copilot4Eclipse</h2>



1. Após o Eclipse/STS reiniciar, note que o logo do plugin **Copilot4Eclipse** será exibido no canto inferior direito (indicado na imagem abaixo)

![https://i.imgur.com/VKvzvjh.png](https://i.imgur.com/VKvzvjh.png)

2. Clique no logo e no menu que será aberto escolha a opção **Sign In to GitHub Copilot**, para autorizar o uso do **GitHub Copilot Free** na sua conta do GitHub.

<div align="center"><img src="https://i.imgur.com/p8AtjY0.png" alt="https://i.imgur.com/p8AtjY0.png" /></div>

3. Será exibida a janela **GitHub Copilot Authorization**, contendo a Chave de Autorização do dispositivo (Device Code). Clique no botão **Copy Code and Open**

<div align="center"><img src="https://i.imgur.com/uMAN3Ez.png" alt="https://i.imgur.com/uMAN3Ez.png" /></div>

4. Será aberta janela abaixo, indicando que você tem 60 segundos para adicionar a chave de ativação no GitHub. Caso ela não seja inserida no GitHub dentro do prazo, será necessário refazer o processo.

<div align="center"><img src="https://i.imgur.com/PZ6YYiY.png" title="source: imgur.com" /></div>

5. Você será redirecionado para o seu navegador, na tela **Device Activation**, caso você esteja logado na sua conta do GitHub. Caso não esteja, será solicitado o seu login antes de exibir a tela abaixo. Clique no botão **Continue**

<div align="center"><img src="https://i.imgur.com/xUrx15v.png" alt="https://i.imgur.com/xUrx15v.png" /></div>

6. Na próxima tela, cole o código de ativação, que foi copiado anteriormente do Eclipse/STS e clique no botão **Continue**

<div align="center"><img src="https://i.imgur.com/K133bUL.png" alt="https://i.imgur.com/K133bUL.png" /></div>

7. Na próxima tela, autorize o uso do **GitHub Copilot** na sua conta do GitHub clicando no botão **Authorize GitHub Copilot IDE Plugin**

<div align="center"><img src="https://i.imgur.com/ePk0gGC.png" alt="https://i.imgur.com/ePk0gGC.png" /></div>

8. Ao final será exibida a mensagem de confirmação abaixo:

<div align="center"><img src="https://i.imgur.com/h9PHMuk.png" alt="https://i.imgur.com/h9PHMuk.png" /></div>

9. Ao retornar para o Eclipse/STS será exibida uma mensagem de confirmação da ativação. Clique em **OK** para continuar.

<div align="center"><img src="https://i.imgur.com/t1tnrNh.png" title="source: imgur.com" /></div>

10. Clique no logo do **Copilot4Eclipse** e no menu que será aberto, observe que na opção **Status** será exibida a mensagem: **Copilot4Eclipse ready**, indicando que o plugin está ativado e pronto para uso.

<div align="center"><img src="https://i.imgur.com/CteGvdk.png" alt="https://i.imgur.com/CteGvdk.png" /></div>

11. Caso a opção **Status** ainda esteja exibindo a mensagem: **GitHub Copilot sign in required**, reinicie o Eclipse/STS e verifique se o Status foi atualizado.
12. Após a ativação, será exibida a mensagem abaixo, ao lado do ícone do **Copilot4GitHub**, contendo as informações da licença gratuita do GitHub Copliot. Para fechar, clique no **X**.

<div align="center"><img src="https://i.imgur.com/Hq9kHRN.png" title="source: imgur.com" /></div>

<br />

<h2>6. Utilizando o Plugin Copilot4Eclipse no Eclipse/STS</h2>



Para utilizar o **Copilot4Eclipse** no Eclipse/STS é necessário estar com pelo menos uma Classe de um Projeto aberta. O plugin oferece 2 recursos essenciais:

- **Autocomplete**: o Copilot sugere automaticamente trechos de código enquanto você digita (desde uma linha até funções inteiras), parecido com o auto completar do Eclipse, mas muito mais inteligente, porque entende o contexto e comentários.
- **Chat**: você pode conversar com o Copilot dentro do Eclipse, pedindo explicações de código, refatorações, geração de testes ou alternativas de solução, como se fosse um assistente interativo integrado à IDE.

A opção **auto completar** é habilitada durante a instalação. O **chat**, precisa ser aberto dentro do Eclipse/STS

1. Para **desabilitar o auto completar**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Disable Completions**  ou **Disable Completions For Java**.

<div align="center"><img src="https://i.imgur.com/AtVJ9ei.png" alt="https://i.imgur.com/AtVJ9ei.png" /></div>

2. Para **habilitar o auto completar**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Enable Completions**.

<div align="center"><img src="https://i.imgur.com/dqkkEwt.png" alt="https://i.imgur.com/dqkkEwt.png" /></div>

3. Para **abrir o chat**, clique no logo do **Copilot4Eclipse** e no menu que será aberto, clique na opção **Open Chat Panel**.

<div align="center"><img src="https://i.imgur.com/4tNt92t.png" alt="https://i.imgur.com/4tNt92t.png" />

4. O Chat será exibido no lado direito da tela, como vemos na imagem abaixo:

![https://i.imgur.com/EMosfQ8.png](https://i.imgur.com/EMosfQ8.png)
