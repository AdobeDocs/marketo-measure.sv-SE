---
unique-page-id: 18874720
description: Hur budhanteringsverktygen påverkar [!DNL Marketo Measure] - [!DNL Marketo Measure] - Produktdokumentation
title: Hur budhanteringsverktygen påverkar [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Hur budhanteringsverktygen påverkar [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Läs om hur anbudshanteringsplattformar påverkar [!DNL Marketo Measure] möjlighet att spåra AdWords och BingAds, tillsammans med hur ni ställer in spårningsmallar med våra parametrar för att säkerställa att alla spår är korrekta.

Kenshoo och Marin är utmärkta verktyg som gör att marknadsförarna kan spåra, hantera och optimera sina annonskampanjer med olika sökmotorer. För att [!DNL Marketo Measure] parametrar som ska läggas till i dessa annonser måste du skapa en spårningsmall med [!DNL Marketo Measure] parametrar. Det går inte att ansluta annonsplattformarna till [!DNL Marketo Measure] kontot och aktivera automatisk taggning eftersom det orsakar [!DNL Marketo Measure] taggningssystem som konkurrerar med Kenshoo/Marins taggningssystem. Detta gör att våra parametrar ändras och läggs till felaktigt. Om du vill kringgå detta spårar du mallar med [!DNL Marketo Measure] parametrar måste ställas in i Kenshoo och Marin.

## För [!DNL Adwords] Konton {#for-adwords-accounts}

Konfigurera en spårningsmall enligt följande:

* Klicka på **[!UICONTROL Campaigns]** -fliken.
* Klicka på **[!UICONTROL Shared library]** i sidnavigeringsfältet.
* Klicka **URL-alternativ**.
* Bredvid Spårningsmall klickar du på **Redigera**.
* Fyll i URL-adressen:

   * Om ALLA era annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Om INGEN av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`


## För [!DNL Bing Ads] Konton {#for-bing-ads-accounts}

Konfigurera en spårningsmall enligt följande:

* Klicka på **[!UICONTROL Campaigns]** -fliken.
* Klicka på **[!UICONTROL Shared library]** i sidnavigeringsfältet.
* Klicka **URL-alternativ**.
* Bredvid Spårningsmall klickar du på **Redigera**.
* Fyll i URL-adressen:

   * Om ALLA era annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Om INGEN av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
