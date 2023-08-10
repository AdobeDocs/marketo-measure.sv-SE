---
unique-page-id: 42762310
description: Synkroniserar historiska data - [!DNL Marketo Measure] - Produktdokumentation
title: Synkroniserar historiska data
exl-id: 5a3c1a71-463a-4d75-98b9-fc225839512a
feature: Channels
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 0%

---

# Synkroniserar historiska data {#syncing-historical-data}

[!DNL Marketo Measure] är en lösning som innehåller de mest detaljerade, användbara data. Vi förstår dock att du kan ha befintliga data som du vill ha attribuering för. Det går att generera kontaktytor för historiska data, men det är viktigt att ta hänsyn till några faktorer innan du går vidare med den här processen.

## Faktorer att tänka på {#factors-to-consider}

**Är data redan organiserade i kampanjer?**

a. Data måste organiseras i kampanjer för att kunna synkroniseras med [!DNL Marketo Measure] för att skapa kontaktpunkter. Om det inte är organiserat i kampanjer just nu vill ni utvärdera om det är värt den tid och de resurser som behövs för att segmentera data i lämpliga kampanjer.

b. Det datum då medlemmen lades till i kampanjen eller markerades som svarad kommer att användas för slutpunktsdatumet, så detta måste också vara korrekt. [!DNL Marketo Measure] erbjuder tillfälliga lösningar i både SFDC och MSD för att uppdatera datumen, men detta kan ta lång tid beroende på volymen.

**Har ni en ganska lika mängd data ordnade i kampanjer för alla kanaler (betalsökningar, evenemang, organiska aktiviteter osv.)?**

Det är viktigt att ha en balanserad bild av attribueringen för att få korrekt och&quot;rättvis&quot; rapportering. Om du t.ex. bara har data för tidigare offlinekanalarbete som Händelser, kommer data i sig att vara partiska utan historiska onlinedata för att komplettera dem.

**Vilken granularitetsnivå väntar du dig?**

Du kommer i princip bara att kunna namnet Kanal, Delkanal och Campaign.

**Vilka är era rapporteringsmål i framtiden?**

Dessa data kommer att begränsas, så det är viktigt att tänka på hur du tänker använda dem. Det kanske inte är så klokt att jämföra historiska data med framtida data.

**Hur långt bak vill du gå?**

[!DNL Marketo Measure] Vi rekommenderar att du inte går förbi det föregående året.

Detta är ett ämne som vi starkt uppmuntrar att diskutera med [!DNL Marketo Measure] kontakta först. Om du har övervägt det ovanstående och vill fortsätta, allmänna instruktioner (separat för [!DNL Salesforce] och [!DNL Microsoft Dynamics]) är nedan.

## Synkronisera historiska kampanjer i [!DNL Salesforce] {#syncing-historic-campaigns-in-salesforce}

**Online:**

Om du vill synkronisera historiska onlinedata måste data organiseras i Salesforce-kampanjer som du sedan synkroniserar med [!DNL Marketo Measure] via [!DNL Salesforce] Regler för kampanjsynkronisering i [!DNL Marketo Measure] app. Det är viktigt att se till att kontaktytor inte genereras från någon av dessa kampanjer efter det datum då JavaScript blev tillgängligt. Orsaken till detta är att undvika dubbla kontaktytor. När JavaScript-skriptet är publicerat spåras onlineinsatserna automatiskt, så vi vill inte spåra dem via en SFDC-kampanj. För att undvika det här problemet måste du lägga till en tidsuppfattning i regeln. Kanske något som &quot;Skapad av kampanjmedlem&quot; är mindre än [JavaScript-publiceringsdatum]&quot;.

![](assets/syncing-historical-data-1.png)

Kanalmappningskomponenten för historiska onlinedata kan vara lite besvärlig. Vi vill att den ska matcha dina nuvarande regler för onlinekanaler (från regelbladet online) så nära som möjligt för ren rapportering. Nedan visas ett exempel på en perfekt kanalmappning.

