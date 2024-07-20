---
description: "[!DNL Marketo Measure] Rapportmall - Power BI - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Rapportmall - Power BI"
exl-id: c296b8f9-4033-4723-9a71-63a458640d27
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 0%

---

# [!DNL Marketo Measure] rapportmall - Power BI {#marketo-measure-report-template-power-bi}

## Komma igång {#getting-started}

Du kan komma åt Power BI-rapportmallen [här](https://github.com/adobe/Marketo-Measure-BI-Templates){target="_blank"}.

Öppna Power BIET för rapportmallen för Adobe [!DNL Marketo Measure].

![](assets/marketo-measure-report-template-power-bi-1.png)

Du kan hitta specifik information om server, lager och schema i användargränssnittet för [!DNL Marketo Measure] på informationssidan för [!DNL Data Warehouse]. Instruktioner för hur du hittar den här sidan finns [här](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target="_blank"}.

Parametrarna QueryFilterStartDate och QueryFilterEndDate används för att begränsa mängden data som importeras. Parametrarna måste ha SQL-format som de används i frågor som skickas till [!DNL Snowflake]. Om du till exempel vill begränsa data till de senaste två åren blir QueryFilterStartDate `dateadd` (year,-2,current_date())). Dessa parametrar jämförs med datetime-datatyper, så vi rekommenderar att du använder `dateadd` (day,1,current_date()) för QueryFilterEndDate för att returnera alla data till den aktuella tiden.

## Dataanslutning {#data-connection}

De parametrar som anges när filen öppnas används för att strukturera interna frågor som importerar tabeller från datalagret. Du måste fortfarande konfigurera en dataanslutning till din [!DNL Snowflake]-instans. För detta behöver du samma server- och lagerställenamn tillsammans med ditt användarnamn och lösenord. Information om var du kan hitta ditt användarnamn och återställa lösenordet finns [här](/help/marketo-measure-data-warehouse/data-warehouse-access-reader-account.md){target="_blank"}.

## Dataimport {#data-import}

Om du vill förbättra rapportens prestanda och utnyttja omvandlingsfunktionerna i Power Query ska du konfigurera den här mallen med importlagringsmetoden.

### Frågeparametrar {#query-parameters}

För att begränsa vilka data som importeras till modellen ställs varje tabell in med en intern fråga som källa. Interna frågor kräver godkännande för att köras. Du måste klicka på Kör för varje fråga. Det här steget behövs bara första gången frågorna körs eller om parametrarna ändras.

![](assets/marketo-measure-report-template-power-bi-2.png)

Alla frågor filtrerar bort raderade rader och tabellerna [!UICONTROL facts] är inställda på att filtrera till rader med ett ändrat datum mellan start- och slutdatum som angetts som parametrar.

>[!NOTE]
>
>Eftersom datumfiltren tillämpas på det ändrade datumet på en rad bör du vara försiktig när du rapporterar datum som ligger utanför det begränsade datumintervallet. Det ändrade datumintervallet är till exempel begränsat till de senaste två åren. Detta kan inkludera en händelse med ett händelsedatum för tre år sedan, men som nyligen har ändrats. Rapportering om händelser för tre år sedan returnerar dock ofullständiga resultat eftersom inte alla rader har ändrats inom den tvååriga tidsramen.

![](assets/marketo-measure-report-template-power-bi-3.png)

Följande tabeller behandlas som faktatabeller. Datumgränserna för ändringsdatum har lagts till i dessa frågor.

* Aktivitet
* Kontaktpunkt
* Kontaktpunkt för lead
* Attribution Touchpoint
* Kostnad
* Webbplatsformulär
* Session
* Kampanjmedlem
* Uppgift
* Händelse
* Övergång mellan lead- och kontaktfas
* Möjlighetsfasövergång

Följande tabeller behandlas som dimensionstabeller. Inga datumgränser har angetts för dessa frågor.

* Konto
* Campaign
* Kontakt
* Konverteringsgrad
* Möjligheter
* Lead
* Scen
* Kanal

## Dataomvandlingar {#data-transformations}

