---
unique-page-id: 18874539
description: Skapa anpassad [!DNL Marketo Measure] Rapporttyper - [!DNL Marketo Measure] - Produktdokumentation
title: Skapa anpassad [!DNL Marketo Measure] Rapporttyper
exl-id: 1d72a04f-6a2d-4607-ad09-3b025125156a
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Skapa anpassad [!DNL Marketo Measure] Rapporttyper {#creating-custom-marketo-measure-report-types}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men fortfarande se &quot;[!DNL Bizible]&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Lär dig hur du skapar egna [!DNL Marketo Measure] [!DNL Salesforce] rapporttyper. Det finns tre olika rapporttyper som vi rekommenderar att du skapar: Leads med Buyer Touchpoints (Custom), [!DNL Marketo Measure] Person med Buyer Touchpoints (Custom), Opportunity with Buyer Attribution Touchpoint (Custom).

## Leads med Buyer Touchpoints (Custom) {#leads-with-buyer-touchpoints-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/1.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL [!UICONTROL Primary Object]]: Lead
   * Identifiering > [!UICONTROL Report Type Label]: Leads med Buyer Touchpoints (Custom)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerat

   ![](assets/2.png)

1. Definiera objektrelationerna.

   * Relatera Lead-objektet (A) till [!DNL Marketo Measure] Person Object (B) och sedan Buyer Touchpoint Object (C)
   * Kontrollera att[!UICONTROL Each A/B record must have at least one B/C]&quot; posten är markerad
   * [!UICONTROL Save]

   ![](assets/3.png)

## [!DNL Marketo Measure] Person med Buyer Touchpoints (Custom) {#marketo-measure-person-with-buyer-touchpoints-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/4.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: [!DNL Marketo Measure] Personer
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: [!DNL Marketo Measure] Person med Buyer Touchpoints (Custom)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerat

   ![](assets/5.png)

1. Definiera objektrelationerna.

   * Relatera [!DNL Marketo Measure] Personobjekt (A) till Buyer Touchpoint-objektet (B)
   * Kontrollera att[!UICONTROL Each A record must have at least one B]&quot; posten är markerad
   * [!UICONTROL Save]

   ![](assets/6.png)

## Möjligheter med Buyer Attribution Touchpoint (anpassad) {#opportunities-with-buyer-attribution-touchpoint-custom}

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Build]** > **[!UICONTROL Report Types]** > **[!UICONTROL New Custom Report Types]**.

   ![](assets/7.png)

1. Definiera den anpassade rapporttypen.

   * [!UICONTROL Report Type Focus] > [!UICONTROL Primary Object]: Möjligheter
   * [!UICONTROL Identification] > [!UICONTROL Report Type Label]: Affärsmöjligheter med Buyer Attribution Touchpoint (anpassad)
   * [!UICONTROL Store in Category]: Andra rapporter
   * [!UICONTROL Deployment] > [!UICONTROL Deployment Status]: Distribuerat

   ![](assets/8.png)

1. Definiera objektrelationerna.

   * Relatera objektet säljprojekt (A) till slutpunktsobjektet för köparattribut (B)
   * Kontrollera att[!UICONTROL Each A record must have at least one B]&quot; posten är markerad
   * [!UICONTROL Save]

   ![](assets/9.png)

## Lägga till anpassade fält till anpassade rapporttyper {#adding-custom-fields-to-custom-report-types}

1. När du har skapat rapporterna omdirigeras du till en översikt över rapporttypen. Klicka på **[!UICONTROL Edit Layout]**.

   ![](assets/10.png)

1. Kontrollera att de anpassade fält som du vill lägga till i rapporten visas i avsnittet Egenskaper för fältlayout. Om det finns andra fält som du vill lägga till använder du[!UICONTROL Add fields related via lookup]&quot;.

   ![](assets/11.png)
