---
description: Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms-vägledning för Marketo Measure-användare
title: Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms
exl-id: fb123e15-523d-4931-b4c1-705fe49be3d0
feature: Tracking
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] skript i [!DNL Uberflip] Forms {#adding-marketo-measure-script-to-uberflip-forms}

Om du för närvarande använder [!DNL Uberflip] för att hantera ditt innehåll är det viktigt att du vidtar dessa nödvändiga åtgärder för att se till att [!DNL Marketo Measure] spårar dessa formulärinskickade data. Din Success Manager på [!DNL Uberflip] bör också kunna hjälpa dig med detta.

1. Lägg till det här skriptet i [!DNL Uberflip] för [!UICONTROL Custom Code>HTML].

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Se till att den här [!DNL Marketo Measure]-prefixkoden aktiveras både vid sidinläsning och vid sidändring i AJAX. Gör detta i avsnittet [!UICONTROL Custom Code>JS]

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   Lägg till den här ingressen i både [!DNL Hubs.onLoad]- och [!DNL Hubs.onPageChange] AJAX JavaScript-händelseloggarna nedan. (Obs! Du kan även ha annan kod i de här händelseloggarna. Se till att du också tar med inledningen.)

   `Hubs.onLoad = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

   `Hubs.onPageChange = function () {`

   `window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`

   `}`

1. Skapa och definiera en funktion som överför data till Bizible när ett formulär-CTA skickas. Detta går in i avsnittet [!UICONTROL Custom Code>JavaScript]. (Obs! Den här funktionen kräver bara att parametern ctaData har Uberflip, men du kan inkludera de andra parametrarna ctaId och ctaName om användaren vill anpassa sin kod för att skicka dessa data också).

   `function bizibleFormCode(ctaId, ctaData, ctaName) {`
   `var email = ctaData["email"];`
   `if(email){`
   `Bizible.Push('User', {`
   `eMail: email, // required`
   `}); }`

   `}`

1. När ett formulär-CTA skickas in kontrollerar du att din [!DNL Marketo Measure]-funktion körs enligt nedan. Detta görs i avsnittet [!UICONTROL Custom Code>JS]. (Obs! Du kan ha annan kod i händelsekroken Hubs.onCtaFormSubmitSuccess JavaScript, kontrollera att du även inkluderar det här funktionsanropet.)

   `Hubs.onCtaFormSubmitSuccess = function (ctaId, ctaData, ctaName) {`
   `bizibleFormCode(ctaId, ctaData, ctaName);`\
   `}`
