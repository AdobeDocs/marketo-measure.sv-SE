---
description: Best Practices for Activities Attribution - [!DNL Marketo Measure] - Produktdokumentation
title: Best Practices for Activities Attribution
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Best Practices for Activities Attribution {#best-practices-for-activities-attribution}

## Översikt {#overview}

The [!DNL Marketo Measure] Funktionen för aktivitetsattribuering gör att kunder kan skapa kontaktytor från aktivitetsposter i CRM. Det här sättet att skapa kontaktytor är flexibelt eftersom det gör att du kan skapa regler baserade på aktivitets- eller händelserefält för att informera [!DNL Marketo Measure] vilken aktivitet som registrerar att den ska producera kontaktytor från och därefter ta emot attribueringskredit.

Det vanligaste användningsområdet för den här funktionen är att utforma regler som inkluderar säljinteraktioner i kundens kontaktpunktsdata. Activity Attribution gör det möjligt för er att anpassa era sälj- och marknadsföringsdata till en enda resa.

För många [!DNL Salesforce] -instanser kan Activity-objektet innehålla en mängd olika posttyper, så det är viktigt att dina Activity-regler är specifika och anpassade till de poster som du försöker att omvandla till kontaktytor. Följande metodtips hjälper dig att se till att du skapar meningsfulla och värdefulla kontaktytor via din aktivitetsattribuering.

## Bästa praxis {#best-practice}

Oavsett om du definierar aktivitetsregler för första gången eller bara granskar aktivitetsregler som har konfigurerats tidigare bör du tänka på följande bästa praxis.

* Börja enkelt
   * Identifiera några viktiga typer av aktiviteter som du vill införliva i [!DNL Marketo Measure] lägg sedan till fler typer när du blir bekväm med hur dessa kontaktytor tilldelas
   * Som vi nämnt är det primära syftet med den här funktionen att skapa kontaktytor som spårar effekten av säljutvecklingsteamet, särskilt utgående telefonsamtal och utgående e-post

>[!NOTE]
>
>Det är **NOT** Vi rekommenderar att du spårar försäljningsaktiviteter som inträffar efter att affärsmöjligheten har skapats, eftersom spårning av en försäljningsprocess inte ger någon större insikt. Målet är att spåra effekten av försäljningen vid sidan av effekten av marknadsföringen, framför allt i utvecklingen av en ny möjlighet/pipeline-produktion

* Använd inte formelfält för att definiera regler
* Skapa regler som är specifika och exakta
   * Du vill att tröskelvärdet för att skapa en kontaktyta för aktivitet ska vara samma (eller liknande) som för en formulärfyllning eller ett kampanjmedlemskap, dvs. (Besvarar en utgående e-post eller slutförda telefonkonversationer)
* Validera alltid nya regler i [!DNL Salesforce] innan du sparar och bearbetar
   * Om du replikerar dina aktivitetsregler i en rapporttyp &quot;Aktiviteter och händelser&quot; får du en tydlig förståelse för exakt hur många kontaktytor som skapas utifrån den regeln
* Arbeta i ditt säljteam
   * Genom att lägga dig i det team som arbetar närmast dina aktivitetsposter eller säljaktiveringsverktyg kan du vara säker på att du använder rätt fält för att definiera dina regler

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar reglerna för aktivitetsattribuering minst två gånger per år ser du till att dina aktivitetskontaktytor är korrekta och aktuella. Du vill se till att dessa regler inte skapar oönskade kontaktytor som späder ut dina Buyer Attribution-data. En recension av hur reglerna är definierade hjälper dig och ditt team att känna sig säkra på ditt aktivitetsattribut och dess roll i ditt [!DNL Marketo Measure] data.

Andra orsaker till att det kan utlösa en granskning av dina aktivitetsregler är ...

* Omsättning i marknadsföringsteamet
* Ändringar i fält som används för att definiera dina aktivitetsposter
* Ändringar eller uppdateringar av säljaktiveringsverktygen

>[!MORELIKETHIS]
>
>* [Verksamhetsattribuering](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Vanliga frågor om attribut för försäljningsaktiviteter](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