>[!NOTE]
>
>Den här kanalmappningen görs i [!UICONTROL Offline Channels] i [!DNL Marketo Measure] eftersom vi använder SFDC-kampanjer.

| Salesforce-kampanjtyp | Kanal | Delkanal |
|---|---|---|
| Betalsökning - AdWords | Betalsökning | AdWords |
| Betalsökning - Bing | Betalsökning | Bing |
| Betald sökning - Yahoo | Betalsökning | Yahoo |

Onlinedata som läggs till på det här sättet är i sig mindre detaljerade än onlinedata [!DNL Marketo Measure] spårar via JavaScript. Till exempel kommer fält som formulär-URL, landningssida, referenssida osv. inte att fyllas i. Därför rekommenderas att kampanjerna delas upp i varje källa om möjligt. Som du ser i exemplet ovan måste du ha flera Campaign-typer för varje källa för att kunna rapportera exakt.

Det kanske inte är möjligt eller rimligt att ha antalet SFDC-kampanjtyper som stöder detaljerad kanalmappning, så du kanske bara behöver mappa till kanalnivå och ignorera delkanaler. Om kanalnivån inte heller är känd kan du skapa en proxykanal som &quot;Historic Digital&quot; så att du åtminstone vet att det var en onlinekontakt.

Om du behöver massredigera det slutdatum som ska användas för de här historiska onlineinsatserna använder du [!DNL Marketo Measure] anpassad &quot;[!UICONTROL Bulk Update Touchpoint Date]&quot; (detta är tillgängligt som ett anpassat fält i Campaign-objektet i SFDC). Om Campaign har en kort tidsrymd kanske det är värt att massredigera slutpunktsdatumet en dag i taget, medan det kan vara vettigt att massuppdatera varje vecka om Campaign har en längre tidsrymd. Om du använder funktionen för att uppdatera slutpunktsdatum gruppvis ska du uppdatera regeln för kampanjsynkronisering så att den använder slutpunktsdatumet för köparen i datumfältet. Observera att detta kan kräva att du får kreativitet med reglerna för Campaign-synkronisering om detta bara gäller en Campaign eller två, och inte alla.

**Offline:**

Historiska data om offlinemarknadsföringsaktiviteter (sådana som inte kan spåras via JavaScript) måste också organiseras i SFDC-kampanjer. SFDC-kampanjer är rätt sätt [!DNL Marketo Measure] spårar offlineaktiviteter oavsett om aktiviteten är &quot;historisk&quot; eller &quot;aktuell/postaktuell[!DNL Marketo Measure] implementering&quot; så följ samma kanalmappning som du valde i den ursprungliga utbildningen för konfiguration av offlinekanaler.

Använd vid behov knappen&quot;Uppdatera slutpunktsdatum gruppvis&quot; för att massredigera slutpunktsdatumet för kampanjmedlemmar. Om du till exempel skapar SFDC-kampanjer efter att händelsen inträffat, vill du massredigera för rätt datum. Om du använder funktionen för att uppdatera slutpunktsdatum gruppvis ska du uppdatera regeln för kampanjsynkronisering så att den använder slutpunktsdatumet för köparen i datumfältet. Observera att detta kan kräva att du får kreativitet med reglerna för Campaign-synkronisering om detta bara gäller en Campaign eller två, och inte alla.

## Synkronisera historiska kampanjer i [!DNL Dynamics] {#syncing-historic-campaigns-in-dynamics}

[!DNL Marketo Measure] kan retroaktivt generera kontaktytor för interaktioner som har inträffat tidigare, så länge de är organiserade i kampanjer inom [!DNL Dynamics].

Detta inbegriper vanligtvis arbete i CRM för att ta hänsyn till historiska datum. Hanteringen kommer också att skilja sig åt när det gäller onlinearbete (spåras av JS) och offlinearbete (kan inte spåras av JS).

