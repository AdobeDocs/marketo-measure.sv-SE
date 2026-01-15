---
description: Ansluta Marketo Measure till Salesforce för Marketo Measure
title: Anslut Marketo Measure till Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# Anslut Marketo Measure till Salesforce {#connect-marketo-measure-to-salesforce}

Den här artikeln innehåller en översikt över hur du ansluter ditt [!DNL Salesforce]-konto till ditt [!DNL Marketo Measure]-konto.

## Ansluter [!DNL Marketo Measure] med [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Logga in på [!DNL Marketo Measure] med en inkognito-webbläsare.

1. Navigera till **[!UICONTROL My Account]** på menyraden högst upp på skärmen och klicka på alternativet **[!UICONTROL Settings]**.

1. Klicka på **[!UICONTROL Connections]** under avsnittet [!UICONTROL Integrations] i kolumnen med inställningsalternativ till vänster.

   ![1. Klicka på ](assets/bizible-full-1.png) i kolumnen med inställningsalternativ till vänster

1. Klicka på **[!UICONTROL Set Up New CRM Connection]** under CRM-avsnittet i Anslutningar.

   ![1. Klicka på Konfigurera ny](assets/bizible-taxonomy-1.png) under CRM-avsnittet i Anslutningar

1. Ett popup-fönster visas där du uppmanas att välja CRM-anslutning. Klicka på **[!UICONTROL Connect]** bredvid logotypen [!DNL Salesforce].

   ![1. Ett popup-fönster visas där du uppmanas att välja CRM-anslutning. Klicka på](assets/connect-salesforce-1.png)

1. Ett slutligt popup-fönster visas där du ombeds ange dina [!DNL Salesforce]-autentiseringsuppgifter, din sandlåda eller din produktion. Ange din information och klicka på **[!UICONTROL Authorize]** för att ansluta kontot till [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] kan bara anslutas till en [!DNL Salesforce]-instans åt gången.
>
>* En [!DNL Marketo Measure]-instans kan anslutas till en SFDC Sandbox-instans för att testa integreringen innan anslutningen till din SFDC Production Instance växlas.
>* Om du först testar med en SFDC Sandbox rekommenderar vi att du testar med en exakt kopia av din SFDC-produktionsinstans i form av fält på objekten Lead, Kontakt, Konto, säljprojekt, Campaign och Case. Om du har aktiva APEX-utlösare i produktionen som aktiveras vid uppdateringar av objekten Lead, Kontakt, Konto, Möjlighet, Kampanj och Fall, bör du försöka att aktivera dem i sandlådan.
>* När du är klar med testningen uppdaterar du ditt [!DNL Marketo Measure]-konto så att det pekar på din produktion [!DNL Salesforce] (i stället för på sandlådan [!DNL Salesforce]). På grund av hur integreringen skapades kan du inte gå bakåt och ansluta till en sandlådeorganisation [!DNL Marketo Measure] när ett [!DNL Salesforce]-konto har anslutits till Production [!DNL Salesforce].

## API-kreditanvändning {#api-credits-usage}

Marketo Measure använder en CRM-integreringsuppgift för att interagera med klientens Salesforce via en integrerad användare. Alla datautbyten via den här användaren använder Salesforce API-krediter. Du kan allokera en kreditkvot till en integreringsanvändare, som vill reglera för många API-anrop. Den här kvoten eller gränsen återställs var 24:e timme.

Du kan komma åt den här gränsen i Marketo Measure via: **Mitt konto** > **Inställningar** > **CRM** > **Allmänt** > **Daglig API-gräns för CRM** och kan konfigurera den för dina klientorganisationer.

![Du kan komma åt den här gränsen i Marketo Measure via: Mina kontoinställningar](assets/connect-salesforce-2.png)

### Ange en gräns för API-krediter {#setting-a-limit-for-api-credits}

1. Navigera till **Mitt konto** > **Inställningar**.

1. Klicka på **Allmänt** under CRM. Alternativet **Daglig CRM API-gräns** visas.

1. Klicka på låsikonen för att redigera.

   ![1. Klicka på låsikonen för att redigera.](assets/connect-salesforce-3.png)

1. Ange en gräns som är lika med eller större än 100 000. Klicka på **Spara** när du är klar.

   ![1. Ange en gräns som är lika med eller större än 100 000. Klicka på](assets/connect-salesforce-1.png)

>[!NOTE]
>
>Om du vill öka antalet tillgängliga Salesforce API-krediter för den anslutna lösningen kontaktar du Salesforce-administratören och refererar till [det här Salesforce-dokumentet](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Felmeddelanden](/help/configuration-and-setup/error-notifications.md){target="_blank"}
