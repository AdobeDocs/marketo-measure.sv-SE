---
unique-page-id: 18874741
description: IFrame Forms och [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: IFrame Forms och [!DNL Marketo Measure]
exl-id: fe8d7403-27be-4702-a1b6-d574e1243c0a
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# IFrame Forms och [!DNL Marketo Measure] {#iframe-forms-and-marketo-measure}

Med [!DNL Marketo Measure] en av de viktigaste funktionerna är att följa upp era digitala marknadsföringssatsningar genom sessioner på er webbplats och inskickade formulär. När Marketo JavaScript placeras på webbplatsen kopplas vi vanligtvis automatiskt till alla formulär på webbplatsen. Den här funktionaliteten är dock begränsad om formuläret finns i en IFrame.

Tänk på en IFrame som en sida på en sida, så precis som vi begär att skriptet läggs till på alla sidor på din webbplats, behöver vi skriptet som placerats i IFrame för att vara säkra på att vi spårar.

I många fall ser vi att IFrame hanteras av en leverantör av marknadsföringsautomatisering så att du måste konfigurera detta inom den plattformen eller via din formulärleverantör.

Vi rekommenderar att du placerar JavaScript i huvudet på IFrame och därifrån kopplas vi automatiskt till formulären i den ramen.

![](assets/1-1.png)

Om du har några frågor om hur du lägger till JavaScript i IFrame-formulär kan du kontakta kontoteamet (din Account Manager) på Adobe eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
