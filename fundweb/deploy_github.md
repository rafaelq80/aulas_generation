<h1>Projeto 01 - Portfólio - Deploy no GitHub Pages</h1>



O **GitHub Pages** é um serviço gratuito, oferecido pelo GitHub, que permite hospedar sites estáticos a partir de um repositório GitHub. O GitHub Pages é uma ferramenta muito popular entre pessoas desenvolvedoras, especialmente para criar portfólios, blogs, documentações de projetos e até mesmo sites pessoais.

<br />

<h3>1.1. Recursos do GitHub Pages</h3>



1. **Hospedagem Gratuita**: Você pode hospedar seu site gratuitamente no domínio `github.io` ou em um domínio personalizado.

2. **Integração com GitHub**: O GitHub Pages é diretamente integrado com repositórios do GitHub, o que facilita o processo de publicação. Basta efetuar um push no repositório remoto, que o site será automaticamente atualizado.

3. **Suporte para Jekyll**: GitHub Pages suporta o Jekyll, um gerador de sites estáticos que permite criar sites complexos e dinâmicos usando Markdown. Ele converte automaticamente seus arquivos Markdown em HTML, facilitando a criação de blogs e documentações.

4. **Temas**: Com Jekyll, é possível usar temas prontos ou personalizar seu próprio tema para o site.

5. **HTTPS**: O GitHub Pages oferece HTTPS automaticamente para garantir que seu site seja seguro e que os dados transmitidos sejam criptografados.

6. **Implementação Fácil**: Com um simples fluxo de trabalho Git, você pode configurar e publicar um site com apenas alguns comandos.

<br />

<h3>1.2. Benefícios do GitHub Pages</h3>



1. **Facilidade de Uso**: Não é necessário conhecimento profundo em administração de servidores ou configuração de hospedagem. O GitHub Pages automatiza a maioria dos processos.

2. **Colaboração**: Como todos os arquivos do site são armazenados em um repositório GitHub, várias pessoas podem colaborar no desenvolvimento e manutenção do site, aproveitando o sistema de controle de versão do Git.

3. **Controle Total**: Você tem controle total sobre os arquivos e o código do site, permitindo customização e ajustes conforme necessário.

4. **Visibilidade**: Publicar um site via GitHub Pages dá visibilidade ao seu projeto, já que é fácil compartilhar o link e promover seu trabalho.

5. **Confiabilidade**: Como o GitHub é uma plataforma robusta e amplamente utilizada, você pode confiar na disponibilidade e estabilidade do serviço de hospedagem.

Após esta breve introdução, vamos aprender na prática como hospedar o Projeto Portfólio no GitHub Pages.

<br />

<h2>👣 Passo 01 - Checklist</h2>



Antes de iniciar o deploy, verifique os seguintes itens do seu projeto:

1. Verifique se todas as pastas e arquivos do projeto estão com os nomes escritos com letras minúsculas;
2. Verifique se as importações dos arquivos CSS e JavaScript (JS) estão com o **caminho relativo**:

```html
<!--  Link para a Folha de Estilos CSS -->
<link rel="stylesheet" href="./assets/css/styles.css">

<!-- Script JavaScript -->
<script src="./assets/js/script.js"></script>
```

3. Verifique se todas as imagens, áudios e vídeos também foram adicionados com o **caminho relativo**:

```html
<!-- Imagem com caminho Relativo -->
<img src="./assets/img/astronauta.svg" alt="Capacete de Astronauta Animado">
```

<br />

<h2>👣 Passo 02 - Publicar o Projeto no GitHub Pages</h2>



1. Atualize o Repositório do Projeto Portfólio no Github.
2. Na Página inicial do Repositório do Projeto Portfólio no Github, clique na opção **Settings**:

<div align="center"><img src="https://i.imgur.com/JEPpPtv.png" title="source: imgur.com" /></div>

3. Na Página que será aberta, no menu lateral, localizado no lado esquerdo da tela, clique na opção **Pages**:

<div align="center"><img src="https://i.imgur.com/NzMpnf3.png" title="source: imgur.com" /></div>

4. Na janela **GitHub Pages**, na opção **Branch**, clique na caixa de seleção identificada com a palavra **None**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/O6VnObQ.png" title="source: imgur.com" /></div>

5. Selecione a branch onde está armazenada a versão final do Portfólio. No exemplo abaixo está na branch **03_JS**, no seu Repositório pode estar em outra branch.

