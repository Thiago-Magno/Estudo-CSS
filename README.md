# Estudos CSS

Neste repositório contem anotações e alguns trechos de como funcionam algumas coisas de CSS, talvez não tenha algo em especicifico porque eu já estudei CSS antes e nesta parte vai ter coisas como child, combinators e pseudo-classe e mais coisas para frente conforme eu for estudando. 

## Seletores

Conecta um elemento HTML com o CSS a fim de alterar o elemento.

### Tipos

- Element selector
    * Todos os elementos HTML
    * Forma de chamar no css
    ```css
    body{

    }
    ```
- ID Selector
    * Um elemento que tenha o atributo `id`.
    * Cada `id` deverá ser único.
    * Forma de chamr no css:
    ```css
    #subtitle{
        
    }
    ```
- Class Selector
    * Os elementos que contenha um atributo `class`.
    * Podemos ter uma ou mais classes.
    * Forma de chamar no CSS:
    ```css
    .card{
        
    }
    ```
- Atribute Selector
    * Um elemento que tenha um atributo especifico.
    * Forma de chamar no CSS:
    ```css
    [title]{
        
    }
    ```
    * Neste chama um elemento com o atributo `title`
 
      
- Pseudo-class selector
    * Elementos em um estado especifico.
    * Forma de chamar no CSS:
    ```css
    p:hover{
        
    }
    ```

### Múltiplos

É possivel selecionar múltiplos elementos e aplicar alguma regra CSS para todos eles.

Usamos uma separação por vírgulas para isso.

```css
    h1, p, a{
        color: #001244
    }
```

## Combinators

Combinadores, pois eles buscam e combinão seletores a fim de aplicar uma estilização

### Descendent combinator

- Identificação por um espaço entre os seletore;
- Busaca um elementos dentro de outro elemento.

```css
    body article section h2{
        color #002255
    }    
```

### Child combinator

- Identficado pelo sinal de `>` entre dois seletores
- Seleciona somente o elemento que é filho direto do pai
- Elementos depois do filho direto serão desconsiderado

```css
    body > header > nav > ul > li{
        color #002255
    }    
```

### Adjacent siblig combinator

- Identificação pelo sinal `+` entre dois seletores
- Seleciona somente o elemento que é irmão direto na hierarquia
```css
    h2 + p{ 
        color #002255
    }    
```


### General sibling selector

- Identificado pelo `~` entre dois seletores;
- Seleciona todos os elementos irmãos.
```css
    h2 ~ p{
        color #002255
    }    
```

### Utilizando combinadores

```css
    ul > li[class="red"]{
        color #002255
    }    
```
### Dica
- Seletores muito especificos tendem a causar dificuldade no reuso das regras de estilização dos elementos;
- Muitas vezes, um simples uso de classes, torna o trabalho muito mais eficiente.

## Pseudo-Classes

É um tipo de seletor que íra selecionar um elemento que estiver em um estado específico.
Como por exemplo o primeiro elemento dentro de uma caixa, ou o elemento que está com o ponteiro do mouse em cima dele.

Pseudo-classes começam com o sinal de `:` seguido do nome da pseudo classe: `:pseudo-calsse-name`

### Selecionando elementos com pseudo-classes

- `:first-child`
    * Pega o primeiro filho dentro da caixa e aplica uma estilização a ele, caso o primeiro filho não seja do tipo especificado a estilização não é aplicada;
    ```css
    ul > li:first-child {
        color #002255
    }    
    ```  

- `:nth-of-type()`
    * Neste tipo ele pega entre os tipos de elemento que você esta procurando e após selecionado dentro do parenteses `nth-of-type( )` em qual ele aplicara a estilização;
    ```css
    article p:nth-of-type(1){
        color #002255
    }    
    ```
- `nth-child`
    * Este segue um principio parecido com o first-child mas é necessario selecionar qual filho tem que receber a estilização dentro do parenteses, e assim como no first child ele conta os elementos dentro da caixa do primeiro ao ultimo como filho então se o `p` não for o primeiro basta contar e ver qual filho ele é e colocar o numero correspondente;
    ```css
    article p:nth-child(1){
        color #002255
    }    
    ```
    * Tambem é possivel aplicar estilização dependendo se o index de cada for impar ou par com o `odd` e `even`  

### Ações do usuario

- `:hover` faz com que seja aplicado um estilo caso o mouse passe por cima, vale notar que os diposistivos mobile não tem hover já que este não tem como passa o indicado por cima
    ```css
    button:hover(1){
        color #fff
    }    
    ```
- `:focus` é mais para campo que receberam um tipo de texto, assim quando selecionados/ativos eles podem trocar a estilização, como quando tocamos em um campo de email e ele aparece um pouco mais brilhante ou com uma borda diferente

### Atributos

- `:disabled` serve para quando um campo/elemento estiver recebendo o atributo de `disabled` nos podemos mudar o seu estilo 
-  `:required` é o mesmo caso do `:disabled`

