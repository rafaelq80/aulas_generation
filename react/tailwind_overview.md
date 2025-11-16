<h1>Tailwind CSS - Overview</h1>



O **Tailwind CSS** é um framework *utility-first*, ou seja, baseado em utilitários prontos que permitem aplicar estilos diretamente no HTML por meio de classes pré-definidas. Essa abordagem elimina a necessidade de criar folhas de estilo personalizadas para cada elemento, tornando o desenvolvimento mais rápido e consistente.

Neste conteúdo, vamos explorar as classes essenciais do Tailwind CSS, entender como utilizá-las na prática e conhecer suas propriedades, variações e particularidades, de forma a aproveitar ao máximo o potencial desse framework.

<br />

<h2>1. Utilizando as Classes do Tailwind no React</h2>



As **classes utilitárias** do Tailwind CSS podem ser aplicadas diretamente nos elementos JSX/TSX de um componente React, sem a necessidade de criar arquivos CSS separados. Cada classe define um estilo específico, e você pode combiná-las livremente para construir layouts e componentes de forma rápida e consistente.

Nos componentes **React**, todas as classes CSS — incluindo as utilitárias do Tailwind — devem ser atribuídas à propriedade `className` do elemento.

> **Por que `className` e não `class`?**
>
> No JavaScript, `class` é uma palavra reservada usada para declarar classes na linguagem. Como o JSX é uma extensão do JavaScript, usar `class` diretamente causaria conflitos de sintaxe. Para evitar esse problema, o React adota a propriedade `className`, que cumpre exatamente a mesma função do atributo `class` no HTML, mas é compatível com a sintaxe JavaScript.

<br />

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>**Exemplo**

```jsx
export default function App() {
  return (
    <h1 className="text-blue-500 text-center mb-4">
      Meu título estilizado
    </h1>
  );
}
```

**O que está acontecendo:**

- `text-blue-500` → cor do texto.
- `text-center` → centraliza o texto.
- `mb-4` → adiciona margem inferior.

Você pode compor estilos complexos combinando múltiplas classes Tailwind em um único elemento.

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> **Exemplo**

```jsx
export default function App() {
  return (
    <div className="bg-gray-200 p-6 rounded-lg shadow-lg">
      <p className="text-lg text-gray-800 font-semibold">
        Texto dentro de um container estilizado
      </p>
    </div>
  );
}
```

**Detalhes das classes:**

- `bg-gray-200` → cor de fundo cinza claro.
- `p-6` → espaçamento interno de 1.5rem.
- `rounded-lg` → cantos arredondados.
- `shadow-lg` → sombra.
- `text-lg` → tamanho de texto.
- `font-semibold` → peso semi-negrito.

O Tailwind permite aplicar estilos condicionais, como `hover:` para eventos de interação.

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>**Exemplo**

```jsx
export default function App() {
  return (
    <button className="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">
      Clique aqui
    </button>
  );
}
```

- `hover:bg-blue-600` → muda a cor de fundo ao passar o mouse.

Você pode usar prefixos como `sm:`, `md:`, `lg:` para aplicar estilos diferentes em cada tamanho de tela.

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>**Exemplo**

```jsx
export default function App() {
  return (
    <p className="text-base md:text-lg lg:text-xl">
      Texto que aumenta conforme o tamanho da tela.
    </p>
  );
}
```

- `text-base` → padrão.
- `md:text-lg` → tamanho maior a partir de telas médias.
- `lg:text-xl` → ainda maior em telas grandes

<br />

<h2>2. Unidades de Medida</h2>



O **Tailwind CSS** utiliza, por padrão, um sistema de espaçamento baseado em `rem`, que é uma unidade relativa ao tamanho da fonte raiz da página (`1rem` normalmente equivale a 16px, salvo alterações no CSS global).

Essas medidas são representadas por escalas numéricas pré-definidas, facilitando a consistência do design.

