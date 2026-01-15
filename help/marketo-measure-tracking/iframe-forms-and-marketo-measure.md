---
description: IFrame Forms och [!DNL Marketo Measure] riktlinjer för Marketo Measure-användare
title: IFrame Forms och [!DNL Marketo Measure]
exl-id: fe8d7403-27be-4702-a1b6-d574e1243c0a
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# IFrame Forms och [!DNL Marketo Measure] {#iframe-forms-and-marketo-measure}

Med [!DNL Marketo Measure] är en av de viktigaste funktionerna att spåra era digitala marknadsföringssatsningar genom sessioner på er webbplats och inskickade formulär. När Marketo JavaScript läggs ut på webbplatsen kopplas vi vanligtvis automatiskt till alla formulär på webbplatsen. Den här funktionaliteten är dock begränsad om formuläret finns i en IFrame.

Tänk på en IFrame som en sida på en sida, så precis som vi begär att skriptet läggs till på alla sidor på din webbplats, behöver vi skriptet som placerats i IFrame för att vara säkra på att vi spårar.

I många fall ser vi att IFrame hanteras av en leverantör av marknadsföringsautomatisering så att du måste konfigurera detta inom den plattformen eller via din formulärleverantör.

Vi rekommenderar att du placerar JavaScript i huvudet på IFrame och därifrån bifogar vi automatiskt formulären inom ramen.

![Vi rekommenderar att du placerar JavaScript i huvudet på ](assets/adding-pages-1.png)

Om du har några frågor om hur du lägger till JavaScript i IFrame-formulär kan du kontakta Adobe Account Team (din kontohanterare) eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
