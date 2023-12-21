---
title: Magiska känslan från Phoenix LiveView
original: The Business Case For LiveView Is Strong Enough To Change How You Staff Your Dev Team
source: https://amattn.com/p/elixir_phoenix_the_business_case_for_liveview_strong_enough_to_change_how_you_staff_your_dev_team.html
date: 2021-01-15
collection: links
layout: single.hbs
---

> What you get is the speed, responsiveness and UX performance exceeding that of a React/Vue/javascript front end framework against a server API, but you haven’t written a line of javascript.
>
> This is a magical feeling.

Kan verkligen bara hålla med.

Den här vägen, att skapa ett abstraktionslager som partiellt renderar om delar av sidor i realtid med serverside-renderad HTML över websockets, känner jag är framtiden.

[Vue][1], [React][2], [Ember][3] och [Angular][4] har visat världen vad som är möjligt, men rent arkitekturellt är det dags att
sluta att blint tro på att [Single Page Applications][7] är ett måste för att skapa en bra användar- och utvecklarupplevelse.

Elixir faller inte alla i smaken, men denna rörelse finns som tur är i flera stora communities.

- .NET har [Blazor][5].
- PHP har [Laravel LiveWire][10].
- Rails har [Hotwire][6].

Den senare är agnostisk, och kommer förmodligen
portas till såväl [Django][9] som [Laravel][8].

[1]: https://vuejs.org/
[2]: https://reactjs.org/
[3]: https://emberjs.com/
[4]: https://angular.io/
[5]: https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor
[6]: https://hotwire.dev/
[7]: https://en.wikipedia.org/wiki/Single-page_application
[8]: https://github.com/jcergolj/hot-la-wire
[9]: https://github.com/hotwire-django/hotwire-django
[10]: https://laravel-livewire.com/
