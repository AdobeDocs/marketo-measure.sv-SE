---
description: Aktuell versionsinformation - [!DNL Marketo Measure] - Produktdokumentation
title: Aktuell versionsinformation
exl-id: e93ff03e-ea21-41f4-abb8-32313ee74c0c
feature: Release Notes
source-git-commit: 2e474dfbda67b53dbf643defa383fc1b4c5f0b42
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 0%

---

# Versionsinformation: 2023 {#release-notes-2023}

Här nedan hittar du alla nya och uppdaterade funktioner för 2023-utgåvorna.

## Q4 Release {#q4-release}

<p>

**Kontrollpanel för webbtrafik**

Den nydesignade [Kontrollpanel för webbtrafik](/help/marketo-measure-discover-ui/dashboards/web-traffic-dashboard.md){target="_blank"} är nu tillgängligt för alla kunder. Den här instrumentpanelen ger en fullständig översikt över besökarnas interaktioner på webbplatsen. Du kan analysera mätvärden som unika besökarantal per URL, övergripande besök, sidvisningar och formulärinskickningar från specifika formulär-URL:er eller landningssidor. Ni kan också hålla reda på trafiktrender varje månad och identifiera högpresterande betalda medier, som hjälper er att förfina era strategier för optimala intäkter.

Den nya uppsättningen färdiga kontrollpaneler planeras att lanseras i vågor som avslutas före årets slut.

>[!NOTE]
>
>Även om de aktuella instrumentpanelerna kommer att vara borttagna i mars 2024 kan du använda båda versionerna fram till dess, vilket ger en smidig övergång.

**Ta bort IP-adressdata**

Vi håller på att ta bort IP-adressdata från vår långtidslagring för att säkerställa att våra data följer gällande sekretess. För närvarande innehåller följande Snowflake-tabeller och vyer IP-adresser, och vi planerar att ta bort dessa data och lägga till ny geolokaliseringsinformation:

<table style="width:400px">
<thead>
  <tr>
    <th style="width:50%">Tabeller</th>
    <th>Vyer</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>CUSTOMER_AB_TESTS</td>
    <td>BIZ_CUSTOMER_AB_TESTS</td>
  </tr>
  <tr>
    <td>CUSTOMER_EVENTS</td>
    <td>BIZ_CUSTOMER_EVENTS</td>
  </tr>
  <tr>
    <td>FORM_SUBMITS</td>
    <td>BIZ_FORM_SUBMITS</td>
  </tr>
  <tr>
    <td>IMPRESSIONER</td>
    <td>BIZ_IMPRESSIONS</td>
  </tr>
  <tr>
    <td>PAGE_VIEWS</td>
    <td>BIZ_PAGE_VIEWS</td>
  </tr>
  <tr>
    <td>SESSIONER</td>
    <td>BIZ_SESSIONS</td>
  </tr>
  <tr>
    <td>WEB_HOST_MAPPINGS</td>
    <td>BIZ_WEB_HOST_MAPPINGS</td>
  </tr>
</tbody>
</table>

* Från och med nu hämtar vi landskod, stadsnamn och regionkod i stället för landsnamn, stadsnamn och regionnamn.
* Under behandlingen av alla tidigare webbaktiviteter kan det uppstå inkonsekvenser i positionsinformation mellan poster. Dessa inkonsekvenser kan vara förekomsten av IP-adresser utan detaljer om geopositionering, uppdaterad geopositioneringsinformation utan IP-adresser eller en blandning av namn och koder för länder eller regioner.
* _**Denna period med blandade uppgifter förväntas äga rum från 01/04/2023 till 02/29/2023.**_

**Data för sidtitel i URL-tabell**

URL-tabellen i [informationslager](/help/marketo-measure-data-warehouse/data-warehouse-schema.md){target="_blank"} kommer nu att innehålla ett sidtitelfält förutom webbdatatabeller.

Observera att sidrubriken i URL-tabellen kanske inte alltid matchar sidtiteln i andra webbtabeller. URL-tabellen kommer att ha den senaste sidrubriken. Om titeln har ändrats för URL:en efter att webbaktiviteten ägde rum, matchar den inte vad som finns i URL-tabellen.

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
>Även om de aktuella instrumentpanelerna kommer att vara borttagna i mars 2024 kan du använda båda versionerna fram till dess, vilket ger en smidig övergång.

