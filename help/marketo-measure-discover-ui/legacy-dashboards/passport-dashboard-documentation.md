---
unique-page-id: 42762628
description: Dokumentation för Passport Dashboard - [!DNL Marketo Measure]
title: Dokumentation för Passport Dashboard
exl-id: 43cb01a8-d02e-4086-af57-d7ec9275f87a
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Dokumentation för Passport Dashboard {#passport-dashboard-documentation}

Via Passport-kontrollpanelen kan marknadsförare visa leads/kontakter och säljprojekt som har gått igenom varje pipeline-fas under en viss tidsram.

Den här instrumentpanelen har två paneler:

* Affärsmöjligheter: Antalet säljprojektsposter som passerat genom varje fas under den angivna tidsramen.
* Leads/kontakter: Antalet lead- eller kontaktposter som passerat genom varje fas under den angivna tidsramen.

>[!NOTE]
>
>På alla Discover-paneler kan bara ett personobjekt, antingen lead eller kontakt, rapporteras. Detta anges i [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Den här instrumentpanelen har stöd för följande filter (alla filter gäller båda plattorna):

* Datum: markera tidsramen.
* Kanal: filtrera posterna efter kanaler. En post kopplas till en kanal om någon av dess kontaktytor är kopplad till kanalen.
* Delkanal: filtrera posterna efter delkanaler. En post kopplas till en underkanal om någon av dess kontaktytor är kopplad till underkanalen.
* Campaign: filtrera posterna efter kampanjer. En post associeras med en kampanj om någon av dess kontaktytor är associerad med kampanjen.
* Kampanjkälla: filtrera posterna efter kampanjkällor. Exempel på kampanjkällor är Adwords, BingAds, Facebook, LinkedIn etc. En post kopplas till en kampanjkälla om någon av dess kontaktytor är kopplad till kampanjkällan.
* CRM-kontonamn: filtrera posterna efter CRM-kontonamn.
* Segmentfilter: filtrera posterna efter anpassade segment. En post kopplas till ett segment om någon av dess kontaktytor är kopplad till segmentet.

För alla filter används&quot;AND&quot;-logik.

>[!NOTE]
>
>Om en post ändrar fas på det valda datumet räknas posten för från- och till-stadierna och alla genomströmningsfaser.

## Möjligheter {#opportunities}

![](assets/one-1.png)

Stegen innehåller OC, valda trattfaser i öppna säljprojektsstadier ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]), och Won Opportunity Stages ([!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL Stage Mapping]).

>[!NOTE]
>
>För Won-faser är antalet poster bara för poster som överförs till scenen under den valda tidsramen.

Du kan gå ned på detaljnivå från varje fält för att visa säljprojektsposterna för varje fas.

## Leads/kontakter {#leads-contacts}

![](assets/two-1.png)

Stegen är FT, LC, valda trattfaser i Öppna lead-/kontaktsteg i Inställningar - CRM - Stage Mapping och Konverterade lead-/kontaktsteg i Inställningar - CRM - Stage Mapping.

>[!NOTE]
>
>För konverterade faser är antalet poster bara för poster som överförs till scenen under den valda tidsramen.

Du kan gå ned i varje fält för att visa lead-/kontaktposterna för varje fas.
