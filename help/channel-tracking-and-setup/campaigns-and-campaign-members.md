---
description: Vägledning om kampanjer och kampanjmedlemmar för Marketo Measure-användare
title: Kampanjmedlemmar och kampanjmedlemmar
exl-id: e4e2b154-39ac-4295-a541-7fa6112672e3
feature: Channels
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---

# Kampanjmedlemmar och kampanjmedlemmar {#campaigns-and-campaign-members}

[!DNL Salesforce] kampanjer är avsedda att spåra listor med leads och kontakter som är kopplade till ett marknadsföringsprogram eller en aktivitet. Detta har till exempel varit webbinarier, registreringar eller besök. Marknadsförarna kan välja om en Campaign ska tillskrivas en kontaktyta eller inte.

>[!NOTE]
>
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användare att använda den [nya, förbättrade processen i appen](/help/channel-tracking-and-setup/custom-campaign-sync.md){target="_blank"}.

## Aktivera kontaktpunkter {#enabling-touchpoints}

Paketet [!DNL Marketo Measure] [!DNL Salesforce] kommer att innehålla ett fält med namnet&quot;Enable Buyer Touchpoints&quot; i Campaign-objektet. När fältet har lagts till i sidlayouten ser det ut ungefär så här:

![Marketo Measure Salesforce Package kommer att innehålla ett fält med etiketten](assets/dynamics-lists-1.png)

Tillgängliga alternativ i plocklistan är:

![Tillgängliga alternativ i listan är:](assets/dynamics-lists-10.png)

* Inkludera alla kampanjmedlemmar - Varje enskild lead eller kontakt som läggs till i kampanjen får en kontaktyta som är kopplad till kampanjen.
* Inkludera endast responderade kampanjmedlemmar - Endast leads eller kontakter som har kampanjmedlemmens status&quot;Responded&quot; får en kontaktyta kopplad till kampanjen.
* Uteslut alla kampanjmedlemmar - Ingen av leads eller kontakter får en kontaktyta som är kopplad till kampanjen.

Observera att kampanjmedlemmar måste ha en e-postadress kopplad till sin post för att [!DNL Marketo Measure] ska kunna skapa en kontaktyta. Utan en e-postadress kommer [!DNL Marketo Measure] inte att tilldela kampanjmedlemmen någon kontaktyta.

## Synkroniseringsdatum för kampanj {#campaign-sync-dates}

När paketet har installerats innehåller [!DNL Marketo Measure] även två datumfält i Campaign-objektet: Startdatum för pekpunkt och Slutdatum för slutpunkt.

Dessa datum talar om för [!DNL Marketo Measure] när vi ska börja eller sluta ta med kampanjmedlemmar från Campaign till kontaktytan. Du kan antingen ange ett datum, eller båda, eller ingen alls.

## Använd skiftläge för slutpunktens startdatum {#use-case-for-touchpoint-start-date}

Startdatumet kan användas om en befintlig kampanj används för att spåra leads och kontakter, men användaren bara vill börja mäta när nya system eller processer har införts, så de bestämmer sig för att ange ett startdatum när [!DNL Marketo Measure] ska börja spåra kampanjmedlemmarna.

## Använd skiftläge för slutdatum för slutpunkt {#use-case-for-touchpoint-end-date}

Om du använde [!DNL Marketo Measure] innan du använde en plattform för marknadsföringsautomatisering som spårade Leads digitala interaktioner (skickade IE-formulär) och sedan överförde dessa leads till en [!DNL Saleforce] -kampanj, kan du använda fältet Slutdatum för slutdatum för pekpunkt. Du angav slutdatumet för slutpunkten som ditt startdatum med [!DNL Marketo Measure] och aktiverade slutpunkter för köpare. Därefter skapas varje leads digitala interaktion som en slutpunkt. Anledningen till att du anger slutdatumet för slutpunkten till ditt startdatum med [!DNL Marketo Measure] är att vi kommer att spåra dessa digitala interaktioner via vårt javascript.

