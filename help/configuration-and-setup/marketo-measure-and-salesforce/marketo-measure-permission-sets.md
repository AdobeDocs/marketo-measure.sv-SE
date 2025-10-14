---
unique-page-id: 18874789
description: "[!DNL Marketo Measure] behörighetsuppsättningar - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] behörighetsuppsättningar"
exl-id: 84b7aa24-3934-4584-af05-02e804d00a98
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# [!DNL Marketo Measure] behörighetsuppsättningar {#marketo-measure-permission-sets}

Lär dig hur du får åtkomst till och tilldelar [!DNL Marketo Measure] behörighetsuppsättningar i Salesforce.

## [!DNL Marketo Measure] behörighetsuppsättningar {#marketo-measure-permission-sets-1}

Det finns tre behörighetsgrupper i Salesforce-paketet [!DNL Marketo Measure]. Dessa behörighetsgrupper ger åtkomst till [!DNL Marketo Measure] för administratörer, marknadsförare och standardanvändare.

Så här öppnar och tilldelar du behörighetsuppsättningar i Salesforce:

1. Klicka på **[!UICONTROL Setup]**.
1. Klicka på **[!UICONTROL Users]** i den vänstra marginalen och sedan på **[!UICONTROL Permission Sets]**.
1. Välj den [!DNL Marketo Measure] behörighetsuppsättning som du vill tilldela.
1. Klicka på **[!UICONTROL Manage Assignments]** och sedan på **[!UICONTROL Add Assignments]**.
1. Markera användarna för behörighetsgruppen och klicka på **[!UICONTROL Assign]**.

   ![](assets/1-5.png)

## [!DNL Marketo Measure] behörighetsuppsättningar förklaras {#marketo-measure-permission-sets-explained}

<table> 
 <tbody> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Administratör</strong></span></td> 
   <td><span>Ger en SFDC-administratör möjlighet att skapa, läsa, skriva och ta bort poster från [!DNL Marketo Measure] objekt. Den licens som [!DNL Marketo Measure] använder för att skicka data till SFDC bör ha den här behörighetsuppsättningen aktiverad. Vi rekommenderar även att den här licensen kan redigera konverterade leads i scenarier där lead konverteras innan [!DNL Marketo Measure] använder data för posten. Detta garanterar att rapporteringen mellan Salesforce och [!DNL Marketo Measure] är korrekt. <a href="https://help.salesforce.com/articleView?id=release-notes.rn_sales_leads_view_converted.htm&type=5&release=206&language=en_us">Läs mer här</a>.</span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Marknadsförare</strong></span></td> 
   <td><span>Ger en marknadsföringsanvändare möjlighet att läsa och skriva poster från [!DNL Marketo Measure] objekt. Alla medlemmar i marknadsföringsteamet ska ha behörighetsuppsättningen [!DNL Marketo Measure] Marketing User aktiverad. <br></span></td> 
  </tr> 
  <tr> 
   <td><span><strong>[!DNL Marketo Measure] Standardanvändare</strong></span></td> 
   <td><span>Ger en användare möjlighet att läsa poster från [!DNL Marketo Measure] objekt.</span></td> 
  </tr> 
 </tbody> 
</table>

Inkommande säljutvecklingsteam och kontochefer kan ha nytta av [!DNL Marketo Measure]-data. Om de här rollerna vill använda [!DNL Marketo Measure]-data vid rapportering aktiverar du behörighetsuppsättningen [!DNL Marketo Measure] Standardanvändare.

>[!NOTE]
>
>Dessutom måste användaren som vi är anslutna via ha profilen Marknadsförare [!DNL Salesforce] aktiverad på användarnivå för att vi ska kunna komma åt Campaign-objektet. Om du vill kontrollera detta klickar du på **[!UICONTROL Setup]** > **[!UICONTROL Manage Users]** > **[!UICONTROL Profiles]** > **[!UICONTROL Marketing User]** > **Tilldelade användare**.
