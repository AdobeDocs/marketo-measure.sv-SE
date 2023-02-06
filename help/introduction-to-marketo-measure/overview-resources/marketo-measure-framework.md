---
unique-page-id: 18874570
description: Marketo Measure Framework - Marketo Measure - Produktdokumentation
title: Marketo Measure Framework
exl-id: fa6de27c-cdd2-4fd9-ac35-7286fe2752d8
source-git-commit: 7eb5ef616e3ae77d53056496f9a1b301ce59d6ee
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# Marketo Measure Framework {#marketo-measure-framework}

Läs mer om de fyra huvudkomponenterna i Marketo Measure-ramverket. Marketo Measure förlitar sig på dessa applikationer för att spåra, organisera och lagra data samt för att tillhandahålla rapporteringsfunktioner. De fyra komponenterna som utgör Marketo Measure ramverk är:

* Marketo Measure JavaScript
* CRM-integreringar
* Tredjepartsprogram/-system
* Marketo Measure

## Marketo Measure JavaScript {#marketo-measure-javascript}

Marketo Measure JavaScript spårar alla de interaktioner för onlinemarknadsföring, som även kallas kontaktytor, som potentiella kunder/leads har med organisationen. Det är ett anpassat skript som läggs till före stängningen `</head>` på alla sidor på webbplatsen.

`<script type="text/javascript" src="//[cdn.bizible.com/scripts/bizible.js](http://cdn.bizible.com/scripts/bizible.js)" async=""></script>`

>[!NOTE]
>
>Instruktioner om hur du lägger till Marketo Measure JS finns i [klicka här](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md).

Marketo Measure JS hämtar in data från webbbesök (inklusive anonyma webbbesök), allmän trafik-/sidnavigering, nedladdning av innehåll och inskickade formulär. Dessa data läggs in i CRM och varje marknadsföringsinteraktion visas som en kontaktyta.

## CRM-integreringar {#crm-integrations}

Marketo Measure kan integreras med CRM:er för att lagra och organisera alla data som hämtas av Marketo Measure JS. För närvarande har Marketo Measure API-integreringar med två CRM:

![](assets/1-2.png)

Genom att lägga in Marketo Measure-data i CRM kan ni se detaljerad information om varje kontaktyta och generera rapporter för att förstå hur era kanaler fungerar.

## Tredjepartsprogram {#third-party-applications}

De flesta marknadsförare förlitar sig på ett antal olika program för att driva sin marknadsföring. Förutom Salesforce och MS Dynamics är Marketo Measure integrerat med 13 tredjepartsprogram (se nedan).

![](assets/2-1.png)

Om du gör några marknadsföringssatsningar med programmen ovan kan du länka dessa konton till ditt Marketo Measure-konto. Detta gör det enkelt att spåra och överföra data till ditt Marketo Measure-konto.

## Marketo Measure {#marketo-measure-application}

Marketo Measure används för att visa och rapportera dina attribueringsdata, konfigurera kontoinställningar och uppdatera kontoinformationen. Huvudmenyalternativen i Marketo Measure-appen är:

**Kontokonfiguration**

Här kan du uppdatera företagets allmänna information och få tillgång till Marketo Measure Javascript.

**Inställningar**

Med det här menyalternativet kan du konfigurera dina inställningar för attribuering och kanalmappning, hantera integreringar med CRM och tredjepartsprogram, visa/lägga till Marketo Measure-kontoanvändare och uppdatera faktureringsinformation.

**Kontrollpanel för marknadsföringsavkastning**

Menyalternativet för Dashboard för marknadsföringsavkastning är där du kan visualisera dina data när det gäller kanalprestanda, aktivitet och kostnader.
