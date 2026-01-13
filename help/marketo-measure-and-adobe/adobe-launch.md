---
description: '[!DNL Marketo Measure] integreringar med Adobe Launch - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] integreringar med Adobe Launch'
exl-id: 316ee8a8-b2d3-42e9-9ee5-c9b1d91c2769
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# [!DNL Marketo Measure] integreringar med Adobe Launch {#marketo-measure-integrations}

Adobe Launch-tillägget är utformat för befintliga [!DNL Marketo Measure]-användare som redan använder Adobe Launch på sin webbplats. Tillägget fungerar som en tagghanteringslösning som du kan använda för att konfigurera och dynamiskt läsa in skript på dina sidor baserat på vissa händelser och villkor.

När tillägget [!DNL Marketo Measure] installeras och konfigureras i Adobe Launch läses det in bizible.js-skript på de sidor där Adobe Launch-skript finns. Detta gör att marknadsförarna kan lägga till bizible.js via Adobe Launch-konfigurationen, i motsats till att uttryckligen ändra webbsidan för att lägga till script-taggen bizible.js.

## Konfigurera Adobe Launch Extension {#configure-the-adobe-launch-extension}

>[!PREREQUISITES]
>Klicka på följande länkar för att lära dig mer om Adobe Launch och dess tillägg:
> [[!DNL Marketo Measure] Tillägg ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email/bizible.html#catalog){target="_blank"}
> [Adobe Launch Overview](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/overview.html){target="_blank"}
> [Adobe Launch Extension Overview](https://experienceleague.adobe.com/docs/experience-platform/tags/extension-dev/overview.html){target="_blank"}

1. Skapa en egenskap enligt stegen [ i den här artikeln](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html#go-to-the-data-collection-interface){target="_blank"}.

1. Klicka på den egenskap som du skapade.

   ![Markeringsskärmen för Adobe Launch-egenskapen visar tillgängliga egenskaper](assets/marketo-measure-integrations-1.png)

1. Klicka på **[!UICONTROL Extensions]**.

   ![Fliken Tillägg i egenskapsinställningarna för Adobe Launch](assets/marketo-measure-integrations-2.png)

1. Klicka på fliken **[!UICONTROL Catalog]** och sök efter [!UICONTROL Bizible].

   ![Sökningen i tilläggskatalogen visar Bizible-tillägg](assets/marketo-measure-integrations-3.png)

1. Klicka på [!UICONTROL Bizible Analytics] i rutan **[!UICONTROL Install]**.

   ![Tilläggsrutan Bizible Analytics med Install-knappen](assets/marketo-measure-integrations-4.png)

1. I fältet Bizible AccountId anger du webbplatsens URL (till exempel `adobe.com`).

   ![Bizible-tilläggskonfiguration med AccountId-fält](assets/marketo-measure-integrations-5.png)

1. Klicka på **[!UICONTROL Save]**.

   ![Spara-knapp för Bizible-tilläggskonfiguration](assets/marketo-measure-integrations-6.png)

1. Klicka på **[!UICONTROL Rules]** och välj sedan **[!UICONTROL Create New Rule]**.

   ![Fliken Regler med knappen Skapa ny regel](assets/marketo-measure-integrations-7.png)

1. Klicka på knappen **[!UICONTROL Add]** under [!UICONTROL Events].

   ![Lägg till knapp i händelseavsnittet i regelkonfigurationen](assets/marketo-measure-integrations-8.png)

1. Välj **[!UICONTROL Core]** i listrutan Tillägg. Välj sedan **[!UICONTROL Library Loaded (Page Top)]** i listrutan Händelsetyp. Om du inte ger evenemanget ett namn används ett standardnamn. Klicka på **[!UICONTROL Keep Changes]** när du är klar.

   ![Dialogrutan Händelsekonfiguration med Core-tillägg och biblioteksinläst händelsetyp ](assets/marketo-measure-integrations-9.png)

1. Klicka på knappen **[!UICONTROL Add]** under Åtgärder.

   ![Knappen Lägg till i avsnittet Åtgärder i regelkonfigurationen](assets/marketo-measure-integrations-10.png)

1. Välj **[!UICONTROL Bizible Analytics]** i listrutan Tillägg. Välj sedan **[!UICONTROL Initialize]** i listrutan Åtgärdstyp. Om du inte ger funktionsmakrot ett namn används ett standardnamn. Klicka på **[!UICONTROL Keep Changes]** när du är klar.

   ![Dialogruta för åtgärdskonfiguration med tillägget Bizible Analytics och åtgärdstypen Initialize](assets/marketo-measure-integrations-11.png)

1. Klicka på **[!UICONTROL Save]**.

   ![Spara-knapp för regelkonfiguration](assets/marketo-measure-integrations-12.png)

