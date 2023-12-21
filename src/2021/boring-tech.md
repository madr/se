---
title: Om att välja tråkiga teknologier
original: Choose Boring Technology
source: https://mcfunley.com/choose-boring-technology
date: 2021-05-12
collection: links
layout: single.hbs
---

> What counts as boring? That’s a little tricky. “Boring” should not be conflated with “bad.” There is technology out there that is both boring and bad. You should not use any of that. But there are many choices of technology that are boring and good, or at least good enough. MySQL is boring. Postgres is boring. PHP is boring. Python is boring. Memcached is boring. Squid is boring. Cron is boring.

Jag kommer på mig själv med att prata om "boring tech" ganska ofta, särskilt när jag sitter i samtal med kollegor som hittar något nytt och skinande som vore roligt att testa. Den är från 2015, men är verkligen otroligt relevant.

T ex så tar den upp konceptet med _Innovation tokens_. Den pratar även om _unknowns_, och _unknown unknowns_.

> When choosing technology, you have both known **unknowns** and **unknown unknowns**.
>
>   * A known unknown is something like: *we don’t know what happens when this database hits 100% CPU.*
>   * An unknown unknown is something like: *geez it didn’t even occur to us that writing stats would cause GC pauses.*

Även denna tankelek och prov på kreativitet är värd att bokmärka artikeln för, och diskutera med sitt team.

> One of the most worthwhile exercises I recommend here is to **consider how you would solve your immediate problem without adding anything new**. First, posing this question should detect the situation where the “problem” is that someone really wants to use the technology. If that is the case, you should immediately abort.
> 
> It can be amazing how far a small set of technology choices can go. The answer to this question in practice is almost never “we can’t do it,” it’s usually just somewhere on the spectrum of “well, we could do it, but it would be too hard”. If you think you can’t accomplish your goals with what you’ve got now, you are probably just not thinking creatively enough.

