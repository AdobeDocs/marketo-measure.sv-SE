---
unique-page-id: 18874539
description: Skapar anpassade  [!DNL Marketo Measure] rapporttyper - [!DNL Marketo Measure]
title: Skapar anpassade  [!DNL Marketo Measure] rapporttyper
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
feature: Reporting
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Skapar anpassade [!DNL Marketo Measure]-rapporttyper {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se [!DNL Bizible] i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Lär dig hur du skapar anpassade [!DNL Marketo Measure] [!DNL Salesforce]-rapporttyper. Det finns tre olika rapporttyper som vi rekommenderar att du skapar: Leads med Buyer Touchpoints (Custom), [!DNL Marketo Measure] Person med Buyer Touchpoints (Custom), Opportunity with Buyer Attribution Touchpoint (Custom).

## Leads med Buyer Touchpoints (Custom) {#leads-with-buyer-touchpoints-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/1.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL [!UICONTROL Primary Object]]: Lead
   * Identifiering > [!UICONTROL Report Type Label]: Leads med Buyer Touchpoints (Custom)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerad

   ![](assets/2.png)

1. Definiera objektrelationerna.

   * Koppla Lead-objektet (A) till [!DNL Marketo Measure] Person-objektet (B) och sedan till Buyer Touchpoint-objektet (C)
   * Kontrollera att posten [!UICONTROL Each A/B record must have at least one B/C] är markerad
   * [!UICONTROL Save]

   ![](assets/3.png)

## [!DNL Marketo Measure] person med Buyer Touchpoints (anpassad) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/4.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: [!DNL Marketo Measure] personer
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: [!DNL Marketo Measure] Person med Buyer Touchpoints (Custom)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerad

   ![](assets/5.png)

1. Definiera objektrelationerna.

   * Relatera [!DNL Marketo Measure]-personobjektet (A) till Buyer Touchpoint-objektet (B)
   * Kontrollera att posten [!UICONTROL Each A record must have at least one B] är markerad
   * [!UICONTROL Save]

   ![](assets/6.png)

## Möjligheter med Buyer Attribution Touchpoint (anpassad) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/7.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: Affärsmöjligheter
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: Möjligheter med Buyer Attribution Touchpoint (anpassat)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerad

   ![](assets/8.png)

1. Definiera objektrelationerna.

   * Relatera objektet säljprojekt (A) till Buyer Attribution Touchpoint-objektet (B)
   * Kontrollera att posten [!UICONTROL Each A record must have at least one B] är markerad
   * [!UICONTROL Save]

   ![](assets/9.png)

## Lägga till anpassade fält till anpassade rapporttyper {#adding-custom-fields-to-custom-report-types}

1. När du har skapat rapporterna omdirigeras du till en översikt över rapporttypen. Klicka på **[!UICONTROL Edit Layout]**.

   ![](assets/10.png)

1. Kontrollera att de anpassade fält som du vill lägga till i rapporten visas i avsnittet Egenskaper för fältlayout. Om det finns andra fält som du vill lägga till använder du alternativet [!UICONTROL Add fields related via lookup].

   ![](assets/11.png)