| Classe    | Valor em `rem` | Equivalente em `px` |
| --------- | -------------- | ------------------- |
| `p-1`     | `0.25rem`      | 4px                 |
| `p-2`     | `0.5rem`       | 8px                 |
| `p-4`     | `1rem`         | 16px                |
| `text-sm` | `0.875rem`     | 14px                |
| `text-xl` | `1.25rem`      | 20px                |

> Essas escalas não se limitam ao *padding* (`p-`), mas também se aplicam a *margin*, *gap*, *width*, *height* e diversos outros utilitários.

Além das escalas predefinidas, o Tailwind permite especificar **valores fixos** usando **colchetes (`[]`)**.
 Isso é útil quando você precisa de um tamanho que não existe na escala padrão.

```html
<div class="w-[120px] h-[60px] bg-gray-300"></div>
```

- `w-[120px]` → define largura fixa de 120 pixels.
- `h-[60px]` → define altura fixa de 60 pixels.

💡 Com os colchetes, você pode usar qualquer unidade suportada pelo CSS, como:

- **px** (pixels) → `w-[300px]`
- **%** (porcentagem) → `w-[50%]`
- **rem/em** → `w-[2.5rem]`
- **vh/vw** (viewport height/width) → `h-[50vh]`

Isso dá flexibilidade para criar layouts responsivos ou elementos com dimensões muito específicas sem precisar criar uma classe personalizada no CSS.

<br />

<h2>3. Cores</h2>



O **Tailwind CSS** oferece uma paleta extensa de cores pré-definidas, baseada no sistema de cores escalonado (shades) que vai de **50** (mais claro) a **950** (mais escuro). Essas cores são aplicadas a qualquer propriedade de estilo que aceite valores de cor, como fundo, texto e borda.

**Estrutura básica de uso:**

```html
<div class="bg-blue-500 text-white border border-blue-700">
  Exemplo de uso de cores
</div>
```

- `bg-blue-500` → cor de fundo azul médio.
- `text-white` → cor do texto branca.
- `border-blue-700` → borda azul mais escura.

Na tabela abaixo estão alguns exemplos da paleta de cores padrão do Tailwind:

| Cor Base   | Classe exemplo  | Escalas Disponíveis                                  |
| ---------- | --------------- | ---------------------------------------------------- |
| **Gray**   | `bg-gray-500`   | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |
| **Red**    | `bg-red-500`    | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |
| **Orange** | `bg-orange-500` | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900      |
| **Yellow** | `bg-yellow-500` | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900      |
| **Green**  | `bg-green-500`  | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |
| **Blue**   | `bg-blue-500`   | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |
| **Purple** | `bg-purple-500` | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |
| **Pink**   | `bg-pink-500`   | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 |

<br />

💡 **Padrão de nomenclatura:**

```
[propriedade]-[cor]-[intensidade]
```

**Exemplos:**

- `text-green-600` → texto verde escuro.
- `bg-yellow-200` → fundo amarelo claro.
- `border-red-700` → borda vermelha escura.

<br />

<h3>3.1. Personalizando a Paleta de Cores</h3>



No **Tailwind CSS 4**, é possível definir uma **paleta de cores personalizada** utilizando variáveis CSS no arquivo de estilos.  Essa abordagem é especialmente útil em projetos React, pois não é necessário alterar o `tailwind.config.js` — basta adicionar as cores no arquivo de estilos global `index.css`, usando a anotação `@theme`.

Essa configuração permite criar nomes de cores descritivos e reutilizáveis, mantendo a consistência visual da aplicação.

<img src="https://i.imgur.com/FkcNWAL.png" title="source: imgur.com" width="4%"/> **Exemplo — Criando uma paleta personalizada:**

