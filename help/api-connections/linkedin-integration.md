---
description: LinkedIn Integration Guide för Marketo Measure-användare
title: LinkedIn-integrering
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
feature: APIs, Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '2694'
ht-degree: 0%

---

# LinkedIn-integrering {#linkedin-integration}

## Översikt {#overview}

Integreringen av [!DNL Marketo Measure] med LinkedIn består av två delar:

Sponsrat innehåll: Integreringen av sponsrat innehåll gör att [!DNL Marketo Measure] kan tagga mål-URL:er på [!DNL LinkedIn] annonser, vilket gör att [!DNL Marketo Measure] kan följa en användare genom hela deras kontaktyta och mappa aktiviteten tillbaka till den specifika [!DNL LinkedIn] Campaign och Creative. Detta ger kunderna insikter om avkastningen på deras [!DNL LinkedIn]-aktivitet.

Lead Gen Forms: Genom integrationen med LinkedIn&#39;s Lead Gen Forms får Marketo Measure insikt i formulär som har skickats via LinkedIn-plattformen. Dessa formulärfyllningar matchas mot leads från CRM- eller [!DNL Marketo Engage]-instansen så att de är berättigade till attribuering. Med insikt i Campaign, Creative och Form som bidrog till att generera formulären kan team nu optimera sina utgifter för LinkedIn-marknadsföring och -annonser ytterligare.

## Tillgänglighet {#availability}

Tillgängligt för alla användare.

## Krav {#requirements}

### Roller för Campaign Manager

För att [!DNL Marketo Measure] ska kunna hämta kostnadsdata för annonser och annonser måste du ha en av följande roller i Campaign Manager:

* Faktureringsadministratör
* Account Manager
* Campaign Manager

