---
unique-page-id: 18874704
description: Vanliga frågor om aktivitetsattribut - [!DNL Marketo Measure] - Produktdokumentation
title: Vanliga frågor om aktivitetsattribut
exl-id: 6272024f-b6ae-4aa7-ba92-c9f183549614
feature: Attribution
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '780'
ht-degree: 0%

---

# Vanliga frågor om aktivitetsattribut {#activities-attribution-faq}

The [!DNL Marketo Measure] Med aktivitetsfunktionerna kan vi importera alla dina aktivitetsposter och generera kontaktytor för dem, så att dessa aktiviteter kan få attribueringskrediter. Det vanligaste användningsexemplet är att spåra aktiviteter från säljteamet, eftersom de vanligtvis skapar ett register över telefonsamtal eller e-postmeddelanden som skickas till potentiella kunder. Andra unika saker som kan spåras är innehållsinteraktioner som hämtning av resurser eller videovyer.

**Hur skiljer sig detta från offlinekampanjer?**

Den största skillnaden är att kampanjer bara kan tillhandahålla en kontaktyta eftersom kampanjer bara tillåter en kampanjmedlem för varje lead eller kontakt. Det innebär att du inte kan spåra återkommande händelser som utgående samtal, demos eller webbinarier-deltagare, såvida du inte skapar enskilda kampanjer för varje gruppering. Med hjälp av aktiviteter kan du mäta varje händelse.

**Är det någon skillnad mellan aktivitet, händelser och aktiviteter?**

Activity-objektet fungerar som paraply, eller överordnat objekt, över objekten Task och Event. Verksamheten omfattar i huvudsak både uppgifter och evenemang. Uppgifter används vanligtvis för att spela in snabba engångsobjekt, t.ex. ett telefonsamtal eller ett e-postmeddelande. Händelser används vanligtvis för saker som kan ha ett start- eller slutdatum, som möten eller konferenser.

**Om jag har en lead eller kontakt med samma återkommande uppgift som ett e-postmeddelande eller ett samtal, kommer jag då att se Buyer Touchpoints för alla dessa?**

Ja. Det kommer att finnas en 1:1-relation mellan dina synkroniserade aktiviteter och skapade kontaktytor.

**Hur vet jag vilka poster som kommer att resultera i att kontaktpunkter skapas?**

Ett bra förslag är att du först konfigurerar filtren med hjälp av Activity-objektet i CRM. Baserat på filterreglerna, som ger dig en bra uppfattning om hur många poster som omfattas av det villkoret, kan du förfina det efter behov. Detta är inte nödvändigt, men ett praktiskt sätt för användare att förstå hur många aktivitetsslutpunkter som skapas när aktivitetsreglerna har konfigurerats.

**Vad är [!DNL Marketo Measure] Kampanjnamn?**

Eftersom dessa aktiviteter kommer att resultera i en kontaktpunkt, [!DNL Marketo Measure] behöver veta vilken kanal och underkanal de tillhör. För varje regel måste du ange [!DNL Marketo Measure] Kampanjnamn. När det är klart kan du använda CSV-filen för onlinekanaler för att mappa det [!DNL Marketo Measure] Kampanjnamn till rätt kanal. The [!DNL Marketo Measure] Kampanjnamnet visas också på själva kontaktytan i dialogrutan [!UICONTROL Ad Campaign Name] fält.

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

**Vad händer om jag behöver skapa en annan regel för varje säljare? Måste jag skapa en annan [!DNL Marketo Measure] Kampanjer för var och en?**

Nej, det gör du inte. Vi introducerade ett koncept för&quot;dynamiska kampanjnamn&quot;. På så sätt kan du fylla i en del (eller hela) av [!DNL Marketo Measure] Kampanjnamn med en&quot;ersättningsparameter&quot; som refererar till ett fält från Activity-objektet. Om du till exempel har en [!DNL Marketo Measure] Kampanjnamnet &quot;Utgående samtal&quot;, men du vill att säljaren ska vara i slutet, tar du CRM-fältnamnet och anropar [!DNL Marketo Measure] Kampanjnamn Utgående samtal {AssignedTo}&quot; eller &quot;Utgående samtal {CreatedBy}.&quot;

**Hur ställer jag in aktiviteter i [!DNL Marketo Measure] app?**

Anvisningar om hur du konfigurerar aktiviteter i [!UICONTROL Marketo] Mätappen finns i [!DNL Marketo Measure] Supportartikel för aktiviteter.

**Vad betyder de olika operatorerna?**

* är lika med: exakt matchning av värdet (alias: social)
* contains: the text is in middle (alias: &#42;social&#42;)
* börjar med: värdet börjar med texten (kallas: social&#42;)
* slutar med: värdet slutar med texten (dvs: &#42;socialt)
* matchar alla: flera värden kan läggas till som är kommaavgränsade. If [!UICONTROL starts with], [!UICONTROL ends with], eller innehåller operatorer som måste användas, används jokertecknet (&#42;)
* större än: används för numeriska fält eller datum/tid-fält
* mindre än: används för numeriska fält eller datum/tid-fält

**Vilken kanal kommer dessa aktiviteter att gå under?**

När aktivitetsregeln och dess motsvarande [!DNL Marketo Measure] Kampanjnamn, som skapas, använder ni definitionerna för onlinekanaler för att placera dessa kampanjer under rätt marknadsföringskanal. [!DNL Marketo Measure] har möjlighet att definiera kanaler med hjälp av inte bara medium och källa, utan även kampanj.

Om du i exemplet ovan vill tilldela BDR-kanalen kampanjen &quot;Utgående samtal {tilldelad till}&quot;, vill du infoga en rad i CSV-filen för onlinekanaler för BDR-kanalen med kampanjdefinitionen &quot;Utgående samtal&#42;&quot; - asterisken anger ett jokervärde, så alla kampanjer som börjar med &quot;Utgående samtal&quot; hamnar under BDR-kanalen i stället för att behöva skapa en separat rad för varje kampanjnamn.
