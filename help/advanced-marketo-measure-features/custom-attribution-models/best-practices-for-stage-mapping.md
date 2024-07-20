---
description: Bästa praxis för Stage Mapping - [!DNL Marketo Measure]
title: Metodtips för scenmappning
exl-id: 1ed380a1-4a3a-4761-b70f-cdf2e290329d
feature: Tracking, Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Metodtips för scenmappning {#best-practices-for-stage-mapping}

## Översikt {#overview}

Avsnittet Stage Mapping i ditt [!DNL Marketo Measure]-konto visar de faser som [!DNL Marketo Measure] automatiskt hämtar från din CRM och alla anpassade stadier som du har definierat om du använder den anpassade attributmodellen. Giltigheten hos dina [!DNL Marketo Measure]-data är beroende av att de här stegen ordnas korrekt, så att [!DNL Marketo Measure] kan förstå tratten och hur posterna fortskrider under hela tratten.

I avsnittet Stage Mapping för instansen [!DNL Marketo Measure] visas både aktiva och inaktiva steg från CRM. Ordna alla faser efter dina behov och anpassa dem efter hur tratten fungerar idag.

Ytterligare en funktion som hanteras i det här avsnittet är Funnel Stages, som ger dig möjlighet att lägga till faser i tratten utan att tillämpa attribuering. Tratt Stages spåras som Touchpoints och fylls i i fältet Positions för kontaktpunkter i CRM. Dessa trattfaser representeras också i olika resevakningar i [!DNL Marketo Measure] Discover.

## Bästa praxis {#best-practices}

Oavsett om du utvärderar din Stage Mapping för första gången eller bara granskar din kanalordning är det viktigt att tänka på följande när det gäller metodtips.

* Beställning är allt!
   * Om du överväger [!DNL Marketo Measure] pullingar i både aktiva och inaktiva faser från CRM, måste du bekräfta att alla stadier som kan användas på en lead/kontakt eller ett säljprojekt grupperas tillsammans och sorteras därefter
* När du definierar en anpassad scen måste du se till att spårning av fälthistorik är aktiverat för alla fält som används för att definiera scenen
* Använd inte ett formelfält för att definiera en anpassad fas
   * Ett booleskt fält är den bästa metoden
* Observera att avsnittet Lead- eller Kontaktstadium är uppdelat i Förlorat, Öppna och Konverterad. Kontrollera att stadierna är i rätt scenavsnitt
   * Om du har en scen i ett felaktigt scenavsnitt kan [!DNL Marketo Measure]-data bli felaktigt
   * Om du är Marketo Measure Ultimate-kund och har angett ditt standardinstrumentpanelsobjekt som kontakt ska du inte använda de två fält nedan som är specifika för lead ([läs mer](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).
      * b2b.personStatus
      * b2b.isConverted
* Observera att avsnittet för säljprojektsfasen är uppdelat i Förlorat, Öppna och Von. Kontrollera att faserna befinner sig i rätt fasavsnitt
   * Om du har en fas i ett felaktigt fasavsnitt kan det resultera i mycket felaktiga intäktsdata för [!DNL Marketo Measure] eller pipeline-intäkter
* Undvik att använda duplicerade scennamn (systemet identifierar dem och tar automatiskt bort ett).
* Om du vill ange en regel som kontrollerar om det finns NULL-värden lämnar du värdetextrutan tom.

## Bästa praxis för underhåll {#best-practices-for-maintenance}

Om du granskar din Stage Mapping en gång om året ser du till att dina säljprojektsdata i [!DNL Marketo Measure] är korrekta och aktuella.

Andra orsaker till varför du kan starta en granskning av din Stage Mapping är ...

* Omsättning i marknadsföringsteamet
* Alla ändringar i CRM-stegen
* Uppdateringar av organisationens tratt
* Se felaktiga intäktsdata i din [!DNL Marketo Measure]-rapportering

>[!MORELIKETHIS]
>
>[Skillnaden mellan trattfaser och anpassade modellsteg](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md#the-difference-between-funnel-stages-and-custom-model-stages)
