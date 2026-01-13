---
description: '[!DNL Marketo Measure] cookies - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] cookies'
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Marketo Measure Cookies {#marketo-measure-cookies}

Lär dig mer om de olika [!DNL Marketo Measure]-cookies som är inlästa på din webbplats när du använder JavaScript [!DNL Marketo Measure] på dina landningssidor. Den här informationen kan vara användbar för webbutvecklingsteamet under implementeringen.

>[!IMPORTANT]
>På grund av integritetsproblem är cookies från tredje part på väg ut. Google Chrome presenterade borttagning av cookies från tredje part under tredje kvartalet 2024 vilket effektivt markerar slutet på den här typen av spårning. Detta innebär att Adobe tar bort Marketo Measure-funktioner som är beroende av cookies från tredje part, närmare bestämt Cross-Domain Tracking och View-through Attribution, som använder Google/DoubleClick-cookie. Inga andra funktioner i Marketo Measure påverkas. Användning av cookies från första part påverkas inte heller. Mot bakgrund av Google tidsplan är det förväntade borttagningsdatumet för de två funktionerna ovan 6/1/2024. Relaterade data som samlats in före detta datum är fortfarande tillgängliga för Adobe-kunder.

<table>
<thead>
  <tr>
    <th>Kaknamn</th>
    <th>Cookie-typ</th>
    <th>Syfte</th>
    <th>Förfaller</th>
    <th>Har säker flagga angetts?<br></th>
    <th>Har bara HTTP-flagga angetts?</th>
    <th>Cookie Setter</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>_biz_uid</td>
    <td>Förste part</td>
    <td>Identifiera en användare unikt på den aktuella domänen.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_nA</td>
    <td>Förste part</td>
    <td>Ett sekvensnummer som Marketo Measure inkluderar för alla begäranden för intern diagnostik.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_flagsA</td>
    <td>Förste part</td>
    <td>En cookie som lagrar olika typer av användarinformation, t.ex. formuläröverföring, domänövergripande migrering, genomskinlig pixel, spårningsavanmälningsstatus osv.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_pendingA</td>
    <td>Förste part</td>
    <td>Lagrar analysdata tillfälligt tills de har skickats till Marketo Measure-servern.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_ABTestA</td>
    <td>Förste part</td>
    <td>Lista över kontrollsummor från Optimizely och Visual Web Optimizer ABTestar data som redan har rapporterats, vilket förhindrar att bizible.js skickar insamlade data på nytt.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_EventA</td>
    <td>Förste part</td>
    <td>Lista över kontrollsummor som rapporterats av Bizible Events för att förhindra att bizible.js skickar insamlade data igen.</td>
    <td>1 år</td>
    <td>Nej</td>
    <td>Nej</td>
    <td>bizible.js</td>
  </tr>
  <tr>
    <td>_biz_su</td>
    <td>Förste part</td>
    <td>Universellt användar-ID för att identifiera en användare i flera domäner, som bara gäller för innehavare där integreringen åsidosätter ITP-begränsningar.</td>
    <td>1 år</td>
    <td>Ja</td>
    <td>Nej</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Tredje part, domain=.<a href="https://business.adobe.com/se/products/marketo/bizible.html">bizible.com</a></td>
    <td>Universellt användar-ID för att identifiera en användare i flera domäner.</td>
    <td>1 år</td>
    <td>Ja</td>
    <td>Nej</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Tredje part, domain=.<a href="https://bizibly.com/">bizible.com</a></td>
    <td>Mappning mellan Marketo Measure cookie-ID på klientens domän och dess Doubleclick-cookie-ID.</td>
    <td>1 år</td>
    <td>Ja</td>
    <td>Nej</td>
    <td>Edgecast</td>
  </tr>
</tbody>
</table>

Om en brandväggsvarning för webbprogram (WAF) utlöses under JavaScript-konfigurationen kan användare antingen inaktivera den WAF-regeln eller tillåtslista cookies, som i följande exempel:

![Exempel på en WAF-varning som ber om att tillåtslista Marketo Measure-cookies](assets/marketo-measure-cookies-1.png)
