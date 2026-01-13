---
description: ROI Dashboard - [!DNL Marketo Measure] - Produkt
title: Kontrollpanel för avkastning
feature: Reporting
exl-id: 878db6e0-3ac7-4f4c-b993-bd7a1cfa0638
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---


# Kontrollpanel för avkastning {#roi-dashboard}

Avkastningsoptimeringen ger marknadsförarna en detaljerad bild av avkastningen på investeringar i olika kanaler, underkanaler och kampanjer. Den bryter noggrant ned kostnads- och intäktsmönster och lyfter också fram mätvärden som kostnad per lead, erbjudande och möjlighet, vilket ger en heltäckande bild av marknadsattribueringen.

**Frågor till styrelsen**

* Vilka var avkastningen för varje kanal, delkanal och kampanj?
* Hur fördelades kostnader och intäkter mellan olika kanaler, underkanaler och kampanjer?
* Vad var kostnad per lead, kostnad per avtal och kostnad per tillfälle?

## Kontrollpanelskomponenter {#dashboard-components}

### KPI-paneler {#kpi-tiles}

* **Kostnad**: Totala kostnader från anslutna datakällor och manuellt överförda kostnader.
* **Attributerad intäkt**: Det totala intäktsbidraget, baserat på den valda attribueringsmodellen, från affärsmöjligheter med kontaktytor som stängts inom den filtrerade datumperioden.
* **Realiserad attributerad intäkt**: Det totala intäktsbidraget, baserat på den valda attribueringsmodellen, från affärsmöjligheter med kontaktytor inom den filtrerade datumperioden, oavsett när de stängdes.
* **Totalt antal nya leads**: Totalt antal nya leads som genererats, inklusive både rörliga och orörda leads.
* **Kostnad per ny lead**: Den genomsnittliga kostnaden per ny lead, som härleds från den totala kostnaden dividerat med det totala antalet nya leads.
* **Totalt antal nya affärsmöjligheter**: Totalt antal nya affärsmöjligheter som genererats, inklusive både rörliga och orörda affärsmöjligheter.
* **Kostnad per nytt affärstillfälle**: Den genomsnittliga kostnaden per nytt affärstillfälle, som härleds från den totala kostnaden dividerat med det totala antalet nya affärsmöjligheter.
* **Totalt antal avtal**: Antal stängda vinstmöjligheter, inklusive affärsmöjligheter utan kontaktytor.
* **Enkel avkastning på investering**: Attribuerad intäkt dividerat med kostnader i den filtrerade datumperioden.
* **Realiserad avkastning på investerat kapital**: Realiserad tilldelad intäkt dividerad med kostnader i den filtrerade datumperioden.

![KPI-paneler för ROI-instrumentpanel för kostnad, tilldelad intäkt och ROI](assets/roi-dashboard-1.png)

### Kostnad och intäkter per kanal, diagram {#cost-and-revenue-by-channel-graph}

Stapeldiagram visar kostnader och intäkter, som är utformade för att ge ett komparativt perspektiv på deras storlek i förhållande till olika kanaler, delkanaler och kampanjer.

* använda detaljfunktionerna för att kategorisera data efter Subchannel och Campaign.
* Håll pekaren över varje fält för att visa enkel och realiserad avkastning på investerat kapital.

**Frågar diagramsvaren**

* Vilka var avkastningen för varje kanal, delkanal och kampanj?
* Finns det några utgående kanaler eller delkanaler med ovanligt höga eller låga kostnader i förhållande till deras intäkter?

![Kostnader och intäkter per staplat stapeldiagram i kanal](assets/roi-dashboard-2.png)

### Realiserad jämfört med enkel avkastning på investerat kapital över tid {#realized-vs-simple-roi-over-time}

Diagram över tidsserielinje som visar jämförelsen mellan Realiserad och Enkel avkastning, med spårning av deras utveckling över tid.

