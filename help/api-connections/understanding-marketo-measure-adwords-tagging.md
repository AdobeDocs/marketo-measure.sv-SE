---
description: Om  [!DNL Marketo Measure] AdWords Tagging-vägledning för Marketo Measure-användare
title: Om  [!DNL Marketo Measure] AdWords-taggning
exl-id: c6658766-d3a8-46ed-b2d2-826eb61ce269
feature: APIs, Integration, UTM Parameters
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 1%

---

# Om [!DNL Marketo Measure] AdWords-taggning {#understanding-marketo-measure-adwords-tagging}

För att kunna spåra era annonser på en mycket detaljerad nivå måste annonsmålens URL:er vara unika. För att uppnå detta lägger [!DNL Marketo Measure] automatisk taggning automatiskt till spårningsparametrar i annonsens mål-URL:er för dina [!DNL AdWords]-annonser. Låt oss titta på ett exempel nedan.

Följande URL kommer inte att innehålla några detaljerade data:

* `http://example.com/landing-page?myParam=foo`

Samma URL ger emellertid detaljerade data på grund av [!DNL Marketo Measure]-parametrarna:

* `http://example.com/landing-page?myParam=foo&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Så här fungerar [!DNL Marketo Measure] automatisk taggning {#how-marketo-measure-auto-tagging-works}

**Om [!DNL Marketo Measure] hittar en spårningsmall:**

* [!DNL Marketo Measure] lägger till sina parametrar i spårningsmallen.
* Om en omdirigering från tredje part hittas i en spårningsmall som Kenshoo eller Marin, kommer [!DNL Marketo Measure] inte att vidta någon åtgärd. I stället måste du [lägga till [!DNL Marketo Measure] parametrar i tredjepartsverktyget i ditt konto](/help/api-connections/how-bid-management-tools-affect-marketo-measure.md){target="_blank"}.

Om ingen spårningsmall hittas kommer [!DNL Marketo Measure] att:

* Sök igenom alla URL:er för annonseringsmål efter våra [!DNL Marketo Measure]-parametrar.
* Om ni hittar er är ni redo att åka.
* Om det inte hittas kommer [!DNL Marketo Measure] att lägga till sina parametrar i slutet av URL:erna för annonseringsmål. För nya annonser kommer [!DNL Marketo Measure] att lägga till sina parametrar till URL:en för annonseringsmål inom två timmar efter att de har skapats.
* Det är viktigt att ha en spårningsmall på plats innan du aktiverar automatisk taggning så att [!DNL Marketo Measure] kan ansluta till den och förhindra en återställning av annonshistoriken.

[!DNL Marketo Measure] rekommenderar att du använder en mall för kontonivå, kampanjnivå eller annonsnivåspårning, eftersom det gör det möjligt att lägga till och subtrahera parametrar för alla annonser utan risk för avbrott eller borttagning av annonshistorik.

## Spårningsmallar {#tracking-templates}

Som förklaras av [!DNL Google AdWords] är en spårningsmall den URL som används för att nå en landningssida. Den spårningsinformation som samlas in används för att förstå er annonstrafik. [Klicka här](https://support.google.com/adwords/answer/7197008?hl=en){target="_blank"} om du vill ha mer information från Google.

[!DNL Marketo Measure] rekommenderar att du använder en mall för kontonivå, kampanjnivå eller annonsnivåspårning, eftersom det gör det möjligt att lägga till och subtrahera parametrar för alla annonser utan risk för avbrott eller borttagning av annonshistorik.

Det finns två spårningsmallar som [!DNL Marketo Measure] rekommenderar. Använd följande för att avgöra vilken version som passar dig:

* Om alla dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:

`{lpurl}&_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

* Om inga av dina annons-URL:er har ett &quot;?&quot; Använd den här URL:en i dem:

`{lpurl}?_bt={creative}&_bk={keyword}&_bm={matchtype}&_bn={network}&_bg={adgroupid}`

## Konfigurera en spårningsmall på kontonivå {#setting-up-a-tracking-template-at-the-account-level}

1. Logga in på ditt [!DNL Google AdWords]-konto.

1. Klicka på **[!UICONTROL All campaigns]** och sedan på **[!UICONTROL Settings]** i det expanderande fönstret.

   ![1. Klicka på Alla kampanjer och sedan på Inställningar i den expanderande &#x200B;](assets/utilizing-connections-13.png)

1. Klicka på **[!UICONTROL Account Settings]** överst och sedan på **[!UICONTROL Tracking Template]**. Ange spårningsmallen [!DNL Marketo Measure].

   ![1. Klicka på Kontoinställningar högst upp och sedan spåra](assets/bizible-guide-1.png)

1. Klicka på **[!UICONTROL Save]**.

## Konfigurera en spårningsmall på kampanjnivå {#setting-up-a-tracking-template-at-the-campaign-level}

1. Klicka på **[!UICONTROL All campaigns]** och sedan på **[!UICONTROL Campaigns]** i det expanderande fönstret.

   ![1. Klicka på Alla kampanjer och sedan på Campaigns i den expanderande &#x200B;](assets/utilizing-connections-12.png)

1. Välj alla tillämpliga kampanjer eller **[!UICONTROL Select All]**, klicka på **[!UICONTROL Edit]** och klicka sedan på **[!UICONTROL Change Tracking Templates]**.

   ![1. Välj alla tillämpliga kampanjer eller välj Alla, klicka på Redigera,](../assets/marketo-engage-activities-05.png)

1. Ange spårningsmallen [!DNL Marketo Measure] och klicka på **[!UICONTROL Apply]**.

## Konfigurera en spårningsmall på annonsgruppsnivå: {#setting-up-a-tracking-template-at-the-ad-group-level}

1. Klicka på **[!UICONTROL All campaigns]** och sedan på **[!UICONTROL Ad Groups]** i det expanderande fönstret.

   ![1. Klicka på Alla kampanjer och sedan på Lägg till grupper i &#x200B;](assets/api-connections-01.png)

1. Välj alla tillämpliga annonsgrupper eller välj Alla, klicka på **[!UICONTROL Edit]** och sedan på **[!UICONTROL Change Tracking Templates]**.

1. Ange spårningsmallen [!DNL Marketo Measure] och klicka på **[!UICONTROL Apply]**.

   ![1. Ange spårningsmallen för Marketo Measure och klicka på Använd.](../assets/marketo-engage-activities-01.png)

## Vanliga frågor och svar {#faq}

**F: Vilka behörigheter behöver den anslutna användaren?**

A: userinfo.email

**F: Hur lång tid kan det ta att importera utgiftsdata?**

A: 6 timmar

**F: Hur lång tid tar det att importera annonsdata?**

A: 4 timmar

**F: För dynamiska sökannonser, kan vi spåra kombinationen av rubrik, beskrivning o.s.v. i den kreativa delen?**

S: Vi kan inte hämta enskilda kreativa detaljer för dynamiska sökannonser, men om autotagging är aktiverat kan vi ändå få det kreativa ID:t och de intäktsgivande attributen.

>[!NOTE]
>
>När ändringarna är klara är du klar. Du kan kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} om du har frågor under installationen.

[Klicka här](https://support.google.com/adwords/answer/6076199?hl=en#tracking){target="_blank"} för instruktioner från Google om hur du skapar spårningsmallar på kontonivå.
