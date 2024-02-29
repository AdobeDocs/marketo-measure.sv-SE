---
unique-page-id: 18874582
description: "[!DNL Marketo Measure] Salesforce-objekt - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Salesforce-objekt"
exl-id: d5d6f334-6531-40fa-b043-75b49d8f43d5
feature: Salesforce
source-git-commit: 289c40a07c60ccc0262e2aaf95f21fca0c945b11
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# [!DNL Marketo Measure] Salesforce-objekt {#marketo-measure-salesforce-objects}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När [!DNL Marketo Measure] är installerat i [!DNL Salesforce] (SFDC), flera anpassade [!DNL Marketo Measure] Objekt läggs till. Den här artikeln innehåller en förklaring till flera av de anpassade [!DNL Marketo Measure] Objekt. Vissa objekt som [!DNL Marketo Measure] lägger till i [!DNL Salesforce] är:

* [Kontaktpunkt för köpare](#touchpoint)
* [Buyer Attribution Touchpoint](#attribution)
* [[!DNL Marketo Measure] Person](#person)
* [[!DNL Marketo Measure] A/B-testning](#ab)
* [[!DNL Marketo Measure] Händelser](#events)

Kontaktpunkter som fångats av det du vill spåra skrivs till de anpassade objekt som skapas vid installationen av [!DNL Bizible Salesforce] paket.

[!DNL Marketo Measure] Objekt relaterar till specifik standard [!DNL Salesforce] Objekt. Detta gör att du kan rapportera om [!DNL Marketo Measure] och [!DNL Salesforce] Objekt tillsammans. Tabellen nedan visar vilka [!DNL Salesforce] Objektet [!DNL Marketo Measure] Objektet är relaterat till.

![](assets/1-1.png)

## Kontaktpunkt för köpare {#buyer-touchpoint}

The [!UICONTROL Buyer Touchpoint] (BT) Object berättar om en individs marknadsföring. Den innehåller alla data som rör de kontaktytor för marknadsföring som genereras av leads och kontakter. BT visar er information om vilken marknadsföringskanal kontaktytan kom från, eller vilken annonskampanj som förde just denna lead/kontakt till er webbplats.

BT-objektet är synligt på Leads- och Kontaktsidor som en **Relaterad lista** (se bilden nedan).

![](assets/2-1.png)

Den BT-relaterade listan visar alla kontaktytor som tillhör lead eller kontakt. Inom listan är de anpassade [!DNL Marketo Measure] Fält som innehåller mer information om varje kontaktyta. Om du klickar på Buyer Touchpoint ID-numret dirigeras du till sidan Buyer Touchpoint Detail, som innehåller ännu mer information om kontaktytan, som den första webbsidan som Lead/Contact besökte under webbsessionen (**landningssida**).

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

The [!UICONTROL Buyer Attribution Touchpoint] Objektet berättar om marknadsföringsinteraktionerna för dina kontakter i samband med en affärsmöjlighet. Den visar *attribuering* data relaterade till kontaktytorna. Med det här objektet kan du se hur stor intäktskrediten som tillskrivs varje marknadsföringskontaktyta. Den typ av attribueringsmodell som du använder avgör hur stor procentandel av intäkterna som tilldelas kontaktytorna.

Kontaktpunkter för Buyer Attribution (BAT) skapas först när en möjlighet skapas som relaterar till kontakter som har BT-data (Buyer Touchpoint). Bästa tillgängliga teknik skapas inte utan möjlighet. När affärsmöjligheten har skapats använder BAT-objektet [!DNL Salesforce] *Belopp* fält i säljprojektet för att förstå hur mycket intäkter som ska tilldelas kontaktytorna.

A **arbetsflöde** måste skapas om du använder en [anpassat beloppsfält](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) om du vill visa intäkter för objektet säljprojekt. [!DNL Marketo Measure] kan inte läsa informationen som finns i anpassade beloppsfält och kan därför inte fylla i intäktsattribueringsdata på kontaktytorna. Det här arbetsflödet använder **[!DNL Marketo Measure]Affärsmöjlighet - belopp** Fält, en av [!DNL Marketo Measure] anpassade fält, för att mappa intäktsvärdet från fältet Anpassat belopp till fältet Affärsmöjlighet.

![](assets/3-1.png)

BAT-objektet visas på [!UICONTROL Opportunity], [!UICONTROL Contact]och [!UICONTROL Account] Objekt som en relaterad lista. I den här listan visas alla kontaktytor med attribueringsdata som hör till ett säljprojekt. Om du klickar på Buyer Attribution Touchpoint ID dirigeras du till sidan Buyer Attribution Touchpoint Detail. Här kan du se mer specifika attribueringsdata och information om varifrån kontaktytan kommer (liknande vad som anges i Buyer Touchpoint-objektet).

## [!DNL Marketo Measure] Person {#marketo-measure-person}

The [!DNL Marketo Measure] Personobjektet relaterar lead- och kontaktobjekten tillsammans. Som standard har Salesforce inte möjlighet att skapa rapporter med hjälp av Lead- och Contact-objektet i samma rapport. Genom att relatera till lead- och kontaktobjektet kan du [!DNL Marketo Measure] Du kan rapportera om båda objekten i samma rapport. Detta är särskilt användbart när en lead har konverterats till en kontakt. På en [!DNL Marketo Measure] Personpost du vill visa en sökning efter motsvarande lead- och/eller kontaktpost, en relaterad lista över de kontaktpunkter som är kopplade till personen och person-ID (som alltid är leadets/kontaktpersonens e-postadress). Sedan [!DNL Marketo Measure] Personen relaterar till lead- och kontaktobjektet, det finns aldrig någon [!DNL Marketo Measure] Personpost som är kopplad till en kontaktyta för Buyer Attribution. Nedan visas ett exempel på en [!DNL Marketo Measure] Personpost i Salesforce:

![](assets/4.png)

## [!DNL Marketo Measure] A/B-test {#marketo-measure-a-b-test}

Om du kör A/B-tester via [!DNL Optimizely] eller VWO (Visual Web Optimizer) kan du ansluta dessa konton till [!DNL Marketo Measure] konto för att visa A/B-testdata i Salesforce. The [!DNL Marketo Measure] A/B Test Object gör det möjligt att ta A/B-testdata från Optimizely/VWO och knyta data till Leads och Contacts.

![](assets/5.png)

The [!DNL Marketo Measure] A/B-testobjekt visas som en relaterad lista på [!UICONTROL Leads], [!UICONTROL Contacts] och [!UICONTROL Opportunity] sidor. I listan visas alla experiment och variationer som du kör med Optimal eller VWO, och du kan se experiment/variationer när de gäller specifika leads och kontakter.

## [!DNL Marketo Measure] Händelser {#marketo-measure-events}

The [!DNL Marketo Measure] Med händelseobjektet kan du spåra specifika händelser som inträffar på webbplatsen. Om du vill spåra specifika händelser som inträffar på webbplatsen måste du lägga till egen kod på sidorna utöver [!DNL Marketo Measure] Javascript. Den hämtade informationen visas i [!DNL Marketo Measure] Objektrelaterad lista som finns på [!UICONTROL Leads], [!UICONTROL Contacts] och [!UICONTROL Opportunity] sidor. The [!DNL Marketo Measure] Händelseobjekt *inte* koppla till attribueringsdata. Syftet med det här objektet är att se om personer vidtar specifika åtgärder på din webbplats.

## [!DNL Marketo Measure] Fält {#marketo-measure-fields}

Data som samlats in av [!DNL Marketo Measure] JavaScript överförs till den anpassade [!DNL Marketo Measure] Fält i [!DNL Marketo Measure] Objekt. Vissa fält finns bara på vissa objekt. Du kan granska [ordlista för [[!DNL Marketo Measure] fält]](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md) och [visualisering av den relaterade [!DNL Marketo Measure] Objekt](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

## [!DNL Marketo Measure] Rapporter och kontrollpaneler {#marketo-measure-reports-and-dashboards}

The [!DNL Marketo Measure] Rapporter och instrumentpaneler som läggs till i dina [!DNL Salesforce] ger dig färdiga funktioner för rapportering och datavisualisering. Dessa är grundläggande [!DNL Marketo Measure] rapporter så att ni snabbt kan ordna, analysera och förstå kontaktpunktsdata.
