---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Cookies"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 69304dddf3569cd92c95a50e9a2e346acdad0f43
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Marketo Measure Cookies {#marketo-measure-cookies}

Läs om de olika [!DNL Marketo Measure] Cookies som läses in på din plats när du använder [!DNL Marketo Measure] JavaScript till landningssidorna. Den här informationen kan vara användbar för webbutvecklingsteamet under implementeringen.

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
    <td>Tredje part, domain=.<a href="http://bizible.com/">bizible.com</a></td>
    <td>Universellt användar-ID för att identifiera en användare i flera domäner.</td>
    <td>1 år</td>
    <td>Ja</td>
    <td>Nej</td>
    <td>Edgecast</td>
  </tr>
  <tr>
    <td>_BUID</td>
    <td>Tredje part, domain=.<a href="http://bizibly.com/">bizibly.com</a></td>
    <td>Mappning mellan Marketo Measure cookie-ID på klientens domän och dess Doubleclick-cookie-ID.</td>
    <td>1 år</td>
    <td>Ja</td>
    <td>Nej</td>
    <td>Edgecast</td>
  </tr>
</tbody>
</table>

Om en varning om Web Application Firewall (WAF) utlöses under JavaScript-konfigurationen kan användarna antingen inaktivera den WAF-regeln eller tillåta att listan över cookies visas, som i följande exempel:

![](assets/marketo-measure-cookies-1.png)
