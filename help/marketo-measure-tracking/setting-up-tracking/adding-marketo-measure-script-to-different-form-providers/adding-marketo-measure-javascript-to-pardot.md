---
unique-page-id: 18874757
description: Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot] - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] formulär kräver ytterligare hantering i formulärmallen utöver att skriptet placeras på webbplatsen för [!DNL Marketo Measure] för att ta hänsyn till inskickade formulär. Processen är enkel, den kräver bara att du placerar [!DNL Marketo Measure] spåra skript i [!DNL Pardot] formulärmall.

## Stegvisa instruktioner {#step-by-step-instructions}

När du har loggat in på [!DNL Pardot] gör du så här:

1. Navigera till **[!UICONTROL Marketing]**.

1. Klicka på **[!UICONTROL Landing Pages]**.

1. Välj **[!UICONTROL Layout Template]**.

   ![](assets/1-3.png)

1. Bestäm lämplig layoutmall och klicka **[!UICONTROL Edit]** till höger.

   ![](assets/2-1.png)

1. Kopiera och klistra in [!DNL Marketo Measure] JavaScript-kod precis före den avslutande rubriktaggen på HTML-sidan.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Följ de här stegen för alla tillämpliga layoutmallar för landningssidor.

1. Se till att [!DNL Marketo Measure] JavaScript finns också på den allmänna webbplatssidan.

   I [!DNL Pardot] Layoutmall ser koden ut ungefär så här:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Ytterligare information {#additional-notes}

Om [!DNL Pardot] IFrame har följande HTML-tagg:

`<base href="http://go.pardot.com">`

_Och_ själva IFrame är en säker sida (HTTPS) i stället för osäker (HTTP) när skriptet läses in i [!DNL Pardot] IFrame, försöker webbläsaren läsa in en HTTP-version av skriptet på en HTTPS-sida som kommer att misslyckas, vilket bryter spårningen. Lösningen är att uppdatera skriptet på [!DNL Pardot] IFrame som läser in den säkra versionen av skriptet:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Det kan redan finnas andra kodfragment för spårning i det här området, som [!DNL Google Analytics] kod. Var noga med att separera dem med ett semikolon `;` och ett enda blanksteg, som i det här exemplet:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
