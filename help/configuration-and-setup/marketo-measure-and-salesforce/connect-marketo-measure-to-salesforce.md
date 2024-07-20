---
unique-page-id: 18874580
description: Anslut Marketo Measure till Salesforce - [!DNL Marketo Measure]
title: Anslut Marketo Measure till Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Anslut Marketo Measure till Salesforce {#connect-marketo-measure-to-salesforce}

Den här artikeln innehåller en översikt över hur du ansluter ditt [!DNL Salesforce]-konto till ditt [!DNL Marketo Measure]-konto.

## Ansluter [!DNL Marketo Measure] med [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Logga in på [!DNL Marketo Measure] med en inkognito-webbläsare.

1. Navigera till **[!UICONTROL My Account]** på menyraden högst upp på skärmen och klicka på alternativet **[!UICONTROL Settings]**.

1. Klicka på **[!UICONTROL Connections]** under avsnittet [!UICONTROL Integrations] i kolumnen med inställningsalternativ till vänster.

   ![](assets/connect-marketo-measure-to-salesforce-1.png)

1. Klicka på **[!UICONTROL Set Up New CRM Connection]** under CRM-avsnittet i Anslutningar.

   ![](assets/connect-marketo-measure-to-salesforce-2.png)

1. Ett popup-fönster visas där du uppmanas att välja CRM-anslutning. Klicka på **[!UICONTROL Connect]** bredvid logotypen [!DNL Salesforce].

   ![](assets/connect-marketo-measure-to-salesforce-3.png)

1. Ett slutligt popup-fönster visas där du ombeds ange dina [!DNL Salesforce]-autentiseringsuppgifter, din sandlåda eller din produktion. Ange din information och klicka på **[!UICONTROL Authorize]** för att ansluta kontot till [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] kan bara anslutas till en [!DNL Salesforce]-instans åt gången.
>
>* En [!DNL Marketo Measure]-instans kan anslutas till en SFDC-sandlådeinstans för att testa integreringen innan anslutningen till SFDC-produktionsinstansen växlas.
>* Om du först testar med en SFDC-sandlåda rekommenderar vi att du testar med en exakt kopia av din SFDC-produktionsinstans när det gäller fält på objekten Lead, Kontakt, Konto, säljprojekt, Campaign och Fall. Om du har aktiva APEX-utlösare i produktionen som aktiveras vid uppdateringar av objekten Lead, Kontakt, Konto, Möjlighet, Kampanj och Fall, bör du försöka att aktivera dem i sandlådan.
>* När du är klar med testningen uppdaterar du ditt [!DNL Marketo Measure]-konto så att det pekar på din produktion [!DNL Salesforce] (i stället för på sandlådan [!DNL Salesforce]). På grund av hur integreringen skapades kan du inte gå bakåt och ansluta till en sandlådeorganisation [!DNL Salesforce] när ett [!DNL Marketo Measure]-konto har anslutits till Production [!DNL Salesforce].

## API-kreditanvändning {#api-credits-usage}

Marketo Measure använder en CRM-integreringsuppgift för att interagera med en kunds Salesforce via en integrerad användare. Alla datautbyten via den här användaren använder Salesforce API-krediter. Du kan allokera en kreditkvot till en integreringsanvändare, som vill reglera för många API-anrop. Den här kvoten eller gränsen återställs var 24:e timme.

Du kan komma åt den här gränsen i Marketo Measure via: **Mitt konto** > **Inställningar** > **CRM** > **Allmänt** > **Daglig API-gräns för CRM** och kan konfigurera den för dina klientorganisationer.

![](assets/connect-marketo-measure-to-salesforce-4.png)

### Ange en gräns för API-krediter {#setting-a-limit-for-api-credits}

1. Navigera till **Mitt konto** > **Inställningar**.

1. Klicka på **Allmänt** under CRM. Alternativet **Daglig CRM API-gräns** visas.

1. Klicka på låsikonen för att redigera.

   ![](assets/connect-marketo-measure-to-salesforce-5.png)

1. Ange en gräns som är lika med eller större än 100 000. Klicka på **Spara** när du är klar.

   ![](assets/connect-marketo-measure-to-salesforce-6.png)

>[!NOTE]
>
>Om du vill öka tillgängliga Salesforce API-krediter för den anslutna lösningen kontaktar du Salesforce-administratören och refererar till [det här Salesforce-dokumentet](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.

>[!MORELIKETHIS]
>
>[Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