```css
@import "tailwindcss";

@theme {
  --color-daisy-bush-50:  #f5f3ff;
  --color-daisy-bush-100: #eceafd;
  --color-daisy-bush-200: #ddd7fd;
  --color-daisy-bush-300: #c2b7fb;
  --color-daisy-bush-400: #a58ff6;
  --color-daisy-bush-500: #8761f1;
  --color-daisy-bush-600: #7740e7;
  --color-daisy-bush-700: #682ed3;
  --color-daisy-bush-800: #5726b1;
  --color-daisy-bush-900: #441f88;
  --color-daisy-bush-950: #2c1362;
}
```

Após definir as cores, você poderá usá-las como qualquer outra cor do Tailwind, combinando-as com propriedades como `bg-`, `text-` e `border-`.

**Exemplos de uso:**

- `bg-daisy-bush-500` → fundo roxo médio
- `text-daisy-bush-800` → texto roxo escuro
- `border-daisy-bush-200` → borda roxa clara

<br />

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> **Exemplo - Componente React**

```jsx
export default function App() {
  return (
    <div className="bg-daisy-bush-500 text-white p-4 rounded">
      Componente com cor personalizada
    </div>
  );
}
```

<br />

> [!TIP]
>
> Para criar **paletas de cores personalizadas** no estilo do Tailwind de forma rápida e prática, experimente o **UI Colors**: https://uicolors.app. Ele permite gerar combinações harmônicas de cores que podem ser aplicadas diretamente no seu projeto.

<br />

<h2>4. Tipografia (Fontes)</h2>



O **Tailwind CSS** oferece uma forma prática de controlar fontes e tipografia, permitindo aplicar **famílias de fontes**, **tamanhos**, **pesos** e **estilos** diretamente nas classes do HTML/JSX, sem necessidade de escrever CSS adicional.

Por padrão, o Tailwind utiliza a **fonte sans-serif do sistema**, definida na configuração padrão, ou seja, se você não alterar nada, os elementos usarão a **fonte padrão do sistema**, garantindo carregamento rápido e compatibilidade entre navegadores.

<br />

<h3>4.1. Usando Fontes do Google no Tailwind com React</h3>



Você pode adicionar fontes do **Google Fonts** em projetos **React** e utilizá-las com Tailwind seguindo estes passos:

1. Acesse o site do Google Fonts clicando no link abaixo: 

<div align="left"><img src="https://i.imgur.com/IImpjoV.png" title="source: imgur.com" width="30px"/> <a href="https://fonts.google.com/" target="_blank"><b>Google Fonts</b></a></div>

2. Será aberta a janela abaixo:

<div align="center"><img src="https://i.imgur.com/hyJi3HU.png" title="source: imgur.com" /></div>

3. No campo **Search fonts**, digite o nome da fonte que deseja utilizar no seu projeto React:

<div align="center"><img src="https://i.imgur.com/1hseX6F.png" title="source: imgur.com" /></div>

4. Clique na fonte desejada para abrir a tela de detalhes:

<div align="center"><img src="https://i.imgur.com/bolN7wH.png" title="source: imgur.com" /></div>

5. Clique no botão **Get font**.

<div align="center"><img src="https://i.imgur.com/izKxRkc.png" title="source: imgur.com" /></div>

6. Na próxima tela, clique em **< > Get embed code**.

<div align="center"><img src="https://i.imgur.com/NdodhrA.png" title="source: imgur.com" /></div>

7. Selecione a opção **@import**, conforme indicado:

<div align="center"><img src="https://i.imgur.com/yAY0B7I.png" title="source: imgur.com" /></div>

8. Na janela **Embed code**, logo abaixo da opção **@import**, no item **Embed code in the `<head>` of your html**, copie **apenas a linha dentro da tag `style`**:

<div align="center"><img src="https://i.imgur.com/hMuEvjw.png" title="source: imgur.com" /></div>

9. Cole a linha copiada **na primeira linha do arquivo CSS global da aplicação React (`index.css`)**:

<div align="center"><img src="https://i.imgur.com/3noQgbQ.png" title="source: imgur.com" /></div>

<br />

> [!WARNING]
>
> A importação deve ser **obrigatoriamente na primeira linha** do arquivo `index.css`, garantindo que a fonte seja carregada antes de qualquer estilo aplicado no projeto. Caso contrário, a fonte não será reconhecida pelo React.

10. Após importar a fonte, você pode configurá-la no Tailwind usando a anotação `@theme`. Adicione a seguinte linha logo após as importações:

```css
@theme{
  --font-montserrat: 'Montserrat', 'sans-serif'
}
```

*Essa configuração define a fonte **Montserrat** como padrão. Caso ela não esteja disponível, será usada a fonte **sans-serif** do sistema.*

11. Após os passos acima, seu arquivo `index.css` ficará semelhante a este:

```jsx
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');
@import "tailwindcss";

@theme{
  --font-montserrat: 'Montserrat', 'sans-serif'
}
```

Após configurar a fonte, você pode aplicá-la nas classes Tailwind, como vemos no exemplo abaixo:

<br />

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> **Exemplo - Componente React**

```jsx
export default function App() {
  return (
    <div className="font-montserrat bg-daisy-bush-500 text-white p-4 rounded">
      Componente com cor personalizada
    </div>
  );
}
```

<br />

<h3>4.2. Tamanhos de Fonte</h3>



O Tailwind utiliza uma nomenclatura **predefinida** que facilita aplicar tamanhos de fonte sem precisar calcular valores em pixels. As mais comuns são:

| Classe      | Tamanho (rem) | Equivalente em px | Descrição                                          |
| ----------- | ------------- | ----------------- | -------------------------------------------------- |
| `text-sm`   | 0.875rem      | 14px              | Pequeno, ideal para legendas ou textos secundários |
| `text-base` | 1rem          | 16px              | Padrão para textos do corpo                        |
| `text-lg`   | 1.125rem      | 18px              | Maior que o padrão, bom para destaques leves       |
| `text-xl`   | 1.25rem       | 20px              | Títulos ou subtítulos pequenos                     |
| `text-2xl`  | 1.5rem        | 24px              | Subtítulos ou títulos médios                       |
| `text-3xl`  | 1.875rem      | 30px              | Títulos maiores                                    |
| `text-4xl`  | 2.25rem       | 36px              | Títulos grandes                                    |
| `text-5xl`  | 3rem          | 48px              | Títulos de destaque                                |
| `text-6xl`  | 3.75rem       | 60px              | Títulos muito grandes                              |

Você também pode definir tamanhos **personalizados** usando colchetes:

```html
<p class="text-[22px]">Texto com tamanho específico</p>
```

<br/>

<h3>4.3. Formatação e Peso da Fonte</h3>



Além do tamanho, o Tailwind permite controlar **peso, estilo e capitalização** da fonte:

| Classe           | Significado / Uso                        |
| ---------------- | ---------------------------------------- |
| `font-thin`      | Fonte muito fina (100)                   |
| `font-light`     | Fonte leve (300)                         |
| `font-normal`    | Fonte normal (400)                       |
| `font-medium`    | Fonte média (500)                        |
| `font-semibold`  | Fonte semi-negrito (600)                 |
| `font-bold`      | Negrito (700)                            |
| `font-extrabold` | Extra negrito (800)                      |
| `font-black`     | Máximo de negrito (900)                  |
| `italic`         | Texto em itálico                         |
| `not-italic`     | Texto normal (sem itálico)               |
| `uppercase`      | Todas as letras maiúsculas               |
| `lowercase`      | Todas as letras minúsculas               |
| `capitalize`     | Primeira letra de cada palavra maiúscula |

<br />

<h2>5. Box Model</h2>



O **Box Model** é um conceito fundamental do CSS que define como os elementos HTML ocupam espaço na página. Ele é composto por quatro camadas:

