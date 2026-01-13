---
description: Integrerade annonsplattformar - [!DNL Marketo Measure]
title: Integrerade annonsplattformar
exl-id: df30ee8a-8b07-4f14-94e8-cc482fca8b18
feature: APIs, Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 0%

---


# Integrerade annonsplattformar {#integrated-ad-platforms}

[!DNL Marketo Measure] har API-anslutningar med Google AdWords, Microsoft BingAds, [!DNL Facebook] Ads och DoubleClick Campaign Manager. Genom dessa API-anslutningar kan [!DNL Marketo Measure] enkelt hämta data och skicka dem till din CRM tillsammans med den externa Buyer-appen. Inga manuella överföringar av kostnader eller data krävs. Dina konton behöver bara vara anslutna och auktoriserade till appen [!DNL Marketo Measure]. [!DNL Marketo Measure] hämtar sedan automatiskt dina marknadsföringskostnader från plattformarna och läser in dem i appen [!DNL Marketo Measure]. Om du väljer att aktivera automatisk taggning för AdWords, BingAds eller [!DNL Facebook] Ads, kommer [!DNL Marketo Measure] automatiskt att lägga till sina parametrar till webbadresserna för dina annonser.

## Ansluta annonsplattformar {#how-to-connect-ad-platforms}

Innan vi börjar gå igenom detaljerna för varje plattform går vi igenom hur du ansluter något av dessa konton till [!DNL Marketo Measure]. Logga först in i appen [!DNL Marketo Measure] och navigera till alternativet **[!UICONTROL Settings]** på fliken **[!UICONTROL My Account]** längst upp till vänster på skärmen. Välj sedan **[!UICONTROL Connections]** under avsnittet **[!UICONTROL Integrations]** till vänster.

Som visas i bilden nedan visas en knapp för att skapa nya annonsanslutningar.

![Sidan Anslutningar med knappen Konfigurera ny annonsanslutning](assets/2.png)

När du har klickat på knappen [!UICONTROL Set up New Ads Connection] öppnas ett fönster (visas nedan) med fyra och [!UICONTROL connect]-jontyper. Klicka på Anslut så visas ett annat fönster där du tillfrågas om inloggningsuppgifter. Ange autentiseringsuppgifterna och klicka på [!UICONTROL authorize] för att ansluta kontot till [!DNL Marketo Measure].

![Marketo Measure annonserar anslutningsspärrar med tillgängliga kontotyper](assets/select-account-type.png)

## Google AdWord {#google-adwords}

När du skapar dina annonser i [!DNL Google AdWords] uppmanas du att tagga dina kampanjer på ett av tre sätt: manuell taggning, automatisk taggning eller genom att skapa en spårningsmall. När du taggar din AdWords-URL manuellt måste du definiera och lägga till parametrarna i slutet av annonsernas URL:er. Manuell taggning gör att andra plattformar än Google enkelt kan läsa data som samlats in med parametrarna.

Spårningsmallen är ett verktyg som Google tillhandahåller för att lägga till det som anropar ValueTrack-parametrar. De fungerar på samma sätt som UTM och andra taggningsparametrar.

## Vad händer när automatisk taggning är aktiverat {#what-happens-when-auto-tagging-is-enabled}

[!DNL Marketo Measure] Söker efter spårningsmallar i ditt [!DNL AdWords]-konto:

