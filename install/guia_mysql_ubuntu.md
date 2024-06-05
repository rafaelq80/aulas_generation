<h1>Guia de Instalação do MySQL for Linux Ubuntu Desktop</h1>

<br />

Este guia demonstrará como instalar o MySQL Server e o MySQL Workbench no **Ubuntu Linux**, uma das Distribuições Linux para Desktop mais utilizadas no Mercado. Em outras Distribuições Linux, o processo de instalação é muito semelhante.

Faremos todo o processo de instalação via Terminal, porque todas as Distribuições Linux possuem o Terminal.

<br />

<h2>Passo 01 - Instalar o MySQL Server</h2>



1. Na tela inicial do **Linux Ubuntu Desktop**, no **Lançador** (Barra de Programas localizada no lado esquerdo da tela), clique no ícone <img src="https://i.imgur.com/d7RvmeQ.png" title="source: imgur.com" width="4%"/> **Mostrar Aplicativos**:

<div align="center"><img src="https://i.imgur.com/lSJKAEj.png" title="source: imgur.com" /></div>

2. Na Janela de Aplicativos, vamos abrir o **Terminal do Linux**, clicando no ícone do **Terminal**:

<div align="center"><img src="https://i.imgur.com/hjQraUd.png" title="source: imgur.com" /></div>

<br />

> [!TIP]
>
> **A forma de abrir o Terminal do Linux pode ser diferente, dependendo da Distribuição Linux e/ou Interface Gráfica instalada.**

<br />

3. Será aberta a Janela do **Terminal Linux**:

<div align="center"><img src="https://i.imgur.com/zpXNVRu.png" title="source: imgur.com" /></div>

4. Vamos atualizar a Lista de Repositórios e Pacotes disponíveis para instalação, através do comando abaixo:

```bash
sudo apt update
```

5. Será solicitado a senha do usuário:

<div align="center"><img src="https://i.imgur.com/h1gkOBR.png" title="source: imgur.com" /></div>

6. Depois de atualizar a Lista de Repositórios e Pacotes disponíveis para instalação, vamos instalar o **MySQL Server** através do comando abaixo:

```bash
sudo apt install mysql-server
```

7. O Pacote do **MySQL Server** será localizado e o **APT** perguntará se você deseja instalar o MySQL Server. Digite **s** (Sim) para continuar.

<div align="center"><img src="https://i.imgur.com/qj4r2Ir.png" title="source: imgur.com" /></div>

8. Quando a instalação for concluída, digite o comando abaixo para saber se a instalação foi bem sucedida:

```bash
mysqld --version
```

9. Será exibida a mensagem abaixo, informando a versão do MySQL Server que foi instalada:

<div align="center"><img src="https://i.imgur.com/bqjIrNb.png" title="source: imgur.com" /></div>

<br />

> [!IMPORTANT]
>
> **A versão instalada pode ser diferente da versão exibida na imagem acima.**

<br />

<h2>Passo 02 - Configurar o MySQL Server</h2>



1. Vamos configurar o **MySQL Server** através do comando abaixo:

```bash
sudo mysql_secure_installation
```

2. O **Assistente de Configuração do MySQL Server** fará algumas perguntas. A primeira pergunta será se você deseja habilitar senha para os usuários do MySQL Server. Pressione a tecla **y** (Yes) para  habilitar senha.

<div align="center"><img src="https://i.imgur.com/FIyUeEh.png" title="source: imgur.com" /></div>

3. A segunda pergunta será o nível de segurança da senha dos usuários do MySQL Server. Como estamos em ambiente de desenvolvimento local, vamos utilizar a a opção **0 - baixo**. Pressione a tecla **0**.

<div align="center"><img src="https://i.imgur.com/dwb8C76.png" title="source: imgur.com" /></div>

<br />

> [!TIP]
>
> **Se estivéssemos configurando o MySQL Server em um Servidor de Produção, utilizaríamos a opção 2, que exige uma senha mais robusta.**

