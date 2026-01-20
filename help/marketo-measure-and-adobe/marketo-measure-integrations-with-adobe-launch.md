---
description: '[!DNL Marketo Measure] integreringar med Adobe Launch - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] integreringar med Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 1%

---

# [!DNL Marketo Measure] integreringar med Adobe Launch {#marketo-measure-integrations-with-adobe-launch}

Adobe Launch-tillägget är utformat för befintliga [!DNL Marketo Measure]-användare som redan använder Adobe Launch på sin webbplats. Tillägget fungerar som en tagghanteringslösning som du kan använda för att konfigurera och dynamiskt läsa in skript på dina sidor baserat på vissa händelser och villkor.

När tillägget [!DNL Marketo Measure] installeras och konfigureras i Adobe Launch läses det in bizible.js-skript på de sidor där Adobe Launch-skript finns. Detta gör att marknadsförarna kan lägga till bizible.js via Adobe Launch-konfigurationen, i motsats till att uttryckligen ändra webbsidan för att lägga till script-taggen bizible.js.

## Konfigurera Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>
>Klicka på följande länkar för att lära dig mer om Adobe Launch och dess tillägg:
>
>* [[!DNL Marketo Measure] Tillägg](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
>* [Adobe Launch Overview](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
>* [Adobe Launch Extension - översikt](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Skapa en egenskap enligt stegen [&#x200B; i den här artikeln](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Klicka på den egenskap som du skapade.

   ![](assets/marketo-measure-integrations-with-adobe-launch-1.png)

1. Klicka på **[!UICONTROL Extensions]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-2.png)

1. Klicka på fliken **[!UICONTROL Catalog]** och sök efter [!UICONTROL Bizible].

   ![](assets/marketo-measure-integrations-with-adobe-launch-3.png)

1. Klicka på [!UICONTROL Bizible Analytics] i rutan **[!UICONTROL Install]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-4.png)

1. I fältet Bizible AccountId anger du webbplatsens URL (till exempel `adobe.com`).

   ![](assets/marketo-measure-integrations-with-adobe-launch-5.png)

1. Klicka på **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-6.png)

1. Klicka på **[!UICONTROL Rules]** och välj sedan **[!UICONTROL Create New Rule]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-7.png)

1. Klicka på knappen **[!UICONTROL Add]** under [!UICONTROL Events].

   ![](assets/marketo-measure-integrations-with-adobe-launch-8.png)

1. Välj **[!UICONTROL Core]** i listrutan Tillägg. Välj sedan **[!UICONTROL Library Loaded (Page Top)]** i listrutan Händelsetyp. Om du inte ger evenemanget ett namn används ett standardnamn. Klicka på **[!UICONTROL Keep Changes]** när du är klar.

   ![](assets/marketo-measure-integrations-with-adobe-launch-9.png)

1. Klicka på knappen **[!UICONTROL Add]** under Åtgärder.

   ![](assets/marketo-measure-integrations-with-adobe-launch-10.png)

1. Välj **[!UICONTROL Bizible Analytics]** i listrutan Tillägg. Välj sedan **[!UICONTROL Initialize]** i listrutan Åtgärdstyp. Om du inte ger funktionsmakrot ett namn används ett standardnamn. Klicka på **[!UICONTROL Keep Changes]** när du är klar.

   ![](assets/marketo-measure-integrations-with-adobe-launch-11.png)

1. Klicka på **[!UICONTROL Save]**.

   ![](assets/marketo-measure-integrations-with-adobe-launch-12.png)

