---
description: Bästa praxis för API-anslutningar - [!DNL Marketo Measure]
title: Bästa tillvägagångssätt för API-anslutningar
exl-id: b8550e4e-a567-427f-b5d3-50232553a066
feature: APIs, Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 0%

---


# Bästa tillvägagångssätt för API-anslutningar {#best-practices-for-api-connections}

## Översikt {#overview}

[!DNL Marketo Measure] erbjuder API-anslutningar med [!DNL Google AdWords], [!DNL Microsoft Bing Ads], [!DNL Facebook Ads] och LinkedIn. Dessa API-anslutningar gör att [!DNL Marketo Measure] kan hämta olika data från dina annonsplattformar som sedan kan rapporteras i dina Buyer Touchpoint-data. En viktig egenskap för dessa API-anslutningar är deras förmåga att hämta utgiftsdata automatiskt, vilket sparar både tid och arbete för teamet som krävs för att manuellt överföra data för rapportering av avkastning. Det är inte obligatoriskt för [!DNL Marketo Measure] att konfigurera dessa API-anslutningar för att spåra kanalerna, men de ger värdefull detaljerad information som förbättrar din rapportering.

API-anslutningarna för [!DNL Marketo Measure] är en ovärderlig aspekt av ditt konto, och våra rekommendationer om god praxis hjälper dig och ditt team att utnyttja våra anslutningar i största möjliga utsträckning.

## Bästa praxis {#best-practice}

Oavsett vilken annonsplattform du ansluter är följande riktlinjer viktiga att tänka på!

* Använd en administratör för att ansluta
* Du kan ansluta flera annonskonton för en plattform
* Koppla samman alla annonskonton för att automatisera utgiftsrapporteringen så mycket som möjligt
* Implementera alltid en spårningsmall om den är tillgänglig. Mallen ser till att även om annonskontot kopplas från kan [!DNL Marketo Measure] fortfarande hämta detaljerade annonsuppgifter

Om du vill optimera varje [!DNL Marketo Measure]-API följer du de bästa metoderna.

**[!DNL Facebook]**: Anslut med automatisk taggning

Innan du aktiverar automatisk taggning exporterar du din annonshistorik till en csv. Om du aktiverar automatisk taggning återställs konverteringshistoriken och det sociala beviset för alla annonser som taggats av [!DNL Marketo Measure].

Genom att följa vår rekommendation om god praxis kan [!DNL Marketo Measure] [!DNL Facebook]-API:t:

* Tagga alla [!DNL Facebook] annonser automatiskt med den nödvändiga [!DNL Marketo Measure]-parametern `_bf ={creative}`
* Hämta annonsinformation för alla aktiva [!DNL Facebook]-annonser

>[!NOTE]
>Det finns ingen spårningsmall för [!DNL Facebook]. API:t använder den automatiska taggade parametern (_bf) för att samla in annonsinformationen.

**AdWords**: Implementera en spårningsmall på kontonivån och aktivera automatisk taggning

[!DNL Marketo Measure] rekommenderar att du använder en mall för kontonivå, kampanjnivå eller annonsnivåspårning, eftersom det gör det möjligt att lägga till och subtrahera parametrar för alla annonser utan risk för avbrott eller borttagning av annonshistorik.

Genom att följa vår rekommendation om god praxis kan API:t för [!DNL Marketo Measure] AdWords:

* Tagga alla AdWords-annonser automatiskt med [!DNL Marketo Measure]-parametrarna för `_bk={keyword}, _bt={creative}, _bm={matchtype}, _bn={network}, _bg={adgroupID}`
* Ladda ned annonsinformation för alla aktiva annonser

**Bing**: Implementera en spårningsmall på kontonivån och aktivera automatisk taggning

Det finns ingen risk för att annonshistorik förloras när du konfigurerar din [!DNL Bing] API-anslutning, till skillnad från vissa andra API-anslutningar.

Genom att följa vår rekommendation om god praxis kan Bing API:t för [!DNL Marketo Measure]:

* Tagga alla Bing Ads automatiskt med följande parametrar för `_bt={adid}, utm_medium=cpc, utm_source=bing, utm_term={keyword}`
* Hämta annonsinformation för alla aktiva Bing-annonser

**LinkedIn**: Anslut med automatisk taggning

När du aktiverar automatisk taggning återskapas en resurs och placeras i en ny Creative, den gamla Creative arkiveras.

Genom att följa vår rekommendation om god praxis kan [!DNL Marketo Measure] LinkedIn API:

* Tagga automatiskt alla LinkedIn-annonser som är annonstyp sponsrat innehåll med den nödvändiga [!DNL Marketo Measure]-parametern _bl={creativeId}. Den här parametern hämtar in det kreativa ID:t som gör att [!DNL Marketo Measure] kan lösa kampanjen och den kreativa informationen.
* Hämta annonsinformation för alla aktiva och stödda [!DNL LinkedIn]-annonser

>[!NOTE]
>Det finns ingen spårningsmall för [!DNL LinkedIn], API:t förlitar sig på den automatiskt taggade parametern (_bl) för att samla in all möjlig annonsinformation.

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Vi rekommenderar att du regelbundet granskar din anslutning, om det är möjligt, varje månad, även om du följer våra rutiner för att skydda dig från att förlora data om du inte är uppkopplad. Det här är en enkel visuell kontroll av avsnittet [!UICONTROL Connections] i [!DNL Marketo Measure]-appen för att kontrollera att det inte finns några röda nyckelikoner, vilket signalerar ett frånkopplat konto.

När ett API-anslutet konto kopplas från kan [!DNL Marketo Measure] inte hämta utgiftsdata eller tagga nya annonser. Därför rekommenderar vi alltid att du implementerar en spårningsmall om det är möjligt. Mallen ser till att även om annonskontot kopplas från kan [!DNL Marketo Measure] fortfarande tagga annonserna och dra in detaljinformation. När du har återanslutit kommer utgiftsdata att återfyllas och störningen i din rapportering om betald kanal är minimal.

Orsaker till frånkoppling och omauktorisering inkluderar..

* Lösenordsändring till det personkonto som är anslutet
* Den personen är inte längre på företaget
* Uppdateringar av API:er

Om ditt team har upplevt något av ovanstående scenarier bör du kontrollera dina API-anslutningar i appen [!DNL Marketo Measure] för att vara säker på att de inte behöver auktoriseras på nytt.

>[!MORELIKETHIS]
> [Integrerade API:er (Ad Platforms)](/help/api-connections/integrated-ad-platforms.md)
> [Så här påverkar hanteringsverktygen för bud  [!DNL Marketo Measure]](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md)
> [[!DNL Marketo Measure] API-parametrar förklaras](/help/api-connections/marketo-measure-parameters.md)
> [Översikt över Facebook-API ](/help/api-connections/facebook-api.md)
> [[!DNL LinkedIn] Integreringsöversikt](/help/api-connections/linkedin-integration.md)
> [Integreringsöversikt för AdWords](/help/api-connections/understanding-marketo-measure-adwords-tagging.md)
> [Återauktoriserar anslutna API-konton ](/help/api-connections/reauthorizing-connected-accounts.md)