Några omformningar har gjorts på data i Power Query. Om du vill visa specifika omformningar för en tabell öppnar du Power Query, navigerar till en tabell och noterar de använda stegen till vänster i fönstret. Några av de specifika omformningarna beskrivs nedan.

![](assets/marketo-measure-report-template-power-bi-4.png)

### Borttagna kolumner {#removed-columns}

För att förenkla datamodellen och ta bort överflödiga och onödiga data har vi minskat antalet kolumner som importerats till Power BI från den ursprungliga [!DNL Snowflake]-tabellen. De borttagna kolumnerna innehåller onödiga sekundärnycklar, denormaliserade flerdimensionella data som används bättre via relationer till andra tabeller i modellen, granskningskolumner och fält som används för intern [!DNL Marketo Measure]-bearbetning. Du kan lägga till eller ta bort kolumner efter behov. Navigera till steget &quot;Borttagna andra kolumner&quot; efter steget &quot;Source&quot; i en tabell, klicka på kugghjulsikonen och uppdatera de markerade kolumnerna i listan.

>[!NOTE]
>
>* Var försiktig när du lägger till ytterligare värden för främmande nycklar. Power BI ställs ofta in på att automatiskt identifiera relationer i modellen och om du lägger till värden för främmande nycklar kan det leda till oönskade länkar mellan tabeller och/eller inaktivera befintliga relationer.
>
>* De flesta tabeller i datalagret [!DNL Marketo Measure] innehåller denormaliserade dimensionella data. Vi har arbetat för att normalisera och städa upp modellen i Power BI så mycket som möjligt för att förbättra prestanda och datakvalitet. Var försiktig när du lägger till ytterligare normaliserade fält i faktatabeller. Detta kan bryta dimensionell filtrering mellan tabeller och kan också leda till felaktiga rapporter.


![](assets/marketo-measure-report-template-power-bi-5.png)

### Kolumner med ändrat namn {#renamed-columns}

Tabellerna och kolumnerna har bytt namn för att göra dem mer användarvänliga och för att standardisera namnkonventioner. Om du vill visa kolumnnamnsändringarna går du till steget &quot;Kolumner som har bytt namn&quot; efter steget &quot;Andra kolumner har tagits bort&quot; i en tabell.

![](assets/marketo-measure-report-template-power-bi-6.png)

### Bytt namn på segment {#renamed-segments}

Eftersom segmentnamn är anpassningsbara har de generiska kolumnnamn i datalagret i Snowflake. [!DNL BIZ_SEGMENT_NAMES] är en mappningstabell som listar det generiska segmentnamnet och dess mappade anpassade segmentnamn, som definieras i segmentavsnittet i [!DNL Marketo Measure]-gränssnittet. Tabellen Segmentnamn används för att byta namn på segmentkolumnerna i tabellerna Lead Touchpoint och Attribution Touchpoint. Om det inte finns något anpassat segment kvarstår det generiska segmentnamnet.

![](assets/marketo-measure-report-template-power-bi-7.png)

### Skiftlägeskänslig ID-konvertering {#case-sensitive-id-conversion}

[!DNL Marketo Measure]-data har ett par tabeller där ID-värden (primärnyckel) är skiftlägeskänsliga, nämligen Touchpoint och Campaign. Datamotorn som driver Power BI-modelleringslagret är skiftlägeskänslig, vilket resulterar i&quot;duplicerade&quot; ID-värden. För att bevara skiftlägeskänsligheten för dessa nyckelvärden har vi implementerat transformeringssteg som kopplar osynliga tecken till gemena tecken och bevarar ID:ts unika karaktär när det utvärderas i datamotolken. Mer information om problemet och de detaljerade stegen om den metod vi har använt finns [här] (https://blog.crossjoin.co.uk/2019)
/10/06/power-bi-and-case-sensitive/){target="_blank"}. Dessa skiftlägeskänsliga ID-värden är märkta som&quot;ID för koppling&quot; och används som kopplingsnycklar i relationslagret. Vi har dolt kopplings-ID:n från rapporteringslagret och har de ursprungliga ID-värdena synliga för rapportering, eftersom de osynliga tecknen kan störa klippningen
/paste funktioner och filtrering.

