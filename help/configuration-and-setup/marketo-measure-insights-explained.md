---
description: '[!DNL Marketo Measure] Insikter har förklarats - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] insikter har beskrivits'
exl-id: d479a15f-4c92-4302-8ce8-6487645012e1
feature: Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# [!DNL Marketo Measure] insikter har beskrivits {#marketo-measure-insights-explained}

Lär dig mer om vyn [!DNL Marketo Measure] Insights i [!DNL Salesforce], inklusive vad de olika ikonerna representerar och hur du använder funktionen. Den här funktionen är mycket användbar när du vill se de första 20 sessionerna för en lead, en kontakt eller ett konto.

När någon spåras av JavaScript:n [!DNL Marketo Measure] och fyller i ett formulär på webbplatsen blir personen ledande i ditt system och deras digitala marknadsföringsdata skickas till din Salesforce (SFDC)-organisation. När detta inträffar visas kontaktpunktsdata i avsnittet [!DNL Marketo Measure] Leadinsikter (en Canvas-app) på lead-/kontakt-/säljprojektsobjekten.

Först ser du i mitten av dina insikter hur många sessioner personen har haft på din webbplats. Du kan bläddra bland sessionerna och navigera när du vill.

![Först ser du i mitten av dina insikter numret ](assets/marketo-app-1.png)

Om du klickar på&quot;Alla&quot; i den övre delen av dina insikter kan du se hur alla sessioner har lagts samman. Där förstår du datumen för de enskilda sessionerna, vilken kanal eller källa som ledde till dem och en uppsättning ikoner som specificerar mer information.

Det första du ser är FT- eller LC-ikonerna. Dessa representerar kontaktpunktspositionen för de listade sessionerna. FT står för First Touch och LC står för Lead Creation. Du kan ha flera sessioner, men bara en kontaktpunkt kan vara FT eller LC. Du hittar aldrig flera FT- eller LC-koder som är kopplade till en person.

Ikonerna som ser ut som papper visar att en sidvy har inträffat under sessionen. Det är troligt att varje session innehåller den här ikonen.

![Ikonerna som ser ut som papper anger att en sidvy har inträffat](assets/marketo-app-2.png)

Ikonen som ser ut som en bägare signalerar att ett A/B-testexperiment har utförts. Vi integrerar nu med Optimizely och VWO. Med den här integreringen kan vi driva på det experiment och den variation som användaren såg på sitt eget seminarium.

![Ikonen som ser ut som en bägare signalerar att ett A/B-test ](assets/marketo-app-3.png)

Om du klickar på en specifik session (du kan göra detta genom att klicka på det faktiska datumet för sessionen eller i den övre delen av de grupperade sessionerna) kan du se sessionsinformationen. I varje session ser du alla sidor som användaren såg beställda per datum och tid.

![Om du klickar på en specifik session (du kan göra detta genom att klicka på](assets/marketo-app-4.png))

Till höger om varje session kan du se mer av de detaljerade marknadsföringsdata som skjuter upp fälten [!DNL Marketo Measure] i din SFDC. I det här exemplet kan du se annonsgrupp, annonsinnehåll, kampanj, nyckelord, Medium. Du kan även rulla nedåt för att se mer av de [!DNL Marketo Measure]-data vi tillhandahåller.

När någon har en mängd sessioner kan du använda några filter i [!UICONTROL Insights] för att söka efter specifika delar av deras engagemang på din webbplats. Du kan till exempel filtrera efter [!UICONTROL Touchpoint Position].

Du kan även söka efter sidvyer, AB-tester eller Forms.
