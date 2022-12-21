---
unique-page-id: 18874580
description: Koppla Marketo-mått till Salesforce - [!DNL Marketo Measure] - Produktdokumentation
title: Koppla Marketo-mått till Salesforce
exl-id: 9be8d3fa-1045-4e41-bc2e-5b9d4d3513ae
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# Koppla Marketo-mått till Salesforce {#connect-marketo-measure-to-salesforce}

Den här artikeln innehåller en översikt över hur du ansluter [!DNL Salesforce] kontot till [!DNL Marketo Measure] konto.

## Ansluter [!DNL Marketo Measure] med [!DNL Salesforce] {#connecting-marketo-measure-with-salesforce}

1. Logga in i en inkognitiv webbläsare [!DNL Marketo Measure].

1. Navigera i menyraden högst upp på skärmen till **[!UICONTROL My Account]** och klicka på [!UICONTROL Settings] alternativ.

1. I kolumnen med alternativ till vänster klickar du på [!UICONTROL Connections] som finns under [!UICONTROL Integrations] -avsnitt.

   ![](assets/1.png)

1. Klicka på under CRM i Anslutningar **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/2.png)

1. Ett popup-fönster visas där du uppmanas att välja CRM-anslutning. Klicka på [!UICONTROL Connect] knappen bredvid [!DNL Salesforce] logotyp.

   ![](assets/3.png)

1. Ett sista popup-fönster visas där du ombeds [!DNL Salesforce] autentiseringsuppgifter, sandlåda eller produktion. Ange dina uppgifter och klicka på **[!UICONTROL Authorize]** för att ansluta kontot till [!DNL Marketo Measure].

>[!NOTE]
>
>[!DNL Marketo Measure] kan bara anslutas till en [!DNL Salesforce] -instans i taget.
>
>* A [!DNL Marketo Measure] -instansen kan anslutas till en SFDC-sandlådeinstans för att testa integreringen innan anslutningen till SFDC-produktionsinstansen växlas.
>* Om du först testar med en SFDC-sandlåda rekommenderar vi att du testar med en exakt kopia av din SFDC-produktionsinstans när det gäller fält på objekten Lead, Kontakt, Konto, säljprojekt, Campaign och Fall. Om du har aktiva APEX-utlösare i produktionen som aktiveras vid uppdateringar av objekten Lead, Kontakt, Konto, Möjlighet, Kampanj och Fall, bör du försöka att aktivera dem i sandlådan.
>* När du är klar med testningen uppdaterar du [!DNL Marketo Measure] konto till produktionspunkten [!DNL Salesforce] (i stället för Sandbox [!DNL Salesforce]). På grund av hur integreringen byggdes har en gång per [!DNL Marketo Measure] kontot är anslutet till produktionen [!DNL Salesforce]går det inte att gå bakåt och ansluta till en sandlåda [!DNL Salesforce] org.


