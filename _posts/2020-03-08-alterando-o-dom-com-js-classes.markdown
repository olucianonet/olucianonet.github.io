---
layout: post
title:  "Alterando o DOM com JS - Classes"
date:   2020-03-08 00:00:00 -0300
categories: dev web html css js
---

...considerando que páginas HTML são estáticas, ou seja, após publicada nada mudará durante o acesso. Quando for necessário adicionar recursos dinâmicos a elas, o Javascript será sempre uma opção _interessante_.

O Javascript é uma das linguagens que tem a capacidade de alterar a estrutura de documentos de marcação, como HTML ou XML. Ele faz isso utilizando a API DOM.

De forma geral, a API DOM é um conjunto de funções que trata cada elemento de um documento de marcação como um nó, permitindo sua navegação e alteração.

**Exemplo 1:**

- Código HTML

```html
<div id="item1" class="green"></div>
```
- Código CSS

 ```css
div {
  width: 200px;
  height: 200px;
  margin-bottom: 10px;
}

div:hover {
  cursor: pointer;
}

.green{
  background-color: green;
}

.yellow{
  background-color: yellow;
}    
 ```

- Código JS

```js
var item = document.getElementById("item1");

item.addEventListener("click", function(e){
  if (this.className === "green"){
    this.className = "yellow"
  } else {
    this.className = "green";
  }
});
```

O HTML acima, cria uma `div` com um `background` na cor verde e ao clicar no elemento, sua cor é alterada.

Isso acontece graças ao script que recupera o item, utilizando o seu id e adiciona um evento que altera sua classe, definida previamente no CSS.

No JS existe um `if` que verifica qual a classe atual do elemento. Isso foi possível graças ao recurso de recuperar o elemento utilizando seu id. 

A variável `item` recebe um elemento existente no objeto `document`, ou seja, a página HTML. O `document` é o elemento principal da API DOM e através dele é possível navegar para os demais elementos utilizando os métodos da API.

**Exemplo 2:**

- Código HTML

```html
<!-- código anterior -->
<div id="item2" class="yellow"></div>
```

- Código JS

```js
// código anterior
  if (this.className === "green"){
    this.className = "yellow";
    this.nextElementSibling.className = "green";
  } else {
    this.className = "green";
    this.nextElementSibling.className = "yellow";
  }
```

O código HTML acima cria mais uma `div`, agora com a classe yellow. Nesse momento, existem duas caixas, uma verde e outra amarela.

Da mesma forma que no exemplo anterior, ao receber o click a cor da primeira `div` é alterada, porém, agora a cor da segunda `div` também é alterada, alternando suas cores entre o verde e o amarelo.

Para isso, foi necessário recuperar o segundo item e alterar sua classe, utilizando JS. Porém, desta vez, foi utilizado o método `nextElementSibling`, que permite caminhar no DOM e acessar o _próximo elemento irmão_, utilizando como referência o objeto atual, o `this`. 

**Veja como ficou o exemplo:**

<p class="codepen" data-height="520" data-theme-id="light" data-default-tab="html,result" data-user="olucianonet" data-slug-hash="RwPjvJa" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="alterando-o-dom-com-js">
  <span>See the Pen <a href="https://codepen.io/olucianonet/pen/RwPjvJa">
  alterando-o-dom-com-js</a> by oluciano.net (<a href="https://codepen.io/olucianonet">@olucianonet</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**Para saber mais:**

- [Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [What is the HTML DOM?](https://www.w3schools.com/whatis/whatis_htmldom.asp)
