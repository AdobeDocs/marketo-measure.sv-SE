---
description: Data som samlas in av JavaScript-vägledning för Marketo Measure-användare
title: Data som samlats in av JavaScript
feature: Tracking
exl-id: 83814168-9d3e-45ac-b514-df58f0b2e90b
hidefromtoc: true
source-git-commit: 0299ef68139df574bd1571a749baf1380a84319b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Data som samlats in av JavaScript {#data-collected-by-javascript}

Läs mer om de data som samlas in av Marketo Measure JavaScript vid driftsättningen.

**Exempelbegäran:**

```text
https://cdn.bizible.com/m/ipv?_biz_r=https%3A%2F%2Fwww.google.com%2F&_biz_h=-1801745101&_biz_u=7059e81415f34f7bbaf40fe32fdcba21&_biz_s=8cbeed&_biz_l=https%3A%2F%2Fwww.zendesk.com%2Fservice%2F&_biz_t=1676483822155&_biz_i=Customer%20service%20software%20for%20the%20best%20customer%20experiences%20%7C%20Zendesk&_biz_n=0&rnd=235938&cdn_o=a&_biz_z=1676483822155
```

<br>

Marketo Measure samlar in följande gemensamma data för alla typer av förfrågningar:

| Ursprung | Namn | Datatyp | Syfte |
| --- | --- | --- | --- |
| Huvud för begäran | IP-adress | string | Användarens plats härleds via GeoIP-sökning. Dessa data är temporära och lagras inte permanent. |
| Huvud för begäran | Användaragentsträng | string | Avgör vilken enhet användaren använder. |
| Frågeparameter | `_biz_u` | string | Bizible cookie ID. |
| Frågeparameter | `_biz_l` | string | Aktuell sidadress. |
| Frågeparameter | `_biz_t` | long | Tidsstämpel för aktivitet. |
| Frågeparameter | `_biz_i` | string | Aktuell sidtitel. |

Förutom de gemensamma data som anges ovan lägger bizible.js även till ytterligare data beroende på vilka typer av begäran som anges nedan:

| Typ av begäran | Sökväg för begäran | Ytterligare frågeparameter | Datatyp | Syfte |
| --- | --- | --- | --- | --- |
| Sidvy | `/ipv` | `_biz_r` | string | URL för referenssida. |
|  |  | `_biz_h` | string | Hash-kodade klientens skärmupplösning. |
|  |  | `_biz_c` | string | Valfri parameter. Om den här parametern finns indikerar det att klientorganisationen konfigurerar `bizible.js` att vänta på användarens samtycke innan den spårar och att `bizible.js` har fått användarens samtycke att spåras. |
| Skicka formulär | `/frm` | `eMail` | string | E-postadress för oformaterad text. |
| Mappning av användar-ID | `/u` | `mapType` | enum | Vilken typ av användar-ID-mappning `bizible.js` har identifierats (Marketo Munchkin ID och Adobe ECID) |
|  |  | `mapValue` | string | Det faktiska värdet för cookie-ID från tredje part för integreringen ovan. |

>[!NOTE]
>
>Bizible är Marketo Measure tidigare namn.
