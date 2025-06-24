---
unique-page-id: 18874682
description: Marknadskanaler och delkanaler - [!DNL Marketo Measure]
title: Marknadsföringskanaler och delkanaler
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
feature: Channels
source-git-commit: 0ba036e7ebba77d870931704a59b19011e84271e
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Marknadsföringskanaler och delkanaler {#marketing-channels-and-subchannels}

## Syfte {#purpose}

Om du vill definiera vad en kanal och en underkanal är i [!DNL Marketo Measure], hur de relaterar till ditt innehåll, skillnaden mellan de två klassificeringarna och hur de används i [!DNL Marketo Measure]-appen.

## Översikt {#overview}

Marknadsföringskanaler används för att kategorisera (eller&quot;bucket&quot;) dina marknadsföringsaktiviteter så att de blir lättare att rapportera, både i [!DNL Marketo Measure]-ROI-strecket och i CRM. [!DNL Marketo Measure] levereras med 12 av kartongskanalerna (som du kan anpassa/byta namn för att passa organisationens konventioner) samt möjligheten att ytterligare skapa anpassade kanaler för ännu mer detaljerad filtrering.

Varje gång du får en besökare till någon av dina innehållssidor på din webbplats (oavsett om innehållet är en webbsida, en nedladdning av rapport, en sidadress osv.), kommer denna lead att &quot;klistras&quot; in i en kanal/underkanal baserat på flera UTM-parametrar som finns i URL:en:

* Medium
* Källa
* Campaign
* Landningssida
* Refererande webbplats

Om du vill anpassa vilken&quot;bucket&quot; som dina leads hamnar i baserat på deras UTM-parametrar kan du använda Kanalregler. [Klicka här](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) om du vill ha mer information om hur du konfigurerar och underhåller kanalreglerna.

Lär dig hur du konfigurerar dina [onlinekanaler](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) och [offlinekanaler](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md), samt skillnaden mellan dem.

**Marknadsföringskanal**

Marknadsföringskanalen är den bredaste klassificeringsnivån och kan omfatta ett brett urval av underkanaler. Det här är den typ av Subchannel som dina leads kommer från. Exempel på marknadsföringskanaler är bland annat **Betald sökning, Organic Search, Display,** och **Betald social**. Marknadskanalen motsvarar vanligtvis parametervärdet utm_medium som finns i URL:en.

**Delkanal**

Delkanaler är den andra pusselbiten när du köper dina inkommande leads. Delkanaler berättar om exakt _vilken_-iteration av din marknadsföringskanal som användes. I den betalda kanalen för social marknadsföring kan du till exempel ha delkanaler för **AdWords**, **BingAds**, **Facebook** osv. Subkanalen motsvarar vanligtvis parametervärdet utm_source i URL:en.

## Exempel på användningsfall {#use-case-example}

Bilden nedan visar ett exempel på en marknadsföringskanal, delkanal och innehåll baserat på en webbsida med följande URL:

`http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&utm_medium=paidsocial`

I det här fallet är det innehåll som användaren försöker få åtkomst till introduktionshandboken för B2B-marknadsattribuering. [!DNL Marketo Measure] kommer att analysera URL:en som leder till det här innehållet med hjälp av kanalreglerna som har konfigurerats i den här organisationen och använda dem för att&quot;markera&quot; det här leadet i marknadsföringskanalen&quot;Betald social&quot; och delkanalen&quot;LinkedIn&quot;.

![](assets/1.jpg)

Fler exempel...

**Marknadskanal (Medium)**

* PPC
* Betald social
* Organic Social
* E-post
* Event och konferenser
* Organic Search/SEO
* PR
* Referensprogram

**Underkanal (Touchpoint Source)**

* Google AdWord
* BingAds
* Facebook-annonser
* Adroll
* Dubbelklicka
* Capterra
* Drip-kampanjer
* LinkedIn-annonser

**Innehåll (rapporter, sidadresser, blogginlägg)**

* www.adobe.com/blog1
* www.adobe.com/whitepaper
* www.adobe.com/sign-up-now
