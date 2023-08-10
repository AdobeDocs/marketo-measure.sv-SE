---
unique-page-id: 18874590
description: "[!DNL Marketo Measure] Cookies - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Cookies"
exl-id: de6e35ae-af92-43ba-8416-3e07d3dd470c
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Marketo Measure Cookies {#marketo-measure-cookies}

Läs om de olika [!DNL Marketo Measure] Cookies som läses in på din plats när du använder [!DNL Marketo Measure] JavaScript till landningssidorna. Den här informationen kan vara användbar för webbutvecklingsteamet under implementeringen.

| **Kaknamn** | **Cookie-typ** | **Syfte** |
|---|---|---|
| _BUID | Tredje part, sparad på .bizible.com | Universellt användar-ID för att identifiera samma användare över flera klientdomäner. |
| _biz_uid | Förste part | Användar-ID på den aktuella domänen. |
| _biz_sid | Förste part | Användarens sessions-ID. |
| _biz_flagsA | Förste part | En enda cookie som lagrar flera uppgifter, t.ex. om användaren har skickat ett formulär, utfört en migrering mellan domäner, skickat en vy via pixel, avanmält sig från spårning osv. |
| _biz_nA | Förste part | Sekvensnummer som [!DNL Marketo Measure] omfattar för alla förfrågningar, för internt diagnostiksyfte |
| _biz_dfsA | Förste part | Lagrar formuläröverföringsdata tillfälligt som sker tidigare [!DNL bizible.js] tar emot en konfigurations-JS för att avgöra om spårningsformulär på HTTPS är aktiverat eller inte. |
| _biz_pendingA | Förste part | lagrar analysdata som inte har skickats till [!DNL Marketo Measure] ännu. |

Om en varning om Web Application Firewall (WAF) utlöses under JavaScript-konfigurationen kan användarna antingen inaktivera den WAF-regeln eller tillåta att listan över cookies visas, som i följande exempel:

![](assets/marketo-measure-cookies-1.png)
