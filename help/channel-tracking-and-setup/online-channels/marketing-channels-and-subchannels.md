---
unique-page-id: 18874682
description: Marknadsföringskanaler och delkanaler - [!DNL Marketo Measure] - Produktdokumentation
title: Marknadsföringskanaler och delkanaler
exl-id: fbe2a994-cf6d-439c-af96-a562216434cc
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Marknadsföringskanaler och delkanaler {#marketing-channels-and-subchannels}

## Syfte {#purpose}

Definiera vad en kanal och en delkanal ska vara i [!DNL Marketo Measure], hur de relaterar till ditt innehåll, skillnaden mellan de två klassificeringarna och hur de används i [!DNL Marketo Measure] app.

## Översikt {#overview}

Marknadsföringskanaler används för att kategorisera (eller&quot;bucket&quot;) era marknadsföringsaktiviteter för att underlätta rapporteringen, båda i [!DNL Marketo Measure] ROI Dash och i CRM. [!DNL Marketo Measure] innehåller 12 av kartongskanalerna (som du kan anpassa/byta namn efter organisationens regler) samt möjligheten att ytterligare skapa anpassade kanaler för ännu mer detaljerad filtrering.

Varje gång du får en besökare till någon av dina innehållssidor på din webbplats (oavsett om innehållet är en webbsida, en nedladdning av rapport, en sidadress osv.), kommer denna lead att &quot;klistras&quot; in i en kanal/underkanal baserat på flera UTM-parametrar som finns i URL:en:

* Medel
* Källa
* Campaign
* Landningssida
* Refererande webbplats

Om du vill anpassa vilken&quot;bucket&quot; som dina leads hamnar i baserat på deras UTM-parametrar kan du använda Kanalregler. Mer information om hur du konfigurerar och underhåller kanalregler finns i [klicka här](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Lär dig hur du konfigurerar [Onlinekanaler](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) och [Offlinekanaler](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)och skillnaden mellan dem.

**Marknadsföringskanal**

Marknadsföringskanalen är den bredaste klassificeringsnivån och kan omfatta ett brett urval av underkanaler. Det här är den typ av Subchannel som dina leads kommer från. Exempel på marknadsföringskanaler är **Betald sökning, organisk sökning, visning,** och **Betald social**. Marknadskanalen motsvarar vanligtvis parametervärdet utm_medium som finns i URL:en.

**Delkanal**

Delkanaler är den andra pusselbiten när du köper dina inkommande leads. Delkanaler berättar om exakt _som_ Den upprepning av marknadsföringskanalen som användes. I den betalda kanalen för social marknadsföring kan du till exempel ha delkanaler för **AdWords**, **BingAds**, **Facebook**, osv. Subkanalen motsvarar vanligtvis parametervärdet utm_source i URL:en.

## Exempel på användningsfall {#use-case-example}

Bilden nedan visar ett exempel på en marknadsföringskanal, delkanal och innehåll baserat på en webbsida med följande URL:

* [http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial](http://info.bizible.com/intro-guide-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=paidsocial)*

I det här fallet är det innehåll som användaren försöker få åtkomst till introduktionshandboken för B2B-marknadsattribuering. [!DNL Marketo Measure] kommer att analysera URL:en som leder till det här innehållet med hjälp av kanalreglerna som har konfigurerats i den här organisationen och använda dem för att&quot;krympa&quot; detta lead i marknadsföringskanalen&quot;Betald social&quot; och delkanalen&quot;LinkedIn&quot;.

![](assets/1.jpg)

Fler exempel...

**Marknadsföringskanal (mellan)**

* PPC
* Betald social
* Organic Social
* E-post
* Event och konferenser
* Organic Search/SEO
* PR
* Referensprogram

**Delkanal (slutpunktskälla)**

* Google AdWords
* BingAds
* Facebook Ads
* Adroll
* Dubbelklicka
* Capterra
* Drip-kampanjer
* linkedIn Ads

**Innehåll (rapporter, sidadresser, blogginlägg)**

* www.adobe.com/blog1
* www.adobe.com/whitepaper
* www.adobe.com/sign-up-now
