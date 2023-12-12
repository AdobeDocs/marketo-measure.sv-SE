---
unique-page-id: 18874694
description: Salesforce Sandbox till produktionsmigrering - [!DNL Marketo Measure] - Produktdokumentation
title: Salesforce-sandlåda till produktionsmigrering
exl-id: b2b71c4a-f192-43ce-a27e-cbd0ec3cf008
feature: Salesforce
source-git-commit: ad658a513b01dc7a51299abcb7313ff1877e49f3
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Salesforce-sandlåda till produktionsmigrering {#salesforce-sandbox-to-production-migration}

Om du valde att testa [!DNL Marketo Measure] i en [!DNL Salesforce] I sandlådemiljö följer du dessa anvisningar för att migrera till Production när du är klar. Följande instruktioner förutsätter att du redan har hämtat [!DNL Marketo Measure] paketera i din sandlådeorganisation, utföra nödvändiga tester och är redo att skickas [!DNL Marketo Measure] till produktion.

## Steg 1: Installera [!DNL Marketo Measure] Packa in i produktionen [!DNL Salesforce] Instance

* Installera [!DNL Marketo Measure] paketet i produktionen med &quot;[!UICONTROL All Users]&quot; inställning

   * [Baskaket](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"}

* Mer information om [!DNL Marketo Measure] relation med [!DNL Salesforce], titta på [den här artikeln](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md)
* Lite av [!DNL Salesforce] måste konfigureras. De specifika åtgärdsobjekten beskrivs nedan [Steg 4 nedan](#salesforce-configuration)

## Steg 2: Ta bort den aktuella CRM-anslutningen för sandlådan i [!DNL Marketo Measure] App {#delete-the-current-sandbox-crm-connection-in-marketo-measure-app}

* Logga in på [!DNL Marketo Measure] program på experience.adobe.com/marketo-measure
* Navigera till Mitt konto >[!UICONTROL Settings] >[!UICONTROL Connections]
* Klicka på papperskorgsikonen bredvid SFDC-anslutningen för att ta bort
* Du uppmanas att bekräfta borttagningen. Var noga med att läsa igenom uppmaningen och förstå konsekvenserna av borttagningen

  ![](assets/salesforce-sandbox-to-production-migration-1.png)

   * Skriv namnet på företaget enligt bekräftelsemodellen och klicka på&quot;Jag förstår konsekvenserna, ta bort den här anslutningen&quot;
* Detta kommer att starta borttagningsprocessen och ta lite tid att slutföra

## Steg 3: Anslut Production CRM-instansen i [!DNL Marketo Measure] App {#connect-the-production-crm-instance-in-marketo-measure-app}

* Logga in på [!DNL Marketo Measure] program på experience.adobe.com/marketo-measure
* Navigera till [!UICONTROL My Account] >[!UICONTROL Settings] > [!UICONTROL Connections]
* När borttagningen av sandlådeanslutningen har tagits bort försvinner anslutningen från sidan. I annat fall visas anslutningen med statusen &quot;Borttagning pågår&quot;
* Klicka på &quot;[!UICONTROL Set up New CRM connection]&quot;
* I dialogrutan[!UICONTROL Select CRM Connection]&quot; modal dialog, click the &quot;[!UICONTROL Connect]&quot; Åtgärd bredvid [!DNL Salesforce] Plattform, välj[!UICONTROL Production]&quot;, alternativ
* Du uppmanas att ange dina inloggningsuppgifter. Se till att du anger inloggningsinformation för produktion

## Steg 4: Salesforce-konfiguration {#salesforce-configuration}

[Sidlayouter](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md)

[Behörighetsuppsättningar](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)

[Dela rapporter](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0){target="_blank"}

[Dölja onödiga rapporttyper](/help/configuration-and-setup/marketo-measure-and-salesforce/hiding-unnecessary-report-types.md)

[Anpassat arbetsflöde om tillämpligt](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
