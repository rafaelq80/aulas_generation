<h1>Responsividade</h1>



Com o crescente uso da internet por meio de dispositivos móveis com diferentes tamanhos de tela, ter um design de site estático que funcione corretamente apenas em computadores tornou-se inviável nos dias de hoje.

Desenvolver um design responsivo e adaptável a diversos tipos e tamanhos de dispositivos é essencial para garantir que o site ofereça uma experiência visual e funcional de qualidade em celulares, tablets, laptops e desktops.

Vale destacar que essa melhoria na experiência do usuário pode resultar em maiores taxas de conversão e contribuir significativamente para o crescimento dos negócios.

<br />

<h2>1. O que é Web Design Responsivo?</h2>



O Design Responsivo é uma abordagem no web design que permite que o conteúdo de um site se ajuste automaticamente aos diversos tamanhos de tela e janelas de diferentes dispositivos.

Por exemplo, em telas de desktop, o conteúdo pode ser exibido em várias colunas, aproveitando o espaço mais amplo. No entanto, se esse mesmo layout de múltiplas colunas fosse aplicado a um dispositivo móvel, a leitura e a navegação se tornariam difíceis para os usuários.

Com o design responsivo, é possível oferecer diferentes versões de layout para variados dispositivos, garantindo uma adaptação que mantém a consistência visual e melhora a experiência de uso.

<br />

<h3>1.1. Por que o Design Responsivo é tão importante?</h3>



A resposta é mais simples do que parece: Não é suficiente projetar um site para um único dispositivo. O tráfego da web móvel ultrapassou a área de trabalho e agora constitui a maior parte do tráfego de um site, representando mais de 51% dos acessos.

Quando mais da metade de seus visitantes potenciais está usando um dispositivo móvel para navegar na Internet, você não pode simplesmente servir-lhes uma página projetada para a área de trabalho. Seria difícil de ler e usar, e levaria a uma má experiência do usuário.

<br />

<h3>1.2. Como criamos a Responsividade com CSS?</h3>



Para que o conteúdo e o layout de um site se adaptem a diferentes tamanhos de tela, utiliza-se uma técnica chamada media query (consulta de mídia). As media queries são instruções em CSS que permitem aplicar estilos específicos com base em certas características do dispositivo, como largura, altura e orientação da tela. Com elas, o desenvolvedor consegue definir estilos distintos para cada tipo de dispositivo, otimizando o design de forma automática.

Na prática, a consulta de mídia funciona de forma semelhante a um Laço Condicional "if”, presente na maioria das linguagens de programação, que verifica se a janela de visão de uma tela é suficientemente ampla ou muito ampla antes de executar o código apropriado.

**Exemplo:**

```css
/* Estilos gerais para todos os dispositivos */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

/* Estilos específicos para dispositivos com largura até 768px (tablets e smartphones) */
@media (max-width: 768px) {
  body {
    font-size: 16px;
  }

  .container {
    flex-direction: column; /* Adapta o layout para uma coluna em telas menores */
  }
}

/* Estilos específicos para dispositivos com largura acima de 768px (desktops) */
@media (min-width: 769px) {
  body {
    font-size: 18px;
  }

  .container {
    flex-direction: row; /* Aplica um layout em linha para telas maiores */
  }
}
```

Neste exemplo, a media query aplica estilos diferentes de acordo com a largura da tela:

- Para telas de até 768px (tablets e smartphones), o layout é ajustado para uma única coluna e um tamanho de fonte menor, tornando-o mais legível.
- Para telas maiores (desktops), o layout assume um formato em linha com um tamanho de fonte ligeiramente maior, aproveitando o espaço disponível.

<br />

<h2>2. Pontos de Interrupção (Breakpoints)</h2>



Os **pontos de interrupção** (ou *breakpoints*, em inglês) são os valores de largura ou altura da tela nos quais as media queries entram em ação para alterar o layout e os estilos de um site, conforme necessário para otimizar a experiência do usuário em diferentes dispositivos.

Em resumo, os pontos de interrupção são divisores estratégicos que separam o layout de um site em diferentes versões para se adaptar melhor a cada tipo de dispositivo, como smartphones, tablets e desktops.

<br />

<h3>2.1. Como Funcionam os Pontos de Interrupção</h3>



Os pontos de interrupção funcionam especificando condições em CSS para quando o layout do site deve se ajustar. Quando a largura ou altura de um dispositivo atinge ou ultrapassa determinado valor, a media query correspondente é ativada, aplicando estilos específicos para aquele tamanho de tela.

**Exemplo:**

