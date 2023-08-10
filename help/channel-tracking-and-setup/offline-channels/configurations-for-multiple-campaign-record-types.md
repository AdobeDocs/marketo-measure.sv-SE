---
unique-page-id: 18874686
description: Konfigurationer för flera kampanjposttyper - [!DNL Marketo Measure] - Produktdokumentation
title: Konfigurationer för flera kampanjposttyper
exl-id: 10499556-a591-4630-9149-ae676e6494af
feature: Channels
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Konfigurationer för flera kampanjposttyper {#configurations-for-multiple-campaign-record-types}

**Picklist-värden saknas i fältet&quot;Enable Buyer Touchpoints&quot;**

Om din SFDC-organisation använder flera kampanjposttyper måste plocklistevärdena för&quot;Enable Buyer Touchpoints&quot; läggas till för varje posttyp. Följ stegen nedan för att lägga till alternativen.

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Record Types]**.

   ![](assets/1.jpg)

1. Välj kampanjposttyper genom att klicka på **[!UICONTROL Record Type Label]**, inte [!UICONTROL edit] -knappen.

   ![](assets/2.jpg)

1. Här visas de tillgängliga plocklistorna för den posttypen. Välj **[!UICONTROL Edit]** bredvid fältet&quot;Enable Buyer Touchpoints&quot;.

   ![](assets/3.jpg)

1. Lägg till alla tre värdena från grupperingen&quot;Tillgängliga värden&quot; i grupperingen&quot;Valda värden&quot;.

   ![](assets/4.jpg)

1. Ange standardvärdet som Ingen och klicka på **[!UICONTROL Save]**. Upprepa för alla ytterligare typer av kampanjposter.
