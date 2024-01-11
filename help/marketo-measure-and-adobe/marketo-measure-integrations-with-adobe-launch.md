---
description: '[!DNL Marketo Measure] Integrering med Adobe Launch - [!DNL Marketo Measure] - Produktdokumentation'
title: '''[!DNL Marketo Measure] Integrering med Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 1b583dac72aadff5d7c2352a064e2ff842b91891
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 1%

---

# [!DNL Marketo Measure] Integrering med Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

Tillägget Adobe Launch är utformat för befintliga [!DNL Marketo Measure] användare som redan använder Adobe Launch på sin webbplats. Tillägget fungerar som en tagghanteringslösning som du kan använda för att konfigurera och dynamiskt läsa in skript på dina sidor baserat på vissa händelser och villkor.

När programmet installeras och konfigureras i Adobe Launch [!DNL Marketo Measure] tillägg läser in bizible.js-skriptet på de sidor där Adobe Launch-skriptet finns. Detta gör att marknadsförarna kan lägga till bizible.js via Adobe Launch-konfigurationen, i stället för att uttryckligen ändra webbsidan för att lägga till script-taggen bizible.js.

## Konfigurera Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Klicka på följande länkar för att lära dig mer om Adobe Launch och dess tillägg:
>
>* [[!DNL Marketo Measure] Tillägg](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html?lang=en#catalog){target="_blank"}
>* [Adobe Launch Overview](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/index.html?lang=en#prerequisites){target="_blank"}
>* [Adobe Launch Extension Overview](https://experienceleague.adobe.com/docs/launch/using/extension-dev/overview.html?lang=en#extension-configuration){target="_blank"}

1. Skapa en egenskap enligt stegen [i den här artikeln](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html?lang=en#go-to-the-data-collection-interface){target="_blank"}.

1. Klicka på den egenskap du nyss skapade.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Klicka på **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Klicka på **[!UICONTROL Catalog]** och sök efter &quot;[!UICONTROL Bizible].&quot;

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. I [!UICONTROL Bizible Analytics] platta, klicka **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. I fältet Bizible AccountId skriver du webbplatsens URL (t.ex. `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

   >[!NOTE]
   >
   >Det här fältet är inte &quot;konto-ID&quot; i tabellen Business_Prod.Business. Alla webbaktiviteter från angiven URL (t.ex. `adobe.com`) mappas till [!DNL Marketo Measure] tenant.

1. Klicka på **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Klicka **[!UICONTROL Rules]** väljer **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Klicka på **[!UICONTROL Add]** knapp under [!UICONTROL Events].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Välj i listrutan Tillägg **[!UICONTROL Core]**. Välj sedan i listrutan Händelsetyp **[!UICONTROL Library Loaded (Page Top)]**. Om du inte ger evenemanget ett namn används ett standardnamn. Klicka **[!UICONTROL Keep Changes]** när det är klart.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Klicka på **[!UICONTROL Add]** under Åtgärder.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Välj i listrutan Tillägg **[!UICONTROL Bizible Analytics]**. Välj sedan i listrutan Åtgärdstyp **[!UICONTROL Initialize]**. Om du inte ger funktionsmakrot ett namn används ett standardnamn. Klicka **[!UICONTROL Keep Changes]** när det är klart.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Klicka på **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)
