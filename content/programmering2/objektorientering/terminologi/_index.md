---
title: "Termer"
date: 2024-08-27T23:26:15Z
draft: false
weight: 100
---

Detta är menat som en strukturerad lista som ska ge dig en översikt över de olika orden och termerna som förekommer. Att ha dessa med sig inför framtiden är bra, och dessutom hjälpsamt för dig när du ska förklara något för någon annan.

|Ord|Förklarning|
|-|-|
|Objekt|En typ likt `int`, `float`, `string` och så vidare. Ett objekt är datorns sätt att förvara variabler och metoder som har en samhörighet (relation).
|Fält|Är ett C#-specifikt ord för en variabel som är en del av en klass (objekt). Kallas för *medlemsvariabel* i andra språk. Denna variabel förvaras **alltid** inuti ett objekt. Variablen existerar endast så länge objektet finns.
|Attribut|Är det datavetenskapliga ordet för att beskriva en variabels tillhörighet i ett objekt. I diagramritningar förekommer detta namn.
|Medlemsvariabel| Är ett annat ord för fält som är gemensamt inom objektorienterade programmeringsspråk. c
|Egenskap|En typ av metod som hanterar ens variabler på ett kontrollerat vis. En egenskap kan bestämma **vem** som kan ändra på variablen, och ifall något speciellt ska hända ifall den ändras. Dessutom kan den också bestämma synligheten eller lägga hämtnongen av variablen bakom villkor.
|Beteenden|Är metoder som är placerade i ett objekt. De verkar oftast bara inom objektet, eller agerar som en brygga mellan flera olika objekt. Metoderna kallas även för *medlemsfunktioner* i vardagligt tal.
|Konstruktor|Är en sorts metod som hjälper en att fylla fält eller göra andra beteenden som krävs för att objektet ska fungera.
|Synlighet|I objekt kan man kontrollera vem som kommer åt en variabel, antingen kan andra objekt utanför ett objekt komma åt dess fält eller beteenden eller bara objektet själv.
|Public| Är nyckelordet för att markera fält, beteenden eller klasser som **synligt för alla**.
|Private| Är nyckelordet för att markera fält, beteenden eller klasser som **inte synligt för någon annan**
|Protected| Är nyckelordet för att markera fält, beteenden eller klasser som **synligt bara för ärvande klasser**
|Arv|När man skriver en klass som hämtar all tidigare funktionalitet från en annan klass, för att man sedan kan utöka med mer eller specifiera dess beteende mer.
|Superklass / Basklass|Namnet man ger den klassen som en annan klass har ärvt ifrån.
|Polymorfism|När man har metoder från en superklass (basklass) som man skriver över med nytt beteende specifikt för den nya klassen. 