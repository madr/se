---
title: Sorgligt nog kommer Firefox snart att dö strypdöden
date: 2023-03-22
layout: single.hbs
collection: articles
---

Allt oftare får jag finna mig i att använda Chrome istället för Firefox.

Nu senast idag skulle jag lägga till integrationstester mellan Lit-komponenter och Vue, och noterade att den interna testsidan var vit och hade felet `Uncaught SyntaxError: import assertions are not currently supported` i konsolen. Detta är [en feature som Firefox fortfarande implementerar](https://bugzilla.mozilla.org/show_bug.cgi?id=1777526).

Lösningen? "Byt till Chrome", med den outtalade frågan varför jag inte bara ger upp och alltid kör Chrome.

Härom veckan satt jag och implementerade `role=radiogroup` enligt [ARIA Authoring Practices Guide för Radio Group-mönstret](https://www.w3.org/WAI/ARIA/apg/patterns/radio/), och vid test med [skärmläsaren NVDA](https://www.nvaccess.org/) noterade jag att grupperingen inte riktigt ville lira.

Förmodligen på grund av att implementationen byggde på Web Components - ett fieldset med ShadowDOM, och radio buttons i egna ShadowDOMs. Det funkade ibland, och ibland inte. Lösningen? "Byt till Chrome", med den outtalade frågan varför jag inte bara ger upp och alltid kör Chrome.

Hela situationen skickar tillbaka mig till minnen från sent 90-tal och 00-tal, där samma argument användes för att använda Internet Explorer 4-6. "Det är vad _alla_ använder", "Jag utvecklar bara mot en webbläsare och saknar motivation att testa i andra", och så vidare.

Mänskliga faktorn består över årtionden, vad det verkar. De yngre webbutvecklarna har inte lärt sig något av oss äldre webbutvecklares misstag.

Det skrivs runtom på Internet att Firefox är döende, och det finns ingen anledning att imbilla sig att det inte kommer att ske. I det allmänna medvetandet är webbläsaren redan död.

## Saker som indikerar strypdöden för Firefox

Listan väger över tid.

- Utvecklare har slutat använda Firefox och testar därför bara saker i Chrome.
- Interna verktyg stöds ej eller testas inte i Firefox.
- Produkter, tjänster och webbplatser utesluter aktivt Firefox ur listan på webbläsare som stöds.
- Än mer allvarligt: kombinationen av NVDA och Firefox har undermåligt stöd för bl a Web components och Shadow DOM. Radio buttons grupperas inte korrekt, exempelvis.
