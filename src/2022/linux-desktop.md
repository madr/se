---
title: Mitt år med Linux Desktop
date: 2022-11-08
layout: single.hbs
collection: articles
---

Sedan 90-talet har det skämtats om [Year of the Linux desktop][yld]. För egen del har jag aldrig kunnat tvätta av känslan av att vara [systemadmin istället för kreatör][sys].

I dagsläget har jag hamnat i en rätt oväntad sitation: allt jag vill göra med en dator kan göras lika bra på Linux som på Windows.

- Jag kan producera musik.
- Jag kan spela spel.
- Jag kan programmera appar och webb.

## Spel? Lutris, eller Steam med Proton

Steam har satsat ordentligt på [Proton][p], deras fork av wine. Hela mitt Steambibliotek går att installera och köra på linux, utan minsta problem.

Många indiespel, som exempelvis Minecraft, finns redan på Linux.

[Lutris][l] täcker upp alla spel som inte finns på Steam, t ex Blizzards katalog.

## Musikproduktion? REAPER och VST-bryggor

Jag har under hösten 2021 gjort en övergång från Propellerhead Reason till [REAPER][r], en DAW som "alla andra" verkar köra och gilla.

Reaper finns på linux och kan med rätt konfiguration komma ner på ett par millisekunders latens med ett class+compliant USB Audio Interface, där jag valt det billiga men uppskattade **Behringer UMC202HD**. Med [några enkla instruktioner][alpa] så är latensen på nivåer nära Apple, och avsevärt bättre än jag fått till med Windows.

Min musiksetup ser ut såhär 2022, 100% linux powered:

- AMD Ryzen 5 3600, 32GB RAM, 1TB M.2 SSD
- Behringer UMC202HD, Class-compliant
- Arch Linux med Pipewire och [Openbox][^1]
- Reaper DAW
- Ett gäng LV2-plugins
- Yabridge för Windows VSTs
- Roland A-500

Även Ardour och Bitwig finns som alternativ till REAPER.

## Arch är trevligt för att bygga sin DAW

 * Det finns bra guider och dokumentation: Arch wiki har all info man kan tänkas behöva.
 * Inget man inte behöver installeras, och man kan aktivt välja vad man känner sig mest produktiv med.
 * Pipewire, linux och annat är alltid senaste versionen då Arch är rolling release.
 * Reaper, linux-rt etc ligger redan i officiella paketförråden. Arch har musiker och ljudproffs i fokus.
 * AUR har allt annat.

## Andra apparater med Linux

På min bärbara dator, som främst används för bloggande, kodande och på resa, kör jag Fedoras KDE-spin.

På det stora hela så kan jag i egenskap av privatperson numera gå all in på Linux.

[^1]: Till det mesta annat föredrar jag min egen rice baserad på i3wm. För
ett smidigt arbetsflöde med DAWs passar en stacking window manager (traditionell fönsterhantering) bättre, och istället för att dra in en hel skrivbordsmiljö fick det bli Openbox med Helvum och Pcmanfm. Behöver jag paneler och widgets i framtiden går det att fixa, men för nu så är det minimalistiskt och helt ur vägen. 

[yld]: https://www.reddit.com/r/linux/comments/3038d4/when_was_the_first_year_of_the_linux_desktop/
[p]: https://www.howtogeek.com/752212/what-is-proton-for-steam-and-how-does-it-affect-gaming-on-linux/
[l]: https://lutris.net/
[r]: https://www.reaper.fm/
[alpa]: https://madskjeldgaard.dk/posts/audio-setup-arch-2021/
[sys]: /2015/no-sysop/
