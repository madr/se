---
title: Grafiska gränssnitts komplexitet
original: The complexity that lives in the GUI
source: https://blog.royalsloth.eu/posts/the-complexity-that-lives-in-the-gui/
date: 2021-02-15
collection: links
layout: single.hbs
---

> * **Connect the boxes**: create the user avatar component and pass its instance to the inventory table component. Whenever the edit state of the inventory table changes, the business logic in the inventory table should also trigger a state change in the user avatar component with the help of the user avatar’s public API.
> * **Lift the state up**: move the internal state of the user avatar component and the state of the inventory table into a separate box/class. The logic of the user avatar and inventory table component will still be neatly separated in their own boxes, but they will be able to communicate without inventory table needing the direct access to the user avatar.
> * **Introduce a message bus**: connect the inventory table and the user avatar component to the shared pipe that is used for distributing events in the application. The user avatar component subscribes to the message bus and every time it receives a table edit event, it executes an appropriate action (e.g turn the light on).

Jag gillar denna skarpt! Det som gör den riktigt bra är att den är skriven på ett teknik-agnostiskt sätt.

En person som skriver saker i LiveView eller Hotwire (som hanterar state
backend) tar till sig idéerna och koncepten lika väl som folk som bara arbetar i
rena SPA:er med React, Vue, Angular eller Elm.

Min egen inställning efter att ha byggt webbgränssnitt 15 år som yrkesverksam är
att fokusera på leverans snarare än perfektion: Göra om är billigt, ändra befintligt efter nya lärdomar är dyrt.