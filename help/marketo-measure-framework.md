---
description: Marketo Measure Framework
title: Marketo Measure Framework
exl-id: fa6de27c-cdd2-4fd9-ac35-7286fe2752d8
feature: Fundamentals
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---


# Marketo Measure Framework {#marketo-measure-framework}

Läs mer om de fyra huvudkomponenterna i Marketo Measure-ramverket. Marketo Measure förlitar sig på dessa applikationer för att spåra, organisera och lagra data samt för att tillhandahålla rapporteringsfunktioner. De fyra komponenterna som utgör Marketo Measure ramverk är:

* Marketo Measure JavaScript
* CRM-integreringar
* Tredjepartsprogram/-system
* Marketo Measure

## Marketo Measure JavaScript {#marketo-measure-javascript}

Marketo Measure JavaScript spårar alla interaktioner för webbmarknadsföring, även kallade kontaktytor, som potentiella kunder/leads har med er organisation. Det är ett anpassat skript som läggs till före den avslutande `</head>`-taggen på alla sidor på webbplatsen.

`<script type="text/javascript" src="//[cdn.bizible.com/scripts/bizible.js](http://cdn.bizible.com/scripts/bizible.js)" async=""></script>`

>[!NOTE]
>[Klicka här](/help/marketo-measure-tracking/adding-marketo-measure-script.md) om du vill ha anvisningar om hur du lägger till Marketo Measure JS.

Marketo Measure JS hämtar in data från webbbesök (inklusive anonyma webbbesök), allmän trafik-/sidnavigering, innehållshämtningar och inskickade formulär. Dessa data läggs in i CRM och varje marknadsföringsinteraktion visas som en kontaktyta.

## CRM-integreringar {#crm-integrations}

Marketo Measure kan integreras med CRM:er för att lagra och organisera alla data som hämtas av Marketo Measure JS. För närvarande har Marketo Measure API-integreringar med två CRM:

![Marketo Measure kan integreras med CRM:er för att lagra och organisera alla data](assets/overview-resources-14.png)

Genom att lägga in Marketo Measure-data i CRM kan ni se detaljerad information om varje kontaktyta och generera rapporter för att förstå hur era kanaler fungerar.

## Tredjepartsprogram {#third-party-applications}

De flesta marknadsförare förlitar sig på ett antal olika program för att driva sin marknadsföring. Förutom Salesforce och MS Dynamics är Marketo Measure integrerat med 13 tredjepartsprogram (se nedan).

![De flesta marknadsförare förlitar sig på några olika program för att köra sin marknadsföring](assets/overview-resources-15.png)

Om du gör några marknadsföringssatsningar med programmen ovan kan du länka dessa konton till ditt Marketo Measure-konto. Detta gör det enkelt att spåra och överföra data till ditt Marketo Measure-konto.

## Marketo Measure {#marketo-measure-application}

Marketo Measure används för att visa och rapportera dina attribueringsdata, konfigurera kontoinställningar och uppdatera kontoinformationen. Huvudmenyalternativen i Marketo Measure-appen är:

**Kontokonfiguration**

Här kan du uppdatera företagets allmänna information och få tillgång till Marketo Measure Javascript.

**Inställningar**

Med det här menyalternativet kan du konfigurera dina inställningar för attribuering och kanalmappning, hantera integreringar med CRM och tredjepartsprogram, visa/lägga till Marketo Measure-kontoanvändare och uppdatera faktureringsinformation.

**Kontrollpanel för marknadsföringsavkastning**

Menyalternativet för Dashboard för marknadsföringsavkastning är där du kan visualisera dina data när det gäller kanalprestanda, -aktivitet och -kostnad.
