---
description: Salesforce Sandbox to Production Migration guidelines for Marketo Measure users
title: Salesforce Sandbox to Production Migration
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Salesforce Sandbox to Production Migration {#salesforce-sandbox-to-production-migration}

Om du väljer att testa [!DNL Marketo Measure] i en [!DNL Salesforce] sandlådemiljö följer du de här instruktionerna för att migrera till Production när du är klar. I följande instruktioner antas att du redan har hämtat paketet [!DNL Marketo Measure] till din sandlådeorganisation, utfört nödvändig testning och är redo att överföra [!DNL Marketo Measure] till produktion.

## Steg 1: Installera paketet [!DNL Marketo Measure] i din [!DNL Salesforce]-produktionsinstans

* Installera paketet [!DNL Marketo Measure] i Production med inställningen [!UICONTROL All Users]

   * [Baskaket](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Mer information om [!DNL Marketo Measure]-relationen med [!DNL Salesforce] finns i [den här artikeln](/help/configuration-and-setup/how-marketo-measure-and-salesforce-interact.md)
* Det krävs lite [!DNL Salesforce]-konfiguration. De specifika åtgärdsobjekten beskrivs nedan i [Steg 4 nedan](#salesforce-configuration)

## Steg 2: Ta bort den aktuella CRM-anslutningen för sandlådan i appen [!DNL Marketo Measure] {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Logga in på programmet [!DNL Marketo Measure] på experience.adobe.com/marketo-measure
* Navigera till Mitt konto >[!UICONTROL Settings] >[!UICONTROL Connections]
* Klicka på papperskorgsikonen bredvid din SFDC-anslutning för att ta bort
* Du uppmanas att bekräfta borttagningen. Var noga med att läsa igenom uppmaningen och förstå konsekvenserna av borttagningen

  ![Du uppmanas att bekräfta borttagningen. Läs över](assets/salesforce-migration-1.png)

   * Skriv namnet på företaget enligt bekräftelsemodellen och klicka på&quot;Jag förstår konsekvenserna, ta bort den här anslutningen&quot;
* Detta utlöser borttagningsprocessen och tar lite tid att slutföra

## Steg 3: Anslut Production CRM-instansen i appen [!DNL Marketo Measure] {#connect-the-production-crm-instance-in-marketo-measure-app}

* Logga in på programmet [!DNL Marketo Measure] på experience.adobe.com/marketo-measure
* Navigera till [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* När borttagningen av sandlådeanslutningen har tagits bort försvinner anslutningen från sidan. I annat fall visas anslutningen med statusen&quot;Pågående borttagning&quot;
* Klicka på [!UICONTROL Set up New CRM connection]
* Klicka på åtgärden [!UICONTROL Select CRM Connection] bredvid plattformen [!UICONTROL Connect] i den modala dialogrutan [!DNL Salesforce] och välj alternativet [!UICONTROL Production]
* Du uppmanas att ange dina inloggningsuppgifter. Se till att du anger inloggningsinformation för produktion

## Steg 4: Salesforce-konfiguration {#salesforce-configuration}

[Sidlayouter](/help/configuration-and-setup/page-layout-instructions.md)

[Behörighetsuppsättningar](/help/configuration-and-setup/marketo-measure-permission-sets.md)

[Dela rapporter](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0){target="_blank"}

[Dölja onödiga rapporttyper](/help/configuration-and-setup/hiding-unnecessary-report-types.md)

[Anpassat arbetsflöde om tillämpligt](/help/channel-tracking-and-setup/using-a-custom-revenue-amount-field.md)
