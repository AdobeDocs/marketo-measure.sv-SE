---
unique-page-id: 18874743
description: Ansluter [!DNL Marketo Measure] till Unbounce Script Manager - [!DNL Marketo Measure]
title: Ansluter [!DNL Marketo Measure] till Unbounce Script Manager
exl-id: c3212bc3-1d8f-4da5-bb2d-11ffd2fb4e98
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '111'
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