* *Alternativ A*: Spårningsmall hittades. [!DNL Marketo Measure] lägger till sina parametrar i mallen.
* *Alternativ B*: Omdirigering från tredje part hittades. Om en omdirigering från tredje part påträffas i spårningsmallen kan [!DNL Marketo Measure] inte utföra någon åtgärd. Du måste lägga till [!DNL Marketo Measure]-taggarna manuellt i tredjepartssystemet. Ett exempel på en omdirigering från tredje part är ett budhanteringsverktyg som Kenshoo eller Marin. Läs mer om hur [budhanteringsverktyg påverkar [!DNL Marketo Measure]](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

* *Alternativ C*: Ingen spårningsmall hittades. [!DNL Marketo Measure] söker igenom alla dina URL:er för annonsmål efter [!DNL Marketo Measure]-parametrarna. Baserat på skanningen, om:
   * Parametrar hittades: installationen är klar!
   * Det gick inte att hitta parametrar: [!DNL Marketo Measure] kommer att lägga till sina parametrar i slutet av URL:erna för annonseringsmål. [!DNL Marketo Measure] lägger till nya annonser inom två timmar efter att de har skapats. Tänk på att parametrarna inte läggs till i en mall.

Läs mer om funktionen [[!DNL AdWords] för automatisk taggning](/help/api-connections/understanding-marketo-measure-adwords-tagging.md){target="_blank"}.

## Så här aktiverar du [!DNL Marketo Measure] automatisk taggning för ord {#how-to-enable-marketo-measure-auto-tagging-for-adwords}

Innan du aktiverar automatisk taggning för [!DNL Marketo Measure] måste du **se till att en spårningsmall är aktiverad på kontonivå, kampanjnivå eller annonsgruppsnivå i ditt Adwords-konto. Detta krävs för alla Adwords-konton som har [!DNL Marketo Measure] automatisk taggning aktiverat.** Om du aktiverar en spårningsmall förhindras alla förluster i data för annonshistorik. Observera att aktivering av spårningsmallar på nyckelords-, sigillänks- eller annonsnivå gör att annonsen går igenom gransknings- och godkännandeprocessen och kan starta om annonsernas prestandahistorik. Om ingen spårningsmall är aktiverad över huvud taget, kommer [!DNL Marketo Measure] att lägga till spårningsparametrarna [!DNL Marketo Measure] direkt till annonsens &quot;Final URL&quot;, vilket också kan leda till att annonshistorikdata går förlorade.

När du har en spårningsmall på plats följer du instruktionerna nedan för att aktivera automatisk taggning för [!DNL Marketo Measure]. Obs! [!DNL Marketo Measure] taggar även automatiskt alla pausade annonser i ditt konto.

1. Logga in på ditt [!DNL Marketo Measure]-konto på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

1. Gå till [!UICONTROL My Account] > [!UICONTROL Settings] > [!UICONTROL Integrations] > [!UICONTROL Connections].

   ![Anslutningslista med befintliga annonskonton](assets/4.png)

1. Klicka på pennikonen bredvid det Adwords-konto som ska ha [!DNL Marketo Measure] automatisk taggning aktiverad.

   ![Lägg till kontoinställningspanelen med växlingsknappen Automatisk taggning](assets/5.png)

1. I det övre högra hörnet växlar du **[!UICONTROL Autotagging]** till **[!UICONTROL Yes]**. Klicka på **[!UICONTROL Learn More]** längst ned på sidan för att utöka textrutan och klicka på **[!UICONTROL Save]**. Konfigurationen av automatisk taggning är klar.

   ![Bekräftelsemodal automatisk taggning i Marketo Measure](assets/6.png)

## Konfigurera en spårningsmall i AdWords med [!DNL Marketo Measure] parametrar {#how-to-set-up-a-tracking-template-in-adwords-with-marketo-measure-parameters}

Kom ihåg att du bör lägga till spårningsmallar på [!UICONTROL Account]-, [!UICONTROL Campaign]- eller annonsgruppsnivå i AdWords. Om du lägger till spårningsmallar på nyckelord-, webbplatslänks- eller annonsnivå måste annonsen gå igenom gransknings- och godkännandeprocessen och du riskerar att starta om annonsernas prestandahistorik. Läs mer om att [skapa spårningsmallar](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"}.

1. Logga in på ditt [!DNL Google AdWords]-konto.
1. Gå till [!UICONTROL Campaigns]-vyn från det vänstra navigeringsfältet
1. Navigera till [!UICONTROL Settings], även i det vänstra navigeringsfältet
1. Växla till vyn [!UICONTROL Account Settings] längst upp
1. Expandera avsnittet [!UICONTROL Tracking]
1. Klistra in en av följande textsträngar i spårningsmallen för att ange mallens värde:

   * Om du har frågetecken i ALLA URL:er använder du följande URL-text:

   `{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

   * Om du inte har några frågetecken på någon av dina URL-adresser lägger du till följande URL-text:

   `{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}*`

   För att förhindra att fel uppstår när du taggar dina URL:er manuellt rekommenderar vi att du genererar UTM-parametrarna automatiskt. Det behöver inte innebära automatisk taggning med AdWords- eller [!DNL Marketo Measure]-parametrar. Det finns flera verktyg som förenklar processen genom att parametrarna för URL:en genereras automatiskt baserat på den information du anger.

   >[!TIP]
   >Om du får ett felmeddelande om att spårningsmallen är ogiltig kan du försöka rensa webbläsarens cache och försöka igen. Detta löser ofta problemet.

## Generera UTM-taggar automatiskt för [!DNL Google AdWords] {#how-to-automatically-generate-utm-tags-for-google-adwords}

UTM-taggar kan se svåra att skapa i början, men det finns många verktyg som du kan använda för att enkelt skapa URL:er med UTM-parametrar. Du kan använda någon av följande resurser eller söka på webben efter fler verktyg. Tänk på att [!DNL Marketo Measure] inte stöder eller garanterar någonting med dessa plattformar och verktyg.

**[!DNL Google URL]Builder**

Google URL Builder är standardverktyg för att skapa korrekt formaterade URL:er med UTM-taggar. Ange URL-adressen och det önskade värdet för varje parameter och klicka på [!UICONTROL Generate URL]. Det här är ett idealiskt verktyg om du bara har en handfull URL:er att tagga. Öppna verktyget [här](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"}.

**Google-kalkylblad genererat av EpikOne**

Det här kalkylbladet innehåller en formel som automatiskt genererar taggade mål-URL:er. Det här är ett bra verktyg om du behöver tagga ett stort antal länkar. Få åtkomst till kalkylbladet [här](https://spreadsheets.google.com/ccc?key=p7c_HKcmspSUfEYSO0gskKw&hl=en){target="_blank"}.

**Rafflecopter Link Tagging Tool**

Kalkylbladet som skapas av Rafflecopter är en modifierad version av kalkylbladet [!DNL EpikOne's]. Den innehåller också en formel som automatiskt genererar taggade mållänkar som du kan använda.

Vart och ett av dessa verktyg innehåller detaljerade anvisningar om hur du använder och ändrar dem efter behov. Verktyget är tillgängligt [här](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"}.

**Gäller endast UTM Builder**

Det här verktyget är ett Chrome-tillägg som gör att du snabbt kan generera UTM-taggar. Hitta den [här](https://chrome.google.com/webstore/detail/effin-amazing-utm-builder/eoaapiimcaimddnfhfnifgkinmpcbccp?hl=en){target="_blank"}.

## Bing Ads {#bing-ads}

Bing Ads är en integrerad plattform som gör att du kan aktivera automatisk taggning för URL-adresser eller använda ett verktyg från tredje part, som [!DNL Marketo Measure], för att tagga annonser. [!DNL Bing Ads] är också beroende av UTM-parametrar.

Vår integrering har stöd för följande annonstyper:

* Text Ad
* Mobil annons
* Utökad textannons

Funktionen för automatisk taggning i Bing Ads lägger till följande UTM-parametrar:

* Utm_källa
* Utm_medium
* Utm_term

Den automatiska taggningen för Bing Ads lägger även till följande anpassade parameter:

`_bt={adid}`

Strängen skulle se ut så här:

`{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`

Det är viktigt att komma ihåg att [!DNL Bing Ads] gör att du kan lägga till ännu fler parametrar genom att använda deras anpassade taggar i dina slutliga URL:er för att få mer granularitet, om du vill.

En spårningsmall kan användas om det behövs, men det är inte nödvändigt för [!DNL Bing Ads] och [!DNL Marketo Measure] att integrera. Detta beror på att [!DNL Bing] tillåter att annonser redigeras utan att ändra historik, så [!DNL Marketo Measure] kan uppdatera mål-URL:en.

Automatisk taggning ska aktiveras via [!DNL Marketo Measure] så att de anpassade [!DNL Marketo Measure]-parametrarna kan läggas till automatiskt. Det finns ingen risk för att Bing Ads förlorar historik över tidigare annonseringar.

Mer information om hur du lägger till taggar på plattformen finns på webbplatsen [[!DNL Bing Ads]](https://advertise.bingads.microsoft.com/en-us/blog/post/august-2016/upgraded-urls-now-available-in-bing-ads-an-easier-way-to-manage-your-tracking-urls){target="_blank"}.

## Facebook-annonser {#facebook-ads}

Integrationen [!DNL Marketo Measure] med [!DNL Facebook] gör att den automatiskt kan hämta annonsinformation och tagga URL:en med sina parametrar. [!DNL Marketo Measure] hämtar information om Campaign och Ad Set via vår automatiska taggning. Ad Set fyller i vårt fält för annonsgruppnamn. Mer information om hur du konfigurerar URL-taggar på plattformen [!DNL Facebook] finns på sidan [!DNL Facebook] [business](https://www.facebook.com/business/help/1016122818401732/?ref=u2u){target="_blank"} .

Innan du aktiverar automatisk taggning med [!DNL Facebook Ads] är det viktigt att exportera den tidigare prestandahistoriken som en CSV-fil. När [!DNL Marketo Measure] taggar [!DNL Facebook Ads] med parametern _bf läser [!DNL Facebook] annonserna som helt nya och raderar prestandahistoriken. Därför är det viktigt att du exporterar ett register över tidigare prestanda om det är något av värde för dig och din organisation.

Observera att du när som helst kan ansluta ditt [!DNL Facebook]-konto till [!DNL Marketo Measure]-appen och inga data går förlorade. Det är bara när automatisk taggning är aktiverat som prestandahistoriken rensas.

Mer information om hur du exporterar [&#x200B; annonsrapporter finns i &#x200B;](https://www.facebook.com/business/help/393890194130036){target="_blank"}den här artikeln[!DNL Facebook] från Facebook.

## LinkedIn Sponsrat innehåll {#linkedin-sponsored-content}

Med LinkedIn-integreringen kan [!DNL Marketo Measure] tagga mål-URL:er för [!DNL LinkedIn] Sponsored Content, vilket gör att [!DNL Marketo Measure] kan följa en användare genom hela deras kontaktyta och mappa aktiviteten tillbaka till den specifika [!DNL LinkedIn] Campaign och Creative. Detta ger kunderna insikter om avkastningen på deras [!DNL LinkedIn]-aktivitet. [!DNL Marketo Measure] söker efter kreatörer med en unik [!DNL LinkedIn] Share och lägger till en `?_bl={creativeId}`-parameter i slutet av den.

Eftersom [!DNL LinkedIn]-resurser kan användas i flera kampanjer och kreativa projekt ber vi att kunderna inte kopierar/klonar/duplicerar befintliga Creative-objekt så att de kan behålla sin unika karaktär. Om resurser hittas och bara används på en Creative kan [!DNL Marketo Measure] tagga delningen som den är utan att behöva återskapa några Creative- eller Shares-objekt och all annonshistorik (visningar, klickningar, delningar) finns kvar.

Så snart en resurs har delats av flera Creative-medlemmar måste [!DNL Marketo Measure] utföra en paus, kopiering och omtaggning för att skapa en unik uppsättning. [!DNL Marketo Measure] pausar och arkiverar aktiva kreatörer, vilket innebär att den kreativa som innehåller visningar, klickningar och sociala resurser också arkiveras.

## Icke-integrerade plattformar {#non-integrated-platforms}

För plattformar som inte är integrerade med [!DNL Marketo Measure] går det inte att använda funktionen för automatisk taggning i [!DNL Marketo Measure]. Parametrarna måste läggas till manuellt.
