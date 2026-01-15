---
description: Bästa praxis för  [!DNL Marketo Measure] CRM-paketvägledning för Marketo Measure-användare
title: Bästa praxis för  [!DNL Marketo Measure] CRM-paket
exl-id: 97ce0ff3-8aa5-4789-9ee0-25d68c001def
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Bästa praxis för CRM-paket [!DNL Marketo Measure] {#best-practices-for-marketo-measure-crm-package}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Den uppdateras och omprofileringen kommer snart att återspeglas i CRM.

## Översikt {#overview}

[!DNL Marketo Measure] integreras med både [!DNL Salesforce] och [!DNL Microsoft Dynamics], det här dokumentet fokuserar på de [!DNL Marketo Measure] bästa metoderna för CRM-paketen som är utformade för [!DNL Salesforce].

Under implementeringen skulle de två följande paketen ha installerats i din [!DNL Salesforce]-instans.

Baspaket: Detta är baspaketet som innehåller anpassade objekt och fält. Vi rekommenderar att alla användare installerar i Production.
Dashboard Extension Package: Detta är vårt Dashboard Extension Package, som innehåller tre fördefinierade instrumentpaneler. Vi rekommenderar att alla användare installerar i Production. Detta är valfritt, men vi uppmuntrar kunderna att installera.

Med de här paketen kan dina [!DNL Marketo Measure]-användare enkelt komma åt kontaktpunktsdata genom sin [!DNL Salesforce]-instans. Att bekräfta att du har konfigurerat dessa paket korrekt är avgörande för att verifiera att sidlayouter, behörighetsgrupper, rapporter och instrumentpaneler visas för dina [!DNL Marketo Measure]-användare som förväntat.

## Bästa praxis {#best-practice}

När du implementerar och hanterar ditt [!DNL Marketo Measure] [!DNL Salesforce]-paket bör du tänka på följande bästa praxis.

* Bekräfta att alla nödvändiga teammedlemmar har åtkomst till rapportmapparna [!DNL Marketo Measure]. Det ska finnas 1-3 [!DNL Marketo Measure] mappar (dessa beskrivs nedan). Den som installerade paketen måste dela rapportmapparna med rätt användare eller roller för att kunna öppna åtkomsten.
   * **Buyer Touchpoint-rapporter** - tillgängliga för alla
   * **[!DNL Marketo Measure]kontobaserade marknadsföringsrapporter** - rapporter fylls bara i för kunder nivå 2 och senare
   * **Buyer Touchpoint Dashboards** - tillgänglig för alla, även om det här paketet är valfritt.

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Även om konfigurationen av ditt CRM-paket täcks under den initiala implementeringen rekommenderar vi att du granskar konfigurationen av ditt CRM-paket en gång per år. Den här granskningen bekräftar att alla sidlayouter har konfigurerats korrekt och att alla lämpliga gruppmedlemmar har tillgång till [!DNL Marketo Measure] rapporter och instrumentpaneler.

Andra orsaker till det kan utlösa en granskning...

* Nya teammedlemmar läggs till
* Uppdateringar av dina [!DNL Salesforce]-sidlayouter
* Migrering för [!DNL Salesforce] Classic till Lightning
* Uppgraderingar av ditt [!DNL Marketo Measure]-kontrakt
* Kontrollera att du har den senaste versionen av Buyer Touchpoints Package installerad i [!DNL Salesforce]

>[!NOTE]
>När du inaktiverar Marketo Measure export av data till Salesforce tas inga befintliga data bort. Följ stegen i [den här Salesforce-hjälpartikeln](https://help.salesforce.com/s/articleView?language=en_US&id=sf.c360_a_delete_data_stream_records.htm&type=5){target="_blank"} för att ta bort den.

>[!MORELIKETHIS]
> [Uppdatera Buyer Touchpoint-paket](/help/configuration-and-setup/install-set-up.md)
> [[!DNL Marketo Measure] Behörighetsuppsättningar](/help/configuration-and-setup/marketo-measure-permission-sets.md)
> [Dela rapporter och instrumentpanelsmapp ](https://help.salesforce.com/s/articleView?language=en_US&id=analytics_share_folder.htm&type=0)
> [Anslut Marketo Measure till Salesforce](/help/configuration-and-setup/connect-marketo-measure-to-salesforce.md)
