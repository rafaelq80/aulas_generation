<h1>Permissões de arquivos e pastas</h1>



Em sistemas Linux, cada arquivo ou pasta possui **permissões de acesso** que controlam quem pode **ler** (*read*), **escrever** (*write*) ou **executar** (*execute*). Vamos visualizar isto na prática:

1. Abra o Terminal do **Git Bash**
2. Acesse a pasta **aula_terminal**, através do comando abaixo:

```bash
cd aula_terminal
```

3. Digite o comando abaixo para listar todos os arquivos e pastas com as respectivas permissões:

```bash
ls -l
```

4. Observe na imagem abaixo, que foram exibidas algumas letras ao lado do nome de cada arquivo e de cada pasta que foram criadas dentro da pasta **aula_terminal**:

<div align="center"><img src="https://i.imgur.com/4HRmDXu.png" alt="imgur" /></div>

Estas letras ao lado das pastas e dos arquivos, indicam as permissões que os usuários possuem em relação aos arquivos e pastas, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/Nl4j59m.png" alt="imgur" /></div>

No total são 10 caracteres, onde:

- O primeiro caractere indica o **tipo do arquivo**

- Os próximos três caracteres (2 a 4) são as **Permissões do Proprietário** do arquivo ou da pasta, ou seja, quem criou o arquivo ou a pasta.

- Os próximos três caracteres (5 a 7) são as **Permissões dos Grupos de Usuários** associados ao arquivo ou a pasta.

- Os últimos três caracteres (8 a 10) são as **Permissões aplicadas para todos os usuários (Outros)**, que não são membros dos grupos associados ou o Proprietário do arquivo ou da pasta.

> ### **O que é um grupo?**
>
> Um grupo é simplesmente uma entidade que contém um ou mais usuários. Cada grupo tem um nome e um identificador único chamado **GID (Group ID)**. Um usuário pode fazer parte de vários grupos, mas sempre terá um **grupo primário** (associado ao usuário por padrão) e pode participar de outros **grupos secundários**.
>
> ### **Como os grupos são usados no sistema de arquivos?**
>
> 1. **Associação de arquivos e diretórios a um grupo**: Cada arquivo ou pasta no Sistema de arquivo Linux pertence a um **proprietário** e a um **grupo**. Os membros do grupo associado a um arquivo ou pasta podem receber permissões específicas (leitura, escrita ou execução) dependendo das configurações.
> 2. **Permissões por grupo**: As permissões dos grupos são a segunda camada de controle. Quando um usuário tenta acessar um arquivo ou pasta:
>    - O sistema verifica primeiro as permissões do **proprietário**.
>    - Em seguida, verifica as permissões para o **grupo**.
>    - Por último, verifica as permissões para **outros**.

<br />

<h2>2. Tipos de Arquivos</h2>



Com relação aos tipos de arquivos, existem diversos tipos, os mais comuns são:

1. **`-` (Hífen)**: Arquivo regular.
   - Representa arquivos normais, como documentos, imagens, ou binários.
2. **`d`**: Diretório.
   - Representa pastas que podem conter outros arquivos e diretórios.
3. **`l`**: Link simbólico (*symbolic link*).
   - Um atalho que aponta para outro arquivo ou diretório, semelhante aos atalhos do Windows.

<br />

<br />

<h2>2. Permissões</h2>



Com relação permissões, existem 3 tipos:

1. **Leitura (r)**: Permite visualizar o conteúdo do arquivo ou listar o conteúdo de uma pasta.
2. **Escrita (w)**: Permite modificar o arquivo ou criar/deletar arquivos dentro de uma pasta.
3. **Execução (x)**: Permite executar arquivos como programas ou acessar o conteúdo de uma pasta.
4. **Sem permissão (-)**

**Exemplo 01 - Arquivo:**

<div align="center"><img src="https://i.imgur.com/Qu5QwKM.png" alt="imgur" /></div>

  - `-`    (Tipo do Arquivo): Arquivo regular.
  - **`rw-`** (Permissões do Proprietário): Leitura (*Read*), Escrita (*Write*), sem permissão de Execução.
  - **`r--`** (Permissões do Grupo): Apenas Leitura (*Read*).
  - **`r--`** (para outros): Apenas Leitura (*Read*).

