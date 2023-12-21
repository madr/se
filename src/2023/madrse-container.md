---
title: "Metalsmith i container"
date: 2023-07-19
layout: single.hbs
collection: articles
---

En sak jag länge varit sugen på att utvärdera är att bli av med beroendet till node.js i mindre, simplare projekt. Som denna webbplats, exempelvis, som enbart behöver det för att transformera markdown-filer till HTML-dokument med [Metalsmith](https://metalsmith.io/).

Det enklaste sättet att göra det på är att använda sig av _containers_, där allt som behövs ligger i en image. Detta inlägg beskriver hur jag gjorde för att få till det.

## Indentifiera vilka volymer som behövs

Jag behöver i princip tre volymer för att kunna återanvända samma container image flera gånger för att bygga min webbplats.

 * `src` - Metalsmiths _source directory_, alltså alla filer som ska transformeras.
 * `pub` - Metalsmiths _target directory_, dvs resultatet av Metalsmith.
 * `assets` - alla statiska filer jag bara vill bifoga som de är, t ex bilder, CSS-filer, redan kompilerade webbkomponenter och liknande.

## Containerfile

Ser ut såhär, i sin enkla helhet.

    FROM node:20-alpine AS base
    WORKDIR /app
    FROM base AS deps
    COPY package*.json ./
    RUN npm install
    FROM deps AS final
    RUN mkdir ./assets ./pub ./src
    VOLUME ["./assets", "./pub", "./src"]
    COPY . .
    ENTRYPOINT ["node", "index.js"]

... med några väl valda **ignores**.

## Bygga container image lokalt

Jag gör detta med Buildah, men det går lika bra att göra med Docker.

    buildah build --net host .

## Kör container imagen lokalt för att bygga webbplatsen

Jag gör detta med Podman, och monterar de tre volymerna.

    podman run \
    --net host \
    -ti \
    --volume ./dist:/app/pub \
    --volume ../../Sync/Rahvin/madrse/src:/app/src \
    --volume ../../Sync/Rahvin/madrse/assets:/app/assets \
    [container id]

Ovanstående volymsökvägar råkar vara det jag använder för stunden. Katalogerna behöver såklart finnas på filsystemet.

Ersätt `[container-id]` med det ID som gavs av Buildah.

## Hosta container images på Github Packages

Då jag har koden på Github så passade jag på att lägga in en action som bygger och publicerar container imagen automatiskt. Då blir det ännu enklare att bygga sajten, eftersom jag då bara behöver hämta imagen från Github Packages istället för att bygga den ochh hålla repa på container-id.

    podman run \
    --net host \
    -ti \
    --volume ./dist:/app/pub \
    --volume ../../Sync/Rahvin/madrse/src:/app/src \
    --volume ../../Sync/Rahvin/madrse/assets:/app/assets \
    ghcr.io/madr/19:main

Två saker extra krävs för detta.

 * Skapa upp en action för att bygga och publicera Docker images.
 * Använd Dockers namngivning, dvs Dockerfile och .dockerignore. Podman och Buildah finns ej på Github Actions i skrivande stund, så `Containerfile` och `.containerignore` kommer inte att fungera.