1. **Content (Conteúdo):** área onde o texto, imagem ou outro conteúdo do elemento aparece.
2. **Padding (Preenchimento):** espaço interno entre o conteúdo e a borda do elemento.
3. **Border (Borda):** contorno ao redor do padding.
4. **Margin (Margem):** espaço externo entre o elemento e os elementos vizinhos.

No Tailwind, você controla todas essas propriedades com classes utilitárias prontas, sem precisar escrever CSS manual.

<br />

<h3>5.1. Padding</h3>



O **padding** define o espaço interno do elemento. O Tailwind utiliza uma escala baseada em `rem`:

| Classe | Valor em `rem` | Equivalente em `px` |
| ------ | -------------- | ------------------- |
| `p-0`  | 0rem           | 0px                 |
| `p-1`  | 0.25rem        | 4px                 |
| `p-2`  | 0.5rem         | 8px                 |
| `p-4`  | 1rem           | 16px                |
| `p-8`  | 2rem           | 32px                |

Você também pode aplicar padding apenas em um lado:

| Classe | Lado Aplicado                |
| ------ | ---------------------------- |
| `pt-4` | padding-top                  |
| `pb-4` | padding-bottom               |
| `pl-4` | padding-left                 |
| `pr-4` | padding-right                |
| `px-4` | padding-left + padding-right |
| `py-4` | padding-top + padding-bottom |

<br />

<h3>5.2. Margin</h3>



A **margem** controla o espaço externo entre elementos:

| Classe | Valor em `rem` | Equivalente em `px` |
| ------ | -------------- | ------------------- |
| `m-0`  | 0rem           | 0px                 |
| `m-1`  | 0.25rem        | 4px                 |
| `m-2`  | 0.5rem         | 8px                 |
| `m-4`  | 1rem           | 16px                |
| `m-8`  | 2rem           | 32px                |

Você também pode aplicar margin apenas em um lado:

| Classe | Lado Aplicado              |
| ------ | -------------------------- |
| `mt-4` | margin-top                 |
| `mb-4` | margin-bottom              |
| `ml-4` | margin-left                |
| `mr-4` | margin-right               |
| `mx-4` | margin-left + margin-right |
| `my-4` | margin-top + margin-bottom |

<br />

<h3>5.3. Border (Borda)</h3>



O Tailwind permite controlar **largura, estilo e cor da borda**:

| Classe            | Descrição                      |
| ----------------- | ------------------------------ |
| `border`          | Adiciona borda de 1px sólida   |
| `border-2`        | Borda de 2px                   |
| `border-4`        | Borda de 4px                   |
| `border-t`        | Apenas a borda superior        |
| `border-b`        | Apenas a borda inferior        |
| `border-l`        | Apenas a borda esquerda        |
| `border-r`        | Apenas a borda direita         |
| `border-gray-500` | Define a cor da borda          |
| `rounded`         | Bordas arredondadas (4px)      |
| `rounded-lg`      | Bordas mais arredondadas (8px) |

<br />

<h3>5.4. Width e Height</h3>



Você também pode controlar o **tamanho do box** com classes utilitárias:

| Classe         | Descrição                  |
| -------------- | -------------------------- |
| `w-32`         | Largura de 8rem (128px)    |
| `h-32`         | Altura de 8rem (128px)     |
| `w-full`       | Largura total do contêiner |
| `h-full`       | Altura total do contêiner  |
| `max-w-md`     | Largura máxima média       |
| `min-h-screen` | Altura mínima da tela      |

Para dimensões não incluídas na escala, você pode usar **colchetes**:

```html
<div class="w-[150px] h-[75px] bg-gray-300"></div>
```

<br />

<h2>6. Bordas e Sombras</h2>



O **Tailwind CSS** oferece utilitários para controlar **bordas** e **sombras**, permitindo criar elementos com aparência mais definida e visualmente atraente, sem precisar escrever CSS manual.

