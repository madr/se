---
title: Bädda in externt webbinnehåll med Shadow DOM
date: 2020-09-29
layout: single.hbs
collection: articles
---

Ett vanligt önskemål som jag ofta hört under mina 2 decennier som yrkesverksam
webbutvecklare är att bädda in ("ajfrejma in") externt innehåll på sin egen webbplats.

Det skulle kunna vara något av följande:

- Instagramflöden,
- Tweets på Twitter,
- Mega-Widgets av olika slag eller
- [Kundservicesystem](https://kundo.se), vilket är vad jag kommer att fokusera
  på i detta blogginlägg.

Behovet kommer ifrån att man vill behålla besökare på den egna webbplatsen
istället för att besökarna ska klicka sig vidare. Helst ska webbplatsen även
tillgodose sig innehållet och sökmotorindexera det som tillhörande den egna
webbplatsen.

Då utvecklingstid är dyrt så ska det helst också kunna göras supersnabbt och smidigt,
framför att skriva en egen backend-lösning som kräver egen CSS och formgivning.

Det är kort och gott nästa svårighetsnivå från enklare widgets såsom [chatt till
hemsida][8], som är relativt smidigt och rättframt.

## Först: exempel på lyckad inbäddning!

Jag har förkovrat mig i detta [på jobbet](https://www.kundo.se/om-oss) nyligen, och
kan därför visa att tipsen och lärdomarna jag skriver om i detta blogginlägg
**fungerar**.

[ATGs kundtjänst](http://kundservice.atg.se) är nämligen en s.k. Mega-widget
helt integrerad på deras webbplats, med JavaScript och utan iframes. En
[googling av "Hur spelar jag en SpikHarry?"][12] visar också att inbäddningen
kan indexeras av sökmotorer.

Magin för att bädda in är inte mer avancerad än ett par rader HTML som klistras
in på webbplatsen.

```html
<div id="embed-placeholder" data-base-url="https://example.com"></div>
<script src="https://example.com/embed.js"></script>
```

## Varför inte bara använda iframes?

Den enkla och pragmatiska vägen har länge varit iframes, som har massor med
problem för såväl sökmotorindexering som tillgänglighet.

- [3 Reasons You Might Not Want To Use Iframes][9]
- [The iFrame Is Evil!][10]
- [Iframes are just terrible. Here’s how they could be better.][11]

Det har faktiskt blivit avsevärt enklare numera tack vare ett par stora saker.

- Googles crawler (Googlebot) [förstår numera JavaScript][7].
- [Shadow DOM][1] stöds av alla moderna webbläsare.

## Shadow DOM?

Konceptet _Shadow DOM_ är en nyckelkomponent i [Web Components][5].

Förenklat går det ut på att ett sandboxat DOM-träd monteras inuti ett
DOM-element, med `document.querySelector('what-ever').attachShadow()`.

Inuti detta träd ärvs (nästan) ingen CSS och all JavaScript kan köras
isolerat. Under huven på webbläsarna så sköts även rendering av Shadow DOMs
separat från <em>host-dokumentet</em> och andra Shadows DOM:s i detta.

## Fördelar med Shadow DOM över iframes

- Mer tillgängligt, då allt inuti en Shadow DOM har samma tabb-prio och nåbarhet
  som vanliga DOM-noder utifrån ett användarperspektiv. Vinst över iframe by far!
- (nästan) ingen CSS ärvs till Shadow DOM.
- SEO fungerar tack vare JavaScript-stöd i Googlebot.

## Begränsningar i Shadow DOM

- Det går ej att använda `rem` i Shadow DOM: `font-size` baseras då på host-dokumentets
  rot-element och det går ej att få `rem` att peka mot Shadow DOM. Se exempel
  [rem i Shadow DOM][2] som återskapar detta.
- Media queries sker på host-dokumentet, inte Shadow DOM. Se exempel [media
  queries i Shadow DOM][3] som visar detta.
- `@font-face` måste läggas som stildeklarationer i host-dokumentet: dessa
  ignoreras inuti Shadow DOM, och ärvs ner från Host-dokumentet till Shadow DOM.
  Se exemplet [@font-face i Shadow DOM][13] som demonstrerar detta.

## Tips för att skriva bra inbäddat innehåll

- Navigera med länkar. Google bot triggar inte händelser (`onclick`, `onsubmit` etc),
  utan navigerar enbart genom klick på länkar. Mer detalj kring detta: [Javascript Crawling Against HTML Crawling][6].
- Ha en snabbladdad sida. Googlebot har ett litet fönster för att ladda in
  innehållet, och kräver att saker laddas in inom en rimlig tid. [5 sekunder
  verkar vara accepterat][4].
- Bli vän med [CORS-headers][14]. Allt behöver CORS-headers för att fungera med
  ajax-fetchning. Kan förstås kringås med en _Ajax-proxy_ eller _jsonp_, med dålig
  felhantering som följd.
- Använd inte SVG sprites från fil. Kör inline för att kringgå
  CORS-relaterade säkerhetsspärrar för SVG.

## Ytterligare Sökmotoroptimering

- Matcha alltid nödvändiga saker i `<head>`: Alla nödvändiga `<meta>`-element, `<title>`-element, OpenGraph-saker, etc.
- Se till att värdens `robots.txt` inte blockerar sökmotorindexering av det inbäddade innehållet.
- Använd alltid en `<link rel='canonical'>` för att undvika dublett-indexering, särskilt om det inbäddade innehållet används på mer än en sida.
- Om det är många undersidor på det inbäddade innehållet, lägg till en [sitemap.xml i värdsidans robots.txt](https://www.woorank.com/en/blog/how-to-locate-a-sitemap-in-a-robots-txt-file).
- Om möjligt, försök använda semantiska adresser framför query strings (). Detta kräver dock teknisk insats från värdsidans webbserver eller CMS.
  - Dvs, istället för det här: `http://example.com/embedded-content?path=foo%2Fbar`
  - Använd detta: `http://example.com/embedded-content/foo/bar`
- Var noga med att alltid lägga till `<meta name='robots' content='noindex,nofollow'>` när
indexering inte önskas av det inbäddade innehållet, t ex vid HTTP 404, HTTP 403 eller HTTP 500.

[1]: https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM
[2]: ../../labs/shadow-dom-rem.html
[3]: ../../labs/shadow-dom-media-queries.html
[13]: ../../labs/shadow-dom-font-face.html
[4]: https://acowebs.com/javascript-seo/#5Second_Rule
[5]: https://developer.mozilla.org/en-US/docs/Web/Web_Components
[6]: https://acowebs.com/javascript-seo/#Javascript_Crawling_Against_HTML_Crawling
[7]: https://acowebs.com/javascript-seo/
[8]: https://kundo.se/chat
[9]: https://www.ostraining.com/blog/webdesign/against-using-iframes/
[10]: https://www.blackburnlabs.com/iframe-evil/
[11]: https://medium.com/@bluepnume/iframes-are-just-terrible-heres-how-they-could-be-better-974b731f0fb4
[12]: https://www.google.com/search?hl=sv&q=Hur%20spelar%20jag%20en%20SpikHarry%3F
[14]: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS
