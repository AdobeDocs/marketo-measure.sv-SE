---
unique-page-id: 18874765
description: Testa Marketo Measure-integrationen med en Salesforce-sandlåda - [!DNL Marketo Measure] - Produktdokumentation
title: Testa Marketo Measure-integrationen med en Salesforce-sandlåda
exl-id: df40b000-4572-46df-aef5-8f690ca8ed7a
feature: Salesforce
source-git-commit: 3df1bd288ebd65f75a2ed52d7c8a6faf50c7ff1f
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---

# Testa Marketo Measure-integrationen med en Salesforce-sandlåda {#testing-the-marketo-measure-integration-with-a-salesforce-sandbox}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

En av [!DNL Marketo Measure] grundfunktionerna är deras förmåga att spåra era digitala marknadsföringssatsningar genom åtgärder på er webbplats och sedan överföra dessa data till er produktion [!DNL Salesforce org] via leads och kontakter. Vanligtvis finns det inga inkommande leads som skapats från din webbplats inom en sandlådeintegrering, så fokus på data kommer att ligga på en helt offline-nivå.

Här anges de två källorna som refereras till för båda testfaserna. [Steg 1-4](https://help.salesforce.com/apex/HTViewHelpDoc?id=lead_import_wizard.htm&amp;language=en_US) och [Steg 5-6](/help/channel-tracking-and-setup/offline-channels/deprecated-processes/syncing-offline-campaigns.md). Vi rekommenderar att du granskar dessa dokument eftersom de innehåller mer information inom vissa områden.

1. Du måste skapa några leads i en CSV-fil så att du kan överföra dem till en kampanj. Så här exporterar du vissa leads via en rapport i Salesforce-produktionen. I annat fall kan du skapa leads i en Excel-fil manuellt och sedan spara den som en CSV-fil för import. Du behöver bara cirka 20 poster. Filen måste ha följande kolumner:

   1. E-post
   1. Företag
   1. Efternamn
   1. Förnamn (valfritt men rekommenderas)

1. Logga in i din sandlådemiljö.
1. Först skapar du en testkampanj. Vi rekommenderar att du använder en kampanjtyp som Event eller Newsletter.
1. När kampanjen har skapats överför du leads som kampanjmedlemmar genom att välja **[!UICONTROL Manage Members]** > **[!UICONTROL Add Members]** > **[!UICONTROL Import Files]**.
1. När detta är klart, och sedan tillbaka till layouten för Campaign-sidan, kommer du att&quot;Enable Buyer Touchpoints&quot;, som är ett plocklistefält. Välj värde: **[!UICONTROL Include All Campaign Members]**.

När detta är klart startar det en synkronisering mellan [!DNL Marketo Measure] och [!DNL Salesforce] och lägga in kontaktytor i leadposterna. Vi rekommenderar att du går tillbaka nästa dag via en rapport med namnet&quot;Buyer Touchpoint on Leads&quot; i [!UICONTROL Buyer Touchpoints Reports] på fliken Rapporter. Om rapporten fyller i en kontaktyta för varje lead är detta ett tecken på framgång.
