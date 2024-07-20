---
unique-page-id: 18874749
description: Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Om du för närvarande använder [!DNL Uberflip] för att hantera ditt innehåll är det viktigt att du vidtar dessa nödvändiga åtgärder för att se till att [!DNL Marketo Measure] spårar dessa formulärinskickade data. Din Success Manager på [!DNL Uberflip] bör också kunna hjälpa dig med detta.

1. Lägg till det här skriptet i [!UICONTROL Custom Code>HTML] för [!DNL Uberflip].

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Kontrollera att den här [!DNL Marketo Measure]-preambelkoden utlöses både vid sidinläsning och AJAX sidändring. Gör detta i avsnittet [!UICONTROL Custom Code>JS]

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Lägg till den här ingressen till både [!DNL Hubs.onLoad] och [!DNL Hubs.onPageChange] AJAX JavaScript-händelseloggarna nedan. (Obs! Du kan även ha annan kod i de här händelseloggarna. Se till att du också tar med inledningen.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Skapa och definiera en funktion som överför data till Bizible när ett formulär-CTA skickas in. Detta går in i avsnittet [!UICONTROL Custom Code>JavaScript]. (Obs! Den här funktionen kräver bara att parametern ctaData har Uberflip, men du kan inkludera de andra parametrarna ctaId och ctaName om användaren vill anpassa sin kod för att skicka dessa data också).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. När ett CTA-formulär skickas in kontrollerar du att funktionen [!DNL Marketo Measure] körs enligt nedan. Detta görs i avsnittet [!UICONTROL Custom Code>JS]. (Obs! Du kan ha annan kod i händelsekroken Hubs.onCtaFormSubmitSuccess JavaScript, kontrollera att du även inkluderar det här funktionsanropet.)

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
