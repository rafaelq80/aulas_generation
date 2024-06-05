<h1>Não consigo enviar arquivos no Github e Autenticar no Github</h1>



Ao enviar os seus arquivos para o Github (**git push**), caso você não tenha autenticado no Github durante a instalação, será exibida a janela abaixo, solicitando a autenticação no Github:

<div align="center"><img src="https://i.imgur.com/sRX8K2X.png" title="source: imgur.com" /></div>

Caso a sua conta do Github não seja reconhecida, provavelmente uma outra conta do Github está salva nas **Credenciais do Windows** e precisa ser removida.

Para verificar as Credenciais

1. Na caixa de pesquisa do Windows, localize o **Gerenciador de Credenciais**.

<div align="center"><img src="https://i.imgur.com/xfESNWM.png" title="source: imgur.com" /></div>

2. Clique no ícone abrir, para abrir o **Gerenciador de Credenciais**.

<div align="center"><img src="https://i.imgur.com/VnjJ3iR.png" title="source: imgur.com" width="80%"/></div>

3. Clique na opção **Credenciais do Windows**.

<div align="center"><img src="https://i.imgur.com/IozVuJ7.png" title="source: imgur.com" /></div>

4. Na lista **Credenciais Genéricas**, localize a Credencial do Github, como mostra a imagem abaixo e clique sobre a Credencial.

<div align="center"><img src="https://i.imgur.com/1XzsXb2.png" title="source: imgur.com" /></div>

5. Verifique se os dados da sua conta do Github estão salvos na Credencial. 

<div align="center"><img src="https://i.imgur.com/80M2O5m.png" title="source: imgur.com" /></div>

6. Se os dados salvos não forem da sua conta, clique no link **Editar**.

<div align="center"><img src="https://i.imgur.com/IhcNpTJ.png" title="source: imgur.com" /></div>

7. Altere os dados das Credenciais do Github e clique no botão **Salvar**.

<div align="center"><img src="https://i.imgur.com/PHIv7yn.png" title="source: imgur.com" /></div>

8. Experimente enviar os arquivos novamente.

9. Caso não funcione, experimente excluir a Credencial, clicando no link **Remover**.

<div align="center"><img src="https://i.imgur.com/GqL4Zpq.png" title="source: imgur.com" /></div>

10. Experimente enviar os arquivos novamente.



<br />

<h2>Autenticando com um Personal Token</h2>



Caso você não tenha encontrado as Credenciais do Github no Windows ou apareça a mensagem de autenticação do Github no Terminal e ao tentar autenticar seja exibida a mensagem abaixo:

```
Github push error. unable to read askpass & could not read Username.
```

Será necessário criar um Personal Token para autenticar no Github. Antes de criarmos o Personal Token, vamos desativar o modo SSH. No Terminal Gitbash, digite o comando abaixo:

```bash
unset SSH_ASKPASS
```

Na sequência, vamos criar o **Personal Token**:

1. Clique no seu usuário do Github (canto direito superior, na foto do seu Perfil) e na sequência clique na opção **Settings**:

<div align="center"><img src="https://i.imgur.com/xT2moJf.png" title="source: imgur.com" /></div>

2. No menu de opções do lado esquerdo da tela, clique na opção **Developer settings** (última opção):

<div align="center"><img src="https://i.imgur.com/t8wpTNx.png" title="source: imgur.com" /></div>

3. No menu de opções do lado esquerdo da tela, em **Github Apps**, clique na opção **Tokens (classic)** (última opção):

<div align="center"><img src="https://i.imgur.com/Y099zk0.png" title="source: imgur.com" /></div>

4. Será solicitada a senha do Github:

<div align="center"><img src="https://i.imgur.com/jL5qRXf.png" title="source: imgur.com" /></div>

5. Na tela **Personal access tokens (classic)**, no menu **Generate new token**, clique na opção **Generate new token (classic)**:

<div align="center"><img src="https://i.imgur.com/FDbjXhZ.png" title="source: imgur.com" /></div>

6. Na tela **New personal access token (classic)**, na opção **Note**, informe um nome para o token (github) e na opção **Expiration**, altere para **No expiration**:

<div align="center"><img src="https://i.imgur.com/yPi59nw.png" title="source: imgur.com" /></div>

7. Na opção **Select scopes**, selecione **todas as opções**:

<div align="center"><img src="https://i.imgur.com/t6MaeMc.png" title="source: imgur.com" /></div>

8. Para concluir, clique no botão **Generate token**:

<div align="center"><img src="https://i.imgur.com/R7tdyhZ.png" title="source: imgur.com" /></div>

9. Copie o token gerado:

<div align="center"><img src="https://i.imgur.com/RJW8mOk.png" title="source: imgur.com" /></div>

10. Volte para o Gitbash e envie novamente os arquivos para o Repositório Remoto
11. Será solicitado o usuário do Github.
12. Na sequência será solicitada a senha. Ao invés de digitar a sua senha, cole o **Personal Token**.
13. A sua conta no Github será registrada no seu computador e os arquivos serão enviados para o Repositório Remoto no Github.