<br />

4. Neste ponto da Configuração, dependendo da versão do MySQL Server, o **Assistente de Configuração do MySQL Server** pode solicitar que você digite uma senha para o usuário **root**. Recomendamos utilizar a senha padrão **rootroot**. Caso não seja solicitado, faremos a configuração da senha no próximo Passo.

<div align="center"><img src="https://i.imgur.com/GDgWMu4.png" title="source: imgur.com" /></div>

5. A terceira pergunta será se você deseja remover todos os usuários anônimos do MySQL Server. Pressione a tecla **y** (Yes).

<div align="center"><img src="https://i.imgur.com/PXyazEk.png" title="source: imgur.com" /></div>

6. A próxima pergunta será se você deseja proibir que o usuário root faça acesso remoto ao MySQL Server. Pressione a tecla **y** (Yes).

<div align="center"><img src="https://i.imgur.com/1sDZc7k.png" title="source: imgur.com" /></div>

7. A próxima pergunta será se você deseja remover todos os Bancos de teste do MySQL Server. Pressione a tecla **y** (Yes).

<div align="center"><img src="https://i.imgur.com/RrtMiBh.png" title="source: imgur.com" /></div>

8. A próxima pergunta será se você deseja remover todos os direitos de acesso, de todos os usuários, aos Bancos de teste do MySQL Server, que foram removidos. Pressione a tecla **y** (Yes).

<div align="center"><img src="https://i.imgur.com/u4hjeVM.png" title="source: imgur.com" /></div>

9. Se todo o processo foi bem sucedido, você receberá a mensagem abaixo indicando que todas as operação foram concluídas.

<div align="center"><img src="https://i.imgur.com/LnEQBFV.png" title="source: imgur.com" /></div>

10. Digite o comando abaixo para checar se o MYSQL está sendo executado:

```bash
sudo systemctl status mysql
```

11. Será solicitado a senha do usuário:

<div align="center"><img src="https://i.imgur.com/h1gkOBR.png" title="source: imgur.com" /></div>

12. Observe que será exibido o Status do MySQL Server. Observe que na propriedade **Active**, será exibida uma mensagem na cor verde, indicando que o MySQL está ativo e em execução.

<div align="center"><img src="https://i.imgur.com/Z1XqltH.png" title="source: imgur.com" /></div>

13. Para sair da tela de Status do MySQL Server e voltar para o Prompt do Terminal, digite a combinação de teclas **CTRL + C**.

<br />

<h2>Passo 03 - Configurar a senha do usuário root</h2>



Caso não tenha sido solicitado a digitação da senha do usuário root, neste passo vamos configurar a senha do usuário root:

1. Vamos acessar o **MySQL Server** através do comando abaixo:

```bash
sudo mysql -u root
```

2. Será aberto o **Prompt de comando do Terminal do MySQL Server**.

<div align="center"><img src="https://i.imgur.com/N4A0nZu.png" title="source: imgur.com" /></div>

