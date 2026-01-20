---
unique-page-id: 18874747
description: Lägger till [!DNL Marketo Measure] skript på Sitecore-sidor - [!DNL Marketo Measure]
title: Lägger till  [!DNL Marketo Measure] skript på webbplatsarkivsidor
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] skript på webbplatsens sidor {#adding-marketo-measure-script-to-sitecore-pages}

Innehållshanteringssystem kan kräva ytterligare steg utöver standardimplementering av skript för [!DNL Marketo Measure] för att identifiera formulärinskickade formulär. Processen nedan visar hur du lägger till [!DNL Marketo Measure] javascript på dina [!DNL Sitecore]-sidor.

För platser med Sitecore-sidor:

1. Logga in på Sitecore och navigera till din webbplats. Leta reda på mappen [!UICONTROL Configuration] som finns på samma nivå som mappen [!UICONTROL Home] item och [!UICONTROL Metadata].
1. Klicka på **[!UICONTROL +]** bredvid mappen [!UICONTROL Configuration].
1. Klicka på **[!UICONTROL +]** bredvid mappen [!UICONTROL Tools].
1. Markera objektet [!UICONTROL Javascript].
1. Klicka på länken [!UICONTROL Content] på fliken **[!UICONTROL Lock and Edit]** för att låsa upp objektet för redigering.
1. Hitta avsnittet [!UICONTROL 'JavaScript']. Om den inte redan är utökad klickar du på **[!UICONTROL +]**.
1. Ange vårt skript: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Klicka på **[!UICONTROL Save]** i det övre vänstra hörnet.
