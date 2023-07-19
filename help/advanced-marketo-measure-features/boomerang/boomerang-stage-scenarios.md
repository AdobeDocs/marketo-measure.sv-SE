---
unique-page-id: 18874692
description: Scenarier i Boomerang - [!DNL Marketo Measure] - Produktdokumentation
title: Scenarier i Boomerang
exl-id: 150db070-eef5-4741-845c-775ab4034ead
source-git-commit: 01be819ccee1b3079b15a748480e9dacf6adb488
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 0%

---

# Scenarier i Boomerang {#boomerang-stage-scenarios}

>[!AVAILABILITY]
>
>Funktionen Boomerang är bara aktiverad för Tier 3-kunder. Om du vill begära en högre kontonivå kontaktar du kontoteamet (din kontoansvarige) på Adobe.

Nedan följer några exempel på Boomerang Stage-scenarier för att få en förståelse för hur [!DNL Marketo Measure] kommer att skapa kontaktytor i varje situation.

## Scenarier med en lead {#single-lead-scenarios}

**Scenario 1: Standard Boomerang Touchpoints för en lead**

Det här är det enklaste scenariot i Boomerang. Den översta raden (märkt Lead 1) representerar de enskilda Leads resa och hur deras kontaktytor visas på Leadposten. Poängen (märkt säljprojekt) visar hur Leads kontaktytor översätts till säljprojektet. Hur kontaktytorna utvecklas förklaras i kronologisk händelse, från vänster till höger.

I det här scenariot har en kund valt att **MQL** och **SQL** som spåras med Boomerangs. Varje position för Boomerang-kontaktyta märks med scenen och numret som den inträffar i (MQL-01, SQL-01, MQL-02). osv.). Den sista boomerang-kontaktytan för den scenen kommer också att ha &quot;(Sista)&quot; i kontaktytspositionen.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

![](assets/1-1.png)

**Scenario 2: Boomerang Touchpoints AND Custom Stages for a Lead**

I det här scenariot har kunden bara valt att spåra **SQL-fas** med boomerang-kontaktytor. MQL- och SAL-faserna spåras fortfarande, men med [!DNL Marketo Measure] Anpassad scenfunktion.

![](assets/2-1.png)

Observera att MQL-kontaktytpunktspositionen inte är märkt med ett tal. Det beror på att den inte markerades för att spåras med Boomerang-kontaktytor. När du skapar kontaktytor för scener som ingår i den anpassade modellen, men inte spåras med Boomerang, [!DNL Marketo Measure] kommer att ta den sista förekomsten från det steget.

När det gäller SAL-stadiet, [!DNL Marketo Measure] ignorerar de två första förekomsterna av den här scenen. [!DNL Marketo Measure] skapar bara en SAL-kontaktyta för _sista_ förekomst. I exemplet ovan inträffar detta precis före OC-kontaktytan.

SQL-scenen spåras med Boomerang-kontaktytor och tre kontaktytor har skapats och etiketterats i enlighet med detta.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

**Scenario 3: När leads inte når/hoppar över en scen**

Detta scenario använder samma kriterier som scenario 2. En kund har valt att endast spåra SQL-scenen med boomerang-kontaktytor. MQL och SAL spåras fortfarande, men med [!DNL Marketo Measure] Anpassad scenfunktion.

![](assets/3.png)

I det här scenariot kommer Lead aldrig att gå över till SAL-steget. Den konverteras till en kontakt innan den når SAL-stadiet, i stort sett&quot;hoppar över&quot; SAL-stadiet. I denna situation [!DNL Marketo Measure] förutsätts att SAL sker med OC-kontaktytan, och både SAL- och OC-positionen visas på samma kontaktyta.

Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

## Scenarier med flera leads {#scenarios-with-multiple-leads}

I följande scenarier kan Boomerang Stages bli mer komplicerat, eftersom vi tittar på hur flera leads kan påverka säljprojektsresan.

Den översta raden (märkt Lead 1, i blått) representerar de enskilda Leads resa och hur deras kontaktytor visas på Lead-posten. Detsamma gäller för lead 2 (i rosa) och lead 3 (i orange). Poängen (märkt säljprojekt) visar hur båda dessa leads kontaktytor översätts till säljprojektet. Hur kontaktytorna utvecklas förklaras i kronologisk händelse, från vänster till höger.

