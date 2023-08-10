---
description: God praxis för API-anslutningar - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa tillvägagångssätt för API-anslutningar
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Bästa tillvägagångssätt för API-anslutningar {#best-practices-for-api-connections}

## Ökning {#overview}

[!DNL Marketo Measure] erbjuder API-anslutningar med [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads]och LinkedIn. Dessa API-anslutningar aktiverar [!DNL Marketo Measure] för att hämta in en mängd data från era annonsplattformar som sedan kan rapporteras i era Buyer Touchpoint-data. En viktig egenskap för dessa API-anslutningar är deras förmåga att hämta utgiftsdata automatiskt, vilket sparar både tid och arbete för teamet som krävs för att manuellt överföra data för rapportering av avkastning. Det är inte obligatoriskt att konfigurera dessa API-anslutningar för [!DNL Marketo Measure] för att spåra dessa kanaler, men de ger värdefull detaljinformation som förbättrar er rapportering.

The [!DNL Marketo Measure] API-anslutningar är en ovärderlig aspekt av ditt konto, och våra rekommendationer för bästa praxis hjälper dig och ditt team att utnyttja våra anslutningar i största möjliga utsträckning.

## Bästa praxis {#best-practice}

Oavsett vilken annonsplattform du ansluter är följande riktlinjer viktiga att tänka på!

* Använd en administratör för att ansluta
* Du kan ansluta flera annonskonton för en plattform
* Koppla samman alla annonskonton för att automatisera utgiftsrapporteringen så mycket som möjligt
* Implementera alltid en spårningsmall om den är tillgänglig. Mallen ser till att även om annonskontot kopplas från, [!DNL Marketo Measure] kan fortfarande hantera detaljinformation om annonser

Optimera varje [!DNL Marketo Measure] API, följ gärna följande metodtips.

**[!DNL Facebook]**: Ansluta med automatisk taggning

Innan du aktiverar automatisk taggning exporterar du din annonshistorik till en csv. Om du aktiverar automatisk taggning återställs konverteringshistoriken och det sociala beviset för alla annonser som taggats av [!DNL Marketo Measure].

Genom att följa vår rekommendation om god praxis [!DNL Marketo Measure] [!DNL Facebook] API kan:

* Tagga alla automatiskt [!DNL Facebook] Ads with the necessary [!DNL Marketo Measure] parameter `_bf ={creative}`
* Ladda ned kostnadsinformation för alla aktiva [!DNL Facebook] annonser

>[!NOTE]
>
>Det finns ingen spårningsmall för [!DNL Facebook], använder API:t parametern auto-tagged (_bf) för att samla in annonsinformationen.

**AdWords**: Implementera en spårningsmall på kontonivå och aktivera automatisk taggning

[!DNL Marketo Measure] rekommenderar att du använder en mall för kontonivå, kampanjnivå eller annonsnivåspårning, eftersom den gör det möjligt att lägga till och ta bort parametrar för alla annonser utan risk för avbrott eller radering av annonshistorik.

Genom att följa vår rekommendation om god praxis [!DNL Marketo Measure] AdWords API kan:

* Tagga alla AdWords Ads automatiskt med [!DNL Marketo Measure] parametrar för `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Ladda ned annonsinformation för alla aktiva annonser

**Bing**: Implementera en spårningsmall på kontonivå och aktivera automatisk taggning

Det finns ingen risk för att du förlorar annonshistorik när du konfigurerar [!DNL Bing] API-anslutning, till skillnad från vissa andra API-anslutningar.

Genom att följa vår rekommendation om god praxis [!DNL Marketo Measure] Bing API kan:
* Tagga alla Bing Ads automatiskt med följande parametrar för `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Hämta annonsinformation för alla aktiva Bing-annonser

**LinkedIn**: Ansluta med automatisk taggning

När du aktiverar automatisk taggning återskapas en resurs och placeras i en ny Creative-version, den gamla Creative-versionen arkiveras.

Genom att följa vår rekommendation om god praxis [!DNL Marketo Measure] LinkedIn API kan:

* Tagga automatiskt alla LinkedIn-annonser som är annonstyper Sponsored Content med nödvändiga [!DNL Marketo Measure] parameter_bl={creativeId}. Den här parametern hämtar in det kreativa ID:t som tillåter [!DNL Marketo Measure] för att lösa kampanjer och kreativ information.
* Ladda ned kostnadsinformation för alla aktiva program som stöds [!DNL LinkedIn] annonser

>[!NOTE]
>
>Det finns ingen spårningsmall för [!DNL LinkedIn], förlitar sig API på den automatiskt taggade parametern (_bl) för att samla in all eventuell annonsinformation.

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Vi rekommenderar att du regelbundet granskar din anslutning, om det är möjligt, varje månad, även om du följer våra rutiner för att skydda dig från att förlora data om du inte är uppkopplad. Det här är en enkel visuell kontroll av [!UICONTROL Connections] i [!DNL Marketo Measure] app för att säkerställa att det inte finns några röda nyckelikoner, vilket signalerar ett frånkopplat konto.

När ett API-anslutet konto kopplas från, [!DNL Marketo Measure] kan inte hämta utgiftsdata i eller tagga nya annonser. Därför rekommenderar vi alltid att du implementerar en spårningsmall om det är möjligt. Mallen ser till att även om annonskontot kopplas från, [!DNL Marketo Measure] kan fortfarande tagga annonserna och dra in detaljinformation om annonserna. När du har återanslutit kommer utgiftsdata att återfyllas och störningen i din rapportering om betald kanal är minimal.

Orsaker till frånkoppling och omauktorisering inkluderar..

* Lösenordsändring till det personkonto som är anslutet
* Den personen är inte längre på företaget
* Uppdateringar av API:er

Om ditt team har upplevt något av ovanstående scenarier bör du kontrollera dina API-anslutningar i [!DNL Marketo Measure] app för att säkerställa att de inte behöver auktoriseras på nytt.

>[!MORELIKETHIS]
>
>* [Integrerade annonsplattformar (API:er)](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md)
>* [Hur budhanteringsverktygen påverkar [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md)
>* [[!DNL Marketo Measure] Förklara API-parametrar](/help/api-connections/utilizing-marketo-measures-api-connections/marketo-measure-parameters.md)
>* [Facebook API - översikt](/help/api-connections/utilizing-marketo-measures-api-connections/facebook-api.md)
>* [[!DNL LinkedIn] Integreringsöversikt](/help/api-connections/utilizing-marketo-measures-api-connections/linkedin-integration.md)
>* [Översikt över integrering av annonstavlor](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md)
>* [Återauktoriserar anslutna API-konton](/help/api-connections/utilizing-marketo-measures-api-connections/reauthorizing-connected-accounts.md)