Referencia para mais estudo: (https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

## Pseudo-elements

Se comporta parecido com os pseudo-classes, com ele podemos adicionar elemento HTML pelo proprio CSS

`::pseudo-element-name`

### Exemplos

- `::before` é necessario o `content:"<conteudo>"` para funcionar, adiciona um conteudo **antes** do elemento HTML;
- `::after`é necessario o `content:"<conteudo>"` para funcionar, adiciona um conteudo **depois** do elemento HTML;
- `::first-line` aplica a estilização apenas a primeira linha do texto.

**Referência:** https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements

## Layouts

Layout é como os elementos estão distribuidos na tela, a seguir algumas linhas com a evolução dos layouts.

### Normal flow
É a maneira que os elementos `block` e `inline` ficam na pagina

```html
    <p>Texto block com <strong>inline</strong> dentro</p>

```

### Tables

É a maneira de tabela onde a tag `table` recebe um display `table` fazendo com que os elementos internos como o `td` e `tr` possam ser usados para montar uma tabela

```html
    <table>
        <th>Tempo</th>
        <tr>
            <td>Hora</td>
            <td>20:00</td>    
        </tr>
        <tr>
            <td>Hora</td>
            <td>22:00</td>    
        </tr>
    </table>

```
### Tabless

Uso da propriedade `float`, `clear` para que os elementos possam mudar de posição na tela.

```html
    <div style="float:left">
        esquerda
    </div>

```

### Flexbox

A caixa se torna flexivel, fazendo com que os elementos internos possam recebem melhor:

- Alinhamento
- Ordenação
- Tamanhos flexíveis

## Teminologia

- Flex container: é o container que contem os itens dentro de si
    *  Flex item
- Nesting: é um conceito onde um elemento vive dentro de outro elemento
- Axis: é o eixo do conteiner, quando aplicamos o `display:flex` o eixo pode mudar dependendo dos atributos que colocarmos por padrão o eixo é na na horizontal, mas com o `flex-direction:column` podesse muda-lo para vertical
    * main: eixo principal
        * start, end
    * cross: eixo cross
        * start, end
- Flex sizing
    * Flexivel
    * Altera width/height dos itens para preenchimento dos espaços do flex container

## Propriedades do Flex Container

- Direção dos itens
    * a direção dos itens flex são em uma direção(horizontal/vertical)
    * valores:
        - row
        - row-reverse
        - column
        - column-reverse
- Multi linhas
    * `flex-wrap` cria novas linha se for necessario
- Flex Flow: `flex-flow` possibilita utiliza varias das propriedades acima como em um short hand
- Alinhamento
    * Principal:
        - `justify-content` alinha os elementos dentro do container e faz a distribuição dos elementos
        - `flex-start` posiciona os itens no começo do eixo proncipal
        - `flex-end` posiciona os itens no final do eixo principal
        - `center` alinha todos os itens no centro do container
        - `space-around` adiciona um espaçamento em volta dos itens 
        - `space-between` adiciona um espaço entre os itens
        - `space-evenly` coloca um espaçamento igual no itens
    * Cruzado/ `align-items`
        - `stretch` é por padrão do flex feito ele estica o itens 
        - `flex-start`alinha no começo do eixo cruzado
        - `flex-end`alinha no final do eixo cruzado
        - `center` alinha no meio do eixo cruzado
- Espaços entre os itens/`gap`
    * valores:
        - Unidades de medida
        - fixas: px, pt
        - flexiveis: %, em, rem

## Propriedades dos itens

- `flex-basis:`
    * Pega o tamanha do elemento e ajusta ao tamanho do conteudo automaticamente
    * O valor do tamanha muda de acordo com o eixo principal
    * No caso de ele estar no comportamento padrão ele toma posse da propriedade de largura do elemento
    * No caso de ele estar no comportamento `column` ele toma posse da propriedade de altura do elemento
    * Recebe os mesmos valores do height e width: px, em, pt, rem e %
    * Fixa um tamanho em relação a os outros elementos
- `flex-grow`
    * É flexivel em relação a os outros elementos
    * O crescimento do item dentro do conteiner em relação aos espaços vazios
    * Esse atributo é dividido em frações de um espaço vazio, por exemplo quando atribuimos o numero 1 ele divide esse esáço vazio em uma fração,
     logo, fazendo com que o elemento ocupe todo o espaço vazio. Caso coloque 1 fração para 2 elementos ele dividiria o espaço vazio em duas frações de um.
    * Caso ocorra uma inversão de eixo ele faz o crescimento em altura.  
- `flex-shrink` 
    * Já é aplicado por padrão, mas pode ser removido usando o valor `0` quando removido o conteudo vaza da caixa
    * quando o valor é acima de `1` ele enconlhe o(s) elemento(s) selecionados e faz uma aumento dos outros  
- `flex`
    * é o shorthand para utilizar o `flex-grow`, `flex-shrink` e `flex-basis` em uma linha só
    * podem ter 1,2 ou os 3 valores

### Ordenando itens

Podemos usar a propriedade `order` pra mudar a posição dos elemento sem ter q mexer no `html`. 

## Exercicios

### Header Menu Navigation

* Crie o `<header>` de um site que tenha uma logo e um menu.
* Um elemento deverá focar ao lado do outro;
* A logo que ficará na extrema esquerda e o menu ficara na extrema direita;
* Os itens do menu ficarão um ao lado do outro, com um espaço de `.8rem` entre eles;
* O último elemento do menu será um botão de contato e você poderá utilizar o seletor `:last-child` para estilizar.
Solução:
![](./Header-nav-menu/solucaoHeader.png)

### 2 Columns Layout

* Crie um layout com dua colunas, uma ao lado da outra;
* A coluna da esquerca deverá ter `25%` de tamanho e a da direita deverá opupar todo o espaço que sobra;
* Faça uma separação de `1rem` entre os elementos.
Solução:
![](./2-Columns-Layout/solucaoColumn.png)
### 9 Fotos em 3 colunas

* Crie uma galeria de fotos onde teremos 3 colunas e 9 fotos
* deixe um espaço de `.8rem` entre os elementos
### Imagem dentro do botão

* Crei um botão que contenha um ícone(img) e um texto
* coloque um espaço de .4rem entre os elementos
![](./Button-image/solucaoBtn.png)
### Footer

* Crie um `<footer>` de um site que contenha a data de criação do site;
* Usando flex, alinhe o elemnto do futter bem ao meio;
* Deixe uma altura de 8rem para o footer;
* O footer deverá ficar no final da página.
![](./Footer/solucaoFooter.png)
