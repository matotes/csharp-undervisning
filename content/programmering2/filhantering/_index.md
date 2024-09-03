---
title: "Filhantering"
date: 2024-09-02T10:59:00Z
draft: false
weight: 100
---
Att hantera filer är ett en typ av IO-process som ofta är nödvändig för en utvecklare. I vissa fall så är det att man vill ha kvar sin data efter programmet stängs av, så att man kan återställa det man arbetat med. Exempel på sådana program är Google Docs, Visual Studio, Unity men även spel behöver också både skriva och läsa från filer. 

## I/O processer
Mycket man gör vid utveckling av mjukvara är att man tar antingen emot input (data in) eller så ger man en output (data ut). IO i sig självt behöver inte innebära att det är den lokala användaren som direkt ser resultatet, utan det kan också vara en sak som inte syns utåt.

Kommunikation mellan enheter (exempelvis två datorer i ett nätverk) kräver ocskå att man både skickar och tar emot data. Analoga detaljer är också en typ av IO-process. Att hantera muspekare och tangentbord är en IO-process, men att skriva ut på en skrivare är också en output.

I C# så har du förmodligen kommit i kontakt med konsolfönstret/terminalen. Detta är en metod för användarinput och även att ge output till användaren.

## Operativsystem (OS)
Operativsystem är ofta nycklen för de olika processerna som är tillgängliga och även möjliggör en att kommunicera med olika typer av IO-processer.