* Håll pekaren över ett avsnitt i diagrammet för att visa enkel och realiserad avkastning på investerat kapital.

**Frågar diagramsvaren**

* Hur är den realiserade avkastningen jämfört med den enkla avkastningen under specifika tidsperioder?
* Hur hänger trenden för realiserad avkastning på investerat kapital samman med några betydande marknadsföringshändelser under samma period?

![Realiserad kontra enkel avkastningstrendlinje &#x200B;](assets/roi-dashboard-3.png)

### Diagram över kostnad över tid {#cost-over-time-graph}

Staplat stapeldiagram med totala kostnader, segmenterade efter associerade kanaler för varje månad/kvartal/år.

* använda detaljfunktionerna för att kategorisera data efter månad, kvartal eller år.
* Håll pekaren över ett stolpsegment eller mellanrummet mellan stolparna för att visa detaljerad information.

**Frågar diagramsvaren**

* Hur står den sammanlagda kostnaden för alla kanaler jämfört med en fjärdedel/månad till nästa?
* Hur har kostnaderna för en viss kanal utvecklats över tid?

![Kostnad över tidsstaplade stapeldiagram med detaljkontroller](assets/roi-dashboard-4.png)

### Diagram Kostnad per kanal {#cost-by-channel-graph}

Stapeldiagram som visar marknadsföringsutgifter segmenterade efter kanal/underkanal/kampanj.

* använda detaljfunktionerna för att kategorisera data efter kanal/delkanal/kampanj.

**Frågar diagramsvaren**

* Vilka underkanaler eller kampanjer i en primär kanal har den högsta tilldelningen?
* Vilka marknadsföringsmöjligheter (kanal, delkanal eller kampanj) verkar underfinansierade jämfört med andra?

![Marknadsföringsutgifter per kanalstapeldiagram](assets/roi-dashboard-5.png)

### Översiktstabell för ROI {#roi-summary-table}

Tabell som visar tillskrivna intäkter, kostnader och avkastning uppdelat efter enskilda kanaler för en detaljerad uppdelning.

* Klicka på plusikonen bredvid varje kanal för att visa uppdelningen efter subkanal och kampanj.

**Kolumner**

* Kanal/delkanal/kampanj
* Kostnad
* Attribuerad intäkt
* Realiserad attributerad intäkt
* Enkel avkastning
* Realiserad avkastning på investering
* Orealiserad attribuerad försäljningsintäkt för pipeline: Inkomster kopplade till kontaktytor (öppna möjligheter) som skapats inom den filtrerade datumperioden.

### Utgiftstabell för marknadsföring {#marketing-spend-table}

Tabell som visar kostnader, nya leads, säljprojekt och erbjudanden stängda efter enskilda kanaler för en detaljerad uppdelning.

* Klicka på plusikonen bredvid varje kanal för att visa uppdelningen efter subkanal och kampanj.

**Kolumner**

* Kanal/delkanal/kampanj
* Kostnad
* Nya leads
* Kostnad per ny lead
* Nya möjligheter
* Kostnad per ny affärsmöjlighet
* Erbjudanden
* Kostnad per avtal

## Filterruta {#filter-pane}

Kontrollpanelen är utrustad med följande inställningar och filter:

* Datum
   * Baserat på:
      * Skapad: Nyhetsleads, nya affärsmöjligheter
      * Falldatum för kostnad: kostnad
      * Stängt datum: avskrivna intäkter (enkel avkastning på investering), erbjudanden
      * Slutpunktsdatum: kontaktytor från intjänad intäkt (realiserad avkastning på investering)
* Attributionsmodell
* Kanal, delkanal
* Campaign

>[!MORELIKETHIS]
> [Grunderna för instrumentpanel](/help/marketo-measure-discover-ui/discover-dashboard-basics.md){target="_blank"}
> [Synlighetsprincip för instrumentpanelsdata &#x200B;](/help/marketo-measure-discover-ui/dashboard-data-visibility-policy.md){target="_blank"}

