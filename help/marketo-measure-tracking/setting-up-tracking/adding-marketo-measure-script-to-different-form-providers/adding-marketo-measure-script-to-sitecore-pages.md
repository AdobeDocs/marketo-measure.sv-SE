---
unique-page-id: 18874747
description: Lägger till [!DNL Marketo Measure] Skript till Sitecore-sidor - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] Skript till Sitecore-sidor
exl-id: 87ce1857-7532-45a7-8c39-255c6118b50a
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] Skript till Sitecore-sidor {#adding-marketo-measure-script-to-sitecore-pages}

Innehållshanteringssystem kan kräva ytterligare steg utöver standardimplementering av skript för [!DNL Marketo Measure] för att ta hänsyn till inskickade formulär. Processen nedan visar hur du lägger till [!DNL Marketo Measure] javascript till [!DNL Sitecore] sidor.

För platser med Sitecore-sidor:

1. Logga in på Sitecore och navigera till din webbplats. Leta reda på [!UICONTROL Configuration] mapp som finns på samma nivå som [!UICONTROL Home] objekt och [!UICONTROL Metadata] mapp.
1. Klicka på **[!UICONTROL +]** bredvid [!UICONTROL Configuration] mapp.
1. Klicka på **[!UICONTROL +]** bredvid [!UICONTROL Tools] mapp.
1. Välj [!UICONTROL Javascript] objekt.
1. I [!UICONTROL Content] klickar du på **[!UICONTROL Lock and Edit]** för att låsa upp objektet för redigering.
1. Hitta [!UICONTROL 'JavaScript'] -avsnitt. Om den inte redan är utökad klickar du på **[!UICONTROL +]**.
1. Ange vårt skript: `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js"async=""></script>`
1. Klicka **[!UICONTROL Save]** i det övre vänstra hörnet.
