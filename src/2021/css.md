---
title: Nästlade selektorer i CSS, utan preprocessors
original: CSS Nesting Module, Editor's draft
source: https://drafts.csswg.org/css-nesting-1/
date: 2021-01-17
collection: links
layout: single.hbs
---

> This module introduces the ability to nest one style rule inside another, with the selector of the child rule relative to the selector of the parent rule. This increases the modularity and maintainability of CSS stylesheets.

Hoppla! Exempel, starkt inspirerat av hur Sass gör, finns på [The future of CSS: Nesting Selectors](https://www.bram.us/2019/03/17/the-future-of-css-nesting-selectors/).

Detta, CSS-variabler och nästlade media queries gör att det blir allt mindre risk i att slopa
preprocessors som Sass, Less eler Stylus i mindre projekt.

Tre saker:

* Detta har potential att få utvecklarverktygen i webbläsarna till nya nivåer.
* `@nest` känns litet märklig, men kanske har den ett nyttigt signalvärde? Vi
  får se!
* Om inte stöd för `&--` och `&__` införs är detta ointressant för alla som använder
  [BEM][1]: dessa utvecklare kommer att stanna med preprocessors, tror jag.

[1]: https://css-tricks.com/bem-101/
