---
unique-page-id: 18874535
description: Övergår till [!DNL Marketo Measure] från hel cirkel - [!DNL Marketo Measure]
title: Övergår till [!DNL Marketo Measure] från hel cirkel
exl-id: fd471771-33e2-413a-b155-02ba6e32e10c
feature: Attribution, Fundamentals
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Övergår till [!DNL Marketo Measure] från hel cirkel {#transitioning-to-marketo-measure-from-full-circle}

Gå över från hel cirkel till [!DNL Marketo Measure]? Du är inte ensam. Här är de största sakerna att tänka på och de lärdomar vi dragit av andra kunder som gått över.

## Kampanjbaserad spårning jämfört med flerkällsspårning {#campaign-based-tracking-vs-multi-source-tracking}

Alla interaktioner i [!UICONTROL Full Circle] spåras via medlemskap i CRM-kampanjer. Med [!DNL Marketo Measure], sammanställs köpresan genom en kombination av våra JavaScript-, CRM-kampanjmedlemskap och CRM-aktivitetsposter. Det kan vara besvärligt att göra den mentala övergången från&quot;all interaktion måste spåras i en CRM-kampanj för att vår attribueringsrapportering ska fungera&quot; till&quot;endast denna delmängd av interaktioner behöver spåras i en CRM-kampanj för att vår attribueringsrapportering ska fungera&quot;.

Generellt sett, så här [!DNL Marketo Measure] skapar kontaktpunktsposter för de vanligaste interaktionstyperna:

* Formulärfyllningar på din/dina webbplatser: [!DNL Marketo Measure] Javascript
* Sidvisningar på din webbplats(er): Skapad av [!DNL Marketo Measure] Javascript endast om den här sidvyn körde en angiven CRM-milstolpe (t.ex. Lead eller Skapa säljprojekt)
* Offlineinteraktioner som konferenser eller mässor: medlemskap i CRM-kampanj
* Digitala interaktioner som sker var som helst på Internet och som inte är din webbplats (till exempel ett webbinarium som finns på en tredjepartswebbplats som genererar en listöverföring): medlemskap i CRM-kampanjen
* Interaktion med säljarna: CRM-aktivitetsposter

Om ni känner er bekväma med er CRM-kampanjhantering och föredrar att behålla befintliga processer är det bra. Det gör inte ont [!DNL Marketo Measure] för att fortsätta spåra alla interaktioner i CRM-kampanjer. Du kan utforma logik som bara skapar kontaktytor från en önskad delmängd av kampanjer för att undvika dubbelarbete vid kontaktytor.

## Synlighet kontra attribut {#visibility-vs-attribution}

Med de flesta Full Circle-inställningar kan ni se varje enskild interaktion en person har med er marknadsföring eller försäljning. Sidvisningar, upprepade sidbesök, medlemskap i dubblett- och tredubblingskampanjer - Alla dessa visas i en hel cirkel. Om du visar en sida 300 gånger skapar Full Circle 300 dubblettkampanjer och ger dig ett medlemskap i var och en av dem. [!DNL Marketo Measure] inte, och det var ett medvetet designbeslut från vår sida.

[!DNL Marketo Measure] vill ge dig en attribueringsberättelse som tar fram meningsfulla interaktioner och fördelar vikt mellan de mest effektiva kontaktytorna på rätt sätt. Till exempel [!DNL Marketo Measure] visas inte sidvyer (utan formulärfyllningar) som vanliga kontaktytor. En fristående sidvy har förmodligen ingen effekt på framkörningen av en köpresa, men vi skapar en kontaktyta om det är den senaste interaktionen före en angiven CRM-milstolpe (som Lead eller Opportunity Creation). Vi vill inte visa allt. Vi vill visa dig de saker som är viktiga ur attribueringssynpunkt.

Arbeta med dina [!DNL Marketo Measure] svara och ställ in lämpliga förväntningar på vilka data som inte längre är tillgängliga för ert team.

## Pre-[!DNL Marketo Measure] Data {#pre-marketo-measure-data}

Standardrekommendationen är att börja rapportera och samla in data från den dag du distribuerade [!DNL Marketo Measure] JavaScript framåt, och det är dubbelt så bra för tidigare kunder med Full Circle. Tänk på de två avsnitten ovan: du är van vid att se en större mängd data och du är van vid alla data som kommer från CRM-kampanjmedlemskapet. Om du väljer att ta med vissa eller alla data från tidigare [!DNL Marketo Measure] kommer du inte att jämföra äpplen med äpplen över JavaScript-implementeringsdatumet.

Men vi förstår säkert att många kunder behöver dessa historiska data, särskilt om du har en längre säljcykel (större än 90 dagar), kanske du vill ge [!DNL Marketo Measure] synlighet för[!DNL Marketo Measure] data. Diskutera detta noggrant med [!DNL Marketo Measure] rep, och glöm inte att förvränga implementeringsdatumet kan leda till förbättringar eller försämrade kanalprestanda eller -engagemang, samt andra potentiellt felaktiga slutsatser.

## I sammanfattning {#in-summary}

Du är i gott sällskap och vi har hjälpt många andra kunder att hantera dessa förändringar. Arbeta med dina [!DNL Marketo Measure] svara för att förstå effekterna ovan och eventuella andra problem du kan ha.