3. Para adicionar uma senha para o usuário root, digite o comando abaixo:

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'rootroot';
```

*Observe que utilizamos a senha padrão rootroot*

4. Será exibida a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/4f9I8oT.png" title="source: imgur.com" /></div>

5. Para confirmar a senha adicionada, utilize o comando abaixo, para atualizar os direitos de acesso:

```sql
FLUSH PRIVILEGES;
```

6. Será exibida a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/4f9I8oT.png" title="source: imgur.com" /></div>

7. Digite o comando abaixo para sair do **Prompt de comando do Terminal do MySQL Server**:

```bash
exit
```

8. Vamos checar se a senha está funcionando. Utilize o comando abaixo para acessar o **Prompt de comando do Terminal do MySQL Server**. 


```bash
sudo mysql -u root -p
```

*Observe que desta vez adicionamos no final do comando a opção **-p** (password), que exigirá que o usuário digite a senha. Caso a opção **-p** não seja adicionada, o MySQL Server não permitirá o acesso.*

9. Digite a senha do usuário root:

<div align="center"><img src="https://i.imgur.com/dqzMH1x.png" title="source: imgur.com" /></div>

10. Será aberto o **Prompt de comando do Terminal do MySQL Server**.

<div align="center"><img src="https://i.imgur.com/N4A0nZu.png" title="source: imgur.com" /></div>

11. Digite o comando abaixo para sair do **Prompt de comando do Terminal do MySQL Server**:

```bash
exit
```

<br />

<h2>Passo 04 - Instalar o MySQL Workbench</h2>



Para finalizarmos, vamos instalar o **MySQL Workbench**, a Interface Gráfica Oficial do MySQL Server:

1. Para instalar o **MySQL Workbench**, utilize o comando abaixo:

```bash
sudo snap install mysql-workbench-community
```

2. Aguarde a conclusão da instalação

<div align="center"><img src="https://i.imgur.com/P7jErAe.png" title="source: imgur.com" /></div>

3. Ao concluir a instalação, será exibida a mensagem abaixo:

<div align="center"><img src="https://i.imgur.com/Px7tY1a.png" title="source: imgur.com" /></div>

4. Feche o Terminal e volte para a Janela de Aplicativos.

<div align="center"><img src="https://i.imgur.com/tSN0mfT.png" title="source: imgur.com" /></div>

5. Na caixa de pesquisas, localize o **MySQL Workbench**:

<div align="center"><img src="https://i.imgur.com/PMVZ1RV.png" title="source: imgur.com" /></div>

6. Clique no ícone do **MySQL Workbench** para abrir o aplicativo:

<div align="center"><img src="https://i.imgur.com/BnN2UFM.png" title="source: imgur.com" /></div>

7. Será aberta a tela inicial do **MySQL Workbench**:

<div align="center"><img src="https://i.imgur.com/XpHr10t.png" title="source: imgur.com" /></div>

<br />

<h2>Passo 05 - Testar o MySQL Workbench</h2>



1. Na tela inicial do **MySQL Workbench**, dê um duplo clique sobre a conexão **Local instance 3306** (Conexão local), como mostra a figura abaixo, para efetuar a conexão com o MySQL Server.

<div align="center"><img src="https://i.imgur.com/0XDHVny.png" title="source: imgur.com" /></div>

2. Caso seja solicitada a senha do usuário root, como mostra a figura abaixo, digite a senha e marque a opção: **Save password in keychain**, para gravar a senha e não solicitar novamente.

<div align="center"><img src="https://i.imgur.com/GZLs6IK.png" title="source: imgur.com" /></div>

3. Será aberta a janela do Editor de Consultas do **MySQL Workbench**. Nesta janela iremos criar e interagir com os Banco de dados do MySQL Server.

<div align="center"><img src="https://i.imgur.com/aomE0yD.png" title="source: imgur.com" /></div>

4. Para testar o MySQL Server, digite o comando **`select @@version`** na janela Query 1, como mostra a imagem abaixo. 

<div align="center"><img src="https://i.imgur.com/WCFcis8.png" title="source: imgur.com" /></div>

5. Em seguida, clique no ícone [![source: imgur.com](https://camo.githubusercontent.com/59475599d52166e5fd84347f571d0b221dba1714ed48e93acafb4a1a43b95990/68747470733a2f2f692e696d6775722e636f6d2f33426c333963612e706e67)](https://camo.githubusercontent.com/59475599d52166e5fd84347f571d0b221dba1714ed48e93acafb4a1a43b95990/68747470733a2f2f692e696d6775722e636f6d2f33426c333963612e706e67) para executar a instrução. Será exibida a versão do MySQL que está  instalada no seu computador, como mostra a imagem abaixo (marcado em  vermelho).

<div align="center"><img src="https://i.imgur.com/4eBylzF.png" title="source: imgur.com" /></div>

