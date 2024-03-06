---
unique-page-id: 18874745
description: AJAX - [!DNL Marketo Measure]
title: AJAX formulärhantering
exl-id: 042e42ff-d8d9-4380-b878-aba4934bc4a0
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# AJAX formulärhantering {#ajax-form-handling}

Rapportera kundkonverteringar manuellt till [!DNL Marketo Measure], finns det ett enkelt API som du kan använda. Båda dessa JavaScript-API:er är automatiskt tillgängliga på din webbplats om du har spårningskod på den. Du behöver inte göra något särskilt för att komma åt dem.

## Scenario 1 - HTML-formulär med AJAX {#scenario-html-form-with-an-ajax-submit}

När du använder formulär som innehåller AJAX (eller någon annan mekanism) för att skicka konverteringsdatum från klienten till våra servrar, [!DNL Marketo Measure] kanske inte känner till kundkonverteringen via någon av de standardvägar som vi övervakar. I det här scenariot kan vi använda ett enkelt API (se nedan).

Om du hanterar dina egna inskickade formulär kan du anropa [!DNL Marketo Measure] från JavaScript. [!DNL Marketo Measure] Samlar in all relevant information från formuläret och skickar den asynkront till våra servrar.

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

## Scenario 2 - Leadinformation som samlats in i en annan form än HTML {#scenario-lead-information-collected-in-a-non-html-form}

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

I koden [!UICONTROL email] fältet är obligatoriskt. [!DNL Marketo Measure] skickar dessa data asynkront till våra servrar.

## Scenario 3 - Rapportera användarinformation från din tacksida {#scenario-report-user-information-from-the-thank-you-page}

Ibland är det bekvämare att rapportera leadinformationen till [!DNL Marketo Measure] på tacksidan när formuläret har skickats in. Det enklaste sättet att rapportera den här informationen är att lägga till ett dolt element på sidan som innehåller information från formulärinlämningen, och [!DNL Bizible.js] kommer att läsa informationen när sidan&quot;Tack&quot; har lästs in.

**Till exempel:**

```html
<div id="bizible.reportUser" style="display:none"  
data-email="user@gmail.com">  
```

Det spelar ingen roll om det dolda elementet är en div, ett skript eller någon annan taggtyp. [!DNL Marketo Measure] söker efter id=&quot;bizible.reportUser&quot; för att läsa informationen.
