
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
1. [Introdução](#introdução)
2. [Instalação e Configuração](#instalação-e-configuração)
3. [Variáveis](#variaveis)
4. [Introdução](#introdução)
5. [Introdução](#introdução)

## Introdução

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
Se você já está acostumada com CSS tradicional, o SCSS é uma escolha natural, pois a sintaxe é quase idêntica.
Se prefere uma abordagem minimalista e gosta de trabalhar com indentação, a sintaxe SASS pode ser mais adequada.
## Instalação e Configuração
## Variáveis

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
