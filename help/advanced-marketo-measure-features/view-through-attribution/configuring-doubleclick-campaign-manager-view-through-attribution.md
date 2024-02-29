---
unique-page-id: 18874781
description: Konfigurera dubbelklickning av Campaign Manager-vy via attribut - [!DNL Marketo Measure] - Produktdokumentation
title: Konfigurera dubbelklickning av Campaign Manager-vy via attribut
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
feature: Attribution
source-git-commit: cc786cb3af08fa36af91ef22f4dba3072c9617eb
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Konfigurera dubbelklickning av Campaign Manager-vy via attribut {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Mätningsvy via attribuering {#measuring-view-through-attribution}

>[!NOTE]
>
>Om du använder [!DNL Marketo Measure] och [!DNL DoubleClick Campaign Manager] integrering, vi behöver en [API-anslutning](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) så att vi kan ladda ned information om kampanjer och kreatörer för att lösa annonserna.

Börja få mer detaljerad information genom att spåra med [!DNL Doubleclick Campaign Manager]måste vår spårningspixel konfigureras.

Please [klicka här](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md) för mer information om [!DNL Marketo Measure] Visa via attribueringsfunktioner.

[!DNL Marketo Measure] betraktas som en piggyback-tagg eftersom det är ett tredjepartsanrop via DCM-annonstaggen. Piggyback-taggar fungerar inte med bildtaggar, bara iframe- och javascript-taggar. Enligt DCM-stödet ändrades detta inte nyligen och har alltid varit fallet. Standardtaggar togs bort den 2 oktober 2017 men påverkar inte möjligheten för [!DNL Marketo Measure] för att spåra intryck.

Om du använder hierarkin Överordnad och Underordnad i DCM måste taggen användas på alla nivåer för att spåra intrycket.

## Lägga till bildtaggen {#how-to-add-the-image-tag}

Du ska lägga till taggen i [!DNL Doubleclick] under inställningen Advertiser och du vill skapa en Impression-händelsetagg.

1. Lägg till följande kod som en 1x1-bildpixel.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Bekräfta att avgränsarna mappas enligt följande när den har lagts till. Detta bör vara automatiskt när taggen används:

   v = %eadv! [!DNL Expand] Annonsörs-ID\
   a = %eaid! Expandera annons-ID\
   c = %ecid! Expandera kreativt ID\
   s = %esid! Expandera plats-ID\
   p = %epid! Expandera placerings-ID\
   m = %m makro för matchningskod\
   n = %n slumpmässigt nummermakro

   ![](assets/1.png)

## Vanliga frågor och svar {#faq}

**F: Är bildtaggen säker?**

S: Ja. Det är inte en JavaScript-tagg, utan en image-tagg.

**F: Vilka behörigheter behöver den anslutna användaren?**

A: dfatrafficking, dfareporting, userinfo.email

**F: Hur lång tid tar det att importera utgiftsdata?**

A: Upp till 6 timmar

**F: Hur lång tid tar det att importera annonsdata?**

A: Upp till 6 timmar
