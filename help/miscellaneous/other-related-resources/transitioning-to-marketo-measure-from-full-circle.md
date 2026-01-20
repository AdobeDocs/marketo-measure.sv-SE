---
unique-page-id: 18874535
description: Övergår till  [!DNL Marketo Measure] från hel cirkel - [!DNL Marketo Measure]
title: Övergår till  [!DNL Marketo Measure]  från hel cirkel
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Övergår till [!DNL Marketo Measure] från hel cirkel {#transitioning-to-marketo-measure-from-full-circle}

Vill du flytta från fullständig cirkel till [!DNL Marketo Measure]? Du är inte ensam. Här är de största sakerna att tänka på och de lärdomar vi dragit av andra kunder som gått över.

## Kampanjbaserad spårning jämfört med Spårning för flera Source {#campaign-based-tracking-vs-multi-source-tracking}

Alla interaktioner i [!UICONTROL Full Circle] spåras via CRM-kampanjmedlemskapet. Med [!DNL Marketo Measure] kompileras inköpsresan via en kombination av våra aktivitetsposter för JavaScript, CRM-kampanjer och CRM-aktiviteter. Det kan vara besvärligt att göra den mentala övergången från&quot;all interaktion måste spåras i en CRM-kampanj för att vår attribueringsrapportering ska fungera&quot; till&quot;endast denna deluppsättning av interaktioner måste spåras i en CRM-kampanj för att vår attribueringsrapportering ska fungera&quot;.

Generellt sett, så här skapar [!DNL Marketo Measure] kontaktpunktsposter för de vanligaste interaktionstyperna:

* Formulärfyllningar på dina webbplatser: [!DNL Marketo Measure] JavaScript
* Sidvyer på dina webbplatser: Skapade av [!DNL Marketo Measure] JavaScript endast om den här sidvyn körde en angiven CRM-milstolpe (till exempel Lead eller Skapa säljprojekt)
* Offlineinteraktioner som konferenser eller mässor: medlemskap i CRM-kampanj
* Digitala interaktioner som sker var som helst på Internet och som inte är din webbplats (till exempel ett webbinarium som finns på en tredjepartswebbplats som genererar en listöverföring): medlemskap i CRM-kampanjen
* Interaktion med säljarna: CRM-aktivitetsposter

Om ni känner er säkra på CRM-kampanjhanteringen och föredrar att behålla befintliga processer är det bra. Det skadar inte [!DNL Marketo Measure] att fortsätta spåra alla interaktioner i CRM-kampanjer. Du kan utforma logik som bara skapar kontaktytor från en önskad delmängd av kampanjer för att undvika dubbelarbete vid kontaktytor.

## Synlighet kontra attribut {#visibility-vs-attribution}

Med de flesta inställningar för Full Circle ser du varje interaktion en person har med marknadsförings- eller säljsatsningarna. Sidvisningar, upprepade sidbesök, medlemskap i tredubbleringskampanjer - Alla dessa visas i en hel cirkel. Om du visar en sida 300 gånger skapar Full Circle 300 dubblettkampanjer och ger dig ett medlemskap i var och en av dem. Det gör inte [!DNL Marketo Measure] och det var ett medvetet designbeslut från vår sida.

[!DNL Marketo Measure] vill förse dig med en attribueringsartikel som på lämpligt sätt fördelar meningsfulla interaktioner och vikt mellan de mest effektiva kontaktytorna. [!DNL Marketo Measure]-ramverket kommer till exempel inte att visa sidvyer (utan formulärfyllningar) som vanliga kontaktytor. En fristående sidvy har förmodligen ingen effekt på framkörningen av en köpresa, men vi skapar en kontaktyta om det är den senaste interaktionen före en angiven CRM-milstolpe (som Lead eller Opportunity Creation). Vi vill inte visa allt. Vi vill visa dig de saker som är viktiga ur attribueringssynpunkt.

Arbeta med din [!DNL Marketo Measure]-representant för att ställa in lämpliga förväntningar på vilka data som inte längre är tillgängliga för ditt team.

## Före-[!DNL Marketo Measure]-data {#pre-marketo-measure-data}

Standardrekommendationen är att börja rapportera och samla in data från den dag du distribuerade JavaScript [!DNL Marketo Measure] framåt, vilket är dubbelt så för tidigare Full Circle-kunder. Tänk på de två avsnitten ovan: Du är van vid att se en större mängd data och du är van vid alla data som kommer från CRM-kampanjmedlemskapet. Om du väljer att ta med vissa eller alla data från före implementeringen av [!DNL Marketo Measure], kommer du inte att jämföra äpplen med äpplen under JavaScript implementeringsdatum.

Men vi förstår säkert att många kunder behöver dessa historiska data, särskilt om du har en längre säljcykel (större än 90 dagar), kanske du vill ge [!DNL Marketo Measure] synlighet i data före [!DNL Marketo Measure]. Diskutera detta noggrant med din [!DNL Marketo Measure]-representant och kom alltid ihåg att en förskjutning över implementeringsdatumet kan leda till förbättringar eller försämrade kanalprestanda eller kanalengagemang och andra potentiellt felaktiga slutsatser.

## I sammanfattning {#in-summary}

Du är i gott sällskap och vi har hjälpt många andra kunder att hantera dessa förändringar. Arbeta med din [!DNL Marketo Measure]-representant för att förstå effekterna ovan och eventuella andra problem du kan ha.
