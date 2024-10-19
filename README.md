
![Logo](https://sass-lang.com/assets/img/logos/logo.svg)


# SASS - Guia Completo

#### Este guia abrange o uso e as funcionalidades do SASS (Syntactically Awesome Stylesheets), um pré-processador CSS que facilita a criação de estilos escaláveis e organizados. Com SASS, é possível utilizar variáveis, aninhamento, mixins, herança e outras funcionalidades que otimizam o desenvolvimento e a manutenção de projetos frontend.

### Esta documentação fornece:

- **Introdução ao SASS**: O que é e como funciona.
- **Configuração e Instalação**: Como começar a usar SASS no seu projeto.
- **Sintaxe SCSS e SASS**: Diferenças e exemplos práticos.
- **Funcionalidades Avançadas**: Mixins, herança, loops, funções e condicionais.
- **Melhores Práticas**: Estruturação de estilos para projetos escaláveis.
- **Ferramentas e Integração**: Uso com extensão VSCode e Sass + Nextjs + React.


## Sumário
1. [Introdução](#1---introdução)
2. [Instalação e Configuração](#2---instalação-e-configuração)
3. [Variaveis](#3---variaveis)
4. [Seletores CSS](#4---seletores-css)
5. [Partials e Importações](#5---partials-e-importações)
6. [Mixin](#6---mixin)
7. [Extend e Herança](#7---extend-e-Herança)
8. [Operadores e Condicionais](#8---operadores-e-condicionais)
9. [Mapas e Listas](#9---mapas-e-listas)
10. [Loops e Estruturas Repetitivas](#10---loops-e-estruturas-repetitivas)
11. [Funções Internas](#11---funções-internas)
12. [Responsividade](#12---responsividade)
13. [Debug e Erros](#13---debug-e-erros)
## 1 - Introdução

O SASS (Syntactically Awesome Stylesheets) é um pré-processador CSS que estende a funcionalidade do CSS tradicional, trazendo mais poder e organização para os estilos. Ele permite utilizar recursos como variáveis, aninhamento de seletores, mixins (blocos reutilizáveis de código), herança, e funções matemáticas, facilitando a escrita e a manutenção de folhas de estilo, especialmente em projetos de grande escala.

### Por que SASS é Melhor que CSS?
Embora o CSS seja essencial para estilizar páginas web, ele apresenta algumas limitações quando se trata de organização e reutilização de código. O SASS foi projetado para resolver essas limitações. Aqui estão algumas razões pelas quais o SASS é considerado melhor que CSS:

### SASS vs SCSS
O SASS e o SCSS são duas sintaxes diferentes para escrever estilos no mesmo pré-processador.

#### SASS (Indentação):

- Não usa chaves {} nem ponto e vírgula ;.
- Sintaxe mais enxuta e inspirada em Python.
- Ideal para quem prefere códigos limpos e menos verbosos.

```sass
nav
  ul
    margin: 0
    li
      display: inline-block

```

#### SCSS (Sassy CSS):

- Usa chaves {} e ponto e vírgula ; como no CSS tradicional.
- É uma sintaxe mais próxima do CSS, facilitando a adoção para quem já está acostumado com CSS puro.

```scss
nav {
  ul {
    margin: 0;
    li {
      display: inline-block;
    }
  }
}
```

### Qual Usar?
- Se você já está acostumada com CSS tradicional, o SCSS é uma escolha natural, pois a sintaxe é quase idêntica.
- Se prefere uma abordagem minimalista e gosta de trabalhar com indentação, a sintaxe SASS pode ser mais adequada.
## 2 - Instalação e Configuração

### Instalação Comum
- 1 = Instalar a extensão no VS Code → **Live Sass Compiler**
- 2 = Crie um arquivo SASS e um CSS (devem ter o mesmo nome). Exemplo: style.scss e style.css
- 3 = Escrever o código no arquivo SASS e aperte em **Watch SASS** na barra inferior, para compilar o arquivo para o style.css.
- **OBS** = escolha apenas uma pasta para colocar no Watch SASS, pois se tiver vários outros projetos, vão ser gerados vários arquivos SASS neles. 

###  Instalação Nextjs/React
- 1 = npm i sass
- 2 = dentro da pasta src, crie uma pasta e arquivo **styles/settings.module.scss**
```scss
@import url('https://fonts.googleapis.com/css2?family=Afacad+Flux:wght@100..1000&family=Montserrat:ital,wght@0,100..900;1,100..900&family=Open+Sans:ital,wght@0,300..800;1,300..800&display=swap');

$primary-color: #4868ff;
$secoundary-color: #0fadff;

$font-primary: "Open Sans", sans-serif;
$font-secoundary: "Afacad Flux", serif;
$font-terciary: "Montserrat", sans-serif;
```
- 3 = estilizando componente

#### styles.module.scss
```scss
@import '/src/styles/settings.module.scss';

.cabecalho{
	border: 1px solid red;

	.titulo{
		font-family: $font-primary;
	}
}
```

#### index.tsx (coloque só classe e id)
```tsx
import styles from "./styles.module.scss";

export default function Header(){
	return (
		<header className={styles.cabecalho}>
			<h1 className={styles.titulo}>
				Olá
			</h1>
		</header>
	)
}
```
## 3 - Variaveis

O Sass permite o uso de variáveis, facilitando a reutilização de valores como cores, tamanhos e fontes em todo o projeto. Isso melhora a organização e a consistência dos estilos. Abaixo, vou mostrar como você pode usar variáveis no Sass.

### Criando Variáveis no Sass
As variáveis no Sass começam com o símbolo $. Um arquivo de variáveis geralmente é criado para facilitar a manutenção.

#### Cores
```scss
$primary-color: #4caf50;
$secondary-color: #2196f3;
$text-color: #333;
```

##### Espaçamento
```scss
$padding: 10px;
$margin: 15px;
```

#### Tamanhos
```scss
$border-radius: 5px;
```
## 4 - Seletores CSS

### Aninhamento

O aninhamento no Sass permite que você organize o CSS de forma hierárquica, simulando a estrutura HTML. Isso evita a repetição de seletores.

#### SASS:
```scss
.navbar {
	background-color: #333;
	padding: 10px;

	ul {
		list-style: none;
		display: flex;

		li {
			margin-right: 15px;

			a {
				text-decoration: none;
				color: white;

				&:hover {
					color: lightgray;
				}
			}
		}
	}
}
```

#### CSS:
```css
.navbar {
	background-color: #333;
	padding: 10px;
}

.navbar ul {
	list-style: none;
	display: flex;
}

.navbar ul li {
	margin-right: 15px;
}

.navbar ul li a {
	text-decoration: none;
	color: white;
}

.navbar ul li a:hover {
	color: lightgray;
}
```

#### Como funciona:
- O Sass permite aninhar seletores, evitando repetição e tornando o código mais organizado.
- O & é um atalho para referenciar o seletor pai (útil para pseudo-classes como :hover)

### Seletores de Referência (&)
O & no Sass é uma forma de referenciar o seletor pai dentro de um bloco aninhado. Ele é útil para criar pseudo-classes, pseudo-elementos ou modificadores de classe.

#### SASS: 
```scss
.button {
	background-color: #4caf50;
	color: white;

	&:hover {
		background-color: darkgreen;
	}

	&.active {
		background-color: #2196f3;
	}
}
```

#### CSS: 
```css
.button {
	background-color: #4caf50;
	color: white;
}

.button:hover {
	background-color: darkgreen;
}

.button.active {
	background-color: #2196f3;
}
```

### Seletores de Atributo
Assim como no CSS, você pode usar seletores de atributo no Sass para aplicar estilos a elementos com atributos específicos.

#### SASS: 
```scss
input[type="text"] {
	border: 1px solid #ddd;
	padding: 5px;

	&:focus {
		border-color: #4caf50;
	}
}
```

#### CSS: 
```css
input[type="text"] {
	border: 1px solid #ddd;
	padding: 5px;
}

input[type="text"]:focus {
	border-color: #4caf50;
}
```

### @extend: Compartilhamento de Estilos Entre Seletores
O @extend permite que você compartilhe estilos entre seletores diferentes. Isso evita repetição de código.

#### SASS
```scss
.button {
	padding: 10px 20px;
	border-radius: 5px;
	background-color: #4caf50;
	color: white;
}

.submit-button {
	@extend .button;
	background-color: #2196f3;
}
```

#### CSS
```css
.button, .submit-button {
	padding: 10px 20px;
	border-radius: 5px;
	background-color: #4caf50;
	color: white;
}

.submit-button {
	background-color: #2196f3;
}
```

O @extend copia os estilos de um seletor para outro, evitando duplicação.
É útil quando você quer que dois seletores compartilhem grande parte dos mesmos estilos.

### Seletores Combinados (Hierárquicos)
Você pode combinar seletores no Sass para aplicar estilos a elementos específicos.

#### SASS
```scss
.card1 {
    + .card1 {
	    margin-top: 20px;
    }
}

.card2 {
    ~ .card2 {
	    margin-top: 20px;
    }
}
```

#### CSS
```css
.card1 + .card1 {
    margin-top: 20px;
}

.card2 ~ .card2 {
    margin-top: 20px;
}
```

- **+** Aplica estilo ao próximo irmão imediato.
- **>**: Aplica estilo apenas ao filho direto do elemento pai.

### Seletores de Pseudo-Classe e Pseudo-Elemento
Você pode aninhar pseudo-classes e pseudo-elementos para manter o código limpo.

#### SASS: 
```scss
a {
	color: blue;

	&:hover {
		text-decoration: underline;
	}

	&::after {
		content: " →";
	}
}
```

#### CSS: 
```css
a {
	color: blue;
}

a:hover {
	text-decoration: underline;
}

a::after {
	content: " →";
}
```

## 5 - Partials e Importações
No SASS, partials e importações são essenciais para manter o código organizado e modular, especialmente em projetos maiores. Eles ajudam a dividir estilos em arquivos menores e mais gerenciáveis que, ao serem importados, são combinados em uma única folha de estilo final.

### 5.1 - Partials no SASS
Um partial é um arquivo SASS que contém uma parte do CSS (como variáveis, mixins ou estilos de componentes) e não é compilado diretamente em um CSS separado. Em vez disso, ele é importado em um arquivo principal que reunirá todos os estilos.

#### Como nomear um Partial?
Por convenção, um partial é nomeado com um underscore (_) no início, indicando que esse arquivo não será processado como CSS por si só.

#### Exemplo de Arquivo Partial (_variables.scss): 
```scss
// Variáveis definidas em um partial
$primary-color: #3498db;
$secondary-color: #2ecc71;
$padding-base: 10px;
```

#### Por que usar Partials?
- Modularidade: Divide o código em partes lógicas (como variáveis, mixins, ou componentes específicos).
- Reutilização: Estilos podem ser usados em diferentes partes do projeto.
- Melhor Manutenção: Facilita a leitura e a modificação do código.

### 5.2 - Importações no SASS
No SASS, o comando **@import** permite combinar múltiplos arquivos SASS em uma única folha de estilo final. Ao usar **@import**, todos os estilos de arquivos importados são compilados juntos no arquivo principal.

#### Exemplo de Arquivo Principal (styles.scss):
```scss
// Importação de partials no arquivo principal
@import 'variables';
@import 'mixins';
@import 'base';
@import 'components/buttons';
```

#### Como funciona a Importação de Partials?
- O underscore e a extensão não são necessários na importação. Por exemplo, @import 'variables' importa o _variables.scss.
- O SASS automaticamente combina todos os arquivos importados em uma única folha de estilo na compilação.

### 5.3 - Organizando o Projeto com Partials e Importações
Aqui está uma estrutura comum de pastas para organizar um projeto com SASS:
```
/scss
│
├── _variables.scss
├── _mixins.scss
├── _base.scss
├── components/
│   ├── _buttons.scss
│   └── _navbar.scss
└── styles.scss
```

#### No arquivo styles.scss, você pode importar todos os partials:
```scss
@import 'variables';
@import 'mixins';
@import 'base';
@import 'components/buttons';
@import 'components/navbar';
```

### 5.4 - @import vs @use vs @forward
O SASS introduziu recentemente **@use** e **@forward** para substituir o **@import**. O **@use** e **@forward** resolvem alguns problemas do antigo sistema de importações:

#### 5.4.1 - @import (Depreciado)
- Importa um arquivo SASS e o mescla no arquivo atual.
- Não fornece isolamento de escopo, o que pode causar conflitos de variáveis e mixins.

```scss
@import 'variables';
@import 'mixins';

body {
  background-color: $primary-color;
}
```

#### Problemas com @import:
- Arquivos podem ser importados várias vezes acidentalmente.
- Conflitos entre variáveis e mixins, pois tudo é adicionado ao mesmo escopo global.
- Por esses motivos, o @use e o @forward foram introduzidos.

#### 5.4.2 - @use (Recomendado)
- Importa o conteúdo como um namespace (escopo fechado).
- Evita conflitos de nomes, já que você precisa referenciar variáveis e mixins com o nome do arquivo importado.
- Importa o arquivo apenas uma vez, mesmo que seja chamado em vários lugares.

#### Exemplo:
```scss
// _variables.scss
$primary-color: #3498db;
$secondary-color: #2ecc71;
```
```scss
// styles.scss
@use 'variables';

body {
  background-color: variables.$primary-color;
}
```

#### Modificando o Namespace com as
Renomeando o Namespace (as)
Se você acha que o nome original do arquivo é muito longo, pode dar um nome mais curto usando as:

```scss
@use 'variables' as var;

body {
  background-color: var.$primary-color;
}
```

#### Removendo o Namespace com as *
Você pode usar as * para importar todo o conteúdo diretamente, sem precisar de um namespace:

```scss
@use 'variables' as *;

body {
  background-color: $primary-color;
}
```

⚠️ Atenção: Usar as * pode ser conveniente, mas perde-se o isolamento de escopo, o que pode levar a conflitos de nomes, especialmente em projetos maiores.


#### Vantagens do @use:
- Escopo controlado e seguro (evita conflitos de nomes).
- Facilita a manutenção de estilos em projetos grandes.
- Importa arquivos apenas uma vez.

#### 5.4.3 - @forward
- Reexporta o conteúdo de outro arquivo.
- Permite criar pontos centralizados para importar vários arquivos de forma modular.
- Usado junto com @use para uma organização mais eficiente.

#### Exemplo:
```scss
// _variables.scss
$primary-color: #3498db;
$secondary-color: #2ecc71;
```
```scss
// _index.scss
@forward 'variables';
```
```scss
// styles.scss
@use 'index' as vars;

body {
  background-color: vars.$primary-color;
}
```

#### Vantagens do @forward:
- Cria pontos de entrada que reexportam vários arquivos de uma vez.
- Facilita a organização e reutilização em projetos grandes.
- Permite ocultar partes do código com a palavra-chave hide.


## 6 - Mixin
O mixin em Sass é uma maneira poderosa de reutilizar blocos de código CSS em vários lugares. Ele é parecido com uma função: você define o mixin com o código CSS desejado e depois o "chama" onde precisar. Mixins ajudam a manter o código limpo e evitam repetição, especialmente quando você tem muitos estilos semelhantes.

#### Sintaxe Básica:
```scss
// Sass
@mixin borda-arredondada {
	border: 1px solid #ddd;
	border-radius: 8px;
	padding: 10px;
}

.card {
	@include borda-arredondada;
	background-color: #f9f9f9;
}
```

```css
// Resultado CSS
.button {
	@include borda-arredondada;
	background-color: #4caf50;
	color: white;
}
```

#### Mixin com Parâmetros:
```scss
// Sass
@mixin displayFlex($direction, $wrap, $justify_content, $align_items, $gap){
	display: flex;
	flex-direction: $direction;
	flex-wrap: $wrap;
	justify-content: $justify_content;
	align-items: $align_items;
	gap: $gap;
}

body{
	@include displayFlex(row, nowrap, center, center, 2rem);
}
```

```css
// Resultado CSS
body {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: center;
	align-items: center;
	gap: 2rem;
}
```

#### Mixin com Parâmetros Opcionais:
```scss
// Sass
@mixin sombra($x: 0px, $y: 0px, $blur: 5px, $color: rgba(0, 0, 0, 0.5)) {
	box-shadow: $x $y $blur $color;
}

.card {
	@include sombra(2px, 2px);
}

.button {
	@include sombra(0px, 4px, 10px, rgba(0, 0, 0, 0.8));
}
```

```css
// Resultado CSS
.card {
	box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
}

.button {
	box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.8);
}
```

#### Mixin com Conteúdo Dinâmico:
Você pode criar mixins que aceitam blocos de código dinâmicos usando @content.

```scss
// Sass
@mixin destaque {
	background-color: yellow;
	padding: 10px;

	@content;
}

div {
	@include destaque {
		border: 1px solid black;
	}
}
```

```css
// Resultado CSS
div {
	background-color: yellow;
	padding: 10px;
	border: 1px solid black;
}
```
## 7 - Extend e Herança
O **@extend** no SASS permite que você reutilize estilos de um seletor em outro, de forma que o CSS gerado seja mais eficiente e fácil de manter. Basicamente, ele funciona como herança, onde um seletor pode "herdar" os estilos de outro seletor.

#### Como Funciona o @extend?
Com o **@extend**, você pode compartilhar estilos entre seletores sem duplicar código. O SASS adiciona todos os seletores que fazem @extend ao bloco de estilo original.

#### Exemplo de Alerta
```scss
// Sass
.alert {
  padding: 15px;
  border-radius: 5px;
  font-weight: bold;
}

.alert-success {
  @extend .alert;
  background-color: green;
  color: white;
}

.alert-error {
  @extend .alert;
  background-color: red;
  color: white;
}

```
```css
// Resultado CSS
.alert, .alert-success, .alert-error {
  padding: 15px;
  border-radius: 5px;
  font-weight: bold;
}

.alert-success {
  background-color: green;
  color: white;
}

.alert-error {
  background-color: red;
  color: white;
}
```

#### Atenção ao Usar @extend
- **Não pode ser usado dentro de blocos de regras aninhadas**: o @extend funciona apenas no nível superior de seletores.
- **Pode aumentar o tamanho do CSS gerado**: como todos os seletores que fazem @extend são adicionados ao mesmo bloco, o CSS pode ficar grande se não for usado com cuidado.

#### Alternativa ao @extend: Mixins
Se você precisar de mais flexibilidade, como evitar que seletores diferentes sejam agrupados, pode usar mixins no lugar do @extend:

```scss
// Sass
@mixin alert {
  padding: 15px;
  border-radius: 5px;
  font-weight: bold;
}

.alert-success {
  @include alert;
  background-color: green;
  color: white;
}

.alert-error {
  @include alert;
  background-color: red;
  color: white;
}
```

#### Diferença entre @extend e Mixins
| Aspecto   | @extend       | Mixin                                   |
| :---------- | :--------- | :------------------------------------------ |
| `CSS Gerado` | Agrupa seletores | Duplica o código |
| `Uso` | Herança entre seletores | Reutilização com mais flexibilidade |
| `Parâmetros` | Não aceita parâmetros | Aceita parâmetros |
| `Tamanho do CSS` | CSS pode ficar menor ou maior | Pode gerar código duplicado |

## 8 - Operadores e Condicionais
O SASS oferece uma série de operadores matemáticos e estruturas condicionais que facilitam a criação de folhas de estilo dinâmicas e reutilizáveis. Esses recursos ajudam a realizar cálculos e aplicar estilos de maneira mais eficiente e personalizada.

### Operadores Matemáticos
- Adição: +
- Subtração: -
- Multiplicação: *
- Divisão: /
- Módulo: %

```scss
$base-padding: 10px;

.container {
  padding: $base-padding * 2;  // 20px
  width: 100% / 3;             // 33.3333%
}
```

⚠️ Nota: A divisão (/) pode ter problemas se o valor não estiver entre parênteses, pois pode ser interpretada como separador de CSS.

### Condicionais no SASS
O SASS suporta condicionais com @if, @else if, e @else. Isso permite a aplicação de diferentes estilos com base em variáveis ou comparações.
```scss
$device: 'tablet';

.container {
  @if $device == 'mobile' {
    width: 100%;
  } @else if $device == 'tablet' {
    width: 75%;
  } @else {
    width: 50%;
  }
}
```

### Operadores de Comparação
- Igual a: ==
- Diferente de: !=
- Maior que: >
- Menor que: <
- Maior ou igual a: >=
- Menor ou igual a: <=

### Operadores Lógicos
- E: and
- Ou: or
- Não: not
## 9 - Mapas e Listas
O SASS oferece suporte para listas e mapas, que ajudam a organizar e manipular dados de forma eficiente. Esses recursos são especialmente úteis quando você precisa definir grupos de variáveis ou pares chave-valor e reutilizá-los dinamicamente no seu projeto.

### 9.1 - Listas no SASS
Uma lista é uma coleção de itens separados por espaço ou vírgula.

#### Criando Listas
```scss
// Lista separada por espaço
$espacamentos: 10px 20px 30px;

// Lista separada por vírgula
$cores: red, green, blue;
```

#### Acessando Itens da Lista com nth()
Use a função nth() para acessar um item específico da lista.
```scss
.box {
  margin: nth($espacamentos, 2); // 20px
}
```
⚠️ As listas no SASS são indexadas a partir de 1, não 0.

#### Iterando sobre uma Lista com @each
```scss
$cores: red, green, blue;

@each $cor in $cores {
  .text-#{$cor} {
    color: $cor;
  }
}
```

#### Adicionando e Removendo Itens de Listas
- **Adicionar**: Use append().
- **Remover**: Use join() ou crie uma nova lista sem o item desejado.

```scss
// append()
$cores: red, green;
$cores = append($cores, blue); // Lista: red, green, blue
```
```scss
// join()
$list1: 10px 20px;
$list2: 30px 40px;

$lista-combinada: join($list1, $list2);
```

### 9.2 - Mapas no SASS
Um mapa é uma coleção de pares chave-valor.

#### Criando Mapas
```scss
$cores: (
  primary: #3498db,
  secondary: #2ecc71,
  danger: #e74c3c
);
```

#### Acessando Itens no Mapa
Use a função **map-get()** para acessar um valor com base em sua chave.
```scss
.button {
  background-color: map-get($cores, primary); // #3498db
}
```

#### Iterando sobre um Mapa com @each
```scss
// Sass
$cores: (
  primary: #3498db,
  secondary: #2ecc71,
  danger: #e74c3c
);

@each $nome, $valor in $cores {
  .btn-#{$nome} {
    background-color: $valor;
  }
}
```
```css
// CSS Gerado
.btn-primary {
  background-color: #3498db;
}
.btn-secondary {
  background-color: #2ecc71;
}
.btn-danger {
  background-color: #e74c3c;
}
```

#### Adicionando e Removendo Itens em Mapas
- **Adicionar**: Use map-merge().
- **Remover**: Use map-remove().

```scss
// Adicionar uma nova cor ao mapa
$cores: map-merge($cores, (success: #2ecc71));

// Remover um item do mapa
$cores: map-remove($cores, danger);
```

### 9.3 - Funções Úteis para Listas e Mapas
#### Funções para Listas:
- **length()**: Retorna o número de itens na lista.
- **nth()**: Retorna o item na posição especificada.

```scss
$total: length($cores); // 3

$segunda-cor: nth($cores, 2); // green
```

#### Funções para Mapas:
- **map-get()**: Retorna o valor associado a uma chave.
- **map-has-key()**: Verifica se uma chave existe no mapa.

```scss
$cor-primaria: map-get($cores, primary); // #3498db

@if map-has-key($cores, danger) {
  // Faz algo se a chave 'danger' existir
}
```



## 10 - Loops e Estruturas Repetitivas
No Sass, você pode criar loops usando as diretivas **@for**, **@each** e **@while**. Eles permitem que você gere estilos dinamicamente, repetindo blocos de código CSS com diferentes valores. Isso é muito útil para situações como geração de múltiplas classes, gradientes, ou tamanhos sequenciais. Abaixo estão exemplos claros de como cada tipo de loop funciona.

### 10.1 - @for: Loop com Intervalo de Números

#### Sintaxe:
```scss
@for $i from <start> through/to <end> {
	// Estilos para cada valor de $i
}
```
- **from**: Define o valor inicial do loop.
- **through**: Inclui o valor final na repetição.
- **to**: Exclui o valor final.

#### Exemplo:
```scss
// Sass
@for $i from 1 through 3 {
	.margin-#{$i} {
		margin: #{$i * 5}px;
	}
}
```

```css
// Resultado CSS
.margin-1 {
	margin: 5px;
}
.margin-2 {
	margin: 10px;
}
.margin-3 {
	margin: 15px;
}
```

### 10.2 - @each: Loop para Listas e Mapas

#### Sintaxe:
```scss
@each $item in <list> {
	// Estilos para cada item da lista
}
```

#### Exemplo:
```scss
// Sass
$sizes: 10rem, 20rem, 30rem;

@each $size in $sizes {
	.icon-#{$size} {
		height: $size;
		width: $size;
		background: red;
	}
}
```

```css
// Resultado CSS
.icon-10rem {
	height: 10rem;
	width: 10rem;
	background: red;
}

.icon-20rem {
	height: 20rem;
	width: 20rem;
	background: red;
}

.icon-30rem {
	height: 30rem;
	width: 30rem;
	background: red;
}
```

### Exemplo com mapas:
```scss
// Sass
$colors: (primary: #4caf50, secondary: #2196f3);

@each $name, $color in $colors {
	.#{$name} {
		background-color: $color;
	}
}
```

```css
// Resultado CSS
.primary {
	background-color: #4caf50;
}

.secondary {
	background-color: #2196f3;
}
```

### 10.3 - @while: Loop com Condição
O loop @while repete enquanto uma condição for verdadeira.

#### Exemplo:
```scss
// Sass
$i: 3;

@while $i > 0 {
	.border-#{$i} {
		border-width: $i * 2px;
	}
	$i: $i - 1;
}
```

```css
// Resultado CSS
.border-3 {
	border-width: 6px;
}

.border-2 {
	border-width: 4px;
}

.border-1 {
	border-width: 2px;
}
```
## 11 - Funções Internas

### 11.1 - Funções de Cores
Essas funções permitem manipular cores, alterando brilho, saturação, transparência e mais.

- **darken($color, $amount)**: Escurece uma cor.
- **lighten($color, $amount)**: Clareia uma cor.
- **transparentize($color, $amount)**: Transparência da cor.
- **mix($color1, $color2, $weight)**: Combina duas cores com base em uma porcentagem.

```scss
// lighten($color, $amount)
.primary {
  background-color: lighten(#3498db, 20%); // Mais claro
}

// darken($color, $amount)
.secondary {
  background-color: darken(#3498db, 10%); // Mais escuro
}

// transparentize($color, $amount)
.overlay {
  background-color: transparentize(#000, 0.5); // Transparência de 50%
}

// mix($color1, $color2, $weight)
.blended {
  background-color: mix(#3498db, #e74c3c, 50%); // Combinação das duas cores
}
```

### 11.2 - Funções Numéricas
Manipula e converte valores numéricos diretamente nos estilos.

- **round()**: Arredonda o número para o mais próximo.
- **ceil()**: Arredonda para cima.
- **floor()**: Arredonda para baixo.
- **percentage($number)**: Converte o número em porcentagem.

```scss
// percentage($number)
.margin {
  margin-top: percentage(0.5); // 50%
}

// round($number), ceil($number), floor($number)
.box {
  width: round(33.3333%);  // Arredonda para 33%
  height: ceil(10.2px);     // Arredonda para 11px
  padding: floor(10.9px);   // Arredonda para 10px
}
```

### 11.3 - Funções de Strings
Manipula strings diretamente no SASS.

- **to-upper-case($string)**: Transforma todas as letras em maiúsculas.
- **to-lower-case($string)**: Transforma todas as letras em minúsculas.
- **str-length($string)**: Retorna o tamanho da string.
- **str-slice($string, $start-at, [$end-at])**: Fatia a string.

```scss
// to-upper-case($string) e to-lower-case($string)
.text {
  content: to-upper-case("sass é incrível"); // "SASS É INCRÍVEL"
}

// str-length($string)
.length {
  width: str-length("SASS"); // 4
}

// str-slice($string, $start-at, [$end-at])
.sliced {
  content: str-slice("SASS", 1, 3); // "SAS"
}
```

### 11.4 - Funções de Listas
Essas funções facilitam a manipulação de listas no SASS.

- **nth($list, $n)**: Retorna o n-ésimo item de uma lista (o primeiro item é indexado como 1).
- **length($list)**: Retorna o número de itens em uma lista.
- **append($list, $value, [$separator])**: Adiciona um novo valor ao final da lista. O separador pode ser espaço ou vírgula (por padrão, ele usa o mesmo separador da lista original).
- **join($list1, $list2, [$separator])**: Combina duas listas em uma única lista. Você pode especificar se a lista combinada será separada por espaço ou vírgula.

```scss
$cores: red, green, blue;

// nth($list, $n)
.item {
  color: nth($cores, 2); // green
}

// length($list)
.total {
  content: length($cores); // 3
}

// append($list, $value, [$separator])
$new-cores: append($cores, yellow); // red, green, blue, yellow

// join($list1, $list2, [$separator])
$extra-cores: pink, purple;
$combined: join($cores, $extra-cores, comma); // red, green, blue, pink, purple
```

### 11.5 - Funções de Mapas
Essas funções permitem trabalhar com mapas chave-valor.

- **map-get($map, $key)**: Retorna o valor associado à chave fornecida em um mapa.
- **map-has-key($map, $key)**: Verifica se um mapa contém uma chave específica. Retorna true ou false.
- **map-keys($map)**: Retorna uma lista contendo todas as chaves do mapa.
- **map-merge($map1, $map2)**: Combina dois mapas. Se houver chaves duplicadas, os valores do segundo mapa substituirão os do primeiro.

```scss
$cores: (
  primary: #3498db,
  secondary: #2ecc71
);

// map-get($map, $key)
.primary-color {
  color: map-get($cores, primary); // #3498db
}

// map-has-key($map, $key)
@debug map-has-key($cores, danger); // false

// map-keys($map)
@each $key in map-keys($cores) {
  .#{$key} {
    content: $key;
  }
}

// map-merge($map1, $map2)
$extra-cores: (danger: #e74c3c);
$all-cores: map-merge($cores, $extra-cores);
```
## 12 - Responsividade
O SASS facilita a criação de media queries aninhadas, tornando o código mais legível e organizado. Com essa funcionalidade, você pode definir estilos responsivos diretamente dentro do seletor correspondente, eliminando a necessidade de duplicação e mantendo a hierarquia do código clara.

### 12.1 - Exemplo Básico de Media Query Aninhada
Em vez de separar as media queries do seletor, o SASS permite que você as aninhe dentro dos seletores correspondentes.

#### Sass:
```scss
.card {
  padding: 10px;
  background-color: #f5f5f5;

  @media (min-width: 768px) {
    padding: 20px;
  }

  @media (min-width: 1024px) {
    padding: 30px;
  }
}
```
#### CSS Gerado:
```css
.card {
  padding: 10px;
  background-color: #f5f5f5;
}

@media (min-width: 768px) {
  .card {
    padding: 20px;
  }
}

@media (min-width: 1024px) {
  .card {
    padding: 30px;
  }
}
```

#### Vantagem:
A media query é mantida dentro do contexto do seletor, facilitando a manutenção do código.

### 12.2 - Media Queries com Mixins
Você pode definir media queries como mixins reutilizáveis para manter o código mais DRY (Don't Repeat Yourself).

#### Mixin para Media Queries:
```scss
// Sass
@mixin respond-to($breakpoint) {
  @if $breakpoint == 'tablet' {
    @media (min-width: 768px) { @content; }
  } @else if $breakpoint == 'desktop' {
    @media (min-width: 1024px) { @content; }
  }
}
```

#### Uso do Mixin:
```scss
// Sass
.card {
  padding: 10px;

  @include respond-to('tablet') {
    padding: 20px;
  }

  @include respond-to('desktop') {
    padding: 30px;
  }
}
```

#### CSS Gerado:
```css
.card {
  padding: 10px;
}

@media (min-width: 768px) {
  .card {
    padding: 20px;
  }
}

@media (min-width: 1024px) {
  .card {
    padding: 30px;
  }
}
```

### 12.3 - Uso de Variáveis para Breakpoints
Defina variáveis para breakpoints que podem ser reutilizadas ao longo do projeto.

```scss
$breakpoints: (
  small: 480px,
  tablet: 768px,
  desktop: 1024px
);

@mixin respond-to($breakpoint) {
  @media (min-width: map-get($breakpoints, $breakpoint)) {
    @content;
  }
}
```

#### Uso:
```scss
.header {
  background-color: lightgray;

  @include respond-to('tablet') {
    background-color: gray;
  }

  @include respond-to('desktop') {
    background-color: black;
  }
}
```

#### CSS Gerado:
```css
.header {
  background-color: lightgray;
}

@media (min-width: 768px) {
  .header {
    background-color: gray;
  }
}

@media (min-width: 1024px) {
  .header {
    background-color: black;
  }
}
```

### 12.4 - Media Queries Complexas
Você também pode definir media queries complexas com múltiplas condições diretamente dentro dos seletores.

#### Sass
```sass
.container {
  display: flex;

  @media (min-width: 768px) and (orientation: landscape) {
    flex-direction: row;
  }

  @media (max-width: 767px) {
    flex-direction: column;
  }
}
```

#### CSS Gerado
```css
.container {
  display: flex;
}

@media (min-width: 768px) and (orientation: landscape) {
  .container {
    flex-direction: row;
  }
}

@media (max-width: 767px) {
  .container {
    flex-direction: column;
  }
}
```


### 12.5 - Conclusão
Com media queries aninhadas e mixins reutilizáveis, o SASS facilita a criação de estilos responsivos de forma clara e eficiente. Isso torna seu CSS:
- Mais fácil de manter, pois cada media query é colocada diretamente no contexto relevante.
- Reutilizável, utilizando mixins e variáveis para breakpoints.
- Escalável, especialmente em projetos grandes, onde a organização e modularidade são cruciais.
## 13 - Debug e Erros
O SASS oferece as diretivas @debug, @warn e @error para ajudar no debug e no tratamento de erros. Essas ferramentas são úteis para identificar problemas durante a compilação e garantir que seu CSS seja gerado corretamente.

### 13.1 - @debug: Exibe Informações para Debug
A diretiva @debug é usada para exibir valores e informações no console durante a compilação do SASS. Ela é útil para verificar o valor de variáveis e o comportamento de funções e mixins.

#### Sintaxe:
```scss
@debug <expressão>;
```
#### Exemplo:
```scss
$primary-color: #3498db;

@debug $primary-color;  // Exibe: #3498db
@debug type-of($primary-color);  // Exibe: color
```
#### Saída no Console:
```
#3498db
color
```

### 13.2 - @warn: Exibe Avisos
A diretiva @warn exibe avisos durante a compilação, mas não interrompe o processo. É útil para notificar sobre práticas não recomendadas, valores incomuns ou comportamentos inesperados.

#### Sintaxe:
```scss
@warn <mensagem>;
```
#### Exemplo:
```scss
$font-size: 8px;

@if $font-size < 10px {
  @warn "Font size muito pequeno! Pode não ser legível.";
}
```
#### Saída no Console:
```
WARNING: Font size muito pequeno! Pode não ser legível.
```

### 13.3 - @error: Lança Erros e Interrompe a Compilação
A diretiva @error exibe uma mensagem de erro e interrompe a compilação do SASS. Use-a quando encontrar uma condição que deve impedir a geração de CSS.

#### Sintaxe:
```scss
@error <mensagem>;
```
#### Exemplo:
```scss
$theme: 'unknown';

@if not ($theme == 'dark' or $theme == 'light') {
  @error "Tema inválido: #{$theme}. O tema deve ser 'dark' ou 'light'.";
}
```
#### Saída no Console:
```
Error: Tema inválido: unknown. O tema deve ser 'dark' ou 'light'.
```
