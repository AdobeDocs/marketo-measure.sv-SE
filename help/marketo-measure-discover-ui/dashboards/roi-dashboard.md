---
description: ROI Dashboard - [!DNL Marketo Measure] - Produkt
title: Kontrollpanel för avkastning
feature: Reporting
source-git-commit: dc4dd001d319f13ebd1c4ce418acf2faa27cfe81
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Kontrollpanel för avkastning {#roi-dashboard}

Avkastningsoptimeringen ger marknadsförarna en detaljerad bild av avkastningen på investeringar i olika kanaler, underkanaler och kampanjer. Den bryter noggrant ned kostnads- och intäktsmönster och lyfter också fram mätvärden som kostnad per lead, erbjudande och möjlighet, vilket ger en heltäckande bild av marknadsattribueringen.

Frågor till styrelsen:

* Vilka var avkastningen för varje kanal, delkanal och kampanj?
* Hur fördelades kostnader och intäkter mellan olika kanaler, underkanaler och kampanjer?
* Vad var kostnad per lead, kostnad per avtal och kostnad per tillfälle?

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
    <td>Kostnadsruta</td>
    <td>Totala kostnader</td>
    <td>Datum för kostnad</td>
    <td><li>Kampanj-ID</li>
<li>Kampanjnamn</li>
<li>Kanal</li>
<li>Delkanal</li>
<li>Datum</li>
<li>Utgift</li></td>
    <td rowspan="15"><li>Datum</li>
<li>Attribution Model (Setting)</li>
<li>Kanal</li>
<li>Delkanal</li>
<li>Campaign</li></td>
  </tr>
  <tr>
    <td>Attribuerad intäktsruta</td>
    <td>Total attributerad intäkt</td>
    <td>Stängt den</td>
    <td><li>ID för affärsmöjlighet</li>
<li>Affärsmöjlighetens namn</li>
<li>Skapad affärsmöjlighet</li>
<li>Stängningsdatum för affärsmöjlighet</li>
<li>Är stängd (J/N)</li>
<li>Är vunnen (J/N)</li>
<li>Attributionsmodell</li>
<li>Attribuerad intäkt</li>
<li>Realiserad intäkt</li></td>
  </tr>
  <tr>
    <td>Enkel ROI-platta</td>
    <td>Äldre avkastning: Inkomster fördelade på kostnader inom en given tidsram. 
    <li>Kostnad: Kostnad för filtrerad datumperiod.</li>
    <li>Intäkter: Inkomster från "Closed Won"-affärsmöjligheter inom den tidsramen.</li></td>
    <td>Stängt den</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>Realiserad avkastningsnivå</td>
    <td>Realiserad avkastning på investerat kapital: Representerar de konkreta resultaten av kontaktytor som genererats av kampanjer inom en viss tidsram.
    <li>Kostnad: Kostnad för filtrerad datumperiod.</li>
    <li>Intäkter: Realiserade intäkter från alla"Closed Won"-erbjudanden, särskilt sådana som påverkas av kontaktytor inom den angivna tidsramen.</li>
    <br/><img src="assets/roi-dashboard-1.png" width="600"></td>
    <td>Datum för kostnad</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>Ny lead-panel totalt</td>
    <td>Totalt antal nya leads (hela antal) som genererats under en angiven period, inklusive både rörliga och orörda leads.</td>
    <td>Skapad den</td>
    <td rowspan="2">
    <li>Lead-ID</li>
    <li>Lead-e-post</li>
    <li>LC-datum</li></td>
  </tr>
  <tr>
    <td>Kostnad per ny lead-panel</td>
    <td>Totalt antal nya leads (hela antal) delat med kostnader.</td>
    <td>Skapad den</td>
  </tr>
  <tr>
    <td>Total ny affärsmöjlighet - panel</td>
    <td>Totalt antal nya affärsmöjligheter (hela antal) som genererats under en angiven period, inklusive både rörliga och orörda säljtillfällen.</td>
    <td>Skapad den</td>
    <td rowspan="2">
    <li>ID för affärsmöjlighet</li>
    <li>Affärsmöjlighetens namn</li>
    <li>Skapad affärsmöjlighet</li>
    <li>Stängningsdatum för affärsmöjlighet</li>
    <li>Är stängd (J/N)</li>
    <li>Är vunnen (J/N)</li>
    <li>Aktuell fas</li></td>
  </tr>
  <tr>
    <td>Kostnad per ny affärsmöjlighet</td>
    <td>Totalt antal nya affärsmöjligheter (heltal) delat med kostnader.</td>
    <td>Skapad den</td>
  </tr>
  <tr>
    <td>Totalt avtalsfönster</td>
    <td>Totalt antal avtal som sluts inom en angiven period, inklusive sådana utan tillhörande kontaktytor.</td>
    <td>Stängt den</td>
    <td><li>ID för affärsmöjlighet</li>
<li>Affärsmöjlighetens namn</li>
<li>Skapad affärsmöjlighet</li>
<li>Stängningsdatum för affärsmöjlighet</li>
<li>Är stängd (J/N)</li>
<li>Är vunnen (J/N)</li>
<li>Aktuell fas</li>
<li>Valuta</li>
<li>Attributionsmodell</li>
<li>Attribuerad intäkt</li>
<li>Realiserad intäkt</li></td>
  </tr>
  <tr>
    <td>Kostnad och intäkter per kanal, diagram</td>
    <td>Stapeldiagram som illustrerar både kostnad och intäkt, utformat för att ge ett jämförande perspektiv på deras storlek i förhållande till olika kanaler, delkanaler och kampanjer.
    <br/><img src="assets/roi-dashboard-2.png" width="600"></td>
    <td>Stängt den</td>
    <td>Kostnad:
<br/>
<li>Kampanj-ID</li>
<li>Kampanjnamn</li>
<li>Kanal</li>
<li>Delkanal</li>
<li>Datum för kostnad</li>
<li>Valuta</li>
<li>Utgift</li>
<p>
Intäkter:
<br/>
<li>ID för affärsmöjlighet</li>
<li>Affärsmöjlighetens namn</li>
<li>Skapad affärsmöjlighet</li>
<li>Stängningsdatum för affärsmöjlighet</li>
<li>Är stängd (J/N)</li>
<li>Är vunnen (J/N)</li>
<li>Attribuerad intäkt</li>
<li>Attributionsmodell</li>
<li>Attribuerad intäkt</li>
<li>Realiserad intäkt</li></td>
  </tr>
  <tr>
    <td>Realiserad jämfört med enkel avkastning på investeringen över tid</td>
    <td>Diagram över tidsserielinje som visar jämförelsen mellan Realiserad och Enkel avkastning, med spårning av deras utveckling över tid.
    <br/><img src="assets/roi-dashboard-3.png" width="600"></td>
    <td>Enkel avkastning på investerat kapital: datum för kostnadskostnad och stängt den
    <p>Realiserad avkastning på investering: datum och slutpunkt för kostnad</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>Diagram över kostnad över tid</td>
    <td>Staplad liggande stapeldiagram med kvartalsvisa/månadsvisa totala kostnader, segmenterade efter enskilda kanaler för en detaljerad uppdelning.
    <br/><img src="assets/roi-dashboard-4.png" width="600"></td>
    <td>Datum för kostnad</td>
    <td rowspan="2"><li>Kampanj-ID</li>
<li>Kampanjnamn</li>
<li>Kanal</li>
<li>Delkanal</li>
<li>Datum för kostnad</li>
<li>Valuta</li>
<li>Utgift</li></td>
  </tr>
  <tr>
    <td>Diagram Kostnad per kanal</td>
    <td>Stapeldiagram som visar marknadsföringsutgifter segmenterade efter kanaler.
    <br/><img src="assets/roi-dashboard-5.png" width="600"></td>
    <td>Datum för kostnad</td>
  </tr>
  <tr>
    <td>Översiktstabell för ROI</td>
    <td>Tabell som visar tillskrivna intäkter, kostnader och avkastning uppdelat efter enskilda kanaler för en detaljerad uppdelning.
<p>
<b>Kolumner:</b>
<p>
<li>Kanal/delkanal/kampanj</li>
<li>Kostnad</li>
<li>Attribuerad intäkt</li>
<li>Enkel avkastning</li>
<li>Realiserad avkastning på investering</li>
<li>Orealiserad pipeline</li>
<ul style="padding-left: 30px;"><li>Pipeline från kontaktytor (öppna möjligheter) som är associerade med kampanjer under en viss tidsram</li></ul></td>
    <td>Enkel avkastning på investerat kapital: datum för kostnadskostnad och stängt den
    <p>Realiserad avkastning på investering: datum och slutpunkt för kostnad</td>
    <td>Ej tillämpligt</td>
  </tr>
  <tr>
    <td>Utgiftstabell för marknadsföring</td>
    <td>Tabell som visar kostnader, nya leads, affärsmöjligheter och avtal som stängts av enskilda kanaler för en detaljerad uppdelning.
<p>
<b>Kolumner:</b>
<p>
<li>Kanal/delkanal/kampanj</li>
<li>Kostnad</li>
<li>Nya leads</li>
<li>Kostnad per ny lead</li>
<li>Nya möjligheter</li>
<li>Kostnad per ny affärsmöjlighet</li>
<li>Avslutade erbjudanden</li>
<li>Kostnad per avtal stängt</li></td>
    <td><li>Kostnad: datum för kostnad</li>
<li>Nya leads: Skapat den</li>
<li>Nya affärsmöjligheter: Skapat den</li>
<li>Avslutade erbjudanden: Stängt datum</li></td>
    <td>Ej tillämpligt</td>
  </tr>
</tbody>
</table>
