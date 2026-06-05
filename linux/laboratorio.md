# Laboratório Prático de Linux com Git Bash

---

## Introdução

A interface de linha de comando (CLI - Command Line Interface) é uma das ferramentas mais importantes para profissionais de tecnologia. Grande parte dos servidores, ambientes de nuvem, containers, pipelines de integração contínua (CI/CD) e sistemas Linux são administrados por meio de comandos executados em um terminal.

Neste laboratório você aprenderá os principais comandos de navegação, manipulação de arquivos e diretórios, busca de informações, compactação de arquivos e conceitos básicos de permissões.

Todas as atividades serão realizadas dentro de uma pasta específica chamada `aula_linux`, evitando alterações em outras áreas do sistema operacional.

---

## Objetivos de Aprendizagem

Ao final deste laboratório você será capaz de:

- Navegar entre diretórios utilizando comandos Linux.
- Criar e organizar estruturas de pastas.
- Criar, visualizar, copiar, mover e excluir arquivos.
- Utilizar comandos de busca de arquivos e conteúdos.
- Compreender diferenças entre comandos de remoção de diretórios.
- Interpretar caminhos absolutos e relativos.
- Visualizar estruturas de diretórios.
- Conhecer conceitos básicos de permissões Linux.

---

## Pré-requisitos

- Windows com Git Bash instalado.
- Conhecimentos básicos de uso do teclado e terminal.

---

## Tempo Estimado

60 minutos

---

## Cenário do Laboratório

Você foi contratado para auxiliar na organização de um projeto de software.

Sua missão será criar uma estrutura de diretórios, gerenciar documentos, organizar códigos-fonte e gerar um backup para entrega ao time de desenvolvimento.

------

## Tarefa 01 – Abrir o Git Bash

1. Clique no botão **Iniciar** e igite **Git Bash** na pesquisa.

