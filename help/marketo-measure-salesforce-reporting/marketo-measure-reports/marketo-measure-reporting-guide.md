---
description: "[!DNL Marketo Measure] Rapporteringsguide - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Rapporteringshandbok"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
feature: Reporting
source-git-commit: 3119b1754bba49139c1a6756851ada580e09c1ef
workflow-type: tm+mt
source-wordcount: '5602'
ht-degree: 0%

---

# Rapporteringshandbok för [!DNL Marketo Measure] {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Innan du skapar en [!DNL Marketo Measure]-rapport är det viktigast att bekräfta att dina [!DNL Marketo Measure]-kontoinställningar har granskats och konfigurerats för att säkerställa att data i rapporterna är korrekta och att de återspeglar ditt företags särdrag. Dessutom fungerar rapportprojekt bäst när de följer en strukturerad process. Justin Norris, en [!DNL Marketo Measure]-användare, advokat och partner från [Perkuto](https://perkuto.com/){target="_blank"}, har gett en expertsammanfattning av [hur man närmar sig rapportering i [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/){target="_blank"}:

**Upprätta mål**:&quot;Den första frågan som ska ställas är&quot;varför mäter vi?&quot; Lori Wizdo från [Forrester Research](https://go.forrester.com/) sammanfattar detta på ett bra sätt i ett [Marketo webbinarium](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/){target="_blank"}. Enligt henne mäter vi för att bevisa eller validera ett beslut eller värdet av marknadsföring eller för att bli bättre (processförbättring). Vi skulle också vilja tillägga att insikterna från god mätning också ger indata och vägledning i marknadsföringsplaneringsprocessen.

Innan du börjar är det viktigt att du är tydlig med dina mål, de frågor du försöker svara på eller de problem du försöker lösa. Vilken historia vill du berätta? Vilka beslut kommer att fattas till följd av detta? Alltför ofta är dessa grundläggande faktorer dåligt genomtänkta, vilket leder till frustration för alla inblandade.&quot;

**Rapportdesign**:&quot;Därefter måste du utforma rapporten och fastställa de specifika dimensioner, mått och datamängd som den kommer att innehålla. En vanlig upplevelse är att ge en företagsanvändare exakt det de vill ha, bara för att de fortfarande känner att deras behov inte uppfylls. Det beror på att den insikt som en affärsanvändare faktiskt letar efter inte alltid finns i den rapport de begär. En bra analytiker (eller en MOPS-person med en analytiker som sitter på) kommer att ställa klargörande frågor, fastställa gemensamma definitioner (&quot;så, vad menar du egentligen med lead?&quot;) och till och med skissa en bild av slutrapporten för att se till att det finns en anpassning. Det är enda sättet att ta fram rapporten i vetskap om att du har en gedigen uppsättning krav.&quot;

**Rapportbygge**:&quot;När du väl har börjat bygga är det inte ovanligt att du stöter på vägspärrar eller ändpunkter. Du kanske upptäcker att du saknar en viktig datapunkt eller att dina objekt inte länkas på det sätt du behöver. För att lösa dessa problem tycker jag också att det är viktigt att förstå vad som händer &quot;under huven&quot; i din rapporteringsmaskin. Tack vare denna smidighet kan ni snabbt anpassa en rapportförfrågan och utvärdera om den är genomförbar (och enklare ta fram kreativa lösningar när den inte är det).&quot;

Låt oss titta &quot;under huven&quot; för att bättre förstå vad som får [!DNL Marketo Measure]-rapporteringsdatorn att köras.

## Buyer Touchpoint Objects (CRM) {#buyer-touchpoint-objects-crm}

På den högsta nivån finns det två rapporteringskategorier som baseras på de två olika Buyer Touchpoint-objekten: Dessa kategorier bestämmer vilken typ av [!DNL Marketo Measure]-data som du vill rapportera om: data som är relaterade till en _individ_, eller data som är relaterade till en _affärsmöjlighet_.

1. **Kontaktpunkter för köpare** (BT)/Enskilda/Totalt engagemang

   * Används vanligen för TOFU-mått (Top of the Trnel) och rapportering för _enskilda_ (Leads, Contacts, [!DNL Marketo Measure] People)
   * BT används för att förstå alla marknadsföringsinteraktioner som är relaterade till **personer**, eftersom de innehåller den fullständiga kontakthistoriken för varje person. Som en påminnelse skapas dessa kontaktytor i CRM för den anonyma First Touch, Lead Creation Touch och efterföljande formulärinskickning eller kontaktyta som du väljer att synkronisera från
en offlinekampanj eller aktivitet.

1. **Touchpoints för Buyer-attribuering** (BAT) / Opportunity / Account level / Revenue

   * Används vanligen för medelvärdet och/eller underkanten av tratten (MOFU och BOFU) och rapportering relaterade till _säljprojekt_.
   * BAT representerar de relevanta kontaktytorna för alla personer som är anslutna till **affärsmöjligheten** (antingen via roller för säljprojektskontakt eller via ett delat konto-ID, beroende på dina inställningar). Till skillnad från BT som bara gäller personer, kan BAT även kopplas till **intäkter**. Därför kommer ni att använda BAT för att besvara frågor om möjligheter, inklusive hur många möjligheter som öppnats eller stängts, eller pipeline-värdet och intäkterna.

>[!NOTE]
>
>BAT skapas från BT. Spårningen börjar i princip på individuell nivå via BT. När ett säljprojekt har skapats på ett konto refereras och kan skapa BAT som relaterar till säljprojektet till, så du vill använda det ena eller det andra beroende på vilka frågor du försöker svara på: frågor som relaterar till&quot;personstatistik&quot; (BT rapporter) eller frågor relaterade till&quot;säljprojektsstatistik&quot; (BAT rapporter)

Supportartikel: [Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup){target="_blank"}

## Buyer Touchpoint (BT) {#buyer-touchpoint-bt}

Buyer Touchpoint (BT) används för att spåra varje marknadsföringsinteraktion någon har med ert marknadsföringsmaterial. Varje persons (lead/kontakt/[!DNL Marketo Measure] person) resa representeras av deras relaterade BT. I [!DNL Marketo Measure] består en persons resa av:

1. Hur interagerade den här personen först med vårt varumärke? (Första beröring eller _FT_)
1. Hur konverterade/blev den här personen känd/blev en lead? (Lead-skapande eller _LC_)
1. Hur har den här personen annars interagerat med vårt varumärke och marknadsföringsmaterial sedan han blev en ledare? (_PostLC_)

Kontaktpunkter för köpare används för att svara på frågor som rör _personer_ (&quot;personer&quot; representeras av antingen leads eller kontakter i en CRM), t.ex. lead-/kontaktgenerering eller kundvärdesstatistik, i stället för säljprojektsrelaterade mått. Exempel:

* Vilka kanaler levererar mest leads?
* Vilka kanaler kostar mer eller mindre att skapa en ny lead?
* Vilket innehåll engagerar mina leads/kontakter?
* Vad är marknadsföringsberättelsen om särskilda titlar, roller, personer?
* Vilka kanaler driver MQL:er eller andra lead-/kontaktstatusar?

I första hand måste företagen veta,&quot;var kommer mina leads/kontakter?&quot;. Historiskt sett besvarades detta med ett enda endimensionellt värde (till exempel Lead Source). Som framgår av #1 och #2 ovan vet vi dock att leads kan ha flera kontaktytor under sin resa som lead. Buyer Touchpoint ger oss insikt i de två viktigaste interaktionerna som visar hur en lead genererades: deras First Touch och deras Lead Creation Touch. Kontaktpunkter för köpare är också _flerdimensionella_, vilket innebär att de har mängder av marknadsföringsdata, främst där personen kom från (marknadsföringskanal) och vad personen interagerade med (innehåll).

[attribueringsmodellerna](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md){target="_blank"} som ger bäst insikt i personbaserade mått är:

* **First Touch** - 100 % attribueringskrediter till Leads First Touch (FT)
* **Leadskapande** - 100 % attribueringskrediter till Lead&#39;s Lead Creation Touch (LC)
* **U-Shaped** - multi-touch-metod, med 40 % kredit till FT, 40 % kredit till LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>U-Shape-modellen är utformad för att belöna alla Buyer Touchpoints som sammanfattar hur en lead blev en lead. Efterföljande kontaktytor från dessa leads kan också rapporteras för att förstå ytterligare engagemang (Post LC), men de ingår inte i <strong>Lead Creation-resan</strong> så de får ingen attribueringskredit i FT-, LC- eller U-formade modeller.<p>

&#42;Det vanligaste är att U-formad attribuering speglar en till och med 50/50 delning mellan FT och LC. Om leadet konverteras i samma session som First Touch representerar en enda kontaktyta både FT- och LC-beröringspunktspositionerna. Därför skulle 100 % av attribueringen ges till en enda kontaktyta.</td>
</tr>
 </tbody>
</table>

Dessa modeller lägger stor vikt vid interaktioner i ett tidigt skede och ett engagemang i tratten. U-Shaped-attribuering är den rekommenderade modellen eftersom den tar hänsyn till både FT- och LC-kontaktytorna, vilket säkerställer att all beröring som påverkade leadet kan komma till sin rätt. Men ytterligare insikter kan ni få från Touch-modellerna First Touch och Lead Creation Touch om ni vill förstå dessa specifika delar av leadresan mer i detalj.

## Rekommenderade rapporter med Buyer Touchpoint (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEADS with BUYER TOUCHPOINTS**

**1.1 | Nya leads efter marknadsföringskanal**

Att sammanfatta era Leads Buyer Touchpoint-data med fältet Marknadskanal är den högsta nivån som representerar vilka kanaler/taktik som påverkar nya leads till skapandet. Om du strukturerar den här rapporten runt en&quot;Datumtyp&quot; =&quot;Skapad den&quot;, skapas en kohort med&quot;Nya lead&quot; (när lead skapades i CRM) i rapporten.

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler påverkar leads till skapandet?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Skapad lead (CRM) / Skapad (Discover)</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Första beröring, Lead-skapande, <strong>U-Shaped</strong><br>
   *SUMMA fälten Antal i dina CRM-rapporter (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>För rapporttypen Leads med Buyer Touchpoints börjar du med att anpassa den fördefinierade rapporten [!DNL Marketo Measure] 101 | Leads by Channel&#39;. Den här rapporten finns tillgänglig när den är färdig och är en utmärkt sandlåda som är fördefinierad enligt beskrivningen i tabellen ovan och kan snabbt anpassas för mer specifika rapporteringsbehov.

**1.2 | Nya leads per Campaign (eller fler detaljerade insikter)**

Om du vill ha mer detaljerad information om de data som sammanfattas i rapporten&quot;New Leads by Marketing Channel&quot; (1.1) lägger du till ytterligare en sammanfattning på kampanjnivå. På så sätt kan ni inte bara förstå vad&quot;marknadsföringskanaler&quot; driver nya leads till skapande, utan snarare vilka kampanjer i dessa kanaler som fungerar bäst:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka <i>kampanjer</i> påverkar leads till skapandet?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Skapad lead (CRM) / Skapad (Discover)</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Namn på annonskampanj (CRM)</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Första beröring, Lead-skapande, <strong>U-Shaped</strong><br>
   *SUMMA fälten Antal i dina CRM-rapporter (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Få ännu mer detaljerad information genom att sammanfatta rapporten med andra tillgängliga fält från Buyer Touchpoint-objektet. Det gör du genom att ange ytterligare grupperingar (CRM) eller dimensioner (Discover). Beroende på vilken kanal (som kanske representerar din roll) kan det finnas ytterligare information utöver den kampanjnivå som du vill få insikter i. Låt oss gå närmare in på Betalsökning, till exempel i tabellen nedan..

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka <i>nyckelord</i> påverkar leads till skapandet?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>Marknadsföringskanal = betald sökning</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Skapad lead (CRM) / Skapad (Discover)</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Nyckelordstext (CRM) / Nyckelord (Discover)</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Första beröring, Lead-skapande, <strong>U-Shaped</strong><br>
   *SUMMA fälten Antal i dina CRM-rapporter (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

Granularitetsnivån kan variera beroende på kanal. Det rekommenderade tillvägagångssättet skulle vara att fråga dig själv,&quot;vad om&quot;kanal X&quot; vill jag veta mer?&quot; Betalande sökhanterare kan också vara intresserade av ytterligare dimensioner, till exempel:

* Namn på annonskampanj
* Annonsinnehåll
* Annonsgrupp

Events-chefer kan dock vara mer intresserade av vilka specifika händelser eller vilka typer av händelser som påverkade de flesta ledarna till skapandet:

* Namn på annonskampanj/Salesforce Campaign = specifik händelse
* Medium = Campaign &#39;Type&#39;

**PÅMINNELSE**: Ytterligare filter kan behöva läggas till i alla rapportvarianter som beskrivs ovan eller nedan. Dessa filter skulle vara specifika för er organisation och skulle vara något som era marknadsföringsteam eller säljteam skulle kunna ge råd om. Det är inte ovanligt att en organisation kör samma filter i alla rapporter för att säkerställa att rapporten är så ren och korrekt som möjligt. Vanliga exempel:

* Filtrera ut interna poster från tester, vanligtvis via e-postadress
* Filtrering baserad på vissa posttyper som kan vara specifika för din affärsenhet

**1.3 | Nya leads efter innehåll (endast CRM-rapporter)**

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vad <i>innehåll</i> påverkar Leads till skapande?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)</td> 
  </tr>
  <tr>
   <td>Datumfält</td> 
   <td>Lead skapad den</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Landningssida <br> 
   Formulär-URL</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Första beröring, Lead-skapande, <strong>U-Shaped</strong><br></td> 
  </tr>
 </tbody>
</table>

**PÅMINNELSE**: De två primära fälten för rapportering av digitalt innehåll/digitala resurser är Landing Page och Form URL. Dessa två värden kan vara desamma om leadet konverterar (skickar ett formulär) på samma sida som de&quot;landade&quot; (landningssida), _men_, ibland är värdena olika. Lead-instansen kan till exempel klicka på en länk på Facebook som tar dem till en sida på webbplatsen (det är värdet för Landing Page). Lead kan sedan navigera bort från den sidan, fortsätta sin session på webbplatsen och skicka ett formulär på en annan sida (formulär-URL). Detta sammanfattas i en enda kontaktyta som representerar var leadet kommer från (marknadsföringskanal), vilket innehåll som förde dem till webbplatsen (landningssida) och vilket innehåll som laddades ned (formulär-URL). &#39;Formulär-URL&#39; är också det go-to-fält som används för att rapportera andra formulär som inte är kopplade till hämtningsbart innehåll, till exempel &#39;Kontakta oss&#39; eller &#39;Demo-begäran&#39;.

>[!TIP]
>
>Få insikter i specifikt &#39;innehåll&#39; med ytterligare filter
>
>* Filtrera efter: &#39;Landing Page&#39; INNEHÅLLER (till exempel):
>   * /blog
>   * /ebook
>   * /webinar
>
>* ELLER: &#39;Formulär-URL&#39; INNEHÅLLER (till exempel)
>   * /contact
>   * /demo

Innehållsbaserade rapporter tillför mycket värde vid rapportering på valfri del av tratten, men de används oftast högst upp i tratten för att ge ytterligare insikter i ett inledande engagemang för leads. Med tanke på att&quot;organisk sökning&quot; ofta är den starkaste kanalen när det gäller att skapa ett första engagemang (FT), finns det inte så mycket data på kampanjnivå.

Innehållsbaserade rapporter är bra för att få insikt i vad som genererar leads mer specifikt inom den högre nivån av marknadsföringskanalen, i det här fallet&quot;Organic Search&quot;.

**1.4 | Totalt lead-engagemang i ett givet datumintervall**

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler har haft mest <i>totalt Lead-engagemang</i> under det senaste (vecka/månad/kvartal)?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br> 
   Mått: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Kontaktpunktsdatum</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal (eller mer detaljerad)</td> 
  </tr>
  <tr>
   <td>Optimala modeller*</td> 
   <td>*Den här rapporten handlar mindre om att mäta var leads kommer från med en attribueringsmodell, men mer om det <i>totala antalet kontaktytor (mängden engagemang)</i>, inklusive dem som kommer efter att leadgenereringen trycks. Det totala antalet kontaktpunkter i registret skulle återspegla vilka kanaler som har sett störst engagemang i leads.</td> 
  </tr>
 </tbody>
</table>

**PÅMINNELSE**: Att basera dina rapporter på &#39;Touchpoint Date&#39; är det mest reflekterande sättet att förstå marknadsföringsprestanda under ett visst datumintervall. &#39;Slutpunktsdatum&#39; strukturerar rapporten på ett sätt där attribueringen inte bara är relaterad till kanalen, kampanjen eller innehållet, utan även visar när kontaktytan inträffade. Detta är det mest effektiva sättet att förstå vilket marknadsföringsengagemang som inträffade vid en viss tidpunkt och även det rekommenderade sättet att mäta marknadsföringens effekt i jämförelse med marknadsföringsutgifter som investerats under samma tid. Det rekommenderas när man gör marknadsföringsinvesteringar eller analyser av avkastningen (se 5.1).

**2. MARKNADSFÖRING AV KVALIFICERADE LEDARE MED TOUCHPOINTS FÖR KÖPARE**

En av de vanligaste rapporterna handlar inte bara om nya leads eller engagemang på leadnivå, utan snarare om&quot;marknadsföringskvalificerade leads&quot; (MQL). Det finns ett par olika tillvägagångssätt när det gäller att rapportera MQL:er beroende på vilka [!DNL Marketo Measure]-funktioner du har tillgång till.

**2.1 | Marknadsföringskvalificerade leads efter kanal (multi-touch)**

Detta tillvägagångssätt för att mäta effekten av marknadsföringen på att påverka MQL:er är i princip en fortsättning på rapporten&quot;New Leads by Marketing Channel&quot; (1.1), men med de ytterligare kriterier som de leads som mäts är mer specifikt MQL:er. Den U-formade attribueringsmodellen rekommenderas fortfarande här för att identifiera vilka marknadsföringskanaler och vilket innehåll som genererar leads som sedan _troligtvis_ blir en MQL:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler är bäst på att generera nya leads som blir <i>MQL</i>?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br> 
   Mått: Leads ([!DNL Marketo Measure] Discover)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>MQL = true*<br>
   *<i>MQL:er kan definieras på olika sätt i olika organisationer. Se till att rapporten [!DNL Marketo Measure] filtreras efter MQL:er med samma fält som andra MQL-baserade rapporter. Ett segmentfilter måste skapas på samma sätt för rapportering av MQL i [!DNL Marketo Measure] Discover.</i></td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>MQL-datum (eller motsvarande)/Skapat den ([!DNL Marketo Measure] Discover)<br> <i>Lead skapad-datum kan också användas i CRM-rapportering om MQL-datum inte är ett alternativ i CRM. Det är viktigt att tänka på vilket datumfält du använder för att definiera den kohorterade datauppsättningen.</i></td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Första beröring, Lead-skapande, <strong>U-Shaped</strong><br> 
   SUM-fälten Antal i CRM-rapporterna (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

**2.2 | Marknadsföringskvalificerade leads efter kanal (endast en pekning, endast CRM)**

Det här tillvägagångssättet för att mäta marknadsföringens påverkan på att påverka MQL:er är mer inriktat på att identifiera vilken _enskild kontaktyta_ som var den sista kontakten innan Lead nådde MQL.

>[!NOTE]
>
>För att kunna köra den här rapporten krävs ett &#39;Lead Status&#39;-värde på &#39;MQL&#39; för att definiera MQL-scenen för spårningsändamål (trattfas). Om MQL:er inte spåras via fältet Lead Status krävs funktionen Custom Attribution Model with Custom Stages för att skapa en anpassad MQL-scen i kontoinställningarna för [!DNL Marketo Measure].

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler är bäst på att få leads att nå MQL-status?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   <i> Den här rapporten är bara möjlig i CRM-rapporter. Det går inte att filtrera på vissa värden för 'Touchpoint Position' i [!DNL Marketo Measure] Discover</i></td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td><strong>Pekpunktsposition INNEHÅLLER "MQL"</strong></td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>MQL-datum (eller motsvarande)</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td><i>Eftersom den här rapporten filtreras på en enda kontaktyta är attribueringsmodellerna på leadnivå inte så relevanta. Precis som i rapporten"Lead Engagement Report" (1.4) skulle antalet kontaktpunktsposter användas här för att förstå vilka kanaler som är störst (varje lead skulle bara ha en MQL-kontaktyta).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Utforska andra grupperingar eller dimensioner för att få ytterligare insikter i MQL:er. Som nämndes i de andra rapporterna om leads med Buyer Touchpoints erbjuder Buyer Touchpoint mycket mer detaljrikedom än bara Marketing Channel. En&quot;innehållsbaserad&quot; rapport kan också kombineras med någon av MQL-rapporterna ovan för att bättre förstå vilket innehåll som bäst påverkar MQL:er.

**3. [!DNL MARKETO MEASURE] PERSONER MED TOUCHPOINTS FÖR KÖPARE**

Det finns ett tredje anpassat [!DNL Marketo Measure]-objekt i Salesforce som kan vara mycket användbart när du rapporterar personrelaterade mått: **den [!DNL Marketo Measure] personen (BP)**. BP löser det gamla problemet med att representera information om både leads och kontakter i samma rapport. Den förenar alla BT som är relaterade till en person (en [!DNL Marketo Measure]-persons ID är deras e-postadress). Vare sig de finns som lead eller kontakt fungerar BP som ett bryggobjekt, vilket gör det lättare att rapportera mellan lead och kontakt, och är mycket användbart när det gäller att skapa mer avancerade rapporter om människor.

Personen [!DNL Marketo Measure] relaterar endast till ett av kontaktobjekten, Buyer Touchpoint (BT). Det innebär att det inte kan användas för en säljprojekts- eller intäktsrelaterad mätning. En rapporttyp [!DNL Marketo Measure] person och Buyer Touchpoints är mycket bra för att förstå _totalt engagemang_ eftersom den BT allt om BT relaterar till en lead eller kontakt mer specifikt. Om du till exempel har en Salesforce Campaign som används för att spåra en händelse kan du ha kampanjmedlemmar i CRM-kampanjen som antingen finns som leads eller kontakter. [!DNL Marketo Measure] skapar kontaktytor för kampanjmedlemmarna oavsett, men utan personen [!DNL Marketo Measure] krävs det två separata rapporter för Salesforce-standardsrapportering för att förstå hur många _totalt_ kontaktytor du har från händelsen: en som är&quot;Leads with Buyer Touchpoints&quot; och en som är&quot;Kontakter med Buyer Touchpoints&quot;. Några andra [!DNL Marketo Measure] personbaserade användningsexempel för rapportering visas nedan:

**3.1 [!DNL Marketo Measure] Personer som har laddat ned e-böcker eller rapporter (totalt antal nedladdningar)**

Den här rapporten skulle vara densamma som en Content-baserad rapport på Lead-nivå. I stället för att försöka mäta antalet möjliga leads för varje del av innehållet, kan det vara bra att använda en [!DNL Marketo Measure]-rapport för personer för att förstå det totala _antalet hämtningar_ om resursen är tillryggalagd (det totala antalet kontaktytor representerar det totala antalet hämtningar/inskickade formulär).

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Hur många har laddat ned en viss resurs?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>[!DNL Marketo Measure] Kontaktpunkter för personer och köpare (CRM)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>'Formulär-URL' INNEHÅLLER (till exempel)<br>
   <li>/ebook</li>
   <li>/whitepaper</li>
   <i>Filtervärdena ovan är endast exempel. Det faktiska värdet baseras på varje organisations URL-struktur.</i></td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Slutpunktsdatum <i> (när hämtades resursen)</i></td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Formulär-URL</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Den här rapporten handlar mindre om att mäta var leads eller kontakter kommer från med en attribueringsmodell, men mer om det <i>totala antalet kontaktytor (mängden engagemang)</i>, inklusive dem som kommer efter leadskapandeberöringen. Med den här rapporten försöker vi förstå <i>mängden totalt engagemang</i>. Det totala antalet poster för kontaktytor skulle återspegla vilka resurser som har laddats ned mest.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Börja med att anpassa den fördefinierade rapporten **[!DNL Marketo Measure]101 för alla rapporttyper för Leads med [!DNL Marketo Measure] Personer | Leads/kontakter efter kanal**. Den här rapporten är tillgänglig direkt och är en utmärkt [!DNL Marketo Measure]-baserad sandlåda. Den är fördefinierad och kan snabbt anpassas för mer specifika rapporteringsbehov.

>[!TIP]
>
>Du kan använda den här rapporten för att få insikt i det totala engagemanget för alla marknadsföringsdimensioner från Buyer Touchpoint-objektet, inte bara för innehållsnedladdningar som presenteras i exemplet. Rapporten kan istället grupperas eller filtreras efter dimensioner som&quot;Marknadskanal&quot; eller&quot;Namn på annonskampanj&quot; för att på bästa sätt förstå det totala engagemanget från både leads och kontakter i databasen. Ändra filter eller grupperingar i rapporten till noll i andra dimensioner som representeras av andra fält från kontaktobjektet.

**3.2 [!DNL Marketo Measure] Personer som har registrerats för en händelse (endast CRM)**

_Den här rapporten gäller endast om registreringsformulär finns på din eller dina webbplatser som [!DNL Marketo Measure] kan spåra digitalt._

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler driver min anmälan till event?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>[!DNL Marketo Measure] Kontaktpunkter för personer och köpare (CRM)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>'Formulär-URL' INNEHÅLLER (till exempel)<br>
   <li>/event</li>
   <i>Filtervärdet ovan är bara exempel. Det faktiska värdet baseras på varje organisations URL-struktur.</i></td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Slutpunktsdatum <i> (när registreringsformuläret skickades)</i></td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Formulär-URL <br>
   Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Den här rapporten handlar mindre om att mäta var leads eller kontakter kommer från med en attribueringsmodell, men mer om det <i>totala antalet kontaktytor (antal registreringar)</i>, inklusive dem som kommer efter att lead skapas. Med den här rapporten vill vi få insikt i vad som driver evenemangsregistreringar. Det totala antalet kontaktpunkter per"marknadsföringskanal" återspeglar vilka kanaler som drev flest registreringar.</td> 
  </tr>
 </tbody>
</table>

Det viktigaste med den här rapporten är att Buyer Touchpoint data också kommer att tillhandahålla data för marknadsföringskanalen. Även om ni redan har insikter om antalet personer som har registrerat sig för era evenemang, kommer den här rapporten även att ge insikter om vilka digitala marknadsföringskanaler, källor och/eller kampanjer som tar personer till er webbplats för att sedan registrera sig för evenemanget.

>[!TIP]
>
>Samma tillvägagångssätt kan användas när man vill få insikt i webbinarier eller kanske hämta webbinarier på begäran (om de är en speciell tillgång). Den enda skillnaden är filtervärdet i formulär-URL:en om formulären finns på webbplatsens unika sidor. Målet är dock detsamma. Det besvarar frågorna:&quot;Vilka av mina marknadsföringskanaler är det som driver de flesta nedladdningar av webbinarier som registreras/hämtas on demand.

**3.3 [!DNL Marketo Measure] Personer med Buyer Touchpoints (Touchpoint-validering)**

Med tanke på att personen [!DNL Marketo Measure] tillåter oss att rapportera alla kontaktytor i en enda rapport, är det den idealiska rapporttypen som används när vi vill validera dina data. Vi vill försäkra oss om att vi inte missar några kontaktytor som kan avslöja var det till exempel finns ett problem i konfigurationen av dina marknadsföringskanaler (se supportartiklarna nedan för mer information om hur du konfigurerar dina marknadsföringskanaler).

* [Anpassade kanalinställningar online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md){target="_blank"}
* [Inställningar för anpassad kanal offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md){target="_blank"}

Kontaktpunktsdata återspeglar i princip vad som har spårats av [!DNL Marketo Measure] och kan granskas för att säkerställa att konfigurationen matchar indata baserat på exempelvis UTM-parametervärden, referenssidor eller kampanjtyper. Om kontaktpunktsdata inte matchar din konfiguration måste något som troligen behöver justeras. Utöver konfigurationen av marknadsföringskanalen kan du titta på kontaktpunktsdata för att avgöra vilka kontaktytor som kan behöva [undertryckas](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) eller [segmenteras](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md){target="_blank"}. Vi rekommenderar att du granskar dina kontaktpunktsdata i en [!DNL Marketo Measure]-rapport för personer och köpare vid slutet av varje månad eller kvartal om det är möjligt. Detta säkerställer att attribueringen blir så korrekt som möjligt. The [!DNL Marketo Measure] 101 | Leads/Kontakter per kanal-rapport som är tillgänglig utan uppdatering är en bra startpunkt. Inkludera följande fält om de inte redan finns med för att granska några av de viktigaste konfigurationsbitarna:

* **Marknadsföringskanal** - Sökväg = Marknadskanal.Subkanal (värden anges i [!DNL Marketo Measure])
* **Touchpoint Source** = utm_source
* **Medium** = utm_medium (kontaktpunkter online) eller CRM-kampanjtyp (kontaktpunkter offline)
* **Referenssida** (använder konfigurationen Onlinekanaler)
* **Landningssida - Raw** (som används i konfigurationen för onlinekanaler) är också en vanlig inmatning för inaktivering av kontaktyta på fliken &#39;Slutpunktsinställningar&#39; i inställningarna
* **Formulär-URL** (en vanlig inmatning för inaktivering av kontaktpunkter på fliken &#39;Touchpoint Settings&#39; i dina inställningar)

**BUYER ATTRIBUTION TOUCHPOINT (BAT)**

Kontaktpunkterna för Buyer Attribution (BAT) representerar de relevanta kontaktytorna för alla kontakter som är kopplade till säljprojektet (antingen via roller för säljprojektskontakt eller via ett delat konto-ID, beroende på dina inställningar). Till skillnad från BT (som i huvudsak är kopplade till människor) kan BAT vara kopplade till intäkter. Därför använder du BAT för att svara på frågor som rör affärsmöjligheter, i första hand öppna _Affärsmöjligheter/Pipeline-intäkter_ och stängde _Affärsmöjligheter/erbjudanden/intäkter_. En BAT skapas via en kontakts BT så snart en möjlighet skapas under samma konto som kontakten (BT konverteras inte till en BAT. BT data refereras bara till för att skapa ytterligare en post - BAT som sedan relaterar till säljprojektet).

Med Buyer Attribution Touchpoint kan vi mäta marknadsföringens påverkan djupare. _Djupet på tratten som du vill mäta kan representeras av de olika multitouch-attribueringsmodellerna_.

BAT primära relationen är säljprojektet, används de för att svara på frågor som:

* Vilken av mina marknadsföringssatsningar har påverkat de största möjligheterna?
* Hur mycket nya intäkter kan jag tillföra varje marknadsföringskanal?
* Vilken av mina kampanjer fick störst avkastning förra kvartalet?

[attribueringsmodellerna](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md){target="_blank"} som ger bästa insikt i säljprojektsbaserade mått är:

**W-Shaped** - _Pipeline-modellen_. Tre milstolpekontaktytor ingår i W-Shaped-modellen. I den här modellen tillskrivs kontaktytorna FT, LC och OC 30 % av attribueringskrediten. Återstående 10 % fördelas jämnt på alla mellanliggande kontaktytor som inträffar mellan de tre milstolppunkterna.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-2.png"></td> 
   <td>I den här modellen sammanfattas i huvudsak kundresan till ett nytt säljprojekt som vanligen är synonymt med genereringen av nya Pipeline-intäkter.<p>
   <p>
   Vi rekommenderar W-Shaped-modellen när vi vill mäta hur marknadsföringen påverkar nya affärsmöjligheter eller hur ny pipeline genereras.</td> 
  </tr>
 </tbody>
</table>

**Fullständig sökväg** - _Sluten Won-modell_. Denna modell innehåller fyra milstolpar: FT, LC, OC och Closed. Var och en ges 22,5 % av säljprojektskrediten och de återstående 10 % fördelas jämnt mellan de mellanliggande kontakterna.

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-3.png"></td> 
   <td>I den här modellen sammanfattas i stort sett kundresan för en stängd egen affär som vanligen är synonym med stängda egna intäkter/bokningar.<p>
   <p>
   När man vill mäta marknadsföringens påverkan på avgivna erbjudanden eller stängda egna intäkter rekommenderar vi en fullständig kundvägsmodell.</td> 
  </tr>
 </tbody>
</table>

I den här modellen sammanfattas i stort sett kundresan för en stängd egen affär som vanligen är synonym med stängda egna intäkter/bokningar.

När man vill mäta marknadsföringens påverkan på avgivna erbjudanden eller stängda egna intäkter rekommenderar vi en fullständig kundvägsmodell.

**Anpassad** - [!DNL Marketo Measure] erbjuder också en modell för anpassad attribuering som gör att användare kan välja vilka kontaktytor eller anpassade stadier som ska ingå i modellen. Dessutom kan användarna styra den procentandel av attribueringskrediten som tilldelats dessa kontaktytor och faser. Beroende på hur din anpassade modell är konfigurerad kan den användas på bästa sätt för att mäta antingen säljprojekt och pipeline ELLER, erbjudanden och slutna vinjetter. Tänk på detta när du använder det i din rapportering.

>[!NOTE]
>
>Custom Attribution Model är en extra funktion som inte är tillgänglig för alla kunder. Kontakta kontogruppen på Adobe (din kontohanterare) om du vill veta mer om hur du lägger till den här funktionen i ditt konto.

Vanligtvis måste marknadsförarna veta, &quot;varifrån kommer mina affärsmöjligheter?&quot;. På samma sätt som vid rapportering på leadnivå besvarades den här frågan historiskt med ett enda endimensionellt värde (t.ex. Source för primär kampanj). Vi vet dock att mycket mer går in på att utveckla ett säljprojekt än en enda kontaktyta från en enda kontakt. Det finns ofta flera kontaktytor från olika kanaler och från flera intressenter som påverkar möjligheterna att skapa. Med [!DNL Marketo Measure] kan vi identifiera alla kontaktytor från ett konto för att bäst förstå var ett säljprojekt kommer ifrån. Utöver detta kan vi dock fortsätta att identifiera alla kontaktytor som har inträffat efter att affärsmöjligheten har skapats och fram till den punkt där affärsmöjligheten har stängts. Detta gör att vi inte bara kan använda en strategi där flera kontaktytor tas för att förstå var ett säljprojekt kommer ifrån, utan även vad som påverkade det att avsluta och slutligen representera slutna vinstintäkter. Detta ger insikt i olika frågor, till exempel &quot;vad påverkar marknadsföringen på att påverka avtal att sluta?&quot;, &quot;vilken marknadsföring driver stängda Vinner Revenue?&quot; och slutligen, &quot;vilket av mina marknadsföringssatsningar får störst avkastning?&quot;

## REKOMMENDERADE RAPPORTER MED BUYER ATTRIBUTION TOUCHPOINT (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4.1 | Nya affärsmöjligheter efter marknadsföringskanal**

Att sammanfatta era affärsmöjligheter med Buyer Attribution Touchpoint-data i fältet Marknadsföringskanal är den högsta nivån som representerar vilka kanaler/taktik som påverkar nya möjligheter till skapande. Genom att strukturera den här rapporten runt ett&quot;Datumtyp&quot; =&quot;Skapad affärsmöjlighet&quot; säkerställer vi att vi också sammanfattar rapporten baserat på när affärsmöjligheten skapades i CRM. Kontaktpunkterna kan ha kommit från en tid tidigare, men de kommer fortfarande att relatera till de affärsmöjligheter som har skapats inom det definierade datumintervallet och därmed få attribueringskrediter eftersom de anses påverka affärsmöjligheten.

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka <i>marknadsföringskanaler</i> påverkar möjligheter att skapa?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer-attribuering med säljprojekt (CRM)<br> 
   Mått: Affärsmöjligheter ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Fas för affärsmöjlighet* <i> (valfritt beroende på vilka specifika affärsmöjligheter du kan vilja begränsa till rapporten. Du kanske bara vill rapportera om BAT som fortfarande är kopplade till endast 'Öppna'-affärsmöjligheter (till exempel)</i></li>
   <li>Affärsmöjlighetstyp (det är vanligt att filtrera in vissa affärsmöjligheter, dvs."Nytt företag", till skillnad från <i>alla</i> -affärsmöjligheter)</li><br>
   *Ett segmentfilter för säljprojektstyp ska användas i [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Skapad affärsmöjlighet (CRM) / Skapad (Discover)</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td><strong>W-Shaped</strong><br>
   SUM-fälten W-Shaped i CRM-rapporterna (Count - W-Shaped, Revenue - W-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>För rapporttypen Buyer Attribution Touchpoints with Opportunity kan du börja med att anpassa den fördefinierade rapporten [!DNL Marketo Measure] 101 | Affärsmöjligheter efter kanal. Den här rapporten är tillgänglig direkt och är en utmärkt sandlåda som är fördefinierad enligt beskrivningen i tabellen ovan och kan snabbt anpassas för mer specifika rapporteringsbehov (rapporten använder en modell med fullständig sökväg som är färdig att användas så se till att rapporten anpassas så att den inkluderar alla andra attribueringsmodeller, i det här fallet W-Shaped-modellen).

>[!TIP]
>
>Den rapport som beskrivs ovan skulle också användas när man vill förstå hur mycket valuta som också bör tillskrivas. Vid rapportering på säljprojektsnivå med BAT finns det två nyckelvärden som kan sammanfattas: valuta (säljprojektsbeloppet) och själva säljprojektsposten. I exemplet ovan mäter vi mer specifikt öppna möjligheter och nya intäkter från pipeline.

>[!TIP]
>
>Få ännu mer detaljerad information genom att sammanfatta rapporten med andra tillgängliga fält från Buyer Attribution Touchpoint-objektet. Detta görs på samma sätt som på nivån Lead med Buyer Touchpoints (1.2). Det gör du genom att lägga till ytterligare grupperingar (CRM) eller dimensioner (Discover). Beroende på vilken kanal (som kanske representerar din roll) kan det finnas ytterligare information utöver den kampanjnivå där du vill få mer information. Vi går in på Betald sökning nedan:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka <i>nyckelord</i> från mina betalsökannonser genererar flest intäkter i pipeline?
</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer-attribuering med säljprojekt (CRM)<br> 
   Mått: Affärsmöjligheter ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Marknadsföringskanal = betald sökning</li>
   <li>Fas för affärsmöjlighet* <i> (valfritt beroende på vilka specifika affärsmöjligheter du kan vilja begränsa till rapporten. Det här exemplet är baserat på Pipeline-intäkt som definieras i [!DNL Marketo Measure] av"Öppna" säljprojekt som representerar potentiella intäkter/öppen pipeline)</i></li>
   <li>Affärsmöjlighetstyp (det är vanligt att filtrera in vissa affärsmöjligheter, dvs."Nytt företag", till skillnad från <i>alla</i> -affärsmöjligheter)</li><br>
   *Ett segmentfilter för säljprojektstyp ska användas i [!DNL Marketo Measure] Discover</td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Skapad affärsmöjlighet</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Nyckelordstext (CRM)<br> 
   Nyckelord (Upptäck)</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td><strong>W-Shaped</strong><br>
   SUM-fälten W-Shaped i CRM-rapporterna (Count - W-Shaped, Revenue - W-Shaped)</td> 
  </tr>
 </tbody>
</table>

**4.2 | Erbjudanden per marknadsföringskanal**

Denna rapport skulle i stort sett vara densamma som det första exemplet från Buyer Attribution Touchpoint (4.1) förutom att mätvärdena nu har ändrats från öppna säljprojekt till stängda vunna avtal. Mätvärdet ska alltid vara det som anger vilken attribueringsmodell som ska användas. Med tanke på att vi nu tittar på stängda kundresor och deras relaterade BAT, bör vi använda en modell som representerar hela köparens resa (avtal). Detta garanterar att alla marknadsföringstester under kundresan får attribueringskrediter:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka <i>marknadsföringskanaler</i> påverkar avtal som ska stängas?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer-attribuering med säljprojekt (CRM)<br> 
   Mått: Erbjudanden ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Affärsmöjlighetens stadium (<i>endast stängda affärsmöjligheter ska finnas i rapport</i>) ELLER,</li>
   <li>Won-affärsmöjlighet = Sant</li>
   <li>Affärsmöjlighetstyp (det är vanligt att filtrera in vissa affärsmöjligheter, dvs."Nytt företag", i motsats till alla affärsmöjligheter)<br>
   </td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>Stängningsdatum för affärsmöjlighet</td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td><strong>Fullständig sökväg</strong><br>
   SUM fälten Fullständig sökväg i CRM-rapporterna (Count - Full Path, Revenue - Full Path)</td> 
  </tr>
 </tbody>
</table>

**PÅMINNELSE**: Det är viktigt att komma ihåg att filtrera efter de specifika affärsmöjligheter som du vill inkludera i BAT-baserad rapportering, särskilt när det gäller Öppna affärsmöjligheter och Försäljning i pipeline jämfört med Avdrag och Avslutade Vinstintäkter. Detta görs vanligtvis via ett &#39;säljprojektsstadiefilter&#39; (filtret &#39;säljprojekt&#39; = sant/falskt kan också vara mycket användbart här).

>[!MORELIKETHIS]
>
>[Ny handbok för Discover Dashboard](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
