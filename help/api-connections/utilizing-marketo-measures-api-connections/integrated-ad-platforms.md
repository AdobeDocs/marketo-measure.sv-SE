---
unique-page-id: 18874594
description: Integrerade annonsplattformar - [!DNL Marketo Measure] - Produktdokumentation
title: Integrerade annonsplattformar
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
feature: APIs, Integration
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 0%

---

# Integrerade annonsplattformar {#integrated-ad-platforms}

[!DNL Marketo Measure] har API-anslutningar med Google AdWords, Microsoft BingAds, [!DNL Facebook] Ads and DoubleClick Campaign Manager. Genom dessa API-anslutningar [!DNL Marketo Measure] kan enkelt hämta data och skicka dem till din CRM tillsammans med den externa Buyer-appen. Inga manuella överföringar av kostnader eller data krävs. I stället behöver dina konton bara vara anslutna och auktoriserade till [!DNL Marketo Measure] app. [!DNL Marketo Measure] hämtar då automatiskt era marknadsföringskostnader från plattformarna och laddar in dem i [!DNL Marketo Measure] app. Om du väljer att aktivera automatisk taggning för AdWords, BingAds eller [!DNL Facebook] Ads, [!DNL Marketo Measure] kommer automatiskt att lägga till sina parametrar till webbadresserna till era annonser.

## Ansluta annonsplattformar {#how-to-connect-ad-platforms}

Innan vi börjar gå igenom detaljerna för de olika plattformarna ska vi gå igenom hur vi kopplar dessa konton till [!DNL Marketo Measure]. Logga först in på [!DNL Marketo Measure] och navigera till **[!UICONTROL Settings]** alternativ under **[!UICONTROL My Account]** längst upp till vänster på skärmen. Nästa, välj **[!UICONTROL Connections]** under **[!UICONTROL Integrations]** till vänster.

Som visas i bilden nedan visas en knapp för att skapa nya annonsanslutningar.

![](assets/2.png)

När du har klickat på [!UICONTROL Set up New Ads Connection] visas ett fönster med fyra annonser [!UICONTROL connect]jontyper. Klicka på Anslut så visas ett annat fönster där du tillfrågas om inloggningsuppgifter. Ange inloggningsuppgifterna och klicka på [!UICONTROL authorize] för att ansluta kontot till [!DNL Marketo Measure].

![](assets/select-account-type.png)

## Google AdWord {#google-adwords}

När du skapar dina annonser i [!DNL Google AdWords]kan du tagga kampanjer på något av tre sätt: manuell taggning, automatisk taggning eller genom att skapa en spårningsmall. När du taggar din AdWords-URL manuellt måste du definiera och lägga till parametrarna i slutet av annonsernas URL:er. Manuell taggning gör att andra plattformar än Google enkelt kan läsa data som samlats in med parametrarna.

Spårningsmallen är ett verktyg som Google tillhandahåller för att lägga till det som anropar ValueTrack-parametrar. De fungerar på samma sätt som UTM och andra taggningsparametrar.

## Vad händer när automatisk taggning är aktiverat {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Söker efter spårningsmallar i [!DNL AdWords] konto:

* *Alternativ A*: Spårningsmall hittades. [!DNL Marketo Measure] lägger till dess parametrar i mallen.
* *Alternativ B*: Omdirigering från tredje part hittades. Om en omdirigering från tredje part hittas i spårningsmallen, [!DNL Marketo Measure] kan inte utföra någon åtgärd. Du måste lägga till [!DNL Marketo Measure] -taggar i tredjepartssystemet. Ett exempel på en omdirigering från tredje part är ett budhanteringsverktyg som Kenshoo eller Marin. Läs mer om hur [budhanteringsverktyg påverkar [!DNL Marketo Measure]](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Alternativ C*: Ingen spårningsmall hittades. [!DNL Marketo Measure] söker igenom alla dina URL:er för annonsmål efter [!DNL Marketo Measure] parametrar. Baserat på skanningen, om:
   * Parametrar hittades: installationen är klar!
   * Det gick inte att hitta parametrarna: [!DNL Marketo Measure] kommer att lägga till sina parametrar i slutet av URL:erna för annonsmålet. [!DNL Marketo Measure] lägger till nya annonser inom två timmar efter att de har skapats. Tänk på att parametrarna inte läggs till i en mall.

Läs mer om våra [[!DNL AdWords] funktioner för automatisk taggning](/help/api-connections/utilizing-marketo-measures-api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Aktivera [!DNL Marketo Measure] Automatisk taggning för ord {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Före aktivering [!DNL Marketo Measure] automatisk taggning, **Kontrollera att du har en spårningsmall aktiverad på konto-, kampanj- eller annonsgruppsnivå i ditt Adwords-konto. Detta krävs för alla Adwords-konton som har [!DNL Marketo Measure] autotaggning har aktiverats.** Om du aktiverar en spårningsmall förhindras alla förluster i data för annonshistorik. Observera att aktivering av spårningsmallar på nyckelords-, sigillänks- eller annonsnivå gör att annonsen går igenom gransknings- och godkännandeprocessen och kan starta om annonsernas prestandahistorik. Om ingen spårningsmall är aktiverad alls [!DNL Marketo Measure] kommer att lägga till [!DNL Marketo Measure] spårningsparametrar direkt till annonsens &quot;Final URL&quot;, som också kan resultera i förlust av annonshistorikdata.

När du har en spårningsmall på plats följer du instruktionerna nedan för att aktivera [!DNL Marketo Measure] Automatisk taggning. Obs! [!DNL Marketo Measure] kommer även att tagga alla pausade annonser i ditt konto automatiskt.

1. Logga in på [!DNL Marketo Measure] konto på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Gå till [!UICONTROL My Account] > [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Connections].

   ![](assets/4.png)

1. Klicka på pennikonen bredvid det Adwords-konto som ska ha [!DNL Marketo Measure] autotaggning har aktiverats.

   ![](assets/5.png)

1. I det övre högra hörnet växlar du **[!UICONTROL Autotagging]** växla till **[!UICONTROL Yes]**. Klicka på längst ned på sidan **[!UICONTROL Learn More]** för att utöka textrutan och klicka på **[!UICONTROL Save]**. Konfigurationen av automatisk taggning är klar.

   ![](assets/6.png)

## Ställa in en spårningsmall i AdWords med [!DNL Marketo Measure] Parametrar {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

Kom ihåg att du bör lägga till spårningsmallar på [!UICONTROL Account], [!UICONTROL Campaign] eller Lägg till gruppnivå i AdWords. Om du lägger till spårningsmallar på nyckelord-, webbplatslänks- eller annonsnivå måste annonsen gå igenom gransknings- och godkännandeprocessen och du riskerar att starta om annonsernas prestandahistorik. Läs mer om [skapa spårningsmallar](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Logga in på [!DNL Google AdWords] Konto.
1. Gå till [!UICONTROL Campaigns] vy från det vänstra navigeringsfältet
1. Navigera till[!UICONTROL Settings]&quot;, även i det vänstra navigeringsfältet
1. Växla till[!UICONTROL Account Settings]&quot; längst upp
1. Expandera[!UICONTROL Tracking]&quot;
1. Klistra in en av följande textsträngar i spårningsmallen för att ange mallens värde:

   * Om du har frågetecken i ALLA URL:er använder du följande URL-text:

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Om du inte har några frågetecken på någon av dina URL-adresser lägger du till följande URL-text:

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   För att förhindra att fel uppstår när du taggar dina URL:er manuellt rekommenderar vi att du genererar UTM-parametrarna automatiskt. Det behöver inte innebära automatisk taggning med AdWords eller [!DNL Marketo Measure] parametrar finns det flera verktyg som förenklar processen genom att automatiskt generera parametrar för URL:en baserat på den information du anger.

   >[!TIP]
   >
   >Om du får ett felmeddelande om att spårningsmallen är ogiltig kan du försöka rensa webbläsarens cache och försöka igen. Detta löser ofta problemet.

## Generera UTM-taggar automatiskt för [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

UTM-taggar kan se svåra att skapa i början, men det finns många verktyg som du kan använda för att enkelt skapa URL:er med UTM-parametrar. Du kan använda någon av följande resurser eller söka på webben efter fler verktyg. Kom ihåg att [!DNL Marketo Measure] stöder eller garanterar ingenting med dessa plattformar och verktyg.

**[!DNL Google URL]Builder**

Google URL Builder är standardverktyg för att skapa korrekt formaterade URL:er med UTM-taggar. Ange bara URL-adressen och det önskade värdet för varje parameter och klicka på &quot;[!UICONTROL Generate URL]&quot;. Det här är ett idealiskt verktyg om du bara har en handfull URL:er att tagga. Öppna verktyget [här](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"}.

**Google-kalkylblad genererat av EpikOne**

Det här kalkylbladet innehåller en formel som automatiskt genererar taggade mål-URL:er. Det här är ett bra verktyg om du behöver tagga ett stort antal länkar. Öppna kalkylbladet [här](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&amp;hl=en){target="_blank"}.

**Rafflecopter Link Tagging Tool**

Kalkylbladet som skapas av Rafflecopter är en modifierad version av [!DNL EpikOne's] kalkylblad. Den innehåller också en formel som automatiskt genererar taggade mållänkar som du kan använda.

Vart och ett av dessa verktyg innehåller detaljerade anvisningar om hur du använder och ändrar dem efter behov. Verktyget är tillgängligt [här](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Fantastisk UTM Builder**

Det här verktyget är ett Chrome-tillägg som gör att du snabbt kan generera UTM-taggar. Hitta den [här](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Bing Ads {#bing-ads}

Bing Ads är en integrerad plattform som gör att du kan aktivera automatisk taggning för URL-adresser eller använda ett verktyg från tredje part, till exempel [!DNL Marketo Measure], för att tagga annonser. [!DNL Bing Ads] är också beroende av UTM-parametrar.

Funktionen för automatisk taggning i Bing Ads lägger till följande UTM-parametrar:

* Utm_källa
* Utm_medium
* Utm_term

Den automatiska taggningen för Bing Ads lägger även till följande anpassade parameter:

`_bt={adid}`

Strängen skulle se ut så här:

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

Det är viktigt att notera att [!DNL Bing Ads] Med kan du lägga till ännu fler parametrar genom att använda egna taggar i de slutliga URL:erna för att få mer granularitet, om du vill.

Du kan använda en spårningsmall om du vill, men det är inte nödvändigt för [!DNL Bing Ads] och [!DNL Marketo Measure] att integrera. Det beror på att [!DNL Bing] tillåter att annonser redigeras utan att historiken ändras, så [!DNL Marketo Measure] kan uppdatera mål-URL:en.

Automatisk taggning ska aktiveras med [!DNL Marketo Measure] så att den [!DNL Marketo Measure] parametrar kan läggas till automatiskt. Det finns ingen risk för att Bing Ads förlorar tidigare annonseringsinsatser.

Besök [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"} för mer information om hur du lägger till taggar på deras plattform.

## Facebook Ads {#facebook-ads}

The [!DNL Marketo Measure] integrering med [!DNL Facebook] gör att den automatiskt kan hämta annonsinformation och tagga URL:en med sina parametrar. [!DNL Marketo Measure] kommer att hämta in information om Campaign och Ad Set via vår automatiska taggning. Ad Set fyller i vårt fält för annonsgruppnamn. Mer information om hur du konfigurerar URL-taggar finns på [!DNL Facebook] -plattformen, besök [!DNL Facebook] [företag](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"} sida.

Innan du aktiverar automatisk taggning med [!DNL Facebook Ads]är det viktigt att exportera den tidigare prestandahistoriken som en CSV-fil. Vid den här tidpunkten [!DNL Marketo Measure] taggar [!DNL Facebook Ads] med parametern _bf, [!DNL Facebook] läser annonserna som helt nya och raderar prestandahistoriken. Därför är det viktigt att du exporterar ett register över tidigare prestanda om det är något av värde för dig och din organisation.

Observera att du kan ansluta [!DNL Facebook] kontot när som helst till [!DNL Marketo Measure] och inga data går förlorade. Det är bara när automatisk taggning är aktiverat som prestandahistoriken rensas.

[Läs den här artikeln](https://www.facebook.com/business/help/393890194130036){target="_blank"} från Facebook om du vill ha mer information om export [!DNL Facebook] Annonsrapporter.

## LinkedIn Sponsored Content {#linkedin-sponsored-content}

Tack vare LinkedIn-integreringen kan [!DNL Marketo Measure] att tagga mål-URL:er på [!DNL LinkedIn] Sponsrat innehåll, som i slutänden tillåter [!DNL Marketo Measure] för att följa en användare genom hela deras kontaktyta och kartlägga aktiviteten tillbaka till den specifika [!DNL LinkedIn] Campaign och Creative. Detta ger kunderna insikter om avkastningen på deras [!DNL LinkedIn] aktivitet. [!DNL Marketo Measure] söker efter kreatörer med en unik [!DNL LinkedIn] Dela och lägga till en `?_bl={creativeId}` -parametern till slutet av den.

För [!DNL LinkedIn] Resurser kan användas för flera kampanjer och kreatörer, vi ber att kunderna inte kopierar/klonar/duplicerar befintliga kreatörer så att de kan bibehålla sin unika karaktär. Om aktier hittas och endast kan användas på en Creative-medlem, [!DNL Marketo Measure] Du kan tagga webbgalleriet som det är utan att behöva återskapa några Creative- eller Shares-objekt och all annonshistorik (visningar, klickningar, delningar) finns kvar.

Så snart en resurs har visats vara delad mellan flera olika kreatörer, [!DNL Marketo Measure] måste gå igenom en process för att pausa, kopiera och tagga om för att skapa en unik uppsättning. [!DNL Marketo Measure] kommer att pausa och arkivera aktiva kreatörer, vilket innebär att kreativiteten som innehåller visningar, klickningar och sociala resurser också arkiveras.

## Icke-integrerade plattformar {#non-integrated-platforms}

För plattformar som inte är integrerade med [!DNL Marketo Measure], [!DNL Marketo Measure] Funktionen för automatisk taggning kan inte användas. Parametrarna måste läggas till manuellt.