<div align="center"><img src="https://i.imgur.com/CCyZ4Jf.png" title="source: imgur.com" /></div>

6. Após escolher a branch clique no botão **Save**, para iniciar o deploy.

<div align="center"><img src="https://i.imgur.com/gjRbw10.png" title="source: imgur.com" /></div>

7. Na parte superior da tela, será exibida a mensagem de confirmação. O deploy será finalizado em alguns minutos. Aguarde a conclusão.

<div align="center"><img src="https://i.imgur.com/oPO6sfS.png" title="source: imgur.com" /></div>

8. Quando o deploy for concluído, será exibida a mensagem abaixo, contendo o endereço do deploy, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/rksMXJT.png" title="source: imgur.com" /></div>

9. Clique no botão **Visit site**, para abrir o deploy no navegador.

<div align="center"><img src="https://i.imgur.com/8YLDxIA.png" title="source: imgur.com" /></div>

10. O Projeto Portfólio será aberto no Navegador

<div align="center"><img src="https://i.imgur.com/DHO9O6h.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 03 - Reconfigurar o Formulário de Contato</h2>



Como o deploy cria um endereço WEB para acessar o Projeto Portfólio através da Internet, precisamos refazer a validação do e-mail no serviço **Form Submit**, para que o formulário de contato funcione na WEB:

<br />

> [!IMPORTANT]
>
> **Lembre-se que anteriormente, validamos o e-mail no serviço Form Submit para uso local (localhost), logo, para utilizarmos o serviço no site publicado na Internet (remoto), teremos que refazer a validação.**

<br />

1. Abra o Projeto Portfólio no Visual Studio Code
2. No arquivo **index.html**, localize o trecho de código abaixo:

<div align="center"><img src="https://i.imgur.com/RzsKV95.png" title="source: imgur.com" /></div>

3. Atualize o endereço de acesso da página **sucess.html**, substituindo o endereço local (http://localhost:5500), indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/hTIKINL.png" title="source: imgur.com" /></div>

4. Pelo **endereço do seu deploy**, que foi gerado pelo GitHub Pages, conforme indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3F2eryI.png" title="source: imgur.com" /></div>

5. O endereço remoto do seu deploy é o endereço que foi exibido quando o deploy foi concluído, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/iIiCotl.png" title="source: imgur.com" /></div>

6. Atualize o Repositório do Projeto Portfólio no GitHub e aguarde a conclusão do novo deploy, que será iniciado automaticamente.
7. Atualize o Portfólio no Navegador e faça o envio de uma mensagem pelo **Formulário de Contato**.
8. Será exibida a mensagem abaixo, solicitando a validação do e-mail:

<div align="center"><img src="https://i.imgur.com/DTCUcwj.png" title="source: imgur.com" /></div>

9. Você receberá um novo e-mail de validação, semelhante a imagem abaixo. Clique no botão **ACTIVATE FORM**, para validar o e-mail:

<div align="center"><img src="https://i.imgur.com/xlsZ5Az.png" title="source: imgur.com" /></div>

10. Você será redirecionado para uma página, semelhante a imagem abaixo, indicando que o e-mail foi validado:

<div align="center"><img src="https://i.imgur.com/sBCNJ2r.png" title="source: imgur.com" /></div>

11. Faça o envio de uma nova mensagem pelo **Formulário de Contato** e verifique:

- Se a Página **sucess.html** foi exibida corretamente;
- Se a mensagem chegou no seu e-mail.

<br />

<h2>👣 Passo 04 - Exibir o Enderelo do Deploy no Repositório</h2>



1. Volte para a Página principal do Repositório do Projeto Portfólio no GitHub e clique no ícone da engrenagem, ao lado da **Seção About** do Repositório, indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/yftbuev.png" title="source: imgur.com" /></div>

2. Na janela **Edit repository details**, na opção **Description**, escreva uma breve descrição sobre o seu Portfólio e na sequência, marque a opção **Use your GitHub Pages website**, para exibir o endereço do deploy na opção **website**:

<div align="center"><img src="https://i.imgur.com/ZfkIvRD.png" title="source: imgur.com" /></div>

3. Clique no botão **Save Changes**.
4. Observe que a **Seção About** do Repositório do Projeto Portfólio foi atualizada!

<div align="center"><img src="https://i.imgur.com/lfGdk2g.png" title="source: imgur.com" /></div>

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div> 
