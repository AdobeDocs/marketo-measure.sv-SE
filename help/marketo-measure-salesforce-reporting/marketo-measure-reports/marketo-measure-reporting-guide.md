---
description: "[!DNL Marketo Measure] Rapporteringsguide - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Rapportguide"
exl-id: 9b991f9e-c187-4b43-b0a8-8ed3e9a6056b
source-git-commit: 51397a02872035fef41d308c1f855bcaecc29c4e
workflow-type: tm+mt
source-wordcount: '6395'
ht-degree: 0%

---

# [!DNL Marketo Measure] Rapporteringshandbok {#marketo-measure-reporting-guide}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Innan du skapar en [!DNL Marketo Measure] är det viktigaste att bekräfta [!DNL Marketo Measure] Kontoinställningarna har granskats och konfigurerats för att säkerställa att data i rapporterna är korrekta och att de återspeglar ditt företags särdrag. Dessutom fungerar rapportprojekt bäst när de följer en strukturerad process. Justin Norris, a [!DNL Marketo Measure] avancerade användare, förespråkare och partner från [Perkuto](https://perkuto.com/) i sammanfattad form [hur rapportering ska ske i [!DNL Marketo Measure]](https://perkuto.com/blog/turning-attribution-data-into-actionable-insights/):

**Upprätta mål**: &quot;Den första frågan att ställa är &#39;varför mäter vi?&#39; Lori Wizdo of [Forrester Research](https://go.forrester.com/) sammanfatta det fint i en [Marketo webbinarium](https://www.marketo.com/webinars/beyond-revenue-performance-real-kpis-of-b2b-marketing/). Enligt henne mäter vi för att bevisa eller validera ett beslut eller värdet av marknadsföring eller för att bli bättre (processförbättring). Vi skulle också vilja tillägga att insikterna från god mätning också ger indata och vägledning i marknadsföringsplaneringsprocessen.

Innan du börjar är det viktigt att du är tydlig med dina mål, de frågor du försöker svara på eller de problem du försöker lösa. Vilken historia vill du berätta? Vilka beslut kommer att fattas till följd av detta? Alltför ofta är dessa grundläggande faktorer dåligt genomtänkta, vilket leder till frustration för alla inblandade.&quot;

**Rapportdesign**: &quot;Därefter måste ni utforma rapporten och fastställa de specifika dimensioner, mätvärden och datauppsättningar som den ska innehålla. En vanlig upplevelse är att ge en företagsanvändare exakt det de vill ha, bara för att de fortfarande känner att deras behov inte uppfylls. Det beror på att den insikt som en affärsanvändare faktiskt letar efter inte alltid finns i den rapport de begär. En bra analytiker (eller en MOPS-person med en analytiker som sitter på) kommer att ställa klargörande frågor, fastställa gemensamma definitioner (&quot;så, vad menar du egentligen med lead?&quot;) och till och med skissa en bild av slutrapporten för att se till att det finns en anpassning. Det är enda sättet att ta fram rapporten i vetskap om att du har en gedigen uppsättning krav.&quot;

**Report Build**: &quot;När man väl har börjat bygga är det inte ovanligt att man stöter på vägspärrar eller ändpunkter. Du kanske upptäcker att du saknar en viktig datapunkt eller att dina objekt inte länkas på det sätt du behöver. För att lösa dessa problem tycker jag också att det är viktigt att förstå vad som händer &quot;under huven&quot; i din rapporteringsmaskin. Tack vare denna smidighet kan ni snabbt anpassa en rapportförfrågan och utvärdera om den är genomförbar (och enklare ta fram kreativa lösningar när den inte är det).&quot;

Låt oss titta &quot;under huven&quot; för att bättre förstå vad som gör [!DNL Marketo Measure] körning av attribueringsrapporteringsmaskin.

## CRM (Buyer Touchpoint Objects) {#buyer-touchpoint-objects-crm}

På den högsta nivån finns det två rapporteringskategorier som baseras på de två olika Buyer Touchpoint-objekten: Dessa kategorier avgör vilken typ av [!DNL Marketo Measure] data som du vill rapportera om: data relaterade till en _individuell_ eller data som är relaterade till en _tillfälle_.

1. **Kontaktpunkter för köpare** (BT) / Individuella / Total Engagement

   * Används vanligen för TOFU-värden (Top of the Trnel) och rapportering relaterade till _enskilda_ (Leads, Kontakter, [!DNL Marketo Measure] Personer)
   * BT används för att förstå alla marknadsföringsinteraktioner relaterade till **människor**, eftersom de innehåller den fullständiga kontaktytehistoriken för varje person. Som påminnelse skapas dessa kontaktytor i CRM för den anonyma First Touch, Lead Creation Touch och efterföljande formulärinskickning eller kontaktyta som du väljer att synkronisera från en offlinekampanj eller aktivitet.

1. **Touchpoints för Buyer-attribuering** (BAT) / Möjligheter / Kontonivå / Intäkter

   * Används vanligen för&quot;trattens mitt och/eller botten&quot; (MOFU och BOFU) mått och rapportering relaterade till _Möjligheter_.
   * BAT representerar de relevanta kontaktytorna för alla personer som är anslutna till **tillfälle** (antingen via Roller för säljprojektskontakt eller via ett delat konto-ID, beroende på dina inställningar). Till skillnad från bärbara datorer som bara gäller människor kan BAT-enheter även kopplas till **omsättning**. Därför kommer ni att använda BAT för att besvara frågor som rör möjligheter, inklusive hur många möjligheter som öppnats eller stängts, eller pipeline-värdet och intäkterna.

>[!NOTE]
>
>BAT skapas från BT. I princip börjar spårningen på individnivå via BT. När ett säljprojekt har skapats på ett konto refereras och är berättigade att skapa BAT-böcker som relaterar till säljprojektet, så du vill använda den ena eller den andra beroende på vilka frågor du försöker svara på: frågor relaterade till &#39;personstatistik&#39; (BT-rapporter), eller frågor relaterade till &#39;säljprojektsstatistik&#39; (BAT-rapporter)

