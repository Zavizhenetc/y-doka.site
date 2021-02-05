---
title: "attr()"
name: attr
author: ezhkov_d
co-authors:
designers:
contributors:
summary:
  - content
  - псевдоэлемент
  - атрибуты
---

## Кратко

`attr()` — это CSS-функция, которая умеет получать значение любого атрибута у элемента, а потом использовать это значение прямо внутри таблицы стилей.

## Пример

```html
<div class="element"></div>
```

```css
.element::after {
  content: "Элемент с классом" attr(class);
}
```

## Как пишется

```css
attr(data-title);
attr(href);

/* С указанием типа */
attr(src url);
attr(data-count number);
attr(data-width px);

/* С указанием "запасного" значения (fallback) */
attr(data-count number, 0);
attr(src url, "");
attr(data-width px, inherit);
attr(data-something, "default");
```

## Подсказки

💡 Функцию `attr()` можно использовать в качестве значения любого CSS-свойства, однако полностью поддерживается только свойство [`content`](/css/doka/content). Для остальных свойств поддержка экспериментальная и может отличаться от браузера к браузеру.

💡 Написание с указанием единиц изерения или фолбека пока имеет статус экспериментальной технологии и не поддерживается браузерами, но потенциально это позволит гораздо сильнее расширить область применения функции `attr()`. Например, мы можем указать браузеру, что значение атрибута — это данные числового типа или одна из единиц измерения, допустимых в CSS:

```css
.colored {
  background-image: attr(data-src url);
}
```

В примере выше мы указали, что в качестве значения для свойства `background-image` мы хотим использовать значение атрибута `data-src`. При этом уточнили, что значение атрибута `data-src` — это не просто строка, а корректный URL.

Примеры записи с указанием типа или фолбека кажутся довольно перспективными, но к сожалению пока не поддерживаются ни одним из браузеров.

## В работе

Самый распространённый случай использования функции `attr()` - отображение значения атрибута `href` после текста ссылки при печати страницы на принтере

```html
<p>Подробнее о скидках и акциях можно узнать <a href="http://best-site.ru/sales">по ссылке</a></p>
```

```css
@media print {
  a::after {
    content: " [" attr(href) "]";
  }
}
```

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="html,result" data-user="ezhkov" data-slug-hash="JjbGeoM" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="attr()">
  <span>See the Pen <a href="https://codepen.io/ezhkov/pen/JjbGeoM">
  attr()</a> by Denis Ezhkov (<a href="https://codepen.io/ezhkov">@ezhkov</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

{% include "authors/ezhkov_d/author.njk" %}
