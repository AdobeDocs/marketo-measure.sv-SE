---
description: '[!DNL Marketo Measure] cookies - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] cookies'
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Marketo Measure Cookies {#marketo-measure-cookies}

Lär dig mer om de olika [!DNL Marketo Measure]-cookies som är inlästa på din webbplats när du använder JavaScript [!DNL Marketo Measure] på dina landningssidor. Den här informationen kan vara användbar för webbutvecklingsteamet under implementeringen.

>[!IMPORTANT]
>
>På grund av integritetsproblem är cookies från tredje part på väg ut. Google Chrome presenterade borttagning av cookies från tredje part under tredje kvartalet 2024 vilket effektivt markerar slutet på den här typen av spårning. Detta innebär att Adobe tar bort Marketo Measure-funktioner som är beroende av cookies från tredje part, närmare bestämt Cross-Domain Tracking och View-through Attribution, som använder Google/DoubleClick-cookie. Inga andra funktioner i Marketo Measure påverkas. Användning av cookies från första part påverkas inte heller. Mot bakgrund av Google tidsplan är det förväntade borttagningsdatumet för de två funktionerna ovan 6/1/2024. Relaterade data som samlats in före detta datum är fortfarande tillgängliga för Adobe-kunder.

| Kaknamn | Cookie-typ | Syfte | Förfaller | Har säker flagga angetts? | Har bara HTTP-flagga angetts? | Cookie Setter |
| --- | --- | --- | --- | --- | --- | --- |
| `_biz_uid` | Förste part | Identifiera en användare unikt på den aktuella domänen. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_nA` | Förste part | Ett sekvensnummer som Marketo Measure inkluderar för alla begäranden för intern diagnostik. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_flagsA` | Förste part | En cookie som lagrar olika typer av användarinformation, t.ex. formuläröverföring, domänövergripande migrering, genomskinlig pixel, spårningsavanmälningsstatus osv. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_pendingA` | Förste part | Lagrar analysdata tillfälligt tills de har skickats till Marketo Measure-servern. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_ABTestA` | Förste part | Lista över kontrollsummor från Optimizely och Visual Web Optimizer ABTests-data som redan har rapporterats, vilket förhindrar `bizible.js` från att skicka om insamlade data. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_EventA` | Förste part | Lista över kontrollsummor som rapporterats av Bizible Events för att förhindra att `bizible.js` skickar om insamlade data. | 1 år | Nej | Nej | `bizible.js` |
| `_biz_su` | Förste part | Universellt användar-ID för att identifiera en användare i flera domäner, som bara gäller för innehavare där integreringen åsidosätter ITP-begränsningar. | 1 år | Ja | Nej | Edgecast |
| `_BUID` | Tredje part, domän=.bizible.com | Universellt användar-ID för att identifiera en användare i flera domäner. | 1 år | Ja | Nej | Edgecast |
| `_BUID` | Tredje part, domän=.bizibly.com | Mappning mellan Marketo Measure cookie-ID på klientens domän och dess Doubleclick-cookie-ID. | 1 år | Ja | Nej | Edgecast |

Om en brandväggsvarning för webbprogram (WAF) utlöses under JavaScript-konfigurationen kan användare antingen inaktivera den WAF-regeln eller tillåtslista cookies, som i följande exempel:

![Om en brandväggsvarning för webbprogram (WAF) aktiveras under JavaScript](assets/adding-script-1.png)
