---
unique-page-id: 18874718
description: Skapa en kampanjlistvy för [!DNL Salesforce Campaigns] - [!DNL Marketo Measure] - Produktdokumentation
title: Skapa en kampanjlistvy för [!DNL Salesforce] Kampanjer
exl-id: 8c673ea3-ac24-4b3d-b67d-76888179c07a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Skapa en kampanjlistvy för [!DNL Salesforce] Kampanjer {#creating-a-campaign-list-view-for-salesforce-campaigns}

Lär dig hur du skapar en listvy för kampanjer som du vill synkronisera med Buyer Touchpoints.

I kampanjlistvyn som kan skapas kan du ha en&quot;gå till&quot;-plats där du kan se och hantera fälten&quot;Typ&quot; och&quot;Aktivera slutpunkter för köpare&quot; för att se till att var och en av dina [!DNL Salesforce] kampanjer som informerar era offline-marknadsföringskanaler är korrekt konfigurerade.

1. Gå till fliken Campaigns i [!DNL Salesforce] och skapa en ny listvy
1. Ge vyn namnet&quot;Kampanjer att synkronisera med [!DNL Marketo Measure].&quot;
1. Vi vill att den här listan bara ska visa de kampanjer som vi vill synkronisera med [!DNL Marketo Measure] så vi behöver ett par filter:

   * **Typ** [LIKA MED] &#39;Alla kampanjtyper som vi har mappat till era offlinekanaler&#39;. Se din implementeringsplan eller fliken Offlinekanaler i [!DNL Marketo Measure] ([experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} -> Mitt konto -> Inställningar -> Offlinekanaler). Du kan välja vilka typer du vill använda (de som mappas till en offline-marknadsföringskanal) via förstoringsglaset.

      * Välj max 3 typer för varje filter. Det finns en gräns för hur många tecken du kan ha i ett filterfält. Börja med 3 typer per filter och lägg till ytterligare rader med Type-filter om det behövs.
   * **Skapad den** [STÖRRE ELLER LIKA] din [!DNL Marketo Measure] startdatum. Du hittar startdatumet på kontrollpanelen för avkastning på investering i [!DNL Marketo Measure] App. Välj &quot;Sedan skapad den&quot; i datumintervallet för strecket så visas startdatumet.
   * **&#42;Posttyp&#42;** - Om du vill redigera i listvyn måste du lägga till ett filter för Posttyp. Alla kampanjposter som du kan behöva redigera måste vara av samma posttyp.


1. Redigera dina markerade fält så att de visas i listvyn. Den fullständiga konfigurationen av listvyn ska se ut som i exemplet nedan:

   I den här vyn kan du se dina kampanjer och redigera fälten&quot;Typ&quot; och&quot;Aktivera Buyer Touchpoints&quot; om det behövs. När ni skapar nya kampanjer som ska synkroniseras med [!DNL Marketo Measure]kommer de att visas i den här vyn och du kan hantera alla inställningar för de kampanjer direkt från listan.

   Om du vill kunna göra infogade redigeringar från listvyn måste du se till att följande också stämmer inom din [!DNL Salesforce] inställning:

   * **[!UICONTROL Setup]** > **[!UICONTROL User Interface]** > **[!UICONTROL Enable Inline Editing]**
   * Du måste även aktivera förbättrade listor som är markerade (direkt under rutan för infogad redigering)
   * Se till att du har behörighet till fälten

>[!MORELIKETHIS]
>
>[Felsöka vanliga problem med infogad redigering i listvyn](http://help.salesforce.com/articleView?id=000003911&amp;language=en_US&amp;type=1){target=&quot;_blank&quot;}