![Om du använde en marknadsföringsautomatiseringsplattform innan du använde Marketo Measure &#x200B;](assets/dynamics-lists-2.png)

## Kampanjmedlemmar {#campaign-members}

Kampanjmedlemmar är kapslade under [!UICONTROL Campaigns] och är relaterade till en lead eller kontakt. En lead eller en kontakt kan bara läggas till en gång i en kampanj, vilket kan vara problematiskt beroende på hur kampanjen används. När en kampanj synkroniseras används kampanjmedlemskapet som en marknadsföringsaktivitet som placeras på kontaktytan och behandlas som en formulärfyllning.

## Buyer Touchpoint-status {#buyer-touchpoint-status}

Om det här alternativet är aktiverat skickar [!DNL Marketo Measure] ett statusvärde till Campaign-medlemmen i fyra olika fält som ingår i det installerade paketet: Touchpoint-status (lead), Touchpoint-status (kontakt), Touchpoint-status (säljprojekt) och Touchpoint-statusdatum. Detta hjälper kunderna att granska om en kontaktyta har skapats som Buyer Touchpoint eller Buyer Attribution Touchpoint, beroende på vilket objekt den hör till. Slutpunktens statusdatum är helt enkelt det sista datumet då statusen uppdaterades för Campaign-medlemmen.

![Om det här alternativet är aktiverat kommer Marketo Measure att överföra ett statusvärde till &#x200B;](assets/dynamics-lists-3.png)

## Buyer Touchpoint Date {#buyer-touchpoint-date}

När paketet har installerats innehåller [!DNL Marketo Measure] även ett fält i Campaign-medlemmen med namnet&quot;Buyer Touchpoint Date&quot;. Detta gör att användaren kan åsidosätta det datum som [!DNL Marketo Measure] skulle använda för slutpunktsdatumet i slutpunktsposten.

Detta kan vara nödvändigt om en lista överfördes dagar/veckor/månader efter det att en händelse faktiskt inträffade. Det finns sätt att uppdatera alla poster samtidigt, vilket förklaras nedan.

![Detta kan vara nödvändigt om en lista har överförts dagar/veckor/månader efter en](assets/dynamics-lists-4.png)

Om du vill veta om du behöver använda Buyer Touchpoint Date eller inte kan du se hur datumen bestäms av [!DNL Marketo Measure] beroende på vilken [!UICONTROL Sync Type] som har valts för Campaign.

Om [!UICONTROL Sync Type] är inställt på Inkludera alla kampanjmedlemmar är prioriteten att ange slutpunktsdatum nedifrån och upp:

* Buyer Touchpoint Date
* Skapad den kampanjmedlem

Om [!UICONTROL Sync Type] är inställt på Inkludera endast kampanjmedlemmar som är responderade, är prioriteten för att ange slutpunktsdatumet uppifrån och ned:

* Buyer Touchpoint Date
* Första svarsdatum
   * Det första svarsdatumet ställs in automatiskt så fort som statusen ändras till&quot;Responded&quot; och är ett [!DNL Salesforce]-standardfält som inte kan ändras

* Skapad den kampanjmedlem

## Uppdatera Touchpoint-datum gruppvis {#bulk-update-touchpoint-date}

Kontaktpunktsdatumet för gruppuppdatering ingår i det installerade [!DNL Marketo Measure] [!DNL Salesforce] -paketet och knappen måste läggas till i sidlayouten.

![Kontaktpunktsdatumet för gruppuppdatering ingår i den installerade Marketo](assets/dynamics-lists-5.png)

Om ett stort antal kampanjmedlemsposter behöver uppdateras kan du använda knappen [!UICONTROL Bulk Update Touchpoint Date] för att massredigera.

Om det finns unika användningsfall som det här gränssnittet inte täcker kan du också använda [datainläsaren](https://dataloader.io/){target="_blank"} för att exportera posterna, göra ändringen och överföra posterna tillbaka till.

Börja med att söka efter posterna och filtrera dem som du vill ange ett Buyer Touchpoint-datum för.

>[!CAUTION]
>
>Det finns en sökning som inte fungerar, vilket visas i exemplet nedan. Gränssnittet stöder inte sökning efter Buyer Touchpoint-datum som är null (sökningen nedan fungerar inte):

![Det finns en sökning som inte fungerar, vilket visas i &#x200B;](assets/legacy-processes-10.png)

Om du inte behöver använda sökningen och bara vill använda datumen för alla Campaign-medlemsposter använder du kryssrutan [!UICONTROL Include All Records] (se skärmbild nedan), som kontrollerar alla poster på alla sidor.

Välj datum och tid i kalenderväljaren. Om du vill välja aktuellt datum och aktuell tid klickar du på datumet/tiden som visas bredvid kalenderväljaren.

När du har angett datum och tid klickar du på knappen **[!UICONTROL Update Selected Records]** för att tillämpa ändringarna.

![När datumet och tiden är inställda klickar du på Uppdatera markerade](assets/dynamics-lists-6.png)

## Kampanjkostnader {#campaign-costs}

Lär dig allt om Campaign-kostnaderna [i den här artikeln](/help/crm-campaign-costs.md){target="_blank"}.

## Borttagning av kampanjmedlem {#campaign-member-removal}

Det sätt som [!DNL Marketo Measure] håller jämna steg med borttagna poster i Salesforce, oavsett om de är borttagna leads eller konton eller säljprojekt, är att visa posterna i API:t och spåra att en post är markerad som&quot;IsDeleted&quot;. Olyckligtvis med Campaign-medlemmar introducerade Salesforce ett annat sätt att ta bort dessa Campaign-medlemmar från en Campaign och de markeras faktiskt som&quot;borttagna&quot; i stället för&quot;borttagna&quot;, så problemet är att kontaktytorna fortfarande bodde i Salesforce och var kopplade till borttagna Campaign-medlemmar.

För att komma runt det här problemet skapade [!DNL Marketo Measure] ett [!DNL Marketo Measure] History-objekt och en utlösare för att spåra varje gång som Campaign-medlemmar tas bort och sedan ta bort motsvarande kontaktyta. **Du behöver [!DNL Marketo Measure] Marketing Analytics-paketet V6.15 eller senare** för att kunna använda den här funktionen.

>[!CAUTION]
>
>Kom ihåg att den här utlösaren inte spårar några kampanjmedlemmar som har tagits bort tidigare, så det här fungerar bara framåt. Om du behöver ta bort ett stort antal kontaktytor för tidigare kampanjmedlemmar kontaktar du [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Självstudiekurser: Kampanjobjektfält](https://experienceleague.adobe.com/sv/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/campaign-object-fields){target="_blank"}
>
>[[!DNL Marketo Measure] Självstudiekurser: Mappa offlinekanaler](https://experienceleague.adobe.com/sv/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
