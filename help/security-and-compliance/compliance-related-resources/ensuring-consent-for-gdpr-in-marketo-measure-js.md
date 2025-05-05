---
unique-page-id: 35586069
description: Säkerställa samtycke för GDPR i Marketo Measure JS - Marketo Measure - produktdokumentation
title: Säkerställa samtycke för GDPR i Marketo Measure JS
exl-id: 9afc5e4d-cf97-4c49-b9ee-ee1cc99c1f90
feature: Tracking
source-git-commit: 4787f765348da71bc149c997470ce678ba498772
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Säkerställa samtycke för GDPR i Marketo Measure JS {#ensuring-consent-for-gdpr-in-marketo-measure-js}

Den allmänna dataskyddsförordningen är en EU-lagstiftning som trädde i kraft den 25 maj 2018.

## Översikt {#overview}

Syftet med den allmänna dataskyddsförordningen är att stärka de registrerades rättigheter inom Europeiska unionen (EU) och Europeiska ekonomiska samarbetsområdet (EES) när det gäller hur deras personuppgifter används och skyddas. Med personuppgifter avses alla uppgifter som rör en identifierad eller identifierbar fysisk person. Den allmänna dataskyddsförordningen gäller alla organisationer inom eller utanför EU som marknadsför varor eller tjänster till och/eller spårar beteenden hos registrerade inom EU och EES. Om ni gör affärer med registrerade i Europa som innefattar behandling av deras personuppgifter, gäller denna lagstiftning er. Påföljderna för bristande efterlevnad är betydande, med stora böter för dem som bryter mot förordningen. Det högsta bötesbeloppet för en enskild överträdelse är 20 miljoner euro eller 4 % av den globala årsomsättningen, beroende på vilket som är störst.

Som standard samlar [!DNL bizible.js] in användarens analysdata om det inte är konfigurerat att vänta på samtycke. När [!DNL bizible.js] är konfigurerad att vänta på användarens samtycke skapas inga cookies eller inga analysdata skickas förrän du har fått samtycke.

## Så här väntar du på godkännande {#how-to-wait-for-consent}

Det finns två sätt att ange [!DNL bizible.js] som väntar på godkännande.

Alternativ 1 - Ersätt standardskripttaggen [!DNL bizible.js] med:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

**Om du använder [!DNL Google Tag Manager] för att installera skript** bör du tänka på att GTM tar bort data- attribut, så använd följande skript i stället:

`<span id="bizible-settings" data-consent-button-id="ConsentButtonId"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>I det här fallet kopplar [!DNL bizible.js] en on-click-händelse till elementet HTML med ID &quot;ConsentButtonId&quot;.

När du klickar på det här HTML-elementet skapas en cookie i [!DNL bizible.js] för att komma ihåg att användarens samtycke har tagits emot och börja samla in analysdata som vanligt.

**-or-**

Alternativ 2 - Ersätt standardskripttaggen [!DNL bizible.js] med:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-requires-user-consent="true"></script>`

Detta anger för [!DNL bizible.js] att inte spåra förrän samtycke har erhållits, vilket kan göras med följande JS-API:

*window[&#39;Bizible&#39;] = window[&#39;Bizible&#39;] || &lbrace;_queue: [], Push: function (o, p) { this._queue.push({ typ: o, data: p }); };*

*Bizibel. Push(&#39;Consent&#39;, true);*

**Om du använder [!DNL Google Tag Manager] för att installera skript** bör du tänka på att GTM tar bort data- attribut, så använd följande skript i stället:

`<span id="bizible-settings" data-requires-user-consent="true"></span>`
`<script type="text/javascript" src=https://cdn.bizible.com/scripts/bizible.js async=""></script>`

>[!NOTE]
>
>bizible.js skapar en cookie som kommer ihåg att användarens samtycke har tagits emot och börjar samla in analysdata som vanligt först efter att JS API har anropats.

Kunder kan däremot också använda denna API för att återkalla användarens samtycke:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) { this._queue.push({ type: o, data: p }); } };`

`Bizible.Push('Consent', false);`

När den här koden körs tar den bort alla cookies som [!DNL bizible.js] tidigare har skapat och återupptar bara samlingen av analysdata om användaren gör det igen.
