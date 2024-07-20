---
description: Best Practices for Activities Attribution - [!DNL Marketo Measure]
title: Best Practices for Activities Attribution
exl-id: 66fb9f47-3912-40a6-b112-3efca789f321
feature: Attribution
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Best Practices for Activities Attribution {#best-practices-for-activities-attribution}

## Översikt {#overview}

Funktionen [!DNL Marketo Measure] för aktivitetsattribuering gör att kunder kan skapa kontaktytor från aktivitetsposter i CRM. Det här sättet att skapa kontaktytor är flexibelt. Det gör att du kan skapa regler baserade på fälten Uppgift eller Händelse för att informera [!DNL Marketo Measure] om vilka aktivitetsposter som ska användas för att skapa kontaktytor och därför få attribueringskrediter.

Det vanligaste användningsområdet för den här funktionen är att utforma regler som inkluderar säljinteraktioner i kundens kontaktpunktsdata. Activity Attribution gör det möjligt för er att anpassa era sälj- och marknadsföringsdata till en enda resa.

För många [!DNL Salesforce]-instanser kan Activity-objektet innehålla olika posttyper, så det är viktigt att dina Activity-regler är specifika och anpassade till de poster som du försöker översätta till kontaktytor. Följande metodtips hjälper dig att se till att du skapar meningsfulla och värdefulla kontaktytor via din aktivitetsattribuering.

## Bästa praxis {#best-practice}

Oavsett om du definierar aktivitetsregler för första gången eller bara granskar aktivitetsregler som har konfigurerats tidigare bör du tänka på följande bästa praxis.

* Börja enkelt
   * Identifiera några viktiga typer av aktiviteter som du vill införliva i dina [!DNL Marketo Measure]-data och lägg sedan till fler typer när du blir bekväm med hur dessa kontaktytor tilldelas
   * Som vi nämnt är det primära syftet med den här funktionen att skapa kontaktytor som spårar effekten av säljutvecklingsteamet, särskilt utgående telefonsamtal och utgående e-post

>[!NOTE]
>
>Vi rekommenderar **INTE** att du spårar försäljningsaktiviteter som inträffar efter att affärsmöjligheten har skapats, eftersom spårning av en försäljningschefsprocess inte ger någon större insikt. Målet är att spåra effekten av försäljningen vid sidan av effekten av marknadsföringen, främst i utvecklingen av en ny möjlighet/pipeline-produktion

* Använd inte formelfält för att definiera regler
* Skapa regler som är specifika och exakta
   * Tröskelvärdet för att skapa en aktivitetskontaktyta ska vara detsamma (eller liknande) som för en formulärfyllning eller ett kampanjmedlemskap: Svar på ett utgående e-postmeddelande eller slutförda telefonkonversationer
* Verifiera alltid nya regler i [!DNL Salesforce] innan de sparas och bearbetas
   * Om du replikerar aktivitetsreglerna i en rapporttyp &quot;Aktiviteter och händelser&quot; får du en tydlig förståelse för exakt hur många kontaktytor som kommer från regeln
* Arbeta i ditt säljteam
   * Genom att lägga dig i det team som arbetar närmast dina aktivitetsposter eller säljaktiveringsverktyg kan du vara säker på att du använder rätt fält för att definiera dina regler

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar dina regler för aktivitetsattribuering minst två gånger per år ser du till att dina kontaktytor för aktiviteten är korrekta och aktuella. Du vill se till att dessa regler inte skapar oönskade kontaktytor som späder ut dina Buyer Attribution-data. En granskning av hur reglerna är definierade hjälper dig och ditt team att känna sig säkra på din aktivitetsattribuering och dess roll i dina [!DNL Marketo Measure]-data.

Andra orsaker till att det kan utlösa en granskning av dina aktivitetsregler är ...

* Omsättning i marknadsföringsteamet
* Ändringar i fält som används för att definiera dina aktivitetsposter
* Ändringar eller uppdateringar av säljaktiveringsverktygen

>[!MORELIKETHIS]
>
>* [Aktivitetsattribut](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Attribuering av försäljningsaktiviteter - frågor och svar](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