- Um layout de três colunas pode funcionar bem em um desktop, mas em telas menores (como smartphones), essas colunas podem ser empilhadas verticalmente para melhorar a legibilidade.
- O ponto de interrupção pode ser definido para que, quando a largura da tela for igual ou menor que 768px, o layout passe de três colunas para uma coluna, com cada item ocupando 100% da largura da tela.



<h3>2.2. Escolha dos Pontos de Interrupção</h3>



Os pontos de interrupção podem ser definidos com base no comportamento do conteúdo e no perfil do público-alvo do site. Embora não exista uma regra fixa, alguns breakpoints são amplamente utilizados como referência. Na imagem abaixo, destacamos três dos breakpoints mais comuns:

<div align="center"><img src="https://i.imgur.com/wJPKEgY.png" title="source: imgur.com" /></div>

<br />

<h2>3. Tornando o Site Responsivo</h2>



Vamos adicionar algumas regras CSS no nosso arquivo **style.css**, utilizando as media queries, com o objetivo de ajustar o nosso layout de acordo com o tamanho da tela.

<br />

<h3>3.1. A Palavra Reservada @media</h3>



A sintaxe da media query no CSS segue uma estrutura que permite aplicar estilos específicos de acordo com as características do dispositivo ou janela onde o site está sendo visualizado, como largura, altura, orientação, resolução, entre outros.

A estrutura básica de uma media query é a seguinte:

```css
@media (condição) {
  /* Declarações CSS aplicadas quando a condição é atendida */
}
```

**Onde:**

- A palavra-chave @media inicia uma consulta de mídia e sinaliza ao navegador que os estilos dentro dela devem ser aplicados apenas se as condições especificadas forem atendidas.
- Dentro dos parênteses, definimos as condições que o dispositivo ou a janela devem atender para que os estilos sejam aplicados. A condição mais comum é baseada na largura da tela (max-width ou min-width), mas também é possível usar outras condições, como altura, orientação (paisagem ou retrato), resolução, entre outras.
- Dentro das chaves { }, são incluídas as regras CSS que serão aplicadas apenas se a condição for verdadeira.

<br />

<div align="left"><img src="https://i.imgur.com/7IdCTXz.png" title="source: imgur.com" width="4%"/> <a href="https://www.w3schools.com/cssref/atrule_media.php" target="_blank"><b>Documentação: CSS - @media</b></a></div>

<br />

<h2>4. Visualizar o Site Responsivo no Navegador</h2>



Durante a criação das regras CSS para responsividade, é essencial visualizar o resultado em diferentes tamanhos de tela para garantir uma experiência consistente em diversos dispositivos. 

Os navegadores modernos possuem ferramentas nativas para visualizar sites em diferentes tamanhos de tela. No entanto, algumas extensões oferecem uma simulação mais precisa da experiência em dispositivos como smartphones e tablets, além de permitir capturas de tela diretamente no navegador.

Uma dessas extensões é o **Responsive Viewer**, disponível para os navegadores **Chrome** e **Edge**. Você pode adicioná-la ao seu navegador pelo link abaixo:

<br />

<div align="left"><img src="https://i.imgur.com/8WmU71z.png" title="source: imgur.com" width="4%"/><a href="https://chromewebstore.google.com/detail/responsive-viewer/inmopeiepgfljkpkidclfgbgbmfcennb" target="_blank"><b>Responsive Viewer for Chrome</b></a></div>

<br />

Vamos testar a Responsividade:

1. Abra a página index com o **Live Server**

<div align="center"><img src="https://i.imgur.com/arWoT6i.png" title="source: imgur.com" /></div>

2. Clique na extensão <img src="https://i.imgur.com/DF4MnC1.png" title="source: imgur.com" width="5%"/> **Responsive Viewer** e clique na guia **Mobile**.
3. Na sequência, clique no botão <img src="https://i.imgur.com/qPpJcT9.png" title="source: imgur.com" width="5%"/>**Toggle Mockups** para emular a tela do Smartphone.
4. O resultado será semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/upzFjeC.png" title="source: imgur.com" /></div>

5. Para visualizar nos Tablets, clique na guia **Tablet**
6. Nas imagens abaixo, podemos ver o site aberto nos Smartphones:

<div align="center"><img src="https://i.imgur.com/VRvlEqW.png" title="source: imgur.com" /></div>

7. Nas imagens abaixo, podemos ver o site aberto nos Tablets:

<div align="center"><img src="https://i.imgur.com/qtZXBqN.png" title="source: imgur.com" /></div>

Observe que foram efetuadas algumas mudanças em relação a disposição dos elementos na tela, margens, espaçamentos, entre outros ajustes. Na prática é o processo de ajustar as regras do CSS, de acordo com o tamanho da tela.

<br /><br />
