---
unique-page-id: 34406495
description: Marknadsföringsgrupper - [!DNL Marketo Measure] - Produktdokumentation
title: Marknadsföringsgrupper
exl-id: e7978a79-6f6e-4bfd-9962-b35b7d46a9ac
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Marknadsföringsgrupper {#marketing-ops-tiles}

Med Marketing Ops kan ni validera och diagnostisera [!DNL Marketo Measure] data med fullständig insyn i enskilda kontaktytor per lead, kontakt, konto, kampanj och säljprojekt.

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><br></td> 
   <td><p><strong>Konto-ID</strong></p></td> 
   <td><p><strong>Kontonamn</strong></p></td> 
   <td><p><strong>Opp-ID</strong></p></td> 
   <td><p><strong>Opp-namn</strong></p></td> 
   <td><p><strong>Lead- eller kontakt-ID</strong></p></td> 
   <td><p><strong>Lead- eller kontaktmejl</strong></p></td> 
   <td><p><strong>Kampanj-ID</strong></p></td> 
   <td><p><strong>Opp Won</strong></p></td> 
   <td><p><strong>Skapat den</strong></p></td> 
   <td><p><strong>Opp stängningsdatum</strong></p></td> 
   <td><p><strong>Kontaktpunktsdatum</strong></p></td> 
   <td><p><strong>Attributionsmodell</strong></p></td> 
  </tr> 
  <tr> 
   <td><p><strong>Konton</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Möjligheter</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Kontakter</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Leads</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X*</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
  <tr> 
   <td><p><strong>Kampanjer</strong></p></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><br></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
   <td><strong>X</strong></td> 
  </tr> 
 </tbody> 
</table>

## Kontopanel {#account-tile}

![](assets/one-1.png)

Visar följande data relaterade till angivna konton.

**Konton måste ha Touchpoint-data (gäller endast om du har ABM aktiverat)**

-Konto-ID: Konto-ID i CRM

-Kontonamn: Kontonamn i CRM

-Skapad: Skapad den för kontot i CRM

* Detaljerad information: Se Skapad den per timme, minut, tid

-Webbplats: Värdet som finns i webbplatsfältet på kontot

-Engagement Rating: Predictive Engagement Score (PES) ifylld av [!DNL Marketo Measure]^1

-Affärsmöjligheter: Antal affärsmöjligheter som är kopplade till kontot

* Detaljerad information: Se information om associerade säljprojekt

-Kontakter: Antal kontakter som finns listade på det här kontot

* Detaljerad information: Se information för associerade kontakter

-Leads: Antal leads som har mappats till det här kontot via lead-till-konto-mappning^1

* Detaljerad information: Se information om leads som har mappats till kontot

-Attribution Touchpoints: Antal kontaktpunkter för Buyer Attribution för kontot

* Detaljerad information: Se Information om Buyer Attribution Touchpoint (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: Antal kontaktpunkter som kontakterna på det här kontot har^2

* Detaljerad information: Se Kontaktpunkter på kontouchpunktsinformation (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, marknadsföringsberöringstyp)

>[!NOTE]
>
>Om du har ABM visas kontaktpunkter för leads som har mappats via Lead to Account Mapping.

## Affärsmöjlighet {#opportunity-tile}

![](assets/two-1.png)

Visar följande data för angivna säljprojekt.

-Affärsmöjlighets-ID: Affärsmöjlighets-ID i CRM

-Affärsmöjlighetens namn: Affärsmöjlighetsnamn i CRM

-Kontonamn: Kontonamn som är associerat med affärsmöjligheten

-Skapad: Skapat datum för affärsmöjligheten i CRM

Detaljerad information: Se Skapad den per timme, minut, tid

-Stängningsdatum: Stängt datum för affärsmöjligheten i CRM

Detaljerad information: Se stängningsdatum per timme, minut, tid

-Belopp: Det totala beloppet för affärsmöjligheten

-Kontakter: Antal kontakter som är associerade med affärsmöjligheten

Detaljerad information: Se information för associerade kontakter

-Attribution Touchpoints: Antal relaterade kontaktpunkter för Buyer Attribution

Detaljerad information: Se Information om Buyer Attribution Touchpoint (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

## Kontaktpanel {#contacts-tile}

![](assets/three-1.png)

Visar följande data som är relaterade till angivna kontakter.

-Kontakt-ID: Kontakt-ID i CRM

-E-post: E-postadress till kontaktpost

-Skapad: Skapat datum för kontakten i CRM

* Detaljerad information: Se Skapad den per timme, minut, tid

-Kontonamn: Kontonamn som är associerat med kontakten

-Attribution Touchpoints: Antal kontaktpunkter för Buyer Attribution för kontakten

* Detaljerad information: Se Information om Buyer Attribution Touchpoint (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: Antal kontaktpunkter för köpare för kontakten

* Detaljerad information: Se Kontakter på kontouchpunktsinformation (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, marknadsföringsberöringstyp)

## Leads-panel {#leads-tile}

![](assets/four-1.png)

Visar följande data relaterade till angivna lead(er).

-Lead-ID: Lead-ID i CRM

-E-post: E-postadress för lead-post

-Skapad: När lead skapades i CRM

* Detaljerad information: Se Skapad den per timme, minut, tid

-Företag (från Lead): Det företag som anges på posten i CRM ifylld av kund

-Kontonamn: Kontonamnet [!DNL Marketo Measure] fylls i baserat på vår lead-to-Account Mapping

-Touchpoints: Antalet kontaktpunkter som är kopplade till leadet (lead(n)

* Detaljerad information: Se Kontakter på kontouchpunktsinformation (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, marknadsföringsberöringstyp)

## Kampanjpanel {#campaigns-tile}

![](assets/five-1.png)

Visar följande data som är relaterade till angivna kampanjer.

-Kampanj-ID: Kampanj-ID i CRM

-Kampanjnamn: Kampanjnamn i CRM

-Kampanjutgift: Utgifterna [!DNL Marketo Measure] har registrerats som är associerad med kampanjen

-Attribution Model: Detta visar lämplig attribuering baserat på vald modell

-Attribution Touchpoints: Antal slutpunkter för Buyer Attribution som är associerade med kampanjen/kampanjerna

* Detaljerad information: Se Information om Buyer Attribution Touchpoint (ID, Email, Touchpoint Date, Account Name, Campaign, Channel, Subchannel, Marketing Touch Type, Attribution Model)

-Touchpoints: Antalet kontaktytor som är associerade med kampanjer

* Detaljerad information: Se Kontakter på kontouchpunktsinformation (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, marknadsföringsberöringstyp)
