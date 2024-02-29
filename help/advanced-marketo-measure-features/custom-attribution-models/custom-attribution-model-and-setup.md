---
unique-page-id: 18874779
description: Anpassad attributmodell och inställningar - [!DNL Marketo Measure]
title: Anpassad attributmodell och inställningar
exl-id: 7b156db2-9ac6-4d32-ac67-06c0aa15d651
feature: Attribution, Custom Models
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Anpassad attributmodell och inställningar {#custom-attribution-model-and-setup}

Nedan finns en översikt över [!DNL Marketo Measure] egen attribueringsmodell och hur du konfigurerar den.

## Anpassad attributmodell {#custom-attribution-model}

The [!DNL Marketo Measure] Med en anpassad attribueringsmodell kan användarna välja vilka kontaktytor eller anpassade stadier som ska ingå i modellen. Användarna kan styra den procentuella intäktskrediten som tilldelats dessa kontaktytor och faser, eller kan använda de procentvärden för attribuering som föreslås av [!DNL Marketo Measure] Machine Learning-modell.

## Så här konfigurerar du en anpassad attributmodell {#how-to-set-up-your-custom-attribution-model}

1. Bestäm vilka faser du vill inkludera i den anpassade modellen.

   För att börja bygga upp en anpassad attribueringsmodell måste ni välja vilka faser som är viktiga för ert marknadsföringsteam. Förutom [!DNL Marketo Measure] milstolpe-faser (FT, LC, OC, Closed) kan du lägga till upp till sex ytterligare lead-/kontaktstatuslägen eller säljprojektsfaser i din anpassade modell. Det är till exempel vanligt att MQL-scenen inkluderas i den anpassade modellen. Marknadsföringsteamen vill ofta veta vilka satsningar eller kanaler som driver övergångar till MQL-steget.

   Logga in på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Gå till [!UICONTROL My Account] > [!UICONTROL Settings] > och under CRM väljer du **[!UICONTROL Stage Mapping]**.

   Välj sedan vilka leads/kontakter och säljprojektsfaser som ska inkluderas genom att välja **[!UICONTROL Include in Model]** box.

   >[!NOTE]
   >
   >Du tillåts upp till sex anpassade steg (exklusive standardvärdena: FT, LC, OC, Closed).

   ![](assets/1-1.png)

   >[!NOTE]
   >
   >_Alla_ Leads/kontakter och säljprojektsfaser visas här, även om scenen är inaktiv eller inte längre används i [!DNL Salesforce]. Om du vill ta bort de här faserna måste du ta bort dem permanent i [!DNL Salesforce].

   När du har valt dina stadier ska du klicka på **[!UICONTROL Save & Process]** längst ned på sidan. Stegen visas nu i **[!UICONTROL Attribution Settings]** och du kan tilldela attribueringsprocentsatser till varje fas. Anpassade faser visas också i Marketing Performance Suite som en lead- eller säljprojektsfas i rapporten Demand Waterfall.

   Om det finns andra stadier som du vill inkludera i modellen, men de finns inte i [!UICONTROL Lead/Contact Status] eller [!UICONTROL Opportunity Stage] kan du definiera en egen anpassad scen baserat på fält i CRM.

   I exemplet nedan definieras en anpassad MQL-fas med hjälp av ett datumfält. Regeln anger helt enkelt att om fältet MQL-datum inte är tomt ska det betraktas som en MQL och inkluderas i den anpassade modellen. Det är också viktigt att sortera de anpassade faserna när de har skapats så att de följer utvecklingen i din säljcykel.

   ![](assets/2-1.png)

   >[!CAUTION]
   >
   >Glöm inte att aktivera historikspårning för anpassade fält.

Om ett anpassat fält används i din anpassade modell MÅSTE du aktivera spårning av fälthistorik i CRM. Instruktioner om hur du aktiverar spårning av fälthistorik finns i [Anpassad modellinställning: Aktivera spårning av fälthistorik](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md).

1. Bestäm attribueringsprocenten för den anpassade modellen.

   Gå till **[!UICONTROL Attribution Settings]** in [!DNL Marketo Measure] Appar; de anpassade stegen visas här i attribueringstabellen. Attributtabellen visar alla [!DNL Marketo Measure] attribueringsmodeller och attribueringsviktningen för varje modell. Attributprocenten för de första fem modellerna är fasta och kan inte ändras.

   I kolumnen längst till höger heter **[!UICONTROL Custom]**,&quot; kan du ange procentviktningen för varje fas i din anpassade attribueringsmodell. Ange bara värdena för varje scen i kolumnen Anpassad. Sedan **[!UICONTROL Save and Reprocess]** när allt är klart.

   Till vänster om _Egen_ kolumnen är **[!DNL Marketo Measure]Machine Learning-modell**. Maskininlärningsmodellen beräknar attribueringsviktningen baserat på den relativa vikten av att vinna ett avtal beroende på vad som hände i varje kundfas. Mer information om Machine Learning-modellen finns i [Vanliga frågor om maskininlärningsmodellen](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).

   ![](assets/3.png)

## Pekpunktspositioner {#touchpoint-positions}

När attribueringsprocenten har sparats och bearbetats uppdateras kontaktytorna och får sina nya faser och positioner. Kontaktpunkten som inträffade senast, före en övergång till en fas, får krediter för den fasen (se nedan). Även den anpassade viktningen och intäkterna fördelas på nytt.

![](assets/4.png)

## Skillnaden mellan trattfaser och anpassade modellfaser {#the-difference-between-funnel-stages-and-custom-model-stages}

Nu kan du se anpassade faser i marknadsföringsfunktionen, även om du inte har aktiverat Anpassad modell. Detta skulle vara tack vare funktionen Funnel Stage. Funktionella scener ger dig nu möjlighet att lägga till faser i tratten, men du kan inte se attribuering för dem.

Tratt Stages spåras fortfarande som Touchpoints och visas fortfarande som Touchpoint-positioner i CRM. Utan en anpassad modell kan dessa Touchpoints fortfarande få mellanberöringsattribuering om det finns en formulärfyllning (10 % för Middle Touches), men ingen attribuering om det bara är ett webbbesök.

Som du ser nedan har vi inkluderat &quot;Dizzy&quot;-stadiet som en del av våra Funnel Stages. Det innebär att vi har kontaktpunkter där positionen innehåller Divattenstämpel, men dessa kontaktpunkter får bara attribueringskrediter för Mellanöstern om Anpassad modell inte är aktiverad (högst 10 %).

![](assets/5.png)

>[!NOTE]
>
>Beteendet för anpassade BAT-modeller är att dela upp den anpassade modellen i mitten med jämna mellanrum över andra faser, förutsatt att det inte finns några mellanjusteringar.
