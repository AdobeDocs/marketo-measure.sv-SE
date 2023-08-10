---
unique-page-id: 37356395
description: "[!DNL Marketo Engage] Integrering av människor - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Engage] Integrering av människor"
exl-id: 51930e84-4ff8-4e35-9d44-ea017c24b051
feature: Integration
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 0%

---

# [!DNL Marketo Engage] Integrering av människor {#marketo-engage-people-integration}

Tack vare integreringen av Marketo-användare kan [!DNL Marketo Measure] för att börja ladda ned personer från Marketo och börja knyta deras spårade sessioner till individen och kartlägga kontaktytor mot deras engagemang. Historiskt, [!DNL Marketo Measure] kunde bara mappa kontaktytor till en person från CRM, så det hjälper marknadsförarna att mäta sina marknadsföringssatsningar snabbare i stället för att vänta på en scen eller utlösare för att synkronisera dem till CRM.

## Krav {#requirements}

* Production Marketo, instans
* Produktion [!DNL Salesforce] eller [!DNL Microsoft Dynamics] instance
* Valfritt [!DNL Marketo Measure] prenumeration
* SOLR aktiverat (kontakta [Marketo Support](https://nation.marketo.com/t5/Support/ct-p/Support) för att aktivera detta)

## Så här fungerar det {#how-it-works}

Som befintlig kund [!DNL Marketo Measure] hämtar redan personer från CRM. Standardprocessen är att [!DNL Marketo Measure] hämtar personerna och mappar e-postadressen till en webbsession som vi har spårat via bizible.js.

I och med nedladdningen av Marketo [!DNL Marketo Measure] kan nu mappa webbsessioner till en större grupp individer, de som inte har synkroniserats med CRM. Vi ser ofta detta på grund av interna processer som väntar tills man uppnår en viss status innan man skickar dem till CRM.

När [!DNL Marketo Measure] har mappat Marketo-personen till en webbsession, kommer bearbetningen att generera relevanta kontaktytor för den, som slutligen kan rapporteras i [!DNL Marketo Measure Discover]. Om den där Marketo-personen skickas till CRM, [!DNL Marketo Measure] hanterar det duplicerade scenariot och vi återskapar kontaktytan för CRM-personen och markerar den ursprungliga uppsättningen som &quot;dubblett&quot;.

För att vi ska kunna upptäcka dessa dubbletter måste du [!DNL Marketo-Salesforce] eller [!DNL Marketo-Dynamics] Synkroniseringen fyller i lead- och kontakt-ID:n på Marketo-personen. Om ID:t synkroniseras korrekt bör du kunna se CRM-ID:t på personposten, så här:

![](assets/5a.png)

![](assets/5b.png)

Kunderna kan rapportera alla Marketo-användare och CRM-personer i [!DNL Marketo Measure] Upptäck. Om du bara är intresserad av att rapportera CRM-personer rekommenderar vi att du skapar ett segment för att filtrera dem.

## [!DNL Marketo Measure Discover] {#marketo-measure-discover}

Vid rapportering av leads (personer) i [!DNL Marketo Measure Discover]kommer du att se det totala antalet leads för Marketo och CRM. Om du bara vill rapportera om Marketo-användare eller bara CRM-leads, vill du skapa en segmentkategori för källan och sedan skapa segmentregler för Marketo och CRM med hjälp av fältet Källsystem för att definiera regeln. När du har skapat segmenten visas källkategorin som kan filtreras i hela [!DNL Marketo Measure Discover] instrumentpaneler.

![](assets/bizible-discover-1.png)

![](assets/bizible-discover-2.png)

## Fältmappningar {#field-mappings}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p><strong>biz_leads</strong></p></th> 
   <th><p><strong>Marketo</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>id</p></td> 
  </tr> 
  <tr> 
   <td><p>MODIFIED_DATE</p></td> 
   <td><p>updatedAt<strong>*</strong></p></td> 
  </tr> 
  <tr> 
   <td><p>CREATED_DATE</p></td> 
   <td><p>createdAt</p></td> 
  </tr> 
  <tr> 
   <td><p>E-POST</p></td> 
   <td><p>e-post</p></td> 
  </tr> 
  <tr> 
   <td><p>WEB_SITE</p></td> 
   <td><p>webbplats</p></td> 
  </tr> 
  <tr> 
   <td><p>FÖRETAG</p></td> 
   <td><p>företag</p></td> 
  </tr> 
  <tr> 
   <td><p>IS_CONVERTED</p></td> 
   <td><p>n/a</p></td> 
  </tr> 
  <tr> 
   <td><p>ACCOUNT_ID</p></td> 
   <td><p>Konto-ID (L2A)</p></td> 
  </tr> 
  <tr> 
   <td><p>BIZIBLE_STAGE</p></td> 
   <td><p>Status</p></td> 
  </tr> 
  <tr> 
   <td><p>IS_DELETED</p></td> 
   <td><p>true/false</p></td> 
  </tr> 
 </tbody> 
</table>

*Det finns ett känt beteendeproblem där fält från Marketo företagsenhet inte påverkar personens uppdateradeAt-värde, så om relevanta fält som Webbplats eller Företag uppdateras. [!DNL Marketo Measure] kommer inte att veta att dessa värden ändras eftersom värdet för updatedAt date/time inte uppdateras. Detta påverkar ABM-funktionen, där vi inte skulle ha nya data för att lösa kontot för leadet. Det finns inga lösningar just nu, men det finns planer på att ta itu med detta i framtiden.

## Vanliga frågor {#faq}

**Varför skiljer sig antalet leads mellan mitt CRM och [!DNL Marketo Measure Discover]?**

Eftersom den här integreringen gör det möjligt för oss att skapa kontaktytor för leads som vi har importerat direkt från Marketo, kan det finnas leads som inte har synkroniserats med CRM, vilket innebär att antalet inom Discover kan vara högre än CRM eftersom kontaktytorna bara pushas för CRM-leads.

**Hur ersätter detta mina data?**

Den här integreringen sammanfogar datauppsättningarna i din nuvarande [!DNL Marketo Measure] -instans så att inget ersätts. Det vi förväntar oss av era nuvarande CRM-leads är att vi när vi laddar ned Marketo Leads tvåårsvärde helt enkelt uppdaterar denna lead-post för att visa att det också fanns en matchning mot en Marketo Lead. Att allt händer i backend-objektet och att kontaktytorna förväntas förbli desamma. Vi förväntar oss också fler kontaktytor tack vare Marketo Leads. Om vi kan hitta webbsessioner som matchar Marketo-folk börjar vi se kontaktytorna som räknas i [!DNL Marketo Measure].

**Kan jag bara hämta mina medarbetare från Marketo och stänga av CRM-anslutningen?**

För tillfället, nej. Vi kommer att ha det här alternativet i framtiden, men vi måste bygga ut andra faser av denna Marketo-integration så att vi kan koppla program, möjligheter och avtal från Marketo till [!DNL Marketo Measure].

**Importerar ni ALLA mina Marketo-användare?**

För närvarande är den tidigaste vi importerar personer från och med den 1 januari 2018 så att vi har minst två års data, vilket är samma beteende som vi tillämpar vid CRM-nedladdningar. Vi implementerar förbättrat beteende för att ladda ned ett rullande tvåårigt fönster när Marketo-anslutningen har upprättats.

Vi filtrerar inte heller efter några typer av personer, så alla personer inom tvåårsperioden importeras och är berättigade till kontaktytor.

**Vad är SOLR och varför måste jag ha det aktiverat för att kunna använda den här funktionen?**

Att aktivera SOLR för din Marketo-instans är ett enkelt steg som öppnar maskinvaruutrymme i Marketo så att din prenumeration kan använda [!DNL Marketo Measure] integrering. Utan SOLR aktiverat har vi inte tillgång till vissa samtal som annars skulle göra det möjligt för oss att hämta lämpliga personer från din Marketo-instans.
