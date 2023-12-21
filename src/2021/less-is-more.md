---
title: Vad är det minsta som krävs för att publicera på webben?
date: 2021-01-07
layout: single.hbs
collection: articles
---

Jag brukar ofta, när folk som visar intresse, nämna att jag haft minst en
hemsida på Internet **sedan hösten 1997**. 

Jag var med min blygsamma ålder på 12 år inte en del av IT-bubblan, men är säker
på att jag varit det om jag varit i högstadieålder istället.

Min tidslinje har på sistone uppvisat att en cirkel har slutits.

* 1997-2001 publicerade jag statisk HTML och CSS, med FTP.
* 2002-2010 publicerade jag med serverrenderat innehåll. Datan var lagrad i en databas
  och hanterades via ett hemknackat CMS, och koden för att rendera HTML bodde på
  egen server eller webbhotell.
* 2010-2012 ersatte jag mina egna hemmaknack med etablerade CMS. Med tiden
  ledsnade jag också på att drifta själv, varvid jag migrerade till
  en bloggtjänst.
* 2012-2015 återgick jag till ett egenutvecklat CMS, som driftades på en
  [Platform as a Service][2].
* 2015-nu: all publicering sker med statisk HTML och CSS, på diverse privata
  webbservrar med stöd för kryptering (HTTPS).

De senaste fem åren är, när allt kommer omkring, mer likt hur det var i slutet
av 1990-talet.

## Hur jag skriver och sedan publicerar

Min skriv- och publiceringsprocess är lätt minimalistisk.

1. Jag skriver mina ord direkt i en textredigerare.
2. Formattering, bildsättning och hyperlänkning görs med hjälp av [Markdown](https://commonmark.org/).
3. Markdown-filerna omvandlas till HTML, och en hel webbplats bestående av
   HTML-dokument med tillhörande stilmall genereras. Till detta används en
   [statisk webbplats-generator][3].
4. Webbplatsen publiceras genom att filerna laddas upp på en [Virtuell server](https://sv.wikipedia.org/wiki/Virtuell_server).

För detta använder jag några verktyg som jag tycker är bäst lämpade för
ändamålet. I en terminal brukar det se ut såhär när jag gör en ny publicering.

```
node index.js
rsync -alPvz ./pub/* madr@demandred:/srv/madr.se
```

## Är det verkligen inte mer?

Nej, det är det inte. Jag har litet JavaScript för att ha en interaktiv karta på
en av sidorna, och kan om jag så önskar lägga till besöksspårning om jag vill ha
mer data om mina besökare.

Jag använde under en lång tid [GitHub pages](https://pages.github.com/) för att 
publicera, men mitt intresse och min nyfikenhet för devOps gjorde till slut
att jag själv valde att återgå till en VPS. Det mest avancerade jag hanterat på
denna är att konfigurera [Certbot](https://certbot.eff.org/), som ordnar ett 
certifikat jag kan använda för köra HTTPS.

## Kontrast

Jag driver andra projekt där jag modellerar, cachar, indexerar och
lagrar data. HTML genereras av webbramverk eller CMS. CSS och JavaScript
struktureras och planeras, och körs genom en verktygskedja som obfuscerar koden
och gör den produktionsredo.

För allt detta krävs 5-8 program (som sandboxas med Docker) och 10-15
terminalfönster (som samlas med Tmux). 

Detta driftsätts sedan med Kubernetes, eller någon sorts PaaS.

Jag känner mig såklart produktiv i detta också, men jag upplever ändå viss
lättnad av att skala bort allt utom det absolut nödvändigaste.

## Omfamna minimalism

Jag kan varmt rekommendera alla att testa att lägga saker åt sidan och fokusera
på att skriva ord och publicera HTML. Det är ett skönt avbrott, och verkar
aldrig bli omodernt eller gå ur tiden.

[1]: https://en.wikipedia.org/wiki/Posterous
[2]: https://en.wikipedia.org/wiki/Platform_as_a_service
[3]: https://en.wikipedia.org/wiki/Web_template_system#Static_site_generators
