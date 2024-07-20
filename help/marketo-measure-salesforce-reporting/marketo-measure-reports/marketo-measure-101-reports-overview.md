---
description: "[!DNL Marketo Measure] 101 Rapporter - översikt - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] 101 Rapporter - översikt"
exl-id: 83977b81-8055-47fd-8a6b-5ef32d280269
feature: Reporting
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# [!DNL Marketo Measure] 101 rapportöversikt {#marketo-measure-101-reports-overview}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Alla [!DNL Marketo Measure]-kunder som använder [!DNL Marketo Measure] och [!DNL Salesforce] har tillgång till mappen Buyer Touchpoints Reports i sin SFDC-instans. Den här mappen innehåller ett antal färdiga rapporter som hjälper dig att komma igång med att rapportera Buyer Touchpoint-data.

![](assets/bizible-101-reports-overview-1.png)

Många av dessa rapporter har redan specifika rapporteringsmål, men det finns sex _[!DNL Marketo Measure]101.._ som representeras av tre viktiga rapporttyper som täcker de flesta rapporteringsbehov.

* Leads med Buyer Touchpoints
* [!DNL Marketo Measure] personer med Buyer Touchpoints
* Kontaktpunkter för Buyer Attribution med möjlighet

![](assets/bizible-101-reports-overview-2.png)

Dessa rapporter ger dig grundläggande fält och den infrastruktur som behövs för alla [!DNL Marketo Measure]-relaterade rapporter som du vill skapa. Vi uppmuntrar alla nya och gamla kunder att börja med dessa rapporter när de utforskar marknadsattribueringsfrågor. Här nedan hittar du en förklaring till de sex _[!DNL Marketo Measure]101..._-rapporterna.

_Om du inte hittar mappen Buyer Touchpoints Report eller de sex_[!DNL Marketo Measure] 101.._-rapporterna i den mappen kan du få hjälp av dem._

**Leads med Buyer Touchpoints** | I följande två varianter kan du rapportera om Leads och deras Buyer Touchpoints. Även om de använder samma grundläggande rapporttyp grupperas de efter olika värden, Lead ID och Marketing Channel, för att ge två huvudvyer av data. Den här rapporttypen är utformad för trattrapportering och är idealisk när du vill utforska hur ledande företag engagerar sig i marknadsföringssatsningarna. Före varje anpassning visas följande två rapporter:

**[!DNL Marketo Measure]101: Leads efter kanal** | En högnivåvy över hur era marknadsföringskanaler påverkar skapandet av leads och deras ytterligare engagemang.
**[!DNL Marketo Measure]101: Leads efter ID** | Det här visar artikeln om leads och är en mycket mer detaljerad rapport som visar varje enskild lead och deras relaterade Buyer Touchpoints.

**Leads/kontakter med Buyer Touchpoints** | Dessa rapporter kallas ofta [!DNL Marketo Measure] rapporten People. De använder det [!DNL Marketo Measure] anpassade objektet _[!DNL Marketo Measure]Person_ i motsats till Lead-objektet i de rapporter som nämns ovan.

Personobjektet [!DNL Marketo Measure] relaterar lead- och kontaktobjekten tillsammans. Efter att ha angetts har [!DNL Salesforce] inte möjlighet att skapa rapporter med lead- och kontaktobjektet i samma rapport. Genom att relatera till lead- och kontaktobjektet med hjälp av en persons unika identifierare, deras e-postadress, kan personen [!DNL Marketo Measure] rapportera om både lead- och kontaktrelaterade köparkontaktytor i samma rapport. Den här rapporttypen är idealisk när du vill validera kontoinställningarna för [!DNL Marketo Measure] eftersom det är den mest omfattande nivån för kontaktytpunktsrapportering.

I följande två rapportvarianter används samma rapporttyp, men de grupperas efter olika mått, person-ID (e-post) och marknadsföringskanal. Det här är de viktigaste trattrapporterna/trattrapporterna som är bra att ta reda på hur era leads och kontakter engagerar er marknadsföring. Före varje anpassning visas följande två rapporter:

**[!DNL Marketo Measure]101: Lead/kontakter efter kanal** | En högnivåvy över hur era marknadsföringskanaler påverkar skapandet av leads eller kontakter och deras ytterligare engagemang. Den här rapporten är perfekt när du vill förstå det totala engagemanget i alla era marknadsföringskanaler och vilka marknadsföringskanaler som genererar nya nettonamn i Salesforce-instansen.
**[!DNL Marketo Measure]101: Lead/kontakter efter ID** | Detta visar varje persons berättelse för [!DNL Marketo Measure] och är en mycket mer detaljerad rapport som visar varje individ och deras Buyer Touchpoints, oavsett om kontaktytan inträffade som lead eller kontakt.

**Affärsmöjligheter med slutpunkter för inköpsattribuering** | De två sista _[!DNL Marketo Measure]101..._-rapporterna är längst ned i trattrapporterna som visar Buyer Attribution Touchpoint-data för säljprojekt. Den viktigaste skillnaden för de här rapporterna är att de är inbyggda i _Slutpunkter för kundattribut_ som relaterar till data på säljprojektsnivå och säljprojektsnivå, t.ex. intäkter. Varje gång du vill rapportera om säljprojekt eller tilldelade intäkter ska den här rapporttypen användas. De två rapporterna nedan använder samma rapporttyp, men de grupperas efter olika värden, säljprojekt-ID:t och marknadsföringskanal. Före varje anpassning visas följande två rapporter:

**[!DNL Marketo Measure]101: Möjligheter efter kanal** | En högnivåvy över hur era marknadsföringskanaler påverkar och ökar de tilldelade intäkterna i era affärsmöjligheter.
**[!DNL Marketo Measure]101: Möjligheter efter ID** | Den här detaljerade rapportversionen visar er hela vägen till era affärsmöjligheter. I den här rapporten kan du se alla Buyer Attribution Touchpoint som är kopplade till ett säljprojekt och dess tillskrivna intäkter genom de olika attribueringsmodellerna.

Det anses vara en god praxis att behandla _[!DNL Marketo Measure]101..._-rapporterna som mallar för dina rapporteringsbehov. Om du börjar med en av rapporterna ovan sparar du tid och ser till att du arbetar med rätt fält för [!DNL Marketo Measure]-data. Se alltid till att du alltid väljer Spara som när du gör anpassningar av mallarna _[!DNL Marketo Measure]101..._ för att behålla den ursprungliga varianten av rapporten.

Mappen&quot;Buyer Touchpoint Reports&quot; är utformad för att hjälpa dig att komma igång med din [!DNL Marketo Measure]-rapportering. För åtgärdbara rapporter måste du anpassa rapporterna så att de är anpassade efter dina rapporteringsbehov. måste du lägga till de filter som behövs för att säkerställa att posterna i rapporten (och deras relaterade kontaktytor) är anpassade efter rapportens mål.

När du är bekant med _[!DNL Marketo Measure]101.._-rapporterna kanske du vill återskapa dem från anpassade rapporttyper för mer anpassade rapporteringsbehov. Om du skapar de [[!DNL Marketo Measure] anpassade rapporttyperna](/help/marketo-measure-salesforce-reporting/new-report-types/creating-custom-marketo-measure-report-types.md) kan du hämta in anpassade fält som du vanligtvis använder i andra CRM-rapporter. Detta hjälper dig att ta [!DNL Marketo Measure]-rapportering till nästa nivå!
