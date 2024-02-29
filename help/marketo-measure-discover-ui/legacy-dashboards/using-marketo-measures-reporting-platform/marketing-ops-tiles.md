---
unique-page-id: 34406495
description: Marknadsföringsgrupper - [!DNL Marketo Measure]
title: Marknadsföringsgrupper
exl-id: e7978a79-6f6e-4bfd-9962-b35b7d46a9ac
feature: Reporting
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '766'
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

-Webbplats: Värdet finns i webbplatsfältet på kontot

-Engagement Rating: Predictive Engagement Score (PES) ifylld av [!DNL Marketo Measure]^1

-Affärsmöjligheter: Antal affärsmöjligheter kopplade till kontot

* Detaljerad information: Se information om associerade säljprojekt

-Kontakter: Antal kontakter som visas på det här kontot

* Detaljerad information: Se information för associerade kontakter

-Leads: Antal leads som har mappats till det här kontot via lead-till-kontomappning^1

* Detaljerad information: Se information om leads som har mappats till kontot

-Attribution Touchpoints: Number of Buyer Attribution Touchpoints for the account

* Detaljerad information: Se Kontaktpunktsinformation för Buyer-attribut (ID, E-post, Slutpunktsdatum, Kontonamn, Kampanj, Kanal, Subkanal, Marknadsföringsberöringstyp, Attributionsmodell)

-Touchpoints: Antal kontaktpunkter som kontakterna på det här kontot har^2

* Detaljerad information: Se Touchpoints på kontouchpoint-informationen (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, typ av marknadsföringsberöring)

>[!NOTE]
>
>Om du har ABM visas kontaktpunkter för leads som har mappats via Lead to Account Mapping.

## Affärsmöjlighet {#opportunity-tile}

![](assets/two-1.png)

Visar följande data för angivna säljprojekt.

-Affärsmöjlighets-ID: Affärsmöjlighets-ID i CRM

-Affärsmöjlighetens namn: Affärsmöjlighetens namn i CRM

-Kontonamn: Kontonamn som är associerat med affärsmöjligheten

-Skapad: Skapad den i CRM

Detaljerad information: Se Skapad den per timme, minut, tid

-Stängningsdatum: Stängt datum för affärsmöjligheten i CRM

Detaljerad information: Se stängningsdatum per timme, minut, tid

-Belopp: Det totala beloppet för affärsmöjligheten

-Kontakter: Antal kontakter som är associerade med affärsmöjligheten

Detaljerad information: Se information för associerade kontakter

-Attribution Touchpoints: Number of related Buyer Attribution Touchpoints

Detaljerad information: Se Kontaktpunktsinformation för Buyer-attribut (ID, E-post, Slutpunktsdatum, Kontonamn, Kampanj, Kanal, Subkanal, Marknadsföringsberöringstyp, Attributionsmodell)

## Kontaktpanel {#contacts-tile}

![](assets/three-1.png)

Visar följande data som är relaterade till angiven(e) kontakt(er).

-Kontakt-ID: Kontakt-ID i CRM

-E-post: E-postadress till kontaktpost

-Skapad: Skapad den här kontaktens datum i CRM

* Detaljerad information: Se Skapad den per timme, minut, tid

-Kontonamn: Kontonamnet som är associerat med kontakten

-Attribution Touchpoints: Number of Buyer Attribution Touchpoints for the contact

* Detaljerad information: Se Kontaktpunktsinformation för Buyer-attribut (ID, E-post, Slutpunktsdatum, Kontonamn, Kampanj, Kanal, Subkanal, Marknadsföringsberöringstyp, Attributionsmodell)

-Touchpoints: Antal kontaktytor för köparen för kontakten

* Detaljerad information: Se Kontakter på kontouchpoint-informationen (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, typ av marknadsföringsberöring)

## Leads-panel {#leads-tile}

![](assets/four-1.png)

Visar följande data relaterade till angivna lead(er).

-Lead-ID: Lead-ID i CRM

-E-post: Leadpostens e-postadress

-Skapad: När leadet skapades i CRM

* Detaljerad information: Se Skapad den per timme, minut, tid

-Företag (från Lead): Det företag som anges i posten i CRM ifylld av kund

-Kontonamn: Kontonamnet [!DNL Marketo Measure] fylls i baserat på vår lead-to-Account Mapping

-Touchpoints: Antalet kontaktytor som är associerade med leadet (leads)

* Detaljerad information: Se Kontakter på kontouchpoint-informationen (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, typ av marknadsföringsberöring)

## Kampanjpanel {#campaigns-tile}

![](assets/five-1.png)

Visar följande data som är relaterade till angivna kampanjer.

-Kampanj-ID: Kampanj-ID i CRM

-Kampanjnamn: Kampanjnamn i CRM

-Kampanjutgifter: Utgifterna [!DNL Marketo Measure] har registrerats som är associerad med kampanjen

-Attribution Model: Detta visar lämplig attribuering baserat på vald modell

-Attribution Touchpoints: Antalet Touchpoints för Buyer Attribution som är associerat med kampanjen/kampanjerna

* Detaljerad information: Se Kontaktpunktsinformation för Buyer-attribut (ID, E-post, Slutpunktsdatum, Kontonamn, Kampanj, Kanal, Subkanal, Marknadsföringsberöringstyp, Attributionsmodell)

-Touchpoints: Antalet kontaktytor som är associerade med kampanjer

* Detaljerad information: Se Kontakter på kontouchpoint-informationen (ID, e-post, slutpunktsdatum, kontonamn, kampanj, kanal, subkanal, typ av marknadsföringsberöring)
