---
unique-page-id: 30082018
description: Försenad cookie-synkronisering - [!DNL Marketo Measure] - Produktdokumentation
title: Försenad cookie-synkronisering
exl-id: 394053ed-5642-48e4-b83c-c483a58ebbd7
source-git-commit: ae5b77744d523606ce6cfcf48d7e8d5049d5ccb7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Försenad cookie-synkronisering {#delayed-cookie-sync}

Den här ändringen är standard [!DNL Marketo Measure] Javascript ger [!DNL bizible.js] API-stöd så att du kan konfigurera JS-programmet så att besökarnas användaraktiviteter lagras temporärt, men inte skicka informationen till [!DNL Marketo Measure] servern tills användaren ger sitt medgivande.

## Instruktioner {#how-to}

Ersätt standard [!DNL bizible.js] script-tagg med följande:

`<script id="bizible-settings" type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" data-consent-button-id="ConsentButtonId"></script>`

Attributet data-medgivande-button-id=&quot;ConsentButtonId&quot; anger [!DNL bizible.js] att inte skicka analysdata förrän någon klickar på ett HTML-element med detta ID.

Alternativt kan kunderna ange [!UICONTROL data-consent-button-id] vara något obefintligt (t.ex. &quot;foobar&quot;) och använda följande API för att berätta [!DNL bizible.js] som användaren har godkänt:

`window['Bizible'] = window['Bizible'] || { _queue: [], Push: function (o, p) {this._queue.push({ type: o, data: p }); } };`
`Bizible.Push("Consent", true });`

>[!NOTE]
>
>Användarens samtycke sparas i cookien, vilket innebär att när användaren väl har godkänt anropet så behöver det inte göras på efterföljande sidor.

## Begränsning {#limitation}

För [!DNL bizible.js] sparar tillfälligt oskickade webbaktiviteter i kundernas cookies från första part, och storleken på cookies från första part är begränsad, endast tre oskickade begäranden kan sparas åt gången.

Om det redan finns tre väntande förfrågningar kommer alla efterföljande aktiviteter att ignoreras. den första sidvyn, som innehåller värdefull referensinformation, bevaras.
