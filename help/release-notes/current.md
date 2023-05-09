---
description: Aktuell versionsinformation - [!DNL Marketo Measure] - Produktdokumentation
title: Aktuell versionsinformation
source-git-commit: 8e8ddd80d69102455fa678a32f31a9fe8319822c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Versionsinformation: 2023 {#release-notes-2023}

Här nedan hittar du alla nya och uppdaterade funktioner för 2023-utgåvorna.

## Q2-release {#q2-release}

<p>

**Salesforce-paketkonsolidering**

* Vi sammanfogar alla Salesforce-paket till ett enda, heltäckande paket för en förbättrad användarupplevelse och förenklad användning. Paketen V1, V2_EXT och Reporting dras tillbaka nästa kvartal. Det nya paketet innehåller alla tidigare funktioner, vilket ger effektivare spårning och djupare kundinsikter.
* Kunder som redan har installerat V2-paketet måste uppdatera det till den nya konsoliderade versionen.
* Vi har lagt till två nya fält för att förbättra dina rapporteringsfunktioner:
   * form_name: Detta fält är nu tillgängligt i BT/BAT-objekt och gör det möjligt för användare att skapa rapporter baserade på formulärnamn.
   * user_touchpoint_id: I det här fältet kan användare skapa rapporter med unika kontaktpunkter.
* [Den här artikeln](/help/configuration-and-setup/marketo-measure-and-salesforce/salesforce-package-consolidation.md){target="_blank"} innehåller guider om hur du återskapar rapporter och instrumentpaneler från äldre rapportpaket.

**Versionsuppdateringar för Salesforce API**

* Alla Salesforce API-versioner av Apex-klasser, inklusive klassen UserActivityContext, uppdateras till de versioner som stöds. (31.0 till 57.0)

**Installation av nytt paket**

* Länk till installation av nytt konsoliderat paket [finns här](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1P000000VY6Z){target="_blank"}

### Vad kommer? {#whats-coming}

<p>

**Ändringar i IP-adresslagring**

* Vi kommer inte längre att lagra IP-adresser i vårt system utifrån sekretesshänsyn. Vi kommer att fortsätta att identifiera och lagra IP-adressens geografiska placering, men formatet kommer att ändras (t.ex. &quot;USA&quot; till &quot;USA&quot;).
