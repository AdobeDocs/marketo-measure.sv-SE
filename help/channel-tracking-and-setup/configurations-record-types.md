---
description: Konfigurationer för vägledning om flera kampanjposttyper för Marketo Measure-användare
title: Konfigurationer för flera kampanjposttyper
exl-id: 10499556-a591-4630-9149-ae676e6494af
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 2%

---

# Konfigurationer för flera kampanjposttyper {#configurations-for-multiple-campaign-record-types}

**Picklist-värden saknas i fältet&quot;Enable Buyer Touchpoints&quot;**

Om din SFDC-organisation använder flera kampanjposttyper måste plocklistevärdena för&quot;Enable Buyer Touchpoints&quot; läggas till för varje posttyp. Följ stegen nedan för att lägga till alternativen.

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Record Types]**.

   ![1. Gå till Konfigurera Anpassa posttyper för kampanjer.](assets/offline-channels-19.jpg)

1. Välj kampanjposttyper genom att klicka på knappen **[!UICONTROL Record Type Label]**, inte på knappen [!UICONTROL edit].

   ![1. Välj kampanjposttyper genom att klicka på posttypen &#x200B;](assets/offline-channels-15.jpg)

1. Här visas de tillgängliga plocklistorna för den posttypen. Välj **[!UICONTROL Edit]** bredvid fältet Aktivera slutpunkter för köpare.

   ![1. Här visas de tillgängliga plocklistorna för &#x200B;](assets/offline-channels-18.jpg)

1. Lägg till alla tre värdena från grupperingen&quot;Tillgängliga värden&quot; i grupperingen&quot;Valda värden&quot;.

   ![1. Lägg till alla tre värdena från grupperingen &quot;Tillgängliga värden&quot; i &#x200B;](assets/offline-channels-10.jpg)

1. Ange standardvärdet som Ingen och klicka på **[!UICONTROL Save]**. Upprepa för alla ytterligare typer av kampanjposter.
