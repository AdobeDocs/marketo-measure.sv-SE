---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] Behörighetsuppsättningar - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Behörighetsuppsättningar"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# [!DNL Marketo Measure] Behörighetsuppsättningar {#marketo-measure-permission-sets}

Lär dig hur du får tillgång till och tilldelar [!DNL Marketo Measure] Behörighetsuppsättningar i Salesforce.

## [!DNL Marketo Measure] Behörighetsuppsättningar {#marketo-measure-permission-sets-1}

Tre behörighetsgrupper ingår i [!DNL Marketo Measure] Salesforce-paket. Dessa behörighetsgrupper ger åtkomst till [!DNL Marketo Measure] för administratörer, marknadsförare och standardanvändare.

Så här öppnar och tilldelar du behörighetsuppsättningar i Salesforce:

1. Klicka på **[!UICONTROL Setup]**.
1. Klicka på i vänstermarginalen **[!UICONTROL Users]** sedan **[!UICONTROL Permission Sets]**.
1. Välj [!DNL Marketo Measure] Behörighetsuppsättning som du vill tilldela.
1. Klicka **[!UICONTROL Manage Assignments]** sedan **[!UICONTROL Add Assignments]**.
1. Välj användare för behörighetsgruppen och klicka på **[!UICONTROL Assign]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] Förklarade behörighetsuppsättningar {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Administratör</strong></span></td> 
   <td><span>Ger en SFDC-administratör möjlighet att skapa, läsa, skriva och ta bort poster från [!DNL Marketo Measure] objekt. Licensen enligt vilken [!DNL Marketo Measure] data skickas till SFDC om den här behörighetsuppsättningen ska vara aktiverad. Vi rekommenderar även att den här licensen kan redigera konverterade leads i scenarier där lead konverteras före [!DNL Marketo Measure] använder data på posten. Detta garanterar att rapporteringen mellan Salesforce och [!DNL Marketo Measure]. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&amp;type=5&amp;release=206&amp;language=en_us">Läs mer här</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Marknadsförare</strong></span></td> 
   <td><span>Ger en marknadsföringsanvändare möjlighet att läsa och skriva poster från [!DNL Marketo Measure] objekt. Alla medlemmar i marknadsföringsteamet ska ha [!DNL Marketo Measure] Behörighetsuppsättningen Marknadsförare har aktiverats. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Standardanvändare</strong></span></td> 
   <td><span>Ger en användare möjlighet att läsa poster från [!DNL Marketo Measure] objekt.</span></td> 
  </tr> 
 </tbody> 
</table>

Inkommande säljutvecklingsteam och kontoansvariga kan ha nytta av [!DNL Marketo Measure] data. Om de här rollerna vill använda [!DNL Marketo Measure] data i rapporter, aktivera [!DNL Marketo Measure] Behörighetsuppsättning för standardanvändare.

>[!NOTE]
>
>Dessutom måste användaren som vi är anslutna via ha&quot;marknadsföringsanvändare&quot; [!DNL Salesforce] Profilen är aktiverad på användarnivå så att vi kan komma åt Campaign-objektet. Om du vill kontrollera detta klickar du på **[!UICONTROL Setup]** > **[!UICONTROL Manage Users]** > **[!UICONTROL Profiles]** > **[!UICONTROL Marketing User]** > **Tilldelade användare**.
