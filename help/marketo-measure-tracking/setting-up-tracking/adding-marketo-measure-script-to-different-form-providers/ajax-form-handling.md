---
unique-page-id: 18874745
description: AJAX-formulärhantering - [!DNL Marketo Measure]
title: AJAX Form Handling
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# AJAX Form Handling {#ajax-form-handling}

Om du vill rapportera kundkonverteringar till [!DNL Marketo Measure] manuellt finns det ett enkelt API som du kan använda. Båda dessa JavaScript-API:er är automatiskt tillgängliga på din webbplats om du har spårningskod på den. Du behöver inte göra något särskilt för att komma åt dem.

## Scenario 1 - HTML-formulär med en AJAX-sändning {#scenario-html-form-with-an-ajax-submit}

När [!DNL Marketo Measure] använder formulär som innehåller AJAX (eller någon annan mekanism) för att skicka konverteringsdatum från klienten till våra servrar kanske inte känner till kundkonverteringen via någon av de standardsökvägar som vi övervakar. I det här scenariot kan vi använda ett enkelt API (se nedan).

Om du hanterar dina egna inskickade formulär kan du anropa [!DNL Marketo Measure] explicit från JavaScript. [!DNL Marketo Measure] samlar in all relevant information från formuläret och skickar den asynkront till våra servrar.

**Nedan visas ett kodexempel med JQuery (förutsatt att ID:t i formuläret är &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the JQuery Selector for the form and we'll collect the data automatically.  
Bizible.Push('Form',$('#*formId*'));
```

**Nedan finns ett kodexempel som inte använder JQuery (förutsatt att ID:t i formuläret är &quot;formId&quot;):**

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// Give Marketo Measure the Form ID and we'll collect the data automatically.
Bizible.Push('Form','MyFormID');
```

## Scenario 2 - Leadinformation som samlats in i ett icke-HTML-formulär {#scenario-lead-information-collected-in-a-non-html-form}

Om information från ett konverterat lead samlas in med JavaScript eller enkla textfält utan HTML-formulär fungerar den här lösningen för dig. Delad nedan är det API som ska användas i det här scenariot:

```jquery
///////////////////////////////////////////////////////////////////////  
// Preamble for all API usage.  
window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };  
  
// If your site is using Ajax, or you are running a secure site, it is best to send us the data directly.  
Bizible.Push('User', {
eMail: 'user@gmail.com' // required  
});  
```

I den här koden krävs fältet [!UICONTROL email]. [!DNL Marketo Measure] skickar dessa data asynkront till våra servrar.

## Scenario 3 - Rapportera användarinformation från din tacksida {#scenario-report-user-information-from-the-thank-you-page}

Ibland är det bekvämare att rapportera leadinformationen till [!DNL Marketo Measure] från din tacksida efter att formuläret har skickats. Det enklaste sättet att rapportera den här informationen är att lägga till ett dolt element på sidan som innehåller information från formuläröverföringen, och [!DNL Bizible.js] läser informationen när sidan Tack har lästs in.

**Till exempel:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Det spelar ingen roll om det dolda elementet är en div, ett skript eller någon annan taggtyp. [!DNL Marketo Measure] söker efter id=&quot;bizible.reportUser&quot; för att läsa informationen.
