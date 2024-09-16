---
unique-page-id: 18874704
description: Vanliga frågor om aktivitetsattribuering - [!DNL Marketo Measure]
title: Vanliga frågor om aktivitetsattribut
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: e5931d783d8aad9ab0b32b4e30bbbfdfd46230dd
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Vanliga frågor om aktivitetsattribut {#activities-attribution-faq}

[!DNL Marketo Measure] aktiviteter importerar alla dina aktivitetsposter och genererar kontaktytor för dem, vilket gör att dessa aktiviteter kan få attribueringskrediter. Det vanligaste användningsexemplet är att spåra aktiviteter från säljteamet, eftersom de ofta skapar ett register över telefonsamtal eller e-postmeddelanden som skickas till potentiella kunder. Andra unika saker som kan spåras är innehållsinteraktioner som hämtning av resurser eller videovyer.

>[!AVAILABILITY]
>
>Den här funktionen är endast aktiverad för Tier 2-kunder. Om du vill begära en högre kontonivå kontaktar du kontoteamet (din kontohanterare) på Adobe.

**Hur skiljer sig detta från offlinekampanjer?**

Den största skillnaden är att kampanjer bara kan tillhandahålla en kontaktyta eftersom kampanjer bara tillåter en kampanjmedlem för varje lead eller kontakt. Det innebär att du inte kan spåra återkommande händelser som utgående samtal, demos eller webbinarier-deltagare, såvida du inte skapar enskilda kampanjer för varje gruppering. Med hjälp av aktiviteter kan du mäta alla händelser.

**Är det någon skillnad mellan aktivitet, händelser och aktiviteter?**

Activity-objektet fungerar som paraply, eller överordnat objekt, över objekten Task och Event. Verksamheten omfattar i huvudsak både uppgifter och evenemang. Uppgifter används vanligtvis för att spela in snabba engångsobjekt, t.ex. ett telefonsamtal eller ett e-postmeddelande. Händelser används vanligtvis för saker som kan ha ett start- eller slutdatum, som möten eller konferenser.

**Om jag har en lead eller kontakt med samma återkommande aktivitet, kommer jag då att se Buyer Touchpoints för alla dessa?**

Ja. Det finns en 1:1-relation mellan dina synkroniserade aktiviteter och skapade kontaktytor.

**Hur vet jag vilka poster som resulterar i att kontaktpunkter skapas?**

Ett bra förslag är att du först konfigurerar filtren med hjälp av Activity-objektet i CRM. Baserat på filterreglerna ger detta dig en bra uppfattning om hur många poster som faller under det villkoret, och du kan sedan förfina det efter behov. Detta är inte nödvändigt, men ett praktiskt sätt för användare att förstå hur många aktivitetsslutpunkter som skapas när aktivitetsreglerna har konfigurerats.

**Vad är [!DNL Marketo Measure] kampanjnamnet?**

Eftersom dessa aktiviteter resulterar i en kontaktyta måste [!DNL Marketo Measure] veta vilken kanal och underkanal de tillhör. Du måste ange ett kampanjnamn för [!DNL Marketo Measure] för varje regel. När det är skapat kan du använda CSV-filen för onlinekanaler för att mappa det [!DNL Marketo Measure] kampanjnamnet till rätt kanal. Kampanjnamnet [!DNL Marketo Measure] visas också i själva pekpunkten i fältet [!UICONTROL Ad Campaign Name].

**Vilka andra Touchpoint-fält är ifyllda?**

| **Touchpoint-fält** | **Värde** |
|---|---|
| Lead/kontakt | Alla aktiviteter är relaterade till en lead eller kontakt |
| Campaign | Channel.Subchannel [[!DNL Marketo Measure]] |
| Touchpoint Source | CRM-aktivitet |
| Medium | Activity.Type |
| Kontaktpunktstyp | Activity.Type |
| Namn på annonskampanj | Kampanjnamn för [!DNL Marketo Measure] |
| Annonsinnehåll | Aktivitetsämne |
| Annons-ID | Externt ID för aktivitet |
| Kontaktpunktsdatum | [anpassad - anges i appar] |

**Vad händer om jag behöver skapa en annan regel för varje säljare? Behöver jag skapa olika [!DNL Marketo Measure]-kampanjer för varje?**

Nej, det gör du inte. Med&quot;dynamiska kampanjnamn&quot; kan du fylla i delar (eller alla) av [!DNL Marketo Measure]-kampanjnamnet med en&quot;ersättningsparameter&quot; som refererar till ett fält från aktivitetsobjektet. Om du till exempel har ett [!DNL Marketo Measure]-kampanjnamn med namnet &quot;Utgående samtal&quot; men vill att säljaren ska vara i slutet, tar du CRM-fältnamnet och anropar [!DNL Marketo Measure] kampanjnamnet &quot;Utgående samtal {AssignedTo}&quot; eller &quot;Utgående samtal {CreatedBy}&quot;.

**Hur konfigurerar jag aktiviteter i [!DNL Marketo Measure]-appen?**

Riktlinjer om hur du konfigurerar aktiviteter i [!UICONTROL Marketo]-mätappen finns i artikeln [!DNL Marketo Measure] - aktivitetsstöd.

**Vad betyder de olika operatorerna?**

* är lika med: exakt matchning av värdet (alias: social)
* innehåller: texten finns i mitten (kallas: &#42;social&#42;)
* börjar med: värdet börjar med texten (kallas: social&#42;)
* slutar med: värdet slutar med texten (dvs: &#42;social)
* matchar alla: flera värden kan läggas till som är kommaavgränsade. Om operatorerna [!UICONTROL starts with], [!UICONTROL ends with] eller innehåller måste användas använder du jokertecknet (&#42;)
* större än: används för numeriska fält eller datum/tid-fält
* mindre än: används för numeriska fält eller datum/tid-fält

**Vilken kanal hamnar de här aktiviteterna under?**

När aktivitetsregeln och dess motsvarande [!DNL Marketo Measure]-kampanjnamn skapas använder du definitionerna för onlinekanaler för att placera dessa kampanjer under rätt marknadsföringskanal. [!DNL Marketo Measure] kan definiera kanaler med hjälp av inte bara medium och källa, utan även kampanj.

Om du i exemplet ovan vill tilldela BDR-kanalen kampanjen &quot;Utgående samtal {tilldelad till}&quot; infogar du en rad i CSV-filen för BDR-kanalen i onlinekanalerna med kampanjdefinitionen &quot;Utgående samtal&#42;&quot;. Asterisken anger ett jokervärde, vilket innebär att alla kampanjer som börjar med &quot;Utgående samtal&quot; hamnar under BDR-kanalen, i stället för att skapa en separat rad för varje kampanjnamn .
