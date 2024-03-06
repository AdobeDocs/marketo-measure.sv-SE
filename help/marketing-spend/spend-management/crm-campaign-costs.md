---
unique-page-id: 18874688
description: CRM-kampanjkostnader - [!DNL Marketo Measure]
title: CRM-kampanjkostnader
exl-id: d967cabe-b9f1-4ea1-a81b-e4484c703ecf
feature: Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 0%

---

# CRM-kampanjkostnader {#crm-campaign-costs}

Mest [!DNL Marketo Measure] kunderna använder CRM-kampanjer för att spåra offline-marknadsföringsaktiviteter. Marknadsförare som använder dessa kampanjer övervakar också kostnaderna inom CRM. Den här funktionen gör det enklare för marknadsförare genom att tillåta [!DNL Marketo Measure] läsa dessa kostnader och tillämpa dem på de rapporterade marknadsföringsutgifterna inom [!DNL Marketo Measure]. Till dags dato har kunderna varit tvungna att manuellt ange kostnader för varje kampanj per månad, men med den nödvändiga informationen till[!DNL Marketo Measure]kan man automatisera denna process så att marknadsförarna kan lägga mer tid på att analysera sina utgifter och sin avkastning.

## Tillgänglighet {#availability}

Den här funktionen är tillgänglig för alla [!DNL Salesforce] och Dynamics.

## Så här fungerar det {#how-it-works}

[!DNL Marketo Measure] söker först efter kampanjer som har&quot;aktiverats&quot; för kontaktytor, så det finns antingen en matchande regel för kampanjsynkronisering som skapades, eller värdet för Aktivera slutpunkter för köpare är&quot;Inkludera alla kampanjmedlemmar&quot; eller&quot;Inkludera kampanjmedlemmar som har svarats&quot;. Dessutom [!DNL Marketo Measure] måste importera rätt värden och veta hur kostnaderna ska fördelas, så vi kräver att följande fält innehåller ett värde:

**[!DNL Salesforce]**: `ActualCost`, `StartDate`, `EndDate`

**[!DNL Microsoft Dynamics]**: `totalactualcost`, `actualstart`, `actualend`

Om något av de tre fälten saknar ett värde, [!DNL Marketo Measure] kommer inte att importera kostnaderna. Du kan korrigera detta genom att uppdatera Campaign-posten i CRM. Kostnaderna importeras inte om de är inställda på $0 eftersom [!DNL Salesforce] behandlar tomt och $0 som samma.

För [!DNL Marketo Measure] för att bestämma fördelningen av en kampanj över flera månader används kampanjens start- och slutdatum för att fördela beloppet jämnt per dag.

![](assets/1.jpg)

I det här exemplet varar en kampanj i 109 dagar, så med en totalkostnad på 18 000 dollar blir utgifterna per dag 165,14 dollar.

Baserat på antalet dagar per månad får vi dessa månadssummor, vilket framgår av tabellen:

Jul 2018: ($18 000/109) x 31 = $5 119.27

aug 2018: ($18 000/109) x 31 = $5 119.27

Sep 2018: ($18 000/109) x 30 = $4 954.13

Okt 2018: ($18 000/109) x 17 = $2 807.34

## Historiskt rapporterade utgifter {#historical-reported-spend}

Om du har angett utgifter för kampanjer som har spårats tidigare och mappats till en CRM-kampanj åsidosätter de inte någon av de angivna kostnaderna. Om samma kampanj i CRM ändras, ignoreras den och de ändringar du tidigare gjort i CSV-överföringen prioriteras.

Om du föredrar att vi tar kostnaden för CRM Campaign från och med nu ändrar du värdet i CSV-filen till $0 som gör att posten annulleras. Nästa gång jobben körs för att importera kostnaderna hämtas tidigare redigerade rapporter in.

## Kampanjer utan kontaktytor {#campaigns-with-no-touchpoints}

Många marknadsförare väljer att rapportera marknadsföringsutgifter för CRM-kampanjer som inte genererade några kontaktytor eller inte har några Campaign-medlemmar för att spåra utgifter. Så länge som de tre fälten är ifyllda (startdatum, slutdatum, kostnad) och kampanjen är aktiverad för kontaktytor, [!DNL Marketo Measure] drar in den kostnaden, även om den inte har några kontaktytor.

Detta kan vara användbart för att spåra utgifter för större marknadsföringskostnader eller verktyg för att få med detta i dina avkastningsberäkningar.

## Marketo Program Sync {#marketo-program-sync}

