---
description: Skillnaden mellan en Google Analytics Conversion och en Buyer Touchpoint-guide för Marketo Measure-användare
title: Skillnaden mellan en Google Analytics-konvertering och en Buyer Touchpoint
exl-id: d09d963c-3207-467c-852a-d1edd49511fa
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Skillnaden mellan en Google Analytics-konvertering och en Buyer Touchpoint {#difference-between-a-google-analytics-conversion-and-a-buyer-touchpoint}

Lär dig vad ett [!DNL Google Analytics (GA)]-mål är och hur det skiljer sig från en Buyer Touchpoint.

**Vad är Google Analytics-konverteringar?**

[!UICONTROL Google Analytics] konverteringar bestäms av hur en marknadsförare eller webbutvecklare kodar &#39;mål&#39; på en viss webbplats. Enligt Google kan man tänka sig att man ska&quot;göra ett inköp (för en e-handelsplats), slutföra en spelnivå (för en mobilspelapp) eller skicka in ett kontaktinformationsformulär (för en webbplats för marknadsföring eller leadgenerering)&quot;. För det mesta ser marknadsförarna mål och konverteringar som någon som fyller i ett informationsformulär.

Men mål kan inte kodas för att hantera visst beteende. Det finns i stället måltyper som en webbutvecklare kan konfigurera. Nedan följer några av dessa exempel:

<table>
 <colgroup>
  <col>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <td><strong>Måltyp</strong></td>
   <td><p><strong>Beskrivning</strong></p></td>
   <td><strong>Exempel</strong></td>
  </tr>
  <tr>
   <td><p>Mål</p></td>
   <td>En specifik platsinläsning</td>
   <td><em>Tack för din registrering!Webbsida eller appskärm för </em></td>
  </tr>
  <tr>
   <td>Varaktighet</td>
   <td>Sessioner som varar en viss tid eller längre</td>
   <td>10 minuter eller längre på en supportwebbplats</td>
  </tr>
  <tr>
   <td>Sidor/Screens per session</td>
   <td>En användare visar ett visst antal sidor eller skärmar</td>
   <td>5 sidor eller skärmar har lästs in</td>
  </tr>
  <tr>
   <td>Händelse</td>
   <td>En åtgärd som definieras som en händelse aktiveras</td>
   <td>Sociala rekommendationer, videouppspelning och klick</td>
  </tr>
 </tbody>
</table>

De flesta marknadsförare konfigurerar sina konverteringar som&quot;Målmål&quot;, vilket innebär att de vanligtvis skapar en tacksida efter ett formulär för att ta hänsyn till att konverteringen är formell.

Detta innebär att Google ser Tack!-sidan som en konvertering. Ur Google Analytics-synpunkt är detta en realism som de flesta marknadsförare är nöjda med.

Buyer Touchpoints fungerar dock annorlunda.

**Hur skiljer sig Buyer Touchpoints?**

[!DNL Marketo Measure] JavaScript spårar sessionsdata och formuläröverföringar på alla former av en viss webbplats. Du behöver inte koda mål från en [!DNL Marketo Measure]-synvinkel. Den här processen är automatisk. När det gäller formulärskickning rapporterar [!DNL Marketo Measure] att ett formulär fylls i varje gång en anonym användare fyller i informationsfält i ett visst formulär och klickar på knappen för att skicka formulär. [!DNL Marketo Measure] behöver ingen tacksida för att kunna registrera formulärinlämningen.

[!DNL Marketo Measure] skapar en kontaktyta för ett formulär när:

* Ett lead/en kontakt som är associerad med dessa konverteringar visas i CRM.
* JS [!DNL Marketo Measure] finns på de webbsidor som innehåller formuläret.
* Ett formulär skickas inom 30 minuter.

[!DNL Marketo Measure] ignorerar Google Analytics-målkonverteringar när:

* En robot skickar in formulär på en webbplats (dessa robotar gör det vanligtvis inte i kundens CRM).
* En användare skickar fler formulär efter att de har skickat in det första formuläret. [!DNL Marketo Measure] skickar bara den första konverteringen från den sessionen.
* Användaren klickar på formuläret som skickas flera gånger. [!DNL Marketo Measure] tar endast hänsyn till den första formuläröverföringen.
* Användaren läser in tacksidan flera gånger.
* Användaren använder något annonsblockeringsverktyg.

Som du ser finns det grundläggande skillnader mellan vad GA och [!DNL Marketo Measure] anser att en konvertering ska vara. Därför är det troligt att antalet konverteringar och antalet kontaktytor i formulär skiljer sig åt.
