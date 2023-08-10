---
unique-page-id: 35586105
description: Engagement Path - [!DNL Marketo Measure] - Produktdokumentation
title: Åtagandesökväg
exl-id: 104d803f-9f40-4ab6-872d-6432f8c087e9
feature: Reporting
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---

# Åtagandesökväg {#engagement-path}

Med Engagement Path kan ni få en komplett bild av alla ärenden - lead, kontakt, konto och affärsmöjlighet - från första beröring hela vägen fram till avslut.

![](assets/one-2.png)

## Platsbeskrivning {#tile-description}

**Typ av händelse:** Typen av kontaktyta (Session, CRM Campaign, CRM Event, CRM Task, Impression)

**Pekpunktsposition:** Kontaktpunktsposition för lead/kontakt

**Touchpoint-position för Buyer-attribut:** Affärsmöjlighetens slutpunktsposition för köparattribut

**Kontaktpunktsdatum:** För onlinekällor: datum och tid då engagemanget inträffade. För offlinehändelser: datum och tid angivet i Salesforce-kampanjen. För aktiviteter: kontaktyta: kontaktpunktsdatumfält refereras i aktivitetskonfigurationen

**E-post:** E-postadressen som är kopplad till engagemanget

**Marknadsföringsberöringstyp:** Typ av engagemang (webbbesök, webbformulär, webbchatt, CRM, aktivitetstyper)

**Kanal:** Marknadsföringskanal som driver engagemanget

**Medel:** Medel för engagemang

* Om engagemanget kommer från en API-ansluten plattform (Adwords/BingAds) blir mediet CPC
* Om engagemangets landningssida innehåller utm_medium tolkas vi
* Om engagemanget kommer från CRM-kampanjen kommer mediet från fältet Type från CRM-kampanjen

**Webbkälla:** Den här kolumnen visar källan till engagemanget

* Om engagemanget kommer från en API-ansluten plattform visar webbkällan annonsplattformens namn
* Om kontaktytan kommer från organisk sökning visas namnet på sökmotorn i det här fältet
* Om inte #1 eller #2, och värdet utm_source finns i startsidans URL för kontaktytan, visas det värdet här
* Om det inte är #1 eller #2 och det inte finns något utm_source-värde visas rotdomänen för den refererande URL:en här.
* Om inget av ovanstående anges visas Web Direct eller Web

**Första interaktionen med personen:** I den här kolumnen visas Ja eller Nej om kontaktytan var den person som först interagerade

**Attribuerad omsättning:** I den här kolumnen visas intäkten som tilldelats den kontaktytan baserat på vald attribueringsmodell

## Filterbeskrivning {#filter-description}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Filternamn</th> 
   <th>Beskrivning</th> 
  </tr> 
  <tr> 
   <td><p>Kontonamn/ID</p></td> 
   <td><p>Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Flera filtervärden har "antingen eller"-relation, vilket innebär att rutor visar resultat för båda filtervärdena. Om något av filtervärdena inte är giltigt kommer instrumentpanelen inte att generera resultat för det ogiltiga värdet, men kommer fortfarande att filtrera till de giltiga filtervärdena. Inte skiftlägeskänsligt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Affärsmöjlighetens namn/ID</p></td> 
   <td><p>Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Flera filtervärden har "antingen eller"-relation, vilket innebär att rutor visar resultat för båda filtervärdena. Om något av filtervärdena inte är giltigt kommer instrumentpanelen inte att generera resultat för det ogiltiga värdet, men kommer fortfarande att filtrera till de giltiga filtervärdena. Inte skiftlägeskänsligt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Lead-ID/e-postadress</p></td> 
   <td><p>Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Flera filtervärden har "antingen eller"-relation, vilket innebär att rutor visar resultat för båda filtervärdena. Om något av filtervärdena inte är giltigt kommer instrumentpanelen inte att generera resultat för det ogiltiga värdet, men kommer fortfarande att filtrera till de giltiga filtervärdena. Inte skiftlägeskänsligt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Kontakt-ID/E-postadress</p></td> 
   <td><p>Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Flera filtervärden har "antingen eller"-relation, vilket innebär att rutor visar resultat för båda filtervärdena. Om något av filtervärdena inte är giltigt kommer instrumentpanelen inte att generera resultat för det ogiltiga värdet, men kommer fortfarande att filtrera till de giltiga filtervärdena. Inte skiftlägeskänsligt.</p><p>Kontonamn/ID, Lead-ID/E-post, Kontakt-ID/E-postfilter är "antingen eller"-relation, vilket innebär att om både lead-filtret och kontaktfiltret har ett värde visas alla poster för något av ID:n.</p></td> 
  </tr> 
  <tr> 
   <td><p>Attributionsmodell</p></td> 
   <td><p>Ange vilken modell som den tilldelade intäkten ska beräknas mot. Tillåtna värden: "Full Path Attribution", "First Touch Attribution", "Custom Model Attribution", "Lead Creation Attribution", "U Shaped Attribution", "W Shaped Attribution".</p></td> 
  </tr> 
  <tr> 
   <td><p>Händelsetyp</p></td> 
   <td><p>Filtrera resan efter typ av händelse som användarkontaktytan baseras på. Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Tillåtna värden: Session, CRM Campaign, CRM Event, CRM Task, Impression.</p></td> 
  </tr> 
  <tr> 
   <td><p>Leadfaser</p></td> 
   <td><p>Filtrera resan efter leadstadium som användarkontaktytan baseras på. Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Som standard visas förslag att välja mellan, men du bör använda "contains" som filtervillkor för flera filter på scener.</p></td> 
  </tr> 
  <tr> 
   <td><p>Affärsmöjlighetens faser</p></td> 
   <td><p>Filtrera resan efter affärstillfället som användarkontaktytan baseras på. Tillåter flera värden genom att lägga till filter med plustecknet "+" till höger. Som standard visas förslag att välja mellan, men du bör använda "contains" som filtervillkor för flera filter på scener.</p></td> 
  </tr> 
  <tr> 
   <td><p>Kontaktpunktsdatum</p></td> 
   <td><p>Filtrera resan efter datum/tid för kontaktpunkten.</p></td> 
  </tr> 
  <tr> 
   <td><p>E-postadress för användarkontaktpunkt</p></td> 
   <td><p>Filtrera resan med e-post vid användarkontaktytan. Detta gör det möjligt att filtrera e-postmeddelanden som inte är kopplade till en lead/kontakt/ett konto.</p></td> 
  </tr> 
  <tr> 
   <td><p>Marknadsföringsberöringstyp</p></td> 
   <td><p>Filtrera resan efter typ av marknadsföringskontakt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Kanal</p></td> 
   <td><p>Filtrera resan efter kanal.</p></td> 
  </tr> 
  <tr> 
   <td><p>Medel</p></td> 
   <td><p>Filtrera resan efter medium.</p></td> 
  </tr> 
  <tr> 
   <td><p>Webbkälla</p></td> 
   <td><p>Filtrera resan efter webbkälla.</p></td> 
  </tr> 
  <tr> 
   <td><p>Första interaktionen med personen</p></td> 
   <td><p>Filtrera resan med kolumnen "Is First Touch" i användarkontakttabellen.</p></td> 
  </tr> 
  <tr> 
   <td><p>Attribuerad intäkt</p></td> 
   <td><p>Filtrera resan efter tilldelat intäktsvärde.</p></td> 
  </tr> 
 </tbody> 
</table>
