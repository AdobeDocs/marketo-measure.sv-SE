---
unique-page-id: 18874692
description: Scenarier i Boomerang - [!DNL Marketo Measure]
title: Scenarier i Boomerang
exl-id: 150db070-eef5-4741-845c-775ab4034ead
feature: Boomerang
source-git-commit: ce54eb497c55c4ab8da55e9b2803dc59a87c7267
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 0%

---

# Scenarier i Boomerang {#boomerang-stage-scenarios}

>[!AVAILABILITY]
>
>Funktionen Boomerang är bara aktiverad för Tier 2- och Tier 3-kunder. Om du vill beställa en högre kontonivå kontaktar du Adobe Account Team (din kontohanterare).

Nedan visas några exempel på scenarier för Boomerang-scenen som ger en förståelse för hur [!DNL Marketo Measure] skapar kontaktytor i varje situation.

## Scenarier med en lead {#single-lead-scenarios}

**Scenario 1: Boomerang-standardkontaktytor för en lead**

Det här är det enklaste scenariot i Boomerang. Den översta raden (märkt Lead 1) representerar de enskilda Leads resa och hur deras kontaktytor visas på Lead-posten. Poängen (märkt säljprojekt) visar hur Leads kontaktytor översätts till säljprojektet. Framgången för kontaktytor förklaras i kronologisk förekomst, från vänster till höger.

I det här scenariot har en kund valt att spåra sina **MQL**- och **SQL**-stadier med Boomerangs. Varje position för Boomerang-kontaktyta är märkt med scenen och numret som den inträffar i (MQL-01, SQL-01, MQL-02). Den sista boomerang-kontaktytan för den scenen har (sista) i kontaktytspositionen.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

![](assets/1-1.png)

**Scenario 2: Boomerang Touchpoints AND Custom Stages for a Lead**

I det här scenariot har en kund bara valt att spåra **SQL-fasen** med boomerang-kontaktytor. MQL- och SAL-stadier spåras fortfarande, men med funktionen för anpassade scener i [!DNL Marketo Measure].

![](assets/2-1.png)

Observera att MQL-kontaktytpunktspositionen inte är märkt med ett tal. Det beror på att den inte markerades för att spåras med Boomerang-kontaktytor. När du skapar kontaktytor för stadier som ingår i den anpassade modellen, men inte spåras med Boomerang, tar [!DNL Marketo Measure] den sista förekomsten från den scenen.

För SAL-scenen ignorerar [!DNL Marketo Measure] de två första förekomsterna av den här scenen. [!DNL Marketo Measure] skapar bara en SAL-kontaktyta för förekomsten _last_. I exemplet ovan inträffar detta precis före OC-kontaktytan.

SQL-scenen spåras med Boomerang-kontaktytor och tre kontaktytor har skapats och etiketterats i enlighet med detta.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

**Scenario 3: När Leads inte når/hoppar över en scen**

Detta scenario använder samma kriterier som scenario 2. En kund har valt att endast spåra SQL-scenen med boomerang-kontaktytor. MQL och SAL spåras fortfarande, men med funktionen [!DNL Marketo Measure] för anpassad scen.

![](assets/3.png)

I det här scenariot kommer Lead aldrig att gå över till SAL-stadiet. Den konverteras till en kontakt innan den når SAL-stadiet, i stort sett&quot;hoppar över&quot; SAL-stadiet. I den här situationen antar [!DNL Marketo Measure] att SAL sker med OC-kontaktytan och att både SAL- och OC-positionen visas på samma kontaktyta.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

## Scenarier med flera leads {#scenarios-with-multiple-leads}

I följande scenarier kan Boomerang Stages bli mer komplicerat, eftersom vi tittar på hur flera leads kan påverka säljprojektsresan.

Den översta raden (märkt Lead 1, i blått) representerar de enskilda Leads resa och hur deras kontaktytor visas på Lead-posten. Detsamma gäller för lead 2 (i rosa) och lead 3 (i orange). Poängen (märkt säljprojekt) visar hur båda dessa leads kontaktytor översätts till säljprojektet. Framgången för kontaktytor förklaras i kronologisk förekomst, från vänster till höger.

**Scenario 1:[!UICONTROL Three Leads with Opportunity]**

I det här scenariot har en kund valt att spåra **MQL**- och **SAL-faserna** med boomerang-kontaktytor. SQL-scenen spåras av standardstadierna.

![](assets/4.png)

FT- och LC-kontaktytorna på affärsmöjligheten kommer från Lead 1 (blå) eftersom de inträffade före FT och LC för Lead 2 (rosa). LC-kontaktytan för Lead 2 visas som en &#39;Form&#39;-kontaktyta i säljprojektet.

MQL-01 (sista) från Lead 2 blir den första MQL för affärsmöjligheten. MQL-01 från Lead 1 visas inte som kontaktyta för säljprojektet eftersom Lead 2:s MQL inträffade först. Lead 1:s MQL-02 och MQL-03 visas dock i säljprojektet.

SQL-scenen spåras med anpassade stadier, inte boomerang-stadier. Även om det finns tre förekomster av SQL-steget mellan Lead 1 och Lead 2 inkluderas bara den sista SQL-förekomsten som kontaktyta i säljprojektet.

SAL-01-kontaktytan (sista) från lead 1 överförs som kontaktyta för affärsmöjligheten. Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson. SAL-01-kontaktytan för lead 2 (sista) skapas som kontaktyta eftersom den här scenövergången inträffade _efter_ OC-beröringen.

