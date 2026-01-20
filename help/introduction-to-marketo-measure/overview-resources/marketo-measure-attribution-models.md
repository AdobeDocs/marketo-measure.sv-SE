---
unique-page-id: 18874568
description: Marketo Measure attribueringsmodeller - Marketo Measure - produktdokumentation
title: Marketo Measure attribueringsmodeller
exl-id: d8f76f29-e7c9-4b2d-b599-e80fd93c4687
feature: Attribution
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# Marketo Measure attribueringsmodeller {#marketo-measure-attribution-models}

Marketo Measure erbjuder sex typer av attribueringsmodeller:

* Första beröring
* Skapa leads
* U-formad
* W-Shape
* Fullständig sökväg
* Anpassad modell

Dessa modeller varierar i komplexitet. Första beröringen och Lead-generering är enkla modeller med en knapptryckning. De återstående fyra är mer komplexa multitouch-modeller. Strukturen på Marketo Measure attribueringsmodeller återspeglar de fyra viktigaste kontaktytorna under kundresan:

* Första beröring (FT)
* Skapa leads (LC)
* Skapa affärsmöjlighet (OC)
* Closed-Won-avtal (CW)

![](assets/1-1.png)

I **single-touch-modellerna** tillskrivs attribueringskrediten bara en milstolpe-kontaktyta, vilket innebär namnet single-touch.
I **multi-touch-modellerna** tilldelas merparten av attribueringskrediten till två eller flera milstolpe-kontaktytor. Den återstående krediten tillskrivs kontaktytor som uppstår mellan milstolpepunkterna.

De följande avsnitten behandlar varje attribueringsmodell och hur attribueringskrediten tilldelas.

## Single-touch-modeller {#single-touch-models}

**Första pekmodellen**

Första beröringsmodellen fokuserar bara på den första interaktionen som en lead har med din organisation. Den här modellen attribuerar 100 % av attribueringskrediten till första gången leadet får kännedom om ditt företag, First Touch (FT).

Säg att Kate besöker `www.adobe.com` för första gången via en annons och tittar på ett whitepaper. Adwords-kanalen skulle få 100 % av attribueringskrediten från den affärsmöjligheten.

![](assets/2.png)

**Leadgenereringsmodell**

Leadgenereringsmodellen tilldelar 100 % av attribueringskrediten till LC-kontaktytan när en potentiell kund lämnar sin kontaktinformation och blir lead.

Efter Kate första besök på `www.adobe.com` via Adwords, kommer Austin att besöka webbplatsen via ett Linkedin-inlägg, vilket är en fortsättning från föregående exempel. Austin fyller i ett formulär och blir en lead. I den här modellen skulle Linkedin få 100 % av attribueringskrediten.

![](assets/3.png)

## Multi-touch-modeller {#multi-touch-models}

Multitouch-modeller används för längre och mer komplicerade säljcykler. Dessa modeller är särskilt användbara om flera personer från ett konto/företag är inblandade i köparens resa.

**U-formad modell**

U-Shaped-modellen fokuserar på både FT- och LC-kontaktytorna. I den här modellen får FT- och LC-kontaktytorna 50 % av intäktskrediten.

Kate första besök på `www.adobe.com` via en Adwords och skulle få 50 % av attribueringskrediten. De återstående 50 % skulle tillskrivas den Linkedin-post som drev Austin att fylla i ett formulär och bli en ledare.

![](assets/4.png)

**W-formad modell**

Tre av milstolpepunkterna ingår i W-Shaped-modellen. I den här modellen tillskrivs kontaktytorna FT, LC och OC 30 % av attribueringskrediten. De återstående 10 % fördelas proportionellt till eventuella mellanliggande kontaktytor som inträffar mellan de tre milstolppunkterna.

Kate och Austin talar om Marketo Measure för sin kollega Hillary. Hon hittar en del av innehållet genom en Google-sökning och fyller i ett formulär. Senare får Austin ett e-postmeddelande om registrering av ett webbinarium och fyller i registreringsformuläret på webbplatsen. Kate har en konversation med en säljare om Marketo Measure.

Hillary får ett mejl med en länk till prissidan och besöker sidan. Sedan skapas ett säljprojekt för deras konto. Hillary&#39;s web visit to the pricing page receive credit for the Opportunity Creation eftersom det var den närmsta marknadsföringsinteraktionen till datumet för att skapa säljprojekt. Var och en av milstolpepunkterna tilldelas 30 % av attribueringskrediten och de mellanliggande kontaktytorna tilldelas de återstående 10 %.

![](assets/5.png)

**Fullständig sökvägsmodell**

Den fullständiga banmodellen innehåller alla fyra milstolpepunkterna. FT, LC, OC och CW får var och en 22,5 % av intäktskrediten, och de återstående 10 % fördelas jämnt mellan de mellanliggande kontakterna.

Efter det att affärsmöjligheten har skapats bestämmer Kate, Austin och Hillary sig för att skicka Marketo Measure till sin marknadschef Elizabeth. Elizabeth deltar i en konferens där Marketo Measure är värd för ett evenemang. Kate ser en Linkedin-post om en fallstudie och fyller i ett formulär för att ladda ned innehållet. Elizabeth håller en säljmiddag hos Marketo Measure. Efter middagen bestämmer hon sig för att köpa Marketo Measure och blir kund. I det här scenariot skulle försäljningsmiddagen tillskrivas 22,5 % av intäktskrediten från den slutna affären. Kontaktpunkterna FT, LC och OC får också 22,5 % av krediten. De mellanliggande kontaktytorna tilldelas också de återstående 10 % av intäktskrediten.

![](assets/6.png)

**Anpassad attributmodell**

Marketo Measure erbjuder också en modell för anpassad attribuering som gör att användare kan välja vilka kontaktytor eller anpassade stadier som ska ingå i modellen. Dessutom kan användarna styra den procentandel av attribueringskrediten som tilldelats dessa kontaktytor och faser. Om ett säljprojekt inte har någon dedikerad medelstor beröring fördelas procentandelen jämnt mellan andra positioner.