![](assets/marketo-measure-report-template-power-bi-8.png)

![](assets/marketo-measure-report-template-power-bi-9.png)

### Rader tillagda {#rows-added}

För att lägga till funktioner för valutakonvertering i beräkningarna i modellen har vi lagt till en kolumn för företagskonverteringssats i tabellerna för säljprojekt och kostnad. Värdet i den här kolumnen läggs till på radnivå och utvärderas genom att koppla till konverteringstabellen för både datum- och valutakod-ID. Mer information om hur valutakonvertering fungerar i den här modellen finns i avsnittet [Valutakonvertering](#currency-conversion) i den här dokumentationen.

![](assets/marketo-measure-report-template-power-bi-10.png)

Registret Konverteringsfrekvens som lagras i [!DNL Snowflake] innehåller ett datumintervall för varje konvertering. Power BI tillåter inte kopplingsvillkor i en beräkning (d.v.s. mellan ett datumintervall). För att kunna ansluta till ett datum har vi lagt till steg i tabellen Konverteringsfrekvens för att expandera raderna så att det finns en rad för varje datum i konverteringsdatumintervallet.

![](assets/marketo-measure-report-template-power-bi-11.png)

## Datamodell {#data-model}

Klicka på bilden nedan för att se vilken version den har.

[![](assets/marketo-measure-report-template-power-bi-12.png)](/help/bi-report-templates/assets/power-bi-data-model.png){target="_blank"}

### Relationer och dataflöde {#relationships-and-data-flow}

Händelsedata, som används för att skapa kontaktytor, lagras i tabellerna [!UICONTROL Session], [!UICONTROL Task], [!UICONTROL Event], [!UICONTROL Activity] och Campaign Member. Dessa händelsetabeller kopplas till Touchpoint-tabellen via sina respektive ID:n, och om händelsen resulterade i en kontaktyta lagras information i Touchpoint-tabellen.

Kontaktpunkter för lead och attribuering lagras i sina egna tabeller med en länk till Touchpoint-tabellen. De flesta dimensionella data för Lead- och Attribution Touchpoints hämtas från länken till motsvarande Touchpoint.

I den här modellen är Campaign- och Channel-dimensionerna länkade till Touchpoint, så alla rapporter om de här dimensionerna är via den här länken och innebär att dimensionell rapportering av händelsedata kan vara ofullständig. Detta beror på att många händelser inte har länkar till de här dimensionerna förrän de har bearbetats till kontaktpunkter. Obs! Vissa händelser, till exempel sessioner, har direkta länkar till kampanjens och kanalens dimensioner. Om du vill rapportera på sessionsnivå om de här dimensionerna rekommenderar vi att en separat datamodell skapas för detta ändamål.

Kostnadsdata lagras på olika aggregeringsnivåer i datalagrets kostnadstabell [!DNL Snowflake]. För alla annonsleverantörer kan kampanjnivådata samlas på kanalnivå. Därför hämtar den här modellen kostnadsdata baserat på flaggan&quot;campaign_is_aggregatable_cost&quot;. Självrapporterade kostnader kan bara skickas på kanalnivå och behöver inte ha Campaign-data. För att få en så korrekt kostnadsrapportering som möjligt hämtas självrapporterade kostnader baserat på flaggan&quot;channel_is_aggregatable_cost&quot;. Frågan som importerar kostnadsdata skrivs med följande logik: Om ad_provider = &quot;SelfReported&quot; så är channel_is_aggregatable_cost = true, else campaign_is_aggregatable_cost = true.

Kostnadsdata och Touchpoint-data har vissa gemensamma dimensioner, så båda faktatabellerna har relationer med dimensionstabellerna Campaign och Channel.

I den här modellens sammanhang betraktas [!UICONTROL Lead]-, [!UICONTROL Contact]-, [!UICONTROL Account]- och [!UICONTROL Opportunity]-data som dimensionella data och kopplas direkt till [!UICONTROL Lead] Touchpoint- och [!UICONTROL Attribution] Touchpoint-tabellerna.

### Tillagda tabeller {#added-tables}

**Datum**

Eftersom Power BI endast tillåter relationer mellan tabeller i en kolumn, lades en datumdimensionstabell till för att underlätta kopplingen mellan tabellerna som innehåller belopp (säljprojekt och kostnad) och konverteringssatsen. I avsnittet Valutakonvertering finns mer information om hur valutakonverteringar beräknas i den här modellen.

**Mått**

Alla åtgärder har lagts till i en särskild åtgärdstabell. Den är inte ansluten till modellen men fungerar som en enda plats där alla mått lagras, så att de blir lätta att använda.

**Attributmodell**

En separat tabell lades till för att lagra namnen på attribueringsmodellerna. Den här tabellen används för att skapa filter som gör det möjligt för användaren att växla mellan attribueringsmodeller för intäktsberäkningar.

### Valutakonvertering {#currency-conversion}

Kurserna i tabellen Konverteringsränta representerar det värde som behövs för att konvertera ett belopp från företagets valuta. Konvertering till valfri valuta kräver en dubbel konvertering, först från den ursprungliga valutan till företagsvalutan och sedan från företagsvalutan till den valda valutan. Det första steget i den här kedjan i modellen är att lägga till en kolumn med konverteringsgraden till företag i tabellerna med belopp, säljprojekt och kostnad. De här stegen beskrivs i rubriken Rader tillagda i avsnittet Dataomvandlingar i det här dokumentet. När du konverterar från den ursprungliga valutan till företagsvalutan delas värdet med den här extra kolumnen. Nästa steg är att multiplicera företagsvalutavärdet med den kurs i konverteringstarifftabellen som motsvarar den valda valutan.

* Konvertera det ursprungliga värdet till företagets valutavärde/konverteringsgrad = värde i företagets valuta
* Konvertera värdet från företag till valt valutavärde i företagsvalutan `*`, konverteringsgrad för vald valuta = värde i vald valuta

Eftersom konverteringsgrader inte behöver vara statiska och kan ändras med angivna datumintervall, måste alla valutakonverteringsberäkningar utföras på radnivå. Eftersom konverteringsgraden gäller för ett visst datumintervall, måste uppslagsberäkningen utföras inom måttets DAX, så relationen kan definieras både för valutakoden och datumet.

Valutakonverteringsmåtten i den här modellen ersätter kursen med värdet 1,0 om ingen konverteringsgrad kan identifieras. Separata mått har skapats för att visa valutavärdet för måttet och larm om en beräkning innehåller mer än ett valutavärde (det vill säga, ett värde kunde inte konverteras till den valda valutan).

![](assets/marketo-measure-report-template-power-bi-13.png)

## Datadefinitioner {#data-definitions}

Definitioner har lagts till i Power BI-modellen för tabeller, anpassade kolumner och mått.

![](assets/marketo-measure-report-template-power-bi-14.png)

![](assets/marketo-measure-report-template-power-bi-15.png)

![](assets/marketo-measure-report-template-power-bi-16.png)

Om du vill visa definitioner för kolumner som kommer direkt från [!DNL Snowflake] läser du [dokumentationen för datalagret](/help/marketo-measure-data-warehouse/data-warehouse-schema.md){target="_blank"}

## Skillnader mellan mallar och Upptäck {#discrepancies-between-templates-and-discover}

### Attribuerad intäkt {#attributed-revenue}

Kontaktpunkter för lead och attribuering för Touchpoints ärver dimensionella data från den ursprungliga kontaktytan. Rapporteringsmallens alla ärvda dimensionella data från relationen till kontaktpunkten, medan dimensionella data i identifieringsmodellen denormaliseras till lead- och attribueringsslutpunktsposterna. De totala inkomster som avsatts för rörledningen eller de intäktsvärden som härrör från detta bör ligga i linje med de båda rapporterna. Skillnader kan dock observeras när intäkterna bryts ned eller filtreras efter dimensionella data (kanal, delkanal eller kampanj). Om dimensionella intäktsbelopp inte matchar mellan mallen och Discover saknas förmodligen beröringspunktsposter i mallrapportdatauppsättningen. Detta inträffar när det finns en lead- eller attribueringsslutpunktspost, men ingen motsvarande post i slutpunktstabellen i datauppsättningen som importeras till rapporten. Eftersom dessa tabeller filtreras efter ändringsdatum är det möjligt att Touchpoint-posten för lead/attribut har ändrats senare än Touchpoint-posten, och därför har Touchpoint för lead/attribut importerats till datauppsättningen medan den ursprungliga Touchpoint-posten inte var det. Du kan åtgärda problemet genom att utvidga det filtrerade datumintervallet för Touchpoint-tabellen eller ta bort datumbegränsningen tillsammans. Obs! Touchpoint är en stor tabell, så tänk på skillnaden mellan en mer fullständig datauppsättning och mängden data som måste importeras.

### Kostnad {#cost}

Kostnadsrapporteringen i mallarna är endast tillgänglig på kampanj- och kanalnivå, men Discover erbjuder rapportering på lägre detaljnivå för vissa annonsleverantörer (d.v.s. kreativa nyckelord, annonsgrupper osv.). Mer information om hur kostnadsdata modelleras i mallarna finns i avsnittet Datamodell i den här dokumentationen. Om dimensionsfiltret i [!UICONTROL Discover] är inställt på kanal eller kampanj, ska kostnaderna på kanal-, delkanals- och kampanjnivåerna stämma överens mellan Discover och rapportmallarna.

### avkastning {#roi}

Eftersom avkastningen beräknas utifrån Attribut för intäkter och kostnader kan samma avvikelser som kan uppstå i dessa beräkningar uppstå i avkastningen och av samma skäl, vilket framgår av dessa avsnitt.

### Pekpunkter {#touchpoints}

Dessa mått, som de visas i rapportmallarna, speglas inte i Discover. Det finns för närvarande ingen direkt jämförelse mellan de båda.

### Webbtrafik {#web-traffic}

Rapportmallens datamodell normaliserar kanal-, delkanals- och kampanjdimensionella data via relationen mellan Session och Touchpoint. Detta skiljer sig från datamodellen Discover, som denoraliserar dessa dimensioner till Session. På grund av den här skillnaden bör antalet besök och besökare stämma överens mellan Discover och rapportmallen, men när de visas eller filtreras efter dimension förväntas inte numren att stämma överens. Detta beror på att dimensionella data i mallen bara är tillgängliga för webbhändelser som resulterade i en kontaktyta (dvs. icke-anonyma händelser). Mer information finns i avsnittet [Datamodell](#data-model) i den här dokumentationen.

Det kan finnas små avvikelser i det totala antalet webbplatsformulär mellan [!DNL Discover] och mallen. Detta beror på att datamodellen i rapportmallen hämtar dimensionella data för platsformulär via en relation till Session och sedan Touchpoint. Det finns några instanser där data för webbplatsformulär inte har någon korrelerad session.

### Leads och konton {#leads-and-accounts}

Dimensionell rapportering för berörda konton kan skilja sig något mellan Discover och mallen. Detta beror återigen på dimensionell modellering som kommer från relationen mellan Touchpoint och Lead Touchpoint eller Attribution Touchpoint. Mer information finns i informationen som beskrivs i avsnittet Attribuerad intäkt.

Alla lead-värden i Discover tilldelas lead-antal, och i rapportmallen anges antalet leads. Det finns därför ingen direkt jämförelse mellan de två rapporterna om denna åtgärd.

### Åtagandesökväg {#engagement-path}

Det finns ingen direkt jämförelse mellan rapporten [!UICONTROL Engagement Path] i Discover och mallen. Rapporten i [!DNL Discover] är baserad på slutpunkten medan rapporten i mallen är baserad på slutpunkten för attribuering. Mallen fokuserar enbart på möjligheter och relaterade kontaktytor i stället för att visa alla kontaktytpunktsdata.

### Avtalshastighet {#deal-velocity}

Det ska inte finnas några skillnader mellan den här rapporten i mallen och avtalsrutan i kontrollpanelen för snabbhet i Discover.
