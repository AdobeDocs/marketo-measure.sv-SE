---
description: Passport Dashboard - [!DNL Marketo Measure] - Produkt
title: Passport Dashboard
feature: Reporting
source-git-commit: 436e30c2a4138d780232d6ba9e64456d6277ac9b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Passport Dashboard {#passport-dashboard}

På Passport-kontrollpanelen får marknadsförarna en dynamisk vy över leads, kontakter och affärsmöjligheter när de går igenom olika faser under en viss period. Genom att filtrera efter ett visst datum kan användare även få en ögonblicksbild av poster för den dagen.

Frågor till styrelsen:

* Hur många leads, kontakter eller möjligheter fanns i varje icke-terminal fas på en vald dag?
* Hur många distinkta leads eller kontakter har utvecklats under en viss period?
   * _Exempel_: Om lead A befann sig i fas 1 den 1 januari 2023 och flyttades till steg 5 senast den 3 mars 2023, skulle Passport-analysen för första kvartalet 2023 räkna lead A i steg 1 till 5.
* Hur många unika möjligheter har passerat genom varje övergångsfas under en given tidsram?

<table style="table-layout:auto"> 
<tbody>
<tr> 
   <th>Komponent</th> 
   <th>Beskrivning</th>
   <th>Datumtyp</th>
   <th>Granska fält</th>
   <th>Filter</th>
  </tr>
  <tr>
    <td>Möjligheter</td>
    <td><li>I varje fas visas antalet möjligheter med bästa tillgängliga teknik som har passerat genom dem inom en viss tidsram.</li>
<ul style="padding-left: 30px;"><li>Om ett säljprojekt går igenom flera faser inom det intervallet räknas de i varje fas som det går.</li></ul>
<li>Terminalfaser som "Closed Won" och "Closed Lost" ingår inte.</li>
<li>Både start- och slutdatum är inkluderande.</li>
<br/><img src="assets/passport-dashboard-1.png" width="600"></td>
    <td rowspan="2">Övergångsdatum</td>
    <td></td>
    <td rowspan="2"><li>Datum</li>
<li>Kanal</li>
<li>Delkanal</li>
<li>Campaign</li>
<li>Segment</li></td>
  </tr>
  <tr>
    <td>Leads/kontakter</td>
    <td><li>I varje fas visas antalet leads eller kontakter med BT:er som har passerat genom dem under en viss tidsram.</li>
<ul style="padding-left: 30px;"><li>Om Lead eller Kontakt ska visas beror på inställningarna under Inställningar &gt; Attributinställningar &gt; Standardinstrumentpanelsobjekt.</li></ul>
<li>Terminalfaser som "Closed Won" och "Closed Lost" ingår inte.</li>
<li>Både start- och slutdatum är inkluderande.</li>
<br/><img src="assets/passport-dashboard-2.png" width="600"></td>
    <td><li>Lead/kontakt-ID</li>
<li>Lead/kontakt-e-postadress</li>
<li>Skapad den</li>
<li>Aktuell fas</li>
<li>Övergång i datum</li>
<li>Övergång inaktuell</li></td>
  </tr>
</tbody>
</table>

>[!MORELIKETHIS]
>
>[Grunderna i kontrollpanelen](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
