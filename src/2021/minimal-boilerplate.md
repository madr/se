---
title: Approach för att starta ett CSS-projekt 2021
date: 2021-04-21
layout: single.hbs
collection: articles
---

En checklista för minimal boilerplate för ett designprojekt för webb.

## HTML

Först av allt, en HTML-mall med det viktigaste.

```
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title></title>
    <link rel="stylesheet" href="./main.css">
  </head>
  <body>
    <h1>hello</h1>
  </body>
</html>
```

För litet mer inspiration, kika på [Poor mans Styleguide](https://poormansstyleguide.com/) för exempel-HTML.

## Normaliserings-CSS

Gå till ett minimalistiskt CSS-bibliotek och inspireras av kod därifrån. Några exempel:

 * [Sakura](https://oxal.org/projects/sakura/demo/)
 * [Basic.css](https://vladocar.github.io/Basic.css/)

En något längre lista finns på [Classless CSS](https://github.com/dbohdan/classless-css).

## Valfritt: lägg till Sass

Om Sass börjar bli nödvändigt, introducera en bundler som konfigurerar sig själv och sparar dig från trubbel. 
Min favorit för 2021 är Parcel: [How to use Parcel for a simple SCSS project](https://www.brianhan.co/2018-12-18-parcel-sass/).

Detta är kortformatet på artikeln ovan. Först terminalkommandot.

```
npm init -y
npm i parcel-bundler -D
```

Skapa `package.json` och lägg följande 4 rader där.

```
{
  "scripts": {
    "dev": "parcel src/index.html",
    "build": "parcel build src/index.html"
  }
}
```

Byt också ut filändelsen på Sass-filen i HTML-dokumentet.

```
<link rel="stylesheet" href="./main.scss">
```

Parcel kommer automatiskt att installera Sass, Autoprefixer och annat bra, och uppdatera `package.json`.

Som en avslutning, gå till [Browserslist](https://browserslist.dev/) och kopiera en lämplig inställning för projektet. Spara denna i `package.json`, eller i `.browserslistrc`.