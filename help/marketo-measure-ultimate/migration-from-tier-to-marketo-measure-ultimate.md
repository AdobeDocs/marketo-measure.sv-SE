---
description: Lär dig mer om migreringsprocessen när du går från  [!DNL Marketo Measure] nivåindelad prenumeration till [!DNL Marketo Measure] Ultimate.
title: Migrering från nivå till [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
source-git-commit: 9c3c3c75a9a505bb078da18e13f210add8699c24
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Migrering från nivå 1-2 till [!DNL Marketo Measure] Ultimate {#migration-from-tier-to-marketo-measure-ultimate}

I den här artikeln beskrivs migreringsprocessen för användare som går från Tier 1- eller Tier 2-prenumerationen till [!DNL Marketo Measure] Ultimate.

>[!IMPORTANT]
>
>Kom ihåg att behålla din befintliga Tier-instans tills migreringen är klar.

## Datainsamling {#data-collection}

### Webbtrafikdata {#web-traffic-data}

* Inga ändringar krävs för JavaScript-distribution.

* Aktivera domäner i den nya Ultimate-instansen.

* Skicka vid behov en biljett för att migrera och bearbeta tidigare webbdata.

* Ad-integreringar förblir oförändrade, men kom ihåg att återkoppla dem i Ultimate. Innan du gör det måste du koppla från dina annonskonton i Tier tenant.

>[!NOTE]
>
>Historiska annonskostnadsdata importeras inte. Vi importerar bara annonsinformation som flyttas framåt när annonskontona har återkopplats.

### Enterprise Data Connection {#enterprise-data-connection}

Implementera om alla källdataanslutningar i AEP, inklusive CRM- och Marketo Engage-anslutningar.

## Dataomvandling {#data-transformation}

* Account-Based Marketing-funktioner, bland annat lead-to-account-matchning och prediktiva engagemangsmoment, finns inte i Ultimate.

   * Du kan dock importera dina lead-to-account-matchningsresultat via AEP och använda dem inom plattformen.

* I Ultimate kan man härleda övergångar för tidigare CRM-scener i stället för att läsa direkt, eftersom det inte finns någon direkt CRM-anslutning.

   * Vi läser affärsmöjlighetsposter och tidsstämplar och ser det aktuella stadiet, och härleder sedan de historiska faserna.

## Rapportering {#reporting}

* Ultimate skickar inte tillbaka data till CRM.

   * Om data ska skickas tillbaka till CRM krävs en anpassad ETL-pipeline för att extrahera data från Marketo Measure Snowflake till CRM. Du måste skapa en anpassad datamodell i CRM.

* Alla Discover-paneler är desamma som i Tiered-lösningen, med tillägg av Attribution AI.
