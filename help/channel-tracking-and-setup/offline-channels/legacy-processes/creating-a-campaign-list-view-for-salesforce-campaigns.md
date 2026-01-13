---
description: Skapar en kampanjlistvy för  [!DNL Salesforce Campaigns] - [!DNL Marketo Measure]
title: Skapar en kampanjlistvy för  [!DNL Salesforce] kampanjer
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# Skapar en kampanjlistvy för [!DNL Salesforce] kampanjer {#creating-a-campaign-list-view-for-salesforce-campaigns}

Lär dig hur du skapar en listvy för kampanjer som du vill synkronisera med Buyer Touchpoints.

>[!NOTE]
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användare att använda den [nya, förbättrade processen i appen](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

I kampanjlistvyn som kan skapas kan du ha en plats där du kan gå till för att visa och hantera fälten Typ och Aktivera Buyer Touchpoints för att se till att alla dina [!DNL Salesforce]-kampanjer som informerar dina offlinemarknadsföringskanaler är korrekt konfigurerade.

1. Gå till fliken Kampanjer i [!DNL Salesforce] och skapa en ny listvy
1. Ge vyn namnet&quot;Kampanjer att synkronisera med [!DNL Marketo Measure]&quot;.
1. Vi vill att den här listan bara ska visa de kampanjer som vi vill synkronisera med [!DNL Marketo Measure] så vi behöver ett par filter:

   * **Typ** [MOTSVARAR] &#39;Alla kampanjtyper som vi har mappat till dina offlinekanaler&#39;. Se din implementeringsplan eller fliken Offlinekanaler i [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} -> Mitt konto -> Inställningar -> Offlinekanaler). Du kan välja vilka typer du vill använda (de som mappas till en offline-marknadsföringskanal) via förstoringsglaset.

      * Välj max 3 typer för varje filter. Det finns en gräns för hur många tecken du kan ha i ett filterfält. Börja med 3 typer per filter och lägg till ytterligare rader med Type-filter om det behövs.

   * **Skapat** [GREATER ELLER LIKA MED] ditt [!DNL Marketo Measure]-startdatum. Du kan hitta ditt startdatum i ROI-instrumentpanelen i appen [!DNL Marketo Measure]. Välj &quot;Sedan skapad den&quot; i datumintervallet för strecket så visas startdatumet.
   * **&#42;Posttyp&#42;** - Om du vill redigera i listvyn måste du lägga till ett filter för Posttyp. Alla kampanjposter som du kan behöva redigera måste vara av samma posttyp.

1. Redigera dina markerade fält så att de visas i listvyn. Den fullständiga konfigurationen av listvyn ska se ut som i exemplet nedan:

   I den här vyn kan du se dina kampanjer och redigera fälten&quot;Typ&quot; och&quot;Aktivera Buyer Touchpoints&quot; om det behövs. När du skapar nya kampanjer som ska synkroniseras med [!DNL Marketo Measure] visas de i den här vyn och du kan hantera alla inställningar för de kampanjerna direkt i listan.

   Om du vill kunna göra infogade redigeringar från listvyn måste du se till att följande även gäller i din [!DNL Salesforce]-konfiguration:

   * **[!UICONTROL Setup]** > **[!UICONTROL User Interface]** > **[!UICONTROL Enable Inline Editing]**
   * Du måste även aktivera förbättrade listor som är markerade (direkt under rutan för infogad redigering)
   * Se till att du har behörighet till fälten

>[!MORELIKETHIS]
>[Felsöka vanliga problem med infogad redigering i listvyn](http://help.salesforce.com/articleView?id=000003911&language=en_US&type=1){target="_blank"}
