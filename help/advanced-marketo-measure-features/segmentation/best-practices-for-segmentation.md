---
description: Bästa praxis för segmentering - [!DNL Marketo Measure]
title: Bästa praxis för segmentering
exl-id: 68281210-383b-4688-86e9-27fbdc1fabbb
feature: Segmentation
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Bästa praxis för segmentering {#best-practices-for-segmentation}

## Översikt {#overview}

Med [!DNL Marketo Measure]-segmentering kan du definiera regler, som i huvudsak är filter, baserat på dina CRM-fält, så att de kan grupperas i enskilda segment. Dessa segment kommer sedan att vara tillgängliga för användning i dina Discover-instrumentpaneler och din [!DNL Salesforce]-rapportering.

Segmentering är avgörande för att ditt [!DNL Marketo Measure]-konto ska kunna användas, särskilt inom Discover boards. Eftersom [!DNL Marketo Measure] Discover-panelerna är begränsade till en fördefinierad uppsättning filter, ger segmentering dig möjlighet att dissekera dina data i Discover på ungefär samma sätt som i din [!DNL Salesforce]-rapportering.

När segmentvärden skickas till [!DNL Salesforce] skrivs de till segmentfältet och ligger inom alla rapporttyper för Buyer-kontaktyta. På så sätt blir rapporteringen enhetlig på båda plattformarna. Segmentet finns också på &#39;Touchpoint Detail&#39; i alla kontaktytor.

När segmenten flyttas till [!UICONTROL Discover] visas de som ett tillgängligt filter på den nedrullningsbara filtermenyn som finns på alla ritytor.

## Bästa praxis {#best-practice}

Oavsett om du definierar segmentering för första gången eller bara granskar den segmentering som har upprättats tidigare bör du tänka på följande.

* Gör det enkelt!
* Justera segmentnamnet efter organisationens nomenklatur, d.v.s. kategorin = filternamn, segment = filtervärde
* Använd inte formelfält i dina regler
* Bygg segmenteringen när det är möjligt på både lead/kontakt och säljprojekt så att du kan använda den i hela tratten
   * Om du är Marketo Measure Ultimate-kund och har angett ditt standardinstrumentpanelsobjekt som kontakt ska du inte använda de två fält nedan som är specifika för lead ([läs mer här](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
   * Alla segmentkategorier justeras inte i hela tratten
      * En segmentkategori för säljprojektstyp kommer inte att relatera till leads, men ett segment som är relaterat till Region är troligen en kategori som kan definieras genom hela tratten
* Fundera på hur du för närvarande vill segmentera dina data, oavsett om de finns i CRM eller ett BI-verktyg, bör du överväga att skapa detta som ett segment i [!DNL Marketo Measure] så att du kan få samma rapportering i Upptäck

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar din segmentering minst två gånger per år ser du till att din segmentering är aktuell. Vi rekommenderar att du granskar dina regler på fliken [!UICONTROL Segments] i dina [!DNL Marketo Measure]-kontoinställningar och drar in rapporter i [!DNL Salesforce] för att granska dina segment i praktiken. Dessa steg hjälper dig och ditt team att känna sig säkra på din segmentering och därefter din [!DNL Marketo Measure]-rapportering.

Andra orsaker till detta kan utlösa en granskning av segmenteringen är ...

* Omsättning i marknadsföringsteamet
* Ändringar i fält som används för att definiera segment
* Tillägg eller ändringar av segment som redan har etablerats

>[!MORELIKETHIS]
>
>[Konfigurera anpassad segmentering](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md)
