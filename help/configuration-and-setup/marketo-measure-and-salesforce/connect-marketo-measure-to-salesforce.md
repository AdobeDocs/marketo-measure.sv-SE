---
unique-page-id: 18874580
description: Anslut Marketo Measure till Salesforce - [!DNL Marketo Measure] - Produktdokumentation
title: Anslut Marketo Measure till Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
feature: Salesforce
source-git-commit: 5b1511395aff958f20f74c8a52c2701c4a64329d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Anslut Marketo Measure till Salesforce {#connect-marketo-measure-to-salesforce}

I den här artikeln finns en översikt över hur du ansluter [!DNL Salesforce] kontot till [!DNL Marketo Measure] konto.

## Ansluter [!DNL Marketo Measure] med [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Logga in i en inkognitiv webbläsare [!DNL Marketo Measure].

1. Navigera i menyraden högst upp på skärmen till **[!UICONTROL My Account]** och klicka på **[!UICONTROL Settings]** alternativ.

1. I kolumnen med alternativ till vänster klickar du på **[!UICONTROL Connections]** som finns under [!UICONTROL Integrations] -avsnitt.

   ![](assets/connect-marketo-measure-to-salesforce-1.png)

1. Klicka på under CRM i Anslutningar **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/connect-marketo-measure-to-salesforce-2.png)

1. Ett popup-fönster visas där du uppmanas att välja CRM-anslutning. Klicka på **[!UICONTROL Connect]** knappen bredvid [!DNL Salesforce] logotyp.

   ![](assets/connect-marketo-measure-to-salesforce-3.png)

1. Ett sista popup-fönster visas där du ombeds ange [!DNL Salesforce] autentiseringsuppgifter, sandlåda eller produktion. Ange dina uppgifter och klicka på **[!UICONTROL Authorize]** för att ansluta kontot till [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] kan bara anslutas till en [!DNL Salesforce] -instans i taget.
>
>* A [!DNL Marketo Measure] -instansen kan anslutas till en SFDC-sandlådeinstans för att testa integreringen innan anslutningen till SFDC-produktionsinstansen växlas.
>* Om du först testar med en SFDC-sandlåda rekommenderar vi att du testar med en exakt kopia av din SFDC-produktionsinstans när det gäller fält på objekten Lead, Kontakt, Konto, säljprojekt, Campaign och Fall. Om du har aktiva APEX-utlösare i produktionen som aktiveras vid uppdateringar av objekten Lead, Kontakt, Konto, Möjlighet, Kampanj och Fall, bör du försöka att aktivera dem i sandlådan.
>* När du är klar med testningen uppdaterar du [!DNL Marketo Measure] konto till produktionspunkten [!DNL Salesforce] (i stället för Sandbox [!DNL Salesforce]). På grund av hur integreringen byggdes har en gång per [!DNL Marketo Measure] kontot är anslutet till produktionen [!DNL Salesforce]går det inte att gå bakåt och ansluta till en sandlåda [!DNL Salesforce] org.

## API-kreditanvändning {#api-credits-usage}

Marketo Measure använder en CRM-integreringsuppgift för att interagera med en kunds Salesforce via en integrerad användare. Alla datautbyten via den här användaren använder Salesforce API-krediter. Du kan allokera en kreditkvot till en integreringsanvändare, som vill reglera för många API-anrop. Den här kvoten eller gränsen återställs var 24:e timme.

Du kan nå den här gränsen i Marketo Measure via: **Mitt konto** > **Inställningar** > **CRM** > **Allmänt** > **Gräns för CRM-API per dag** och kan konfigurera det för dina klientorganisationer.

![](assets/connect-marketo-measure-to-salesforce-4.png)

### Ange en gräns för API-krediter {#setting-a-limit-for-api-credits}

1. Navigera till **Mitt konto** > **Inställningar**.

1. Klicka på under CRM **Allmänt**. Du kommer att se **Gräns för CRM-API per dag** alternativ.

1. Klicka på låsikonen för att redigera.

   ![](assets/connect-marketo-measure-to-salesforce-5.png)

1. Ange en gräns som är lika med eller större än 100 000. Klicka **Spara** när det är klart.

   ![](assets/connect-marketo-measure-to-salesforce-6.png)

>[!NOTE]
>
>Om du vill öka tillgängliga Salesforce API-krediter för den anslutna lösningen kontaktar du Salesforce-administratören och referensen [det här Salesforce-dokumentet](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target="_blank"}.
