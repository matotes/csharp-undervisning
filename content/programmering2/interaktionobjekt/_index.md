---
title: "Interaktion mellan Objekt"
date: 2024-08-27T23:26:15Z
draft: false
weight: 2
resources:
- name: styles
  src: common_styles.css
---

# Objekt som interagerar med varandra
Objekt har flera olika vis de kan på olika vis interagera med varandra. Deras interaktion bestäms av utvecklaren, och där beror det på vad man vill lyckas med. Vissa objekt bygger man genom att ha flera underliggande objekt i strukturen.

Ett exempel på detta är när man har en kurs med elever. Man har en del elever i en kurs, och kursen har sedan sitt innehåll. För att representera detta så har man ett par alternativ:
- Varje elev har en kurs som de läser
- En kurs har alla elever som läser den
- En mellanhand håller koll på vilken elev som läser vilken kurs

| Elev |vs| Kurs |
|------|-------|------|
|string Namn|------|string KursNamn|
|string Efternamn|------|string[] KursInnehåll|
|DateTime Födelsedag|------|Elev[] elever|
|Kurs[] Kurser|------|

I tabellen ovan så är där en liten jämförelse mellan upplägget av att ha en Elev som läser flera kurser, eller ifall man registrerar elever i kurser. Den mest logiska situationen ifall man har ett "toppen-ner" perspektiv är att låta Kursen innehålla alla deltagare, för då behöver man inte dubblera antalet kurser - och det är lättare att läggat till elever och hålla koll på alla deltagare. Annars lägger man ansvaret på eleven att hålla koll på alla sina kurser.

Båda dessa metoder är däremot valida, men exemplet som kommer att fortsätta användas nedan är den av att **en kurs har elever**.

## Exempel: Elever registrerade på kurs
Det man har från början i detta exempel är två distinkta objekt; Elev och Kurs. Det är ganska enkelt att se skillnaden mellan dem, eftersom det ena objektet beskriver en deltagare i studier och det andra objektet beskriver en utbildning inom ett ämne.

För enkelhetens skull så har eleverna inte betyg, utan bara namn, efternamn, klass och en födelsedag. I kursen så behöver man veta vad kursen heter, vilket ämne, instruktioner och sedan alla deltagare.

Klassbeskrivningen för en Elev blir så här:
```csharp
class Elev
{
    public string förnamn;
    public string efternamn;
    public string klass;
    public DateTime födelsedag;
}
```

Klassbeskrivningen för en Kurs blir så här:
```csharp
class Kurs
{
    public string namn;
    public string amne;
    public string[] instruktioner;
    public Elev[] elever;

    public void LäggTillElev(Elev elev) { ... }
    public void TaBortElev(Elev elev) { ... }

    public void SkrivUtRegistreradeElever() { ... }
}
```

Om man tittar på dessa olika objekten så blir det synligt för en att där finns en tydlig relation mellan elev och kurs. Här har vi att Kurser **har** elever. Precis så kan också elever **ha** kurser. Men det är inte rekommenderat att båda har det samtidigt, man väljer alltså lösning efter behovet på applikationen.

Nu finns där alltså ett objekt som kommunicerar eller arbetar med ett annat objekt. Man använder det precis som alla andra typer även här.

### Testköra att registrera elever på kurs

Exempelkod för att registera elever på en kurs kan se ut som följande:
```csharp
Kurs ma1 = new Kurs();
ma1.namn = "Matematik 1";
ma1.amne = "Matematik";
ma1.instruktioner = [ "Räkna 103-130", "Intervjua om levnadsvana (statistik)" ];

Elev e1 = new Elev();
e1.förnamn = "Klas";
e1.efternamn = "Göransson";
e1.klass = "EK2";
e1.födelsedag = new DateTime(2002, 04, 23);

Elev e2 = new Elev();
e2.förnamn = "Klara";
e2.efternamn = "Andersson";
e2.klass = "SA3";
e2.födelsedag = new DateTime(2001, 07, 10);

ma1.LäggTillElev(e1);
ma1.LäggTillElev(e2);

ma1.SkrivUtRegistreradeElever();
```

Detta ger ett program som kommer att skapa en kurs, och sedan registreras två elever på kursen. Sedan listas alla deltagare i kursen `ma1` ut på ett strukturerat vis.

# Sammanfattning
Ett objekt kan **referera** till ett annat objekt genom att ha en variabel av den typen. Ifall du har klass `A` och klass `B` så kan `A` känna till `B` genom att ha den som variabel.

```csharp
class A 
{
    public B B_Type_Variable;
}

class B 
{
    public string Some_Cool_Text;
}
```


Man kan se detta som att du har en cykel, och cykeln i sin tur har två däck. När man då trampar på cykelns pedaler så lägger den till en kraft på däcken. Objekten kan alltså "prata" med varandra.