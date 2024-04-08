---
description: Aktuell versionsinformation - [!DNL Marketo Measure]
title: Aktuell versionsinformation
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: db71cbfaf7deb5b724ac4babc38e835c04fadac7
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Versionsinformation: 2024 {#release-notes-2024}

Nedan finns alla nya och uppdaterade funktioner för 2024-utgåvorna.

## Q2-release {#q2-release}

<p>

**Borttagning av Marketo Measure-funktioner som svar på cookie-utfasning från tredje part**

Som ett svar på allt större integritetsproblem fasas cookies från tredje part ut, med Google Chrome sista-datum 3 2024 som signalerar att de upphör. Marketo Measure tar bort vissa funktioner som är beroende av cookies från tredje part, särskilt Cross-Domain Tracking och View-through Attribution, som är beroende av Google/DoubleClick-cookie. Den här ändringen påverkar inte andra Marketo Measure-funktioner eller användningen av cookies från första part. Efter Google tidslinje förväntas dessa funktioner bli inaktuella den 1 juni, men data som samlats in före detta datum är fortfarande tillgängliga för kunderna.

* [Anpassa till cookie-borttagning från tredje part i Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Marketo Measure Cookies](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Avfasad utrullning av vår förbättrade felhantering**

Vi introducerar en stegvis utrullning av förbättrad felhantering för exportjobb, med inledande av omedelbara pulsmeddelanden i appen för tillståndsfel och övergång den 25 april till en ny metod där exportjobb pausas vid felpunkten. Ändringen syftar till att förbättra dataintegriteten och synligheten, vilket ger våra användare smidigare och mer tillförlitliga datahanteringsprocesser. För att säkerställa en smidig övergång och minimala störningar i verksamheten genomför vi dessa ändringar i två faser:

* Omedelbar tillgänglighet för Pulse-meddelanden: Du får pulsmeddelanden i appen om behörighetsfel under exportjobb. Detta kommer inte att avbryta exporten, men det kommer att hjälpa dig att få reda på felen utan att det påverkar dina nuvarande jobb.
* Implementering av jobbpausning den 25 april: Från och med den 25 april pausas jobbet om ett behörighetsfel uppstår under ett exportjobb. På så sätt kan inga data hoppas över. Du får ett meddelande om eventuella problem, och när behörigheterna har korrigerats återupptas exportjobbet utan problem där det slutade.

_Varför det här spelar någon roll_

Förbättrad dataintegritet och framtidskorrektur för din integrering: Vi avbryter jobbet vid första tecken på problem för att förhindra dataförlust och säkerställa precision. Detta gör att det går snabbt att lösa problem, vilket förbättrar dataexportens kvalitet och systemens tillförlitlighet.

Omedelbar synlighet: Införandet av pulsmeddelanden gör det möjligt att snabbt reagera på behörighetsfel och förhindra potentiella konsekvenser för verksamheten.

_Stöd för övergången_

För att hjälpa dig att anpassa dig till denna förändring [vi har skapat dokumentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} med tydliga felbeskrivningar och omfattande felsökningssteg.

<br>
**Åtgärd krävs för LinkedIn-integrering**

LinkedIn har nyligen släppt en uppdaterad version av sin Lead Sync API. Please reauthenticate the LinkedIn connection in your Marketo Measure instance by May 20 to avoid any störtions.

