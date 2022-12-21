---
unique-page-id: 18874757
description: Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot] - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] JavaScript till [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] formulär kräver ytterligare hantering i formulärmallen utöver att skriptet placeras på webbplatsen för att [!DNL Marketo Measure] för att ta hänsyn till inskickade formulär. Processen är enkel; kräver bara att [!DNL Marketo Measure] spåra skript i [!DNL Pardot] formulärmall.

## Steg för steg-instruktioner {#step-by-step-instructions}

När du har loggat in på [!DNL Pardot] gör du så här:

1. Navigera till **[!UICONTROL Marketing]**.

1. Klicka på **[!UICONTROL Landing Pages]**.

1. Välj **[!UICONTROL Layout Template]**.

   ![](assets/1-3.png)

1. Bestäm lämplig layoutmall och klicka på **[!UICONTROL Edit]** till höger.

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

_Och_ själva IFrame finns på en säker sida (HTTPS) i stället för en osäker sida (HTTP) när vi försöker läsa in skriptet på [!DNL Pardot] IFrame, webbläsaren kommer att försöka läsa in en HTTP-version av skriptet på en HTTPS-sida som kommer att misslyckas och förhindra oss från att spåra. Lösningen är att uppdatera skriptet på [!DNL Pardot] IFrame för att läsa in den säkra versionen av vårt skript:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Det kan också finnas andra kodfragment för spårning i det här området, till exempel en [!DNL Google Analytics] kod. Var noga med att separera dem med ett semikolon `;` och ett enda blanksteg, som i det här exemplet:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
