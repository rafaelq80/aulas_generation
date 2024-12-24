<h1>Tipos de dados - Bancos de dados Relacionais</h1>

<br />

<h2>1. MySQL e Postgres SQL</h2>



Veja na tabela abaixo os principais tipos de dados no **MySQL** e os seus equivalentes no **Postgres SQL**. Ela está organizada por categorias para facilitar a consulta:

| **Categoria**        | **MySQL**                    | **Postgres SQL**           | **Descrição**                                                |
| -------------------- | ---------------------------- | -------------------------- | ------------------------------------------------------------ |
| **Inteiros**         | TINYINT (1 byte)             | SMALLINT (2 bytes)         | Inteiros de tamanho pequeno.                                 |
|                      | SMALLINT (2 bytes)           | INTEGER ou INT (4 bytes)   | Inteiros de tamanho médio.                                   |
|                      | MEDIUMINT (3 bytes)          | BIGINT (8 bytes)           | Inteiros de tamanho grande.                                  |
|                      | INT ou INTEGER (4 bytes)     | INT ou INTEGER (4 bytes)   | Inteiros padrão em ambas as bases.                           |
|                      | BIGINT (8 bytes)             | BIGINT (8 bytes)           | Inteiros de tamanho muito grande.                            |
| **Decimais**         | DECIMAL (ou NUMERIC)         | NUMERIC ou DECIMAL         | Valores exatos, como preços, especificando precisão e escala. |
|                      | FLOAT (4 bytes)              | REAL (4 bytes)             | Valores com ponto flutuante de precisão simples.             |
|                      | DOUBLE ou DOUBLE PRECISION   | DOUBLE PRECISION           | Valores com ponto flutuante de precisão dupla.               |
| **Cadeias de Texto** | CHAR (tamanho fixo)          | CHAR (tamanho fixo)        | Cadeia de caracteres de tamanho fixo.                        |
|                      | VARCHAR (tamanho variável)   | VARCHAR (tamanho variável) | Cadeia de caracteres de tamanho variável.                    |
|                      | TEXT (tamanho variável)      | TEXT (tamanho variável)    | Cadeia de caracteres de tamanho ilimitado (não indexável diretamente). |
| **Datas e Horas**    | DATE                         | DATE                       | Datas no formato `YYYY-MM-DD`.                               |
|                      | DATETIME                     | TIMESTAMP                  | Data e hora no formato `YYYY-MM-DD HH:MM:SS`.                |
|                      | TIMESTAMP                    | TIMESTAMP                  | Igual ao `DATETIME`, mas com fuso horário (PostgreSQL é mais avançado aqui). |
|                      | TIME                         | TIME                       | Apenas hora no formato `HH:MM:SS`.                           |
|                      | YEAR                         | Não disponível             | Apenas ano no formato `YYYY`.                                |
| **Booleanos**        | TINYINT(1) (usado como bool) | BOOLEAN ou BOOL            | Valores lógicos (true/false).                                |
| **Binários**         | BINARY (tamanho fixo)        | BYTEA                      | Dados binários de tamanho fixo.                              |
|                      | VARBINARY (tamanho variável) | BYTEA                      | Dados binários de tamanho variável.                          |
| **UUID**             | Não disponível               | UUID                       | Identificador único universal.                               |
| **JSON**             | JSON                         | JSON ou JSONB              | Dados estruturados no formato JSON (`JSONB` no PostgreSQL é mais otimizado). |
| **Geográficos**      | Não disponível               | GEOMETRY, GEOGRAPHY        | Dados espaciais e geográficos (via extensão `PostGIS`).      |
| **Outros**           | ENUM                         | Não disponível diretamente | Conjunto de valores fixos definidos pelo usuário.            |
|                      | SET                          | Não disponível             | Conjunto de valores múltiplos permitidos.                    |
|                      | Não disponível               | ARRAY                      | Vetores ou listas de valores.                                |
|                      | Não disponível               | HSTORE                     | Dados chave-valor no formato chave/string.                   |

------

### **Notas Importantes:**

1. **MySQL**:
   - Não possui suporte nativo a `UUID`, `ARRAY` ou tipos geográficos avançados.
   - Utiliza `TINYINT(1)` para representar booleanos.
   - Tipos como `ENUM` e `SET` são úteis, mas difíceis de migrar para outros bancos de dados.
2. **Postgres SQL**:
   - Possui suporte avançado para tipos como `JSONB`, `ARRAY`, `UUID` e dados geográficos.
   - É mais robusto no trabalho com tipos de dados complexos, como dados espaciais e estruturas chave-valor (`HSTORE`).
   - Para utilizar o tipo `ENUM` é necessário primeiro criar o tipo ENUM e na sequência ele estará pronto para uso.

<br />

<h2>2. MySQL, SQL Server e Oracle</h2>



Veja na tabela abaixo os principais tipos de dados do **MySQL** e seus equivalentes no **SQL Server** e no **Oracle**. A tabela está organizada por categorias.

