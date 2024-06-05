---
description: Aktuell versionsinformation - [!DNL Marketo Measure]
title: Aktuell versionsinformation
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 97a82ae0649ae5b1349d025a7a7cf433bc64bc7e
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Versionsinformation: 2024 {#release-notes-2024}

Nedan finns alla nya och uppdaterade funktioner för 2024-utgåvorna.

## Q3-version {#q3-release}

<p>

**Påminnelse: Borttagningar av Salesforce-fält - 14 juni**

Som vi meddelade förra året kommer vi att fasa ut våra exportjobb till Lead/Contact-objekt för att förenkla vår integrering och eliminera behovet av att exportera till Salesforce-standardobjekt. Du kan hämta samma data från dina Touchpoint-objekt genom att följa stegen [dokumenteras här](/help/release-notes/previous-releases/2023.md#deprecations){target="_blank"}. Vi delar också dokumentation om hur du skapar arbetsflöden för att lägga till dessa data i lead-/kontaktobjektet. Utbyggnaden kommer att träda i kraft den 14 juni 2024.

Den här förändringen ger två viktiga fördelar:

* **Minskade kostnader för Salesforce API**: Kunderna kan förvänta sig att minska sina kostnader för Salesforce API med ca 10 %.
* **Smidig integrering**: Det högsta antalet fel i våra exportjobb är relaterat till dessa processer. Om du tar bort dem kommer integreringen att effektiviseras avsevärt.

**Kontrollpanel för attributerade affärsmöjligheter**

Vi är glada över att kunna presentera nya [Kontrollpanel för attributerade affärsmöjligheter](/help/marketo-measure-discover-ui/dashboards/attributed-opportunity-dashboard.md){target="_blank"}, som är utformad för att ge er en heltäckande bild av hur era marknadsföringssatsningar bidrar till både nya och mogna försäljningsmöjligheter. Med den här kontrollpanelen kan du ta reda på detaljerna för alla öppna och stängda affärsmöjligheter som kan hänföras till era strategier, med flexibiliteten att filtrera efter affärsmöjlighetens stadium. Här får ni insikter om vilka kanaler, underkanaler eller kampanjer som rangordnas högst när det gäller tilldelat affärsmöjlighetsbelopp och visar det totala tilldelade affärsmöjlighetsbeloppet tillsammans med antalet tilldelade öppna och stängda affärsmöjligheter.

**Marketo Engage cookie Sync för Marketo Measure Ultimate**

Marketo Engage Cookie Sync finns nu för Marketo Measure Ultimate. Så här använder du funktionen:

1. På sidan AEP-scheman redigerar du B2B-personschemat och lägger till fältgruppen &quot;Marketo Engage personinformation&quot;.
1. När du importerar data till MMU mappar du fältet Kakips-ID från fältgruppen till fältet Kakor från Marketo Engage.

**Boomerang Stages aktiverat för Tier 2-kunder**

Funktionen Boomerang Stage är tidigare bara tillgänglig för Tier 3-kunder och är också tillgänglig för alla Tier 2-kunder från och med den 13 juni 2024. Mer information om den här funktionen finns i dokumentationen nedan.

* [Boomerang Stages och Touchpoints](/help/advanced-marketo-measure-features/boomerang/boomerang-stages-and-touchpoints.md){target="_blank"}
* [Konfigurera Boomerang Stages](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md){target="_blank"}
* [Scenarier i Boomerang](/help/advanced-marketo-measure-features/boomerang/boomerang-stage-scenarios.md){target="_blank"}

<p>

## Q2-release {#q2-release}

<p>

**Borttagning av Marketo Measure-funktioner som svar på cookie-utfasning från tredje part**

Som ett svar på allt större integritetsproblem fasas cookies från tredje part ut, med Google Chrome sista-datum 3 2024 som signalerar att de upphör. Marketo Measure tar bort vissa funktioner som är beroende av cookies från tredje part, särskilt Cross-Domain Tracking och View-through Attribution, som är beroende av Google/DoubleClick-cookie. Den här ändringen påverkar inte andra Marketo Measure-funktioner eller användningen av cookies från första part. Efter Google tidslinje förväntas dessa funktioner bli inaktuella den 1 juni, men data som samlats in före detta datum är fortfarande tillgängliga för kunderna.

* [Anpassa till cookie-borttagning från tredje part i Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Marketo Measure Cookies](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

**Avfasad utrullning av vår förbättrade felhantering**

Vi introducerar en stegvis utrullning av förbättrad felhantering för exportjobb. Vi börjar med att omedelbart skicka meddelanden i appen om behörighetsfel och övergår till en ny metod där exportjobb pausas vid felpunkten. Ändringen syftar till att förbättra dataintegriteten och synligheten, vilket ger våra användare smidigare och mer tillförlitliga datahanteringsprocesser. För att säkerställa en smidig övergång och minimala störningar i verksamheten genomför vi dessa ändringar i två faser:

* Omedelbar tillgänglighet för Pulse-meddelanden: Du får pulsmeddelanden i appen om behörighetsfel under exportjobb. Detta kommer inte att avbryta exporten, men det kommer att hjälpa dig att få reda på felen utan att det påverkar dina nuvarande jobb.
* Implementering av jobbpausning den 25 april: **POSTPONED** - Efter att ha övervägt synpunkter från Marketo Measure-användare har vi beslutat att skjuta upp implementeringen av pausade exportjobb vid felpunkten, som ursprungligen var schemalagd till 25 april. Vi inser att det kanske inte är den mest effektiva metoden att stoppa jobb. Vi strävar efter att hitta en bättre lösning som bibehåller dataintegriteten och minimerar störningar. Vi kommer att vänta med att göra ändringar i vårt nuvarande system tills vi kan säkerställa en lösning som bättre motsvarar användarnas behov.

_Varför det här spelar någon roll_

Förbättrad dataintegritet och framtidskorrektur för din integrering: Vi avbryter jobbet vid första tecken på problem för att förhindra dataförlust och säkerställa precision. Detta gör att det går snabbt att lösa problem, vilket förbättrar dataexportens kvalitet och systemens tillförlitlighet.

Omedelbar synlighet: Införandet av pulsmeddelanden gör det möjligt att snabbt reagera på behörighetsfel och förhindra potentiella konsekvenser för verksamheten.

_Stöd för övergången_

För att hjälpa dig att anpassa dig till denna förändring [vi har skapat dokumentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} med tydliga felbeskrivningar och omfattande felsökningssteg.

<br>

**Åtgärd krävs för LinkedIn-integrering**

LinkedIn har nyligen släppt en uppdaterad version av sin Lead Sync API. Please reauthenticate the LinkedIn connection in your Marketo Measure instance by May 20 to avoid any störtions.

