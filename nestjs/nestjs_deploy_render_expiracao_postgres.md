<h1>Deploy no Render - Expiração do Banco de dados</h1>



O Serviço de Hospedagem Gratuito Render modificou a sua política para hospedagem de Webservices com Banco de dados. Até o inicio de 2024 o Banco de dados PostgreSQL se mantinha ativo por 90 dias. Com as novas regras, **o Banco de dados PostgreSQL se mantém ativo por apenas 30 dias**.

Ao completar os 30 dias, você será notificado por e-mail da expiração do Banco de dados e será indicado a aquisição de um plano pago. Entretanto, ainda é possível renovar o uso do Banco de dados por mais 30 dias excluindo o banco de dados expirado e criando um novo. Neste guia mostraremos com fazer:

<br />

<h2>👣 Passo 01 - Excluir o Banco de dados Expirado</h2>



1. Acesse o site do Render: **https://render.com/**
2. Acesse o **Dashboard** através da sua conta do **Github**
3. Clique no Banco de dados, para acessar as configurações

<div align="center"><img src="https://i.imgur.com/LaaaY7l.png" title="source: imgur.com" /></div>

4. Role a tela de configurações até o final e localize o botão **Delete Database**

<div align="center"><img src="https://i.imgur.com/9ae5HI3.png" title="source: imgur.com" /></div>

5. Clique no botão  **Delete Database**. Será aberta a janela abaixo:

<div align="center"><img src="https://i.imgur.com/nFfrNU0.png" title="source: imgur.com" /></div>

6. Observe que será solicitado que você digite o texto em vermelho no input, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/3ynnvxF.png" title="source: imgur.com" /></div>

7. Copie o texto em vermelho, cole dentro do input, como mostra a imagem abaixo e clique no botão **Delete Database** para concluir.

<div align="center"><img src="https://i.imgur.com/ae1xLRH.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 02 - Criar um novo Banco de dados</h2>



1. Para adicionar um novo Banco de dados, no Dashboard do Render, clique no botão **New +** e em seguida clique na opção **PostgreSQL**.

<div align="center"><img src="https://i.imgur.com/MbMjaSK.png" title="source: imgur.com" /></div>

2. Na próxima tela, informe o nome do Banco de dados na propriedade **Name**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/0LCVlTo.png" title="source: imgur.com" /></div>

3. Role a tela para baixo e verifique se o Plano Gratuito (**Free**) está selecionado e na sequência, clique no botão **Create Database**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/IoFuYXl.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <p align="justify"> **ATENÇÃO:** *Caso seja selecionado um plano diferente, o Render exigirá o Cartão de Crédito para emitir a fatura do serviço. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

4. Na próxima tela, aguarde até que o **Status** esteja **Available**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Aq2bsDP.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 03 - Configurar o novo Banco de dados no Webservice</h2>



1. Role a tela para baixo e localize o item: **External Database URL**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/T9TXAWz.png" title="source: imgur.com" /></div>

2. Clique no botão **copiar**, conforme indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/fLcSTa6.png" title="source: imgur.com" /></div>

3. Abra um arquivo do **Bloco de Notas** e cole esta **URL (Endereço do Banco de dados)** no arquivo, como mostra a imagem abaixo. Nós utilizaremos este endereço no próximo passo.

<div align="center"><img src="https://i.imgur.com/su4ZN45.png" title="source: imgur.com" /></div>

4. No arquivo do Bloco de Notas, onde copiamos a URL do Banco de dados, acrescente depois do **.com**, o numero da porta de conexão com o Banco de dados PostgreSQL **:5432**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/4JIRm3p.png" title="source: imgur.com" /></div>

5. Volte para o **Dashboard** e clique no **Webservice** que será atualizado:

<div align="center"><img src="https://i.imgur.com/12iPIe3.png" title="source: imgur.com" /></div>

6. Será aberta a janela abaixo:

<div align="center"><img src="https://i.imgur.com/2QD5ePD.png" title="source: imgur.com" /></div>

7. Clique na opção **Environment**

<div align="center"><img src="https://i.imgur.com/JXnUiDl.png" title="source: imgur.com" /></div>

8. Na Opção **Environment Variables**, no item **DATABASE_URL**, substitua o valor atual da variável pela nova string de conexão, gerada pelo novo Banco de dados, salvo anteriormente no arquivo do Bloco de Notas:

<div align="center"><img src="https://i.imgur.com/y4v0yW3.png" title="source: imgur.com" /></div>

9. Clique no botão **Save Changes** e aguarde a conclusão do novo Deploy.
10. Ao finalizar o Deploy, teste a aplicação.
