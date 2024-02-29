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

[!DNL Marketo Measure] integreras direkt med Unbounce så att ni kan spåra den digitala marknadsföringskällan för era landningssidkonverteringar direkt i [!DNL Salesforce]. Om du vill ansluta lägger du bara till [!DNL Marketo Measure] till Unbounce Script Manager. Så här gör du.

1. Logga in på [!DNL Unbounce] konto.
1. Klicka på **[!UICONTROL Settings]** > **[!UICONTROL Script Manager]** > **[!UICONTROL Add Script]**.
1. I popup-fönstret väljer du [!UICONTROL Custom Script] och ge den namnet &quot;[!DNL Marketo Measure Marketing Analytics].&quot; Klicka på **[!UICONTROL Add Script Details]**.
1. Välj placering i huvudet. Inkludera skriptet på Main Landing Page och formulärbekräftelsedialogrutan. Klistra in [!DNL Marketo Measure] skript nedanför i lådan.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Klicka på **[!UICONTROL Save]**.

The [!DNL Marketo Measure] integreringen fungerar på Unbounce-landningssidor så länge de finns på din domän (t.ex. landing.mysite.com), inte på dem som använder unbounce.com.
