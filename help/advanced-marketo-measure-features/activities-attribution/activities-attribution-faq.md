---
unique-page-id: 18874704
description: Vanliga frågor om aktivitetsattribut - [!DNL Marketo Measure]
title: Vanliga frågor om aktivitetsattribut
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# Vanliga frågor om aktivitetsattribut {#activities-attribution-faq}

[!DNL Marketo Measure] Aktiviteter importerar alla dina aktivitetsposter och genererar kontaktytor för dem, vilket gör att dessa aktiviteter kan få attribueringskrediter. Det vanligaste användningsexemplet är att spåra aktiviteter från säljteamet, eftersom de ofta skapar ett register över telefonsamtal eller e-postmeddelanden som skickas till potentiella kunder. Andra unika saker som kan spåras är innehållsinteraktioner som hämtning av resurser eller videovyer.

**Hur skiljer sig detta från offlinekampanjer?**

Den största skillnaden är att kampanjer bara kan tillhandahålla en kontaktyta eftersom kampanjer bara tillåter en kampanjmedlem för varje lead eller kontakt. Det innebär att du inte kan spåra återkommande händelser som utgående samtal, demos eller webbinarier-deltagare, såvida du inte skapar enskilda kampanjer för varje gruppering. Med hjälp av aktiviteter kan du mäta alla händelser.

**Är det någon skillnad mellan aktivitet, händelser och aktiviteter?**

Activity-objektet fungerar som paraply, eller överordnat objekt, över objekten Task och Event. Verksamheten omfattar i huvudsak både uppgifter och evenemang. Uppgifter används vanligtvis för att spela in snabba engångsobjekt, t.ex. ett telefonsamtal eller ett e-postmeddelande. Händelser används vanligtvis för saker som kan ha ett start- eller slutdatum, som möten eller konferenser.

**Om jag har en lead eller kontakt med samma återkommande uppgift, kommer jag då att se Buyer Touchpoints för alla dessa?**

Ja. Det finns en 1:1-relation mellan dina synkroniserade aktiviteter och skapade kontaktytor.

**Hur vet jag vilka poster som resulterar i att kontaktpunkter skapas?**

Ett bra förslag är att du först konfigurerar filtren med hjälp av Activity-objektet i CRM. Baserat på filterreglerna ger detta dig en bra uppfattning om hur många poster som faller under det villkoret, och du kan sedan förfina det efter behov. Detta är inte nödvändigt, men ett praktiskt sätt för användare att förstå hur många aktivitetsslutpunkter som skapas när aktivitetsreglerna har konfigurerats.

**Vad är [!DNL Marketo Measure] Kampanjnamn?**

Eftersom dessa aktiviteter resulterar i en kontaktyta, [!DNL Marketo Measure] måste veta vilken kanal och underkanal de tillhör. Du måste ange en [!DNL Marketo Measure] Kampanjnamn. När det är klart kan du använda CSV-filen för onlinekanaler för att mappa det [!DNL Marketo Measure] Kampanjnamn till rätt kanal. The [!DNL Marketo Measure] Kampanjnamnet visas också på själva kontaktytan i dialogrutan [!UICONTROL Ad Campaign Name] fält.

**Vilka andra Touchpoint-fält fylls i?**

| **Touchpoint-fält** | **Värde** |
|---|---|
| Lead/kontakt | Alla aktiviteter är relaterade till en lead eller kontakt |
| Campaign | Channel.Subchannel [[!DNL Marketo Measure]] |
| Kontaktpunktskälla | CRM-aktivitet |
| Medel | Activity.Type |
| Kontaktpunktstyp | Activity.Type |
| Namn på annonskampanj | [!DNL Marketo Measure] Kampanjnamn |
| Annonsinnehåll | Aktivitetsämne |
| Annons-ID | Externt ID för aktivitet |
| Kontaktpunktsdatum | [anpassad - ange i appar] |

**Vad händer om jag behöver skapa en annan regel för varje säljare? Måste jag skapa en annan [!DNL Marketo Measure] Campaign for each?**

Nej, det gör du inte. Med&quot;dynamiska kampanjnamn&quot; kan ni fylla i delar (eller alla) av [!DNL Marketo Measure] Kampanjnamn med en&quot;ersättningsparameter&quot; som refererar till ett fält från Activity-objektet. Om du till exempel har en [!DNL Marketo Measure] Kampanjnamnet &quot;Utgående samtal&quot;, men du vill att säljaren ska vara i slutet, tar CRM-fältnamnet och anropar [!DNL Marketo Measure] Kampanjnamn Utgående samtal {AssignedTo}&quot; eller &quot;Utgående samtal {CreatedBy}.&quot;

**Hur ställer jag in aktiviteter i [!DNL Marketo Measure] app?**

Anvisningar om hur du konfigurerar aktiviteter i [!UICONTROL Marketo] Mätappen finns i [!DNL Marketo Measure] Supportartikel för aktiviteter.

**Vad betyder de olika operatorerna?**

* är lika med: exakt matchning av värdet (alias: social)
* contains: the text is in middle (alias: &#42;social&#42;)
* börjar med: värdet börjar med texten (kallas: social&#42;)
* slutar med: värdet slutar med texten (dvs: &#42;socialt)
* matchar alla: flera värden kan läggas till som är kommaavgränsade. If [!UICONTROL starts with], [!UICONTROL ends with], eller operatorerna innehåller måste användas, använder du jokertecknet (&#42;)
* större än: används för numeriska fält eller datum/tid-fält
* mindre än: används för numeriska fält eller datum/tid-fält

**Vilken kanal går dessa aktiviteter under?**

När aktivitetsregeln och dess motsvarande [!DNL Marketo Measure] Kampanjnamn skapas. Använd definitionerna för onlinekanaler för att placera dessa kampanjer under rätt marknadsföringskanal. [!DNL Marketo Measure] kan definiera kanaler med hjälp av inte bara medium och källa, utan även kampanj.

Om du i exemplet ovan vill tilldela BDR-kanalen kampanjen&quot;Utgående samtal {tilldelad till}&quot; infogar du en rad i CSV-filen för onlinekanaler för BDR-kanalen med kampanjdefinitionen&quot;Utgående samtal&#42;&quot; - asterisken anger ett jokervärde, så alla kampanjer som börjar med &quot;Utgående samtal&quot; hamnar under BDR-kanalen i stället för att behöva skapa en separat rad för varje kampanjnamn.
