<h1>Guia de Facilidades - Insomnia</h1>



<h2>1. Criar Backup da Collection</h2>



1. Com a Collection aberta, clique no menu **Application 🡪 Preferences**.

<div align="center"><img src="https://imgur.com/qSU7ohx.png" title="source: imgur.com" /></div>

2. Na janela **Insomnia Preferences**, clique na guia **Data**
3. No item **Export**, clique no botão **Export the Nome da Collection**.

<div align="center"><img src="https://i.imgur.com/Jz6spLY.png" title="source: imgur.com" /></div>

4. Na janela **Export requests** serão exibidas todas a requisições armazenadas na collection selecionadas. Clique no botão **Export** para continuar

<div align="center"><img src="https://i.imgur.com/pf3b2KT.png" title="source: imgur.com" /></div>

5. Será exibida a tela para você escolher onde deseja salvar o Backup. Escolha a pasta e clique no botão **Export**

<div align="center"><img src="https://i.imgur.com/0dJZC19.png" title="source: imgur.com" /></div>

<br />

<h2>2. Restaurar Backup da Collection</h2>



1. Na tela inicial do Insomnia, clique no menu **Application 🡪 Preferences**.

<div align="center"><img src="https://imgur.com/qSU7ohx.png" title="source: imgur.com" /></div>

2. Na janela **Insomnia Preferences**, clique na guia **Data**
3. No item **Import**, clique no botão **Import to the "Personal Workspace" Project**.

<div align="center"><img src="https://imgur.com/EaFWAfv.png" title="source: imgur.com" /></div>

4. Na janela **Import to...** arraste o arquivo do Backup ou clique na área indicada na imagem abaixo para selecionar o arquivo do Backup

<div align="center"><img src="https://i.imgur.com/NMSvSKP.png" title="source: imgur.com" /></div>

5. Será exibida a janela para localizar o arquivo. Localize o arquivo do backup e clique no botão **Abrir**

<div align="center"><img src="https://i.imgur.com/u4K94vt.png" title="source: imgur.com" /></div>

6. Após abrir o arquivo, clique no botão **Scan**

<div align="center"><img src="https://i.imgur.com/7Ztfq6u.png" title="source: imgur.com" /></div>

7. Na janela **Import to...** serão exibidos os detalhes do Backup. Clique no botão **Import** para concluir o processo

<div align="center"><img src="https://i.imgur.com/2vtJMPy.png" title="source: imgur.com" /></div>



<br />

<h2>3. Automatizar Token</h2>




1. Com a aplicação Backend em execução, execute a Requisição **Autenticar Usuário**
2. Abra a Requisição **Consultar todos os Usuários**.


<div align="center"><img src="https://i.imgur.com/Veedyux.png" title="source: imgur.com" /></div>

3. Clique na Guia **Headers** da Requisição **Consultar todos os Usuários**.

<div align="center"><img src="https://i.imgur.com/VKGHZHf.png" title="source: imgur.com" /></div>

4. Localize a propriedade **Authorization**.

<div align="center"><img src="https://i.imgur.com/wIYZN9z.png" title="source: imgur.com" /></div>

5. Caso a propriedade **Authorization** esteja com um **Token**, como mostra a figura acima, apague o token.

<div align="center"><img src="https://i.imgur.com/lvA616E.png" title="source: imgur.com" /></div>

6. Caso você não tenha adicionado a propriedade **Authorization**, clique no botão **Add**:

<div align="center"><img src="https://i.imgur.com/Bu8c2lq.png" title="source: imgur.com" /></div>

<br />

> [!CAUTION]
>
> Em hipótese alguma remova ou altere qualquer propriedade pré-existente na guia **Headers**. Caso contrário, a Requisição deixará de funcionar.

<br />

7. Será criado um novo campo:

<div align="center"><img src="https://i.imgur.com/nkn1Apr.png" title="source: imgur.com" /></div>

8. No item **header**, adicione a propriedade **Authorization**.

<div align="center"><img src="https://i.imgur.com/lvA616E.png" title="source: imgur.com" /></div>

9. Digite no campo value **resp**. Observe que será aberto um menu com algumas opções:

<div align="center"><img src="https://i.imgur.com/qqxfqdn.png" title="source: imgur.com" /></div>

10. Dê um duplo clique na opção **Response => Body Attribute**

<div align="center"><img src="https://i.imgur.com/N4Y4Pme.png" title="source: imgur.com" /></div>

11. Note que a opção selecionada ficará destacada com a cor vermelha. Clique na parte vermelha.

<div align="center"><img src="https://i.imgur.com/WcfWm6Z.png" title="source: imgur.com" /></div>

12. Será aberta a janela **Edit Tag**

<div align="center"><img src="https://i.imgur.com/e7cBVjU.png" title="source: imgur.com" /></div>

13. No item **Request**, selecione a Requisição **Autenticar Usuário**

<div align="center"><img src="https://i.imgur.com/5NVq9ZF.png" title="source: imgur.com" /></div>

14. No item **Filter (JSONPath or XPath)**, digite **`$.token`**, para selecionar apenas o atributo token

<div align="center"><img src="https://i.imgur.com/keEruXB.png" title="source: imgur.com" /></div>

15. Role a tela para abaixo e observe que no item **Live Preview** será exibido o token atual gerado pela requisição **Autenticar Usuário****:

<div align="center"><img src="https://i.imgur.com/1jaJ81i.png" title="source: imgur.com" /></div>

16. Clique no botão **Done** para finalizar

<div align="center"><img src="https://i.imgur.com/MezTF5p.png" title="source: imgur.com" /></div>

17. Teste a Requisição novamente.

<br />

> [!WARNING]
>
> **Não esqueça de repetir este processo em todas as Requisições, de todos os Módulos, exceto as requisições Autenticar e Cadastrar Usuário**.

<br />

<h2>4. Automatizar URL das Requisições</h2>



1. Com a Collection aberta, clique na opção **Base Environment**.

<div align="center"><img src="https://i.imgur.com/LsNpFI5.png" title="source: imgur.com" /></div>

2. No menu que será aberto, no item **Collection Environments**, clique no lápis para criar ou editar variáveis de ambiente do Insomnia

<div align="center"><img src="https://i.imgur.com/msyQcMm.png" title="source: imgur.com" /></div>

3. Ao lado do item **Base Environment**, clique no botão **+** e crie uma nova variável chamada **render_url**. Dentro do JSON, adicione o atributo **base_url**. No valor do atributo, adicione o endereço do seu deploy. Utilize a imagem abaixo apenas como referência.

<div align="center"><img src="https://i.imgur.com/AuHfXkk.png" title="source: imgur.com" /></div>

4. Clique no botão **Close** para concluir

<br />

> [!WARNING]
>
> **Insira o endereço do seu deploy, fornecido pelo Render.**

<br />

5. Abra a pasta **Blog Pessoal - Render** e localize a requisição **Cadastrar Usuário**
6. Substitua o endereço do servidor (**http://localhost:4000**), indicado na imagem abaixo

<div align="center"><img src="https://i.imgur.com/HT9MFJe.png" title="source: imgur.com" /></div>

7. Pela variável de ambiente **`_.base_url`**, como mostra a imagem abaixo

<div align="center"><img src="https://i.imgur.com/3n0kdjm.png" title="source: imgur.com" /></div>

8. Repita o processo para todas as requisições da pasta **Blog Pessoal - Render**. As requisições da pasta **Blog Pessoal** não devem ser modificadas.

<br />