<br />

### 6.1. Bordas

As bordas envolvem o contorno de um elemento e podem ser controladas em **largura**, **cor**, **estilo** e **arredondamento**.

#### Largura da borda

| Classe     | Descrição             |
| ---------- | --------------------- |
| `border`   | Borda de 1px (padrão) |
| `border-2` | Borda de 2px          |
| `border-4` | Borda de 4px          |
| `border-8` | Borda de 8px          |
| `border-0` | Remove a borda        |



#### Borda em um lado específico

| Classe     | Lado aplicado |
| ---------- | ------------- |
| `border-t` | Superior      |
| `border-b` | Inferior      |
| `border-l` | Esquerdo      |
| `border-r` | Direito       |



#### Cor da borda

O Tailwind oferece classes de cores prontas para bordas:

```html
<div class="border-2 border-red-500"></div>
<div class="border-4 border-gray-300"></div>
```



#### Bordas arredondadas

As bordas podem ter cantos arredondados, controlados por classes:

| Classe         | Arredondamento                   |
| -------------- | -------------------------------- |
| `rounded`      | 4px (padrão)                     |
| `rounded-sm`   | 2px                              |
| `rounded-md`   | 6px                              |
| `rounded-lg`   | 8px                              |
| `rounded-xl`   | 12px                             |
| `rounded-2xl`  | 16px                             |
| `rounded-full` | 9999px (círculo)                 |
| `rounded-t-lg` | Apenas cantos superiores grandes |

<br />

> [!TIP]
>
> Você pode combinar largura, cor e arredondamento para criar botões, cartões e outros elementos estilizados rapidamente.

<br />

<h3>6.2. Sombras (Box Shadow)</h3>



As sombras criam profundidade nos elementos e ajudam a destacar conteúdo. O Tailwind possui classes prontas para sombras leves, médias ou intensas.

| Classe         | Descrição               |
| -------------- | ----------------------- |
| `shadow-sm`    | Sombra pequena          |
| `shadow`       | Sombra padrão (default) |
| `shadow-md`    | Sombra média            |
| `shadow-lg`    | Sombra grande           |
| `shadow-xl`    | Sombra extra grande     |
| `shadow-2xl`   | Sombra muito grande     |
| `shadow-inner` | Sombra interna          |
| `shadow-none`  | Remove a sombra         |

<br />

<h2>7. Layout</h2>



O Tailwind oferece **classes utilitárias poderosas** para controlar o layout de elementos, permitindo criar interfaces responsivas e organizadas sem escrever CSS adicional. Os dois sistemas principais de layout são **Flexbox** e **Grid Layout**.

<br />

<h3>7.1. Flexbox</h3>



O **Flexbox** permite organizar elementos em uma linha ou coluna e controlar como eles se comportam dentro de um container.

#### Container Flex

| Classe             | Descrição                             |
| ------------------ | ------------------------------------- |
| `flex`             | Define o elemento como container flex |
| `inline-flex`      | Flex container inline                 |
| `flex-row`         | Elementos dispostos em linha (padrão) |
| `flex-row-reverse` | Linha invertida                       |
| `flex-col`         | Elementos dispostos em coluna         |
| `flex-col-reverse` | Coluna invertida                      |



#### Alinhamento

| Classe            | Descrição                          |
| ----------------- | ---------------------------------- |
| `justify-start`   | Alinha itens à esquerda            |
| `justify-end`     | Alinha itens à direita             |
| `justify-center`  | Alinha itens ao centro horizontal  |
| `justify-between` | Espaço entre itens                 |
| `justify-around`  | Espaço ao redor dos itens          |
| `justify-evenly`  | Espaço uniforme entre itens        |
| `items-start`     | Alinha itens ao topo verticalmente |
| `items-center`    | Alinha itens no centro vertical    |
| `items-end`       | Alinha itens na parte inferior     |
| `items-stretch`   | Itens esticam verticalmente        |



