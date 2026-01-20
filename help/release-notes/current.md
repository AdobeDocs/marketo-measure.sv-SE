---
description: Aktuell versionsinformation - [!DNL Marketo Measure]
title: Aktuell versionsinformation
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---

# Versionsinformation: 2024 {#release-notes-2024}

Nedan finns alla nya och uppdaterade funktioner för 2024-utgåvorna.

## Q4 Release {#q4-release}

### Nytt beteende för överföring av sessionskanal

Kanalen från föregående session kommer nu att fortsätta om en ny session börjar inom sju dagar efter 30 minuters inaktivitet, vilket endast gäller för direktbesök (ingen hänvisare eller interna referenter). Efter sju dagars inaktivitet blir sessionen som standard Direkt/Annat. Kanaler som inte är direktkanaler åsidosätts inte av tidigare sessionsdata.

Dessutom sammanfogas sessioner med social inloggning (Google, Microsoft eller Apple) till en sammanhängande session, vilket ger en smidigare upplevelse. Utan denna övergång kan sociala inloggningar skapa separata sessioner på grund av skillnader mellan externa referenter.

För nya kunder är överföring av sessionskanal nu standardbeteendet. Befintliga kunder kan aktivera detta genom att aktivera Sessionskanalöverföringar under Inställningar > All touch Attribution. Den här inställningen kan inte ångras när den har aktiverats.

