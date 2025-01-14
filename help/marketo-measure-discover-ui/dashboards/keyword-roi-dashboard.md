---
description: Kontrollpanel för nyckelords-ROI - [!DNL Marketo Measure]  - Produkt
title: Kontrollpanel för nyckelordens ROI
feature: Reporting
exl-id: 9c85a3ad-1806-4e30-b0fb-686760aea587
source-git-commit: f1adf53a9bf3adbc77d52c12dbafb09a28e51178
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Kontrollpanel för nyckelordens ROI {#keyword-roi-dashboard}

Instrumentpanelen för nyckelordsavkastning ger detaljerade insikter om resultatet för betalningskampanjer. Den ger en omfattande analys av kostnader på nyckelordsnivå, tillskrivna intäkter och nya leads och möjligheter som genereras, vilket ger en tydlig förståelse för nyckelordens avkastning.

Frågor som kontrollpanelen besvarar:

* Vilken är avkastningen för varje nyckelord i Google Adwords, Linkedin och Bing Ads?
* Hur delas kostnader och inkomster upp efter nyckelord?
* Hur många leads och möjligheter skapades från varje nyckelord?

## Kontrollpanelskomponenter {#dashboard-components}

### Sammanfattningstabell för nyckelordens ROI {#keyword-roi-summary-table}

Tabell som visar tillskrivna intäkter, kostnader och avkastning segmenterat efter enskilda nyckelord för en detaljerad uppdelning.

Granska de specifika nyckelorden för att se vilka möjligheter som påverkas av varje nyckelord.

**Kolumner:**

* **Nyckelord**
* **Campaign**
* **Lägg till konto-ID**
* **Lägg till kontonamn**
* **Lägg till grupp-ID**
* **Lägg till gruppnamn**
* **Kostnad**: Totala kostnader från anslutna datakällor.
* **Attribuerad intäkt**: Det totala intäktsbidraget, baserat på den valda attribueringsmodellen, från affärsmöjligheter med kontaktytor som stängts inom den filtrerade datumperioden
* **Realiserad attributerad intäkt**: Det totala intäktsbidraget, baserat på den valda attribueringsmodellen, från affärsmöjligheter med kontaktytor inom den filtrerade datumperioden, oavsett när de stängdes.
* **Orealiserad attributerad försäljningsintäkt för pipeline**: Intäkter för pipeline som är kopplade till kontaktytor (öppna affärsmöjligheter) som skapats inom den filtrerade datumperioden.
* **Enkel avkastning på investering**: Attribuerad intäkt dividerat med kostnader i den filtrerade datumperioden.
* **Realiserad avkastning på investerat kapital**: Realiserad tilldelad intäkt dividerad med kostnader i den filtrerade datumperioden.

### Leads och säljprojekt per nyckelordstabell {#leads-and-opportunities-by-keyword-table}

Tabell som visar nya leads, affärsmöjligheter och tillhörande kostnader segmenterade efter enskilda nyckelord för en detaljerad uppdelning.

Granska de specifika nyckelorden för att se vilka möjligheter som påverkas av varje nyckelord.

**Kolumner:**

* **Nyckelord**
* **Campaign**
* **Lägg till konto-ID**
* **Lägg till kontonamn**
* **Lägg till grupp-ID**
* **Lägg till gruppnamn**
* **Kostnad**
* **Nya leads**: Totalt antal nya leads som genererats, inklusive både rörliga och orörda leads.
* **Kostnad per ny lead**: Den genomsnittliga kostnaden per ny lead, som härleds från den totala kostnaden dividerat med det totala antalet nya leads.
* **Nya affärsmöjligheter**: Totalt antal nya affärsmöjligheter som genererats, inklusive både rörliga och orörda affärsmöjligheter.
* **Kostnad per nytt affärstillfälle**: Den genomsnittliga kostnaden per nytt affärstillfälle, som härleds från den totala kostnaden dividerat med det totala antalet nya affärsmöjligheter.

## Filterruta {#filter-pane}

Kontrollpanelen är utrustad med följande inställningar och filter:

* Datum
   * Baserat på:
      * Skapad: Nyhetsleads, nya affärsmöjligheter
      * Falldatum för kostnad: kostnad
      * Stängt datum: avskrivna intäkter (enkel avkastning på investering), erbjudanden
      * Slutpunktsdatum: kontaktytor från intjänad intäkt (realiserad avkastning på investering)
* Attributionsmodell
* Nyckelord
* Campaign