------

| **Categoria**        | **MySQL**                    | **SQL Server**               | **Oracle**                            | **Descrição**                                                |
| -------------------- | ---------------------------- | ---------------------------- | ------------------------------------- | ------------------------------------------------------------ |
| **Inteiros**         | TINYINT (1 byte)             | TINYINT (1 byte)             | Não disponível                        | Inteiros de pequeno tamanho.                                 |
|                      | SMALLINT (2 bytes)           | SMALLINT (2 bytes)           | NUMBER(5)                             | Inteiros pequenos.                                           |
|                      | MEDIUMINT (3 bytes)          | Não disponível               | Não disponível                        | Inteiros médios (somente no MySQL).                          |
|                      | INT ou INTEGER (4 bytes)     | INT (4 bytes)                | NUMBER(10)                            | Inteiros padrão.                                             |
|                      | BIGINT (8 bytes)             | BIGINT (8 bytes)             | NUMBER(19)                            | Inteiros grandes.                                            |
| **Decimais**         | DECIMAL ou NUMERIC           | DECIMAL ou NUMERIC           | NUMBER                                | Valores exatos com precisão definida (ex.: valores monetários). |
|                      | FLOAT (4 bytes)              | REAL (4 bytes)               | BINARY_FLOAT                          | Ponto flutuante de precisão simples.                         |
|                      | DOUBLE ou DOUBLE PRECISION   | FLOAT (8 bytes)              | BINARY_DOUBLE                         | Ponto flutuante de precisão dupla.                           |
| **Cadeias de Texto** | CHAR (tamanho fixo)          | CHAR (tamanho fixo)          | CHAR (tamanho fixo)                   | Cadeias de caracteres com tamanho fixo.                      |
|                      | VARCHAR (tamanho variável)   | VARCHAR (tamanho variável)   | VARCHAR2 (tamanho variável)           | Cadeias de caracteres com tamanho variável.                  |
|                      | TEXT (tamanho ilimitado)     | TEXT                         | CLOB                                  | Texto de tamanho grande ou ilimitado.                        |
| **Datas e Horas**    | DATE                         | DATE                         | DATE                                  | Datas sem hora.                                              |
|                      | DATETIME                     | DATETIME                     | TIMESTAMP                             | Data e hora.                                                 |
|                      | TIMESTAMP                    | DATETIMEOFFSET               | TIMESTAMP WITH TIME ZONE              | Data e hora com suporte a fuso horário.                      |
|                      | TIME                         | TIME                         | Não disponível                        | Apenas hora.                                                 |
|                      | YEAR                         | Não disponível               | Não disponível                        | Apenas ano.                                                  |
| **Booleanos**        | TINYINT(1) (como booleano)   | BIT                          | Não disponível                        | Valores lógicos (verdadeiro/falso).                          |
| **Binários**         | BINARY (tamanho fixo)        | BINARY (tamanho fixo)        | RAW (tamanho fixo)                    | Dados binários de tamanho fixo.                              |
|                      | VARBINARY (tamanho variável) | VARBINARY (tamanho variável) | BLOB                                  | Dados binários de tamanho variável.                          |
|                      | BLOB                         | VARBINARY(MAX)               | BLOB                                  | Dados binários grandes.                                      |
| **UUID**             | Não disponível               | UNIQUEIDENTIFIER             | Não disponível                        | Identificador único universal.                               |
| **JSON**             | JSON                         | JSON                         | Não disponível (armazenado como CLOB) | Dados no formato JSON.                                       |
| **Geográficos**      | Não disponível               | GEOGRAPHY ou GEOMETRY        | SDO_GEOMETRY (via extensão)           | Dados espaciais e geográficos.                               |
| **Outros**           | ENUM                         | Não disponível (usar CHECK)  | Não disponível (usar CHECK)           | Conjunto fixo de valores.                                    |
|                      | SET                          | Não disponível               | Não disponível                        | Conjunto de valores múltiplos.                               |
|                      | Não disponível               | Não disponível               | Não disponível                        | Vetores ou listas de valores.                                |
|                      | Não disponível               | Não disponível               | Não disponível                        | Dados chave-valor (apenas PostgreSQL).                       |

------

### **Notas Importantes:**

1. **ENUM**:
   - No SQL Server e Oracle, usa-se também **CHECK constraints** para valores fixos.
2. **JSON**:
   - No Oracle, JSON é geralmente armazenado como **CLOB** ou outros tipos.
3. **Binários**:
   - O SQL Server e o Oracle possuem como alternativa ao tipo Binário o **BLOB**.
4. **Booleanos**:
   - No MySQL, o tipo **BOOLEAN** é mapeado para **TINYINT(1)**.
   - No Oracle, não há suporte nativo para **BOOLEAN**.
5. **Geográficos**:
   - Para dados espaciais, o Oracle utiliza **SDO_GEOMETRY**.

