---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookies - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Cookies"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Marketo Measure Cookies {#marketo-measure-cookies}

Läs om de olika [!DNL Marketo Measure] Cookies som läses in på din plats när du använder [!DNL Marketo Measure] JavaScript till landningssidorna. Den här informationen kan vara användbar för webbutvecklingsteamet under implementeringen.

>[!IMPORTANT]
>
>På grund av integritetsproblem är cookies från tredje part på väg ut. Google Chrome presenterade ett utkast till tredje kvartalet 2024 om borttagning av cookies från tredje part som effektivt markerar slutet på den här typen av spårning. Därför kommer Adobe att ta bort Marketo Measure-funktioner som är beroende av cookies från tredje part, närmare bestämt Cross-Domain Tracking och View-through Attribution, som använder Google/DoubleClick-cookie. Inga andra funktioner i Marketo Measure påverkas. Användning av cookies från första part påverkas inte heller. Mot bakgrund av Google tidsplan är det förväntade borttagningsdatumet för de två funktionerna ovan 6/1/2024. Relaterade data som samlats in före detta datum kommer även fortsättningsvis att vara tillgängliga för Adobe-kunder.

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
