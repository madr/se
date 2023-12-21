---
title: Utmärkta exempel på att använda CSS custom properties
original: Two options for using custom properties
source: https://www.quirksmode.org/blog/archives/2021/05/two_options_for.html
date: 2021-05-05
collection: links
layout: single.hbs
---

> In practice, component definitions have way more styles than just colours. There’s a bunch of box-model properties, maybe a display, and possibly text styling instructions. In any case, a lot of lines of CSS.
>
> If you use custom properties only for those CSS properties that will change you give future CSS developers a much better and quicker insight in how your component works. If the definition uses a custom property that means the property may change in some circumstances. If it uses a fixed definition you know it’s a constant.

_CSS custom properties_ är något som jag själv försöker tillämpa så mycket jag kan i projekt. Denna artikel öppnade några dörrar till och gör det än tydligare att det är skillnad på Sass-variabler och CSS Custom Properties: man ska _kombinera_ dem, inte välja en av dem.

På Twitter-tråden om artikeln [kompletterade Sara Soeidan med en egen artikel][1] om att arbeta med CSS custom properties, som också är läsvärd.

[1]: https://www.sarasoueidan.com/blog/style-settings-with-css-variables/