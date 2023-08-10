---
unique-page-id: 18874678
description: Förstå [!DNL Marketo Measure] AdWords Tagging - [!DNL Marketo Measure] - Produktdokumentation
title: Förstå [!DNL Marketo Measure] AdWords Tagging
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: 3bad77a72c0dea6caf0daadbb594f10f791af715
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Förstå [!DNL Marketo Measure] AdWords Tagging {#understanding-marketo-measure-adwords-tagging}

För att kunna spåra era annonser på en mycket detaljerad nivå måste annonsmålens URL:er vara unika. För att uppnå detta [!DNL Marketo Measure] automatisk taggning lägger automatiskt till spårningsparametrar i webbadresserna för annonserna i [!DNL AdWords] annonser. Låt oss titta på ett exempel nedan.

Följande URL kommer inte att innehålla några detaljerade data:

* `http://example.com/landing-page?myParam=foo`

På grund av [!DNL Marketo Measure] parametrar:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Hur [!DNL Marketo Measure] Automatisk taggning i Works {#how-marketo-measure-auto-tagging-works}

**If [!DNL Marketo Measure] söker efter en spårningsmall:**

* [!DNL Marketo Measure] lägger till parametrarna i spårningsmallen.
* Om en omdirigering från tredje part hittas i en spårningsmall som Kenshoo eller Marin, [!DNL Marketo Measure] kommer inte att vidta några åtgärder. I stället måste du [lägg till [!DNL Marketo Measure] parametrar till tredjepartsverktyget i ditt konto](/help/api-connections/utilizing-marketo-measures-api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Om ingen spårningsmall hittas [!DNL Marketo Measure] kommer att

* Sök igenom alla URL:er för annonsmål efter [!DNL Marketo Measure] Parametrar.
* Om ni hittar er är ni redo att åka.
* Om den inte hittas [!DNL Marketo Measure] kommer att lägga till sina parametrar i slutet av URL:erna för annonsmålet. För nya annonser [!DNL Marketo Measure] kommer att lägga till sina parametrar till annonsmålets URL inom två timmar efter att de har skapats.
* Det är viktigt att ha en spårningsmall på plats innan du aktiverar automatisk taggning, så att [!DNL Marketo Measure] kan kopplas till den och förhindra en återställning av annonshistorik.

[!DNL Marketo Measure] rekommenderar att du använder en mall för kontonivå, kampanjnivå eller annonsnivåspårning, eftersom den gör det möjligt att lägga till och ta bort parametrar för alla annonser utan risk för avbrott eller radering av annonshistorik.

## Spårningsmallar {#tracking-templates}

Som förklaras av [!DNL Google AdWords]är en spårningsmall den URL som används för att nå en landningssida. Den spårningsinformation som samlas in används för att förstå er annonstrafik. [Klicka här](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} för mer information från Google.

[!DNL Marketo Measure] rekommenderar att du använder en kontonivå, kampanjnivå eller spårningsmall på annonsnivå, eftersom det gör det möjligt att lägga till och ta bort parametrar för alla annonser utan risk för avbrott eller borttagning av annonshistorik.

Det finns två spårningsmallar [!DNL Marketo Measure] rekommenderar att du använder. Använd följande för att avgöra vilken version som passar dig:

* Om alla dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Om inga av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Konfigurera en spårningsmall på kontonivå {#setting-up-a-tracking-template-at-the-account-level}

1. Logga in på [!DNL Google AdWords] Konto.

1. Klicka **[!UICONTROL All campaigns]** och sedan **[!UICONTROL Settings]** i det expanderande fönstret.

   ![](assets/1.png)

1. Klicka **[!UICONTROL Account Settings]** överst och sedan **[!UICONTROL Tracking Template]**. Ange [!DNL Marketo Measure] Spårningsmall.

   ![](assets/2-1.png)

1. Klicka på **[!UICONTROL Save]**.

## Konfigurera en spårningsmall på kampanjnivå {#setting-up-a-tracking-template-at-the-campaign-level}

1. Klicka **[!UICONTROL All campaigns]** och sedan **[!UICONTROL Campaigns]** i det expanderande fönstret.

   ![](assets/3.png)

1. Välj alla tillämpliga kampanjer eller **[!UICONTROL Select All]**, klicka **[!UICONTROL Edit]** och klicka sedan på **[!UICONTROL Change Tracking Templates]**.

   ![](assets/4-1.png)

1. Ange [!DNL Marketo Measure] Spårningsmall och klicka på **[!UICONTROL Apply]**.

## Konfigurera en spårningsmall på annonsgruppsnivå: {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Klicka **[!UICONTROL All campaigns]** och sedan **[!UICONTROL Ad Groups]** i det expanderande fönstret.

   ![](assets/5-1.png)

1. Välj alla tillämpliga annonsgrupper eller välj alla, klicka på **[!UICONTROL Edit]** och sedan klicka **[!UICONTROL Change Tracking Templates]**.

1. Ange [!DNL Marketo Measure] Spårningsmall och klicka på **[!UICONTROL Apply]**.

   ![](assets/6-1.png)

## Vanliga frågor {#faq}

**F: Vilka behörigheter behöver den anslutna användaren?**

A: userinfo.email

**F: Hur lång tid tar det att importera utgiftsdata?**

A: 6 timmar

**F: Hur lång tid tar det att importera annonsdata?**

A: 4 timmar

**F: För dynamiska sökannonser, kan vi spåra kombinationen av rubrik, beskrivning osv. i det projekt som vi serverade?**

S: Vi kan inte hämta enskilda kreativa detaljer för dynamiska sökannonser, men om autotagging är aktiverat kan vi ändå få det kreativa ID:t och de intäktsgivande attributen.

>[!NOTE]
>
>När ändringarna är klara är du klar. Nå ut till [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} om det finns några frågor under installationen.

[Klicka här](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} om du vill ha instruktioner från Google om hur du skapar spårningsmallar på kontonivå.
