---
unique-page-id: 18874684
description: Synkroniseringsdatum för kampanj - [!DNL Marketo Measure]
title: Synkroniseringsdatum för kampanj
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
feature: Channels
source-git-commit: b84909fbb34a1d8f739ebeea3400ef8816e17d32
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Synkroniseringsdatum för kampanj {#campaign-sync-dates}

Lär dig vad funktionen för kampanjsynkroniseringsdatum gör, och visa några användningsexempel för den här funktionen.

>[!NOTE]
>
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användare att använda den [nya, förbättrade processen i appen](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

**[!DNL Marketo Measure]Paket krävs: 6.9 eller senare**

Den här funktionen består av två enkla datumfält på kampanjobjektet [!DNL Salesforce]:

* Startdatum för kontaktpunkt
* Slutdatum för slutpunkt

När Buyer Touchpoints har aktiverats för en viss kampanj kan ni med Campaign Sync Dates ange parametrar för slutpunktsdatum för den enskilda kampanjen. Om du lägger till slutdatumet för slutpunkten den 1 mars 2017 kommer [!DNL Marketo Measure] bara att skapa kontaktpunkter på kampanjmedlemmar som lades till i kampanjen före det datumet. [!DNL Marketo Measure] skapar inte kontaktytor för kampanjmedlemmar som lades till efter den 1 mars 2017.

![](assets/1.gif)

På samma sätt gäller att om du lägger till ett startdatum för kontaktpunkt på en kampanj (till exempel 1 januari 2017), kommer [!DNL Marketo Measure] inte att skapa kontaktpunkter på kampanjmedlemmar som lades till i kampanjen före 1 januari 2017. Du behöver inte lägga till ett startdatum för pekpunkten om du lägger till ett slutdatum för pekpunkten och vice versa.

## Användningsexempel {#use-cases}

**Kontaktpunkter som fyllts på baklänges**

Det kan finnas tillfällen då ett marknadsföringsteam kanske missar att lägga till utm-parametrar i en viss marknadsföringssatsning. Med kampanjsynkroniseringsdatum kan du (om du använder SFDC-kampanjer för onlinearbete) fylla i vissa missade data. Låt oss säga att du kör en e-postkampanj som började 1 maj, men ditt team lade inte till utm-parametrar för den e-postkampanjen förrän 15 maj. Om du spårar e-postkonverteringar via en SFDC-kampanj kan du ställa in slutdatumet för slutpunkten den 15 maj för den kampanjen och aktivera slutpunkterna för&quot;Responded&quot;-medlemmar i kampanjen. Den här åtgärden instruerar [!DNL Marketo Measure] att skapa kontaktpunkter för alla dessa svar fram till 15 maj.

**Retroaktivt kampanjmedlemskap - kontaktpunkter**

Om du är en ny [!DNL Marketo Measure]-kund kan du vara intresserad av att få med en del marknadsföringsdata som du har spårat via SFDC-kampanjer. Om du däremot vill aktivera kontaktpunkter för dina SFDC-kampanjer online kan du stöta på problemet med dubbelräkning eftersom [!DNL Marketo Measure] automatiskt skapar kontaktpunkter för dina onlinemarknadsföringsinsatser. För att undvika dubbelräkning av data kan du använda slutdatum för slutdatum för slutpunkter i kampanjen för att ange en gräns för de slutdatum för slutpunkter som skapas av [!DNL Marketo Measure] i SFDC-kampanjen. Om du till exempel vill lägga till retroaktiva konverteringar för en social kampanj som du har spårat i SFDC, men du är införstådd med att du har lagt till [!DNL Marketo Measure] JavaScript (som skapar onlinekontrollpunkter) den 1 juli, kan du redigera Social SFDC-kampanjen så att den innehåller ett slutdatum för slutpunkten som är lika med 1 juli och aktivera Buyer Touchpoints för den kampanjen.

Det kan finnas många andra användningsområden för slutdatum för slutpunkter. Om du behöver hjälp med att lösa en viss situation kan du kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
