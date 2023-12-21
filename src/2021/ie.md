---
title: Tack för tiden, Internet Explorer
date: 2021-08-12
layout: single.hbs
collection: articles
---

**Tack för tiden, Internet Explorer. Du var full av innovation och framsteg 1995–2003, och provade webbutvecklares tålamod ihärdigt 2004–2011, och 2013–2022.**

IE 1-5 drevs av optimism och innovation, mot lika drivna konkurrenter. Din skapare Microsoft anklagades för att ge dig orättvisa fördelar, men detta förminskar inte [alla dina innovationer][1]. Du fanns inledningsvis också på MacOS innan Apple hade en egen webbläsare, och även på UNIX.

IE 6, [vinnaren i det första webbläsarkriget][bw], var din höjdpunkt. Det var en fantastisk webbläsare när denna version av dig lanserades 2001, med sitt utmärkta stöd för webbstandarder. På grund av några dåliga beslut från din skapare Microsoft hamnade du dock snabbt på efterkälken och blev omodern, och din användarbas började i rask takt byta till andra mer moderna webbläsare. 

Du förhalade förloppet så gott du kunde med IE 7–8, men vid det laget var det tyvärr inga glada miner åt ditt håll från webbutvecklare. Din användarbas var mycket förtjusta i IE 6 och skeptiska till dina försök att bli mer modern. När IE 6 fyllde 10 år fick du en [webbplats med en nedräkning][ie6cd] till din föredetta praktfullhet, från din skapare Microsoft.

Du försökte rycka upp dig 2011–2013 med lanseringarna av IE 9–11 (en ny version per år!). Vid lanseringen av version 11 så var du den snabbaste och bäst presterande webbläsaren i flera tester. 

Dessvärre hade dina användare blivit din största fiende vid det laget: de enda som fortfarande använde IE var de som saknade möjlighet att själva välja webbläsare. Du var ett forcerat default och saknade tyvärr såväl förkämpar som ambassadörer. 

Din skapare Microsoft försökte efter version 11 att få över dina användare till din efterträdare [Edge][mse], men utan framgång. På grund av detta fryste dina användare teknologiurvalet till 2013 för alla webbutvecklare, vilket inte var din avsikt alls. Konkurrenter till dig hade fått vind i seglen, och du stod som [förlorare i det andra webbläsarkriget][bw2].

Detta sågs såklart som ett misslyckade för din skapare Microsoft, som nu hade investerat flera år att skapa en efterträdare till dig som ingen ville ha: dina användare var nöjda och visste inte vad de borde sakna, och webbutvecklarna arga för att ha ännu en webbläsare i sin testsvit. Din skapare insåg att hårdare tag krävdes, precis som för IE 6.

* Edge bytte ut den egenutvecklade tekniken till Google Chrome, till webbutvecklarnas mättade glädje, och slutade supporta den förra versionen av Edge (omdöpt till Edge Legacy).
* Under hösten 2020 började flera tjänster, bl a [Microsoft Teams][mst], att sluta stödja dig. 
* I augusti 2021 slutade [Office 365][o365] att stödja dig.
* **Den 15 juni 2022 kommer du att utebli från [alla konsumentversioner av Windows][eol].**

I och med att du stiger ner, möjliggör du massor av tekniker tillkomna efter 2013 för bred användning. En mer komplett lista finns på [caniuse.com][ie11vsff93], men här är några saker jag ser fram emot att börja använda:

 * **WebP, WebM och AVIF.** Bättre bild- och videoformat med högre kompression.
 * **WOFF 2.0.** Bättre typsnittsformat, med webben i åtanke.
 * **HTML Templates.** Gör det enklare att server-rendera JavaScript-templates.
 * ECMAScript 2015 (ES6) **utan Babel**.
 * **IntersectionObserver.** Gör det smidigare att få till bra saker med `position: sticky`.
 * **Shadow DOM.** För att kunna bygga bra webbkomponenter.
 * **Service Workers.** För att PWA:er är en bra sak.
 * **CSS.supports() API.** Gör det så mycket enklare att få till såväl *Progressive enhancement* som *Graceful degradation*.
 * **CSS Variables (Custom Properties).** För att Sass inte ska behöva vara ett krav för att skriva bra stilmallar.
 * **CSS Grids.** Vi har väntat länge på en acceptabel nivå av layout, och CSS Grids ger oss det.
 * **Flexbox gap.** För att det är med `gap` vi ska definiera mellanrum, inte hacks med `padding` och `margin`.
 * `:focus-within`. För att det ska vara enkelt att rödmarkera en div som innehåller ett fält som har tangentbordsfokus.
 * `line-clamp`. För att text borde gå att snygga till så här rättframt!
 * `Background-clip: text`. För mer artistisk frihet.

Den 15 juni 2022 blir det fest till din ära, Internet Explorer!

[1]: https://humanwhocodes.com/blog/2012/08/22/the-innovations-of-internet-explorer/
[bw]: https://en.wikipedia.org/wiki/Browser_wars#First_Browser_War_(1995%E2%80%932001)
[bw2]: https://en.wikipedia.org/wiki/Browser_wars#Second_Browser_War_(2004%E2%80%932017)
[ie6cd]: https://www.microsoft.com/security/blog/2011/03/09/take-action-the-ie6-countdown/
[mst]: https://answers.microsoft.com/en-us/msteams/forum/all/microsoft-teams-will-stop-working-on-internet/91a72837-0dab-40c1-9f29-bef956e46eb0
[o365]: https://docs.microsoft.com/en-us/lifecycle/announcements/m365-ie11-microsoft-edge-legacy
[eol]: https://docs.microsoft.com/en-us/lifecycle/announcements/internet-explorer-11-end-of-support
[ie11vsff93]: https://caniuse.com/?compare=ie+11,firefox+93&compareCats=all
[mse]: https://sv.wikipedia.org/wiki/Microsoft_Edge