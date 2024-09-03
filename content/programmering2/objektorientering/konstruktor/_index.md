---
title: "Konstruktorer"
date: 2024-09-01T20:00:00Z
draft: false
weight: 1
---

## Vad är en konstruktor?
Vid flera tillfällen har man objekt som man egentligen har all information redan när man skapar det. Det kan vara så att man vill mest bara ha en plats att förvara informationen och göra den lättillgänglig för senare användning. Oavsett anledning så kommer konstruktorn att vara hjälpsam att enkelt konstruera nya objekt.

Ett exempel är att i Unity3D så kan man skapa en `Vector2` eller `Vector3`, vilket är en typ av punkt eller koordinat i ett spel. När man skapar en vektor oavsett dimensioner så behöver man skriva in var den befinner sig, och för att göra den mer tillgänglig kan man skicka in koordinaterna **när** man skapar den.
```csharp
Vector3 targetPosition = new Vector3(10, 0, 5);
```
Denna kod tillverkar en `Vector3` på koordinaterna `x=10` `y=0` `z=5`. Liknar sättet man tidigare skapat objekt på, men nu finns där även parametrar för att skapa själva objektet. Detta är resultatet av en konstruktor; Den **konstruerar** objektet och ger variabler värden.

## Hur man skriver en konstruktor
Man skriver en konstruktor nästan som en vanlig metod, men istället för att ha en "resultattyp" så kommer denna metod endast ha ett namn, och sedan parametrar. Namnet man ger konstruktorn **måste** vara samma som man har gett sin klass (objektbeskrivningen).

```csharp
class Person
{
    private string name;
    private string familyName;
    private DateTime dateOfBirth;

    public Person(string aName, string aFamilyName, DateTime aDateOfBirth)
    {
        name = aName;
        familyName = aFamilyName;
        dateOfBirth = aDateOfBirth;
    }
}
```
I kodstycket ovan är en klass beskriven, `Person`. I den så finns där tre fält (attribut). Unden fälten så finns där en metod som är markerad `public` och den har samma namn som person-klassen har. Det enda som skiljer den åt är att där finns också tre parameterar inkluderat, det konstruktorn sedan gör att bara assignera värdet på objektets fält, sedan är den slut. För att skapa en **instans** av en person måste man alltså ge alla parametrar.
```csharp
DateTime dob = new DateTime(1990, 1, 1);

Person testPerson = new Person("Kalle", "Kaviarsson", dob);
```
I denna kod så är det då ett nytt objekt skapas, och den kommer att vara av **typen** `Person`. Fälten i denna person kommer då att vara satta till värdena vi gett till **konstruktorn**: `name = Kalle`, `familyName = "Kaviarsson` och `dateOfBirth = 01011990` *(observera detta är bara ett datum, och inte en korrekt representation av vad DateTime faktiskt är)*.

## Sammanfattning
En konstruktor är en metod som **bygger** ett objekt av egen typ. Man kan lägga till antalet parametrar man behöver, eller inte ha någon alls. Detta hjälper en att bygga sin kod och sätta alla värden **enklare**, och behöver inte vara nödvändigt för att få fungerande kod, men däremot för bättre samarbete mellan programmerare så kan det vara bra att använda konstruktorn på ett sådant vis som tvingar en att alltid ge objektet vad det behöver för att existera.