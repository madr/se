---
title: Saker jag vill lära mig just nu, maj 2021
date: 2021-05-12
layout: single.hbs
collection: articles
---

Efter 15 år i yrket som webb- och systemutvecklare finns det fortfarande massor av saker jag vill lära mig, och gärna skulle vilja bygga något roligt med. Då och då _braindumpar_ jag gärna dessa, med en motivering **varför** jag tror att sakerna skulle ge mig något av värde som mina existerande kunskaper inte kan ge mig.

## Rust

Jag vill lära mig [Rust][rst] för att det är ett mycket omtyckt språk. Det känns som att Rust kommer att bli [boring tech][bt] om ett par år, och jag har idag endast C eller Vala som alternativ för att laborera med [GTK][gtk].

**Vad ger Rust för värde för mig?** Det ger mig ett sätt att skriva statiskt typad, lågnivå-optimerad och _blixtsnabb_ kod, något som jag känner att jag borde göra oftare.

## .NET Core MVC

Jag vill lära mig skriva webbsaker i C#. 

**Vad ger .NET Core MVC för värde för mig?** Nästan ingenting, faktiskt. Python täcker upp mina generella behov och Elixir ger mig realtids-webb som skalar uppåt. Infrastruktursmässigt sett så är jag nöjd med Linuxdistar, Docker och allt annat kring den stacken.

Jag upplever det dock som en negativ sak att inte kunna åtminstone något i .NET-stacken, då det framförallt här hemma i Sverige är otroligt efterfrågat på arbetsmarknaden. Det, och Java. Och då ser jag C# som ett bättre alternativ.

## Svelte

Jag vill använda [Svelte][svt] mer för att bygga frontend. Svelte skiljer sig från React, Angular och Vue genom att inte köra i en virtuell DOM, utan istället kompilera ner allt till ES5/6-kod som är avsevärt snabbare och skonsammare mot hårdvara.

**Vad ger Svelte för värde för mig?** Det ger mer värde för mitt arbetslag än för mig. Jag kan skriva tunga och avancerade saker i React eller Vue, men kan även skriva saker med enbart JavaScript eller TypeScript. Svelte är för de saker som ligger i mitten, då Svelte agerar mer som en kompilator än en runtime. Svelte är också bättre för att börja smått, men långsamt skala uppåt, då komponent-orienterad kod i regel är bättre som [Separation of concerns][soc] än den vanliga webbstacken av JavaScript, CSS och HTML.

## Vega

Jag har i flera år känt ett kall mot att jobba mer med data-visualisering, och [Vega][vg] (med Vega-lite och Vega-embed) har fångat mitt intresse. Projektet kommer från samma skapare som D3. Vega gör att behov av lågnivå-utveckling för att få interaktiva grafer och diagram nästan blir totalt oförsvarbart.

**Vad ger Vega för värde för mig?** Jag vill skapa insikter och värde, snarare än sitta tiotals timmar och skotta SVG-kod. Vega låter mig fokusera på det jag vill.


[vg]: https://vega.github.io/
[svt]: https://svelte.dev/
[gtk]: https://sv.wikipedia.org/wiki/GTK
[soc]: https://sv.wikipedia.org/wiki/Inkapsling_(Separation_of_Concerns)
[rst]: https://www.rust-lang.org/
[bt]: https://mcfunley.com/choose-boring-technology
[1]: https://en.wikipedia.org/wiki/Posterous
[2]: https://en.wikipedia.org/wiki/Platform_as_a_service
[3]: https://en.wikipedia.org/wiki/Web_template_system#Static_site_generators