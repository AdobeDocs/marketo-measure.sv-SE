---
description: '[!DNL Marketo Measure] Rapportmall - tabell - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Rapportmall - tabell'
exl-id: 18963be9-5c6e-4454-8244-b50460e2bed5
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '2445'
ht-degree: 0%

---

# [!DNL Marketo Measure] Rapportmall - tabell {#marketo-measure-report-template-tableau}

## Komma igång {#getting-started}

Du kan komma åt rapportmallen [!DNL Tableau] [här](https://github.com/adobe/Marketo-Measure-BI-Templates){target="_blank"}.

Öppna arbetsboksfilen för rapportmallen [!DNL Adobe Marketo Measure].

Du måste uppdatera befintliga anslutningsdata till din specifika anslutningsinformation för Snowflake. Klicka på knappen [!UICONTROL Edit Connection] och följ stegen som beskrivs i avsnittet [[!UICONTROL Data Connection]](#data-connection) i den här dokumentationen.

![Du måste uppdatera befintliga anslutningsdata till din specifika Snowflake](assets/marketo-tableau-7.png)

## Dataanslutning {#data-connection}

Du måste skapa en dataanslutning till din Snowflake-instans. För detta behöver du servernamnet tillsammans med ditt användarnamn och lösenord. Information om var du kan hitta den här informationen och återställa ditt lösenord, om det behövs, finns [här](/help/data-warehouse-access-reader-account.md){target="_blank"}.

![Du måste konfigurera en dataanslutning till din Snowflake-instans.](assets/marketo-tableau-5.png)

Du måste också ange ett inledande SQL-kommando. Detta stöder användning av anpassade frågor i den här datamodellen. Kommandot som ska anges är &quot;Använd schema `<your schema name>`&quot;. Du kan hitta schemanamnet på sidan [!UICONTROL data warehouse connections], se den dokumentation som det hänvisas till ovan.

![Du måste också ange ett inledande SQL-kommando. Detta stöder ](assets/marketo-tableau-6.png)

### Anpassade SQL-frågor {#custom-sql-queries}

Eftersom [!DNL Tableau] tillämpar datakällfilter på den övergripande frågan och inte på den enskilda tabell som filtret är inställt på, har vi valt att använda anpassad SQL för varje tabell i modellen. Detta gör att modellen kan filtrera bort borttagna och duplicerade rader på tabellnivå. Om det till exempel används som ett datakällfilter, session._deleted_date är null läggs till i where-satsen i frågan, vilket resulterar i följande fråga.

**Filter har lagts till i Data Source**

```sql
--A deleted session removes this row completely and the touchpoint data is lost. Select *
   From Touchpoint    tp
      join Session sn
      on tp.session_id = sn.session_id
 Where tp._deleted_date is null
    and sn._deleted_date is null
```

Detta är dock felaktigt eftersom om en session togs bort, men motsvarande kontaktyta inte tas bort, tas data om kontaktytan bort från datauppsättningen. Vi vill att det ska finnas kontaktpunktsdata i datauppsättningen eftersom kontaktytan inte har tagits bort. Genom att lägga till anpassad SQL säkerställer du att filtervillkoren tillämpas på tabellnivå, vilket resulterar i följande fråga.

**Filter som används via anpassad SQL**

```sql
--A deleted session only removes the session related data, and the touchpoint data is preserved. Select *
   From Touchpoint       tp
      join Session sn
      on tp.session_id          = sn.session_id
      and sn._deleted_date      is null
  Where tp._deleted_date is null
```

## Dataomvandlingar {#data-transformations}

Några transformationer har tillämpats på data i [!DNL Tableau] från det ursprungliga läget i Snowflake. De flesta av dessa omformningar används i anpassade SQL-frågor som genererar tabellerna i modellen [!DNL Tableau]. Om du vill visa den anpassade SQL-kod som används för att generera en tabell högerklickar du på tabellnamnet och väljer Redigera anpassad SQL-fråga. Några av de specifika omformningarna beskrivs nedan.

![Några omformningar har tillämpats på data i Tablet PC](assets/marketo-tableau-1.png)

![Några omformningar har tillämpats på data i Tablet PC](assets/marketo-tableau-2.png)

### Borttagna kolumner {#removed-columns}

För att förenkla datamodellen och ta bort överflödiga och onödiga data har vi minskat antalet kolumner som importerats till Tableau från den ursprungliga Snowflake-tabellen. De borttagna kolumnerna innehåller onödiga sekundärnycklar, denormaliserade flerdimensionella data som bättre används via relationer till andra tabeller i modellen, granskningskolumner och fält som används för intern [!DNL Marketo Measure]-bearbetning. Du kan lägga till eller ta bort kolumner efter behov genom att redigera listan över importerade kolumner i avsnittet Välj i den anpassade SQL-satsen.

>[!NOTE]
>
>De flesta tabeller i datalagret innehåller denormaliserade dimensionella data. Vi har arbetat med att normalisera och rensa modellen i [!DNL Tableau] så mycket som möjligt för att förbättra prestanda och datakvalitet. Var försiktig när du lägger till ytterligare normaliserade fält i faktatabeller. Detta kan bryta dimensionell filtrering mellan tabeller och kan också leda till felaktiga rapporter.

### Kolumner med ändrat namn {#renamed-columns}

Tabellerna och kolumnerna har bytt namn för att göra dem mer användarvänliga och för att standardisera namnkonventioner. Om du vill visa kolumnnamnsändringarna refererar du till de anpassade SQL-satser som skapar tabellerna.

### Rader tillagda {#rows-added}

För att lägga till funktioner för valutakonvertering i beräkningarna i modellen har vi lagt till en företagskonverteringssats och en kolumn för målkonverteringsgrad i tabellerna för både säljprojekt och kostnad. Värdet i de här kolumnerna läggs till på radnivå och utvärderas genom att koppla till konverteringstabellen för både datum- och valutakod-ID. Eftersom det inte går att dela faktatabeller med mer än en dimensionstabell i Tableau, lades konverteringssatserna till direkt i de tabeller där den används. Mer information om hur valutakonvertering fungerar i den här modellen finns i avsnittet [Valutakonvertering](#currency-conversion) i den här dokumentationen.

![Vi har](assets/marketo-tableau-4.png) om du vill lägga till funktioner för valutakonvertering i beräkningarna i modellen.

Det finns några platser där två tabeller från [!DNL Snowflake] har kombinerats med en union för att skapa en tabell i datamodellen [!DNL Tableau]. I de här instanserna har en Type-kolumn lagts till för att ange vilken [!DNL Snowflake]-tabell den kommer från och vilken entitet raden representerar. Mer information om de tabeller som har kombinerats finns i avsnittet Relation och Dataflöde i den här dokumentationen.

![Det finns några ställen där två tabeller från Snowflake har](assets/marketo-tableau-3.png)

### Segmentnamn {#segment-names}

Eftersom segmentnamn är anpassningsbara har de generiska kolumnnamn i Snowflake datalager. [!DNL BIZ_SEGMENT_NAMES] är en mappningstabell som listar det generiska segmentnamnet med det anpassade segmentnamnet som det mappas till, enligt definitionen i segmentavsnittet i [!DNL Marketo Measure]-gränssnittet. Om du använder egna segmentnamn och vill uppdatera [!DNL Tableau]-modellen så att den innehåller dessa, använder du den här tabellen och byter namn manuellt på kolumnerna i Tableau-modellen. Segmentkolumnerna finns i tabellen Lead och Attribution Touchpoint och behöver bara byta namn en gång.

Kolumnen [!UICONTROL CATEGORY] listar kategorinumret och kolumnen SEGMENT_NAME har det anpassade segmentnamn som den mappar till.

![KATEGORIkolumnen listar kategorinumret och SEGMENTNAME-kolumnen](assets/marketo-tableau-13.png)

Namn kan uppdateras på två sätt. Det första alternativet är att uppdatera den anpassade SQL:en. I det här exemplet har kategorierna 1-6 bytt namn baserat på mappningen från tabellen Segmentnamn.

![Namn kan uppdateras på två sätt. Det första alternativet är ](assets/marketo-tableau-14.png)

Det andra alternativet är att byta namn på kolumnerna direkt i tabellen [!DNL Tableau].

![Det andra alternativet är att byta namn på kolumnerna direkt i ](assets/marketo-tableau-9.png)

## Datamodell {#data-model}

Klicka på bilden nedan för att se vilken version den har.

[![Klicka på bilden nedan för att se vilken version den har.](assets/marketo-tableau-8.png)](assets/tableau-model-1.png){target="_blank"}

### Relationer och dataflöde {#relationships-and-data-flow}

Händelsedata, som används för att skapa kontaktytor, lagras i tabellerna [!UICONTROL Session], [!UICONTROL Task], [!UICONTROL Event], [!UICONTROL Activity] och [!UICONTROL Campaign Member]. Dessa händelsetabeller kopplas till Touchpoint-tabellen via sina respektive ID:n, och om händelsen resulterade i en kontaktyta lagras information i Touchpoint-tabellen.

Kontaktpunkter för lead och attribuering kombineras till en tabell i den här modellen, med en länk till kontakttabellen. Kolumnen &quot;Touchpoint Type&quot; har lagts till för att ange om en rad är en lead eller en Attribution-kontaktyta. De flesta dimensionella data för Lead- och Attribution Touchpoints hämtas från länken till motsvarande Touchpoint.

Scenövergångar för säljprojekt och Lead-scenövergångar kombineras till en tabell i den här modellen, med en länk till [!UICONTROL Lead and Attribution]-kontakttabellen. Kolumnen&quot;Övergångstyp&quot; har lagts till för att ange om en rad är en övergång av typen säljprojekt eller Lead-fas.

Både kostnads- och slutpunktsdata delar kanaldimensioner och kampanjdimensioner. Det är dock begränsat i Tableau att det är möjligt att modellera delade dimensioner mellan faktatabeller. Eftersom vi är begränsade till endast en delad dimensionstabell har data för Kanal och Kampanj kombinerats till en tabell. De kombineras med hjälp av en korskoppling av de två dimensionerna till en tabell i Tablet: Channel och Campaign. Det unika ID:t skapas genom att kanal- och kampanj-ID sammanfogas. Samma ID-värde läggs till i både Touchpoint- och Cost-tabellerna för att skapa en relation till den här kombinerade dimensionstabellen.

![Både kostnads- och slutpunktsdata delar kanaldimensioner och kampanjdimensioner. Tableau](assets/marketo-tableau-10.png)

I den här modellen är Campaign- och Channel-dimensionerna länkade till Touchpoint, så alla rapporter om de här dimensionerna är via den här länken och innebär att dimensionell rapportering av händelsedata kan vara ofullständig. Detta beror på att många händelser inte har länkar till de här dimensionerna förrän de har bearbetats till kontaktpunkter.

>[!NOTE]
>
>Vissa händelser, till exempel sessioner, har direkta länkar till kampanjdimensionerna och kanaldimensionerna. Om du vill rapportera på sessionsnivå om de här dimensionerna rekommenderar vi att en separat datamodell skapas för detta ändamål.

Kostnadsdata lagras på olika aggregeringsnivåer i kostnadsregistret för Snowflake datalager. För alla annonsleverantörer kan kampanjnivådata samlas på kanalnivå. Därför hämtar den här modellen kostnadsdata baserat på flaggan&quot;campaign_is_aggregatable_cost&quot;. Självrapporterade kostnader kan bara skickas på kanalnivå och behöver inte ha Campaign-data. För att få en så korrekt kostnadsrapportering som möjligt hämtas självrapporterade kostnader baserat på flaggan&quot;channel_is_aggregatable_cost&quot;. Frågan som importerar kostnadsdata skrivs med följande logik: Om ad_provider = &quot;SelfReported&quot; så är channel_is_aggregatable_cost = true, else campaign_is_aggregatable_cost = true.

I den här modellens sammanhang betraktas lead-, [!UICONTROL Contact]-, [!UICONTROL Account]- och [!UICONTROL Opportunity]-data som dimensionella data och kopplas direkt till lead- och attributslutpunktstabellen.

### Valutakonvertering {#currency-conversion}

Kurserna i tabellen Konverteringsränta representerar det värde som behövs för att konvertera ett belopp från företagets valuta. Konvertering till valfri valuta kräver en dubbel konvertering, först från den ursprungliga valutan till företagsvalutan och sedan från företagsvalutan till den valda valutan. Det första steget i den här kedjan i modellen är att lägga till två kolumner med dessa konverteringsgrader i tabellerna med belopp, möjlighet och kostnad. Dessa steg beskrivs i avsnittet Rader tillagda i det här dokumentet. Eftersom konverteringsgrader inte behöver vara statiska och kan ändras med angivna datumintervall, måste alla valutakonverteringsberäkningar utföras på radnivå. Konverteringen från den ursprungliga valutan till företagsvalutan består av att dividera värdet med företagets konverteringsgrad och sedan multiplicera med målkonverteringsgraden. Målkonverteringsgraden bestäms av det valda valutaparametervärdet.

* Konvertera det ursprungliga värdet till företagets valutavärde/konverteringsgrad = värde i företagets valuta
* Konvertera värdet från företag till valt valutavärde i företagsvalutan `*`, konverteringsgrad för vald valuta = värde i vald valuta

![Konvertera värdet från företag till vald valuta i företagsvaluta](assets/marketo-tableau-11.png)

Valutakonverteringsmåtten i den här modellen ersätter kursen med värdet 1,0 om ingen konverteringsgrad kan identifieras. Separata mått har skapats för att visa valutavärdet för måttet och larm om en beräkning innehåller mer än ett valutavärde (det vill säga, ett värde kunde inte konverteras till den valda valutan). Dessa mått, Kostnadsvaluta och Intäktsvaluta, inkluderas som verktygstips i alla visuella data som visar kostnads- eller intäktsdata.

![Valutakonverteringsmåtten i den här modellen ersätter värdet 1.0](assets/marketo-tableau-12.png)

## Datadefinitioner {#data-definitions}

Definitioner har lagts till i [!DNL Tableau model] för parametrar, anpassade kolumner och mått.

![Definitioner har lagts till i tabellmodellen för parametrar, anpassad](assets/marketo-tableau-15.png)

Om du vill visa definitioner för kolumner som kommer direkt från [!DNL Snowflake] läser du [dokumentationen för datalagret](/help/data-warehouse-schema.md){target="_blank"}.

## Skillnader mellan mallar och Upptäck {#discrepancies-between-templates-and-discover}

### Attribuerad intäkt {#attributed-revenue}

Kontaktpunkter för lead och attribuering för Touchpoints ärver dimensionella data från den ursprungliga kontaktytan. Rapporteringsmallens alla ärvda dimensionella data från relationen till kontaktpunkten, medan dimensionella data i identifieringsmodellen denormaliseras till lead- och attribueringsslutpunktsposterna. De totala inkomster som avsatts för rörledningen eller de intäktsvärden som härrör från detta bör ligga i linje med de båda rapporterna. Skillnader kan dock observeras när intäkterna bryts ned eller filtreras efter dimensionella data (kanal, delkanal eller kampanj). Om dimensionella intäktsbelopp inte matchar mellan mallen och Discover saknas förmodligen beröringspunktsposter i mallrapportdatauppsättningen. Detta inträffar när det finns en lead- eller attribueringsslutpunktspost, men ingen motsvarande post i slutpunktstabellen i datauppsättningen som importeras till rapporten. Eftersom dessa tabeller filtreras efter ändringsdatum är det möjligt att Touchpoint-posten för lead/attribut har ändrats senare än Touchpoint-posten, och därför har Touchpoint för lead/attribut importerats till datauppsättningen medan den ursprungliga Touchpoint-posten inte var det. Du kan åtgärda problemet genom att utvidga det filtrerade datumintervallet för Touchpoint-tabellen eller ta bort datumbegränsningen tillsammans.

>[!NOTE]
>
>Slutpunkten är en stor tabell, så tänk på skillnaden mellan en mer komplett datauppsättning och mängden data som måste importeras.

### Kostnad {#cost}

Kostnadsrapporteringen i mallarna är endast tillgänglig på kampanj- och kanalnivå, men Discover erbjuder rapportering på lägre detaljnivå för vissa annonsleverantörer (dvs. kreativa, nyckelord, annonsgrupper osv.). Mer information om hur kostnadsdata modelleras i mallarna finns i avsnittet [!UICONTROL Data Model] i den här dokumentationen. Om dimensionsfiltret i [!UICONTROL Discover] är inställt på kanal eller kampanj, ska kostnaderna på kanal-, delkanals- och kampanjnivåerna stämma överens mellan Discover och rapportmallarna.

### avkastning {#roi}

Eftersom avkastningen beräknas utifrån Attribut för intäkter och kostnader kan samma avvikelser som kan uppstå i dessa beräkningar uppstå i avkastningen och av samma skäl, vilket framgår av dessa avsnitt.

### Pekpunkter {#touchpoints}

Dessa mått, som de visas i rapportmallarna, speglas inte i Discover. Det finns för närvarande ingen direkt jämförelse mellan de båda.

### Webbtrafik {#web-traffic}

Rapportmallens datamodell normaliserar kanal-, delkanals- och kampanjdimensionella data via relationen mellan Session och Touchpoint. Detta skiljer sig från datamodellen Discover, som denoraliserar dessa dimensioner till Session. På grund av den här skillnaden bör antalet besök och besökare stämma överens mellan Discover och rapportmallen, men när de visas eller filtreras efter dimension förväntas inte numren att stämma överens. Detta beror på att dimensionella data i mallen bara är tillgängliga för webbhändelser som resulterade i en kontaktyta (d.v.s. icke-anonyma händelser). Mer information finns i avsnittet [Datamodell](#data-model) i den här dokumentationen.

Det kan finnas små avvikelser i det totala antalet webbplatsformulär mellan [!DNL Discover] och mallen. Detta beror på att datamodellen i rapportmallen hämtar dimensionella data för platsformulär via en relation till Session och sedan Touchpoint. Det finns några instanser där data för webbplatsformulär inte har någon korrelerad session.

### Leads och konton {#leads-and-accounts}

Dimensionell rapportering för berörda konton kan skilja sig något mellan [!DNL Discover] och mallen. Detta beror på den dimensionella modelleringen som kommer från relationen mellan kontaktpunkten och kontaktpunkten för lead eller attribueringsslutpunkten. Mer information finns i informationen som beskrivs i avsnittet Attribuerad intäkt.

Alla lead-antal i [!UICONTROL Discover] tilldelas lead-antal och i rapportmallen är måttet [!UICONTROL leads] rört. Det finns därför ingen direkt jämförelse mellan de två rapporterna om denna åtgärd.

### Åtagandesökväg {#engagement-path}

Det finns ingen direkt jämförelse mellan [!UICONTROL Engagement Path]-rapporten i [!DNL Discover] och mallen. Rapporten i [!DNL Discover] är baserad på slutpunkten medan rapporten i mallen är baserad på slutpunkten för attribuering. Mallen fokuserar enbart på möjligheter och relaterade kontaktytor i stället för att visa alla kontaktytpunktsdata.

### Avtalshastighet {#deal-velocity}

Det ska inte finnas några skillnader mellan den här rapporten i mallen och avtalsrutan i kontrollpanelen för snabbhet i Discover.
