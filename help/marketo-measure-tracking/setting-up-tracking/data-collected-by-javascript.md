---
description: Data som samlats in med JavaScript - [!DNL Marketo Measure]
title: Data som samlats in med JavaScript
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Data som samlats in med JavaScript {#data-collected-by-javascript}

Lär dig mer om de data som samlas in av Marketo Measure JavaScript vid distributionen.

**Exempelbegäran:**

```
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure samlar in följande gemensamma data för alla typer av förfrågningar:

<table>
<thead>
  <tr>
    <th>Ursprung</th>
    <th>Namn</th>
    <th>Datatyp</th>
    <th>Syfte</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Huvud för begäran</td>
    <td>IP-adress</td>
    <td>string</td>
    <td>Användarens plats härleds via GeoIP-sökning. Dessa data är temporära och lagras inte permanent.</td>
  </tr>
  <tr>
    <td>Huvud för begäran</td>
    <td>Användaragentsträng</td>
    <td>string</td>
    <td>Avgör vilken enhet användaren använder.</td>
  </tr>
  <tr>
    <td>Frågeparameter</td>
    <td>_biz_u</td>
    <td>string</td>
    <td>Bizible cookie ID.</td>
  </tr>
  <tr>
    <td>Frågeparameter</td>
    <td>_biz_l</td>
    <td>string</td>
    <td>Aktuell sidadress.</td>
  </tr>
  <tr>
    <td>Frågeparameter</td>
    <td>_biz_t</td>
    <td>long</td>
    <td>Tidsstämpel för aktivitet.</td>
  </tr>
  <tr>
    <td>Frågeparameter</td>
    <td>_biz_i</td>
    <td>string</td>
    <td>Aktuell sidtitel.</td>
  </tr>
</tbody>
</table>

Förutom de gemensamma data som anges ovan lägger bizible.js även till ytterligare data beroende på vilka typer av begäran som anges nedan:

<table>
<thead>
  <tr>
    <th>Typ av begäran</th>
    <th>Sökväg för begäran</th>
    <th>Ytterligare frågeparameter</th>
    <th>Datatyp</th>
    <th>Syfte</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Sidvy</td>
    <td>/ipv</td>
    <td>_biz_r</td>
    <td>string</td>
    <td>URL för referenssida.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_h</td>
    <td>string</td>
    <td>Hash-kodade klientens skärmupplösning.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>_biz_c</td>
    <td>string</td>
    <td>Valfri parameter. Om den här parametern finns indikerar det att tenant konfigurerar bizible.js att vänta på användarens samtycke innan han/hon spårar, och att bizible.js har fått användarens samtycke till att spåras.</td>
  </tr>
  <tr>
    <td>Skicka formulär</td>
    <td>/form</td>
    <td>eMail</td>
    <td>string</td>
    <td>E-postadress för oformaterad text.</td>
  </tr>
  <tr>
    <td>Mappning av användar-ID</td>
    <td>/u</td>
    <td>mapType</td>
    <td>enum</td>
    <td>Vilken typ av användar-ID-mappning bizible.js har identifierats (Marketo Munchkin id och Adobe ECID)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>mapValue</td>
    <td>string</td>
    <td>Det faktiska värdet för cookie-ID från tredje part för integreringen ovan.</td>
  </tr>
</tbody>
</table>

>[!NOTE]
>
>Bizible är Marketo Measure tidigare namn.