#### Flex Grow, Shrink e Basis

| Classe         | Descrição                                 |
| -------------- | ----------------------------------------- |
| `flex-1`       | Item cresce para ocupar espaço disponível |
| `flex-auto`    | Item cresce e encolhe automaticamente     |
| `flex-initial` | Tamanho inicial definido                  |
| `flex-none`    | Item não cresce nem encolhe               |

<br />

<h3>7.2. Grid Layout</h3>



O **Grid Layout** permite organizar elementos em linhas e colunas, oferecendo maior controle sobre layouts complexos.

#### Container Grid

| Classe        | Descrição                             |
| ------------- | ------------------------------------- |
| `grid`        | Define o elemento como container grid |
| `inline-grid` | Grid container inline                 |
| `grid-cols-2` | 2 colunas                             |
| `grid-cols-3` | 3 colunas                             |
| `grid-cols-4` | 4 colunas                             |
| `grid-rows-2` | 2 linhas                              |
| `grid-rows-3` | 3 linhas                              |



#### Gaps

| Classe    | Descrição            |
| --------- | -------------------- |
| `gap-1`   | Gap de 0.25rem (4px) |
| `gap-2`   | Gap de 0.5rem (8px)  |
| `gap-4`   | Gap de 1rem (16px)   |
| `gap-x-4` | Gap horizontal       |
| `gap-y-4` | Gap vertical         |



#### Alinhamento

| Classe                 | Descrição                            |
| ---------------------- | ------------------------------------ |
| `justify-items-start`  | Alinha itens ao início horizontal    |
| `justify-items-center` | Alinha itens ao centro horizontal    |
| `justify-items-end`    | Alinha itens ao final horizontal     |
| `items-start`          | Alinha itens ao topo vertical        |
| `items-center`         | Alinha itens verticalmente no centro |
| `items-end`            | Alinha itens na parte inferior       |

<br />

> [!TIP]
>
> 1. Use **Flexbox** para layouts lineares simples (linhas ou colunas).
> 2. Use **Grid** quando precisar de layouts mais complexos com linhas e colunas.
> 3. Combine `gap`, `justify-*` e `items-*` para criar espaçamentos consistentes sem precisar de padding/margin extra.
> 4. Para responsividade, utilize os **prefixos de breakpoint**: `sm:`, `md:`, `lg:`, `xl:`, aplicando diferentes classes dependendo do tamanho da tela.

<br />

<h2>8. Pseudoclasses e Pseudoelementos</h2>



O **Tailwind CSS** permite aplicar estilos baseados em **estado do elemento** ou **partes específicas do elemento** usando **pseudo-classes** e **pseudo-elementos**, sem escrever CSS manual.

Esses utilitários são extremamente úteis para criar **interações visuais**, como hover, focus, active, além de efeitos como primeiro ou último filho, ou antes/depois de um elemento.

<br />

<h3>8.1. Pseudo-classes</h3>



As pseudo-classes aplicam estilos com base no **estado do elemento** ou **posição na árvore do DOM**.



#### Estados de interação

| Pseudo-classe Tailwind | Equivalente CSS | Uso típico                                       |
| ---------------------- | --------------- | ------------------------------------------------ |
| `hover:`               | `:hover`        | Aplica estilo ao passar o mouse                  |
| `focus:`               | `:focus`        | Aplica estilo ao focar o elemento (input, botão) |
| `active:`              | `:active`       | Aplica estilo quando o elemento é clicado        |
| `visited:`             | `:visited`      | Aplica estilo em links visitados                 |
| `disabled:`            | `:disabled`     | Aplica estilo em inputs desabilitados            |



#### Filhos e posições

