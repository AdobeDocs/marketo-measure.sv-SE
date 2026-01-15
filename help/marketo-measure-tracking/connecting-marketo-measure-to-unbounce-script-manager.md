---
description: Ansluta [!DNL Marketo Measure] till Unbounce Script Manager-vägledning för Marketo Measure-användare
title: Ansluter [!DNL Marketo Measure] till Unbounce Script Manager
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 2%

---


# Ansluter [!DNL Marketo Measure] till Unbounce Script Manager {#connecting-marketo-measure-to-unbounce-script-manager}

[!DNL Marketo Measure] integreras direkt med Unbounce, vilket gör att du kan spåra den digitala marknadsföringskällan för dina konverteringar på landningssidan direkt i [!DNL Salesforce]. Om du vill ansluta lägger du bara till skriptet [!DNL Marketo Measure] i Unbounce Script Manager. Så här gör du.

1. Logga in på ditt [!DNL Unbounce]-konto.
1. Klicka på **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. Välj [!UICONTROL Custom Script] på popup-menyn och ge den namnet [!DNL Marketo Measure Marketing Analytics]. Klicka på **[!UICONTROL Add Script Details]**.
1. Välj placering i huvudet. Inkludera skriptet på Main Landing Page och formulärbekräftelsedialogrutan. Klistra in skriptet [!DNL Marketo Measure] nedan i rutan.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Klicka på **[!UICONTROL Save]**.

Integreringen av [!DNL Marketo Measure] fungerar på Unbounce-landningssidor så länge som de finns på din domän (t.ex. landing.mysite.com), inte på dem som använder unbounce.com.
