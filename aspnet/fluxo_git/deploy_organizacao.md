<h1>Deploy do Backend no Render - Github Organization</h1>



Quando estamos trabalhando com Organizações, além de conectar o Render com a Conta do Github é necessário autorizar o acesso do Render na Organização, permitindo que o Render acesse os repositórios da Organização.
Neste material, o **[Passo 10](https://github.com/conteudoGeneration/cookbook_csharp/blob/main/04_aspnet/24.md#-passo-10---criar-o-web-service-no-render)** foi adaptado para o Deploy do Projeto Integrador via Github Organization. Substitua o Passo 10 do Guia do Deploy do Projeto Blog Pessoal pelas instruções abaixo. Os demais passos são iguais.

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="200px"/> | <p align="justify"> **ATENÇÃO:**  *Crie uma nova conta no Render utilizando o e-mail que foi criado para o projeto, ou seja, a mesma conta que o grupo utilizou para criar a conta no Github, onde foi criada a Organização*. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<h2>👣 Passo 10 - Criar o Web Service no Render a partir de uma Organização</h2> 



1. Na barra de menus principal do Render, clique no item Dashboard, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/AYQts2Z.png" title="source: imgur.com" /></div>

2. Para adicionar um novo Web Service, no Dashboard do Render, clique no botão **New +** e em seguida clique na opção **Web Service**.

<div align="center"><img src="https://i.imgur.com/FVGlwLN.png" title="source: imgur.com" /></div>

3. Na janela **Create a new Web Service**, mantenha a primeira opção selecionada **Build and deploy from a Git repository** e clique no botão **Next** para continuar.

<div align="center"><img src="https://i.imgur.com/riRmjXa.png" title="source: imgur.com" /></div>

4. No item **GitHub**, clique no link **+ Connect account**, para conectar a sua conta do Render com a sua Conta do Github.

<div align="center"><img src="https://i.imgur.com/xaffIQz.png" title="source: imgur.com" /></div>

5. Na tela, **Install Render**, clique na **Organização** que foi criada na conta do Github do Projeto Integrador (no exemplo abaixo, **Projeto-Integrador-Modelo**), como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/F1Da8Nv.png" title="source: imgur.com" /></div>

6. Na próxima tela, clique no botão **Install**, para concordar que o Render acesse a Organização no Github.

<div align="center"><img src="https://i.imgur.com/OWUK5N8.png" title="source: imgur.com" /></div>

7. Conecte o Render com o Repositório onde você enviou o **Backend do Projeto Integrador**, clicando no botão **Connect**, localizado ao lado do Repositório.

<div align="center"><img src="https://i.imgur.com/hzNpT9m.png" title="source: imgur.com" /></div>

8. Na próxima tela, informe o nome da sua aplicação na propriedade **Name** (nome do seu projeto integrador) e verifique se a propriedade **Environment** está com a opção **Docker** selecionada.

<div align="center"><img src="https://i.imgur.com/LBnrRSp.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="120px"/> | <p align="justify"> **ATENÇÃO:** O NOME DO PROJETO NÃO PODE CONTER LETRAS MAIUSCULAS, NUMEROS OU CARACTERES ESPECIAIS. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

9. Role a tela para baixo e verifique se o Plano Gratuito (**Free**) está selecionado.

<div align="center"><img src="https://i.imgur.com/7TZeGuY.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <p align="justify"> **ATENÇÃO:** *Caso seja selecionado um plano diferente, o Render exigirá o Cartão de Crédito para emitir a fatura do serviço. </p> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

Daqui em diante, siga os passos do Cookbook a partir do Passo 11.
