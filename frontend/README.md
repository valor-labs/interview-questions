блочные - строчные элементы

---
Вместить три блока 20X20px в ряд, в блок шириной 60px, при этом у блоков должны быть границы.

```html
<div class="wrap">
  <div class="block"></div>
  <div class="block"></div>
  <div class="block"></div>
</div>
```
```css
.wrap {
  width: 600px;
  height: 200px;
  border: 1px solid green;
}

.block {
  float: left;
  width: 200px;
  height: 200px;
  outline: 1px solid black;
}
```
 или
```html
<div class="wrap">
  <div class="block"></div><div class="block"></div><div class="block"></div>
</div>
```
```css
.wrap {
  width: 600px;
  height: 200px;
  border: 1px solid green;
}

.block {
  display: inline-block;
  width: 200px;
  height: 200px;
  outline: 1px solid black;
}
```
---
Требуется сверстать попап по центру, его размеры нам известны, но мы не хотим что бы он прокручивался вместе со страницей, причем по высоте может и не влезать в высоту экрана.
```css
body {
  overflow: hidden;
}

.wrap {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow-y: auto;
  background-color: rgba(230, 230, 230, .1);
}

.popup {
  position: absolute;
  width: 400px;
  height: 300px;
  right: 0;
  left: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
```
---
Нарисовать стилями полукруг
```css
width: 100px;
height: 100px;
border-right: 1px solid #f00;
border-radius: 0 50% 50% 0;
```
---
Чем opacity отличается от visible: hidden и что это такое, отличие от overflow: hidden?

opacity отвечает за прозрачность элемента. Принимает значения от 0 до 1, при 0 — элемент не виден, .5 — полупрозрачен, 1 — полностью виден. Даже при 0 занимает место на странице.
Элемент со стилями visible: hidden так же занимает место, не видим. Но в отличие от элемента с opacity, js-события на нем не срабатывают.
display: none — полностью скрывает элемент, он не видим и не занимает место на странице. javascript не может получить ни width, height.
overflow: hidden; — скрывает все, что попадет за его пределы.

---
Есть div, в нем другой div, у второго задан padding 50%, как это все будет выглядеть?
```css
.wrap {
  width: 200px;
  border: 1px solid green;
}

.block {
  width: 200px;
  padding-bottom: 50%;
  border: 1px solid red;
}
```
---
Напишите код, который при клике на любой div внутри root будет выводить в консоль его id.
```html
<div id="root" style="background: red;">
    root
    <span id="id1" style="background: lightblue;">id1</span>
    <div id="id2" style="background: green;">
        id2
        <div id="id3" style="background: yellow;">id3</div>
    </div>
</div>
```
```javascript
$('#root').on('click', function (event) {
    event.stopPropogation();
    console.log($(event.target).attr('id'));
})
```
---

дан html

```html
<html>
<head>
  <style>
.wrapper {
  background-color: green;
  padding: 10px;
}
.chld {
  background-color: red;
  margin: 10px;
  float: left;
}
  </style>
</body>
<body>
  <div class="wrapper">
    <div class="chld">content is here</div>
  </div>
</body>
</html>
```

габариты wrapper блока

---

дан html

```html
<html>
<head>
  <style>
.d1 {
  background-color: red;
  margin-bottom: 300px;
}
.d2 {
  background-color: blue;
  margin-top: 300px;
}
  </style>
</body>
<body>
  <div class="d1">111</div>
  <div class="d2">222</div>
</body>
</html>
```

расстояние между блоками

---
