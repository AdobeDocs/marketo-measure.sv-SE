---
unique-page-id: 18874554
description: Generering och mappning av pekpunkter - [!DNL Marketo Measure] - Produktdokumentation
title: Generering och mappning av kontaktpunkter
exl-id: bb4988f5-4fbc-43b7-9544-da541b8e1d32
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Generering och mappning av kontaktpunkter {#touchpoint-generation-and-mapping}

[!DNL Marketo Measure] attribueringsberättelser hänger på två processer:

* Skapa kontaktytor, som skapar kontaktytor som representerar en persons interaktioner med marknadsförings- och säljsatsningar
* Kontaktpunktsmappning, som ger poäng till rätt kanal och underkanal

För att du ska få ut så mycket som möjligt av [!DNL Marketo Measure]bör du arbeta med [!DNL Marketo Measure] anpassa båda processerna efter organisationens behov.

Genereringsmetoder för kontaktpunkter

Processen för att skapa kontaktytor besvarar frågan&quot;Hur är [!DNL Marketo Measure] kommer du att veta att det här hände?&quot; Beroende på vilka funktioner du har och vilka typer av interaktioner dina presumtiva kunder kan ha, finns det upp till tre sätt [!DNL Marketo Measure] kan fortsätta med en interaktion och skapa en kontaktyta som representerar den.

| **Typ av interaktion** | **Exempel** | **Genereringsmetod för kontaktpunkt** |
|---|---|---|
| Online, på din/dina webbplatser | Formulärfyllning | [!DNL Marketo Measure] JavaScript |
| Offline; Online finns inte på din/dina webbplatser | Handelsprogram Partner för innehållssyndikering tillhandahåller en lista över leads som har interagerat med ditt innehåll | CRM Campaign-medlemskap synkroniserat med [!DNL Marketo Measure], antingen genom att ställa in Campaign-synkroniseringstypen direkt i kampanjen eller genom att ställa in regler på kampanjsidan i [!DNL Marketo Measure] |
| Försäljningsaktivitet | Utgående samtal av SDR | CRM-aktivitetspost (Aktivitet eller Händelse) synkroniserad till [!DNL Marketo Measure], via logik i [!UICONTROL Activities] sida in [!DNL Marketo Measure] |

Mappningsmetoder för kontaktpunkter

Processen för att mappa kontaktytor besvarar frågan:&quot;När den här kontaktytan har skapats, hur [!DNL Marketo Measure] kommer du att veta vilken kanal och underkanal den tillhör?&quot; Varje metod för generering av kontaktpunkter har en egen metod för att mappa kontaktytor.

| **Typ av interaktion** | **Genereringsmetod** | **Mappningsmetod** |
|---|---|---|
| Online, på din/dina webbplatser | [!DNL Marketo Measure] JavaScript | Via [!DNL Online Channels] sida in [!DNL Marketo Measure], genom att referera till UTM-värden, landningssida och referera till sidinformation |
| Offline; Online, inte på din/dina webbplatser | Synkronisering av CRM-kampanjmedlemskap | Via [!UICONTROL Offline Channels] sida in [!DNL Marketo Measure]genom att referera till Campaign-typen |
| Försäljningsaktivitet | Synkronisering av CRM-aktivitet | Via [!UICONTROL Online Channels] sida in [!DNL Marketo Measure]genom att referera till det kampanjnamn som tilldelats på [!UICONTROL Activities] page |

>[!MORELIKETHIS]
>
>* [Mappa onlinekontaktytor till [!DNL Marketo Measure] Kanaler/delkanaler](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [Synkronisera CRM-kampanjer inifrån SFDC](/help/channel-tracking-and-setup/offline-channels/syncing-offline-campaigns.md)
>* [Synkroniserar CRM-kampanjer inifrån [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Mappa CRM-kampanjer till [!DNL Marketo Measure] Kanaler/delkanaler](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Skapa kontaktpunkter från försäljningsaktiviteter](/help/advanced-marketo-measure-features/activities-attribution/salesforce-activities-attribution.md)
>* [Frågor och svar om aktiviteter och Mappa aktiviteter Touchpoints till kanaler/underkanaler](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)


