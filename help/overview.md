---
description: '[!DNL Marketo Measure] Ultimate - översikt - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Ultimate - översikt'
exl-id: fada9479-0671-4698-8043-c67d7977577b
feature: Integration, Tracking, Attribution
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---

# [!DNL Marketo Measure] Ultimate - översikt {#marketo-measure-ultimate-overview}

[!DNL Marketo Measure] (tidigare Bizible) ger marknadsförarna insikt i vilka marknadsföringssatsningar som är mest effektiva när det gäller att öka intäkterna och maximera avkastningen på investeringen för deras företag. [!DNL Marketo Measure] är en marknadsföringsattribueringslösning som automatiskt spårar och rapporterar kanalernas prestanda, vilket ger synlighet i vilka kanaler som ökar kundengagemanget och gör att ni kan optimera era era marknadsföringsutgifter i enlighet med detta.

[!DNL Marketo Measure Ultimate] innehåller ytterligare funktioner:

* Hämta in alla data för attribuering genom att hämta in data från nästan vilken datakälla som helst och från flera datakällor av samma typ.
   * Använd med nästan alla CRM-system, inte bara Salesforce och Dynamics.
   * Anslut flera CRM-instanser och/eller MAP-instanser till en [!DNL Marketo Measure]-instans.
   * Hämta in registrerings- och deltagardata för webbinarium från tredje part.

* Omvandla era data mycket flexibelt med hjälp av fältmappning och omvandlingsfunktioner för att säkerställa rätt dataform.

* Gör attribueringsinsikter tillgängliga för externa program via det medföljande datalagret för att integrera insikterna i arbetsflödet. Mer detaljerade resultatdata och BI-baserad rapportering, inklusive Snowflake Data Warehouse, som ger tillgång till detaljerade resultatdata och möjlighet att använda alla BI-verktyg för analys och rapportering.

* Integrering med RTCDP (B2B eller B2P Edition), som ger en integrerad B2B-attribueringslösning för RTCDP-kunder som RTCDP och [!DNL Marketo Measure] fungerar båda utifrån centraliserade Adobe Experience Platform-data (AEP).

**[!DNL Marketo Measure]Tiers 1-3**

![Marketo Measure Tiers 1-3](assets/marketo-overview-1.png)

**[!DNL Marketo Measure Ultimate]**

![Marketo Measure Ultimate](assets/marketo-overview-3.png)

## Nyheter i [!DNL Marketo Measure Ultimate] {#whats-new-in-marketo-measure-ultimate}

**Importera B2B-data via AEP**

Marknadsförarna förväntas hämta sina B2B-data (till exempel konto, säljprojekt, kontakt, lead, kampanj, kampanjmedlem, aktivitet) via AEP. De direkta CRM- och Marketo Engage-anslutningarna är inte längre tillgängliga för Ultimate. Marknadsförarna fortsätter att föra över Ad Platform-data via direkta anslutningar och spåra webbaktiviteter via [!DNL Marketo Measure] javascript.

![Marknadsförarna förväntas ta med sina B2B-data (till exempel Konto, Möjlighet,](assets/marketo-overview-2.png))

**Standardinställning för valuta**

[!DNL Marketo Measure Ultimate] anger standardvalutan till USD tills användaren ändrar den. Om du anger en ny standardvaluta uppdateras data utan ombearbetning. Så länge den valda valutan finns som mål-ISO-kod behöver du inte skicka konverteringsgrader.

![Marketo Measure Ultimate ställer in standardvalutan till USD fram till &#x200B;](assets/marketo-overview-7.png)

**[!DNL Marketo Measure Ultimate]Sandbox**

[!DNL Marketo Measure Ultimate]-instansen måste mappas till en AEP-sandlåda innan [!DNL Marketo Measure]-måldataflödena i AEP kan skapas.

>[!NOTE]
>
>En [!DNL Marketo Measure Ultimate]-produktionsinstans måste mappas till en AEP-produktionssandlåda. En [!DNL Marketo Measure Ultimate]-utvecklarinstans måste mappas till en AEP-utvecklarsandlåda.

När markeringen för sandlådemappning har sparats kan du inte ändra den i programmet. Om du vill ändra den kontaktar du [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

Data för en given entitet (till exempel Konto) från en viss datakälla kan bara gå till en datamängd. Varje datauppsättning kan bara inkluderas i ett dataflöde. Överträdelser stoppar dataflödet vid körning.

![Data för en angiven entitet (till exempel Konto) från angivna data](assets/marketo-overview-6.png)

**Stage Mapping**

Alla [!DNL Marketo Measure Ultimate]-regler är datauppsättningsspecifika. Regler för Stage Mapping måste skapas för alla datamängder och alla markerade steg.

Det finns sex inbyggda faser:

* Lead förlorad
* Öppna lead
* Konverterad lead
* Förlorade affärsmöjligheter
* Öppen affärsmöjlighet
* Vunnen affärsmöjlighet

Avsnitten Förlorad, Vunn och Konverterad tillåter inte anpassade stadier. Source-data kan dock mappas till de inbyggda faserna Förlorad/Vunnen/Konverterad genom att mappningsregeln uppdateras.

Anpassade steg kan bara definieras för Öppna-avsnitt.
CRM-faser inkluderas inte längre automatiskt i scenmappningen.

Fyra inbyggda steg måste mappas med regler (mappningsregler för de andra två, Lead Lost och Lead Converted, är valfria):

* Öppna lead
* Förlorade affärsmöjligheter
* Öppen affärsmöjlighet
* Vunnen affärsmöjlighet

Regelvillkoren är datauppsättningsspecifika. Stage Mapping-regler måste skapas för alla datauppsättningar och alla faser utom Lead Lost och Lead Converted.

Inget val för funnel jämfört med boomerang jämfört med anpassad modell. Alla faser väljs för funnel, boomerang och anpassad modell. Det finns en gräns för hur många steg vi stöder: 15 anpassade plus 6 inbyggda steg.

![Inget val för funnel jämfört med boomerang jämfört med anpassad modell. Alla faser är &#x200B;](assets/marketo-overview-4.png)

Kontaktpunktsregler för kampanjmedlemmar och Touchpoint-regler för aktivitet är datauppsättningsspecifika.

![Kontaktpunktsregler för kampanjmedlem och Touchpoint-regler för aktivitet är datauppsättningsspecifika.](assets/marketo-overview-5.png)

![Kontaktpunktsregler för kampanjmedlem och Touchpoint-regler för aktivitet är datauppsättningsspecifika.](assets/marketo-overview-8.png)

Attribution Touchpoints skrivs inte till CRM eftersom Ultimate inte har någon direkt CRM-anslutning.

[!DNL Marketo Measure] ABM ML-tjänster (Lead-to-Account Matching och Predictive Engagement Score) är inte tillgängliga för [!DNL Marketo Measure Ultimate]. Dessa tjänster ingår kostnadsfritt i RT-CDP B2B edition.

## Begränsningar {#limitations}

* Begränsade fält är tillgängliga för dataomvandlingsregler.
* Det finns ingen migreringsväg för befintliga Tier 1/2/3-användare. Kräver en ny implementering, men vi hjälper dig att migrera spårade webbaktivitetsdata från den befintliga instansen.

>[!MORELIKETHIS]
>
>* [Marketo Measure Ultimate-mål](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/adobe/marketo-measure-ultimate.html?lang=en){target="_blank"}
>
>* [VIDEO: Marketo Measure Ultimate - översikt](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/marketo-measure-ultimate/overview){target="_blank"}
