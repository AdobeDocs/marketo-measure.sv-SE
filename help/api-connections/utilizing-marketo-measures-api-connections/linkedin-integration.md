---
unique-page-id: 35586080
description: linkedIn Integration - [!DNL Marketo Measure] - Produktdokumentation
title: linkedIn Integration
exl-id: 705209ef-1ece-496c-ac2f-6a31055bd993
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '2594'
ht-degree: 0%

---

# linkedIn Integration {#linkedin-integration}

## Översikt {#overview}

The [!DNL Marketo Measure] integrering med LinkedIn finns i två delar:

Sponsrat innehåll: Integreringen med Sponsrat innehåll tillåter [!DNL Marketo Measure] att tagga mål-URL:er på [!DNL LinkedIn] annonser, som i slutänden tillåter [!DNL Marketo Measure] för att följa en användare genom hela deras kontaktyta och kartlägga aktiviteten tillbaka till den specifika [!DNL LinkedIn] Campaign och Creative. Detta ger kunderna insikter om avkastningen på deras [!DNL LinkedIn] aktivitet.

Lead Gen Forms: Genom integrationen med LinkedIn Lead Gen Forms får Marketo Measurement insikt i formulär som skickats in via LinkedIn. Dessa formulärfyllningar matchas mot leads från CRM eller [!DNL Marketo Engage] så att de är berättigade till attribuering. Med insikt i den kampanj, det kreativa och det formulär som bidrog till att generera formulären kan team nu optimera sina utgifter för marknadsföring och annonsering i LinkedIn ytterligare.

## Tillgänglighet {#availability}

Tillgängligt för alla kunder.

## Krav {#requirements}

**Roller för Campaign Manager**

För [!DNL Marketo Measure] För att kunna hämta kostnadsdata för annonser och annonser måste du ha en av följande roller i Campaign Manager:

* Faktureringsadministratör
* Account Manager
* Campaign Manager

Läs mer: [Användarroller och -funktioner i Campaign Manager](https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager).

**Roller för betald medieadministratör**

För [!DNL Marketo Measure] För att kunna skapa/uppdatera sponsrade kreatörer måste du ha någon av följande roller för betald mediaadministratör:

* Sponsrat Content Poster
* Lead Gen Forms Manager

