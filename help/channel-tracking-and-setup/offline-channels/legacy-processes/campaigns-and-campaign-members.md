---
unique-page-id: 18874578
description: Kampanjmedlemmar och kampanjmedlemmar - [!DNL Marketo Measure] - Produktdokumentation
title: Kampanjmedlemmar och kampanjmedlemmar
exl-id: e4e2b154-39ac-4295-a541-7fa6112672e3
feature: Channels
source-git-commit: 38c721d10ac33ae85da1d425b6af53b9e3dfd0a1
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 0%

---

# Kampanjmedlemmar och kampanjmedlemmar {#campaigns-and-campaign-members}

[!DNL Salesforce] Kampanjer är avsedda att spåra listor med leads och kontakter som är kopplade till ett marknadsföringsprogram eller en aktivitet. Detta har till exempel varit webbinarier, registreringar eller besök. Marknadsförarna kan välja om en Campaign ska tillskrivas en kontaktyta eller inte.

>[!NOTE]
>
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användarna att använda [ny, förbättrad process i appen](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Aktivera kontaktpunkter {#enabling-touchpoints}

The [!DNL Marketo Measure] [!DNL Salesforce] Paketet kommer att innehålla ett fält med namnet&quot;Enable Buyer Touchpoints&quot; i Campaign-objektet. När fältet har lagts till i sidlayouten ser det ut ungefär så här:

![](assets/1.png)

Tillgängliga alternativ i plocklistan är:

![](assets/2.png)

* Inkludera alla kampanjmedlemmar - Varje enskild lead eller kontakt som läggs till i kampanjen får en kontaktyta som är kopplad till kampanjen.
* Inkludera endast responderade kampanjmedlemmar - Endast leads eller kontakter som har kampanjmedlemmens status&quot;Responded&quot; får en kontaktyta kopplad till kampanjen.
* Uteslut alla kampanjmedlemmar - Ingen av leads eller kontakter får en kontaktyta som är kopplad till kampanjen.

Observera att kampanjmedlemmarna måste ha en e-postadress kopplad till sin post för att [!DNL Marketo Measure] för att skapa en kontaktyta. Utan e-postadress [!DNL Marketo Measure] tilldelar inte någon kontaktyta till kampanjmedlemmen.

## Synkroniseringsdatum för kampanj {#campaign-sync-dates}

När paketet installeras [!DNL Marketo Measure] innehåller även två datumfält i Campaign-objektet: Startdatum för pekpunkt och Slutdatum för slutpunkt.

Dessa datum talar om [!DNL Marketo Measure] när vi ska påbörja eller sluta inkludera Campaign-medlemmar från Campaign i kontaktytan. Du kan antingen ange ett datum, eller båda, eller ingen alls.

## Använd skiftläge för slutpunktens startdatum {#use-case-for-touchpoint-start-date}

Startdatum kan användas om en befintlig kampanj används för att spåra leads och kontakter, men användaren bara vill börja mäta när nya system eller processer har införts, så de bestämmer sig för att ange ett startdatum en gång [!DNL Marketo Measure] ska börja spåra kampanjmedlemmarna.

## Använd skiftläge för slutdatum för slutpunkt {#use-case-for-touchpoint-end-date}

Om innan du använder [!DNL Marketo Measure]använde ni en plattform för marknadsföringsautomatisering som spårade Leads digitala interaktioner (skickade IE-formulär) och överförde sedan dessa leads till en [!DNL Saleforce] Med Campaign kan du utnyttja fältet Slutdatum för slutpunkt. Du angav slutdatumet för slutpunkten som ditt startdatum med [!DNL Marketo Measure] och aktivera Buyer Touchpoints så skapas var och en av dessa Leads digitala interaktion som en kontaktyta. Orsaken till att du anger slutdatumet för slutpunkten till ditt startdatum med [!DNL Marketo Measure] eftersom vi nu kommer att spåra dessa digitala interaktioner genom vårt javascript.

![](assets/3.png)

## Kampanjmedlemmar {#campaign-members}

Kampanjmedlemmar är kapslade under [!UICONTROL Campaigns]och är relaterade till en lead eller kontakt. En lead eller en kontakt kan bara läggas till en gång i en kampanj, vilket kan vara problematiskt beroende på hur kampanjen används. När en kampanj synkroniseras används kampanjmedlemskapet som en marknadsföringsaktivitet som placeras på kontaktytan och behandlas som en formulärfyllning.

## Status för köparens kontaktpunkt {#buyer-touchpoint-status}

Om den är aktiverad [!DNL Marketo Measure] skickar ett statusvärde till Campaign-medlemmen i fyra olika fält som ingår i det installerade paketet: Touchpoint Status (Lead), Touchpoint Status (Kontakt), Touchpoint Status (säljprojekt) och Touchpoint Status Date. Detta hjälper kunderna att granska om en kontaktyta har skapats som en kontaktyta för köpare eller Buyer Attribution, beroende på vilket objekt den är relaterad till. Slutpunktens statusdatum är helt enkelt det sista datumet då statusen uppdaterades för Campaign-medlemmen.

![](assets/4.png)

## Buyer Touch Point Date {#buyer-touchpoint-date}

När paketet installeras [!DNL Marketo Measure] innehåller också ett fält på Campaign-medlemmen med namnet&quot;Buyer Touchpoint Date&quot;. Detta gör att användaren kan åsidosätta datumet som [!DNL Marketo Measure] skulle använda för slutpunktsdatumet i slutpunktsposten.

Detta kan vara nödvändigt om en lista överfördes dagar/veckor/månader efter det att en händelse faktiskt inträffade. Det finns sätt att uppdatera alla poster samtidigt, vilket förklaras nedan.

![](assets/5.png)

Om du vill veta om du behöver använda Buyer Touchpoint Date eller inte, så här bestäms datumen av [!DNL Marketo Measure] beroende på [!UICONTROL Sync Type] som har valts för Campaign.

Om [!UICONTROL Sync Type] är inställt på Inkludera alla kampanjmedlemmar, prioriteten för att ställa in slutpunktsdatumet är uppifrån och ned:

* Buyer Touch Point Date
* Skapad den kampanjmedlem

Om [!UICONTROL Sync Type] är inställd på&quot;Inkludera endast &#39;responderade&#39; kampanjmedlemmar&quot;, prioriteten för att ställa in slutpunktsdatumet är uppifrån och ned:

* Buyer Touch Point Date
* Första svarsdatum
   * Det första svarsdatumet ställs in automatiskt så fort som statusen ändras till&quot;Responded&quot; (Svarat) och är en standard [!DNL Salesforce] fält som inte kan ändras

* Skapad den kampanjmedlem

## Uppdatera Touchpoint-datum gruppvis {#bulk-update-touchpoint-date}

Kontaktpunktsdatumet för gruppuppdatering ingår i den installerade [!DNL Marketo Measure] [!DNL Salesforce] paket och knapp måste läggas till i sidlayouten.

![](assets/6.png)

Om ett stort antal Campaign-medlemsposter behöver uppdateras kan du använda [!UICONTROL Bulk Update Touchpoint Date] för massredigering.

Om det finns unika användningsfall som det här gränssnittet inte täcker kan du även använda [Datainläsare](https://dataloader.io/){target="_blank"} om du vill exportera posterna, göra ändringarna och överföra posterna tillbaka till.

Börja med att söka efter posterna och filtrera dem som du vill ange ett datum för Buyer Touchpoint för.

>[!CAUTION]
>
>Det finns en sökning som inte fungerar, vilket visas i exemplet nedan. Gränssnittet stöder inte sökning efter nolldatum för Buyer Touchpoint (sökningen nedan fungerar inte):

![](assets/7.png)

Om du inte behöver använda sökningen och bara vill använda datumen på alla Campaign-medlemsposter använder du &quot;[!UICONTROL Include All Records]&quot; kryssrutan (se skärmbild nedan) som kontrollerar alla poster på alla sidor.

Välj datum och tid i kalenderväljaren. Om du vill välja aktuellt datum och aktuell tid klickar du på datumet/tiden som visas bredvid kalenderväljaren.

När du angett datum och tid klickar du på **[!UICONTROL Update Selected Records]** för att tillämpa ändringarna.

![](assets/8.png)

## Kampanjkostnader {#campaign-costs}

Lär dig allt om kampanjkostnader [i den här artikeln](/help/marketing-spend/spend-management/crm-campaign-costs.md).

## Borttagning av kampanjmedlem {#campaign-member-removal}

Så där [!DNL Marketo Measure] håller reda på alla borttagna poster i Salesforce, oavsett om de är borttagna leads, konton eller säljprojekt, är att se posterna i API:t och spåra att en post är markerad som&quot;IsDeleted&quot;. Tyvärr har Salesforce med Campaign-medlemmar infört ett annat sätt att ta bort de här kampanjmedlemmarna från en kampanj, och de markeras faktiskt som&quot;borttagna&quot; i stället för&quot;borttagna&quot;, så problemet är att kontaktytorna fortfarande bodde i Salesforce som var relaterade till borttagna kampanjmedlemmar.

För att komma runt problemet [!DNL Marketo Measure] skapade en [!DNL Marketo Measure] Händelseobjekt och en utlösare som ska spåras när Campaign-medlemmar tas bort och sedan ta bort motsvarande kontaktyta. **Du behöver [!DNL Marketo Measure] Marknadsföringsanalyspaket V6.15 eller senare** om du vill använda den här funktionen.

>[!CAUTION]
>
>Kom ihåg att den här utlösaren inte spårar några kampanjmedlemmar som har tagits bort tidigare, så det här fungerar bara framåt. Om du behöver ta bort ett stort antal kontaktytor för tidigare kampanjmedlemmar kontaktar du [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Universitet: fält för kampanjobjekt](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
>
>[[!DNL Marketo Measure] Universitet: Mappa offlinekanaler](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
