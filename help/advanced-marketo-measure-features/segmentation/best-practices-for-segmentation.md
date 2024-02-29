---
description: Bästa praxis för segmentering - [!DNL Marketo Measure]
title: Bästa praxis för segmentering
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Bästa praxis för segmentering {#best-practices-for-segmentation}

## Översikt {#overview}

[!DNL Marketo Measure] Med segmentering kan du definiera regler, som i huvudsak är filter, baserat på dina CRM-fält, för att kunna bugga in dem i enskilda segment. Segmenten kommer sedan att vara tillgängliga för användning på Discover-panelerna samt på [!DNL Salesforce] rapportering.

Segmentering är avgörande för att du ska kunna använda [!DNL Marketo Measure] konto, särskilt i Discover boards. På grund av [!DNL Marketo Measure] Upptäck endast en fördefinierad uppsättning filter, segmentering ger dig möjlighet att dissekera data i Upptäck ungefär som i [!DNL Salesforce] rapportering.

Vid överföring till [!DNL Salesforce], skrivs segmentvärden till segmentfältet och ligger inom alla rapporttyper för köparens kontaktyta. På så sätt blir rapporteringen enhetlig på båda plattformarna. Segmentet finns också på &#39;Touchpoint Detail&#39; i alla kontaktytor.

Vid överföring till [!UICONTROL Discover], visas segment som ett tillgängligt filter på den nedrullningsbara filtermenyn som finns på alla ritytor.

## Bästa praxis {#best-practice}

Oavsett om du definierar segmentering för första gången eller bara granskar den segmentering som har upprättats tidigare bör du tänka på följande bästa praxis.

* Gör det enkelt!
* Justera segmentnamnet efter organisationens nomenklatur, d.v.s. kategorin = filternamn, segment = filtervärde
* Använd inte formelfält i dina regler
* Bygg segmenteringen när det är möjligt på både lead/kontakt och säljprojekt så att du kan använda den i hela tratten
   * Om du är kund hos Marketo Measure Ultimate och har angett ditt standardinstrumentpanelsobjekt som kontakt ska du inte använda nedanstående två fält som är specifika för lead ([läs mer här](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
   * Alla segmentkategorier justeras inte i hela tratten
      * En segmentkategori för säljprojektstyp kommer inte att relatera till leads, men ett segment som är relaterat till Region är troligen en kategori som kan definieras genom hela tratten
* Fundera på hur du för närvarande vill segmentera data, oavsett om det är i CRM- eller BI-verktyget, och överväg att bygga upp detta som ett segment i [!DNL Marketo Measure] så att du kan få samma rapportering i Discover

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar din segmentering minst två gånger per år ser du till att din segmentering är aktuell. Vi rekommenderar att du granskar dina regler i[!UICONTROL Segments]fliken &#39; [!DNL Marketo Measure] Kontoinställningar, samt att ta fram rapporter i [!DNL Salesforce] för att granska era segment i praktiken. Dessa steg hjälper dig och ditt team att känna sig säkra på segmenteringen och därefter på att [!DNL Marketo Measure] rapportering.

Andra orsaker till detta kan utlösa en granskning av segmenteringen är ...

* Omsättning i marknadsföringsteamet
* Ändringar i fält som används för att definiera segment
* Tillägg eller ändringar av segment som redan har etablerats

>[!MORELIKETHIS]
>
>[Konfigurera anpassad segmentering](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
