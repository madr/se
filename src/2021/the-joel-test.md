---
title: Är The Joel test fortfarande relevant?
date: 2021-02-04
layout: single.hbs
collection: articles
---

Detta är **The Joel Test**, först publicerat i
[The Joel Test: 12 Steps to Better Code][1]:

> 1. Do you use source control?
> 1. Can you make a build in one step?
> 1. Do you make daily builds?
> 1. Do you have a bug database?
> 1. Do you fix bugs before writing new code?
> 1. Do you have an up-to-date schedule?
> 1. Do you have a spec?
> 1. Do programmers have quiet working conditions?
> 1. Do you use the best tools money can buy?
> 1. Do you have testers?
> 1. Do new candidates write code during their interview?
> 1. Do you do hallway usability testing?

Det är 12 ja/nej-frågor som är tänkt att agera självtest åt organisationer där
det arbetar programmerare. I detta inlägg hade jag tänkt att skriva litet om hur
jag tolkar dessa 12 frågor, och försöka sätta dem i kontexten för
webbutveckling 2021.

## Använder ni versionshantering?

Denna är oförändrad sedan 2000. Använd git, perforce, SVN eller CVS: det viktiga
är inte vilket verktyg, utan att det används.

Fördelarna är så många och självklara att jag inte tänker skriva något om det
här: jag hänvisar istället till blogginlägget ovan.

## Kan ni göra en build i ett steg?

I kontexten webbutveckling så ska det gå att skriva ett kommando eller klicka på
en knapp för att skeppa en ny version till produktion.

Det får ta tid och logga allt som sker, så länge det kan göras i ett enda steg.

## Gör ni dagliga builds?

I dagens webbutvecklings-kontext är frågan ett steg längre:
_"Använder ni ett CI-verktyg?"_

Det bör alla göra, åtminstone på de stabila brancherna i kod-repositoriet
(`master` eller `main` i git). Där bör allt göras, exempelvis:

- Köra frontend-tester med JavaScript
- Köra backend-tester
- Nedladdning av alla dependencies
- Bundling av alla frontend-assets
- Kompilering av all källkod till något skeppbart (tarball, jar, vad som helst).
- Kompilering av språkfiler.

## Har ni en bugg-databas?

Fortfarande aktuell!

## Fixar ni buggar innan ni skriver ny kod?

Knivig fråga. Min tolkning är att frågan egentligen är
_"Om en bugg upptäcks, rättar ni den på en gång eller senare?"_

Detta är inte helt enkelt att få till i praktiken, men är förmodligen något man
vill sträva efter. Detta är inte helt olikt [No Broken Windows-teorin][2].

Att lösa buggar direkt, med full kraft och med synsättet att det är en blocker
för annan kod, är förmodligen vad som efterfrågas.

## Har ni en uppdaterad planering?

Jag tolkar denna som

> vet alla vad de ska göra nu och härnäst, både för egen del och sina närmaste
> kollegors, och hur mycket tid varje sak förväntas ta?

Det finns även en antydan till att planeringen justeras och ändras över tid, och
att det är viktigt att **alla** är med på detta.

I vilket format planeringen står nedskriven eller utformas tycker jag inte är så
viktigt, bara det görs. Varje enskild organisation känner nog bäst om det räcker
med en lista över datum på en whiteboard, eller om ett detaljerat gant-diagram
är vad som krävs.

_Iterationer_, som är rätt populärt nu i jämförelse med år 2000, är ett bra
verktyg för att med jämna mellanrum få en reality check på var man befinner sig
i planeringen.

## Har ni en spec?

Många mindre team jobbar förmodligen inte med _tekniska specifikationer_ längre,
då sådana är skrivna i ett format som tar tid och energi att sammanställa, och
som gör dem svåra att ändra på vid behov.

Min liberala tolkning här är

> är alla överens om vad som förväntas skeppas i närtid, om ett tag och längre
> fram?

Tidigare nämnda _iterationer_ hjälper till här, då de ger en återkommande
kalenderhändelse där man kan justera förväntningar och ändra prioritet på saker.

## Har programmerarna en tyst arbetsmiljö?

Fortfarande aktuell. Öppna landskapen har befäst sig mer de senaste 20 åren, och
även om det finns bättre gadgets så är det inte jämförbart med att ges eget rum
med möjlighet att stänga dörren.

Jag har under mina 15 år som verksam webbutvecklare aldrig haft en stängd dörr,
annat än under [pandemin](../../2020/covid19).

## Har ni de bästa verktygen som kan köpas för pengar?

Fortfarande aktuell. Snåla inte på ergonomistöd, tangentbord, pekdon, belysning, mikrofoner,
hörlurar, bildskärmar och datorer. Värdet bra utrustning ger överskrider
vida det höga inköpspriset.

Detsamma gäller alla devops- och DX-verktyg som kan tänkas spara värdefull tid
för

- Om loggar är viktigt att läsa, överväg [Kibana](https://www.elastic.co/kibana)
  eller annan LaaS.
- Om mycket fel uppstår i driftmiljön, överväg [Sentry](https://sentry.io/welcome/).
- Om oro för större incidenter finns, överväg
  [Pingdom](https://www.pingdom.com/) eller [Status Page](statuspage.io).
- Och så vidare.

## Har ni testare?

Inte lika applicerbart idag, särskilt inte i webbutvecklingssammanhang där
A/B-testning eller automatiska tester med verktyg som exempelvis [Cypress](https://www.cypress.io/)
skulle kunna användas.

Att få arbeta med riktiga testare är dock en sann ynnest när behovet är motiverat.

## Får kandidater skriva kod under sin intervju?

Fortfarande aktuell.

## Gör ni "Hallway usability testing"?

[Hallway usability testing][3] kan översättas litet slarvigt till
_"Spontan användbarhetstestning"_, där en eller flera personer som går i ett kontorslandskap
eller en korridor genomför ett spontant användbarhetstest genom att man frågar
om de har en minut. Om så är fallet, visas en vy som personen eller personerna
får interagera med.

Kul grej som kan främja bra kultur, men inte applicerbart i alla miljöer. Jag
tror dock att det objektivt är en god sak att uppmuntra.

[1]: https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code/
[2]: https://sv.wikipedia.org/wiki/Broken_Windows
[3]: https://www.techopedia.com/definition/30678/hallway-usability-testing
