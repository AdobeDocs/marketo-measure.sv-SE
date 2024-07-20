---
unique-page-id: 18874582
description: "[!DNL Marketo Measure] Salesforce-objekt - [!DNL Marketo Measure]"
title: '[!DNL Marketo Measure] Salesforce-objekt'
exl-id: d5d6f334-6531-40fa-b043-75b49d8f43d5
feature: Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---

# [!DNL Marketo Measure] Salesforce-objekt {#marketo-measure-salesforce-objects}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När [!DNL Marketo Measure] installeras i [!DNL Salesforce] (SFDC) läggs flera anpassade [!DNL Marketo Measure] objekt till. I den här artikeln beskrivs flera av de anpassade [!DNL Marketo Measure]-objekten. Vissa objekt som [!DNL Marketo Measure] lägger till i [!DNL Salesforce] är:

* [Buyer Touchpoint](#touchpoint)
* [Buyer Attribution Touchpoint](#attribution)
* [[!DNL Marketo Measure] person](#person)
* [[!DNL Marketo Measure] A/B-tester](#ab)
* [[!DNL Marketo Measure] händelser](#events)

Kontaktpunkter som fångas av de saker som du vill spåra skrivs till de anpassade objekt som skapas vid installationen av paketet [!DNL Bizible Salesforce].

[!DNL Marketo Measure] objekt relaterar till specifika [!DNL Salesforce] standardobjekt. Detta gör att du kan rapportera [!DNL Marketo Measure] och [!DNL Salesforce] objekt tillsammans. Tabellen nedan visar vilket [!DNL Salesforce]-objekt som [!DNL Marketo Measure]-objektet är relaterat till.

![](assets/1-1.png)

## Buyer Touchpoint {#buyer-touchpoint}

Objektet [!UICONTROL Buyer Touchpoint] (BT) berättar om en individs marknadsföring. Den innehåller alla data som rör de kontaktytor för marknadsföring som genereras av leads och kontakter. BT visar er information om vilken marknadsföringskanal kontaktytan kom från, eller vilken annonskampanj som förde just denna lead/kontakt till er webbplats.

Det BT objektet visas på Leads- och Kontaktsidor som en **Relaterad lista** (se bilden nedan).

![](assets/2-1.png)

I BT relaterade lista visas alla kontaktytor som tillhör lead eller kontakt. I listan finns anpassade [!DNL Marketo Measure] fält som ger mer information om varje kontaktyta. Om du klickar på Buyer Touchpoint ID-numret dirigeras du till Buyer Touchpoint-informationssidan, som innehåller ännu mer information om kontaktytan, som den första webbsidan som den lead/kontakt som besöktes under den webbsessionen (**landningssida**).

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

Objektet [!UICONTROL Buyer Attribution Touchpoint] berättar om marknadsföringsinteraktionerna för dina kontakter som rör en affärsmöjlighet. Den visar *attribueringsdata* som är relaterade till marknadsföringens kontaktytor. Med det här objektet kan du se hur stor intäktskrediten som tillskrivs varje marknadsföringskontaktyta. Den typ av attribueringsmodell som du använder avgör hur stor procentandel av intäkterna som tilldelas kontaktytorna.

Kontaktpunkter för Buyer Attribution (BAT) skapas endast när en möjlighet skapas som relaterar till kontakter som har Buyer Touchpoint (BT)-data. BAT skapas inte utan en möjlighet. När affärsmöjligheten har skapats använder det BAT objektet fältet [!DNL Salesforce] *Belopp* i affärsmöjligheten för att förstå hur mycket intäkt som ska tilldelas kontaktytorna.

Ett **arbetsflöde** måste skapas om du använder ett [anpassat beloppsfält](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md) för att visa intäkter för säljprojektsobjektet. [!DNL Marketo Measure] kan inte läsa informationen som finns i anpassade beloppsfält och kan därför inte fylla i intäktsattribueringsdata på kontaktytorna. I det här arbetsflödet används fältet **[!DNL Marketo Measure]för säljprojektsbelopp**, ett av de [!DNL Marketo Measure] anpassade fälten, för att mappa intäktsvärdet från det anpassade beloppsfältet till fältet Affärsmöjlighet.

![](assets/3-1.png)

Det BAT objektet är synligt på objektet [!UICONTROL Opportunity], [!UICONTROL Contact] och [!UICONTROL Account] som en relaterad lista. I den här listan visas alla kontaktytor med attribueringsdata som hör till ett säljprojekt. Om du klickar på Buyer Attribution Touchpoint-id:t dirigeras du till Buyer Attribution Touchpoint-informationssidan. Här kan du se mer specifika attribueringsdata och information om varifrån kontaktytan kommer (som i Buyer Touchpoint Object).

## [!DNL Marketo Measure] person {#marketo-measure-person}

Personobjektet [!DNL Marketo Measure] relaterar lead- och kontaktobjekten tillsammans. Som standard har Salesforce inte möjlighet att skapa rapporter med hjälp av Lead- och Contact-objektet i samma rapport. Genom att relatera till lead- och kontaktobjektet kan du med hjälp av personen [!DNL Marketo Measure] rapportera om båda objekten i samma rapport. Detta är särskilt användbart när en lead har konverterats till en kontakt. På en [!DNL Marketo Measure]-personpost ser du en sökning efter motsvarande lead- och/eller kontaktpost, en relaterad lista över de kontaktpunkter som är kopplade till personen och person-ID (som alltid är e-postadressen för lead/kontakt). Eftersom personen [!DNL Marketo Measure] relaterar till lead- och kontaktobjektet finns det aldrig någon [!DNL Marketo Measure]-personpost som är kopplad till en Buyer Attribution Touchpoint. Nedan visas ett exempel på en [!DNL Marketo Measure]-personpost i Salesforce:

![](assets/4.png)

## [!DNL Marketo Measure] A/B-test {#marketo-measure-a-b-test}

Om du kör A/B-tester via [!DNL Optimizely] eller VWO (Visual Web Optimizer) kan du ansluta dessa konton till ditt [!DNL Marketo Measure]-konto för att visa A/B-testdata i Salesforce. I A/B-testobjektet [!DNL Marketo Measure] kan du ta A/B-testdata från Optimizely/VWO och koppla data till Leads och Contacts.

![](assets/5.png)

A/B-testobjektet [!DNL Marketo Measure] visas som en relaterad lista på [!UICONTROL Leads]-, [!UICONTROL Contacts]- och [!UICONTROL Opportunity]-sidor. Listan innehåller alla experiment och variationer som du kör via Optimizely eller VWO, och gör att du kan se experiment/variationer när de gäller specifika leads och kontakter.

## [!DNL Marketo Measure] händelser {#marketo-measure-events}

Med händelseobjektet [!DNL Marketo Measure] kan du spåra specifika händelser som inträffar på webbplatsen. Om du vill spåra specifika händelser som inträffar på webbplatsen måste du lägga till anpassad kod på sidorna utöver JavaScript-skriptet [!DNL Marketo Measure]. Den hämtade informationen visas i den [!DNL Marketo Measure] objektrelaterade listan, som finns på sidorna [!UICONTROL Leads], [!UICONTROL Contacts] och [!UICONTROL Opportunity]. [!DNL Marketo Measure]-händelseobjektet *kopplar inte* till attribueringsdata. Syftet med det här objektet är att se om personer vidtar specifika åtgärder på din webbplats.

## [!DNL Marketo Measure] fält {#marketo-measure-fields}

Data som hämtas av JavaScript [!DNL Marketo Measure] överförs till de anpassade [!DNL Marketo Measure] fälten i [!DNL Marketo Measure]-objekten. Vissa fält finns bara på vissa objekt. Du kan granska [ordlistan för [[!DNL Marketo Measure] fält]](/help/introduction-to-marketo-measure/overview-resources/glossary-of-marketo-measure-fields.md) och en [visualisering av de relaterade  [!DNL Marketo Measure] objekten](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-object-and-field-taxonomy.md).

## [!DNL Marketo Measure] rapporter och instrumentpaneler {#marketo-measure-reports-and-dashboards}

[!DNL Marketo Measure]-rapporter och instrumentpaneler som läggs till i [!DNL Salesforce] ger dig färdiga funktioner för rapportering och datavisualisering. Det här är grundläggande [!DNL Marketo Measure]-rapporter som gör att du snabbt kan ordna, analysera och förstå kontaktpunktsdata.
