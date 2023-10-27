---
description: Aktuell versionsinformation - [!DNL Marketo Measure] - Produktdokumentation
title: Aktuell versionsinformation
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: dc4fda07004398207fb5067eb42ecd9e8ffe8624
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Versionsinformation: 2023 {#release-notes-2023}

Här nedan hittar du alla nya och uppdaterade funktioner för 2023-utgåvorna.

## Q4 Release {#q4-release}

<p>

**Upptäck omdesignen av instrumentpanelen**

Alla Marketo Measure-användare kommer att uppleva våra omdesignade instrumentpaneler i appen som kombinerar förbättrad användbarhet med mervärde. Vi introducerar också nya mätvärden, som&quot;Realiserad avkastning på investering&quot;, som tar hänsyn till den typiska fördröjningen mellan marknadsföringsinvesteringar och inköp på B2B-marknader.

Den nya uppsättningen förbyggda kontrollpaneler planeras att lanseras i vågor, med början den första veckan i oktober och som avslutas före årets slut. Dessa nya instrumentpaneler visas automatiskt i dina instanser, tillsammans med produktinformation och länkar till dokumentation.

* [Ny guide för Discover Dashboard](/help/marketo-measure-discover-ui/dashboards/new-discover-dashboard-guide.md){target="_blank"}
* [Grunderna i kontrollpanelen](/help/marketo-measure-discover-ui/dashboards/discover-dashboard-basics.md){target="_blank"}
* [Instrumentpanel för intäktsöversikt](/help/marketo-measure-discover-ui/dashboards/revenue-overview-dashboard.md){target="_blank"}
* [Kontrollpanel för attributerade intäkter](/help/marketo-measure-discover-ui/dashboards/attributed-revenue-dashboard.md){target="_blank"}
* [Kontrollpanel för avkastning](/help/marketo-measure-discover-ui/dashboards/roi-dashboard.md){target="_blank"}
* [Passport Dashboard](/help/marketo-measure-discover-ui/dashboards/passport-dashboard.md){target="_blank"}

>[!NOTE]
>
>De aktuella instrumentpanelerna kommer att vara borttagna i mitten av januari 2024, men du kan använda båda versionerna fram till dess, vilket ger en smidig övergång.

### Undertryckningar {#deprecations}

<p>

* **&quot;custom_properties&quot;-fält**

I vårt datalager har fältet&quot;custom_properties&quot; använts som lagring för ytterligare datapunkter som inte omfattas av vårt fasta schema. Det här fältets användning är begränsad och det kan vara komplicerat att integrera det med SQL-frågor, vilket påverkar prestandan. Detta lagras i JSON-format. Med tanke på dessa faktorer har vi beslutat att ta bort det här fältet. Den här ändringen påverkar i huvudsak databehandlingslagret i Azure-tabellagringen och de data som exporteras till vårt datalager.

* **Dynamics-paket relaterat**

   * Installera vår senaste paketversion, v6.12, om du vill vara ansluten till Dynamics. Gamla versioner `(<v6.12)` stöds inte längre. Den här uppdateringen optimerar postgenerering för historik för att minska lagringsanvändningen.

   * Den inaktuella metoden för OAuth med en RefreshToken kommer att bli inaktuell. Se [den här guiden](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} för att uppdatera dina autentiseringsuppgifter så att de följer Microsoft bästa praxis när det gäller att använda ClientSecret.

### Vad kommer? {#q4-whats-coming}

<p>

**Anpassad rapportering i appen**

Marketo Measure-kunder kommer för första gången att kunna skapa och spara sina egna rapporter direkt i appen. Detta kommer att följa på releasen av de förbyggda kontrollpanelerna i början av 2024.

<br>

## Q2-release {#q2-release}

<p>

* **Salesforce-paketkonsolidering**

Vi sammanfogar alla Salesforce-paket till ett enda, heltäckande paket för en förbättrad användarupplevelse och förenklad användning. Paketen V1, V2_EXT och Reporting dras tillbaka nästa kvartal. Det nya paketet innehåller alla tidigare funktioner, vilket ger effektivare spårning och djupare kundinsikter.

Kunder som redan har installerat V2-paketet måste uppdatera det till den nya konsoliderade versionen.

Vi har lagt till två nya fält för att förbättra dina rapporteringsfunktioner:

* form_name: Detta fält är nu tillgängligt i BT/BAT-objekt och gör att användare kan skapa rapporter baserade på formulärnamn.
* user_touchpoint_id: Det här fältet gör att användare kan skapa rapporter med unika användarkontaktytor.

[Den här artikeln](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} innehåller guider om hur du återskapar rapporter och instrumentpaneler från äldre rapportpaket.

* **Versionsuppdateringar för Salesforce API**

Alla Salesforce API-versioner av Apex-klasser, inklusive klassen UserActivityContext, uppdateras till de versioner som stöds. (31.0 till 57.0)

* **Installation av nytt paket**

Länk till installation av nytt konsoliderat paket [finns här](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Vad kommer? {#q2-whats-coming}

<p>

**Ändringar i IP-adresslagring**

Vi kommer inte längre att lagra IP-adresser i vårt system utifrån sekretesshänsyn. Vi kommer att fortsätta att identifiera och lagra IP-adressens geografiska placering, men formatet kommer att ändras (t.ex. &quot;USA&quot; till &quot;USA&quot;).