Följ instruktionerna nedan för att ordna historiska data i [!DNL Dynamics] i ett format som kan synkroniseras till [!DNL Marketo Measure].

**Online:**

Historisk digital information måste struktureras i [!DNL Dynamics] kampanjer för att bli efterfyllda. Det bästa är att den här strukturen redan finns.

Om informationen finns på annat håll (t.ex. fortfarande bor i Marketing Automation) måste den föras in i [!DNL Dynamics] och är organiserade i lämpliga kampanjer. Sedan måste du räkna med slutpunktsdatumet när du vill att det ska återspegla datumet från det förflutna, inte datumet som du sparade in det i [!DNL Dynamics]. Om du vill åsidosätta det här datumet kan du använda det anpassade fältet&quot;Buyer Touchpoint Date&quot; för att ändra datumet. Du måste lägga till detta i marknadsföringslistformuläret.

![](assets/syncing-historical-data-2.png)

Som ett resultat av detta kan du massange datumet för alla i den marknadsföringslistan som ska användas för slutpunktsdatumet. Om du vill ha mer korrekta historiska datum skapar du flera marknadsföringslistor för samma kampanj - var och en med ett eget Touchpoint-datum. Om Campaign har en kort tidsperiod kanske det är värt besväret att skapa en marknadsföringslista för varje dag. Om Campaign har en längre tidsrymd kan det vara bra att skapa en marknadsföringslista varje vecka.

Mer information om synkronisering av marknadsföringslistor finns här: [[!DNL Dynamics] Kampanjer och marknadsföringslistor](/help/marketo-measure-and-dynamics/dynamics-reporting/dynamics-campaigns-and-marketing-lists.md)

>[!NOTE]
>
>Om du av någon anledning har en kampanjspårning online-aktivitet som är aktiv efter JavaScript-livedatumet måste du ange &quot;[!UICONTROL Touchpoint End Date]till det datum då JS blev aktiv. Detta för att undvika att ha dubbla kontaktytor för samma interaktion.

Att tänka på: Onlinedata som läggs till på det här sättet är i sig mindre detaljerade än onlinedata [!DNL Marketo Measure] spårar via JavaScript. Fält som t.ex. formulär-URL, landningssida, referenssida osv. fylls inte i. Därför rekommenderas att kampanjerna delas upp i varje källa om möjligt. Nedan visas ett exempel på en perfekt mappning.

| Dynamics-kampanjtyp | Kanal | Delkanal |
|---|---|---|
| Betalsökning - AdWords | Betalsökning | AdWords |
| Betalsökning - Bing | Betalsökning | Bing |
| Betald sökning - Yahoo | Betalsökning | Yahoo |

Om du inte har ett sätt att identifiera en källa eller om det inte är värt besväret kan du använda en Campaign-typ som är mappad till en kanal som kallas&quot;gammal digital&quot; eller&quot;historik webbplats&quot;.

**Offline:**

För att få kontaktytor för tidigare offlinemarknadsföringsaktiviteter måste data organiseras i [!DNL Dynamics] kampanjer och synkroniseras med [!DNL Marketo Measure]. Processen är densamma som för aktuella offlinekanaler (synkronisera kampanjen via marknadsföringslistor eller kampanjsvar). Nedan visas ett exempel på kanalmappning.

| Dynamics-kampanjtyp | Kanal | Delkanal |
|---|---|---|
| Event - sponsrade konferenser | Händelser | Sponsrade konferenser |
| Evenemang - partnerevent | Händelser | Partnerevent |
| Händelser - Hosted Events | Händelser | Hosted Events |
| Webbinarium - Partner Webinar | Webbinarium | Partner Webinar |

Om dessa data inte redan är organiserade i kampanjer med rätt datum kan du använda fältet&quot;Buyer Touchpoint Date&quot; för att återspegla korrekt datum från tidigare offlineaktivitet.