Läs mer: [Roller för linkedIn-sidadministration](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

Det finns andra [!DNL LinkedIn] roller som vi gör **not** kräver vår integrering. De här rollerna är ofta felaktiga för de roller som krävs, så observera att det är en skillnad!

**Roller för sidadministration**

För [!DNL Marketo Measure] Om du vill kunna hämta/integrera leads från formulär för lead-generering måste du ha följande sidadministratörsroll:

* Superadministratör

Läs mer: [Roller för linkedIn-sidadministration](https://www.linkedin.com/help/linkedin/answer/4783/linkedin-page-admin-roles-overview).

## linkedIn annonstyper {#linkedin-ad-types}

[!DNL Marketo Measure] kommer att stödja:

**Sponsrat innehåll:** Sponsrat innehåll gör det möjligt att leverera innehåll till [!DNL LinkedIn] för medlemmar utöver dem som följer ert företag. Sponsrat innehåll kan riktas till en viss målgrupp och kan hjälpa annonsörerna att nå ut [!DNL LinkedIn] medlemmar oavsett var och när de engagerar sig i [!DNL LinkedIn] på datorer, mobiler och surfplattor. Sponsrat innehåll med Lead Gen Forms stöds.

De typer av annonsformat för sponsrat innehåll som stöds av [!DNL Marketo Measure] är Single Image Ads och Video Ads (via Lead Gen Forms). På grund av schemats komplexitet stöder vi inte Carousel-annonser.

[!DNL Marketo Measure] stöder inte Sponsored Messaging, Text Ads eller Dynamic Ads.

![](assets/one.png)

>[!TIP]
>
>För alla era kampanjer/utgifter som kommer från en icke-sponsrad innehållskälla (t.ex. kampanjtypen &quot;Text Ad&quot; eller &quot;Sponsored InMail&quot;), [!DNL Marketo Measure] gör _not_ har stöd för spårning av dessa kampanjtyper. Om du vill spåra utgifter för kampanjer som dessa tillsammans med dina&quot;Sponsored Content&quot;-utgifter måste du använda vår Marketing Spend CSV för att manuellt logga dessa utgifter.

## Så här fungerar det: Sponsrat innehåll {#how-it-works-sponsored-content}

>[!NOTE]
>
>Innan den första användningen måste den här funktionsinställningen aktiveras genom att du går till [!DNL Marketo Measure] [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Ads] > [!UICONTROL Enable LinkedIn Lead Gen Forms].

**[!DNL LinkedIn's]Unika krav för automatisk taggning**

[!DNL Marketo Measure] kan hjälpa dig att spåra [!DNL LinkedIn] kampanjresultat genom att automatiskt tagga era landningssidor.

[!DNL Marketo Measure] söker du efter kreatörer med en unik LinkedIn Share och lägger till en `?_bl={creativeId}` till slutet av den.

**Kopierar resurser**

Med det här [!DNL Marketo Measure/LinkedIn] Integration innebär att kunderna inte får kopiera, klona eller duplicera befintliga kreatörer. Om aktier hittas och endast kan användas på en Creative-medlem, [!DNL Marketo Measure] Du kan tagga webbgalleriet som det är utan att behöva återskapa några Creative- eller Shares-objekt och all annonshistorik (visningar, klickningar, delningar) finns kvar.

Så snart en resurs har visats vara delad mellan flera olika kreatörer, [!DNL Marketo Measure] måste gå igenom en process för att pausa, kopiera och tagga om för att skapa en unik uppsättning. [!DNL Marketo Measure] pausar och arkiverar aktiva kreatörer och raderar därför annonshistorik, inklusive visningar, klickningar och sociala resurser, för att tagga allt automatiskt.

Framåt, [!DNL Marketo Measure] rekommenderar att du inte duplicerar några [!DNL LinkedIn] Dela och behåll alla kreatörer och delningar så unika som möjligt så att vi enkelt kan lägga till vår spårning utan att behöva radera annonsberättelsen.

**Förkortade URL:er**

Orsaken till det extra steget är att LinkedIn tillåter att mål-URL:er är en förkortad URL (bit.ly, goog.le osv.), vilket betyder [!DNL Marketo Measure] inte ser den långa, lösta URL:en och [!DNL Marketo Measure] måste lägga till spårningsparametrar till en matchad URL. För att komma runt den frågan [!DNL Marketo Measure] söker efter förkortade URL:er innan en annons återskapas, expanderar URL:en, skapar sedan den nya annonsen med den matchade URL:en och alla dess parametrar, vilket [!DNL Marketo Measure] om du vill lägga till taggar. Om du skapar en ny annons raderas annonshistoriken (visningar, klickningar, delningar), vilket innebär att du måste ha behörighet att tagga förkortade URL:er.

Om du använder förkortade URL:er i stor utsträckning kan detta få allvarliga konsekvenser för dina kreatörer. Vi rekommenderar att du inte längre använder förkortade URL:er så att [!DNL Marketo Measure] kan tagga landningssidorna utan att behöva skapa nya annonser och radera annonshistorik.

**Processen**

Låt oss börja med några exempel. Säg att vi har....

Creative A: Dela 123\
Kreativ B: Dela 234\
Creative C: Dela 234\
Creative D: Dela 234

![](assets/two.png)

`1)` [!DNL Marketo Measure] kommer först att undersöka alla kampanjer, kreatörer och aktiekurser med statusen&quot;Aktiv&quot;. [!DNL Marketo Measure] kommer inte att tagga pausade, arkiverade eller annullerade annonser. Om en annons har pausats anges den till [!UICONTROL active]märker vi det när det är aktivt igen. Om vi kan hitta en unik resurs, vilket betyder att den inte används i flera olika kreativa eller kampanjskapande program (t.ex. Creative A: Dela 123), [!DNL Marketo Measure] lägger till vår anpassade parameter `>> ?_bl={creativeId}` till delnings-URL:en.

`2)` Om resursen har delats och blivit mindre unik (till exempel Creative B: Dela 234 och Creative CC: Dela 234 och Creative D: Andel 234), [!DNL Marketo Measure] kommer att pausa och arkivera alla liknande kreatörer (som skulle vara Creative B, Creative C och Creative D).

`3)` [!DNL Marketo Measure] kommer att skapa tre nya kreatörer, Creative E, Creative F och Creative G, som kopierar innehållet i Creative B, som är arkiverat.

`4)` [!DNL Marketo Measure] skapar också 3 nya aktier, Share 345, Share 456 och Share 567, som kopierar innehållet i Share 234, förutom att det har ett eget unikt `?_bl` taggning.

`5)` [!DNL Marketo Measure] regelbundet kontrollera att resurserna inte delas och om de gör det kommer vi att starta om processen i steg 2 ovan.

>[!NOTE]
>
>Om vi genomför detta kommer våra kunder att förlora annonshistoriken hos Creative B: Dela 234, Creative C: Dela 234 och Creative D: Dela 234 eftersom det nu återskapas med Creative E: Dela 345, Dela F: Dela 456 och Creative G: Dela 567.

![](assets/three.png)

## Så här fungerar det: Lead Gen Forms {#how-it-works-lead-gen-forms}

**Processen**

Via [!DNL LinkedIn's] API:t för annonsformulär och API:t för formulärsvar kan vi samla in data för ett annonskonto och koppla e-postadressen till en lead från CRM eller Marketo.

linkedIn-formulär kan innehålla flera e-postadresser. När vi hämtar formulärsvar letar vi efter e-postadresser med följande prioritet: E-postadress, e-postadress (primärt formulärfält) eller anpassade fält med ett giltigt e-postvärde.

Oavsett Campaign- eller Creative-status resulterar alla formulärsvar i en kontaktyta. [!DNL Marketo Measure] har en 90-dagars uppslagsbegränsning, så [!DNL Marketo Measure] kan inte komma åt formulärsvar som är äldre än 90 dagar, men det längre värdet [!DNL Marketo Measure] och [!DNL LinkedIn] är aktiverat så blir fler kontaktytor för Lead Gen Form synliga genom [!DNL Marketo Measure].

>[!NOTE]
>
>linkedIn-kostnader hämtas fortfarande som en del av Sponsored Content Campaigns.

**Spåra lead Gen Forms i CRM eller Marketo**

Före [!DNL Marketo Measure] och LinkedIn Lead Gen Forms Integration fanns, var det vanligt att kunderna skickade in blanketter till ett Marketo-program och/eller CRM Campaign för att spåra blanketterna och få attribuering av dessa. När inställningen Lead Gen Forms är aktiverad vill vi se till att dessa formulärinskickade formulär inte räknas två gånger. Kontrollera följande:

* Fältet Aktivera slutpunkter för köpare i CRM-objektet är inställt på Ingen eller Exkludera alla kampanjmedlemmar
* Uppdatera alla relaterade aktivitetsregler för Marketo eller Marketo
* Uppdatera alla relaterade CRM-kampanjregler

>[!NOTE]
>
>LinkedIn API har en 90-dagars uppslagsbegränsning, så om du använder Marketo- eller CRM-regler bör du ange slutdatumet för regeln till 90 dagar före det datum då du aktiverade integreringen i [!DNL Marketo Measure].

## Kontaktpunktsinformation {#touchpoint-details}

En gång [!DNL Marketo Measure] har taggat din landningssida på LinkedIn Creative Cloud så kan du visa lösta annonser på kontaktytan. Här är mappningen av datavärden som du kan förvänta dig att se:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Touchpoint-fält</th> 
   <th>Exempelvärde</th> 
  </tr> 
  <tr> 
   <td><p>Annons-ID </p></td> 
   <td><p>84186224 </p></td> 
  </tr> 
  <tr> 
   <td><p>Annonsinnehåll </p></td> 
   <td><p>95 % av marknadsförarna på #B2B anser att strategin för att skapa efterfrågan är framgångsrik. Läs mer: [!DNL https]/lnkd.in/jgdi50vKrgv</p></td> 
  </tr> 
  <tr> 
   <td><p>Annonsgrupp-ID </p></td> 
   <td><p>(tom) </p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonsgrupp </p></td> 
   <td><p>(tom) </p></td> 
  </tr> 
  <tr> 
   <td><p>ID för annonskampanj </p></td> 
   <td><p>138949954 </p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonskampanj </p></td> 
   <td><p>SU - COM Accounts - Demand Skills </p></td> 
  </tr> 
  <tr> 
   <td><p>Måladress för annons </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217 </p></td> 
  </tr> 
  <tr> 
   <td><p>Formulär-URL </p></td> 
   <td><p>info.bizible.com/demo </p></td> 
  </tr> 
  <tr> 
   <td><p>Formulär-URL - Raw </p></td> 
   <td><p>info.bizible.com/demo </p></td> 
  </tr> 
  <tr> 
   <td><p>Nyckelords-ID </p></td> 
   <td><p>(tom) </p></td> 
  </tr> 
  <tr> 
   <td><p>Matchningstyp för nyckelord </p></td> 
   <td><p>(tom) </p></td> 
  </tr> 
  <tr> 
   <td><p>Landningssida </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders </p></td> 
  </tr> 
  <tr> 
   <td><p>Landningssida - Raw </p></td> 
   <td><p>https://www.adobe.com/marketing-attribution-for-demand-generation-leaders?_bl=84186217 </p></td> 
  </tr> 
  <tr> 
   <td><p>Marknadsföringskanal </p></td> 
   <td><p>Betald social </p></td> 
  </tr> 
  <tr> 
   <td><p>Marknadsföringskanal - sökväg </p></td> 
   <td><p>Betald social.LinkedIn </p></td> 
  </tr> 
  <tr> 
   <td><p>Medel </p></td> 
   <td><p>"cpc" eller "Lead Gen Form"</p></td> 
  </tr> 
  <tr> 
   <td><p>Referenssida </p></td> 
   <td><p>www.linkedin.com/ </p></td> 
  </tr> 
  <tr> 
   <td><p>Referenssida - Raw </p></td> 
   <td><p>www.linkedin.com/ </p></td> 
  </tr> 
  <tr> 
   <td><p>Sökfras </p></td> 
   <td><p>(tom) </p></td> 
  </tr> 
  <tr> 
   <td><p>Kontaktpunktstyp </p></td> 
   <td><p>Webbformulär </p></td> 
  </tr> 
  <tr> 
   <td><p>Kontaktpunktskälla </p></td> 
   <td><p>LinkedIn </p></td> 
  </tr> 
 </tbody> 
</table>

## Kostnader {#costs}

För [!DNL Marketo Measure] är direkt integrerat med [!DNL LinkedIn]laddar vi ned de inspelade utgifterna för varje Campaign och Creative varje dag. Kunden behöver inte rapportera om [!DNL LinkedIn] inom [!DNL Marketo Measure] längre.

Precis som med andra annonsintegreringar [!DNL Marketo Measure] har definierat en regel för marknadsföringskanaler för att placera alla [!DNL LinkedIn] kampanjer, kreatörer och kostnader. För att kunna använda regeln måste kunden infoga en ny rad för sin betald [!DNL LinkedIn] insatser. Det kan vara en ny eller befintlig kanal. Använd definitionen &quot;[[!DNL LinkedIn] Betalat]&quot; som [!DNL Marketo Measure] har definierats som en kontaktyta med en [!DNL Marketo Measure] -tagg.

![](assets/four.png)

## [!DNL Marketo Measure] Upptäck {#marketo-measure-discover}

Några förbättringar har gjorts i [!DNL Marketo Measure] Upptäck stöd för rapportering från Lead Gen Forms.

**Betalat mediakort**

Lead Gen Forms: Ny ruta som innehåller antal formulärfyllningar i LinkedIn. Granska av det här antalet visar Aktivitets-ID, Formulärdatum, Formulärnamn och E-postadress.

**Förlovningsnämnd**

Events resa: Inkluderar händelsetypen &quot;Aktivitet&quot; och mediet &quot;Lead Gen Form&quot; för formulär som kommer genom integreringen. Detaljerad information innehåller information om Campaign, Creative och Form.

## Vanliga frågor om sponsrat innehåll {#sponsored-content-faq}

**Vad är en mörk resurs?**

En mörk andel är ett inlägg där det aldrig publiceras på företagssidan och omedelbart skapas och läggs till som en kreativ resurs. Så här [!DNL Marketo Measure]Creative-skapade kreatörer visas inte överst på företagets sida och befordras igen. Mörka delningar används så att de kan visas bakom kulisserna.

**Vad status gör [!DNL Marketo Measure] tagga?**

Det finns fyra olika statusvärden på en [!DNL LinkedIn] Campaign and Creative: Aktiv, Pausad, Arkiverad och Avbruten. Vi taggar bara aktiva kampanjer och kreatörer. Om du taggar andra statusar anges de som Aktiv igen. [!DNL Marketo Measure] taggar inte Pausad, Arkiverad eller Avbruten kampanj eller Creative, men fortsätter taggningen om statusen ändras till Aktiv.

**Vad är värdet som [!DNL Marketo Measure] använder du för att tagga?**

I slutet av mål-URL:en [!DNL Marketo Measure] lägger till parametern `&_bl={creativeId}`, där `{creativeId}` är det kreativa ID:t från LinkedIn. Med det kreativa ID:t [!DNL Marketo Measure] kan också avgöra kampanj-ID eftersom [!DNL LinkedIn] har en ganska grundläggande annonsstruktur eftersom varje Creative-medlem bara kan tillhöra en Campaign.

**Vad händer en gång med min gamla kreativa [!DNL Marketo Measure] skapar en ny version av den?**

När [!DNL Marketo Measure] återskapar en resurs och placerar den i en ny Creative, den gamla Creative-versionen arkiveras. Det är också därför [!DNL Marketo Measure] inte taggar arkiverade kampanjer eller kreatörer - annars slingrar det sig med [!DNL Marketo Measure] försöker tagga det på obestämd tid.

**Varför matchar inte den skapade annonsens mål-URL min ursprungliga annons?**

[!DNL Marketo Measure] spårningsparametrarna måste läggas till i en matchad URL, men URL:en som presenteras i API:t kan vara en förkortad URL utan att alla parametrar finns. För att komma runt den frågan [!DNL Marketo Measure] söker efter förkortade URL:er innan ett tillägg återskapas, åtgärdar det och skapar sedan den nya annonsen med den matchade URL:en och alla dess parametrar, vilket [!DNL Marketo Measure] om du vill lägga till taggar.

**Taggar du alla mina annonser? Jag ser inte bl-parametern på alla mina landningssidor?**

Vi har observerat att vissa marknadsförare kommer att lägga in en bildlänk i mål-URL:en, som [!DNL Marketo Measure] kan inte tagga, så vi söker efter URL:en i annonsinnehållet. If [!DNL Marketo Measure] har behörighet att tagga förkortade URL:er, vi utökar URL:en och taggen som, på grund av LinkedIn kopieringsstruktur, automatiskt förkortas i texten. Taggen finns i den förkortade webbadressen för LinkedIn, som visas i kontaktpunktens fält för annonsinnehåll i stället för i fältet Landningssida - Raw.

**Någon i mitt team råkade klona en del. Kan jag pausa den?**

Inga problem. [!DNL Marketo Measure] söker efter aktier som inte längre är unika, vilket innebär att de sedan dess har kopierats till ett annat Creative-program. När kopian har identifierats [!DNL Marketo Measure] följer det vanliga flödet för att tagga och skapa nya annonser.

**Min annons var under behandling tidigare. Varför väntar den på granskning igen efter [!DNL Marketo Measure] taggade den?**

linkedIn kräver att alla annonser som skapas eller ändras genomgår den normala säkerhetsprocessen innan de publiceras. [!DNL Marketo Measure] försöker att fånga upp annonsen så snabbt som möjligt, eftersom den söker efter nya annonser var sjätte timme men med [!DNL LinkedIn's] ytterligare ett steg kan det fördröja starten med några timmar.

**Det finns två URL:er på min annons. Vilken taggas?**

Båda. The [!DNL Marketo Measure] integreringen gör att vi kan tagga mål-URL:en från klickbilden i annonsen, men även uppdaterar automatiskt den förkortade URL:en i annonsbeskrivningen.

![](assets/five.png)

**Jag har kopplat samman min [!DNL LinkedIn ads] konto. Varför är det inte? [!DNL Marketo Measure] taggar jag mina länkar?**

Den anslutna [!DNL LinkedIn] användaren måste ha rätt redigeringsåtkomst, vilket innebär att användaren måste vara kontohanterare, kampanjhanterare eller Creative Manager.

**Hur vet jag om min kreativitet kommer att kopieras? Kan jag se om mina kreatörer använder samma resurs?**

Resurs-ID anges inte i en [!DNL LinkedIn] så det finns inget tydligt och tydligt sätt att söka efter kreativa till-dela-mappningar. Om du misstänker att en person kan vara en kopia kan du kontrollera manuellt genom att öppna annonsen inifrån [!DNL LinkedIn] Kampanjhanteraren - annonsen öppnas på en ny flik och du hittar resurs-ID:t i URL:en.

![](assets/six.png)

## Lead Gen Forms - frågor och svar {#lead-gen-forms-faq}

**Vad kostar den här förbättringen?**

Detta erbjudande ingår i alla [!DNL Marketo Measure] prenumeration.

**Är integreringen retroaktiv?**

Ja, vi kommer att ladda ned historiska annonseringssvar från LinkedIn, även om vi är begränsade till 90-dagars uppslagsfönstret. Ju längre [!DNL Marketo Measure] och LinkedIn-integrationen är aktiverad kommer fler kontaktytor för Lead Gen Form att synas genom [!DNL Marketo Measure].

Det finns inget alternativ för att ange ett specifikt datum för hämtning, men du kan också ange regler för borttagning av pekpunkter om det finns kontaktpunkter som du behöver inaktivera.

**Aktiveras detta automatiskt om jag redan använder [!DNL Marketo Measure] Integrering av linkedIn-annonser?**

Nej, vi börjar inte automatiskt ladda ned den för alla kunder, men det är en mycket enkel växling för att aktivera den här funktionen i inställningarna.

**Är formulärdata tillgängliga?**

Formulärdata är tillgängliga via [!DNL Marketo Measure] Identifiera inklusive formulär-ID och formulärnamn. Formulärinformationen är ännu inte tillgänglig för kontaktobjekten i CRM.

**Vad händer med [!DNL LinkedIn] leads som tidigare har synkroniserats med Marketo-program eller CRM-kampanjer?**

Vi rekommenderar att du justerar [!DNL Marketo Measure] regler för att generera kontaktytor från dessa specifika program eller kampanjer för att undvika dubbelarbete. LinkedIn API har en 90-dagars uppslagsbegränsning, så om du använder Marketo- eller CRM-regler bör du ange slutdatumet för regeln till 90 dagar före det datum då du aktiverade integreringen i [!DNL Marketo Measure]. Från och med nu [!DNL Marketo Measure] kan ladda ned leads med större insikter och information.

**Finns det någon automatisk taggning eller spårning?**

Nej, det här skiljer sig från andra [!DNL Marketo Measure] integreringar. I stället för att ändra landningssidan (eftersom det inte finns något klick genom landningssidan) hämtar vi bara den relevanta informationen från LinkedIn och behandlar dem som aktiviteter inom [!DNL Marketo Measure].
