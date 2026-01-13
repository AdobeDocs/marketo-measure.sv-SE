---
description: Generering och mappning av kontaktpunkter - [!DNL Marketo Measure]
title: Generering och mappning av kontaktpunkter
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
feature: Touchpoints
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Generering och mappning av kontaktpunkter {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] attribueringsartiklar har två processer:

* Skapa kontaktytor, som skapar kontaktytor som representerar en persons interaktioner med marknadsförings- och säljsatsningar
* Kontaktpunktsmappning, som ger poäng till rätt kanal och underkanal

För att du ska få ut så mycket som möjligt av [!DNL Marketo Measure] bör du samarbeta med din [!DNL Marketo Measure]-representant för att anpassa båda processerna efter organisationens behov.

Genereringsmetoder för kontaktpunkter

Processen för generering av kontaktytor besvarar frågan&quot;Hur kommer [!DNL Marketo Measure] att veta att detta har inträffat?&quot; Beroende på vilken funktionsuppsättning du har och vilka typer av interaktioner dina presumtiva kunder kan ha, finns det upp till tre sätt [!DNL Marketo Measure] kan använda för att hämta en interaktion och skapa en kontaktyta som representerar den.

>[!IMPORTANT]
>[!DNL Marketo Measure] genererar bara en kontaktpunkt per session. Om fler än ett formulär har fyllts i hämtas endast den första formulärfyllningen.

| Typ av samverkan | Exempel | Genereringsmetod för kontaktpunkt |
| ---|---|--- |
| Online, på dina webbplatser | Formulärfyllning | [!DNL Marketo Measure] JavaScript |
| Offline; online finns inte på dina webbplatser | Varumärkesföretag; Content Syndication Partner levererar en lista över leads som har interagerat med ditt innehåll | CRM-kampanjmedlemskapet synkroniserat med [!DNL Marketo Measure], antingen genom att ställa in Campaign-synkroniseringstypen direkt i kampanjen eller genom att ställa in regler på kampanjsidan i [!DNL Marketo Measure] |
| Försäljningsaktivitet | Utgående samtal av SDR | CRM-aktivitetsposten (aktivitet eller händelse) synkroniserad till [!DNL Marketo Measure], via logik på sidan [!UICONTROL Activities] i [!DNL Marketo Measure] |

Mappningsmetoder för kontaktpunkter

Kontaktpunktsmappningsprocessen besvarar frågan:&quot;När den här kontaktytan har skapats, hur vet [!DNL Marketo Measure] vilken kanal och underkanal den tillhör?&quot; Varje metod för generering av kontaktpunkter har en egen metod för att mappa kontaktytor.

| Typ av samverkan | Genereringsmetod | Mappningsmetod |
| ---|---|--- |
| Online, på dina webbplatser | [!DNL Marketo Measure] JavaScript | Genom sidan [!DNL Online Channels] i [!DNL Marketo Measure] kan du referera till UTM-värden, landningssida och refererande sidinformation |
| Offline; online, inte på dina webbplatser | Synkronisering av CRM-kampanjmedlemskap | Genom att referera till Campaign-typen via sidan [!UICONTROL Offline Channels] i [!DNL Marketo Measure] |
| Försäljningsaktivitet | Synkronisering av CRM-aktivitet | Genom sidan [!UICONTROL Online Channels] i [!DNL Marketo Measure] kan du referera till det kampanjnamn som tilldelats på sidan [!UICONTROL Activities] |

>[!MORELIKETHIS]
> [Mappar onlinekontaktytor till [!DNL Marketo Measure] Kanaler/underkanaler](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
> [Synkroniserar CRM-kampanjer inifrån SFDC](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
> [Synkroniserar CRM-kampanjer inifrån  [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
> [Mappar CRM-kampanjer till [!DNL Marketo Measure] Kanaler/underkanaler](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
> [Skapar kontaktytor från försäljningsaktiviteter](/help/advanced-features/activities-attribution/salesforce-activities-attribution.md)
> [Vanliga frågor om aktiviteter och Mappningsaktiviteter Touchpoints till kanaler/underkanaler](/help/advanced-features/activities-attribution/activities-attribution-faq.md)

