---
description: Passport Dashboard - [!DNL Marketo Measure] - Produkt
title: Passport Dashboard
feature: Reporting
exl-id: 0fbd9714-7d9c-4330-b35f-d011e17c3bfe
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Passport Dashboard {#passport-dashboard}

På Passport-kontrollpanelen får marknadsförarna en dynamisk vy över leads, kontakter och affärsmöjligheter när de går igenom olika faser under en viss period. Genom att filtrera efter ett visst datum kan användare även få en ögonblicksbild av poster för den dagen.

**Frågor till styrelsen:**

* Hur många leads, kontakter eller möjligheter fanns i varje icke-terminal fas på en vald dag?
* Hur många distinkta leads eller kontakter har utvecklats under en viss period?
   * _Exempel_: Om Lead A befann sig i fas 1 den 1 januari 2023 och flyttades till steg 5 senast den 3 mars 2023, skulle Passport-analysen Q1 2023 räkna Lead A i steg 1 till 5.
* Hur många unika möjligheter har passerat genom varje övergångsfas under en given tidsram?

## Kontrollpanelskomponenter {#dashboard-components}

### Möjligheter i Stage efter scennamn {#opportunities-in-stage-by-stage-name}

* I varje fas visas antalet möjligheter med kontaktytor som passerat genom dem under en viss tidsperiod.
   * Om en affärsmöjlighet går igenom flera steg inom det intervallet räknas den i varje fas den går.
* Terminalfaser som &quot;Closed Won&quot; och &quot;Closed Lost&quot; ingår inte.
* Både start- och slutdatum är inkluderande.

![](assets/passport-dashboard-1.png)

### Leads eller kontakter i scenen efter scennamn {#leads-or-contacts-in-stage-by-stage-name}

* I varje fas visas antalet leads eller kontakter med kontaktpunkter som passerat genom dem under en given tidsram.
   * Om Lead eller Kontakt ska visas beror på inställningarna under Inställningar > Attributinställningar > Standardinstrumentpanelsobjekt.
   * Om en lead eller kontakt går igenom flera steg inom det intervallet räknas den i varje fas den går.
* Terminalfaser som &quot;Closed Won&quot; och &quot;Closed Lost&quot; ingår inte.
* Både start- och slutdatum är inkluderande.

![](assets/passport-dashboard-2.png)

## Filterruta {#filter-pane}

Kontrollpanelen är utrustad med följande inställningar och filter:

* Datum (baserat på övergångsdatum)
* Kanal, delkanal
* Campaign
* Segment

>[!MORELIKETHIS]
>
>* [Grunderna för instrumentpanel](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
>* [Synlighetsprincip för instrumentpanelsdata](/help/marketo-measure-discover-ui/dashboards/dashboard-data-visibility-policy.md){target="_blank"}
