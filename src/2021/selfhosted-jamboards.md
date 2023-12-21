---
title: 4 öppna alternativ till Miro och Google Jamboard att hosta själv
date: 2021-08-25
layout: single.hbs
collection: articles
---

Jag gillar skarpt att visualisera mitt arbetsflöde ända sedan jag först läste på om [Kanban][kb]. Istället för ett par stela spalter så är det skönt att ha alla tillstånd en uppgift kan ha med i en visualisering för att göra det tydligt. Det är också skönt att ha möjligheten att ta bort eller lägga till tillstånd när behov uppstår.

Allra bäst är det att ha en generös whiteboard eller vägg med post-its, som alla i ens team kan samlas runt tavlan. I tider av **hemarbete och digitalisering** så behövs dock något liknande för videosamtal för att täcka upp behovet.

Det finns även andra behov av whiteboard-liknande samarbetsverktyg, t ex för planeringsmöten, workshops eller teammöten. Att arbeta på frihand på en stor yta ska inte underskattas, särskilt inte med en väl tilltagen pekskärm.

På jobbet har jag haft bra erfarenhet av [Miro][m] och [Google Jamboard][gjb]. I tider av GDPR, Cloud Acts och amerikanska molntjänster ville jag dock se om det finns alternativ till dessa.

 * Möjligt att hosta själv, helst med Docker.
 * Webbläsarbaserat.
 * Gärna öppen källkod, eller åtminstone en rimlig licenspeng.
 * Samarbetsverktyg, där 2 eller fler kan göra saker samtidigt i realtid. Gärna med touchstöd, men inget krav.
 * Minimum: post-its, text, ritverktyg, enklare geometriska figurer (rektanglar, linjer, pilar), möjlighet att länka till saker.
 * Bonus: Möjlighet till videosamtal med alla deltagare, fler ritfunktioner.

Utifrån denna lista kikade jag på litet alternativ, och kunde se att det finns god mognad på alternativen som släpps under öppen källkod.

## Excalidraw

[Excalidraw][ex] är en whiteboard, kort och gott, med stöd för diagram och flödesscheman. 

> Virtual whiteboard for sketching hand-drawn like diagrams. Collaborative and end-to-end encrypted.

Rakt in i en whiteboard. Det går att slå på delning, och även att bädda in whiteboards med som en React-komponent i webappar skrivna i React.

## Spacedeck

[Spacedeck][sd] är mer åt whiteboard-hållet, och liknar Google Jamboard mest med ett enkelt och tydligt gränssnitt.

> A web based, real time, collaborative whiteboard application with rich media support. 

Detta var tidigare en kommersiell SaaS, men som släpptes som öppen källkod när den ursprungliga tjänsten stängde ner 2018.

## MiroTalk

[MiroTalk][mt] sätter onekligen ribban högt för vad som är möjligt att åstadkomma under öppen källkod.

> A free WebRTC browser-based video call, chat and screen sharing

Det är en rumsorienterad lösning för videosamtal, där alla deltagare i ett rum kan se whiteboards, chatta och dela skärm.

Det är ett ambitiöst webbaserat samabetsverktyg som försöker mätta alla munnar. Jag är inte helt såld på gränssnittet, men det funkar helt okej. 

Det är inte centrerat kring en whiteboard-yta, men kan nog komma till användning för utbildningar eller workshops.

## Nettu-meet

[Nettu-meet][nm] är mer för brainstorming och workshops.

> An open source video conference web application designed for interactive online tutoring.

Detta är förmodligen ett trevligt verktyg för att hålla i föreläsningar med en whiteboard, eller för att tillsammans jobba på något i frihand. 
Man skapar en whiteboard, bjuder in folk till videosamtal och hamnar direkt på ytan. Whiteboarden blir inte persistent, vad jag kan se.

## Mer tips

Jag hittade dessa via [en tråd på reddit][r], där även andra tjänster nämns.

[kb]: https://projektledning.se/kanban/
[m]: https://miro.com
[gjb]: https://edu.google.com/products/jamboard/
[mt]: https://github.com/miroslavpejic85/mirotalk
[sd]: https://spacedeck.com/
[nm]: https://github.com/fmeringdal/nettu-meet
[r]: https://www.reddit.com/r/selfhosted/comments/nyqp33/any_alternative_for_miro_whiteboard_if_possible/
[ex]: https://github.com/excalidraw/excalidraw