**Scenario 1:[!UICONTROL Three Leads with Opportunity]**

I det här scenariot har kunden valt att spåra **MQL** och **SAL-faser** med boomerang-kontaktytor. SQL-scenen spåras av standardstadierna.

![](assets/4.png)

FT- och LC-kontaktytorna på affärsmöjligheten kommer från Lead 1 (blå) eftersom de inträffade före FT och LC för Lead 2 (rosa). LC-kontaktytan för Lead 2 visas som en &#39;Form&#39;-kontaktyta i säljprojektet.

MQL-01 (sista) från Lead 2 blir den första MQL för affärsmöjligheten. MQL-01 från Lead 1 visas inte som kontaktyta för säljprojektet eftersom Lead 2:s MQL inträffade först. Lead 1:s MQL-02 och MQL-03 visas dock i säljprojektet.

Observera att SQL-scenen spåras med anpassade stadier, inte boomerang-stadier. Även om det finns tre förekomster av SQL-steget mellan Lead 1 och Lead 2 inkluderas bara den sista SQL-förekomsten som kontaktyta i säljprojektet.

SAL-01-kontaktytan (sista) från lead 1 överförs som kontaktyta för affärsmöjligheten. Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson. SAL-01-kontaktytan för lead 2 (sista) skapas som kontaktyta eftersom den här scenövergången inträffade _efter_ OC-kontakten.

3:s FT-, LC- och MQL-, SQL-, SAL-kontaktytor (orange) inträffade alla efter OC-kontaktytan i säljprojektet. Dessa kontaktytor kommer att ingå i säljprojektet, men betraktas som&quot;medelkontaktytor&quot;.

När lead 2 och 3 konverteras till kontakter, [!DNL Marketo Measure] kommer inte att skapa en ny OC-kontaktyta eftersom det bara kan finnas en enda fas där affärsmöjligheten skapas.

**Scenario 2 -[!UICONTROL Three Leads with Opportunity]**

I det här scenariot har kunden valt att spåra **MQL**, **SQL** och **SAL** scener med boomerang-kontaktytor.

Alla kontaktytor från Lead 1 inkluderas i affärsmöjligheten, från FT till SAL-01 (Last). LC-kontaktytan från Lead 2 kommer att ingå som en kontaktyta mellan LC- och MQL-01-kontaktytorna på affärsmöjligheten.

![](assets/5.png)

MQL-01 (sista) från lead 2 blir till slut MQL-04 (sista)-kontaktytan för affärsmöjligheten. Eftersom det här scenariot handlar om flera Leads resor inom ett säljprojekt kan positioneringen och numreringen av Leads kontaktytor ändras när de översätts som kontaktytor i säljprojektet. På samma sätt blir SQL-01 (sista) från Lead 2 SQL-04 (sista) på Opp. Lead 2’s SAL-01 (Last) blir också säljprojektets SAL-02 (Last).

Lägg även märke till att det endast finns två SAL-kontaktytor i säljprojektet. [!DNL Marketo Measure] kommer inte att försöka tvinga/skapa kontaktytor för scenövergångar om de inte faktiskt har inträffat.

Lead 3:s kontaktpunktsresa börjar precis innan OC-beröringen sker, men långt efter att Lead 1 och Lead 2 haft sin FT- och LC-beröring. I det här fallet visas FT och LC för lead 3 som en kontaktyta för säljprojektet. Lead 1 konverteras sedan till en kontakt med ett säljprojekt, vilket anses vara en kontaktperson.

MQL-, SQL- och SAL-kontakterna för lead 3 sker samtidigt, efter OC-beröringen. Eftersom de inträffade efter OC-kontaktytan visas den här kontaktytan som en Form/Middle Touch på säljprojektet i stället för som en övergång på Boomerang-scenen.

**Scenario 2a - Webbbesök Boomerang Touchpoints**

I det här scenariot har kunden valt att spåra **MQL**, **SQL** och **SAL** scener med boomerang-kontaktytor. Detta scenario är nästan identiskt med det ovanstående, med några få undantag.

![](assets/6.png)

Alla kontaktytor från Lead 1 inkluderas i affärsmöjligheten, från FT till SAL-01 (Last). LC-kontaktytan från Lead 2 kommer att ingå som en kontaktyta mellan LC- och MQL-01-kontaktytorna på affärsmöjligheten.

