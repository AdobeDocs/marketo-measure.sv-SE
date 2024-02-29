---
unique-page-id: 18874564
description: Definition av [!DNL Marketo Measure] Webbsessioner - [!DNL Marketo Measure]
title: Definition av [!DNL Marketo Measure] Webbsessioner
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Definition av [!DNL Marketo Measure] Webbsessioner {#definition-of-marketo-measure-web-sessions}

Lär dig mer [!DNL Marketo Measure] definierar webbsessioner.

A **webbsession** avser en persons interaktioner med din webbplats under en viss tid. Sessionen börjar när en användare kommer till din webbplats.

Haley besöker till exempel adobe.com. Hennes besök på webbplatsen påbörjar en session. När Haley lämnar webbplatsen, genom att stänga fliken/webbläsaren eller navigera bort från webbplatsen, avslutas sessionen.

En användare kan inte öppna flera sessioner samtidigt. Om Haley öppnas [!DNL adobe.com] på 10 olika flikar har endast en session skapats i samband med hennes besök på webbplatsen.

## Hur [!DNL Marketo Measure] Vill du definiera en ny session? {#how-does-marketo-measure-define-a-new-session}

Det finns några saker som avgör när en session avslutas och när en ny session börjar. De två huvudsakliga sätten [!DNL Marketo Measure] sessionerna kan avslutas med:

* **Tidsbaserat förfallodatum**
* **Kanalbaserat förfallodatum**

## Tidsbaserad förfallotid {#time-based-expiration}

**Hur länge varar en session?**

[!DNL Marketo Measure] -sessionerna avslutas efter 30 minuters inaktivitet på webbplatsen. Exempel:

När Haley besöker adobe.com påbörjas en session. Hon utforskar webbplatsen i några minuter och tar sedan några steg bort från datorn, men lämnar webbplatsen öppen. Efter 30 minuters inaktivitet avslutas sessionen.

För närvarande [!DNL Marketo Measure] hanterar bara sidnavigering och formulärinskickning som aktivitet. Att bläddra genom webbsidan eller hovra över ett element på sidan anses inte vara en aktivitet. Så om Haley besöker adobe.com för att läsa ett blogginlägg, och det tar en timme att läsa, avslutas hennes webbsession efter 30 minuter även om hon bläddrar igenom innehållet på sidan.

## Kanalbaserad förfallotid {#channel-based-expiration}

[!DNL Marketo Measure] börjar en ny session när en användare kommer till din webbplats från en annan digital marknadsföringskanal eller en extern webbplats. Detta omfattar följande:

* En webbplats för hänskjutande
* Sociala kanaler ([!DNL Facebook], [!DNL LinkedIn], osv.)
* Betalda eller organiska sökkanaler ([!DNL Google/Bing])

**Hänvisa till webbplatser och sociala kanaler**

Varje gång en besökare kommer till din webbplats från en hänvisande webbplats eller en social kanal börjar en ny session.

Säg att Haley är på LinkedIn, klicka på en [!DNL Marketo Measure] posta och omdirigeras till Adobe webbplats. När du sedan bläddrar igenom [!DNL Facebook], ser Haley en annan [!DNL Marketo Measure] publicera. När hon klickar på det här inlägget och omdirigeras till webbplatsen Adobe, orsakar detta den första webbsessionen som är relaterad till [!DNL LinkedIn] till slut och en ny session som är relaterad till [!DNL Facebook] börjar.

**Betalda eller organiska sökkanaler**

Nya sessioner börjar när en användare kommer till webbplatsen via betalda eller organiska sökkanaler. Om Haley kommer till Adobe webbplats genom organisk sökning och sedan omedelbart besöker er webbplats via en betald annons på Google, kommer två separata sessioner att skapas.

**Web Direct-trafik**

Om en besökare kommer till din webbplats genom att skriva webbplatsens URL i adressfältet leder det inte alltid till att en ny session börjar.

Om Haleys första webbsession börjar som ett resultat av ett besök från en hänvisningswebbplats, en social kanal eller en betald/organisk sökkanal och sedan besöker webbplatsen via webben direkt, skulle det inte leda till att en ny session inleds.

_Men_, om Haleys första webbsession kom från Web Direct och sedan besöker hon webbplatsen via _en extern/hänvisande webbplats_, avslutas den första sessionen och en ny session öppnas som är relaterad till den externa platsen/hänvisningswebbplatsen.

## Google Analytics sessioner {#google-analytics-sessions}

Det finns vissa likheter med hur [!DNL Marketo Measure] och Google Analytics definierar sessioner. Mer information om hur Google Analytics definierar sessioner finns på: [https://support.google.com/analytics/answer/2731565?hl=en](http://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
