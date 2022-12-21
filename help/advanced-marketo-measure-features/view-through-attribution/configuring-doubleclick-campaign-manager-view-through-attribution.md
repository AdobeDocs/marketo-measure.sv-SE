---
unique-page-id: 18874781
description: Konfigurera dubbelklickning av Campaign Manager-vy via attribut - [!DNL Marketo Measure] - Produktdokumentation
title: Konfigurera dubbelklickning av Campaign Manager-vy via attribut
exl-id: 2cc6c2cd-afb7-4052-b18b-9ad0bf16a9fa
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Konfigurera dubbelklickning av Campaign Manager-vy via attribut {#configuring-doubleclick-campaign-manager-view-through-attribution}

## Mätningsvy via attribuering {#measuring-view-through-attribution}

>[!NOTE]
>
>Om du använder [!DNL Marketo Measure] och integrering med DoubleClick Campaign Manager kräver en [API-anslutning](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms) så att vi kan ladda ned information om kampanjer och kreatörer för att lösa annonserna.

För att börja få mer detaljerad information genom att spåra med Doubleclick Campaign Manager måste vi konfigurera vår spårningspixel.

Please [klicka här](/help/advanced-marketo-measure-features/view-through-attribution/marketo-measure-view-through-attribution-faq.md) för mer information om [!DNL Marketo Measure] Visa via attribueringsfunktioner.

[!DNL Marketo Measure] betraktas som en piggyback-tagg eftersom det är ett tredjepartsanrop via DCM-annonstaggen. Piggyback-taggar fungerar inte med bildtaggar, bara iframe- och javascript-taggar. Enligt DCM-stödet ändrades detta inte nyligen och har alltid varit fallet. Standardtaggar togs bort den 2 oktober 2017 men påverkar inte möjligheten för [!DNL Marketo Measure] för att spåra intryck.

Om du använder hierarkin Överordnad och Underordnad i DCM måste taggen användas på alla nivåer för att spåra intrycket.

## Så här lägger du till bildtaggen {#how-to-add-the-image-tag}

Du lägger till taggen i Dubbelklicka under inställningen Advertiser och du vill skapa en Impression-händelsetagg.

1. Lägg till följande kod som en 1x1-bildpixel.

`https://cdn.bizibly.com/i?v=%eadv!&a=%eaid!&c=%ecid!&s=%esid!&p=%epid!&m=%m&n=%n`

1. Bekräfta att avgränsarna mappas enligt följande när den har lagts till. Detta bör vara automatiskt när taggen används:

   v = %eadv! Expandera annonsörs-ID\
   a = %eaid! Expandera annons-ID\
   c = %ecid! Expandera kreativt ID\
   s = %esid! Expandera plats-ID\
   p = %epid! Expandera placerings-ID\
   m = %m makro för matchningskod\
   n = %n slumpmässigt nummermakro

   ![](assets/1.png)

## Vanliga frågor {#faq}

**F: Är bildtaggen säker?**

S: Ja. Det är inte en JavaScript-tagg, utan en image-tagg.

**F: Vilka behörigheter behöver den anslutna användaren?**

S: dfatrafficking, dfareporting, userinfo.email

**F: Hur lång tid tar det att importera utgiftsdata?**

S: Upp till 6 timmar

**F: Hur lång tid tar det att importera annonsdata?**

S: Upp till 6 timmar
