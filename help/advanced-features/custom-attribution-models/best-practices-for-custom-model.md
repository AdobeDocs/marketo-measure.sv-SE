---
description: Bästa praxis för anpassad modell - [!DNL Marketo Measure]
title: Bästa praxis för anpassad modell
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---


# Bästa praxis för anpassad modell {#best-practices-for-custom-model}

## Översikt {#overview}

Förutom [!DNL Marketo Measure] i rutan Attribution Models har Tier 2-kunder och högre tillgång till en Custom Attribution Model.

Med den anpassade attributmodellen [!DNL Marketo Measure] kan användare välja vilka milstolppunktspositioner och/eller anpassade stadier som ska inkluderas i modellen. Dessutom kan användare styra den procentandel av kredit som tilldelas varje steg i modellen (användare kan definiera ytterligare 6 anpassade steg) eller använda de procentvärden för attribuering som föreslås av [!DNL Marketo Measure] Machine Learning-modellen.

Det finns två viktiga aspekter av din anpassade attribueringsmodell:

**Anpassade steg** tillåter användare att definiera sin funnel i relation till sin verksamhet och sina processer. Anpassade faser ska representera&quot;milstolpar&quot; under hela kundresan, ungefär som de [!DNL Marketo Measure] milstolparna (First Touch, Lead Creation Touch, Opportunity Creation Touch och Closed Won Touch) i lagerattribueringsmodellerna. Det är viktigt att dina anpassade faser är korrekt definierade och mappade inom ditt konto för att säkerställa att [!DNL Marketo Measure] spårar scenövergångar korrekt. Detta är för att identifiera vilka kontaktytor som ska kopplas till varje fas och attribuera kreditpoäng på lämpligt sätt. Anpassad Stage-mappning är i princip ett tillägg till standard Stage Mapping och bör följa samma praxis.

>[!NOTE]
>Mer information finns i resursen för metodmappning

**Anpassad attribueringsmodellering** definieras när du har valt funnel för anpassade scener. Användarna kan sedan styra hur mycket attribueringskrediter som ska tilldelas till varje anpassad fas samt milstolpen [!DNL Marketo Measure]. Användare kan tilldela varje fas ett betyg när de passar, eller referera till [!DNL Marketo Measure] Machine Learning Model som fungerar som en&quot;förslagsmodell&quot; baserad på historiska data.

Det är viktigt att dessa två aspekter av din anpassade modell definieras korrekt och exakt för att säkerställa att [!DNL Marketo Measure] skapar en korrekt anpassad attributmodell.

## Bästa praxis {#best-practice}

Oavsett om du konfigurerar din anpassade modell för första gången eller granskar det som redan har etablerats är det viktigt att tänka på följande bästa praxis.

* Börja enkelt
   * Identifiera de nyckelstadier som du vill lägga till i din anpassade modell som är viktiga för din [!DNL Marketo Measure]-rapportering. Vanligtvis är det här steg som du brukar mäta dig mot eller som du vill få kunskap om
   * Du kan alltid lägga till i din anpassade modell med tiden
* Använd [!DNL Marketo Measure] Machine Learning-modellen
   * Om du har problem med att bestämma procentattribueringsbrytningen kan [!DNL Marketo Measure] Machine Learning-modellen hjälpa dig att fatta välgrundade beslut när du anger din anpassade attributmodell.
   * När du tittar på Machine Learning-modellen återspeglar attribueringsprocenten för varje fas den potentiella effekten av dina marknadsföringssatsningar
      * En högre procentandel innebär att marknadsföringen direkt kan påverka funnel rörelser vid den tidpunkten
      * En lägre attribueringsprocent innebär att det är mindre viktigt för teamet att övervaka stadierna
* Du måste definiera toppen på funnel-stadierna baserat på lead- eller kontaktstadierna, inte tvärs över båda
   * Det innebär att du måste se till att alla personer kommer att passera genom det steget på det relativa objektet
      * Om du till exempel definierar MQL-steget från Lead-objektet måste alla personer gå in i systemet som en lead och markeras som en MQL på sin Lead-post för att [!DNL Marketo Measure] ska kunna återge exakt vilken beröring som var relaterad till leadens övergång till MQL. Om så inte är fallet, och vissa personer går vidare till Kontakt innan de blir MQL som lead, kommer [!DNL Marketo Measure] inte att kunna redovisa detta korrekt i dina Touchpoint-data och vi måste anta att personen redan har MQL. [!DNL Marketo Measure] kan inte ta hänsyn till hoppande scener, så vi kommer att sluta oss till att faserna har passerat även om de inte har det.
* Kontrollera att spårning av fälthistorik är aktiverat för alla fält som används för att definiera anpassade steg som du inkluderar
* Använd inte formelfält för att definiera en anpassad fas
   * Ett booleskt fält är att rekommendera
* Inkludera inte anpassade steg i din anpassade modell som sammanfaller med en [!DNL Marketo Measure]-milstolpe-position (FT, LC, OC, Closed Won/Lost)
   * Om du gör det sker dessa positioner alltid samtidigt och kan orsaka inflaterade attribueringskrediter till delar av din funnel.
* Arbeta i ditt säljteam
   * Genom att lägga dig i teamet som arbetar närmast med stadier och deras innebörd ser du till att du använder rätt stadier och att de är korrekt definierade

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar din anpassade modell minst två gånger per år ser du till att din anpassade attribueringsrapportering är korrekt och tillförlitlig.

Om din anpassade modell använder maskininlärningsmodellen bör du granska dess program inom den anpassade modellen varje kvartal för att se till att din anpassade modell är så aktuell som möjligt.

Andra orsaker till detta kan utlösa en granskning av din anpassade modell är ...

* Omsättning i marknadsföringsteamet
* Alla ändringar i CRM-stegen
* Uppdateringar till er organisation funnel
* Se felaktiga intäktsdata i din [!DNL Marketo Measure]-rapportering när du använder den anpassade modellen
* Se vilka kontaktytor som inte längre är relevanta för er organisation funnel

>[!MORELIKETHIS]
> [Anpassad attributmodell och inställning](/help/advanced-features/custom-attribution-models/custom-attribution-model-and-setup.md)
> [Aktivera spårning av fälthistorik för den anpassade modellen ](/help/advanced-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
> [Maskininlärningsmodell ](/help/advanced-features/custom-attribution-models/machine-learning-model-faq.md)