Lead 2&#39;s MQL-01 (Last) (Web Visit) kommer inte att skapas som kontaktyta på Opp. Detta beror på att denna kontaktyta var ett webbbesök som inträffar efter den sista förekomsten av SQL-steget och inte bidrar till att driva säljprojektet framåt.

Lead 1 ändras till SAL och konverteras sedan till en kontakt med ett säljprojekt. I det här fallet kommer SAL-01 (sista) och OC-positionen att kombineras i samma kontaktyta.

Fort 3:s FT, LC touch kommer att skapas som en kontaktyta i form på Opp. Endast formulärfyllningsåtgärder skapas som kontaktytor efter OC-beröringen. Av den anledningen skapas inte övergångarna SQL-01 (senaste) och SAL-01 (sista) för lead två som kontaktytor eftersom dessa kontaktytor var webbbesök.

Lead 3&#39;s MQL, SQL, SAL Touches will be included as a touchpoint because this was a form fill action.

**Scenario 3 - Boomerang Attribution Weighting**

I det här scenariot har kunden valt att spåra **MQL**, **SQL** och **SAL** scener med boomerang-kontaktytor.

![](assets/7.png)

FT- och LC-kontaktytorna på affärsmöjligheten kommer från Lead 1 (blå) eftersom de inträffade före FT och LC för Lead 2 (rosa). LC-kontaktytan för Lead 2 visas som en &#39;Form&#39;-kontaktyta i säljprojektet.

MQL-01 (sista) från Lead 2 blir den första MQL för affärsmöjligheten. MQL-01 från Lead 1 visas inte som kontaktyta för säljprojektet eftersom Lead 2:s MQL inträffade först.

SQL-01 (sista) från Lead 2 blir SQL-01 i säljprojektet. SQL-01 på Lead 1 visas inte som kontaktyta för affärsmöjligheten eftersom SQL-01 på Lead 2 inträffade först.

Observera att Lead 1-boomerangerna mellan MQL och SQL några gånger innan de äntligen når SAL-stadiet. SQL-01, MQL-02, SQL-02, MQL-03, SQL-03 _inte_ tas med som kontaktytor på affärsmöjligheten eftersom dessa övergångar inte bidrar till att driva fram möjligheten under resan.

Slutpunkten för SAL-01 (sista) från Lead 1 blir nästa kontaktyta som ska ingå i Opp. Lead 1 konverteras sedan till en kontakt med en möjlighet, vilket skapar en OC-kontaktyta.

FT- och LC för lead 3 samt MQL-, SQL- och SAL-kontaktytan visas som en kontaktyta i säljprojektet.

SQL-01-kontaktytan för lead 2 (sista) inkluderas inte som en kontaktyta på Opp eftersom den inträffade efter OC-kontaktytan. Dessutom har övergång till SQL-fasen för lead 2 skett _efter den slutliga övergången till SAL-stadiet_, och hjälper inte till att driva affärsmöjligheterna framåt.

## Scenarier om affärsmöjligheter {#opportunity-scenarios}

**Scenario 1 - kontakter med säljprojekt och Boomerang-spårning**

I det här scenariot har kunden valt att spåra **Demo- och förhandlingsfasövergångar** på **Kontakt**. Varje boomerang-scen kan ta emot upp till två kontaktytor. Skillnaden mellan scenövergångar för en kontakt- och scenövergång på en lead är att kontaktfasövergångar kan visas som Boomerang-kontaktytor i säljprojektet _efter_ OC-kontaktytan. Detta gäller inte för scenövergångar som förekommer på leadet eftersom dessa kommer att visas som en kontaktyta i form.

![](assets/8.png)

I det här exemplet ingår Demo- och förhandlingsfasövergångarna för Contact 1 som Demo-01- och Negotiation-01-kontaktytor i säljprojektet. Kontakt 2 har en övergång till Demo-scenen _efter_ Kontakt 1 och visas som Demo-02-kontaktyta (sista) i säljprojektet.

Observera att det inte finns en andra övergång till förhandlingsfasen. Möjligheten går omedelbart från Demo-02 (sista) till Close Won. I detta fall [!DNL Marketo Measure] kommer att inkludera förhandlingsövergången med sluten Won-kontaktyta.
