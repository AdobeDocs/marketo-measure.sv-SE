---
unique-page-id: 18874608
description: "[!DNL Marketo Measure] Parametrar - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Parametrar"
exl-id: d66b9864-0d7e-455a-ae20-cca555f4d8c8
source-git-commit: 65e7f8bc198ceba2f873ded23c94601080ad0546
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# [!DNL Marketo Measure] Parametrar {#marketo-measure-parameters}

## [!DNL Marketo Measure] Förklarade parametrar {#marketo-measure-parameters-explained}

För att få ytterligare insikter från användningen av UTM-moduler [!DNL Marketo Measure] lägger till anpassade parametrar i annonserna i [!DNL Google] AdWords, Bing Ads and [!DNL Facebook] Ads. [!DNL Marketo Measure] integreras med dessa plattformar för att automatisera merparten av installationsprocessen. Om du väljer att använda automatisk taggning [!DNL Marketo Measure] kommer automatiskt att lägga till sina parametrar till webbadresserna till era annonser. [!DNL Marketo Measure] hämtar automatiskt marknadsföringskostnaderna från plattformarna och lägger in dem i [!DNL Marketo Measure] app.

Exempel på en URL utan parametrar:

`http://adobe.com/landing-page?myParam=foo`

Exempel på en URL med [!DNL Marketo Measure] parametrar:

`http://adobe.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## AdWords-parametrar {#adwords-parameters}

* `_bk={keyword}`
   * Representerar nyckelordet som personen använde i sökmotorn.
   * Den liknar termsparametern UTM.

* `_bt={creative}`
   * Representerar det kreativa ID:t eller namnet.
   * Den liknar UTM-innehållsparametern.

* `_bm={matchtype}`
   * Representerar hur nära nyckelordet matchades.
   * Nyckelordsmatchningstyper hjälper dig att styra vilka sökningar som utlöser din annons. Du kan till exempel använda en bred matchning för att visa annonsen för en bred publik eller använda exakt matchning för att hona in specifika kundgrupper.
   * De tre matchningstyperna är: Bred, suddig och exakt.

>[!NOTE]
>
>Mer information om matchningstyper finns i [här är en relevant AdWords-artikel](https://support.google.com/adwords/answer/2497836?hl=en){target=&quot;_blank&quot;}.

* `_bn={network}`
   * Representerar annonsnätverkstypen - [visa eller söka](https://support.google.com/adwords/answer/1752334?hl=en){target=&quot;_blank&quot;}.
   * Detta liknar parametern UTM-källa.

* `_bg={adgroupID}`
   * Representerar ID:t för annonskoncern som annonsen tillhör

## Parametrar för Bing Ads {#bing-ads-parameters}

* `_bt={adid}`
* `utm_medium=cpc`
* `utm_source=bing`
* `utm_term={keyword}`

## Facebook Parameters {#facebook-parameters}

* `_bf ={creative}`
   * Detta representerar det kreativa ID:t eller namnet