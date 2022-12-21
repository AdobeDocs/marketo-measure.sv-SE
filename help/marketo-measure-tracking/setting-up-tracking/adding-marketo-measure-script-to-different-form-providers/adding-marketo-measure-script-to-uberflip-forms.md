---
unique-page-id: 18874749
description: Lägger till [!DNL Marketo Measure] Skript till [!DNL Uberflip] Forms - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] Skript till [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] Skript till [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Om du använder [!DNL Uberflip] om du vill hantera ditt innehåll är det viktigt att du vidtar dessa nödvändiga åtgärder för att se till att [!DNL Marketo Measure] spårar de formulärinskickade data. Din Success Manager på [!DNL Uberflip] kan också hjälpa dig med detta.

1. Lägg till det här skriptet i [!DNL Uberflip]&#39;s [!UICONTROL Custom Code>HTML] -avsnitt.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Se till att [!DNL Marketo Measure] Inledande kod aktiveras både vid sidinläsning och AJAX sidändring. Gör detta i [!UICONTROL Custom Code>JS] section

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Du ska lägga till den här ingressen i båda [!DNL Hubs.onLoad] och [!DNL Hubs.onPageChange] AJAX Javascript-händelsekopplingar enligt nedan. (Obs! Du kan även ha andra koder i de här händelseloggarna. Se bara till att du tar med inledningen också.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Skapa och definiera en funktion som skickar data till Bizible när ett formulär-CTA skickas. Det här går in i [!UICONTROL Custom Code>Javascript] -avsnitt. (Obs! den här funktionen kräver bara parametern ctaData som Uberflip tillhandahåller, men du kan inkludera de andra parametrarna ctaId och ctaName om användaren vill anpassa sin kod för att skicka dessa data också).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. När ett CTA-formulär skickas in ska du [!DNL Marketo Measure] funktionen utförs enligt nedan. Detta görs i [!UICONTROL Custom Code>JS] -avsnitt. (Obs! Du kan ha annan kod i händelsekroken Hubs.onCtaFormSubmitSuccess javascript (kontrollera att du även inkluderar det här funktionsanropet).

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
