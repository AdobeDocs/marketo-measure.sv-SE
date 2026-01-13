---
description: Snabbkontrollpanel för affärsmöjlighet - [!DNL Marketo Measure]  - Produkt
title: Kontrollpanel för snabbhet i affärsmöjlighet
feature: Reporting
exl-id: d02455fd-8fca-435e-8ded-69abbbdcb3a4
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# Kontrollpanel för snabbhet i affärsmöjlighet {#opportunity-velocity-dashboard}

Snabbkontrollpanelen ger en dynamisk bild av hur de potentiella kunderna rör sig genom funnel och ger marknadsförare och säljteam viktiga insikter i konverteringstiderna över olika kanaler. Det här verktyget är värdefullt för att besvara viktiga frågor om affärsmöjlighetens livscykel och effektiviteten i utvecklingen genom försäljningsfaser, vilket gör att ni kan optimera era engagemangsstrategier för snabbare tillväxt och konverteringar.

Frågor som den här instrumentpanelen besvarar:

* Hur lång tid tar det i genomsnitt att konvertera ett lead?
* I genomsnitt, för varje fas, hur lång tid tar det för en lead eller kontakt att gå vidare till nästa fas? Hur förändras den här perioden över tid?

## Kontrollpanelskomponenter {#dashboard-components}

### KPI-panel {#kpi-tile}

* **Avstängd avtalshastighet**: Genomsnittligt antal dagar för stängda vinstmöjligheter från första fasen till avslut.

### Snabbhet för affärsmöjlighet efter fas {#opportunity-velocity-by-stage}

I stapeldiagrammet visas den genomsnittliga varaktigheten, i dagar, för de affärsmöjligheter som lagts ned i varje försäljningsfas under en viss tidsram.

Frågor om diagramsvaren:

* I vilket skede tillbringar affärsmöjligheterna mest tid i genomsnitt under den angivna tidsramen?
* Hur skiljer sig den genomsnittliga varaktigheten för affärsmöjligheter i fasen Skapa säljprojekt från fasen Prospect och Opportunity Qualifications?

>[!NOTE]
>Stegen före Skapa säljprojekt använder det senaste kontaktpunktsdatumet som indatadatum för övergången.

![Affärsmöjlighet - hastighet per stapeldiagram för försäljningsstadium](assets/lead-velocity-dashboard-1.png)

### Snabbhet för affärsmöjlighet över tid {#opportunity-velocity-over-time}

Diagrammet över tidsserierader visar den genomsnittliga tiden, i dagar, för affärstillfällen som spenderats vid varje försäljningsfas under den angivna tidsramen.

* använda detaljfunktionerna för att kategorisera data efter månad, kvartal eller år.
* Hovra över en linje för att visa detaljerad information.

Frågor om diagramsvaren:

* Vilka trender för hur lång tid som tillbringas i varje skede för att skapa möjligheter under de observerade månaderna?
* Under vilken månad upplevde möjligheterna den snabbaste utvecklingen genom försäljningsfaserna?

![Snabba trender för affärsmöjligheter över tidslinjen](assets/lead-velocity-dashboard-2.png)

### Snabbhet för affärsmöjlighet efter kanal {#opportunity-velocity-by-channel}

I stapeldiagrammet visas den genomsnittliga varaktighet (i dagar) som leads/kontakter stannar i varje funnel-fas, segmenterad efter kanal.

* Hovra över en linje för att visa detaljerad information.

Frågor om diagramsvaren:

* I vilken kanal visas den snabbaste vägen genom funnel?
* Hur varierar hastigheten på affärsmöjligheten i fasen Prospect mellan olika kanaler?

![Affärsmöjlighet, snabbhet per kanaljämförelse](assets/lead-velocity-dashboard-3.png)

## Filterruta {#filter-pane}

Kontrollpanelen är utrustad med följande inställningar och filter:

* Datum
   * Baserat på: Övergång i datum
* Scen
* Kanal
* Delkanal
* Campaign
* Segment
