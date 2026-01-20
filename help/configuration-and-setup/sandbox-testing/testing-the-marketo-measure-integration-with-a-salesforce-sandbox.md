---
unique-page-id: 18874765
description: Testar Marketo Measure-integrationen med en Salesforce-sandlåda - [!DNL Marketo Measure]
title: Testa Marketo Measure-integrationen med en Salesforce-sandlåda
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
feature: Salesforce
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 1%

---

# Testa Marketo Measure-integrationen med en Salesforce-sandlåda {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

En av de [!DNL Marketo Measure] viktigaste funktionerna är möjligheten att spåra era digitala marknadsföringssatsningar via åtgärder på din webbplats och sedan överföra dessa data till din produktion [!DNL Salesforce org] via Leads and Contacts. Vanligtvis finns det inga inkommande leads som skapats från din webbplats inom en sandlådeintegrering, så fokus på data kommer att ligga på en helt offline-nivå.

Här anges de två källorna som refereras till för båda testfaserna. [Steg 1-4](https://help.salesforce.com/s/articleView?id=lead_import_wizard.htm&language=en_US&type=5) och [Steg 5-6](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md). Vi rekommenderar att du granskar dessa dokument eftersom de innehåller mer information inom vissa områden.

1. Du måste skapa några leads i en CSV-fil så att du kan överföra dem till en kampanj. Så här exporterar du några leads via en rapport i din Salesforce-produktion. I annat fall kan du skapa leads i en Excel-fil manuellt och sedan spara den som en CSV-fil för import. Du behöver bara cirka 20 poster. Filen måste ha följande kolumner:

   1. E-post
   1. Företag
   1. Efternamn
   1. Förnamn (valfritt men rekommenderas)

1. Logga in i din sandlådemiljö.
1. Skapa en testkampanj. Använd en kampanjtyp som Event eller Newsletter.
1. När kampanjen har skapats kan du överföra leads som kampanjmedlemmar genom att välja **[!UICONTROL Manage Members]** > **[!UICONTROL Add Members]** > **[!UICONTROL Import Files]**.
1. När detta är klart, och sedan tillbaka till layouten för Campaign-sidan, kommer du att&quot;Enable Buyer Touchpoints&quot;, som är ett plocklistefält. Välj värdet: **[!UICONTROL Include All Campaign Members]**.

När detta är klart, inaktiveras en synkronisering mellan [!DNL Marketo Measure] och [!DNL Salesforce] och kontaktpunkter tillämpas på lead-posterna. Vi rekommenderar att du går tillbaka nästa dag via en rapport med namnet&quot;Buyer Touchpoint on Leads&quot; i mappen [!UICONTROL Buyer Touchpoints Reports] på fliken Rapporter. Om rapporten fyller i en kontaktyta för varje lead är detta ett tecken på framgång.
