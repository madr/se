---
title: "DAW med Arch linux, Pipewire, Reaper och YABridge"
date: 2023-01-01
layout: single.hbs
collection: articles
---

_OBS! Detta går precis lika bra att köra med Fedora, Debian eller annan distribution som förinstallerar så minimalt som möjligt. Se bara till att ha fräsch version av Pipewire._

_OBS! Förkunskaper om linux och tidigare erfarenheter av att konfigurera DAWs är förmodligen ett plus, då det kan gå fel på flera ställen på vägen. Detta rekommenderas inte för nybörjare._

## Välj hårdvara

- Researcha ljudkortet så att det fungerar med linux. Googla, kika på reddit.
- Ett par extra gånger mer än nödvändigt skadar inte!
- Generellt sett så kan ett begagnat ljudkort förmodligen fungera bättre än ett sprillans nytt.

## Installera Arch

- Använd archinstall eller kör EndeavourOS om Archs standardinstallation inte känns lockande.
- Installera ingenting annat än grundsystemet till att börja med.

## Konfigurera systemet för pro audio

- Installera Pipewire och Pipewire-jack
- Följ guiden på [Arch wiki](https://wiki.archlinux.org/title/Professional_audio).
- Därefter denna guide: [Setting up Arch Linux for audio performance](https://madskjeldgaard.dk/posts/audio-setup-arch-2021/)

## Välj ett grafiskt gränssnitt

Kör på det som känns mest bekvämt och som inte är i vägen för dig som kreatör.

- Undvik krävande DEs som installerar för många program du inte kommer att använda, som t ex GNOME, Pantheon, KDE eller Cinnamon.
- En lättviktig DE som t ex XFCE, LXDE eller LXQT är att föredra.
- Eller, om det föredras: välj en tiling window manager, som t ex i3, Qtile eller bswm.

Jag föredrar att köra en slimmad Openbox för att undvika onödiga processer.

## Installera Reaper

Går precis lika bra att köra Bitwig, Ardour eller annan DAW. Reaper är dock det jag använder.

- Installera `reaper`. Använd JACK i inställningarna, detta kommer att spela via Pipewire.

## Valfritt: Installera VST-brygga

Reaper har bra plugins som det är, men om du har några VSTs som bara kör på Windows, behövs en brygga som får dem att upptäckas av Reaper.

- Installera yabridge och wine: `wine`, `yabridge`, `yabridgectl`.
- Installera sedan VSTerna med wine, och lägg till dem i yabridge.

## Om du kör fast

- r/linuxaudio
- linuxaudio.org
