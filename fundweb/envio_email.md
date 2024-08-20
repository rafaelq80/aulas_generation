<h1>Projeto 01 - Portfólio - Enviar E-mail pelo Formulário</h1>



Através dos Eventos da Linguagem JavaScript, vamos tornar o nosso formulário funcional, ou seja, vamos configurar o formulário para enviar e-mail para o seu endereço de e-mail, contendo as informações inseridas no formulário.

Para enviar o e-mail, utilizaremos o serviço gratuito de envio de mensagens **Form Submit**. 

<br />

<h2>1. Form Submit</h2>



O **FormSubmit** é uma ferramenta que facilita o envio de dados de formulários HTML diretamente para o seu e-mail, sem a necessidade de configurar uma API ou usar código de servidor como PHP ou JavaScript, que geralmente são bloqueados pelos serviços de e-mail. 

<br />

<div align="left"><img src="https://i.imgur.com/wKHNfGi.png" title="source: imgur.com" width="4%"/> <a href="https://formsubmit.co/" target="_blank"><b>Form Submit</b></a></div>

<br />

O Form Submit é muito simples de se utilizar e não requer grandes configurações ou a criação de uma conta. Em linhas gerais ele funciona da seguinte forma:

1. **Conectar o formulário**: Adicione no atributo `action` do seu formulário HTML  a URL do FormSubmit com o seu endereço de e-mail (https://www.formsubmit.co/seu_email@email.com.br).
2. **Adicionar atributos nos campos do formulário**: Inclua nos atributos `name` de todos os elementos do formulário (como `<input>`, `<select>`, e `<textarea>`) os atributos name (nome), email, subject (assunto) e message (mensagem).
3. **Enviar e confirmar**: Submeta o formulário uma vez para ativar o serviço. Você receberá um e-mail de confirmação para validar o seu endereço. Valide o seu endereço clicando no link recebido no e-mail.
4. **Adicione o código de validação na URL:** Após a ativação, substitua o endereço do seu e-mail na propriedade `action` pelo código de ativação recebido no e-mail de confirmação (https://www.formsubmit.co/seu_codigo_de_ativacao).

Além disso, o FormSubmit oferece recursos avançados, como definir uma URL de confirmação após o envio do formulário, personalizar o assunto do e-mail e adicionar endereços de e-mail em cópia, entre outros.

Vamos configurar o Form Submit na prática!

<br />

<h2>👣 Passo 01 - Atualizar o Formulário na Página index</h2>



1. Abra a página **index.html**
2. Localize o trecho de código abaixo:

<div align="center"><img src="https://i.imgur.com/nGgIKYE.png" title="source: imgur.com" /></div>

3. Substitua a **linha 03**, pelo trecho de código abaixo:

```html
<form action="https://formsubmit.co/seu_email@email.com" method="POST">
```

*Na propriedade `action`, onde está escrito **seu_email@email.com**, substitua pelo endereço do seu e-mail pessoal.*

> A propriedade `action` do elemento `<form>` do HTML especifica para onde os dados do formulário devem ser enviados quando ele é submetido, ou seja, quando o botão Enviar for clicado. Basicamente, ela define a URL do servidor que processará os dados do formulário, em nosso projeto, o servidor do serviço Form Submit, que se encarregará de enviar a mensagem par o seu e-mail pessoal.

4. Na **linha 04**, adicione o trecho de código abaixo:

```html
<input type="hidden" name="_next" value="http://localhost:5500/sucess.html">
<input type="hidden" name="_captcha" value="false">
```

O trecho de código acima, insere 2 inputs do tipo **hidden**, ou seja, são inputs ocultos, que não ficam visíveis para o usuário, mas que possuem valores padrões, que são enviados para o servidor em conjunto com os dados preenchidos no formulário.

O primeiro input, chamado **_next**, indica o endereço da página que será exibida quando o envio do e-mail for bem sucedido!

O segundo input, chamado **_captcha**, indica que o antes de enviar o e-mail o usuário não precisará preencher o **captcha** (false), para verificar se é um ser humano que está enviando a mensagem.

> O **CAPTCHA** (*Completely Automated Public Turing test to tell Computers and Humans Apart*) é um mecanismo de segurança digital projetado para diferenciar humanos de *Bots* (programas de software projetados para executar tarefas automatizadas na internet). Ele apresenta desafios que são fáceis para humanos resolverem, mas difíceis para máquinas.
>
> <div align="center"><img src="https://i.imgur.com/2sgPeyf.png" title="source: imgur.com" /></div>
>
> Existem várias formas de CAPTCHA, entre eles, destacamos:
>
> 1. **Texto Distorcido**: O usuário deve digitar corretamente um texto distorcido.
> 2. **Seleção de Imagens**: O usuário deve selecionar imagens que correspondem a uma descrição específica.
> 3. **ReCAPTCHA**: Desenvolvido pelo Google, pode incluir a marcação de uma caixa "Não sou um robô" ou a seleção de imagens.
>
> Esses testes ajudam a proteger sites contra spam e outras atividades maliciosas automatizadas.
>

5. Na imagem abaixo, você confere como ficou o código do formulário com as alterações, que estão destacadas em amarelo:

<div align="center"><img src="https://i.imgur.com/jZuqKVC.png" title="source: imgur.com" /></div>

<br />

> [!WARNING]
>
> **Não esqueça de inserir o seu endereço de e-mail pessoal, na url da propriedade action do formulário.**

<br />

<div align="left"><img src="https://i.imgur.com/wKHNfGi.png" title="source: imgur.com" width="4%"/> <a href="https://formsubmit.co/documentation" target="_blank"><b>Documentação: Form Submit</b></a></div>

<br />

<h2>👣 Passo 02 - Validar o E-mail</h2>



1. Abra a página index.html no Navegador, através do **Live Server** e clique no item **Contate-me** do menu.
2. Preencha o formulário e clique no botão **Enviar**.

<div align="center"><img src="https://i.imgur.com/PB7dOqR.png" title="source: imgur.com" /></div>

3. Após o envio, você será redirecionado para a página abaixo, solicitando que você acesse o seu e-mail pessoal e verifique o e-mail que foi enviado para ativar o serviço.

<div align="center"><img src="https://i.imgur.com/DTCUcwj.png" title="source: imgur.com" /></div>

4. Você receberá um e-mail semelhante a imagem abaixo. Clique no botão **ACTIVATE FORM**, para validar o e-mail:

<div align="center"><img src="https://i.imgur.com/kY7lo2W.png" title="source: imgur.com" /></div>

5. Você será redirecionado para a página abaixo, indicando que o e-mail foi validado:

<div align="center"><img src="https://i.imgur.com/vxYq79R.png" title="source: imgur.com" /></div>

6. Volte para o e-mail de ativação e copie o código de ativação (destacado em vermelho na imagem):

<div align="center"><img src="https://i.imgur.com/EVfNNJT.png" title="source: imgur.com" /></div>

7. Abra a página **index.html** no Visual Studio Code e substitua o seu endereço de e-mail na url da propriedade action do formulário, pelo **código de ativação**, como mostra a imagem abaixo (destacado em amarelo):

<div align="center"><img src="https://i.imgur.com/YOLoRse.png" title="source: imgur.com" /></div>

8. Volte para o Navegador, abra a página index, preencha o formulário novamente e clique no botão **Enviar**:

<div align="center"><img src="https://i.imgur.com/PB7dOqR.png" title="source: imgur.com" /></div>

9. Observe que desta vez você será redirecionado para a página **sucess**. Clique no botão **Voltar**, para retornar para a página index.

<div align="center"><img src="https://i.imgur.com/dtO7AyW.png" title="source: imgur.com" /></div>

10. Volte para o seu e-mail pessoal e observe que você recebeu uma mensagem do Form Submit, contendo os dados preenchidos no formulário:

<div align="center"><img src="https://i.imgur.com/DzJVYG7.png" title="source: imgur.com" /></div>

O Formulário de Contato está funcional!

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div> 
