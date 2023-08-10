---
unique-page-id: 18874676
description: "[!DNL Marketo Measure] Förklara insikter - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Förklara insikter"
exl-id: d479a15f-4c92-4302-8ce8-6487645012e1
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# [!DNL Marketo Measure] Förklara insikter {#marketo-measure-insights-explained}

Läs mer om [!DNL Marketo Measure] Vyn Insikter i [!DNL Salesforce], inklusive vad de olika ikonerna representerar och hur du använder funktionen. Den här funktionen är mycket användbar när du vill se de första 20 sessionerna för en lead, en kontakt eller ett konto.

När någon spåras av [!DNL Marketo Measure] javascript och fyller i ett formulär på din webbplats, personen blir en ledare i ditt system och vi överför deras digitala marknadsföringsdata till din Salesforce-organisation (SFDC). När det här inträffar visas kontaktpunktsdata som fyllts i i [!DNL Marketo Measure] Avsnittet Lead Insights (en Canvas-app) på Lead/Contact/Opportunity/Account Objects.

Först och främst kommer ni att se hur många sessioner personen har haft på er webbplats i mitten av era insikter. Du kan bläddra bland sessionerna och navigera när du vill.

![](assets/1.png)

Om du klickar på&quot;Alla&quot; i den övre delen av dina insikter kan du se hur alla sessioner har lagts samman. Där kommer du att förstå datumen för de enskilda sessionerna, vilken kanal eller källa som ledde till dem och en uppsättning ikoner som specificerar mer information.

Det första du kommer att se är FT- eller LC-ikonerna. Dessa representerar kontaktpunktspositionen för de listade sessionerna. FT står för First Touch och LC står för Lead Creation. Du kan ha flera sessioner, men bara en kontaktpunkt kan vara FT eller LC. Du hittar aldrig flera FT- eller LC-koder som är kopplade till en person.

Ikonerna som ser ut som papper visar att en sidvy har inträffat under sessionen. Det är troligt att alla sessioner kommer att innehålla den här ikonen.

![](assets/2.png)

Ikonen som ser ut som en bägare signalerar att ett A/B-testexperiment har utförts. Vi integrerar nu med Optimizely och VWO. Med den här integreringen kan vi driva på det experiment och den variation som användaren såg på sitt eget seminarium.

![](assets/3.png)

Om du klickar på en specifik session (du kan göra detta genom att klicka på det faktiska datumet för sessionen eller i den övre mellersta delen av grupperade sessioner) kan du se sessionsinformationen. I varje session ser du alla sidor som användaren såg beställda per datum och tid.

![](assets/4.png)

På höger sida av varje session kan du se mer av de detaljerade marknadsföringsdata som vi går vidare med [!DNL Marketo Measure] fält i SFDC. I det här exemplet kan du se annonsgrupp, annonsinnehåll, kampanj, nyckelord, medel. Du kan även rulla nedåt för att se mer av [!DNL Marketo Measure] data som vi tillhandahåller.

När någon har en mängd sessioner kan du använda vissa filter i [!UICONTROL Insights] för att hitta specifika delar av deras engagemang på er webbplats. Du kan filtrera efter [!UICONTROL Touchpoint Position] till exempel.

Du kan även söka efter sidvyer, AB-tester eller Forms.