**Exemplo 02 - Pasta:**

<div align="center"><img src="https://i.imgur.com/c7ugOeq.png" alt="imgur" /></div>

  - `d`    (Tipo do Arquivo): Pasta
  - **`rwx`** (Permissões do Proprietário): Leitura (*Read*), Escrita (*Write*) e Execução.
  - **`r-x`** (Permissões do Grupo): Apenas Leitura (*Read*) e Execução.
  - **`r-x`** (para outros): Apenas Leitura (*Read*) e Execução.

Estas Permissões também podem ser representadas por números:

1. **Leitura (r)** 🡪 4
2. **Escrita (w)** 🡪 2
3. **Execução (x)** 🡪 1

Para atribuir as Permissões através dos números, utilizamos a soma deles:

- r + w + x 🡪 4 + 2 + 1 = 7 (Acesso total)
- r + w  🡪 4 + 2 = 6 (Leitura e Gravação)
- r + x 🡪 4 + 1 = 5 (Leitura e Execução)
- r = 4 (Somente Leitura)

Você também pode visualizar as Permissões dos arquivos e pastas no formato numérico, no **Git Bash**, através do comando abaixo:

```bash
stat -c '%a %n' *
```

O resultado, você confere na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/bacIfsO.png" alt="imgur" /></div>

*Note que as Permissões serão exibidas no formato numérico.*

<br />

<h2>3. Alterando Permissões</h2>



Para modificar as Permissões dos arquivos e pastas no Linux, utilizamos o comando `chmod`. Para alterar as Permissões, tanto podemos utilizar o modo Simbólico (RWX), quanto o modo Numérico, como veremos a seguir:

<br />

<h3>3.1. Modo simbólico</h3>



1. Adiciona a permissão de leitura para o proprietário no arquivo **verao.txt**:

```bash
chmod u+r verao.txt
```

*A letra **u** indica que a permissão está sendo aplicada no Proprietário.*

2. Remove a permissão de escrita para o grupo no arquivo **outono.txt**:

```bash
chmod g-w outono.txt
```

*A letra **g** indica que a permissão está sendo aplicada no grupo.*

3. Adiciona permissão de execução para outros no arquivo **primavera.txt**:

```bash
chmod o+x primavera.txt
```

*A letra **o** indica que a permissão está sendo aplicada para os demais usuários.*

4. Define apenas leitura para todos no arquivo **inverno.txt**:

```bash
chmod a=r inverno.txt
```

*A letra **a** indica que a permissão está sendo aplicada no proprietário, no grupo e nos demais usuários.*

**Observações Importantes:**

- O sinal de **+** indica que um novo direito está sendo atribuído
- O sinal de **-** indica que um direito está sendo removido
- O Sinal de **=** indica que a nova permissão atribuída sobrescreverá todas as permissões existentes.

<br />

<h3>3.2. Modo numérico</h3>



1. Adiciona as seguintes permissões no arquivo **django.txt**:
   1. **Proprietário:** leitura, escrita e execução; 
   2. **Grupo:** leitura e execução;
   3. **Outros:** leitura e execução;

```bash
chmod 755 django.txt  
```

2. Adiciona as seguintes permissões no arquivo **python.txt**:
   1. **Proprietário:** leitura e escrita; 
   2. **Grupo:** leitura e execução;
   3. **Outros:** leitura e execução;

```bash
chmod 644 python.txt  
```

3. Adiciona as seguintes permissões na pasta **verao**:
   1. **Proprietário:** leitura, escrita e execução; 
   2. **Grupo:** leitura e execução;
   3. **Outros:** nenhum acesso;

```bash
chmod 750 verao/
```

<br />

> [!CAUTION]
>
> Muito cuidado ao atribuir a permissão 777 em um diretório ou arquivo. Com esta permissão, todos os Usuários terão todas as permissões no arquivo ou na pasta, podendo fazer qualquer coisa.

