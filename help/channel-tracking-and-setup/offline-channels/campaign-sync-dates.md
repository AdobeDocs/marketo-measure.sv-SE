---
unique-page-id: 18874684
description: Synkroniseringsdatum för kampanj - [!DNL Marketo Measure] - Produktdokumentation
title: Synkroniseringsdatum för kampanj
exl-id: 66ce9948-9297-47ef-8b16-0ac45c5664fc
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Synkroniseringsdatum för kampanj {#campaign-sync-dates}

Lär dig vad funktionen för kampanjsynkroniseringsdatum gör, och visa några användningsexempel för den här funktionen.

**[!DNL Marketo Measure]Paket krävs: 6.9 eller senare**

Den här funktionen består av två enkla datumfält på [!DNL Salesforce] Kampanjobjekt:

* Startdatum för kontaktpunkt
* Slutdatum för slutpunkt

När Buyer Touchpoints har aktiverats för en viss kampanj kan ni med Campaign Sync Dates ange parametrar för slutpunktsdatum för den enskilda kampanjen. Om du lägger till slutdatumet för slutpunkten den 1 mars 2017 ska du göra det [!DNL Marketo Measure] kommer endast att skapa kontaktytor för Campaign-medlemmar som lades till i Campaign före det datumet. [!DNL Marketo Measure] inte skapar kontaktytor för kampanjmedlemmar som lades till efter den 1 mars 2017.

![](assets/1.gif)

Om du lägger till ett startdatum för en kontaktyta i en kampanj (till exempel 1 januari 2017) kan du [!DNL Marketo Measure] kommer inte att skapa kontaktytor för kampanjmedlemmar som lades till i kampanjen före den 1 januari 2017. Du behöver inte lägga till ett startdatum för pekpunkten om du lägger till ett slutdatum för pekpunkten och vice versa.

## Användningsexempel {#use-cases}

**Kontaktpunkter som fyller igen**

Det kan finnas tillfällen då ett marknadsföringsteam kanske missar att lägga till utm-parametrar i en viss marknadsföringssatsning. Med kampanjsynkroniseringsdatum kan du (om du använder SFDC-kampanjer för onlinearbete) fylla i vissa missade data. Låt oss säga att du kör en e-postkampanj som började 1 maj, men ditt team lade inte till utm-parametrar för den e-postkampanjen förrän 15 maj. Om du spårar e-postkonverteringar via en SFDC-kampanj kan du ange slutdatumet för slutpunkten den 15 maj för den kampanjen och aktivera slutpunkterna för respondenterna i Campaign. Den här åtgärden kommer att berätta [!DNL Marketo Measure] för att skapa kontaktpunkter för alla dessa svar fram till 15 maj.

**Retroaktiva kontaktpunkter för kampanjmedlemskap**

Om du är ny [!DNL Marketo Measure] kan du vara intresserad av att få med marknadsföringsdata som du har spårat via SFDC Campaigns. Om du däremot aktiverar kontaktpunkter för SFDC-kampanjer online kan du stöta på problem med dubbelräkningsattribuering eftersom [!DNL Marketo Measure] skapar automatiskt kontaktytor för er onlinemarknadsföring. För att undvika dubbelräkning av data kan du använda slutdatum för slutdatum för kampanjpunkten för att ange en gräns för de slutdatum för slutpunkter som skapas av [!DNL Marketo Measure] på SFDC-kampanjen. Om du till exempel vill lägga till retroaktiva konverteringar för en social kampanj har du spårat i SFDC, men du är införstådd med att du har lagt till [!DNL Marketo Measure] JavaScript (som skapar onlinekontaktytor) den 1 juli, kan du redigera Social SFDC-kampanjen så att den innehåller ett slutdatum för slutpunkten som är lika med 1 juli och aktivera Buyer Touchpoints för den kampanjen.

Det kan finnas många andra användningsområden för slutdatum för slutpunkter. Om du behöver hjälp med att ta reda på en viss situation kan du kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Universitet: Medlemsfält för kampanj och kampanj](https://learn.bizible.com/2-bizible-customization/137720https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
