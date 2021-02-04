---
title: "text-decoration"
name: text-decoration
author: ABatickaya
co-authors:
  - furtivite
designers:
contributors: skorobaeus
summary:
  - text-decoration
---

## Кратко

Свойство `text-decoration` позволяет добавить декоративные линии тексту. Текст можно подчеркнуть, перечеркнуть или добавить линию над текстом. Больше ни на что это свойство не способно.

`text-decoration: underline` часто встречается при работе со ссылками.

## Пример

Создадим четыре абзаца текста. По одному для каждого из доступных значений свойства `text-decoration`.

HTML

```html
<div class="parent">
  <p class="none">Диакритические знаки...</p>
  <p class="underline">В типографике...</p>
  <p class="line-through">Диакритическими знаками не могут...</p>
  <p class="overline">Черта сверху — типографический знак...</p>
</div>
```

CSS

```css
.none {
  text-decoration: none; /* Значение по умолчанию, ничего не меняется */
}

.underline {
  text-decoration: underline; /* Нижнее подчёркивание */
}

.line-through {
  text-decoration: line-through; /* Перечёркнутый текст */
}

.overline {
  text-decoration: overline; /* Линия над текстом */
}
```

{% demo "/text-decoration/basic", "Декор текста", 710 %}

# Как это понять

С английского языка слово **decoration** переводится как украшение или декор. Дословно можно перевести свойство как текст-украшение. Говоря человеческим языком, украшение текста.

# Как пишется

Пишем свойство `text-decoration` и после двоеточия указываем одно из доступных значений:

- `underline` — подчёркнутый текст.
- `line-through` — перечёркнутый текст.
- `overline` — надчёркнутый текст, линия находится над словами.
- `none` — отменяет все эффекты.

Выше указаны стандартные значения, с которыми ты будешь сталкиваться чаще всего.

Не многие знают, что после ключевого слова, означающего положение линии, можно указать ещё и стиль этой линии и её цвет.

Для управление стилем линии используются следующие ключевые слова:

- `solid` — сплошная линия. Значение по умолчанию.
- `double` — двойная линия.
- `dotted` — точечная линия.
- `dashed` — пунктирная линия.
- `wavy` — волнистая линия.

Управлять стилем подчёркивания обычно не требуется, но об этой возможности знать нужно.

Как будет выглядеть двойное перечёркивание:

```css
selector {
  text-decoration: line-through double;
}
```

Стиль линии можно указать отдельно при помощи свойства `text-decoration-style`.

{% demo "/text-decoration/style", "Стиль линии декора текста", 600 %}

Цвет линии по умолчанию совпадает с цветом текста, для которого задаётся свойство `text-decoration`.

Мы можем изменить это значение, указав после ключевых слов типа и стиля линии код цвета в любом доступном в вебе формате.

Например, сделаем двойное подчёркивание красного цвета:

```css
selector {
  text-decoration: underline double #ff0000;
}
```

Цветом линии можно управлять отдельно при помощи свойства `text-decoration-color`:

{% demo "/text-decoration/style-color", "Стиль и цвет линии декора текста", 730 %}

## Подсказки

💡 Свойство не наследуется.

💡 Значение по умолчанию для обычного текста — `none`. Но для ссылок ([<a>](/html/doka/a/)) значение по умолчанию — `underline`.

💡 Свойство `text-decoration` целиком нельзя анимировать при помощи свойства `transition` 😒

Но можно анимировать цвет линии!

Пусть по умолчанию цвет линий будет совпадать с цветом текста, а по наведению курсора цвет будет меняться на другой за 0.3 секунды.

HTML

```html
<div class="parent">
  <p class="none">К диакритикам...</p>
  <p class="underline">Дополнение подчеркивается...</p>
  <p class="line-through">Эпанортозис...</p>
  <p class="overline">В большинстве языков...</p>
</div>
```

CSS

```css
p {
  transition: text-decoration-color 0.3s;
}

.none {
  text-decoration: none;
}

.underline {
  text-decoration: underline;
}

.line-through {
  text-decoration: line-through;
}

.overline {
  text-decoration: overline;
}

.dotted {
  text-decoration-style: dotted;
}

.double {
  text-decoration-style: double;
}

.wavy {
  text-decoration-style: wavy;
}

.blue:hover {
  text-decoration-color: #1a5ad7;
}

.red:hover {
  text-decoration-color: #ed6742;
}

.green:hover {
  text-decoration-color: #49a16c;
}

```

<a name="example"></a>

{% demo "/text-decoration/color", "Анимированный декор текста", 730 %}

💡 Нельзя управлять толщиной и положением линии, заданной при помощи `text-decoration`.

💡 Если по дизайну требуется задать тексту или ссылке подчёркивание, отличающееся от стандартного по толщине или положению, а также если нужно анимировать появление / пропадание линии, то используй псевдоэлементы `:before` или `:after`.

## В работе

{% include "authors/ABatickaya/in-work.njk" %}

🛠 У ссылок по умолчанию задано подчёркивание. Если по дизайну оно не требуется, то нужно будет его _сбросить_ — задать свойство `text-decoration: none`. Это самый частый случай применения этого свойства. Перечёркивание или надчёркивание почти не встречаются в работе.

🛠 Отдельные свойства — `text-decoration-line`, `text-decoration-style` и `text-decoration-color` — редко встречаются в вёрстке, но знать о них нужно, чтобы при необходимости не переписывать свойство целиком только для изменения стиля или цвета линии.

{% include "authors/furtivite/in-work.njk" %}

Иногда вам может потребоваться управлять расстоянием между текстом и линией ниже. Обычно это делается, через свойство `line-height`. Чем больше высота строки, тем ниже будет полоса подчеркивания.

К сожалению, этот способ подходит не всегда. Например, когда дизайнер задумал элемент несколько иначе. На примере ниже отказываемся от `text-decoration` и используем `border-bottom`.

HTML

```html
<header>
  <div class="container top">
    <nav>
      <ul class="navigation">
        <li class="navigation__item">
          <a href="#" class="navigation__link">О магазине</a>
        </li>
        <li class="navigation__item">
          <a href="#" class="navigation__link">Новости</a>
        </li>
        <li class="navigation__item">
          <a href="#" class="navigation__link">Акции</a>
        </li>
        <li class="navigation__item">
          <a href="#" class="navigation__link">Личный кабинет</a>
        </li>
      </ul>
    </nav>
  </div>
  <div class="container">
    <h1>Магазин «лето»</h1>
  </div>
</header>
```

CSS

```css
.navigation__link, .navigation__link:visited {
  display: inline-block; /* делаем элементы строчно-блочными */
  color: #18191C;
  text-decoration: none; /* убираем подчеркивание */
  padding-top: 16px;
  padding-bottom: 16px;
  text-transform: uppercase;
  font-weight: 500;
  font-size: 15px;
}

.navigation__link:hover {
  padding-bottom: 14px; /* нивелируем размеры рамки */
  border-bottom: 2px solid #18191C; /* добавляем рамку снизу */
}
```

{% demo "/text-decoration/header", "Рамка вместо подчеркивания", 460 %}

{% include "authors/ABatickaya/author.njk" %}
