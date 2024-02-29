---
description: Metodtips för scenmappning - [!DNL Marketo Measure]
title: Metodtips för scenmappning
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Metodtips för scenmappning {#best-practices-for-stage-mapping}

## Översikt {#overview}

Avsnittet Stage Mapping i [!DNL Marketo Measure] kontot visar de faser som [!DNL Marketo Measure] hämtar automatiskt från din CRM och alla anpassade stadier som du har definierat om du använder den anpassade attributmodellen. Giltigheten hos [!DNL Marketo Measure] data är beroende av att dessa steg ordnas korrekt, så att [!DNL Marketo Measure] kan förstå er tratt och utvecklingen av register genom hela tratten.

I avsnittet Stage Mapping i [!DNL Marketo Measure] Du kan till exempel se både aktiva och inaktiva faser från CRM. Ordna alla faser efter dina behov och anpassa dem efter hur tratten fungerar idag.

Ytterligare en funktion som hanteras i det här avsnittet är Funnel Stages, som ger dig möjlighet att lägga till faser i tratten utan att tillämpa attribuering. Tratt Stages spåras som Touchpoints och fylls i i fältet Positions för kontaktpunkter i CRM. Dessa trattfaser kommer också att representeras i olika reselinjer i [!DNL Marketo Measure] Upptäck.

## Bästa praxis {#best-practices}

Oavsett om du utvärderar din Stage Mapping för första gången eller bara granskar din kanalordning är det viktigt att tänka på följande när det gäller metodtips.

* Beställning är allt!
   * Överväg [!DNL Marketo Measure] hämta in både aktiva och inaktiva faser från CRM, bekräfta att alla stadier som kan användas på en lead/kontakt eller säljprojekt grupperas tillsammans och ordnas därefter
* När du definierar en anpassad scen måste du se till att spårning av fälthistorik är aktiverat för alla fält som används för att definiera scenen
* Använd inte ett formelfält för att definiera en anpassad fas
   * Ett booleskt fält är den bästa metoden
* Observera att avsnittet Lead- eller Kontaktstadium är uppdelat i Förlorat, Öppna och Konverterad. Kontrollera att stadierna är i rätt scenavsnitt
   * Om du har en scen i ett felaktigt scenavsnitt kan det resultera i mycket felaktigt [!DNL Marketo Measure] data
   * Om du är kund hos Marketo Measure Ultimate och har angett ditt standardinstrumentpanelsobjekt som kontakt ska du inte använda de två fält nedan som är specifika för lead ([läs mer här](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* Observera att avsnittet för säljprojektsfasen är uppdelat i Förlorat, Öppna och Von. Kontrollera att faserna befinner sig i rätt fasavsnitt
   * Om du har en scen i ett felaktigt scenavsnitt kan det resultera i mycket felaktigt [!DNL Marketo Measure] intäktsdata för pipeline
* Undvik att använda duplicerade scennamn (systemet identifierar dem och tar automatiskt bort ett).
* Om du vill ange en regel som kontrollerar om det finns NULL-värden lämnar du värdetextrutan tom.

## Bästa praxis för underhåll {#best-practices-for-maintenance}

Om du granskar din Stage Mapping en gång om året ser du till att dina säljprojektsdata i [!DNL Marketo Measure] är korrekt och aktuell.

Andra orsaker till varför du kan starta en granskning av din Stage Mapping är ...

* Omsättning i marknadsföringsteamet
* Alla ändringar i CRM-stegen
* Uppdateringar av organisationens tratt
* Se felaktiga intäktsdata i [!DNL Marketo Measure] rapportering

>[!MORELIKETHIS]
>
>[Skillnaden mellan trattfaser och anpassade modellfaser](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