Om du samlar Marketo-program i CRM som kampanjer kontrollerar du att du har konfigurerat mappningen Startdatum, Slutdatum och Periodkostnad för de CRM-fält som krävs. Eftersom det inte finns någon mappning till fältet Enable Buyer Touchpoints (Aktivera slutpunkter för köpare) måste ni ändå aktivera dessa kampanjer så att kostnaderna kan hämtas.

## Redigera kostnaderna {#editing-the-costs}

När en kampanj har importerats från CRM behandlas den på samma sätt som en API Ads Provider och visas inte i CSV-filen för att göra några kostnadsändringar.

Alla ändringar av kostnaderna eller distributionen måste göras i CRM så att vi kan peka på en enda sanning.

## Vanliga frågor och svar {#faq}

**Jag har gjort en ändring i min kampanj - när ska jag förvänta mig att se ändringarna i tabellen för Marketing Spend eller i min rapportering?**

3-4 timmar

**Jag har fyllt i startdatum, slutdatum och kostnad, men varför visas inte mina kostnader i [!DNL Marketo Measure]?**

Kontrollera att du antingen har värdet Enable Buyer Touchpoint (Aktivera slutpunkt för köpare) inställt på Include All Campaign Members (Inkludera alla kampanjmedlemmar) eller åtminstone Include &#39;Responded&#39; Campaign Members (Inkludera kampanjmedlemmar), eller att du har skapat en anpassad kampanjsynkroniseringsregel som inkluderar den här kampanjen. Om du har bekräftat detta och fortfarande inte ser Campaign kan du kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} så att vi kan kontrollera att era kampanjer importeras på rätt sätt.

**Jag måste ändra distributionen av min kampanj så att jag kan väga den tyngre under vissa månader. Hur ska jag göra det?**

Kostnadens fördelning bygger uteslutande på en jämn fördelning mellan startdatumet och slutdatumet. Tyvärr kan vi inte ändra det så att dina kostnader har en annan viktning än de angivna datumen. Du kan kontrollera detta genom att justera start- och slutdatumet för kampanjen eftersom varje dag i månaden är viktig.

**Jag har skapat kostnader för min överordnade kampanj - hur tilldelas barnkampanjer kostnaderna från den överordnade kampanjen?**

Faktiskt så kommer kostnaderna att hämtas in direkt från en enda kampanj, oavsett vilken relation mellan Förälder eller Barn det gäller. Vi rekommenderar att kostnaden läggs på barnkampanjer, tillsammans med kampanjens datum, och sedan använder vi Parent som paraplykampanj där den överordnade kampanjen inte skulle aktiveras för kontaktytor.

**Hur ändrar jag kostnaden för en månad i [!DNL Marketo Measure]?**

Eftersom vi förlitar oss på CRM som den enda källan till sanning måste alla ändringar göras i CRM. När kampanjen har importerats av [!DNL Marketo Measure]kan kampanjvärdena inte redigeras i [!DNL Marketo Measure] eller i CSV-filen.

**I vilket scenario skulle en kampanj visas i tabellen Marketing Spend, och sedan inte längre visas?**

Alla tre nyckelfälten måste ha ett värde: Startdatum, Slutdatum och Kostnad. Vårt standardbeteende är att vi bara importerar kampanjer med ett värde som är större än $0. Helst skulle vi importera kampanjer där det finns en explicit $0 och inte importera dem som lämnas tomma, men Salesforce-API importerar båda som $0 oavsett värdet. Om värdet för Enable Buyer Touchpoint ändras från Include All (Inkludera alla) eller Include &quot;Responded&quot; (Inkludera alla)) till Exclude All (Uteslut alla), tar vi bort Campaign och Cost (Kostnad) från tabellen Marketing Spend.

**Vilken kostnad prioriterar om en rad redan har hämtats från CRM och jag har angett en annan rad i CSV-filen med samma kampanj-ID?**

Även om du kan överföra filen kan du [!DNL Marketo Measure] använder inte den raden eftersom vi redan har ett kampanj-ID med samma värde som hämtas automatiskt från integreringen.

**Hur föreslår ni att vi ska få in kostnaderna från våra digitala kampanjer som vi har skapat i CRM?**

För vår [!DNL Marketo Measure] javascript håller redan på att spåra webbaktiviteter från din webbplats, vi rekommenderar att du inte synkroniserar några kampanjer som spårar kampanjmedlemmar från webbformulär eller andra webbplatsaktiviteter eftersom det kommer att göra att kontakterna räknas dubbelt. På grund av detta kanske du vill fortsätta använda alternativet CSV-överföring i Marketing Spend för att spåra dessa online-/digitala kostnader om vi inte redan är integrerade med den plattformen (det vill säga Twitter, Adroll).