Läs mer: [Användarroller och -funktioner i Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

### Roller för betald medieadministratör

För att [!DNL Marketo Measure] ska kunna skapa/uppdatera sponsrade Creative-objekt måste du ha någon av följande roller för betald mediaadministratör:

* Sponsrat Content Poster
* Lead Gen Forms Manager

Läs mer: [LinkedIn Page Admin Roles](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Det finns andra [!DNL LinkedIn]-roller som vi **inte** behöver för vår integrering. De här rollerna är ofta felaktiga för de roller som krävs, så observera att det är en skillnad!

### Roller för sidadministration

För att [!DNL Marketo Measure] ska kunna hämta/integrera leads från lead-genereringsformulär måste du ha följande roll för sidadministration:

* Superadministratör

Läs mer: [LinkedIn Page Admin Roles](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## LinkedIn-annonstyper {#linkedin-ad-types}

[!DNL Marketo Measure] kommer att stödja:

Sponsrat innehåll gör att du kan leverera innehåll till [!DNL LinkedIn]-flödet med medlemmar utöver de som följer ditt företag. Sponsrat innehåll kan riktas mot en viss målgrupp och kan hjälpa annonsörer att nå [!DNL LinkedIn]-medlemmar oavsett var och när de interagerar på [!DNL LinkedIn]-plattformen på datorn, mobilen och surfplattan. Sponsrat innehåll med Lead Gen Forms stöds.

De typer av annonsformat för sponsrat innehåll som stöds av [!DNL Marketo Measure] är Single Image Ads och Video Ads (via Lead Gen Forms). På grund av schemats komplexitet stöder vi inte Carousel-annonser.

[!DNL Marketo Measure] stöder inte Sponsored Messaging, Text Ads eller Dynamic Ads.

![Marketo Measure stöder inte Sponsored Messaging, Text Ads eller Dynamic](assets/bizible-guide-1.png)

>[!TIP]
>
>För alla kampanjer/utgifter som kommer från en icke-finansierad innehållskälla (till exempel Campaign-typen &quot;Text Ad&quot; eller &quot;Sponsored InMail&quot;), stöder [!DNL Marketo Measure] _inte_ i sig spårning av dessa kampanjtyper. Om du vill spåra utgifter för kampanjer som dessa tillsammans med dina&quot;Sponsored Content&quot;-utgifter måste du använda vår Marketing Spend CSV för att manuellt logga dessa utgifter.

## Så här fungerar det: Sponsrat innehåll {#how-it-works-sponsored-content}

>[!NOTE]
>
>Den här funktionsinställningen måste aktiveras innan du kan använda den första gången genom att gå till [!DNL Marketo Measure] [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Ads] > [!UICONTROL Enable LinkedIn Lead Gen Forms].

### [!DNL LinkedIn's] unika krav för automatisk taggning

[!DNL Marketo Measure] kan hjälpa dig att spåra din [!DNL LinkedIn]-kampanjprestanda genom att tagga dina landningssidor automatiskt.

[!DNL Marketo Measure] söker efter kreatörer med en unik LinkedIn-resurs och lägger till en `?_bl={creativeId}`-parameter i slutet av den.

### Kopierar resurser

Med den här [!DNL Marketo Measure/LinkedIn]-integreringen frågar vi om kunderna inte kopierar/klonar/duplicerar befintliga Creative-objekt. Om resurser hittas och bara används på en Creative kan [!DNL Marketo Measure] tagga delningen som den är utan att behöva återskapa några Creative- eller Shares-objekt och all annonshistorik (visningar, klickningar, delningar) finns kvar.

Så snart en resurs har delats av flera Creative-medlemmar måste [!DNL Marketo Measure] utföra en paus, kopiering och omtaggning för att skapa en unik uppsättning. [!DNL Marketo Measure] pausar och arkiverar aktiva kreatörer och raderar därför annonshistorik, inklusive visningar, klickningar och sociala resurser, för att tagga allt automatiskt.

Om du går framåt rekommenderar [!DNL Marketo Measure] att du inte duplicerar några [!DNL LinkedIn]-resurser och behåller alla kreativa och delade resurser så unika som möjligt så att vi enkelt kan lägga till vår spårning utan att behöva radera annonshistoriken.

### Förkortade URL:er

Orsaken till det extra steget är att LinkedIn tillåter att mål-URL:er är en förkortad URL (bit.ly, goog.le osv.), vilket innebär att [!DNL Marketo Measure] inte kan se den långa, lösta URL:en och [!DNL Marketo Measure] måste lägga till spårningsparametrar i en matchad URL. För att komma runt det problemet letar [!DNL Marketo Measure] efter förkortade URL:er innan en annons återskapas, expanderar URL:en, skapar sedan den nya annonsen med den matchade URL:en och alla dess parametrar så att [!DNL Marketo Measure] kan lägga till taggar. Om du skapar en ny annons raderas annonshistoriken (visningar, klickningar, delningar), vilket innebär att du måste ha behörighet att tagga förkortade URL:er.

Om du använder förkortade URL:er i stor utsträckning kan detta få allvarliga konsekvenser för dina kreatörer. Vi rekommenderar att du inte längre använder förkortade URL:er så att [!DNL Marketo Measure] kan tagga landningssidorna utan att behöva skapa nya annonser och radera annonshistorik.

### Processen

Låt oss börja med några exempel. Säg att vi har...

Creative A: Share 123\
Creative B: Share 234\
Creative C: Share 234\
Creative D: Share 234

![Creative D : Share 234](../assets/marketo-engage-activities-05.png)

`1)` [!DNL Marketo Measure] kommer först att genomsöka alla kampanjer, kreativa aktiviteter och resurser med statusen Aktiv. [!DNL Marketo Measure] taggar inte pausade, arkiverade eller annullerade annonser. Om en annons pausades och sedan anges till [!UICONTROL active] taggas den när den är aktiv igen. Om vi kan hitta en unik resurs, vilket innebär att den inte används i flera olika Creative-program eller kampanjer (t.ex. Creative A: Dela 123), lägger [!DNL Marketo Measure] till den anpassade parametern `>> ?_bl={creativeId}` i delnings-URL:en.

`2)` Om resursen har delats och blivit mindre unik (till exempel Creative B: Dela 234 och Creative C: Dela 234 och Creative D: Dela 234) pausar och arkiverar [!DNL Marketo Measure] alla liknande projekt (som Creative B, Creative C och Creative D).

`3)` [!DNL Marketo Measure] skapar tre nya kreatörer, Creative E, Creative F och Creative G, som kopierar innehållet i Creative B, som arkiveras.

`4)` [!DNL Marketo Measure] skapar också tre nya resurser, Share 345, Share 456 och Share 567, som kopierar innehållet i Share 234, förutom att det har en egen unik `?_bl` -taggning.

`5)` [!DNL Marketo Measure] måste regelbundet kontrollera att resurser inte delas och om de gör det kommer vi att starta om processen i steg 2 ovan.

>[!NOTE]
>
>Om vi implementerar detta kommer våra kunder att förlora annonshistoriken för Creative B: Share 234, Creative C: Share 234 och Creative D: Share 234 eftersom det nu återskapas med Creative E: Share 345, Share F: Share 456 och Creative G: Share 567.

![Om du implementerar det här innebär det att våra kunder förlorar annonshistoriken](assets/api-connections-01.png)

## Så här fungerar det: Lead Gen Forms {#how-it-works-lead-gen-forms}

[!DNL Marketo Measure] kan hjälpa dig att spåra din [!DNL LinkedIn]-kampanjprestanda genom att tagga dina landningssidor automatiskt.

[!DNL Marketo Measure] söker efter kreatörer med en unik LinkedIn-resurs och lägger till en `?_bl={creativeId}`-parameter i slutet av den.

Genom [!DNL LinkedIn's] API:t för annonseringsformulär och API:t för formulärsvar kan vi samla in formuläröverföringsdata för ett annonskonto och koppla e-postadressen till ett lead från CRM eller Marketo.

LinkedIn-formulär kan innehålla flera e-postadresser. När vi hämtar formulärsvar letar vi efter e-postadresser med följande prioritet: E-postadress (arbete), e-postadress (primärt formulärfält) eller anpassade fält med ett giltigt e-postvärde.

Oavsett status för Campaign eller Creative resulterar alla formulärsvar i en kontaktyta. [!DNL Marketo Measure] har en 90-dagars uppslagsbegränsning, så [!DNL Marketo Measure] kan inte komma åt formulärsvar som är äldre än 90 dagar, men ju längre [!DNL Marketo Measure] - och [!DNL LinkedIn]-integreringen är aktiverad, desto fler Lead Gen-kontaktytor visas via [!DNL Marketo Measure].

>[!NOTE]
>
>LinkedIn-kostnader hämtas fortfarande som en del av Sponsored Content Campaigns.


Innan [!DNL Marketo Measure] och LinkedIn Lead Gen Forms Integration fanns var det vanligt att kunderna skickade in formulär till ett Marketo-program och/eller CRM Campaign för att spåra formulären och få attribuering för dessa aktiviteter. När inställningen Lead Gen Forms är aktiverad vill vi se till att dessa formulärinskickade formulär inte räknas två gånger. Kontrollera följande:

* Fältet Aktivera slutpunkter för köpare i CRM-objektet är inställt på Ingen eller Exkludera alla kampanjmedlemmar
* Uppdatera alla relaterade aktivitetsregler för Marketo eller Marketo
* Uppdatera alla relaterade CRM-kampanjregler

>[!NOTE]
>
>LinkedIn API har en 90-dagars uppslagsbegränsning, så om du använder Marketo- eller CRM-regler bör du ange slutdatumet för regeln till 90 dagar före det datum då du aktiverade integreringen i [!DNL Marketo Measure].

## Kontaktpunktsinformation {#touchpoint-details}

När [!DNL Marketo Measure] har taggat din landningssida på LinkedIn-kreativiteten kan du visa lösta annonser på kontaktytan. Här är mappningen av datavärden som du kan förvänta dig att se:

<table>
 <colgroup>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th style="width:30%">Touchpoint-fält</th>
   <th>Exempelvärde</th>
  </tr>
  <tr>
   <td>Annons-ID</td>
   <td>84186224</td>
  </tr>
  <tr>
   <td>Annonsinnehåll</td>
   <td>95 % av marknadsförarna på #B2B anser att strategin för att skapa efterfrågan är framgångsrik. Läs mer: [!DNL https]://lnkd.in/jgdi50vKrgv</td>
  </tr>
  <tr>
   <td>Annonsgrupp-ID</td>
   <td>(tom)</td>
  </tr>
  <tr>
   <td>Namn på annonsgrupp</td>
   <td>(tom)</td>
  </tr>
  <tr>
   <td>ID för annonskampanj</td>
   <td>138949954</td>
  </tr>
  <tr>
   <td>Namn på annonskampanj</td>
   <td>SU - COM Accounts - Demand Skills</td>
  </tr>
  <tr>
   <td>Publicera mål-URL <b>*</b></td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td>
  </tr>
  <tr>
   <td>Formulär-URL</td>
   <td>info.bizible.com/demo</td>
  </tr>
  <tr>
   <td>Formulär-URL - Raw</td>
   <td>info.bizible.com/demo</td>
  </tr>
  <tr>
   <td>Nyckelords-ID</td>
   <td>(tom)</td>
  </tr>
  <tr>
   <td>Matchningstyp för nyckelord</td>
   <td>(tom)</td>
  </tr>
  <tr>
   <td>Landningssida</td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders</td>
  </tr>
  <tr>
   <td>Landningssida - Raw</td>
   <td>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217</td>
  </tr>
  <tr>
   <td>Marknadsföringskanal</td>
   <td>Betald social</td>
  </tr>
  <tr>
   <td>Marknadsföringskanal - sökväg</td>
   <td>Betald social.LinkedIn</td>
  </tr>
  <tr>
   <td>Medium</td>
   <td>"cpc" eller "Lead Gen Form"</td>
  </tr>
  <tr>
   <td>Referentsida</td>
   <td>www.linkedin.com/</td>
  </tr>
  <tr>
   <td>Referenssida - Raw</td>
   <td>www.linkedin.com/</td>
  </tr>
  <tr>
   <td>Sökfras</td>
   <td>(tom)</td>
  </tr>
  <tr>
   <td>Kontaktpunktstyp</td>
   <td>Webbformulär</td>
  </tr>
  <tr>
   <td>Touchpoint Source</td>
   <td>LinkedIn</td>
  </tr>
 </tbody>
</table>

Fältet **&#42;** _&quot;Webbadress för annonsmål&quot; är bara ifyllt för Sponsrat innehåll. Den har inte fyllts i för Lead Gen Forms._

<br>

## Kostnader {#costs}

Eftersom [!DNL Marketo Measure] är direkt integrerat med [!DNL LinkedIn] hämtar vi de inspelade utgifterna för varje Campaign och Creative varje dag. En kund behöver inte längre rapportera om [!DNL LinkedIn] utgifter i [!DNL Marketo Measure]-programmet.

Precis som med andra annonseringsintegreringar har [!DNL Marketo Measure] definierat en regel för marknadsföringskanaler för att placera alla [!DNL LinkedIn]-kampanjer, kreativa aktiviteter och kostnader. För att kunna använda regeln måste kunden infoga en ny rad för sina [!DNL LinkedIn]-insatser. Det kan vara en ny eller befintlig kanal. I kolumnen Referens använder du definitionen &quot;[[!DNL LinkedIn] Betald]&quot; som [!DNL Marketo Measure] har definierat som en kontaktyta med en [!DNL Marketo Measure] -tagg.

![Precis som med andra annonsintegreringar har Marketo Measure definierat en marknadsföring](../assets/marketo-engage-activities-01.png)

## [!DNL Marketo Measure] Upptäck {#marketo-measure-discover}

Vissa förbättringar har gjorts i [!DNL Marketo Measure] Discover för att stödja Lead Gen Forms-rapportering.

**Betalat mediakort**

Lead Gen Forms-platta: Ny platta som innehåller antalet LinkedIn-formulärfyllningar. Granska av det här antalet visar Aktivitets-ID, Formulärdatum, Formulärnamn och E-postadress.

**Förlovningsanslagstavla**

Events-resa: Innehåller händelsetypen &quot;Activity&quot; och mediet &quot;Lead Gen Form&quot; för formulär som kommer igenom integreringen. Detaljerad översikt innehåller information om Campaign, Creative och Form.

## Vanliga frågor om sponsrat innehåll {#sponsored-content-faq}

**Vad är en mörk resurs?**

En mörk aktie är ett inlägg där det aldrig publiceras på företagets sida och omedelbart skapas och läggs till direkt som Creative. Så att [!DNL Marketo Measure] skapade kreatörer inte visas överst på en företagssida och framhävs igen, används mörka delningar så att de kan visas bakom kulisserna.

**Vilka statusvärden taggar [!DNL Marketo Measure] egentligen?**

Det finns fyra olika statusvärden för en [!DNL LinkedIn]-kampanj och Creative: Aktiv, Pausad, Arkiverad och Avbruten. Vi taggar bara aktiva kampanjer och kreatörer. Om du taggar andra statusar anges de som Aktiv igen. [!DNL Marketo Measure] kommer inte att tagga Pausade, Arkiverade eller Avbrutna kampanjer eller Creative-program, men fortsätter taggen om statusen ändras till Aktiv.

**Vad är värdet som [!DNL Marketo Measure] använder för att tagga?**

I slutet av mål-URL:en lägger [!DNL Marketo Measure] till parametern `&_bl={creativeId}`, där `{creativeId}` är Creative-ID:t från LinkedIn. Med Creative-id:t kan [!DNL Marketo Measure] även fastställa kampanj-ID:t eftersom [!DNL LinkedIn] har en ganska grundläggande annonseringsstruktur eftersom varje Creative bara kan tillhöra en kampanj.

**Vad händer med min gamla kreatör när [!DNL Marketo Measure] skapar en ny version av den?**

När [!DNL Marketo Measure] återskapar en resurs och placerar den i en ny Creative arkiveras den gamla Creative. Detta är också orsaken till att [!DNL Marketo Measure] inte taggar arkiverade kampanjer eller kreatörer. Annars skulle [!DNL Marketo Measure] göra en slinga och försöka tagga det i oändlighet.

**Varför matchar inte den skapade annonsens mål-URL min ursprungliga annons?**

[!DNL Marketo Measure] måste lägga till spårningsparametrarna i en matchad URL, men URL:en som presenteras i API:t kan vara en förkortad URL utan att det finns några parametrar. För att komma runt det problemet letar [!DNL Marketo Measure] efter förkortade URL:er innan ett tillägg återskapas, löser det och skapar sedan den nya annonsen med den matchade URL:en och alla dess parametrar så att [!DNL Marketo Measure] kan lägga till taggar.

**Taggar du alla mina annonser? Kan jag inte se bl-parametern på alla mina landningssidor?**

Vi har observerat att vissa marknadsförare placerar en bildlänk i mål-URL:en, som [!DNL Marketo Measure] inte kan tagga, så vi söker efter URL:en i annonsinnehållet. Om [!DNL Marketo Measure] har behörighet att tagga förkortade URL:er utökar vi URL:en och taggen som, men på grund av LinkedIn:s kopieringsstruktur, förkortas den automatiskt i texten. Taggen finns i den förkortade URL:en för LinkedIn, som visas i kontaktpunktens fält för annonsinnehåll i stället för i fältet Landningssida - Raw.

**Åh nej, någon i mitt team råkade klona en del. Kan jag pausa den?**

Inga bekymmer. [!DNL Marketo Measure] söker efter resurser som inte längre är unika, vilket innebär att de sedan dess har kopierats till en annan Creative. När kopian har identifierats följer [!DNL Marketo Measure] det vanliga flödet för att tagga och skapa nya annonser.

**Min annons väntar på granskning tidigare. Varför väntar den på granskning igen efter att [!DNL Marketo Measure] har taggat den?**

LinkedIn kräver att alla annonser som skapas eller ändras genomgår den normala säkerhetsprocessen innan den publiceras. [!DNL Marketo Measure] försöker fånga annonsen så snabbt som möjligt, eftersom den söker efter nya annonser var sjätte timme, men med ytterligare [!DNL LinkedIn's] steg kan det fördröja lanseringen med några timmar.

**Det finns två URL:er i min annons. Vilken taggas?**

Båda. Integrationen [!DNL Marketo Measure] gör att vi kan tagga mål-URL:en från klickbilden i annonsen, men den förkortade URL:en i annonsbeskrivningen uppdateras automatiskt.

![Båda. Tack vare Marketo Measure-integreringen kan vi tagga målet ](assets/select-type-1.png)

**Jag har anslutit mitt [!DNL LinkedIn ads]-konto. Varför taggar inte [!DNL Marketo Measure] mina länkar?**

Den anslutna [!DNL LinkedIn]-användaren måste ha rätt redigeringsåtkomst, vilket innebär att användaren måste vara en Account Manager, Campaign Manager eller Creative Manager.

**Hur vet jag om min kreativitet kommer att kopieras? Kan jag se om mina kreatörer använder samma resurs?**

Resurs-ID:t anges inte i en [!DNL LinkedIn]-rapport, så det finns inget tydligt och tydligt sätt att söka efter mappningar av typen creative-to-share. Om du misstänker att en kreatör kan vara en kopia kan du kontrollera manuellt genom att öppna annonsen i din [!DNL LinkedIn] Campaign Manager. Detta öppnar annonsen på en ny flik och du hittar resurs-ID:t i URL:en.

![Resurs-ID:t finns inte i en LinkedIn-rapport, så](assets/linkedin-integration-02.png)

## Lead Gen Forms - frågor och svar {#lead-gen-forms-faq}

**Vad kostar den här förbättringen?**

Det här erbjudandet ingår i alla betalda [!DNL Marketo Measure]-prenumerationer.

**Är integreringen retroaktiv?**

Ja, vi hämtar historiska annonseringssvar från LinkedIn, men vi är begränsade till 90-dagars uppslagsfönstret. Ju längre integreringen av [!DNL Marketo Measure] och LinkedIn är aktiverad, desto fler kontaktytor för Lead Gen-formulär visas via [!DNL Marketo Measure].

Det finns inget alternativ för att ange ett specifikt datum för hämtning, men du kan också ange regler för borttagning av pekpunkter om det finns kontaktpunkter som du behöver inaktivera.

**Kommer detta att aktiveras automatiskt om jag redan använder [!DNL Marketo Measure] LinkedIn-annonsintegreringen?**

Nej, vi börjar inte automatiskt ladda ned den för alla kunder, men det är en mycket enkel övergång för att aktivera den här funktionen i inställningarna.

**Är formulärdata tillgängliga?**

Formulärdata är tillgängliga via [!DNL Marketo Measure] Identifiera inklusive formulär-ID och formulärnamn. Formulärinformationen är ännu inte tillgänglig för kontaktobjekten i CRM.

**Vad händer med [!DNL LinkedIn] leads som tidigare har synkroniserats med Marketo-program eller CRM-kampanjer?**

Vi rekommenderar att du justerar alla [!DNL Marketo Measure]-regler för att generera kontaktytor från dessa specifika program eller kampanjer för att undvika dubbletter. LinkedIn API har en 90-dagars uppslagsbegränsning, så om du använder Marketo- eller CRM-regler bör du ange slutdatumet för regeln till 90 dagar före det datum då du aktiverade integreringen i [!DNL Marketo Measure]. Från och med den här punkten kan [!DNL Marketo Measure] hämta dessa leads med större insikter och information.

**Finns det någon automatisk taggning eller spårning?**

Nej, det här skiljer sig från andra [!DNL Marketo Measure]-integreringar. I stället för att ändra landningssidan (eftersom det inte finns något klick genom landningssidan) hämtar vi bara relevant information från LinkedIn och behandlar dem som aktiviteter i [!DNL Marketo Measure].