Dokumentation: [Definition av Marketo Measure webbsessioner](https://experienceleague.adobe.com/en/docs/marketo-measure/using/marketo-measure-tracking/setting-up-tracking/definition-of-marketo-measure-web-sessions){target="_blank"}

### Kontrollpanel för nyckelordens ROI

Den nya Dashboard-panelen för nyckelordsavkastning ger detaljerade insikter om resultatet för betalda sökkampanjer och ger en heltäckande bild av kostnader på nyckelordsnivå, tillskrivna intäkter samt de leads och möjligheter som genereras. Den här kontrollpanelen hjälper dig att utvärdera avkastningen på varje nyckelord för Google Adwords, LinkedIn, Bing Ads osv.

Dokumentation: [Instrumentpanel för nyckelordsavkastning](https://experienceleague.adobe.com/en/docs/marketo-measure/using/marketo-measure-discover-ui/dashboards/keyword-roi-dashboard){target="_blank"}

### Förbättrade segmentregler

Nu kan du skapa segment med hjälp av fälten Campaign och Campaign Member, förutom Touchpoint och Kontakt. Den här förbättringen gör att ni kan analysera och sprida era data mer effektivt i Discover.

![Förbättrade segmentregler](assets/mm-q4-release-1.png)

### Uppdatering: Felhanteringsinställning för CRM-export

Vi har lyssnat på din feedback om hur du stoppar jobben och vi introducerar en ny funktion i användargränssnittet. Från och med idag kan du välja om exportjobb ska pausa när fel uppstår. Använd den nya växlingsknappen i **Mitt konto** > **Inställningar** > **CRM** > **Allmänt**. Den här växeln är aktiverad som standard för att förbättra dataintegriteten och synligheten. Om du inte vill använda den här funktionen kan du stänga av den i användargränssnittet, så återupptas exportjobben. Uppdateringen är utformad för att öka tillförlitligheten i datahanteringsprocesserna samtidigt som du får större kontroll.

#### Nyckeldatum och utfasning

1. **Omedelbar växlingstillgänglighet:** Växlingsknappen finns nu i användargränssnittet och är aktiverad som standard för att förhindra att data hoppas över under exportjobb. Om du föredrar att exportjobben fortsätter att köras trots att fel påträffas, inaktiverar du växlingsknappen.

1. **Aktivering av jobbpausning den 1 oktober:** Med början 1 oktober 2024 pausas jobbet för att säkerställa att inga data går förlorade om växlingen är aktiv och ett fel på postnivå påträffas under ett exportjobb. Felen beror vanligtvis på att behörigheter saknas, att anpassade valideringsregler har tillämpats felaktigt eller att arbetsflöden/utlösare inte fungerar som de ska. Du får meddelanden om problemet, och när det har korrigerats återupptas exportjobbet från den punkt där det avbröts. Om du väljer att avbryta jobbpausningen får du fortfarande meddelanden om problem, och när de har korrigerats återexporteras de poster som hoppats över automatiskt.

#### Varför det här spelar någon roll

* **Förbättrad dataintegritet och framtidssäkra din integrering:** Genom att pausa jobbet vid det första tecknet i ett problem kan vi förhindra dataförlust och säkerställa att allt är korrekt. Detta möjliggör snabb fellösning, vilket ger bättre dataexportkvalitet och total systemtillförlitlighet.

* **Omedelbar synlighet:** Med pulsmeddelanden får du aviseringar om behörighetsfel så att du kan få snabba svar och minimera potentiella konsekvenser för dina åtgärder.

#### Stöd för övergången

För att hjälpa dig att anpassa dig till den här ändringen har vi skapat dokumentation om den nya funktionen och tydliga felbeskrivningar med omfattande felsökningssteg.

* Ny dokumentation: [Felhanteringsinställning för CRM-export](/help/configuration-and-setup/marketo-measure-and-salesforce/crm-error-handling.md)
* [Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md)

## Q3-version {#q3-release}

<p>

### Påminnelse: Borttagna fält i Salesforce - 14 juni

Som vi meddelade förra året kommer vi att [fasa ut våra exportjobb till lead-/kontaktobjekt](https://nation.marketo.com/t5/employee-blogs/marketo-measure-salesforce-lead-and-contact-field-deprecation-06/ba-p/350179){target="_blank"} för att förenkla vår integrering och eliminera behovet av att exportera till Salesforce standardobjekt. Du kan hämta samma data från dina Touchpoint-objekt genom att följa stegen [som beskrivs här](/help/release-notes/previous-releases/2023.md#deprecations){target="_blank"}. Vi delar också dokumentation om hur du skapar arbetsflöden för att lägga till dessa data i lead-/kontaktobjektet. Utbyggnaden kommer att träda i kraft den 14 juni 2024.

Den här förändringen ger två viktiga fördelar:

* **Minskade Salesforce API-kostnader**: Kunderna kan förvänta sig att minska sina Salesforce API-kostnader med ca 10 %.
* **Smidig integrering**: Det högsta antalet fel i våra exportjobb är relaterat till dessa processer. Om du tar bort dem kommer integreringen att effektiviseras avsevärt.

### Kontrollpanel för attributerade affärsmöjligheter

Vi är glada över att kunna presentera den nya [attributerade säljprojektsinstrumentpanelen](/help/marketo-measure-discover-ui/dashboards/attributed-opportunity-dashboard.md){target="_blank"}, som ger dig en heltäckande bild av hur dina marknadsföringssatsningar bidrar till både nya och mogna försäljningsmöjligheter. Med den här kontrollpanelen kan du ta reda på detaljerna för alla öppna och stängda affärsmöjligheter som kan hänföras till era strategier, med flexibiliteten att filtrera efter affärsmöjlighetens stadium. Här får ni insikter om vilka kanaler, underkanaler eller kampanjer som rangordnas högst när det gäller tilldelat affärsmöjlighetsbelopp och visar det totala tilldelade affärsmöjlighetsbeloppet tillsammans med antalet tilldelade öppna och stängda affärsmöjligheter.

### Marketo Engage Cookie-synkronisering för Marketo Measure Ultimate

Marketo Engage Cookie Sync finns nu för Marketo Measure Ultimate. Så här använder du funktionen:

1. På sidan AEP Schemas redigerar du B2B-personschemat och lägger till fältgruppen &quot;Marketo Engage personinformation&quot;.
1. När du importerar data till MMU mappar du fältet Kakips-ID från fältgruppen till fältet Kakor från Marketo Engage.

### Boomerang Stages aktiverat för Tier 2-kunder

Funktionen Boomerang Stage är tidigare bara tillgänglig för Tier 3-kunder och är också tillgänglig för alla Tier 2-kunder från och med den 13 juni 2024. Mer information om den här funktionen finns i dokumentationen nedan.

* [Boomerang-scener och kontaktpunkter](/help/advanced-marketo-measure-features/boomerang/boomerang-stages-and-touchpoints.md){target="_blank"}
* [Konfigurerar bokmärken](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md){target="_blank"}
* [Scenarier i Boomerang](/help/advanced-marketo-measure-features/boomerang/boomerang-stage-scenarios.md){target="_blank"}

<p>

## Q2-release {#q2-release}

<p>

### Borttagning av Marketo Measure-funktioner som svar på cookie-utfasning från tredje part

Som svar på allt större integritetsproblem fasas cookies från tredje part ut, med Google Chrome 3 2024 som sista ansökningsdatum. Marketo Measure tar bort vissa funktioner som är beroende av cookies från tredje part, särskilt Cross-Domain Tracking och View-through Attribution, som är beroende av Google/DoubleClick-cookie. Den här ändringen påverkar inte andra Marketo Measure-funktioner eller användningen av cookies från första part. Efter Google tidslinje förväntas dessa funktioner bli inaktuella den 1 juni, men data som samlats in före detta datum är fortfarande tillgängliga för kunderna.

* [Anpassa till cookie-borttagning från tredje part i Marketo Measure](https://nation.marketo.com/t5/employee-blogs/adapting-to-third-party-cookie-deprecation-in-marketo-measure/ba-p/345110){target="_blank"}
* [Marketo Measure Cookies](/help/marketo-measure-tracking/setting-up-tracking/marketo-measure-cookies.md){target="_blank"}

### Avfasad utrullning av vår förbättrade felhantering

Vi introducerar en stegvis utrullning av förbättrad felhantering för exportjobb. Vi börjar med att omedelbart skicka meddelanden i appen om behörighetsfel och övergår till en ny metod där exportjobb pausas vid felpunkten. Ändringen syftar till att förbättra dataintegriteten och synligheten, vilket ger våra användare smidigare och mer tillförlitliga datahanteringsprocesser. För att säkerställa en smidig övergång och minimala störningar i verksamheten genomför vi dessa ändringar i två faser:

* Omedelbar tillgänglighet för Pulse-meddelanden: Du får pulsmeddelanden i appen om behörighetsfel under exportjobb. Detta kommer inte att avbryta exporten, men det kommer att hjälpa dig att få reda på felen utan att det påverkar dina nuvarande jobb.
* Implementering av jobbpausning den 25 april: **POSTPONED** - Efter att ha övervägt synpunkter från Marketo Measure-användare har vi beslutat att skjuta upp implementeringen av pausade exportjobb vid den tidpunkt då felet uppstod, ursprungligen planerat till den 25 april. Vi inser att det kanske inte är den mest effektiva metoden att stoppa jobb. Vi strävar efter att hitta en bättre lösning som bibehåller dataintegriteten och minimerar störningar. Vi kommer att vänta med att göra ändringar i vårt nuvarande system tills vi kan säkerställa en lösning som bättre motsvarar användarnas behov.

_Varför det här spelar någon roll_

Förbättrad dataintegritet och framtidskorrektur för din integrering: Vi avbryter jobbet vid första tecken på problem för att förhindra dataförlust och säkerställa precision. Detta gör att det går snabbt att lösa problem, vilket förbättrar dataexportens kvalitet och systemens tillförlitlighet.

Omedelbar synlighet: Införandet av pulsmeddelanden gör det möjligt att snabbt reagera på behörighetsfel och förhindra potentiella konsekvenser för verksamheten.

_Stöd för övergången_

[Vi har skapat dokumentation](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"} med tydliga felbeskrivningar och omfattande felsökningssteg som hjälper dig att anpassa dig till den här ändringen.

<br>

### Åtgärd krävs för LinkedIn-integrering

LinkedIn har nyligen släppt en uppdaterad version av sin Lead Sync API. Please reauthenticate the LinkedIn connection in your Marketo Measure instance by May 20 to avoid any ruptions.
