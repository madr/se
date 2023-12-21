---
title: "Programmera Python med Helix"
date: 2023-12-23
layout: single.hbs
collection: articles
---

Sedan en tid tillbaka så försöker jag aktivt att ersätta appar baserade på
Electron med andra alternativ.

För att ersätta VSCode har jag länge sneglat åt en vim-liknande editor som
heter [Helix][h], och efter ungefär sex månaders användning börjar jag få upp
farten och närmar mig ett läge där jag kan ersätta VSCode och PyCharm.

Mitt startläge var följande:

- Jag föredrar egentligen texteditorer som alltid låter mig skriva, och har
  aldrig prioriterat effektivitet när det handlar om att skriva kod.
- Av Vim och Emacs, när jag hamnade i detta berömda vägskäl, var Vim det som kändes
  minst knöligt och verkade vara mer vanlig på servrar.
- För riktigt stora projekt och vid behov av debugger, vevar jag igång PyCharm.
  För mindre och snabbare insatser är det dock bra att ha mer än ett alternativ.

## Varför Helix istället för Neovim?

Helix är designat för att likna Vim, med kolon för att hoppa mellan lägena normal,
inmatning och selektion. Helix, precis som Vim, startar blixtsnabbt och har
i stort sett obefintligt footprint i CPU- och RAM-användning. Stora filer är inga
problem, precis som i Vim.

Helix har däremot några fördelar mot Neovim som tilltalade mig skarpt.

- Språkstöd sker via [language servers][ls], där Helix har en lista över [defaults som
  automatiskt försöker startas][dl] när en viss filtyp öppnas. Installera
  rätt language servers och börja skriva kod.
- Multipla textpekare, som är den feature jag använder överlägset mest i VSCode.

Language servers tror jag är framtiden, och den modulära tillämpningen Helix har
känns helt rätt.

Dessa två saker är förmodligen möjliga att få till i NeoVim med plugins, men de gånger
jag försökt har det alltid slutat med att jag gett upp. Jag vill nämligen fokusera på
att _skriva_, inte att konfigurera min editor.

## Min setup för Python

Min setup har följande acceptanskriterier:

- Lintning ska ske löpande.
- Kodformatering ska ske varje gång jag sparar filen.
- importer av beroenden ska föreslås när jag börjar skriva.

Så här ser avsnittet ut i min `languages.toml` för att åstadkomma detta:

```toml
[[language]]
name = "python"
auto-format = true
formatter = { command = "sh", args = ["-c", "ruff check --fix --silent - | ruff format - | ruff --select I --fix --silent -"] }

[language-server.pylsp.config.pylsp.plugins]
rope_autoimport = { enabled = true }
rope = { enabled = true }
ruff = { enabled = true, extendSelect = ["I"]}
```

Några anmärkningar:

- Jag kör sortering av imports, lintning och kodformatering med [Ruff][r]. Fram tills
  nyligen använde jag kombinationen `isort`, `flake8` och `black`, och ser det som en
  uppgradering att bara behöva ett beroende (även om Ruff är aningen omoget).
- För att importera beroenden snabbt används [rope][rp], som även har mycket annat
  bra för att refaktorera pythonkod.

[Installation av språkservern PyLSP][plsp] kan ske på litet olika sätt, beroende på hur Python är
uppsatt. Viktigast är att Helix finner installationen. Kör `hx --health python`, eller
`helix --health python` om aliaset inte finns.

```sh
$ hx --health python
Configured language servers:
  ✓ pylsp: /usr/bin/pylsp
Configured debug adapter: None
Highlight queries: ✓
Textobject queries: ✓
Indent queries: ✓
```

## Slutsats

Jag har kört Helix parallellt med VSCode under året, och har gjort årets [Advent of Code][aoc]
uteslutande i Helix. Jag är helnöjd, och skulle rekommendera den till någon som vill köra Vim,
men ha en något bättre OOTB-upplevelse vad gäller stöd för LSP och multicursors.

[h]: https://helix-editor.com/
[ls]: https://microsoft.github.io/language-server-protocol/
[dl]: https://github.com/helix-editor/helix/wiki/How-to-install-the-default-language-servers
[r]: https://docs.astral.sh/ruff/
[rp]: https://github.com/python-rope/rope
[aoc]: https://adventofcode.com
[plsp]: https://github.com/python-lsp/python-lsp-server
