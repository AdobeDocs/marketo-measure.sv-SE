---
description: '[!DNL Marketo Measure] parametrar - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] parametrar'
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
feature: APIs, Integration, UTM Parameters
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# [!DNL Marketo Measure] parametrar {#marketo-measure-parameters}

## [!DNL Marketo Measure] parametrar förklaras {#marketo-measure-parameters-explained}

Om du vill få ytterligare insikter från användningen av UTM:er lägger [!DNL Marketo Measure] till anpassade parametrar i dina annonser i [!DNL Google] AdWords, Bing Ads och [!DNL Facebook] Ads. [!DNL Marketo Measure] integreras med dessa plattformar för att automatisera merparten av konfigurationsprocessen. Om du väljer att använda automatisk taggning kommer [!DNL Marketo Measure] automatiskt att lägga till sina parametrar till webbadresserna för dina annonser. [!DNL Marketo Measure] hämtar automatiskt dina marknadsföringskostnader från plattformarna och läser in dem i appen [!DNL Marketo Measure].

Exempel på en URL utan parametrar:

`http://adobe.com/landing-page?myParam=foo`

Exempel på en URL med [!DNL Marketo Measure] parametrar:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## AdWords-parametrar {#adwords-parameters}

* `_bk={keyword}`
   * Representerar nyckelordet som personen använde i sökmotorn.
   * Den liknar termsparametern UTM.

* `_bt={creative}`
   * Representerar kreativt ID eller namn.
   * Den liknar UTM-innehållsparametern.

* `_bm={matchtype}`
   * Representerar hur nära nyckelordet matchades.
   * Nyckelordsmatchningstyper hjälper dig att styra vilka sökningar som utlöser din annons. Du kan till exempel använda en bred matchning för att visa annonsen för en bred publik eller använda exakt matchning för att hona in specifika kundgrupper.
   * De tre matchningstyperna är: breda, oskarpa och exakta.

>[!TIP]
>Mer information om matchningstyper finns i [här är en relevant AdWords-artikel](https://support.google.com/adwords/answer/2497836?hl=en){target="_blank"}.

* `_bn={network}`
   * Representerar annonsnätverkstypen - [visa eller sök](https://support.google.com/adwords/answer/1752334?hl=en){target="_blank"}.
   * Detta liknar parametern UTM Source.

* `_bg={adgroupID}`
   * Representerar ID:t för annonskoncern som annonsen tillhör

>[!NOTE]
>Vi stöder inte parametrar för omdirigerings-URL.

## Parametrar för Bing Ads {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Facebook-parametrar {#facebook-parameters}

* `_bf ={creative}`
   * Detta representerar ditt kreativa ID eller namn
