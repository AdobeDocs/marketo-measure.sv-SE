---
description: Definition av  [!DNL Marketo Measure] webbsessioner - [!DNL Marketo Measure]
title: Definition av  [!DNL Marketo Measure] webbsessioner
exl-id: ddf4f19d-2024-413a-b0ae-4efd468c24de
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# Definition av [!DNL Marketo Measure] webbsessioner {#definition-of-marketo-measure-web-sessions}

Lär dig hur [!DNL Marketo Measure] definierar webbsessioner.

En **webbsession** refererar till en persons interaktioner med din webbplats under en viss tid. Sessionen börjar när en användare kommer till din webbplats.

Haley besöker till exempel adobe.com. Hennes besök på webbplatsen påbörjar en session. När Haley lämnar webbplatsen, genom att stänga fliken/webbläsaren eller navigera bort från webbplatsen, avslutas sessionen.

En användare kan inte öppna flera sessioner samtidigt. Om Haley öppnar [!DNL adobe.com] på tio separata flikar har bara en session skapats i samband med hennes besök på webbplatsen.

## Hur definierar [!DNL Marketo Measure] en ny session? {#how-does-marketo-measure-define-a-new-session}

Det finns några saker som avgör när en session avslutas och när en ny session börjar. De två huvudsakliga sätten som [!DNL Marketo Measure]-sessioner kan avsluta är:

* **Tidsbaserat förfallodatum**
* **Kanalbaserat förfallodatum**

## Tidsbaserad förfallotid {#time-based-expiration}

### Äldre beteende {#legacy-behavior}

**Hur länge varar en session?**

[!UICONTROL Marketo Measure] sessioner avslutas efter 30 minuters inaktivitet på webbplatsen. Exempel:

När Haley besöker adobe.com påbörjas en session. Hon utforskar webbplatsen i några minuter och tar sedan några steg bort från datorn, men lämnar webbplatsen öppen. Efter 30 minuters inaktivitet avslutas sessionen.

För närvarande behandlar [!UICONTROL Marketo Measure] bara sidnavigering och formuläröverföringar som aktivitet. Att bläddra genom webbsidan eller hovra över ett element på sidan anses inte vara en aktivitet. Så om Haley besöker adobe.com för att läsa ett blogginlägg, och det tar en timme att läsa, avslutas hennes webbsession efter 30 minuter även om hon bläddrar igenom innehållet på sidan.

### Nytt beteende {#new-behavior}

För nya användare är detta standardbeteendet.

Befintliga användare kan använda det nya beteendet genom att aktivera växlingen under **Inställningar** > **All touch Attribution** > **Sessionskanalöverföring**. Den här inställningen kan inte ångras när den har aktiverats.

När en ny session skapas efter 30 minuters inaktivitet överförs den föregående sessionens kanal om den nya sessionen börjar inom sju dagar. Överföringen gäller endast för direktbesök (varken referenter eller interna referenter). Om inaktiviteten överstiger sju dagar används kanalen för den nya sessionen som standard för Direkt/Annan. Om Haley till exempel besöker landingpage.com från Google, är inaktiv i över 30 minuter och återkommer inom sju dagar, behåller den nya sessionen Google-kanalen. Om samma användare däremot ändrar sidan genom en annan kanal åsidosätts inte den andra kanalen av den tidigare Google-kanalen.

Endast kanalen överförs, exklusive kampanj- eller referensinformation. Detta beror på att kanalklassificeringen hanteras av Marketo Measure, medan andra datapunkter samlas in separat.

**Inloggning via sociala medier**

När en besökare använder social inloggning via Google, Microsoft eller Apple sammanfogas sessionen till en kontinuerlig session. Om en besökare till exempel får plats på en sida från LinkedIn, slutför en social Google-inloggning och når en tacksida, räknas allt som en enda session. Om inte överföringskanalen för sessionskanalen aktiveras skulle social inloggning skapa separata sessioner på grund av den externa referenten.

## Kanalbaserad förfallotid {#channel-based-expiration}

[!DNL Marketo Measure] påbörjar en ny session varje gång en användare kommer till din webbplats från en annan digital marknadsföringskanal eller en extern webbplats. Detta inkluderar:

* En webbplats för hänskjutande
* Sociala kanaler ([!DNL Facebook], [!DNL LinkedIn] och så vidare)
* Betalade eller organiska sökkanaler ([!DNL Google/Bing])

**Referera till webbplatser och sociala kanaler**

När en besökare kommer till webbplatsen från en hänvisande webbplats eller en social kanal börjar en ny session.

Säg att Haley är på LinkedIn, klickar på ett [!DNL Marketo Measure]-inlägg och omdirigeras till Adobe webbplats. När Haley sedan bläddrar igenom [!DNL Facebook] ser han ett annat [!DNL Marketo Measure]-inlägg. När hon klickar på det här inlägget och omdirigeras till Adobe-webbplatsen avslutas den första webbsessionen som är relaterad till [!DNL LinkedIn] och en ny session som är relaterad till [!DNL Facebook] påbörjas.

**Betalda eller organiska sökkanaler**

Nya sessioner börjar när som helst när en användare kommer till din webbplats via betalda eller organiska sökkanaler. Om Haley kommer till Adobe webbplats genom organisk sökning och sedan omedelbart besöker er webbplats via en betald annons på Google, skapas två separata sessioner.

**Web Direct-trafik**

Om en besökare kommer till din webbplats genom att skriva webbplatsens URL i adressfältet leder det inte alltid till att en ny session börjar.

Om Haleys första webbsession börjar som ett resultat av ett besök från en hänvisningswebbplats, en social kanal eller en betald/organisk sökkanal och sedan besöker webbplatsen via webben direkt, skulle det inte leda till att en ny session inleds.

_Om Haleys första webbsession kommer från Web Direct och sedan besöker webbplatsen via_ en extern/hänvisad webbplats _, avslutas den första sessionen och en ny session öppnas som är relaterad till den externa/hänvisande webbplatsen._

## Google Analytics Sessions {#google-analytics-sessions}

Det finns vissa likheter med hur [!DNL Marketo Measure] och Google Analytics definierar sessioner. Mer information om hur Google Analytics definierar sessioner finns på: [https://support.google.com/analytics/answer/2731565?hl=en](https://support.google.com/analytics/answer/2731565?hl=en){target="_blank"}
