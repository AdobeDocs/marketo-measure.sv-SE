---
description: Bästa praxis för anpassad modell - [!DNL Marketo Measure]
title: Bästa praxis för anpassad modell
exl-id: 7c19bb6a-30fc-4cbd-a58e-f20751102afe
feature: Custom Models
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Bästa praxis för anpassad modell {#best-practices-for-custom-model}

## Översikt {#overview}

Förutom [!DNL Marketo Measure] ur förpackningen Attribution Models, Tier 2-kunder och högre har tillgång till en Custom Attribution Model.

The [!DNL Marketo Measure] Med en anpassad attribueringsmodell kan användarna välja vilka milstolppunktspositioner och/eller anpassade stadier som ska ingå i modellen. Dessutom kan användarna styra den procentandel av kredit som tilldelas varje steg i modellen (användarna kan definiera ytterligare upp till sex anpassade steg) eller använda de procentvärden för attribuering som föreslås av [!DNL Marketo Measure] Machine Learning-modell.

Det finns två viktiga aspekter av din anpassade attribueringsmodell:

**Anpassade scener** gör det möjligt för användare att definiera sin kanal i förhållande till sin verksamhet och sina processer. Anpassade etapper bör utgöra&quot;milstolpar&quot; under hela kundresan, ungefär som [!DNL Marketo Measure] milstolpar (First Touch, Lead Creation Touch, Opportunity Creation Touch och Closed Won Touch) finns i resursattribueringsmodellerna. Det är viktigt att dina anpassade faser är korrekt definierade och mappade inom ditt konto för att säkerställa att [!DNL Marketo Measure] spårar scenövergångar korrekt. Detta är för att identifiera vilka kontaktytor som ska kopplas till varje fas och attribuera kreditpoäng på lämpligt sätt. Anpassad Stage-mappning är i princip ett tillägg till standard Stage Mapping och bör följa samma praxis.

>[!NOTE]
>
>Mer information finns i resursen för metodmappning

**Anpassad attributmodellering** definieras när du har valt en anpassad fas-tratt. Användarna kan sedan styra hur mycket attribueringskrediter som ska tilldelas till varje anpassad fas samt [!DNL Marketo Measure] milstolpar. Användarna kan tillskriva varje scen kredit när de passar eller referera till [!DNL Marketo Measure] Maskininlärningsmodell som fungerar som en&quot;förslagsmodell&quot; baserad på historiska data.

Det är viktigt att dessa två aspekter av din anpassade modell definieras korrekt och exakt för att säkerställa att [!DNL Marketo Measure] skapar en korrekt anpassad attributmodell.

## Bästa praxis {#best-practice}

Oavsett om du konfigurerar din anpassade modell för första gången eller granskar det som redan har etablerats är det viktigt att tänka på följande bästa praxis.

* Börja enkelt
   * Identifiera de nyckelstadier som du vill lägga till i din anpassade modell som är viktiga för din [!DNL Marketo Measure] rapportering. Vanligtvis är det här steg som du brukar mäta dig mot eller som du vill få kunskap om
   * Du kan alltid lägga till i din anpassade modell med tiden
* Använd [!DNL Marketo Measure] Maskininlärningsmodell
   * Om du har svårt att bestämma procentattribueringsfördelningen kan du [!DNL Marketo Measure] Maskininlärningsmodellen kan hjälpa dig att fatta välgrundade beslut när du anger din anpassade attributmodell.
   * När du tittar på Machine Learning-modellen återspeglar attribueringsprocenten för varje fas den potentiella effekten av dina marknadsföringssatsningar
      * En högre procentandel innebär att marknadsföring direkt kan påverka trattens rörelse vid den tidpunkten
      * En lägre attribueringsprocent innebär att det är mindre viktigt för teamet att övervaka stadierna
* Du måste definiera de övre trattfaserna baserat på antingen lead- eller kontaktfaserna, inte på båda
   * Det innebär att du måste se till att alla personer kommer att passera genom det steget på det relativa objektet
      * Om du till exempel definierar MQL-steget från Lead-objektet måste alla personer gå in i systemet som en lead och markeras som en MQL på sin lead-post för att [!DNL Marketo Measure] för att exakt ta reda på vilken beröring som var kopplad till leadens övergång till MQL. Om så inte är fallet, och vissa personer går vidare till Kontakt innan de blir MQL som lead, [!DNL Marketo Measure] kommer inte att kunna redovisa detta korrekt i dina Touchpoint-data och vi måste anta att personen redan har MQL. [!DNL Marketo Measure] kan inte ta hänsyn till scenhoppen så vi kommer att sluta oss till att faserna har passerat även om de inte har det.
* Kontrollera att spårning av fälthistorik är aktiverat för alla fält som används för att definiera anpassade steg som du inkluderar
* Använd inte formelfält för att definiera en anpassad fas
   * Ett booleskt fält är att rekommendera
* Inkludera inte anpassade steg i din anpassade modell som sammanfaller med en [!DNL Marketo Measure] Pekpunktsposition för milstolpe (FT, LC, OC, Closed Won/Lost)
   * Om du gör det sker dessa positioner alltid samtidigt och kan orsaka inflaterad attribueringskrediter till delar av tratten.
* Arbeta i ditt säljteam
   * Genom att lägga dig i teamet som arbetar närmast med stadier och deras innebörd ser du till att du använder rätt stadier och att de är korrekt definierade

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar din anpassade modell minst två gånger per år ser du till att din anpassade attribueringsrapportering är korrekt och tillförlitlig.

Om din anpassade modell använder maskininlärningsmodellen bör du granska dess program inom den anpassade modellen varje kvartal för att se till att din anpassade modell är så aktuell som möjligt.

Andra orsaker till detta kan utlösa en granskning av din anpassade modell är ...

* Omsättning i marknadsföringsteamet
* Alla ändringar i CRM-stegen
* Uppdateringar av er organisationstrå
* Se felaktiga intäktsdata i [!DNL Marketo Measure] rapportera när den anpassade modellen används
* Se hur kontaktpunktspositioner som inte längre är relevanta för er organisationstrå visas

>[!MORELIKETHIS]
>
>* [Anpassad attributmodell och inställningar](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md)
>* [Aktivera spårning av fälthistorik för anpassad modell](/help/advanced-marketo-measure-features/custom-attribution-models/custom-model-setup-enable-field-history-tracking.md)
>* [Maskininlärningsmodell](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md)
