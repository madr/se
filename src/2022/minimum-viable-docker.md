---
title: Minimum viable setup för webbprojekt i containers på VPS
date: 2022-10-19
layout: single.hbs
collection: articles
---

Ett av mina favorit-memes för containers är denna:

![Docker poison meme](../../img/docker-meme.jpg)

Allvaret bakom skämtet är att _containers_ inte alls är viktigt. Att deploya till VPS:er man själv är ensam ägare till kräver sällan den typen av investering. Att deploya via SFTP eller git post-receive hooks räcker längre än man kan tro, och det är snarare ansible eller något motsvarande som borde användas om man vill göra livet lättare för sig.

Med detta sagt så hade jag ett projekt där det passade att labba litet med detta, så jag ställde mig själv frågan: vad är the _minimum viable setup_ för att sköta deployer med containers istället för källkod?

Min VPS är minimalt confad och körde innan detta projekt i stort sett bara en nginx med en wwwroot innehållande statisk HTML (denna webbplats). SSL-certifikaten hanteras av [Certbot](https://certbot.eff.org/).

Vinsterna med containers i mitt fall är uppenbara.

- Jag slipper installera mer paket (för Python, Postgres, Elixir, Node.js eller vad jag nu kodar projekt i) på min VPS.
- Jag slipper förlita mig på git eller sshd för att kunna göra en deploy.
- Jag slipper bli bromsad av att Ubuntu server, som jag har som operativsystem på min VPS, inte har samma versioner av saker som min lokala devmiljö.

Projektet jag ville driftsätta är skrivet i Django, och kräver således Python 3 och SQLite (då jag inte har behov av musklerna av en "riktig" databas).

Jag vill vidare köra containern bakom [nginx](https://nginx.org/en/), med SSL-certifikat som hanteras av Certbot.

Det här är de steg jag vidtog för att få upp allt.

## 1/7: Bygg en container av projektet

En container, oavsett om den byggs med Docker eller Podman, definieras enklast med en _Dockerfile_.

Det här är en mycket förenklad uppsättning, där en enda container behövs för att köra hela applikationen. Databasen ligger i `/app/data` och görs tillgänglig som en volym för att kunna backupas och leva kvar mellan deployer. Applikationsservern sparas som en unix-socket som delas via volym, så att nginx kommer åt den.

```docker
FROM python:3 as deps
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
ENV DEBUG=0
WORKDIR /app
COPY requirements.txt /app/
RUN pip install -r requirements.txt

FROM deps AS source
COPY ./src /app/

FROM source AS db
RUN mkdir -p /app/data
VOLUME /app/data
RUN ./manage.py migrate

FROM db AS finished

VOLUME /run

# may demand chmod 777 on host to avoid "permission denied errors"
CMD waitress-serve --socket=/run/waitress.sock example:wsgi.application
```

Det är också en god idé att skapa filen [.dockerignore](di) för att inte skicka över mer än absolut nödvändigt i containern, och därmed hålla dess storlek på en minimal nivå.

För detta projekt är det primärt git-saker och python-cacher som berörs.

    __pycache__
    venv
    .git
    .github
    .gitignore
    README
    todo.txt
    *.sqlite3

För att testa om containern funkar, bygg en avbild.

    docker build .

Det ska sedan gå att gå in på http://localhost:13371 och få en Django-app visad.

För referens, så är nedanstående en startplatta för framtida, liknande setups.

```docker
FROM some-base:v as deps

WORKDIR /app

# install dependencies

FROM deps AS source

COPY ./src /app/

FROM source AS finished

# Expose unix socket
VOLUME /run

# CMD to start application
CMD start-app.sh
```

## 2/7: Gör avbilder av containern tillgänglig för VPS

Det finns flera strategier att publicera container-avbilder, de flesta sätt kostar ingenting.

Jag väljer aktivt bort alternativ som tvingar mig att göra imagen publik, då jag i detta projekt inte är intresserad av att ge andra åtkomst. Det gör att exempelvis [Docker hub](https://hub.docker.com) inte är ett alternativ.

Om koden ligger på Github, kan [Github Actions](https://docs.github.com/en/packages/managing-github-packages-using-github-actions-workflows/publishing-and-installing-a-package-with-github-actions) automatisera bygget och publicera containern på [Github Packages](https://github.com/features/packages). Då kan VPS:en hämta senaste versionen av containern med `docker pull`. Valet finns också att göra källkoden och container-avbilden privata, alltså ej synlig för andra.

- Fördelar: inget extra utöver Docker eller Podman krävs på på VPS.
- Nackdelar: beroende av Github för att deploya saker, vilket kan kännas obekvämt.

Det går även att sätta upp ett bare git repo på VPS:en, och starta ett eget bygge av containern med en post-receive hook.

- Fördelar: Inget beroende av Github, Docker Hub eller annan hosting av container-avbilder.
- Nackdelar: Kräver mer setup och att git installeras på VPS. Om diskutrymme är kritiskt så behövs även schemalagda städrutiner för gamla container-avbilder skapas och konfigureras.

Jag valde alternativ 1, med **privat repo** och **privat package**. Det kan dock ändras om Github bestämmer sig för att jag inte kan göra det gratis i framtiden.

Det finns en Github Action färdig och klar för att bygga och publicera docker images, så använd denna.

## 3/7: Installera Docker (eller Podman) på VPS

OBS! Min VPS kör Ubuntu Server 20.04 LTS, och på denna finns inte [Podman](https://podman.io/) som alternativ. Podman går precis lika bra för vad som skrivs om här, och rekommenderas varmt som ersättare av [flera bra skäl](https://pacroy.com/try-podman-buildah-and-skopeo-instead-of-docker-c45a0e9394b0).

Nginx och Certbot är på plats sedan tidigare på VPS:en, och det är bara Docker CE som behövs.

    apt-get update
    apt-get install docker-ce

Lägg till din användare i Dockergruppen för att slippa köra som root.

    usermod -aG docker $USER

Dubbelkolla så att docker kör:

    systemctl status docker

## 4/7: Starta container-avbilden på VPS

Hämta eller bygg en avbild av containern beroende på strategin som valts innan. För att hämta ser det ut såhär:

    docker login ghcr.io
    docker pull ghcr.io/madr/example-app:main

Mer info om detta finns i dokumentationen för Github Pages.

Starta därefter container-avbilden. Genom att ge ett namn på den körande container-avbilden blir den enklare att hantera med Dockers cli. Montera också volymen för `/app/data` så att sqlite-databasfilen blir persistent mellan deployer. Använd en absolut sökväg så att volymen blir lätt att hitta. Som package används här `example-app` - den riktiga paketnamnet är ett annat.

    docker run -d --name example -it \
    -v ./run:/run \
    -v ./exampledb:/app/data \
    ghcr.io/madr/example-app:main

För att deploya en annan version som ersätter existerande version, ser det ut såhär. Som package används här `example-app` - den riktiga paketnamnet är ett annat.

    docker pull ghcr.io/madr/example-app:main
    docker stop example
    docker rm example
    docker run -d --name example -it \
    -v ./run:/run \
    -v ./exampledb:/app/data \
    ghcr.io/madr/example-app:main

Notera här att jag här valt att bort den gamla versionen direkt. Att rollbacka till en äldre version krävs alltså en ny pull!

## 5/7: Exponera containern för webbtrafik med nginx

Tanken är att köra Django inuti containern, och att bara köra en reverse proxy för nginx på den delade unix-socketen.

Som domän används här `example.madr.se` - den riktiga domänen är en annan.

    cat <<END /etc/nginx/sites-available/example.madr.se
    upstream app_server {
        server unix:/home/example/run/waitress.sock fail_timeout=0;
    }
    server {
        listen 80 default_server;
        return 444;
    }
    server {
        listen 80 deferred;
        client_max_body_size 4G;
        server_name example.com www.example.com;
        keepalive_timeout 5;
        root /home/example/static;
        location / {
            try_files $uri @proxy_to_app;
        }
        location @proxy_to_app {
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            proxy_set_header Host $http_host;
            proxy_redirect off;
            proxy_pass http://app_server;
        }
    }
    END

För att se så att allt lirar, validera config:

    service nginx configtest

Om allt gick bra, aktivera siten genom att symlänka.

    ln -s /etc/nginx/sites-available/example.madr.se /etc/nginx/sites-enabled/example.madr.se

Och starta om nginx.

    systemctl restart nginx

## 6/7: Hantera SSL-certifikat för projektet med Certbot

Hisspitchen för Certbot är att den automatiserar uppskapandet av SSL-certifikat för att kunna köra dina självhostade webbplatser med HTTPS. Let's Encrypt står för utfärdandet av certifikat, så det kostar ingenting.

Är Certbot inte installerat, så finns en bra guide.

Med Certbot på plats, kör detta kommando för att generera certifikat, populera nginx-configen med nödvändig config och schemalägga automatisk förnyelse av certifikat. Scriptet startar även om nginx.

    certbot --nginx -d example.madr.se

Klart! Nu ligger docker-containern uppe i produktion, där den lyssnar på port 80 och är krypterad med SSL.

## 7/7: Konfigurera brandvägg på VPS (valfritt)

Detta steg är valfritt, men rekommenderat.

Ubuntu Server kör `ufw`, så jag tillåter SSH, HTTP och HTTPS och nekar allt annat.

    ufw default deny incoming
    ufw allow in ssh
    ufw allow in http
    ufw allow in https
    ufw enable

Docker struntar tyvärr i detta eftersom egna `iptables` tillämpas, så för att få Docker att respektera `ufw` krävs litet config.

Lägg till följande i /etc/docker/daemon.json:

    "iptables": true,

Finns inte filen, skapa den istället:

    cat <<END > /etc/docker/daemon.json
    {"iptables":true}
    END

Inaktivera även `iptables` för `dockerd` genom att lägga till `--iptables=false` i `DOCKER_OPTS`.

    echo 'DOCKER_OPTS="--iptables=false"' >> /etc/default/docker

Starta sedan om Docker.

    systemctl restart docker

## Nästa steg

Detta är _minimum viable setup_, så det finns flera saker som är bra att göra.

- Sätt upp ett script som hämtar hem ny version av container-avbilder, och deploya denna till produktion. Kan till och med placeras i en crontab för att få _Continuous Delivery_.
- Städa upp bland hämtade container-avbilder, med ett cronjob eller liknande.
- Som en akademisk övning, testa att sätta upp 3 körande containers och använd nginx som lastbalanserare.