3:s FT-, LC- och MQL-, SQL-, SAL-kontaktytor (orange) inträffade alla efter OC-kontaktytan i säljprojektet. Dessa kontaktytor ingår i säljprojektet, men betraktas som&quot;medelkontaktytor&quot;.

När Lead 2 och 3 konverteras till Kontakter skapar [!DNL Marketo Measure] inte en ny OC-kontaktyta eftersom det bara kan finnas en fas där affärsmöjligheten skapas.

**Scenario 2 - Webbbesök Boomerang-kontaktpunkter**

I det här scenariot har en kund valt att spåra **MQL**-, **SQL**- och **SAL**-stadierna med boomerang-kontaktytor. Detta scenario är nästan identiskt med det ovanstående, med några få undantag.

![](assets/6.png)

Alla kontaktytor från Lead 1 inkluderas i affärsmöjligheten, från FT till SAL-01 (Last). LC-kontaktytan från Lead 2 kommer att ingå som en kontaktyta mellan LC- och MQL-01-kontaktytorna på affärsmöjligheten.

Lead 2&#39;s MQL-01 (Last) (Web Visit) kommer inte att skapas som kontaktyta på Opp. Detta beror på att denna kontaktyta var ett webbbesök som inträffar efter den sista förekomsten av SQL-steget och inte bidrar till att driva säljprojektet framåt.

Lead 1 ändras till SAL och konverteras sedan till en kontakt med ett säljprojekt. I det här fallet kombineras positionerna SAL-01 (senaste) och OC i samma kontaktyta.

Fort 3:s FT, LC touch skapas som en kontaktyta i form på Opp. Endast formulärfyllningsåtgärder skapas som kontaktytor efter OC-beröringen. Av den anledningen skapas inte övergångarna SQL-01 (senaste) och SAL-01 (sista) för lead två som kontaktytor eftersom dessa kontaktytor var webbbesök.

Lead 3:s MQL-, SQL- och SAL-beröringar inkluderas som en kontaktyta eftersom det var en formulärfyllningsåtgärd.

**Scenario 3 - Boomerang-attribueringsviktning**

I det här scenariot har en kund valt att spåra **MQL**-, **SQL**- och **SAL**-stadierna med boomerang-kontaktytor.

![](assets/7.png)

FT- och LC-kontaktytorna på affärsmöjligheten kommer från Lead 1 (blå) eftersom de inträffade före FT och LC för Lead 2 (rosa). LC-kontaktytan för Lead 2 visas som en &#39;Form&#39;-kontaktyta i säljprojektet.

MQL-01 (sista) från Lead 2 blir den första MQL för affärsmöjligheten. MQL-01 från Lead 1 visas inte som kontaktyta för säljprojektet eftersom Lead 2:s MQL inträffade först.

SQL-01 (sista) från Lead 2 blir SQL-01 i säljprojektet. SQL-01 på Lead 1 visas inte som kontaktyta för affärsmöjligheten eftersom SQL-01 på Lead 2 inträffade först.

Observera att Lead 1-boomerangerna mellan MQL och SQL några gånger innan de äntligen når SAL-stadiet. SQL-01, MQL-02, SQL-02, MQL-03, SQL-03 _inkluderas inte_ som kontaktytor i affärsmöjligheten eftersom de här scenövergångarna inte hjälper till att föra affärsmöjligheten framåt under resan.

Slutpunkten för SAL-01 (sista) från Lead 1 är nästa kontaktyta som ska ingå i Opp. Lead 1 konverteras sedan till en kontakt med en möjlighet, vilket skapar en OC-kontaktyta.

FT- och LC för lead 3 och MQL-, SQL- och SAL-kontaktytorna visas som en formulärpekning på säljprojektet.

SQL-01-kontaktytan för lead 2 (sista) inkluderas inte som en kontaktyta på Opp eftersom den inträffade efter OC-kontaktytan. Lead 2:s SQL-scenövergång inträffade _efter den sista SAL-scenövergången_ och hjälper inte till att driva affärsmöjlighetens resa framåt.

## Scenarier om affärsmöjligheter {#opportunity-scenarios}

**Scenario 1 - Kontakter med möjlighet och Boomerang-spårning**

I det här scenariot har en kund valt att spåra **Demo- och förhandlingsfasövergångarna** för **kontakten**. Varje boomerang-scen kan ta emot upp till två kontaktytor. Skillnaden mellan scenövergångar för en kontakt- och scenövergång på en lead är att kontaktfasövergångar kan visas som Boomerang-kontaktytor på säljprojektet _efter_ OC-kontaktytan. Detta gäller inte för scenövergångar som förekommer på leadet eftersom dessa visas som en kontaktyta i form.

![](assets/8.png)

I det här exemplet ingår Demo- och förhandlingsfasövergångarna för Contact 1 som Demo-01- och Negotiation-01-kontaktytor i säljprojektet. Kontakt 2&#39;s Demo stage transition (Demo-scenövergång) inträffar _efter_ Contact 1&#39;s och visas som Demo-02 (Last)-kontaktyta i säljprojektet.

Observera att det inte finns någon andra övergång till förhandlingsfasen. Möjligheten går omedelbart från Demo-02 (sista) till Close Won. I det här fallet kommer [!DNL Marketo Measure] att inkludera förhandlingsövergången med sluten Won-kontaktyta.
