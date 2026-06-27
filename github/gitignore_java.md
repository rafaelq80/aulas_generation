# Modelo  .gitgnore - Java 



1. No Terminal, crie o arquivo **`.gitignore`** na pasta da sua Workspace (versionar vários projetos) ou na pasta do seu Projeto (versionar apenas um projeto específico)

```bash
touch .gitignore
```

2. Abra o arquivo **`.gitignore`** através do comando abaixo:

**Windows**

```bash
notepad .gitignore
```

**Linux e macOS**

```bash
nano .gitignore
```

**Visual Studio Code**

```bash
code .
```

3. Copie o código abaixo, cole no seu arquivo **`.gitignore`** e salve

> [!TIP]
>
> **Como utilizar o Nano?**
>
> 1. Para copiar e colar o conteúdo do **`.gitignore`** no Nano:
>
> **Linux**
>
> - **Copiar:** `Ctrl + Shift + C`
> - **Colar:** `Ctrl + Shift + V`
>
> **macOS**
>
> - **Copiar:** `Command + C` (⌘ + C)
>
> - **Colar:** `Command + V` (⌘ + V)
>
> 2. Pressione **`Ctrl + X`** para salva e sair.
> 3. O Nano perguntará se deseja salvar. Pressione **`Y`** (para *Yes* ou Sim).
> 4. Ele mostrará o nome do arquivo. Apenas pressione **`Enter`** para confirmar.

<br />

```bash
# ================================
# Arquivos comuns de Java
# ================================
*.class
*.jar
*.war
*.ear
*.log

# ================================
# Pastas de build/output
# ================================
bin/
build/
target/
out/

# ================================
# Eclipse / Spring Tool Suite (STS)
# ================================
.classpath
.project
.settings/
.springBeans
.factorypath
.metadata/

# ================================
# IntelliJ IDEA
# ================================
.idea/
*.iml
*.iws
*.ipr
out/

# ================================
# VS Code
# ================================
.vscode/

# ================================
# Arquivos de sistema (Windows / macOS / Linux)
# ================================
.DS_Store
Thumbs.db
ehthumbs.db
*.swp
*.swo
```