Supportartikel: [Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md#configuration-and-setup)

## Kontaktpunkt för köpare (BT) {#buyer-touchpoint-bt}

Buyer Touchpoint (BT) är det objekt som används för att spåra varje marknadsföringsinteraktion någon har med ert marknadsföringsmaterial. Var och en av individerna (Lead/Contact/[!DNL Marketo Measure] Personen) skulle representeras av deras närstående BT:er. I [!DNL Marketo Measure], en individs resa består av

1. Hur interagerade den här personen först med vårt varumärke? (First Touch eller _FT_)
1. Hur konverterade/blev den här personen känd/blev en lead? (Lead Creation eller _LC_)
1. Hur har den här personen annars interagerat med vårt varumärke och marknadsföringsmaterial sedan han blev en ledare? (_PostLC_)

Kontaktpunkter för köpare används för att svara på frågor som rör _människor_ (&quot;personer&quot; representeras antingen av Leads eller Kontakter i en CRM), t.ex. lead-/kontaktgenerering eller kundvärdesstatistik, i stället för säljprojektsrelaterade mått. Exempel:

* Vilka kanaler levererar mest leads?
* Vilka kanaler kostar mer eller mindre att skapa en ny lead?
* Vilket innehåll engagerar mina leads/kontakter?
* Vad är marknadsföringsberättelsen om särskilda titlar, roller, personer?
* Vilka kanaler driver MQL:er eller andra lead-/kontaktstatusar?

I första hand måste företagen veta,&quot;var kommer mina leads/kontakter?&quot;. Historiskt sett besvarades detta med ett enda endimensionellt värde (t.ex. Leadkälla). Som framgår av #1 och #2 ovan vet vi dock att leads kan ha flera kontaktytor under sin resa som lead. Med Buyer Touchpoint kan vi få insikt i de två viktigaste interaktionerna som visar hur en lead genererades: sin First Touch och sin Lead Creation Touch. Kontaktpunkterna för köpare är också _flerdimensionell_ innebär att de bär på mängder av marknadsföringsdata, främst där personen kom från (marknadsföringskanal) och vad personen interagerar med (Innehåll).

The [attribueringsmodeller](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) De bästa insikterna om personbaserade mätvärden är följande:

* **Första beröring** - 100 % attribueringskreditering till Leads First Touch (FT)
* **Skapa leads** - 100 % attribueringskrediter till Lead&#39;s Lead Creation Touch (LC)
* **U-formad** - multi-touch-strategi, med 40 % kredit till FT, 40 % kredit till LC

<table> 
 <tbody>
  <tr>
   <td><img src="assets/bizible-reporting-guide-1.png"></td> 
   <td>U-Shape-modellen är utformad för att belöna alla Buyer Touchpoints som sammanfattar hur en lead blev en lead. Efterföljande kontaktytor från dessa leads kan också rapporteras för att förstå ytterligare engagemang (Post LC), men de ingår inte i <strong>Lead Creation - resa</strong> så att de inte får någon attribueringskrediter i FT-, LC- eller U-formade modeller.<p>

&#42;Det vanligaste är att U-formad attribuering återspeglar en till och med 50/50 delning mellan FT och LC. Om leadet konverteras i samma session som First Touch representerar en enda kontaktyta både FT- och LC-beröringspunktspositionerna. Därför skulle 100 % av attribueringen ges till en enda kontaktyta.</td>
</tr>
 </tbody>
</table>

Dessa modeller lägger stor vikt vid interaktioner i ett tidigt skede och ett engagemang i tratten. U-Shaped-attribuering är den rekommenderade modellen eftersom den tar hänsyn till både FT- och LC-kontaktytorna, vilket säkerställer att all beröring som påverkade leadet kan komma till sin rätt. Men ytterligare insikter kan ni få från Touch-modellerna First Touch och Lead Creation Touch om ni vill förstå dessa specifika delar av leadresan mer i detalj.

## Rekommenderade rapporter med Buyer Touchpoint (BT) {#recommended-reports-using-the-buyer-touchpoint-bt}

1. **LEADS with BUYER TOUCHPOINS**

**1.1 | Nya leads per marknadsföringskanal**

Att sammanfatta leadets data om köparens kontaktpunkt med fältet Marknadskanal är den översta nivån som representerar vilka kanaler/taktik som påverkar nya leads i skapandet. Om du strukturerar den här rapporten runt en datumtyp = Skapad den skapas en kohort med nya lead (när lead skapades i CRM) som skapas i rapporten.

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler påverkar leads till skapandet?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Upptäck)</td> 
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
   <td>First Touch, Lead Creation, <strong>U-formad</strong><br>
   *SUMMA fälten Antal i dina CRM-rapporter (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>För rapporttypen Leads with Buyer Touchpoints kan du börja med att anpassa den färdigbyggda rapporten som heter[!DNL Marketo Measure] 101 | Leads by Channel&#39;. Den här rapporten finns tillgänglig när den är färdig och är en utmärkt sandlåda som är fördefinierad enligt beskrivningen i tabellen ovan och kan snabbt anpassas för mer specifika rapporteringsbehov.

**1.2 | Nya leads per kampanj (eller mer detaljerade insikter)**

Om du vill ha mer detaljerad information om de data som sammanfattas i rapporten&quot;New Leads by Marketing Channel&quot; (1.1) lägger du till ytterligare en sammanfattning på kampanjnivå. På så sätt kan ni inte bara förstå vad&quot;marknadsföringskanaler&quot; driver nya leads till skapande, utan snarare vilka kampanjer i dessa kanaler som fungerar bäst:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vad <i>kampanjer</i> Påverkar Leads till skapande?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Upptäck)</td> 
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
   <td>First Touch, Lead Creation, <strong>U-formad</strong><br>
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
   <td>Vad <i>nyckelord</i> Påverkar Leads till skapande?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   Mått: Leads ([!DNL Marketo Measure] Upptäck)</td> 
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
   <td>First Touch, Lead Creation, <strong>U-formad</strong><br>
   *SUMMA fälten Antal i dina CRM-rapporter (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

Granularitetsnivån kan variera beroende på kanal. Det rekommenderade tillvägagångssättet skulle vara att fråga dig själv,&quot;vad om&quot;kanal X&quot; vill jag förstå mer i detalj?&quot; Betalande sökhanterare kan också vara intresserade av ytterligare dimensioner, som:

* Namn på annonskampanj
* Annonsinnehåll
* Annonsgrupp

Events-chefer kan dock vara mer intresserade av vilka specifika händelser eller vilka typer av händelser som påverkade de flesta ledarna till skapandet:

* Namn på annonskampanj/Salesforce-kampanj = specifik händelse
* Medium = Campaign &#39;Type&#39;

**PÅMINNELSE**: Ytterligare filter kan behöva läggas till i de rapportvarianter som beskrivs ovan eller nedan. Dessa filter skulle vara specifika för er organisation och skulle vara något som era marknadsföringsteam eller säljteam skulle kunna rekommendera. Det är inte ovanligt att en organisation kör samma filter i alla rapporter för att säkerställa att rapporten är så ren och korrekt som möjligt. Vanliga exempel kan vara:

* Filtrera ut interna poster från tester, vanligtvis via e-postadress
* Filtrering baserad på vissa posttyper som kan vara specifika för din affärsenhet

**1.3 | Nya leads efter innehåll (endast CRM-rapporter)**

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vad <i>innehåll</i> Påverkar Leads till skapande?</td> 
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
   <td>Landningssida<br> 
   Formulär-URL</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>First Touch, Lead Creation, <strong>U-formad</strong><br></td> 
  </tr>
 </tbody>
</table>

**PÅMINNELSE**: De två primära fälten för rapportering av digitalt innehåll/digitala resurser är Landing Page och Form URL. Dessa två värden kan vara desamma om leadet konverterar (skickar in ett formulär) på samma sida som de&quot;landade&quot; (landningssida), _dock_, ibland är dessa värden olika. Lead-instansen kan till exempel klicka på en länk på Facebook som tar dem till en sida på webbplatsen (det är värdet för Landing Page). Lead kan sedan navigera bort från den sidan, fortsätta sin session på webbplatsen och skicka ett formulär på en annan sida (formulär-URL). Detta sammanfattas i en enda kontaktyta som representerar var leadet kommer från (marknadsföringskanal), vilket innehåll som förde dem till webbplatsen (landningssida) och vilket innehåll som laddades ned (formulär-URL). &#39;Formulär-URL&#39; är också det go-to-fält som används för att rapportera om andra formulär som inte är kopplade till hämtningsbart innehåll som &#39;Kontakta oss&#39; eller &#39;Demo-begäran&#39;.

>[!TIP]
>
>Få insikter i specifikt &#39;innehåll&#39; med ytterligare filter
>
>* Filtrera efter: &#39;Landningssida&#39; INNEHÅLLER (till exempel):
   >   * /blog
   >   * /ebook
   >   * /webinar
>
>* ELLER: &#39;Formulär-URL&#39; INNEHÅLLER (till exempel)
   >   * /contact
   >   * /demo


Innehållsbaserade rapporter tillför mycket värde vid rapportering på valfri del av tratten, men de används oftast högst upp i tratten för att ge ytterligare insikter i ett inledande engagemang för leads. Med tanke på att&quot;organisk sökning&quot; ofta är den starkaste kanalen när det gäller att skapa ett första engagemang (FT) finns det inte så mycket data på kampanjnivå.

Innehållsbaserade rapporter är bra för att få insikt i vad som genererar leads mer specifikt inom den högre nivån av marknadsföringskanalen, i det här fallet&quot;Organic Search&quot;.

**1.4 | Totalt lead-engagemang i ett givet datumintervall**

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler har haft mest <i>totalt ledarengagemang</i> tidigare (vecka/månad/kvartal)?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br> 
   Mått: Leads ([!DNL Marketo Measure] Upptäck)</td> 
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
   <td>*Den här rapporten handlar mindre om att mäta var leads kommer från med en attribueringsmodell, men mer om <i>totalt antal kontaktytor (engagemang)</i>, även efter leadskapandekontakten. Det totala antalet kontaktpunkter i registret skulle återspegla vilka kanaler som har sett störst engagemang i leads.</td> 
  </tr>
 </tbody>
</table>

**PÅMINNELSE**: Att basera era rapporter på &#39;Touchpoint Date&#39; är det mest reflekterande sättet att förstå marknadsföringens resultat under ett visst datumintervall. &#39;Slutpunktsdatum&#39; strukturerar rapporten på ett sätt där attribueringen inte bara är relaterad till kanalen, kampanjen eller innehållet, utan även visar när kontaktytan inträffade. Detta är det mest effektiva sättet att förstå vilket marknadsföringsengagemang som inträffade vid en viss tidpunkt och även det rekommenderade sättet att mäta marknadsföringens effekt i jämförelse med marknadsföringsutgifter som investerats under samma tid. Det rekommenderas när man gör marknadsföringsinvesteringar eller gör en analys av avkastningen (se 5.1).

**2. MARKNADSFÖRING AV KVALIFICERADE LEDARE MED TOUCHPOINS FÖR KÖPARE**

En av de vanligaste rapporterna handlar inte bara om nya leads eller engagemang på leadnivå, utan snarare om&quot;marknadsföringskvalificerade leads&quot; (MQL). Det finns ett par olika strategier när det gäller att rapportera om minimikvalitetskrav beroende på vad [!DNL Marketo Measure] funktioner som du har tillgång till.

**2.1 | Marknadsföringskvalificerade leads efter kanal (multi-touch)**

Detta tillvägagångssätt för att mäta effekten av marknadsföringen på att påverka MQL:er är i princip en fortsättning på rapporten&quot;New Leads by Marketing Channel&quot; (1.1), men med de ytterligare kriterier som de leads som mäts är mer specifikt MQL:er. Den amerikanska attribueringsmodellen rekommenderas fortfarande här för att identifiera vilka marknadsföringskanaler och vilket innehåll som genererar leads som sedan _sannolik_ för att bli MQL:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler är bäst på att generera nya leads som blir <i>MQLs</i>?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br> 
   Mått: Leads ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>MQL = true*<br>
   *<i>MQL:er kan definieras olika för olika organisationer. Se till att [!DNL Marketo Measure] rapporten filtreras efter MQL:er med samma fält som andra MQL-baserade rapporter. Ett segmentfilter måste skapas på samma sätt för att rapportera MQL i [!DNL Marketo Measure] Upptäck.</i></td> 
  </tr>
  <tr>
   <td>Datumfält / Datumtyp</td> 
   <td>MQL-datum (eller motsvarande) / Skapad ([!DNL Marketo Measure] Upptäck)<br> <i>Lead skapad den kan också användas i CRM-rapporter om MQL Date inte är ett alternativ i CRM. Det är viktigt att tänka på vilket datumfält du använder för att definiera den kodade datauppsättningen.</i></td> 
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
   <td>First Touch, Lead Creation, <strong>U-formad</strong><br> 
   SUM-fälten Antal i CRM-rapporterna (Count - First Touch, Count - Lead Creation, Count - U-Shaped)</td> 
  </tr>
 </tbody>
</table>

**2.2 | Marknadsföringskvalificerade leads per kanal (endast en pekning, CRM)**

Detta tillvägagångssätt för att mäta effekten av marknadsföringen på att påverka minimikvaliteten är mer inriktat på att identifiera vilka _enkel kontaktyta_ var den sista kontakten innan leadet nådde MQL.

>[!NOTE]
>
>För att kunna köra den här rapporten krävs ett &#39;Lead Status&#39;-värde på &#39;MQL&#39; för att definiera MQL-scenen för spårningsändamål (trattfas). Om MQL:er inte spåras via fältet Lead Status krävs funktionen Custom Attribution Model with Custom Stages för att skapa en anpassad MQL-scen i [!DNL Marketo Measure] Kontoinställningar.

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vilka marknadsföringskanaler är bäst på att få leads att nå MQL-status?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Leads och Buyer Touchpoints (CRM)<br>
   <i>den här rapporten är bara möjlig inom CRM-rapportering. Det går inte att filtrera på vissa värden för 'Touchpoint Position' i [!DNL Marketo Measure] Upptäck</i></td> 
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
   <td><i>Eftersom den här rapporten filtreras på en enda kontaktyta är attribueringsmodellerna på leadnivå inte så relevanta. Precis som i"Ledningsengagemangsrapporten" (1.4) skulle antalet kontaktpunktsposter utnyttjas här för att förstå vilka kanaler som är störst (varje lead skulle bara ha en enda MQL-kontaktyta).</i></td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>Utforska andra grupperingar eller dimensioner för att få ytterligare insikter i MQL:er. Som nämndes i de andra rapporterna&quot;Leads with Buyer Touchpoints&quot; erbjuder Buyer Touchpoint mycket mer detaljrikedom än bara Marketing Channel. En&quot;innehållsbaserad&quot; rapport kan också kombineras med någon av MQL-rapporterna ovan för att bättre förstå vilket innehåll som bäst påverkar MQL:er.

**3. [!DNL MARKETO MEASURE] PERSONER MED INKÖPARE TOUCHPOINTS**

Det finns en tredje anpassad [!DNL Marketo Measure] objekt i Salesforce som kan vara mycket användbara när du rapporterar personrelaterade mått: **den [!DNL Marketo Measure] Person (BP)**. BP löser det gamla problemet med att representera information om både leads och kontakter i samma rapport. Den förenar alla BT:er som är relaterade till en&quot;person&quot; (en [!DNL Marketo Measure] Personens ID är deras e-postadress). Vare sig de finns som lead eller kontakt fungerar BP som ett bryggobjekt, vilket gör det lättare att rapportera mellan lead och kontakt, och är mycket användbart när det gäller att skapa mer avancerade rapporter om människor.

The [!DNL Marketo Measure] Personen relaterar endast till ett av kontaktobjekten, Buyer Touchpoint (BT). Det innebär att det inte kan utnyttjas för att mäta ett säljprojekt eller en intäktsrelaterad investering. A[!DNL Marketo Measure] Formtypen för Person- och Buyer Touchpoints är mycket bra för förståelsen _totalt engagemang_ eftersom det omfattar alla BT:er, vare sig det gäller en lead eller kontakten mer specifikt. Om du till exempel har en Salesforce-kampanj som används för att spåra en händelse, kan du ha kampanjmedlemmar i CRM-kampanjen som antingen finns som Leads ELLER Kontakter. [!DNL Marketo Measure] kommer att skapa kontaktytor för kampanjmedlemmarna oavsett, men utan [!DNL Marketo Measure] Personen, standard Salesforce-rapportering skulle kräva två separata rapporter för att förstå hur många _total_ kontaktytor från händelsen: en som är&quot;Leads with Buyer Touchpoints&quot; och en som är&quot;Contacts with Buyer Touchpoints&quot;. Några andra [!DNL Marketo Measure] Personbaserade användningsexempel för rapportering anges nedan:

**3.1 [!DNL Marketo Measure] Personer som har laddat ned e-böcker eller rapporter (totala nedladdningar)**

Den här rapporten skulle vara densamma som en Content-baserad rapport på Lead-nivå. I stället för att mäta antalet tillhörande leads för varje innehållspunkt, använder du en [!DNL Marketo Measure] Personernas rapport kommer att vara till hjälp när det gäller att förstå totalbeloppet _antal nedladdningar_ om tillgången är insamlad (det totala antalet kontaktytor motsvarar det totala antalet nedladdningar/inskickade formulär).

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
   <td>Kontaktpunktsdatum <i>(när hämtades resursen)</i></td> 
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
   <td>Den här rapporten handlar mindre om att mäta var leads eller kontakter kommer från med en attribueringsmodell, men mer om <i>totalt antal kontaktytor (engagemang)</i>, även efter leadskapandekontakten. Med den här rapporten vill vi förstå <i>totalt engagemang</i>. Det totala antalet poster för kontaktytor skulle återspegla vilka resurser som har laddats ned mest.</td> 
  </tr>
 </tbody>
</table>

>[!TIP]
>
>För alla Leads med [!DNL Marketo Measure] Typ av personrapport, börja med att anpassa den färdigbyggda rapporten med titeln **[!DNL Marketo Measure]101 | Leads/kontakter efter kanal**&#39;. Den här rapporten finns tillgänglig när som helst och är en utmärkt [!DNL Marketo Measure] Personbaserad sandlåda. Den är fördefinierad och kan snabbt anpassas för mer specifika rapporteringsbehov.

>[!TIP]
>
>Du kan använda den här rapporten för att få insikt i det totala engagemanget för alla marknadsföringsdimensioner från Buyer Touchpoint-objektet, inte bara för innehållsnedladdningar enligt exemplet. Rapporten kan istället grupperas eller filtreras efter dimensioner som&quot;Marknadskanal&quot; eller&quot;Namn på annonskampanj&quot; för att på bästa sätt förstå det totala engagemanget från både leads och kontakter i databasen. Ändra bara filtren eller grupperingarna i rapporten till noll i andra dimensioner som representeras av andra fält från kontaktobjektet.

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
   <td>Kontaktpunktsdatum <i>(när registreringsblanketten har skickats)</i></td> 
  </tr>
  <tr>
   <td>Datumintervall</td> 
   <td><i>välj önskat datumintervall</i></td> 
  </tr>
  <tr>
   <td>Grupp/Dimension</td> 
   <td>Formulär-URL<br>
   Marknadsföringskanal</td> 
  </tr>
  <tr>
   <td>Optimala modeller</td> 
   <td>Den här rapporten handlar mindre om att mäta var leads eller kontakter kommer från med en attribueringsmodell, men mer om <i>totalt antal kontaktytor (antal registreringar)</i>, även efter leadskapandekontakten. Med den här rapporten vill vi få insikt i vad som driver evenemangsregistreringar. Det totala antalet kontaktpunkter per"marknadsföringskanal" återspeglar vilka kanaler som drev flest registreringar.</td> 
  </tr>
 </tbody>
</table>

Huvudsaken från den här rapporten är att Buyer Touchpoint-data också kommer att tillhandahålla data för marknadsföringskanaler. Även om ni redan har insikter om antalet personer som har registrerat sig för era evenemang, kommer den här rapporten även att ge insikter om vilka digitala marknadsföringskanaler, källor och/eller kampanjer som tar personer till er webbplats för att sedan registrera sig för evenemanget.

>[!TIP]
>
>Samma tillvägagångssätt kan användas när man vill få insikt i webbinarier eller kanske hämta webbinarier på begäran (om de är en speciell tillgång). Den enda skillnaden är filtervärdet i formulär-URL:en om formulären finns på webbplatsens unika sidor. Målet är dock detsamma. Det besvarar frågorna:&quot;Vilka av mina marknadsföringskanaler är det som driver de flesta nedladdningar av webbinarier som registreras/hämtas on demand.

**3.3 [!DNL Marketo Measure] Personer med Buyer Touchpoints (Touchpoint Validation)**

Med tanke på [!DNL Marketo Measure] Personen tillåter oss att rapportera om alla kontaktytor i en enda rapport, det är den idealiska rapporttypen för validering av dina data. Vi vill försäkra oss om att vi inte missar några kontaktytor som kan avslöja var det till exempel finns ett problem i konfigurationen av dina marknadsföringskanaler (se supportartiklarna nedan för mer information om hur du konfigurerar dina marknadsföringskanaler).

* [Anpassad kanalinställning online](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
* [Anpassad kanalinställning offline](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)

I grund och botten återspeglar data om kontaktytan vad som har spårats av [!DNL Marketo Measure] och kan granskas för att säkerställa att konfigurationen matchar indata baserat på exempelvis: UTM-parametervärden, referenssidor eller kampanjtyper. Om kontaktpunktsdata inte matchar din konfiguration måste något som troligen behöver justeras. Utöver konfigurationen av marknadsföringskanalen kan ni titta på data från kontaktytor för att avgöra vilka kontaktytor som behöver vara [undertryckt](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) eller [segmenterad](/help/advanced-marketo-measure-features/segmentation/custom-segmentation.md). Vi rekommenderar att du granskar dina kontaktpunktsdata i en[!DNL Marketo Measure] Rapport från People and Buyer Touchpoints i slutet av varje månad eller kvartal om det är möjligt. Detta säkerställer att attribueringen blir så korrekt som möjligt. The[!DNL Marketo Measure] 101 | Leads/kontakter per kanal - rapport som är tillgänglig direkt är en bra startpunkt. Inkludera följande fält om de inte redan finns med för att granska några av de viktigaste konfigurationsbitarna:

* **Marknadsföringskanal** - Path = Marketing Channel.Subchannel (värden anges i [!DNL Marketo Measure])
* **Kontaktpunktskälla** = utm_source
* **Medel** = utm_medium (kontaktytor online) ELLER CRM-kampanjtyp (kontaktytor offline)
* **Referenssida** (använder konfigurationen &#39;Onlinekanaler&#39;)
* **Landningssida - Raw** (som används i konfigurationen för Onlinekanaler) även som en vanlig inmatning för inaktivering av kontaktytor på fliken &#39;Slutpunktsinställningar&#39; i inställningarna)
* **Formulär-URL** (en vanlig inmatning för inaktivering av kontaktpunkter på fliken &#39;Touchpoint Settings&#39; i inställningarna)

**TOUCHPOINT FÖR KÖPARATTRIBUTION (BAT)**

Kontaktpunkterna för Buyer Attribution (BAT) representerar de relevanta kontaktytorna för alla kontakter som är kopplade till säljprojektet (antingen via roller för säljprojektskontakt eller via ett delat konto-ID, beroende på dina inställningar). Till skillnad från BT (som i huvudsak är kopplade till människor) kan BAT:er kopplas till intäkter. Därför kommer ni att använda BAT för att besvara frågor som rör möjligheter, främst öppna _Affärsmöjligheter/försäljningsförlopp_ och stängd _Affärsmöjligheter/erbjudanden/intäkter_. En BAT skapas via en kontakts BT-poster så snart ett säljprojekt skapas under samma konto som kontakten (BT konverteras inte till BAT. BT-data refereras bara till för att skapa en ytterligare post - BAT som sedan relaterar till säljprojektet).

Med Buyer Attribution Touchpoint kan vi mäta marknadsföringens påverkan djupare i tratten. _Djupet på tratten som du vill mäta kan representeras av de olika multitouch-attribueringsmodellerna_.

Med tanke på att bästa tillgängliga teknik har ett primärt samband med säljprojektet används de för att svara på frågor som:

* Vilken av mina marknadsföringssatsningar har påverkat de största möjligheterna?
* Hur mycket nya intäkter kan jag tillföra varje marknadsföringskanal?
* Vilken av mina kampanjer fick störst avkastning förra kvartalet?

The [attribueringsmodeller](/help/introduction-to-marketo-measure/overview-resources/marketo-measure-attribution-models.md) De bästa insikterna om möjligheterna är följande:

**W-Shaped** -_Pipeline-modell_&#39;. Tre milstolpekontaktytor ingår i W-Shaped-modellen. I den här modellen tillskrivs kontaktytorna FT, LC och OC 30 % av attribueringskrediten. Återstående 10 % fördelas jämnt på alla mellanliggande kontaktytor som inträffar mellan de tre milstolppunkterna.

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

**Fullständig sökväg** -_Stängd Won-modell_&#39;. Den här modellen innehåller fyra milstolpar: FT, LC, OC och Closed. Var och en ges 22,5 % av säljprojektskrediten och de återstående 10 % fördelas jämnt mellan de mellanliggande kontakterna.

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

**Egen** - [!DNL Marketo Measure] erbjuder också en modell för anpassad attribuering som gör att användare kan välja vilka kontaktytor eller anpassade stadier som ska ingå i modellen. Dessutom kan användarna styra den procentandel av attribueringskrediten som tilldelats dessa kontaktytor och faser. Beroende på hur din anpassade modell är konfigurerad kan den användas på bästa sätt för att mäta antingen säljprojekt och pipeline ELLER, erbjudanden och slutna vinjetter. Tänk på detta när du använder det i din rapportering.

>[!NOTE]
>
>Custom Attribution Model är en extra funktion som inte är tillgänglig för alla kunder. Kontakta kontogruppen på Adobe (din kontohanterare) om du vill veta mer om hur du lägger till den här funktionen i ditt konto.

Vanligtvis måste marknadsförarna veta, &quot;varifrån kommer mina affärsmöjligheter?&quot;. På samma sätt som vid rapportering på leads besvarades den här frågan historiskt med ett enda endimensionellt värde (till exempel Primär kampanjkälla). Vi vet dock att mycket mer går in på att utveckla ett säljprojekt än en enda kontaktyta från en enda kontakt. Det finns vanligtvis flera kontaktytor från olika kanaler och från flera intressenter som påverkar möjligheterna att skapa. Med [!DNL Marketo Measure]kan vi identifiera alla kontaktytor från ett konto för att få en bättre förståelse för var ett säljprojekt kommer ifrån. Utöver detta kan vi dock fortsätta att identifiera alla kontaktytor som har inträffat efter att affärsmöjligheten har skapats och fram till den punkt där affärsmöjligheten har stängts. Detta gör att vi inte bara kan använda en strategi där flera kontaktytor tas för att förstå var ett säljprojekt kommer ifrån, utan även vad som påverkade det att avsluta och slutligen representera slutna vinstintäkter. Detta ger insikt i olika frågor, till exempel &quot;vad påverkar marknadsföringen på att påverka avtal att sluta?&quot;, &quot;vilken marknadsföring driver stängda Vinner Revenue?&quot; och slutligen, &quot;vilket av mina marknadsföringssatsningar får störst avkastning?&quot;

## REKOMMENDERADE RAPPORTER MED TOUCHPOINT FÖR KÖPSATTRIBUTION (BAT) {#recommended-reports-using-the-buyer-attribution-touchpoint}

**4.1 | Nya affärsmöjligheter per marknadsföringskanal**

Att sammanfatta era säljprojekts Buyer Attribution Touchpoint-data med fältet Marketing Channel är den vy på högsta nivån som representerar vilka kanaler/taktik som påverkar nya möjligheter till skapande. Genom att strukturera den här rapporten runt ett&quot;Datumtyp&quot; =&quot;Skapad affärsmöjlighet&quot; säkerställer vi att vi också sammanfattar rapporten baserat på när affärsmöjligheten skapades i CRM. Kontaktpunkterna kan ha kommit från en tid tidigare, men de kommer fortfarande att relatera till de affärsmöjligheter som har skapats inom det definierade datumintervallet och därmed få attribueringskrediter eftersom de anses påverka affärsmöjligheten.

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vad <i>marknadsföringskanaler</i> Påverkar det möjligheter att skapa?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer Attribution med Opportunity (CRM)<br> 
   Mått: Möjligheter ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Affärsmöjlighet* <i>(valfritt beroende på vilka specifika affärsmöjligheter du vill begränsa till rapporten. Du kanske bara vill rapportera om BAT som fortfarande bara är kopplade till"Öppna"-möjligheter)</i></li>
   <li>Typ av affärsmöjlighet (det är vanligt att filtrera in vissa affärsmöjligheter, dvs. Ny verksamhet i stället för <i>alla</i> Möjligheter)</li><br>
   *Ett segmentfilter för säljprojektstyp ska användas i [!DNL Marketo Measure] Upptäck</td> 
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
>För alla rapporttyper för &#39;Buyer Attribution Touchpoints with Opportunity&#39; börjar du med att anpassa den fördefinierade rapporten &#39;[!DNL Marketo Measure] 101 | Affärsmöjligheter efter kanal&#39;. Den här rapporten är tillgänglig direkt och är en utmärkt sandlåda som är fördefinierad enligt beskrivningen i tabellen ovan och kan snabbt anpassas för mer specifika rapporteringsbehov (rapporten använder en modell med fullständig sökväg som är färdig att användas så se till att rapporten anpassas så att den inkluderar alla andra attribueringsmodeller, i det här fallet W-Shaped-modellen).

>[!TIP]
>
>Den rapport som beskrivs ovan skulle också användas när man vill förstå hur mycket valuta som också bör tillskrivas. Vid rapportering på affärsmöjlighetsnivå med hjälp av bästa tillgängliga teknik finns det två viktiga mätvärden som kan sammanfattas: valuta (beloppet för affärsmöjligheten) och själva säljprojektsposten. I exemplet ovan mäter vi mer specifikt öppna möjligheter och nya intäkter från pipeline.

>[!TIP]
>
>Få ännu mer detaljerad information genom att sammanfatta rapporten med andra tillgängliga fält från Buyer Attribution Touchpoint-objektet. Detta görs på samma sätt som på nivån Lead med Buyer Touchpoints (1.2). Det gör du genom att lägga till ytterligare grupperingar (CRM) eller dimensioner (Discover). Beroende på vilken kanal (som kanske representerar din roll) kan det finnas ytterligare information utöver den kampanjnivå där du vill få mer information. Vi går in på Betald sökning nedan:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>som <i>nyckelord</i> från mina betalsökannonser genererar de mest rörliga intäkterna?
</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer Attribution med Opportunity (CRM)<br> 
   Mått: Möjligheter ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Marknadsföringskanal = betald sökning</li>
   <li>Affärsmöjlighet* <i>(valfritt beroende på vilka specifika affärsmöjligheter du vill begränsa till rapporten. Det här exemplet är baserat på Pipeline Revenue, som definieras i [!DNL Marketo Measure] av"Open" Opportunity som representerar potentiella intäkter/öppen pipeline)</i></li>
   <li>Typ av affärsmöjlighet (det är vanligt att filtrera in vissa affärsmöjligheter, dvs. Ny verksamhet i stället för <i>alla</i> Möjligheter)</li><br>
   *Ett segmentfilter för säljprojektstyp ska användas i [!DNL Marketo Measure] Upptäck</td> 
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

Den här rapporten skulle i princip vara densamma som det första exemplet med Buyer Attribution Touchpoint (4.1), förutom att måttet nu har ändrats från öppna säljprojekt till stängda vunna erbjudanden. Mätvärdet ska alltid vara det som anger vilken attribueringsmodell som ska användas. Med tanke på att vi nu tittar på stängda vunna avtal och deras relaterade BAT bör vi använda en modell som representerar hela köparens resa (avtal). Detta garanterar att alla marknadsföringstester under kundresan får attribueringskrediter:

<table> 
 <tbody>
  <tr>
   <td>Fråga</td> 
   <td>Vad <i>marknadsföringskanaler</i> Påverkar det avtal som ska stängas?</td> 
  </tr>
  <tr>
   <td>Typ av rapportering</td> 
   <td>Kontaktpunkter för Buyer Attribution med Opportunity (CRM)<br> 
   Mått: Erbjudanden ([!DNL Marketo Measure] Upptäck)</td> 
  </tr>
  <tr>
   <td>Filter</td> 
   <td>
   <li>Affärsmöjlighet (<i>Endast stängda vunna affärsmöjligheter ska anges i rapporten</i>) ELLER</li>
   <li>Won-affärsmöjlighet = Sant</li>
   <li>Typ av affärsmöjlighet (det är vanligt att filtrera in vissa affärsmöjligheter, dvs. "New Business" i motsats till alla affärsmöjligheter)<br>
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

**PÅMINNELSE**: Det är viktigt att komma ihåg att filtrera efter de specifika möjligheter som du vill inkludera i BAT-baserad rapportering, särskilt när det gäller Öppna möjligheter och Pipeline-intäkter jämfört med &#39;Erbjudanden och slutna vinstintäkter&#39;. Detta görs vanligtvis via ett &#39;säljprojektsstadiefilter&#39; (filtret &#39;säljprojekt&#39; = sant/falskt kan också vara mycket användbart här).

**5. avkastning ([!DNL Marketo Measure] Upptäck endast)**

The [!DNL Marketo Measure] Upptäck instrumentpaneler som ger en överblick över era marknadsföringsprestanda med [!DNL Marketo Measure] attribueringsdata. Dessa aggregerade kontrollpaneler tillhandahåller viktiga marknadsföringsutlägg och ROI-data som inte är tillgängliga i CRM-rapporterna. I den här fördefinierade miljön kan ni se hur marknadsföringen fungerar i linje med era ROI-data, så att ni kan fatta konkreta beslut om marknadsföringen.

>[!TIP]
>
>När du har en fråga som rör avkastning, utgifter eller kostnader, [!DNL Marketo Measure] Upptäck är det bästa stället att rapportera!

The [!DNL Marketo Measure] Discover-panelerna består av Buyer Touchpoint- och Buyer Attribution Touchpoints-data samt viktiga CRM-data. Den största skillnaden mellan CRM-rapportering och rapportering i [!DNL Marketo Measure] Discover visar att kontaktpunktsdata i Discover presenteras mer i&quot;aggregerad&quot; form och summeras efter dimension (marknadsföringskanal, kampanj osv.) till skillnad från individuella kontaktytsposter som sedan kan sammanfattas. [!DNL Marketo Measure] Upptäck används för att på en hög nivå förstå vilka av dina insatser som har störst effekt på leads, motsättningar, erbjudanden och hur mycket intäkter som ska tillskrivas dem. När vi har beräknat de tillskrivna intäkterna via de olika attribueringsmodellerna (Full Path rekommenderas för att tilldela stängda egna intäkter/bokningar) kan vi sedan mäta dem mot hur mycket som spenderats i samma dimension (Marketing Channel, Subchannel eller Campaign). Då får vi **avkastning**.

>[!TIP]
>
>En av de viktigaste sakerna att komma ihåg när du rapporterar i Discover är vilken datatyp du använder för att filtrera. Datumtyp anger vilken datauppsättning som [!DNL Marketo Measure] används i de olika rutorna.

* **Kontaktpunktsdatum**: Visar relaterade data som hade &#39;Slutpunktsdatum&#39; i den angivna tidsramen
* **Skapad den**: Visar relaterade data som hade ett Skapat den i den angivna tidsramen
* **Stängt den**: Visar relaterade data som hade ett stängningsdatum i den angivna tidsramen

Vid rapportering av avkastning på investeringar i [!DNL Marketo Measure] Upptäck att du bör använda datumtypen = &quot;Slutpunktsdatum&quot;. För att fastställa avkastningen för varje investerad dollar måste vi se till att intäkterna återförs till det datum då investeringen gjordes. &#39;Datumtyp&#39; = &quot;Slutpunktsdatum&quot; säkerställer att rapporterna är strukturerade på det här sättet i motsats till när affärsmöjligheten skapades (Skapa datum) eller stängdes (Stängt datum). Ta en närmare titt:

De filter som anges nedan är avgörande för en rapport med fokuserad avkastning i [!DNL Marketo Measure] (troligen kommer du att ställa in dessa filter i panelerna Översikt, CMO eller ROI):

**5.1 | Avkastning på anslagstavlan**

![](assets/bizible-reporting-guide-4.png)

Datumintervallet anger inte bara vilken kohort av kontaktytor (efter slutpunktsdatum) som tar emot attribuering, utan också det intervall som representerar&quot;utgiftsrutan&quot; eller kolumnerna.
[!DNL Marketo Measure] tittar bara på datumintervallet för att avgöra hur mycket som spenderas antingen totalt eller på nivåerna Marknadsföringskanal, Delkanal eller Campaign Se nedan:

![](assets/bizible-reporting-guide-5.png)

Skärmbilden ovan visar marknadsföringsbudgeten för de senaste tre månaderna. I det här exemplet spenderades 12 970 dollar över alla kanaler. Detta nummer består av marknadsföringsbudgeten [!DNL Marketo Measure] har integrerats med något av dina anslutna annonskonton (Google AdWords, Bing Ads, Facebook Ads, LinkedIn, DoubleClick) och eventuella ytterligare marknadsföringsutgifter som har överförts inom ditt konto eller hämtats automatiskt från en Campaign-post i CRM. Exemplet visar också hur mycket stängd vunnen intäkt som också kan tillskrivas kontaktpunkter som inträffade under samma datumintervall (gröna rutor). Så här beräknas avkastningen på investeringen: Intäkter från kontaktytor som härrör från investeringar inom samma datumintervall:

![](assets/bizible-reporting-guide-6.png)

**PÅMINNELSE**: [!DNL Marketo Measure] definierar &#39;Intäkter&#39; som stängda egna intäkter eller bokningar och definierar &#39;Pipeline Revenue&#39; som _öppna/potentiella intäkter från öppna affärsmöjligheter_.

En annan viktig skillnad från ROI-rapporten ovan är&quot;Pipeline Revenue&quot; som finns i den röda rutan. Det innebär att från de 12 970 USD som investerats under de senaste tre hela månaderna tilldelar vi för närvarande 705 199 dollar i sluten vinst, men vi tilldelar även 6 905 532 dollar i öppna, potentiella intäkter (&quot;Pipeline Revenue&quot;) till kontaktytor som skapats från samma investering! Det vi förväntar oss är en del av stängningen av Pipeline Revenue över tiden, som matar in talet Revenue, och därmed skulle avkastningen öka med tiden. &#39;Utgiftsvärdet&#39; är fast eftersom vi inte kan lägga mer tid på de senaste tre hela månaderna. Det är viktigt att du använder datumtypen &quot;Touchpoint Date&quot; i alla rapporter om avkastning på investerat kapital: Den definierar mängden (**I** har investerats och säkerställer (**R**)Andel tillskrivs samma kontaktytor som härrör från investeringen (för varje spenderad dollar, hur mycket gjordes?).

>[!TIP]
>
>Filtrera in på marknadsföringskanaler, delkanaler och/eller kampanjer där ni vet att marknadsföringsbudgeten är fullständig och korrekt. Exemplet ovan gäller alla marknadsföringskanaler, men om vissa kanaler inte har de relaterade marknadsföringsutgiftsdata överförda kan avkastningen på investeringen bli felaktig. Se exemplet nedan, den här gången i&quot;ROI&quot;-panelen som fokuserar på kampanjer i marknadsföringskanalen i&quot;Betald sökning&quot;, en kanal med mycket detaljerade marknadsföringsutlägg via integreringarna.

![](assets/bizible-reporting-guide-7.png)
