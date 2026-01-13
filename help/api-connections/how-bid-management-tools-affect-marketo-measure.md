---
description: Så här påverkar hanteringsverktygen för bud  [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Så här påverkar hanteringsverktygen för bud  [!DNL Marketo Measure]
exl-id: 67c00ad9-8b12-4238-8a1f-2d2f5ed04423
feature: APIs, Integration, UTM Parameters
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Så här påverkar hanteringsverktygen för bud [!DNL Marketo Measure] {#how-bid-management-tools-affect-marketo-measure}

Lär dig hur anbudshanteringsplattformar påverkar [!DNL Marketo Measure] förmågan att spåra AdWords och BingAds, samt hur du ställer in spårningsmallar med våra parametrar för att säkerställa att alla spår är korrekta.

Kenshoo och Marin är utmärkta verktyg som gör att marknadsförarna kan spåra, hantera och optimera sina annonskampanjer med olika sökmotorer. För att [!DNL Marketo Measure] parametrar ska kunna läggas till i dessa annonser måste du konfigurera en spårningsmall med våra [!DNL Marketo Measure]-parametrar. Det går inte att ansluta annonsplattformarna till ditt [!DNL Marketo Measure]-konto och aktivera automatisk taggning eftersom det leder till att taggningssystemet [!DNL Marketo Measure] konkurrerar med Kenshoo/Marins taggningssystem. Detta gör att våra parametrar ändras och läggs till felaktigt. För att undvika detta måste spårningsmallar med [!DNL Marketo Measure] parametrar konfigureras i Kenshoo och Marin.

## För [!DNL Adwords]-konton {#for-adwords-accounts}

Konfigurera en spårningsmall enligt följande:

* Klicka på fliken **[!UICONTROL Campaigns]**.
* Klicka på länken **[!UICONTROL Shared library]** i sidnavigeringsfältet.
* Klicka på **URL-alternativ**.
* Klicka på **Redigera** bredvid Spårningsmall.
* Fyll i URL-adressen:

   * Om ALLA era annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}&_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`
   * Om INGEN av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}?_bk={keyword}&_bt={creative}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## För [!DNL Bing Ads]-konton {#for-bing-ads-accounts}

Konfigurera en spårningsmall enligt följande:

* Klicka på fliken **[!UICONTROL Campaigns]**.
* Klicka på länken **[!UICONTROL Shared library]** i sidnavigeringsfältet.
* Klicka på **URL-alternativ**.
* Klicka på **Redigera** bredvid Spårningsmall.
* Fyll i URL-adressen:

   * Om ALLA era annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}&_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
   * Om INGEN av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:
      * `{lpurl}?_bt={adid}&utm_term={keyword}&utm_source=Bing_Yahoo&utm_medium=CPC`
