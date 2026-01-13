---
description: Ordlista för Marketo Measure-fält
title: Ordlista för Marketo Measure-fält
exl-id: 8e23b102-6d4f-4919-b361-04d1b184e710
feature: Fundamentals
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '3210'
ht-degree: 0%

---


# Ordlista för Marketo Measure-fält {#glossary}

I den här artikeln finns en ordlista med alla Marketo Measure-fält som har lagts till i Salesforce från Marketo Measure baspaket. Du hittar även information om vilket objekt som fältet kan hittas på och hur varje fält fylls i med information.

[Klicka här](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md) om du vill se vilket objekt varje Marketo Measure-fält relaterar till.

[A](#a) ・ [B](#b) ・ [C](#c) ・ [D](#d) ・ [E](#e) ・ [F](#f) ・ [G](#g) ・ H ・ I ・ J ・ [K](#k) ・ [L](#l) ・ [M &#x200B;](#m) ・ N ・ [O](#o) ・ [P](#p) ・ Q ・ [R](#r) ・ [S](#s) ・ [T](#t) ・ [U](#u) ・ [V](#v) ・ W ・ X ・ Y ・ Z

## A {#a}

**Konto** | Hittade på Buyer Attribution Touchpoint

Det här fältet fylls i med det kontonamn som är associerat med BAT.

**Annonskampanj-ID** | Finns på Buyer Touchpoint, Buyer Attribution Touchpoint

Det finns tre sätt att fylla i det här fältet:

`1)` Om kontaktytan kommer från en betald sökåtgärd (antingen AdWords eller BingAds) visas annonskampanj-ID:t från annonsplattformen här.

`2)` Om kontaktytan inte kom från en betald sökning fylls fältet i med värdet utm_campaign från landningssidans URL.

t.ex. `http://info.marketomeasure.com/adwords-for-lead-generation?utm_source=Event&utm_medium=booth&utm_campaign=Marketo%20Virtual%20Event%20sep2014`

I det här exemplet skulle annonskampanj-ID:t visa: __GAId__ Marknadsföringsvirtuell händelse sept2014

`3)` Om kontaktytan kommer från en offlinekampanj i Salesforce (en konferens, middag, osv.) visas Salesforce Campaign-ID:t för annonskampanj

Om inget av ovanstående anges är fältet tomt.

**Namn på annonskampanj** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från betalsökningen (AdWords/Bing Ads) visas annonskampanjens namn från annonsplattformen här.

`2)` Om kontaktytan inte kom från betald sökning och landningssidans URL innehåller ett värde för utm_campaign, fylls värdet i här.

`3)` Om kontaktytan kommer från en Salesforce-kampanj visas namnet på Salesforce Campaign här.

`4)` Detta fylls i med det kampanjnamn som definierats för kontaktpunkter som skapats från aktiviteter som skapats i ditt Marketo Measure-konto.

Om inget av ovanstående anges är fältet tomt.

**Namn på annonskampanj (FT)** | Buyer Touchpoint

Det här fältet fylls i på samma sätt som annonskampanjens namn. I det här fältet visas dock namnet på annonskampanjen som genererade första kontaktytan.

**Namn på annonskampanj (LC)** | Buyer Touchpoint

Det här fältet fylls i på samma sätt som annonskampanjens namn. I det här fältet visas emellertid namnet på annonskampanjen som genererade kontaktpunkten för att skapa leads.

**Lägg till innehåll** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från betalsökningen (AdWords/Bing Ads) visas hela annonskopian från annonsplattformen i fältet.

`2)` Om kontaktytan inte kommer från en betald sökning visas värdet utm_content i landningssidans URL.

`3)` Detta fylls i med ämnesvärdet från den relaterade aktiviteten som genererade Touchpoint.

Om inget av ovanstående anges är fältet tomt.

**Lägg till mål-URL** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från en betald sökning visar det här fältet den URL-adress som du omdirigeras till efter att du klickat på annonsen från sökmotorn.

Om kontaktytan inte kommer från en betald sökning är fältet tomt.

**Lägg till grupp-ID** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kom från en betald sökning visas annonsgrupps-ID:t från AdWords/Bing Ads här.

Om kontaktytan inte kom från en betald sökning är fältet tomt.

**Lägg till gruppnamn** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kom från en betald sökning visas annonsgruppens namn från AdWords/Bing Ads här.

Om kontaktytan inte kom från en betald sökning är fältet tomt.

**Annons-ID** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kom från en betald sökning visas annons-ID från AdWords/Bing Ads här.

`2)` Detta fylls i med det externa aktivitets-ID:t om kontaktpunkten genereras från en CRM-aktivitet.

Om kontaktytan inte kom från en betald sökning är fältet tomt.

**Attribution % Custom Model** | Buyer Attribution Touchpoint

Om du använder en anpassad attribueringsmodell visas den procentuella intäkt som tilldelats en kontaktyta enligt de värden som angetts i din anpassade modell.

Om du inte använder en anpassad modell kommer det här fältet att vara tomt.

**Attribution % First Touch** | Buyer Attribution Touchpoint

I det här fältet visas den procentuella intäkt som tilldelats en kontaktyta enligt en First Touch Model.

**Attribution % Full** | Buyer Attribution Touchpoint

I det här fältet visas den procentuella intäkt som tilldelats en kontaktyta enligt en modell för fullständig sökväg.

**Attribution % Lead Creation** | Buyer Attribution Touchpoint

I det här fältet visas den procentuella intäkt som tilldelats en kontaktyta enligt en modell för att skapa leads.

**Attribution % U-Shaped** | Buyer Attribution Touchpoint

I det här fältet visas den procentuella intäkt som tilldelats en kontaktyta enligt en U-formad modell.

**Attribution % W-Shaped** | Buyer Attribution Touchpoint

I det här fältet visas den procentuella intäkt som tilldelats en kontaktyta enligt en W-Shaped-modell.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## B {#b}

**Marketo Measure-säljprojektsbelopp** | Salesforce möjlighet

Om du använder ett anpassat beloppsfält för att rapportera säljprojektsintäkter kan Marketo Measure inte läsa dessa anpassade beloppsfält. Marketo Measure Opportunity Amount är ett dolt fält som används för att skapa ett arbetsflöde som gör att Marketo Measure kan läsa anpassade beloppsfält i säljprojektet.

**Webbläsare** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas vilken typ av webbläsare som används under webbsessionen (Chrome, Safari, Firefox osv.).

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## C {#c}

**Kontakt** | Buyer Touchpoint, Buyer Attribution Touchpoint

I fältet visas kontakten som kontaktytan tillhör.

**Antal - anpassad modell** | Buyer Attribution Touchpoint

Om du använder en anpassad attribueringsmodell visas i det här fältet, i decimalform, den procentuella intäktskrediten som tilldelats en kontaktyta enligt de värden som angetts i din anpassade modell.

Om du inte använder en anpassad modell kommer det här fältet att vara tomt.

**Antal - anpassad modell** | Buyer Touchpoint

Om du använder en anpassad attribueringsmodell visar det här fältet, i decimalform, den procentandel attribueringskrediter som har tilldelats en kontaktyta enligt de värden som har angetts i din anpassade modell. Eftersom det här fältet gäller Buyer Touchpoint Object är det inte en reflexion av intäktskrediter, utan bara attribueringskrediter.

Om du inte använder en anpassad modell kommer det här fältet att vara tomt.

**Antal - första beröring** | Buyer Attribution Touchpoint

I det här fältet visas, i decimalform, den procentuella intäktskrediten som tilldelats en kontaktyta enligt en First Touch Model.

**Antal - första beröring** | Buyer Touchpoint

I det här fältet visas, i decimalform, den procentuella attribueringskrediten som tilldelats en kontaktyta enligt en First Touch Model. Om kontaktytan är First Touch blir fältet alltid 1,0 (vilket anger 100 % attribueringskrediter). Om kontaktytan inte är den första kontakten är fältet alltid 0 (vilket anger 0 % attribueringskrediter).

Eftersom det här fältet gäller Buyer Touchpoint Object är det inte en reflexion av intäktskrediter, utan bara attribueringskrediter.

**Antal - fullständig sökväg** | Buyer Attribution Touchpoint

I det här fältet visas, i decimalform, den procentuella intäkt som ges till en kontaktyta enligt en fullständig sökvägsmodell.

**Antal - Leadskaparberöring** | Buyer Attribution Touchpoint

I det här fältet visas, i decimalform, den procentuella intäktskrediten som tilldelats en kontaktyta enligt en Lead Creation Model.

**Antal - Leadskaparberöring** | Buyer Touchpoint

I det här fältet visas, i decimalform, den procentuella attribueringskrediten som tilldelats en kontaktyta enligt en Lead Creation Model. Om kontaktytan Lead Creation (Leadskapandekontakt) är fältet alltid 1.0 (vilket anger 100 % attribueringskrediter). Om kontaktytan Lead Creation (Lead Creation) inte visas är fältet alltid 0 (vilket anger 0 % attribution).

Eftersom det här fältet gäller Buyer Touchpoint Object är det inte en reflexion av intäktskrediter, utan bara attribueringskrediter.

**Antal - U-formad** | Buyer Attribution Touchpoint

I det här fältet visas, i decimalform, den procentuella intäktskrediten som tilldelats en kontaktyta enligt en U-Shaped-modell.

**Antal - U-formad** | Buyer Touchpoint

I det här fältet visas, i decimalform, den procentuella attribueringskrediten som tilldelats en kontaktyta enligt en U-Shaped-modell. I den U-formade modellen delas krediten mellan First Touch, Lead Creation Touch och alla mellanliggande formulärinskickade formulär som gjordes mellan First Touch och Lead Creation Touch.

Eftersom det här fältet gäller Buyer Touchpoint Object är det inte en reflexion av intäktskrediter, utan bara attribueringskrediter.

**Antal - W-Shaped** | Buyer Attribution Touchpoint

I det här fältet visas, i decimalform, den procentandel kredit som ges till en kontaktyta enligt en W-Shaped-modell.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## D {#d}

Rapportdatum | Marketo Measure ABTest, Marketo Measure Event

Marketo Measure Event - det datum då en användare utförde en specifik åtgärd på din webbplats och aktiverade en händelse

Marketo Measure ABTest - det datum då en användare deltog i ett A/B-test på er webbplats

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## E {#e}

**Händelsenamn** | Marketo Measure Event

I det här fältet visas namnet på den åtgärd som utlöste händelsen (t.ex. sidvyn).

**Händelsevärde** | Marketo Measure Event

Beskrivning av händelsen (t.ex. hemsida)

**Experimentnamn** | Marketo Measure ABTest

I det här fältet visas namnet på experimentet (dvs. testknappen)

**Experiment-ID** | Marketo Measure AB Test

Unik identifieringskod för varje experiment

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## F {#f}

Formulär-URL | Buyer Touchpoint, Buyer Attribution Touchpoint

Det här fältet visar en förkortad version av en sidas URL där formulärfyllningen inträffade (inga UTM-parametrar)

Formulär-URL - Raw | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas hela den sida-URL där formulärfyllningen inträffade, inklusive UTM-parametrar

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## G {#g}

Geo City | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas namnet på den ort där leadet/kontakten besökte webbplatsen. Detta görs via omvänd IP-sökning.

Geo-land | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas var det land där leadet/kontaktpersonen besökte webbplatsen. Detta görs via omvänd IP-sökning.

Georegion | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas region eller stat där leadet/kontakten besökte webbplatsen. Detta görs via omvänd IP-sökning.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## k {#k}

**Nyckelords-ID** | Buyer Touchpoint, Buyer Attribution Touchpoint

Om kontaktytan kommer från betalsökningen visas nyckelords-ID:t från annonsplattformen (Adwords/BingAds) i det här fältet.

Om den här kontaktytan inte kom från en betald sökning är fältet tomt.

**Matchningstyp för nyckelord** | Buyer Touchpoint, Buyer Attribution Touchpoint

Om kontaktytan kommer från betalsökningen visas matchningstypen från annonsplattformen (Adwords/Bing) i det här fältet.

**Nyckelordstext** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från en betald sökning visar det här fältet nyckelordstexten från annonsplattformen (Adwords/BingAds) ELLER värdet från parametern _bk i URL:en för landningssidan.

t.ex. `http://info.marketomeasure.com/intro-guide-b2b-marketing-attribution?_bt=12345678&_bk=marketing%20attribution&_bm=p&gclid=ABc123def456ghi789jkl`

`2)` Om kontaktytan inte kommer från en betald sökning visar det här fältet värdet utm_term från landningssidans URL.

`http://www.marketomeasure.com/blog/lead-generation?utm_source=linkedin&utm_medium=Social&utm_campaign=ABC%20Blog&utm_content=Lead%20Gen&utm_term=lead%20gen`.

Om kontaktytan inte kom från en betald sökning, eller om det inte finns något utm_term-värde, kommer det här fältet att vara tomt.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## L {#l}

**Startsida** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas en förkortad version av URL:en (inga UTM-parametrar) för den första webbsida som besöktes under en webbsession.

**Landningssida - Raw** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas hela URL-adressen (inklusive UTM-parametrar) för den första webbsidan som besöktes under en webbsession.

**Lead** | Buyer Touchpoint, Marketo Measure

I det här fältet visas namnet på det lead som en kontaktyta tillhör.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## m {#m}

**Marknadsföringskanal** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas den allmänna gruppen av marknadsföringsaktiviteter eller marknadsföringskanal som kontaktytan tillhör (t.ex. Betald sökning, Direkt, Socialt osv.). Kontaktpunkterna grupperas efter hur kanalerna har konfigurerats i Marketo Measure App. [Klicka här](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) om du vill ha mer information om marknadsföringskanaler eller om hur du konfigurerar dina kanaler.

**Marknadsföringskanal - sökväg** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas marknadsföringskanalen och den delkanal som en kontaktyta tillhör. I exemplet nedan är Marketing Channel - Path Social.Linkedin, där marknadsföringskanalen är Social och underkanalen är LinkedIn.

![&#x200B; 3](assets/1-3.png)

**Medium** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från en betald sökning visas mediet från Adwords/BingAds här (t.ex. CPC).

`2)` Om kontaktytan inte kommer från en betald sökning visar det här fältet värdet utm_medium från landningssidans URL.

`3)` Om kontaktytan kommer från en offlinekampanj visas fältet Type i Salesforce Campaign.

`4)` Detta fylls i med aktivitetstypvärdet från den relaterade aktiviteten som genererade kontaktpunkten.

Om inget av det ovanstående anges ett Medium-värde automatiskt av Marketo Measure.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

O

**Möjlighet** | Buyer Attribution Touchpoint

I det här fältet visas affärsmöjligheten som BAT tillhör.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

P

**Plattform** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas vilken typ av dator eller telefon det är och vilken typ av operativsystem som användes under webbsessionen.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

R

**Referenssida** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas URL-adressen (utan UTM-parametrar) för den sista webbsidan som Lead/Contact var på som dirigerade dem till din webbplats.

Exempel:

- Om kontaktytan kommer från betald/organisk sökning visas sökmotorns URL i fältet

- Om kontaktytan kommer från Social visas URL-adressen till den sociala webbplatsen (dvs LinkedIn) i fältet.

**Referenssida - Raw** | Buyer Touchpoint, Buyer Attribution Touchpoint

Det här fältet visar samma information som Referenssida, förutom att det här fältet visar hela den refererande URL:en (inklusive UTM-parametrar).

**Intäkter - anpassad modell** | Buyer Attribution Touchpoint

Om du använder en anpassad attribueringsmodell visar det här fältet det dollarintäktsbelopp som tilldelats en kontaktyta enligt den attribueringsprocent som angetts i din anpassade modell.

Om du inte använder en anpassad modell blir dollarbeloppet 0.

**Intäkter - första beröring** | Buyer Attribution Touchpoint

I det här fältet visas dollarintäktsbeloppet som tilldelats en kontaktyta enligt attribueringsprocenten i den första beröringsmodellen.

**Intäkter - fullständig sökväg** | Buyer Attribution Touchpoint

I det här fältet visas dollarintäktsbeloppet som tilldelats en kontaktyta enligt attribueringsprocenten i modellen för fullständig sökväg.

**Intäkter - Lead Creation Touch** | Buyer Attribution Touchpoint

I det här fältet visas dollarintäktsbeloppet som tilldelats en kontaktyta enligt attribueringsprocenten i modellen Lead Creation.

**Intäkter - U-formad** | Buyer Attribution Touchpoint

I det här fältet visas dollarintäktsbeloppet som tilldelats en kontaktyta enligt attribueringsprocenten i den amerikanska modellen.

**Intäkter - W-Shaped** | Buyer Attribution Touchpoint

I det här fältet visas dollarintäktsbeloppet som tilldelats en kontaktyta enligt attribueringsprocenten i W-Shaped-modellen.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

S

**Salesforce Campaign** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas den Salesforce Campaign som kontaktytan tillhör.

**Sökfras** | Buyer Touchpoint, Buyer Attribution Touchpoint

Om kontaktytan kommer från betald eller organisk sökning visas den sökfras som angetts i sökmotorn. Av sekretesskäl är dock den här informationen vanligtvis inte tillgänglig.

**Segment** | Buyer Attribution Touchpoint

I det här fältet visas de segment som kontaktytan tillhör. Detta beror på hur du har konfigurerat segmenteringsreglerna i Marketo Measure-appen.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

T

**Slutpunktsdatum** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kommer från en onlinekälla visar det här fältet datum och tid då kontaktytan inträffade.

`2)` Om kontaktytan kom från en offlinehändelse visar det här fältet det datum och den tid som angetts i Salesforce Campaign eller från det datumfält som valts i reglerna för kampanjsynkronisering.

`3)` Om kontaktytan kommer från en aktivitet, visar det här fältet datum och tid för det fält som markerats som slutpunktsdatum i aktivitetsreglerna.

**Slutpunktsdatum (FT)** | Buyer Touchpoint

Det här är samma fält som Touchpoint Date, men i det här fältet visas specifikt datum och tid då den första beröringspunkten inträffade.

**Slutpunktsdatum (LC)** | Buyer Touchpoint

Det här är samma fält som Touchpoint Date, men i det här fältet visas specifikt datum och tid då kontaktpunkten för att skapa lead inträffade.

**Pekpunktsposition** | Buyer Touchpoint, Buyer Attribution Touchpoint

I det här fältet visas positionen för kontaktytan. Kontaktpunktens position återspeglar de största milstolparna i kundresan (t.ex. FT, Form, LC, OC, Closed). Kontaktpunktens position beror på när den inträffade under kundresan, och en enda kontaktyta kan ha mer än en position. De olika beröringspunktspositionerna är följande:

First Touch (FT) - Den allra första marknadsföringsinteraktionen någon har med ditt varumärke

Lead Creation (LC) - Den allra första kända marknadsföringsinteraktionen (vanligtvis en formulärinlämning eller en Salesforce Campaign-inkludering)

Formulär - När en besökare fyller i ett onlineformulär

Möjligheter att skapa - Den interaktion som ligger närmast när Opp skapas

Closed - Den interaktion som ligger närmast när Opp stängs (Won eller Lost)

**Touchpoint Source** | Buyer Touchpoint, Buyer Attribution Touchpoint

`1)` Om kontaktytan kom från en betald sökning visar det här fältet annonsplattformens namn (AdWords/BingAds)

`2)` Om kontaktytan kommer från organisk sökning visas namnet på sökmotorn i det här fältet

`3)` Om inte #1 eller #2, och värdet utm_source finns i startsidans URL för kontaktytan, visas det värdet här

`4)` Detta fylls i som CRM-kampanj om kontaktytan genereras från en CRM-kampanj.

`5)` Detta fylls i som CRM-aktivitet om Touchpoint genereras från en CRM-aktivitet.

Om inget av ovanstående anges fylls fältet i som &quot;Web Direct&quot; eller &quot;Web&quot;.

**Touchpoint Source (FT)** | Buyer Touchpoint

Det här är samma fält som Touchpoint Source, men i det här fältet visas källan för den första beröringspunkten.

**Touchpoint Source (LC)** | Buyer Touchpoint

Det här är samma fält som Touchpoint Source, men i det här fältet visas källan för kontaktpunkten Lead Creation.

**Touchpoint-typ** | Finns på Buyer Touchpoint och Buyer Attribution Touchpoint.

I det här fältet visas typen av interaktion för pekpunkten. Det visas som: Webbbesök, Webbformulär eller Webbchatt för JavaScript kontaktytor. För CRM Campaign-kontaktytor visas det som CRM. Den fylls i med aktivitets- eller händelsetypen för aktivitetens slutpunkter.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

U

**UniktID** | Buyer Touchpoint, Buyer Attribution Touchpoint

Det unika ID som är kopplat till varje kontaktyta

**Användar-ID** | Marketo Measure ABTest

Optimizelys unika identifieringskod för varje användning

[Klicka här om du vill gå tillbaka till sidans överkant](#top)

## V {#v}

**Variation** | Marketo Measure ABTest

Namnet på variationen av A/B-provningen

**Variations-ID** | Marketo Measure ABTest

Den unika identifieringskoden för varje A/B-testvariation.

[Klicka här om du vill gå tillbaka till sidans överkant](#top)