| Pseudo-classe Tailwind | Equivalente CSS    | Uso típico                           |
| ---------------------- | ------------------ | ------------------------------------ |
| `first:`               | `:first-child`     | Aplica estilo ao primeiro filho      |
| `last:`                | `:last-child`      | Aplica estilo ao último filho        |
| `odd:`                 | `:nth-child(odd)`  | Aplica estilo em filhos ímpares      |
| `even:`                | `:nth-child(even)` | Aplica estilo em filhos pares        |
| `first-of-type:`       | `:first-of-type`   | Aplica estilo ao primeiro de um tipo |
| `last-of-type:`        | `:last-of-type`    | Aplica estilo ao último de um tipo   |

<br />

<h3>8.2. Pseudo-elementos</h3>



Os pseudo-elementos permitem aplicar estilos em **partes específicas do elemento**, como conteúdo antes ou depois do elemento.

<br />

#### Principais pseudo-elementos Tailwind

| Pseudo-elemento Tailwind | Equivalente CSS | Uso típico                           |
| ------------------------ | --------------- | ------------------------------------ |
| `before:`                | `::before`      | Adiciona conteúdo antes do elemento  |
| `after:`                 | `::after`       | Adiciona conteúdo depois do elemento |

> Observação: Para funcionar, o Tailwind precisa que você defina o **content** via utilitário `content-['texto']` ou em CSS customizado.

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>**Exemplo**

```jsx
<div className="relative before:content-['★'] before:absolute before:-left-4 before:text-yellow-400 p-4 border">
  Destaque com estrela antes do texto
</div>
```

- `before:content-['★']` → adiciona uma estrela antes do texto
- `before:absolute before:-left-4` → posiciona a estrela à esquerda do texto
- `before:text-yellow-400` → define a cor da estrela

<br />

<h2>9. Responsividade e Mobile-First com Tailwind</h2>



**Responsividade** é a capacidade de um site ou aplicação web se adaptar automaticamente a diferentes tamanhos de tela — como smartphones, tablets, notebooks e desktops — proporcionando uma boa experiência de uso em qualquer dispositivo.

**Exemplos de Dispositivos**

| Dispositivo       | Exibição esperada                      |
| ----------------- | -------------------------------------- |
| Celular (360px)   | Menu empilhado, texto menor            |
| Tablet (768px)    | Layout com duas colunas                |
| Desktop (1024px+) | Layout em três colunas, fontes maiores |

<br />

<h3>9.1. O que é o modelo Mobile-First?</h3>



**Mobile-first** é uma abordagem de desenvolvimento onde:

- Primeiro se cria o layout **para dispositivos móveis** (telas pequenas);
- Depois se adicionam **adaptações progressivas** para telas maiores (usando breakpoints).

O Tailwind segue a lógica **mobile-first por padrão**. Ou seja, qualquer classe **sem prefixo** é aplicada **em qualquer tela**, inclusive as menores.

Se você quiser que algo **mude** apenas em telas maiores, você usa os **breakpoints com prefixo**.

O Tailwind define os seguintes **breakpoints padrão** (min-width):

| Prefixo | Telas a partir de | Usado para...      |
| ------- | ----------------- | ------------------ |
| `sm:`   | ≥ 640px           | Celulares grandes  |
| `md:`   | ≥ 768px           | Tablets            |
| `lg:`   | ≥ 1024px          | Laptops pequenos   |
| `xl:`   | ≥ 1280px          | Laptops grandes    |
| `2xl:`  | ≥ 1536px          | Telas muito largas |

<br />

> [!IMPORTANT]
>
> Os **breakpoints não substituem o estilo base**, eles o complementam.

<br />

<img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>**Exemplo**

```html
<div class="text-sm md:text-lg xl:text-2xl">
  Texto responsivo
</div>
```

### Como interpretar:

- `text-sm`: estilo padrão (mobile);
- `md:text-lg`: em telas ≥ 768px, o texto aumenta;
- `xl:text-2xl`: em telas ≥ 1280px, o texto fica ainda maior.

