---
description: Anpassad attributmodell och konfigurationsvägledning för Marketo Measure-användare
title: Anpassad attributmodell och inställningar
exl-id: 7b156db2-9ac6-4d32-ac67-06c0aa15d651
feature: Attribution, Custom Models
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 0%

---

# Anpassad attributmodell och inställningar {#custom-attribution-model-and-setup}

Nedan finns en översikt över den anpassade attribueringsmodellen [!DNL Marketo Measure] och hur du konfigurerar den.

## Anpassad attributmodell {#custom-attribution-model}

Med den anpassade attributmodellen [!DNL Marketo Measure] kan användare välja vilka kontaktytor eller anpassade steg som ska inkluderas i modellen. Användarna kan styra procentandelen av intäktskrediten som tilldelats dessa kontaktytor och faser, eller så kan de använda de procentvärden för attribuering som föreslås av [!DNL Marketo Measure] Machine Learning-modellen.

## Så här konfigurerar du en anpassad attributmodell {#how-to-set-up-your-custom-attribution-model}

1. Bestäm vilka faser du vill inkludera i den anpassade modellen.

   För att börja bygga upp en anpassad attribueringsmodell måste ni välja vilka faser som är viktiga för ert marknadsföringsteam. Förutom milstolpestegen [!DNL Marketo Measure] (FT, LC, OC, Closed) kan du lägga till upp till sex ytterligare Lead/Contact-statusar eller säljprojektsfaser i din anpassade modell. Det är till exempel vanligt att MQL-scenen inkluderas i den anpassade modellen. Marknadsföringsteamen vill ofta veta vilka satsningar eller kanaler som driver övergångar till MQL-steget.

   Logga in på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Gå till [!UICONTROL My Account] > [!UICONTROL Settings] > och välj **[!UICONTROL Stage Mapping]** under CRM-avsnittet.

   Välj sedan vilka leads/kontakter och säljprojektsfaser som ska inkluderas genom att markera rutan **[!UICONTROL Include in Model]**.

   >[!NOTE]
   >
   >Du tillåts upp till sex anpassade steg (exklusive standardvärdena: FT, LC, OC, Closed).

   ![Du tillåts upp till sex anpassade stadier (inklusive inte standardvärdena:](assets/custom-models-1.png)

   >[!NOTE]
   >
   >_Alla_ leads/kontakter och säljprojektsfaser visas här, även om scenen är inaktiv eller inte längre används i [!DNL Salesforce]. Om du vill ta bort de här faserna måste du ta bort dem i [!DNL Salesforce].

   När du har valt dina stadier ska du klicka på knappen **[!UICONTROL Save & Process]** längst ned på sidan. Stegen visas nu på fliken **[!UICONTROL Attribution Settings]** och du kan tilldela attribueringsprocentsatser till varje fas. Anpassade faser visas också i Marketing Performance Suite som en lead- eller säljprojektsfas i rapporten Demand Waterfall.

   Om det finns andra stadier som du vill inkludera i modellen, men de inte finns i listan [!UICONTROL Lead/Contact Status] eller [!UICONTROL Opportunity Stage], kan du definiera en egen anpassad scen baserat på fälten i CRM.

   I exemplet nedan definieras en anpassad MQL-fas med hjälp av ett datumfält. Regeln anger helt enkelt att om fältet MQL-datum inte är tomt ska det betraktas som en MQL och inkluderas i den anpassade modellen. Det är också viktigt att sortera de anpassade faserna när de har skapats så att de följer utvecklingen i din säljcykel.

   ![I exemplet nedan definieras en anpassad MQL-scen med en &#x200B;](assets/custom-models-10.png)

   >[!CAUTION]
   >
   >Glöm inte att aktivera historikspårning för anpassade fält.

Om ett anpassat fält används i din anpassade modell MÅSTE du aktivera spårning av fälthistorik i CRM. Instruktioner om hur du aktiverar spårning av fälthistorik finns i [Anpassade modellinställningar: Aktivera spårning av fälthistorik](/help/channel-tracking-and-setup/custom-model-setup-enable-field-history-tracking.md).

1. Bestäm attribueringsprocenten för den anpassade modellen.

   Gå till **[!UICONTROL Attribution Settings]** i [!DNL Marketo Measure] appar. De anpassade stegen visas här i attribueringstabellen. I attribueringstabellen visas alla [!DNL Marketo Measure]-attribueringsmodeller och attribueringsviktningen för varje modell. Attributprocenten för de första fem modellerna är fasta och kan inte ändras.

   I kolumnen längst till höger med namnet **[!UICONTROL Custom]** kan du ange procentviktningen för varje fas i din anpassade attribueringsmodell. Ange värdena för varje fas i kolumnen Anpassad och klicka på **[!UICONTROL Save and Reprocess]** när du är klar.

   Till vänster om kolumnen _Anpassad_ finns **[!DNL Marketo Measure]Machine Learning-modellen**. Maskininlärningsmodellen beräknar attribueringsviktningen baserat på den relativa vikten av att vinna ett avtal beroende på vad som hände i varje kundfas. Mer information om maskininlärningsmodellen finns i [Vanliga frågor om maskininlärningsmodellen](/help/channel-tracking-and-setup/machine-learning-model-faq.md).

   ![Till vänster om kolumnen Anpassad finns Marketo Measure](assets/custom-models-2.png)

## Pekpunktspositioner {#touchpoint-positions}

När attribueringsprocenten har sparats och bearbetats uppdateras kontaktytorna och får sina nya faser och positioner. Kontaktpunkten som inträffade senast, före en övergång till en fas, får krediter för den fasen (se nedan). Även den anpassade viktningen och intäkterna fördelas på nytt.

![När attribueringsprocenten har sparats och bearbetats blir kontaktytorna &#x200B;](assets/custom-models-3.png)

## Skillnaden mellan Funnel-scener och anpassade modellfaser {#the-difference-between-funnel-stages-and-custom-model-stages}

Nu kan du se anpassade faser i din Marketing Funnel, även om du inte har aktiverat Anpassad modell. Detta sker genom att vi använder vår Funnel Stage-funktion. Funnel Stages ger dig nu möjlighet att lägga till faser i funnel, men du kan inte se attribuering för dem.

Funnel Stages spåras fortfarande som Touchpoints och visas fortfarande som Touchpoint-positioner i CRM. Utan en anpassad modell kan dessa Touchpoints fortfarande få mellanberöringsattribuering om det finns en formulärfyllning (10 % för Middle Touches), men ingen attribuering om det bara är ett webbbesök.

Som du kan se nedan har vi inkluderat&quot;Dizzy&quot;-scenen som en del av Funnel Stages. Det innebär att vi har kontaktpunkter där positionen innehåller Divattenstämpel, men dessa kontaktpunkter får bara attribueringskrediter för Mellanöstern om Anpassad modell inte är aktiverad (högst 10 %).

![Som du kan se nedan har vi inkluderat stadiet Distinkt](assets/custom-models-7.png)

>[!NOTE]
>
>BAT egna modeller uppträder som att dela upp den anpassade modellen i mitten med jämna mellanrum i andra steg, förutsatt att det inte finns några mellanjusteringar.
