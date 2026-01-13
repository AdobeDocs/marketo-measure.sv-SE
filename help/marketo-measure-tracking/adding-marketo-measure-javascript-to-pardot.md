---
description: Lägger till [!DNL Marketo Measure] JavaScript i [!DNL Pardot] - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] JavaScript i [!DNL Pardot]
exl-id: e49190ad-aa86-4f8f-a9ed-48de9e937a7e
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 1%

---


# Lägger till [!DNL Marketo Measure] JavaScript i [!DNL Pardot] {#adding-marketo-measure-javascript-to-pardot}

[!DNL Pardot] formulär kräver ytterligare hantering i formulärmallen utöver att skriptet placeras på webbplatsen för att [!DNL Marketo Measure] ska känna igen formuläröverföringar. Processen är enkel. Den kräver bara att [!DNL Marketo Measure]-spårningsskriptet placeras i formulärmallen [!DNL Pardot].

## Stegvisa instruktioner {#step-by-step-instructions}

När du har loggat in på ditt [!DNL Pardot]-konto följer du stegen nedan.

1. Navigera till **[!UICONTROL Marketing]**.

1. Klicka på **[!UICONTROL Landing Pages]**.

1. Välj **[!UICONTROL Layout Template]**.

   ![ 3](assets/1-3.png)

1. Kontrollera lämplig layoutmall och klicka på **[!UICONTROL Edit]** till höger.

   ![ 1](assets/2-1.png)

1. Kopiera och klistra in JavaScript-koden [!DNL Marketo Measure] precis före den avslutande rubriktaggen på din HTML-sida.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Följ de här stegen för alla tillämpliga layoutmallar för landningssidor.

1. Se även till att JavaScript [!DNL Marketo Measure] finns på den allmänna webbplatssidan.

   I layoutmallen [!DNL Pardot] ser koden ut ungefär så här:

```text
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>
   </head>
   <body>
```

## Ytterligare information {#additional-notes}

Om IFrame [!DNL Pardot] har följande HTML-tagg:

`<base href="http://go.pardot.com">`

_Och_ IFrame är i själva verket en säker sida (HTTPS) i stället för osäker (HTTP). När skriptet läses in i [!DNL Pardot] IFrame försöker webbläsaren läsa in en HTTP-version av skriptet på en HTTPS-sida som kommer att misslyckas och spårningen bryts. Lösningen är att uppdatera skriptet på IFrame [!DNL Pardot] för att läsa in den säkra versionen av skriptet:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Det kan redan finnas andra spårningskod i det här området, till exempel en [!DNL Google Analytics]-kod. Se till att separera dem med ett semikolon `;` och ett enda mellanslag, som i det här exemplet:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="othercode_example" src="otherfile_example.js" ></script>`
