# Criando Perfis de Agente e Templates no Text Cortex

<br />

## 1. Criar a conta pessoal no Text Cortex



1. Acesse a página do **[Text Cortex](https://textcortex.com/pt)** e clique no link **Iniciar sessão**

![https://i.imgur.com/b0kSMhj.png](https://i.imgur.com/b0kSMhj.png)

2. Faça o login ou crie uma com sua conta Google.

![https://i.imgur.com/Qr5g1Ki.png](https://i.imgur.com/Qr5g1Ki.png)

3. Caso você esteja criando uma nova conta, personalize respondendo as perguntas abaixo:

![https://i.imgur.com/QnxozaO.png](https://i.imgur.com/QnxozaO.png)

4. Na próxima tela, clique no link **pular** para ignorar o tour na plataforma

![https://i.imgur.com/sC4U3aV.png](https://i.imgur.com/sC4U3aV.png)

5. Após efetuar o login ou criar a sua conta pessoal, você será redirecionado para a tela do chat do Text Cortex:

![https://i.imgur.com/way9p2D.png](https://i.imgur.com/way9p2D.png)

<br />

> [!WARNING]
>
> Ao criar a sua conta, você receberá **100 créditos gratuitos** para utilizar o Text Cortex, que serão consumidos de acordo com a complexidade da tarefa. Para consultar os créditos, clique no  **botão configurações**, localizado no canto esquerdo inferior. Ao clicar, será aberto o menu abaixo, indicando os créditos disponíveis, que o Text Cortex chama de **Criações**:
>
> <div align="center"><img src="https://i.imgur.com/gXVkNhF.png" alt="https://i.imgur.com/gXVkNhF.png" /></div>
>
> Ao terminar os créditos, você precisará assinar a versão Premium (paga) da ferramenta para continuar utilizando, ou obter créditos através do **Centro de Recompensas**, que pode ser acessado no menu de configurações.

<br />

## 2. Criar o Perfil de Agente (Persona)



1. Clique no botão **Perfis de Agente**, indicado na imagem abaixo, para criar um Perfil de Agente

![https://i.imgur.com/zQwoLwQ.png](https://i.imgur.com/zQwoLwQ.png)

2. Na tela **Agents**, clique no botão **+ Create**

![https://i.imgur.com/mYGSmRG.png](https://i.imgur.com/mYGSmRG.png)

3. Será exibida a janela **Perfil de agente**

<div align="center"><img src="https://i.imgur.com/sx0FMrR.png" alt="https://i.imgur.com/sx0FMrR.png" /></div>

4. Preencha as seguintes informações:

- **Imagem** - foto ou ícone para identificar visualmente o agente
- **Nome do agente** — curto, claro e objetivo
- **Descrição** — breve descrição do objetivo do agente em 1-2 frases
- **Plano de fundo** — aqui você descreverá de forma detalhada o perfil do agente: tom (formal/jovem), público, formato da resposta (bullets, exemplos de código, limite de linhas), entre outros elementos relevantes. Seja o mais específico possível.

<div align="center"><img src="https://i.imgur.com/ouhGPas.png" alt="https://i.imgur.com/ouhGPas.png" /></div>

5. Role a tela para baixo e defina as **Regras** do Agente:

- **Sempre** — são instruções que o agente deve **sempre** seguir, ou seja, as obrigações, como por exemplo: *"Basear todas as conclusões apenas nos dados fornecidos nos logs"*

<div align="center"><img src="https://i.imgur.com/0BZgdbZ.png" alt="https://i.imgur.com/0BZgdbZ.png" /></div>

- **Nunca** — São instruções que o agente **nunca** deve executar, ou seja, as proibições, como por exemplo: *"Inventar dados."*

<div align="center"><img src="https://i.imgur.com/g9X3XdZ.png" alt="https://i.imgur.com/g9X3XdZ.png" /></div>

6. Após definir as regras, clique no botão **Salvar alterações**
7. Você será redirecionado para a tela **Agents** e o seu agente estará criado

<div align="center"><img src="https://i.imgur.com/V8RHScY.png" alt="https://i.imgur.com/V8RHScY.png" /></div>

<br />

## 3. Criar as Templates



Clique no botão **Templates**, indicado na imagem abaixo, para criar uma nova Template (modelo)

![https://i.imgur.com/RRSlRMq.png](https://i.imgur.com/RRSlRMq.png)

2. Na tela **Templates**, clique no botão **+ Create**

![https://i.imgur.com/0exZaEx.png](https://i.imgur.com/0exZaEx.png)

3. Será aberta a janela **Criar Modelo Personalizado**

![https://i.imgur.com/bhJ43zK.png](https://i.imgur.com/bhJ43zK.png)

4. Preencha as seguintes informações:

- **Nome do Template** — curto, claro e objetivo
- **Descrição** — breve descrição do objetivo do modelo em 1-2 frases
- **Modelo de Prompt** - escreva o prompt que o agente deve processar e preencher com as informações obtidas após a análise dos dados. Use *placeholders* para campos variáveis, por exemplo: `[logs]`.

![https://i.imgur.com/h7BRuPv.png](https://i.imgur.com/h7BRuPv.png)

5. Role a tela para baixo e na propriedade **Acesso Geral** selecione a opção **Private** para garantir que apenas você terá acesso a esse Template e clique no botão **Criar Template**

<div align="center"><img src="https://i.imgur.com/nxRrw8m.png" alt="https://i.imgur.com/nxRrw8m.png" /></div>

6. Você será redirecionado para a tela **Templates** e a sua Template estará criada

![https://i.imgur.com/HXzcvIi.png](https://i.imgur.com/HXzcvIi.png)

7. Repita todos os passos anteriores para criar as demais templates

<br />



<br />

## 4. Executar a Template dentro do Perfil de Agente personalizado



1. Clique no botão **Nova conversa**, indicado na imagem abaixo, para criar um novo chat

![https://i.imgur.com/R99wls4.png](https://i.imgur.com/R99wls4.png)

2. Clique no botão **Agents**, indicado na imagem abaixo e selecione o Agente que você criou.

![https://i.imgur.com/BSbQC8x.png](https://i.imgur.com/BSbQC8x.png)

3. Observe que a tela do chat será modificada, exibindo os detalhes do Agente Personalizado

![https://i.imgur.com/TqDnMnW.png](https://i.imgur.com/TqDnMnW.png)

4. Clique no botão **Conhecimento**, indicado na imagem abaixo e clique no botão **Templates**.

![https://i.imgur.com/ZaOFWrk.png](https://i.imgur.com/ZaOFWrk.png)

5. Selecione uma das templates que você criou. Caso a Template não esteja visível na lista, clique no botão **Navegar pelos templates** e localize a Template desejada.

<div align="center"><img src="https://i.imgur.com/nsZ31Nc.png" alt="https://i.imgur.com/nsZ31Nc.png" /></div>

6. Observe que a Template selecionada foi anexada no chat

![https://i.imgur.com/tA58HPx.png](https://i.imgur.com/tA58HPx.png)

7. Digite um texto de teste (por exemplo: *Executar*) apenas se os dados forem enviados em um arquivo anexo. Caso contrário, cole diretamente o conteúdo a ser analisado. Depois, clique no botão roxo com a seta, conforme mostrado abaixo:

![https://i.imgur.com/qLNUKBK.png](https://i.imgur.com/qLNUKBK.png)

8. A Template continuará aguardando até que os dados sejam enviados.

![https://i.imgur.com/PLEJn3y.png](https://i.imgur.com/PLEJn3y.png)

9. Clique no botão **Anexar arquivos**, indicado na imagem abaixo e clique no botão **Carregar do computador**.

![https://i.imgur.com/LUEvB4K.png](https://i.imgur.com/LUEvB4K.png)

10. Selecione o arquivo desejado e clique no botão **Abrir**

<div align="center"><img src="https://i.imgur.com/Z8X9UIo.png" alt="https://i.imgur.com/Z8X9UIo.png" /></div>

11. Para fazer o upload do arquivo, clique no botão **Carregar**

<div align="center"><img src="https://i.imgur.com/FrdhDff.png" alt="https://i.imgur.com/FrdhDff.png" /></div>

12. O arquivo carregado será anexado no chat

![https://i.imgur.com/nSWc0Tc.png](https://i.imgur.com/nSWc0Tc.png)

13. Digite um texto indicando que o arquivo anexo contém os dados que serão analisados e clique no botão roxo com a seta, conforme indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/whzFFkh.png" alt="https://i.imgur.com/whzFFkh.png" /></div>

14. A Template processará os dados do arquivo anexo e exibirá na tela o resultado.

![https://i.imgur.com/3xRmxYL.png](https://i.imgur.com/3xRmxYL.png)

15. Remova o arquivo anexo e repita os passos 9 a 14 para processar os demais arquivos usando a mesma Template
16. Após concluir uma Template, repita o processo para os demais arquivos utilizando as outras Templates que você criou.

> [!TIP]
>
> Ao trocar de Template, como os arquivos já foram carregados na execução da primeira Template, você pode reutilizá-los sem precisar refazer o upload (passos 9 a 11).
>
> Clique no botão **Conhecimento**, indicado na imagem abaixo e clique no botão **Arquivos**.
>
> ![https://i.imgur.com/lWL4FBA.png](https://i.imgur.com/lWL4FBA.png)
>
> Observe que todos os arquivos que você carregou, estarão disponíveis para uso. Para anexar no chat, basta selecionar o arquivo.

