---
description: Bästa praxis för [!DNL Marketo Measure] CRM-paket - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa praxis för [!DNL Marketo Measure] CRM-paket
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
source-git-commit: 00268f49ff6e5dfc105fa7ea21837375eae49647
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Bästa praxis för [!DNL Marketo Measure] CRM-paket {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

## Översikt {#overview}

[!DNL Marketo Measure] integreras med båda [!DNL Salesforce] och [!DNL Microsoft Dynamics]fokuserar det här dokumentet på [!DNL Marketo Measure] bästa praxis för CRM-paket som utformats för [!DNL Salesforce].

Under implementeringen skulle följande paket ha installerats i din [!DNL Salesforce] -instans.

Baspaket: Detta är vårt baspaket som innehåller våra anpassade objekt och fält. Vi rekommenderar att du installerar i Production för alla användare.
Tilläggspaket för instrumentpanel: Det här är vårt tilläggspaket för Dashboard, som innehåller tre färdiga instrumentpaneler. Vi rekommenderar att du installerar i Production för alla användare. Detta är valfritt, men vi uppmuntrar kunderna att installera.

Dessa paket aktiverar [!DNL Marketo Measure] -användare enkelt få tillgång till kontaktpunktsdata genom hela [!DNL Salesforce] -instans. Att bekräfta att du har konfigurerat dessa paket korrekt är avgörande för att verifiera att sidlayouter, behörighetsgrupper, rapporter och instrumentpaneler visas för din [!DNL Marketo Measure] som förväntat.

## Bästa praxis {#best-practice}

När det gäller implementering och hantering av [!DNL Marketo Measure] [!DNL Salesforce] Tänk på följande när du paketerar:

* Bekräfta att alla nödvändiga teammedlemmar har tillgång till [!DNL Marketo Measure] rapportmappar. Det ska vara 1-3 [!DNL Marketo Measure] mappar (förklaras nedan). För att kunna öppna åtkomst måste den person som installerade paketen dela rapportmapparna med rätt användare eller roller.
   * **Kontaktpunktsrapporter för köpare** - tillgängliga för alla
   * **[!DNL Marketo Measure]Kontobaserade marknadsföringsrapporter** - Rapporterna fylls endast i för kunder i nivå 2 och högre
   * **Instrumentpaneler för Buyer Touchpoint** - tillgänglig för alla, även om det här paketet är valfritt.

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Under den inledande implementeringen av CRM-paketet bör du granska konfigurationen av CRM-paketet en gång om året. Granskningen bekräftar att alla sidlayouter är korrekt konfigurerade och att alla relevanta gruppmedlemmar har tillgång till [!DNL Marketo Measure] rapporter och kontrollpaneler.

Andra orsaker till det kan utlösa en granskning...

* Nya teammedlemmar läggs till
* Uppdateringar till dig [!DNL Salesforce] sidlayout
* Migrering för [!DNL Salesforce] Klassisk till ljusare
* Uppgradera till [!DNL Marketo Measure] kontrakt
* Kontrollera att du har den senaste versionen av Buyer Touchpoints Package installerad i [!DNL Salesforce]

>[!NOTE]
>
>När du inaktiverar Marketo Measure export av data till Salesforce tas inga befintliga data bort. Följ stegen i [den här Salesforce-hjälpartikeln](https://help.salesforce.com/s/articleView?id=sf.c360_a_delete_data_stream_records.htm&amp;type=5){target="_blank"}.

>[!MORELIKETHIS]
>
>* [Uppdatera Buyer TouchPoint-paket](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md)
>* [[!DNL Marketo Measure] Behörighetsuppsättningar](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md)
>* [Dela rapporter och instrumentpanelsmapp](https://help.salesforce.com/articleView?id=analytics_share_folder.htm&amp;type=0)
>* [Anslut Marketo Measure till Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/connect-marketo-measure-to-salesforce.md)

