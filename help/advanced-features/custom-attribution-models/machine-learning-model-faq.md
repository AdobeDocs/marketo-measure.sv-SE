---
description: Vanliga frågor om maskininlärningsmodellen - [!DNL Marketo Measure]
title: Vanliga frågor om maskininlärningsmodellen
exl-id: 2fc142b2-8ac4-4c48-a8f1-398e29ccfe97
feature: Custom Models
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Vanliga frågor om maskininlärningsmodellen {#machine-learning-model-faq}

Maskininlärningsmodellen [!DNL Marketo Measure] använder dina kontaktpunktsdata för att beräkna hur mycket attribueringsviktning som ska tilldelas varje fas. Detta avgörs av hur viktigt varje fas var för att få avtal att sluta.

Vad säger attribueringsprocenten från Machine Learning Model om varje steg?

Tilldelningsprocenten för varje fas återspeglar den potentiella effekten av era marknadsföringssatsningar. En högre procentandel innebär att marknadsföringen direkt kan påverka funnel rörelser vid den tidpunkten. En lägre attribueringsprocent innebär att faser är mindre viktiga för teamet att övervaka.

Hur beräknas maskininlärningsmodellen?

[!DNL Marketo Measure] beräknar vikten av varje anpassad fas med hjälp av kontaktpunktsdata från ditt konto. De kriterier som används för att fastställa vikten av varje fas är följande:

* Modellprecision: Om vi bygger en prediktiv modell med kontaktpunktsdata för att förutsäga om vi kommer att vinna ett avtal så småningom, hur korrekt kommer modellen att vara? Högre prediktiv precision innebär att detaljerna i det här steget bättre motsvarar om ett avtal kommer att sluta
* Konverteringsgrad: Om leads eller säljprojekt i det här skedet konverteras till nästa steg i hög hastighet tyder detta på att de marknadsföringsaktiviteter som inträffade i det här skedet inte spelade någon särskilt stor roll. Omvänt kan det, om ett visst stadium konverteras till nästa steg i låg takt, tyda på att de marknadsföringsaktiviteter som förekom i det här skedet var avgörande för konverteringsgraden.
* Unikhetsvikt för slutpunkter: Om en scen förekommer som en fristående övergång, vilket innebär att det inte finns några andra scenövergångar som inträffade samtidigt, kan den här scenen få en högre attribueringsvikt. Omvänt, om en kontaktyta för en scen delas med andra faser (t.ex. kontaktytan för första kontakten, leadkonvertering och säljprojektskonvertering) kan den här fasen få en lägre attribueringsvikt.

Slutvikten för ett anpassat stadium beräknas som sådan:

**_Modellprocent = Modellprecision x konverteringsgrad x Unikhetsvikt för pekpunkt_**

I slutet normaliseras alla anpassade scenvikter och konverteras till % enligt nedan.

Varför visas inga siffror i kolumnen Machine Learning?

När Custom Attribution Model är aktiverat för ditt konto tar det i allmänhet mellan 3 och 7 dagar för vår modell att köra och skapa dessa nummer, baserat på dina historiska data.

Hur ofta uppdateras Machine Learning-modellen?

Vi kör om modellen var 7:e dag.

Varför ställs Mellanöstern alltid in på 10 %?

Att tilldela 10 % attribueringskrediter till Middle Touches är en standardinställning för alla våra attribueringsmodeller.

När ska jag ändra min attribueringsfördelning?

Kontakta din kontoansvarige för att diskutera konsekvenserna av att ändra dina attribueringsprocentsatser och vilka faser som ska ingå i din anpassade modell. Varje [!DNL Salesforce] och försäljningsprocess är unik och vi vill försäkra oss om att din anpassade modell är korrekt modellerad.

Med detta sagt har vi identifierat några allmänna trender för våra kunder:

En trend vi har märkt är att det inte alltid är bra att ta med fler faser i modellen. När kunder till exempel har lagt till flera säljprojektsfaser längst ned i funnel tenderar de att få mycket låga procentvärden för attribuering. Låga procentvärden anger en hög konverteringsgrad, vilket vanligtvis innebär att de här stegen inte är lika effektiva när det gäller att driva avtal till avslut. Vissa kunder bestämmer sig slutligen för att inte ta med de här stegen i funnel. Om du bestämmer dig för att ta bort en fas från din attribueringsmodell, kommer datormodellen att beräkna om och omfördela procentsatserna.

Vi har också noterat att det finns en hög konverteringsgrad från Lead Creation till Marketing Qualified och att Marketing Qualified-fasen därför kan få en lägre attribueringsviktning i procent. Beroende på ditt företags- och säljprogram kan det vara bra att ta bort det här steget från den anpassade modellen.

Tänk på att om ni vill spåra marknadsföringsaktiviteter under en viss fas, men inte vill att den här fasen ska ta emot attribueringskrediter, kan ni ta med den här fasen i modellen och tilldela 0 % attribueringskrediter till den fasen.