### Undertryckningar {#deprecations}

<p>

#### Borttagningar av Salesforce-fält {#salesforce-field-deprecations}

Vi kommer att fasa ut våra exportjobb till Lead/Contact-objekt för att förenkla vår integrering och eliminera behovet av att exportera standardobjekt till Salesforce. De normaliserade fälten som anges nedan kommer också att bli inaktuella, eftersom kunderna kan hämta samma data från sina Touchpoint-objekt. _**Tidslinjen för borttagning är juni 2024.**_

<table style="width:350px">
<tbody>
  <tr>
    <td>bizible2_Ad_Campaign_Name_FT__c</td>
  </tr>
  <tr>
    <td>bizible2_Ad_Campaign_Name_LC__c</td>
  </tr>
  <tr>
    <td>bizible2_Landing_Page_FT__c</td>
  </tr>
  <tr>
    <td>bizible2_Landing_Page_LC__c</td>
  </tr>
  <tr>
    <td>bizible2_Touchpoint_Date_FT__c</td>
  </tr>
  <tr>
    <td>bizible2_Touchpoint_Date_LC__c</td>
  </tr>
  <tr>
    <td>bizible2_Touchpoint_Source_FT__c</td>
  </tr>
  <tr>
    <td>bizible2_Touchpoint_Source_LC__c</td>
  </tr>
  <tr>
    <td>bizible2_Marketing_Channel_FT__c</td>
  </tr>
  <tr>
    <td>bizible2_Marketing_Channel_LC__c</td>
  </tr>
</tbody>
</table>

De fält som innehåller samma information om Touchpoint- och Attribution Touchpoint-objekt är:

* bizible2_Ad_Campaign_Name__c
* bizible2_Landing_Page__c
* bizible2_Marketing_Channel__c
* bizible2_Touchpoint_Date__c
* bizible2_Touchpoint_Source_c

**Nödvändiga åtgärder**

* Skapa nya rapporttyper för leads och kontakter med eller utan kontaktpunkter.

![](assets/release-notes-2023-1.png)

* Skapa rapporter som fångar funktionaliteten i befintliga rapporter som använder de borttagna fälten. Som en del av den här processen vill du ändra fälten i rapporten enligt vad som anges nedan:

   * Ta bort fält för lead/kontakt-FT/LC:

![](assets/release-notes-2023-2.png)

* Lägg till Touchpoint-fält:

![](assets/release-notes-2023-3.png)

* Pekpunktsplaceringsfiltret och eventuella filter som använder FT/LC-fälten, inklusive datumfältet, ska uppdateras enligt följande:

![](assets/release-notes-2023-4.png)

![](assets/release-notes-2023-5.png)

* Ta bort alla befintliga rapporter som använde de borttagna fälten från lead-/kontaktobjektet för att inte längre referera till dessa fält.

<p>

* **Dynamics-paket relaterat**

   * Installera vår senaste paketversion, v6.12, om du vill vara ansluten till Dynamics. Gamla versioner `(<v6.12)` stöds inte längre. Den här uppdateringen optimerar postgenerering för historik för att minska lagringsanvändningen.

   * Den inaktuella metoden för OAuth med en RefreshToken kommer att bli inaktuell. Se [den här guiden](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md){target="_blank"} för att uppdatera dina autentiseringsuppgifter så att de följer Microsoft bästa praxis när det gäller att använda ClientSecret.

* **&quot;custom_properties&quot;-fält**

I vårt datalager har fältet&quot;custom_properties&quot; använts som lagring för ytterligare datapunkter som inte omfattas av vårt fasta schema. Det här fältets användning är begränsad och det kan vara komplicerat att integrera det med SQL-frågor, vilket påverkar prestandan. Detta lagras i JSON-format. Med tanke på dessa faktorer har vi beslutat att ta bort det här fältet. Den här ändringen påverkar i huvudsak databehandlingslagret i Azure-tabellagringen och de data som exporteras till vårt datalager.

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