![](https://i.imgur.com/t8uLd8H.png)

2. Clique em **Git Bash** para abrir o terminal. 

![](https://i.imgur.com/spmcFDn.png)

3. Será aberta a janela abaixo:

![](https://i.imgur.com/TEuYqbG.png)

> [!TIP]
>
> Caso o **Git Bash** não esteja instalado ou não esteja disponível no seu computador, consulte o **Guia de Instalação do Git** e realize a instalação antes de prosseguir com as atividades deste laboratório.
>
> Após a instalação, abra o Git Bash e confirme que ele está funcionando corretamente antes de continuar.

---

## Tarefa 02 – Conhecendo o Ambiente

Nesta tarefa vamos criar o ambiente inicial do laboratório e acessar a pasta de trabalho.

1. Descubra em qual diretório (pasta) você se encontra neste momento

```bash
pwd
```

2. Observe o caminho exibido.

```bash
/c/Users/rafael
```

> [!NOTE]
>
> O caminho exibido no terminal indica a pasta atual em que você está trabalhando. Por padrão, ao abrir o Git Bash, você será direcionado para a pasta pessoal (**Home Directory**) do seu usuário.
>
> Por exemplo, se o nome do seu usuário no Windows for `pedro`, o caminho exibido será semelhante a:
>
> ```bash
> /c/Users/pedro
> ```
>
> No Git Bash, a unidade `C:` do Windows é representada como `/c`, seguindo a convenção de caminhos utilizada pelos sistemas Unix/Linux.

<br />

> [!WARNING]
>
> Embora o Git Bash utilize uma sintaxe semelhante à do Linux, ele está sendo executado sobre o Windows. Por esse motivo, alguns caminhos diferem dos encontrados em uma distribuição Linux.
>
> Em um sistema Linux, a pasta pessoal do usuário `pedro`, por exemplo, seria representada por:
>
> ```bash
> /home/pedro
> ```
>
> Já no Git Bash executado no Windows, o equivalente seria:
>
> ```bash
> /c/Users/pedro
> ```
>
> Essa diferença ocorre porque o Linux e o Windows utilizam estruturas de diretórios distintas para organizar seus arquivos e usuários.

3. Liste todos os arquivos da pasta atual

```bash
ls
```

4. Liste todos os arquivos da pasta atual, com detalhes (permissões, tamanho, data de criação, dono, entre outros)

```bash
ls -l
```

5. Liste todos os arquivos da pasta atual, incluindo os arquivos ocultos

```bash
ls -a
```

> [!NOTE]
>
> Um **arquivo oculto** é um arquivo configurado para não ser exibido normalmente nas listagens padrão de pastas e diretórios do sistema operacional. 
>
> Esse tipo de arquivo é geralmente utilizado para armazenar configurações, preferências, informações de sistema ou dados necessários para o funcionamento de aplicações e do próprio sistema operacional, evitando que sejam alterados ou excluídos acidentalmente pelos usuários. 
>
> - No Linux e macOS, arquivos ocultos normalmente possuem um ponto (`.`) no início do nome, como `.bashrc`
> - No Windows eles recebem o atributo de oculto, podendo ser visualizados ao habilitar a exibição de arquivos ocultos nas configurações do Explorador de Arquivos.

6. Crie a pasta principal do laboratório, chamada `aula_linux`, dentro da pasta do usuário

```bash
mkdir aula_linux
```

7. Acesse a pasta `aula_linux`

```bash
cd aula_linux
```

8. Confirme a localização atual

```bash
pwd
```

9. Você deverá estar dentro da pasta

```bash
aula_linux
```

10. Crie a estrutura inicial de pastas

```bash
mkdir documentos codigos backups imagens
```

11. Para validar a criação execute:

```bash
ls
```

12. Resultado esperado:

```bash
backups/
codigos/
documentos/
imagens/
```

---

## Tarefa 03 - Navegação entre diretórios

Nesta tarefa vamos praticar a navegação pela estrutura de pastas criada.

1. Acesse a pasta documentos

```bash
cd documentos
```

2. Para validar execute:

```bash
pwd
```

3. Retorne para a pasta anterior

```bash
cd ..
```

4. Para validar execute:

```bash
pwd
```

5. Acesse a pasta codigos

```bash
cd codigos
```

6. Retorne para a pasta anterior utilizando o parâmetro `-` no comando `cd`

```bash
cd -
```

7. Para validar execute:

```bash
pwd
```

> [!NOTE]
>
> O comando `cd -` retorna para o última pasta acessado.

8. Acesse diretamente a pasta do usuário

```bash
cd ~
```

9. Para validar execute:

```bash
pwd
```

10. Retorne para a pasta do laboratório

```bash
cd ~/aula_linux
```

11. Para validar execute:

```bash
pwd
```

---

## Tarefa 04 - Criar os arquivos do projeto

Nesta tarefa vamos criar os arquivos utilizados pelo projeto.

1. Crie o arquivo `README.md`

```bash
touch README.md
```

2. Para validar execute:

```bash
ls
```

3. Crie os arquivos `requisitos.md`, `manual.md` e `arquitetura.md` dentro da pasta documentos

```bash
touch documentos/requisitos.md
touch documentos/manual.md
touch documentos/arquitetura.md
```

4. Para validar execute:

```bash
ls documentos
```

5. Crie os arquivos `app.js` e `config.js` dentro da pasta codigos

```bash
touch codigos/app.js codigos/config.js
```

6. Para validar execute:

```bash
ls codigos
```

---

## Tarefa 05 - Adicionar conteúdo aos arquivos

Nesta tarefa vamos adicionar conteúdo aos arquivos criados.

1. Adicione conteúdo ao `README.md`

```bash
echo "Projeto Linux para Desenvolvedores" > README.md
```

> [!NOTE]
>
> Os operadores `>`, `>>`, `<` e `<<` são utilizados para **redirecionar entradas e saídas** de comandos no terminal.
>
> * **`>`**: redireciona a saída de um comando para um arquivo, **substituindo** todo o conteúdo existente.
>
>   ```bash
>   echo "Olá" > arquivo.txt
>   ```
>
> * **`>>`**: redireciona a saída de um comando para um arquivo, **adicionando** o conteúdo ao final do arquivo sem apagar o que já existe.
>
>   ```bash
>   echo "Novo texto" >> arquivo.txt
>   ```
>
> * Em resumo, os operadores `>` e `>>` trabalham com a **saída (output)** dos comandos.
>
> 


2. Para validar execute:

```bash
cat README.md
```

3. Adicione conteúdo ao arquivo `requisitos.md`

```bash
echo "Cadastro de usuários" > documentos/requisitos.md
```

4. Para validar execute:

```bash
cat documentos/requisitos.md
```

5. Adicione conteúdo ao arquivo `app.js`

```bash
echo "console.log('Aplicacao iniciada');" > codigos/app.js
```

6. Para validar execute:

```bash
cat codigos/app.js
```

---

## Tarefa 06 - Copiar, mover e renomear arquivos 

Nesta tarefa vamos organizar os arquivos do projeto.

1. Copie o arquivo `README.md` para a pasta documentos

```bash
cp README.md documentos/
```

2. Para validar execute:

```bash
ls documentos
```

3. Mova o arquivo `requisitos.md` para a pasta codigos

```bash
mv documentos/requisitos.md codigos/
```

4. Para validar execute:

```bash
ls codigos
```

5. Resultado esperado

```bash
app.js  
config.js  
requisitos.md
```

6. Renomeie o arquivo `app.js` para `index.js`

```bash
mv codigos/app.js codigos/index.js
```

7. Para validar execute:

```bash
ls codigos
```

8. Resultado esperado:

```bash
config.js
index.js
requisitos.md
```

> [!NOTE]
>
> O comando `mv` é utilizado tanto para **mover** quanto para **renomear** arquivos e pastas. 
>
> Quando a origem e o destino estão no mesmo local, o comando apenas altera o nome do arquivo ou da pasta.

---

## Tarefa 07 - Renomear e mover pastas

Nesta tarefa vamos organizar as pastas do projeto.

1. Renomeie a pasta `imagens` para `assets`:

```bash
mv imagens assets
```

2. Para validar execute:

```bash
ls
```

3. Resultado esperado:

```bash
assets/      
backups/  
codigos/ 
documentos/
README.md
```

4. Crie a pasta  `img`, dentro da pasta `aula_linux`

```bash
mkdir img
```

5. Acesse a pasta `img`

```bash
cd img
```

6. Faça o download da imagem disponível em: `https://i.imgur.com/10TBmwA.png`

```bash
curl -L https://i.imgur.com/10TBmwA.png -o imagem.jpg
```

> [!NOTE]
>
> O comando `curl` (*Client URL*) é uma ferramenta de linha de comando, amplamente utilizada no universo Linux para transferir arquivos entre um computador e servidores na internet. 
>
> **Exemplo:**
>
> ```bash
> curl -L https://i.imgur.com/abc123.jpg -o imagem.jpg
> ```
>
> Neste comando:
>
> - **`-L`**: segue redirecionamentos automaticamente. Alguns servidores redirecionam a requisição para outro endereço antes de disponibilizar o arquivo, e essa opção garante que o download seja concluído corretamente.
> - **`https://i.imgur.com/abc123.jpg`**: URL direta do recurso que será baixado. Neste exemplo, trata-se de uma imagem hospedada no Imgur.
> - **`-o imagem.jpg`**: define o nome do arquivo que será salvo localmente. Caso o arquivo já exista, ele será sobrescrito.

7. Para validar execute:

```bash
explorer imagem.jpg
```

8. A imagem será aberta no editor de imagens padrão do Windows

![](https://i.imgur.com/10TBmwA.png)

> [!TIP]
>
> O comando `explorer` é bastante útil no Git Bash porque permite integrar facilmente comandos Linux com aplicativos do Windows. 
>
> Além de imagens, ele também pode ser usado para abrir arquivos PDF, documentos, páginas HTML e diretórios.

9. Retorne para a pasta do laboratório

```bash
cd ~/aula_linux
```

10. Mova a pasta `img` para dentro da pasta `assets`

```bash
mv img assets
```

> [!IMPORTANT]
>
> O comando `mv` atua sobre a pasta inteira. Independentemente da quantidade de arquivos e subdiretórios existentes dentro dela, todo o conteúdo será movido ou renomeado juntamente com o diretório principal. A única diferença é se o destino já existe (movimentação), se não existe (renomeação).

11. Para validar execute:

```bash
cmd //c tree //F
```

12. Resultado esperado:

```bash
Listagem de caminhos de pasta
O número de série do volume é F484-7E2A
C:.
│   README.md
│
├───assets
│   └───img
│           imagem.jpg
│
├───backups
├───codigos
│       config.js
│       index.js
│       requisitos.md
│
└───documentos
        arquitetura.md
        manual.md
        README.md
```

> Observe na árvore acima que a pasta `img` e todo o seu conteúdo foi movido para dentro da pasta `assets`.

> [!WARNING]
>
> O comando `cmd //c tree` utiliza o utilitário **Tree** do Windows para exibir a estrutura hierárquica de diretórios da pasta atual em formato de árvore.
>
> ```bash
> cmd //c tree
> ```
>
> Para exibir também os arquivos contidos em cada diretório, utilize a opção `//F`:
>
> ```bash
> cmd //c tree //F
> ```
>
> Nesse caso, além das pastas, todos os arquivos serão listados dentro da estrutura apresentada.
>
> Em sistemas Linux, a visualização da árvore de diretórios é realizada por meio do comando `tree`:
>
> ```bash
> tree
> ```
>
> Para exibir também os arquivos, normalmente utiliza-se:
>
> ```bash
> tree -a
> ```
>
> A representação em árvore facilita a compreensão da organização de diretórios e arquivos, sendo muito utilizada para documentar estruturas de projetos, analisar sistemas de arquivos e verificar rapidamente o conteúdo de uma pasta.

---

## Tarefa 08 - Buscar arquivos e conteúdos

Nesta tarefa vamos localizar arquivos e pesquisar conteúdos.

1. Localize todos os arquivos `.js`

```bash
find . -name "*.js"
```

2. Localize todos os arquivos `.md`

```bash
find . -name "*.md"
```

3. Pesquise a palavra Projeto

```bash
grep -R "Projeto" .
```

> [!NOTE]
>
> Caso nenhum resultado seja retornado, verifique se o conteúdo foi adicionado corretamente ao arquivo README.md.

4. Pesquise a palavra Cadastro

```bash
grep -R "Cadastro" .
```

---

## Tarefa 09 - Utilizar opções avançadas do comando find

Nesta tarefa vamos utilizar filtros adicionais de busca.

1. Liste apenas diretórios

```bash
find . -type d
```

2. Liste apenas arquivos

```bash
find . -type f
```

3. Localize arquivos iniciados por "`a`"

```bash
find . -name "a*"
```

4. Localize arquivos terminados em "`.jpg`"

```bash
find . -name "*.jpg"
```

5. Localize arquivos contendo a palavra "`config`"

```bash
find . -name "*config*"
```

> [!TIP]
>
> Em sistemas Linux, o `.` representa a pasta atual, enquanto o `/` representa a raiz do sistema de arquivos, sendo o ponto de partida para todos os demais diretórios. Por isso, o comando `find /` realiza a busca em todo o sistema. 
>
> **Exemplo - Buscar em todo o sistema**
>
> ```bash
> find / -name "*.jpg"
> ```
>
> Já no Git Bash, os discos do Windows são representados como diretórios (`/c`, `/d`, `/e`, etc.), permitindo que as buscas sejam realizadas em uma unidade específica.
>
> **Exemplo - Buscar em toda a unidade C:**
>
> ```bash
> find /c -name "*.jpg"
> ```

---

## Tarefa 10 - Exclusão de arquivos e pastas

Nesta tarefa vamos utilizar os comandos de exclusão de arquivos e pastas.

> [!CAUTION]
>
> Os comandos de exclusão do Linux removem arquivos e diretórios de forma permanente. Diferentemente da exclusão realizada pelo Explorador de Arquivos do Windows, os itens removidos por esses comandos **não são enviados para a Lixeira**.
>
> Antes de executar qualquer comando de exclusão, verifique cuidadosamente o nome e o caminho do arquivo ou diretório que será excluído. Uma vez concluída a operação, a recuperação dos dados pode ser difícil ou até impossível.

1. Exclua o arquivo `README.md` da pasta documentos

```bash
rm documentos/README.md
```

2. Para validar execute:

```bash
ls documentos
```

3. Exclua a pasta backups e todo o seu conteúdo

```bash
rmdir backups
```

4. Para validar execute:

```bash
ls
```

5. Exclua a pasta assets e todo o seu conteúdo

```bash
rmdir assets
```

6. Será exibida a mensagem de erro:

```bash
rmdir: failed to remove 'assets': Directory not empty
```


> [!WARNING]
>
> O comando `rmdir` remove apenas diretórios vazios.
>
> Para remover diretórios com arquivos e pastas permanentemente sem solicitar confirmação, utilize o comando `rm -rf`.

7. Exclua a pasta assets e todo o seu conteúdo com o comando `rm -rf`

```bash
rm -rf assets
```

8. Para validar execute:

```bash
ls
```

---

## Tarefa 11 - Comandos úteis

Nesta tarefa vamos testar alguns comandos úteis.

1. Limpar a tela

```bash
clear
```

2. Ver o histórico de comandos do terminal

```bash
history
```

3. Salve o histórico de comandos do terminal

```bash
history > historico_comandos.txt
```

4. Visualize a data e hora do sistema

```bash
date
```

5. Identifique o usuário autenticado

```bash
whoami
```

---

## Desafio Final

Nesta atividade você deverá criar uma nova estrutura sem seguir um roteiro detalhado.

1. Crie a estrutura de pastas abaixo

```bash
projeto_final
├── backend
├── frontend
├── banco
└── documentacao
```

2. Crie os arquivos abaixo

```bash
backend/server.js
frontend/index.html
banco/script.sql
documentacao/README.md
```

3. Adicione conteúdo aos arquivos criados, através do comando `echo`.
3. Liste toda a estrutura de pastas e arquivos criada
3. Salve a estrutura de pastas e arquivos em um arquivo txt chamado `seunome_desafio_linux.txt`

---

## Tarefa Extra - Permissões e Segurança (Linux)

Nesta tarefa vamos conhecer comandos relacionados a permissões.

> [!WARNING]
>
> O Git Bash possui suporte parcial às permissões Linux. Alguns comportamentos podem ser diferentes de uma distribuição Linux real.

1. Visualize as permissões dos arquivos

```bash
ls -l
```

2. Remova a permissão de escrita do arquivo `README.md`

```bash
chmod 444 README.md
```

3. Para validar execute:

```bash
ls -l
```

4. Abra o arquivo através do Nano e tente modificar o arquivo

```bash
nano README.md
```

5. O Nano exibirá a mensagem `[ File 'README.md' is unwritable ]`, ou seja, somente leitura

![](https://i.imgur.com/3Y2P4Mx.png)

6. Pressione `ctrl + x` para sair
7. Adicione permissão de escrita novamente

```bash
chmod 644 README.md
```

8. Para validar execute:

```bash
ls -l
```

9. Abra o arquivo através do Nano e tente modificar o arquivo

```bash
nano README.md
```

10. O Nano agora permitirá que você edite e salve o arquivo

![](https://i.imgur.com/w0mKUxw.png)

11. Pressione `ctrl + o + enter` para salvar
12. Pressione `ctrl + x` para sair
