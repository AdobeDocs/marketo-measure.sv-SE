---
description: Översikt över integreringsbehörigheter - [!DNL Marketo Measure] - Produktdokumentation
title: Översikt över integreringsbehörigheter
hide: true
hidefromtoc: true
feature: APIs, Integration
source-git-commit: 4953d6c51a87669ced0a13e2a54810d14976585c
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Översikt över integreringsbehörigheter {#integration-permissions-overview}

I den här guiden beskrivs de nödvändiga behörigheterna för smidig integrering med Marketo Measure, så att varje integrering fungerar effektivt och utan problem.

<table>
<thead>
  <tr>
    <th>Integrering</th>
    <th>Datatyp
    <li>Webbinteraktionsdata</li>
    <li>Systemdata för B2B</li>
    <li>Ad Platform Data</li></th>
    <th>Vad vi spårar</th>
    <th>Behörighetskrav</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Systemdata för B2B    
</td>
    <td>Marketo Measure spårar:
    <br>
    <li>Konto</li>
<li>Campaign</li>
<li>CampaignMember</li>
<li>Kontakt</li>
<li>CurrencyConversionRange</li>
<li>CurrencyStatus</li>
<li>Händelser</li>
<li>FieldHistory (Lead, Contact, and Opportunity)</li>
<li>Lead</li>
<li>Möjligheter</li>
<li>AffärsmöjlighetKontaktRoll</li>
<li>OpportunityHistory</li>
<li>Uppgifter</li>
<br>
Kontaktpunkter som skapats och andra data skrivs in i anpassade bizibla fält på konto, Campaign, CampaignMember, Case, Contact, Lead och Opportunity.</td>
    <td><b>Salesforce-anslutna användarbehörigheter (krävs)</b>
    <br>
    <b>Behörighetsuppsättning för Marketo Measure-administratör för dedikerad användare:</b> Tillåt SFDC-administratörer att utföra CRUD-åtgärder på markering för att mäta objekt.
    <br>
    <b>Visa och redigera behörighetsgrupp för konverterade leads:</b> På så sätt kan Marketo Measure dekorera leads efter att de har konverterats till kontakter.
    <br>
    <b>Kryssruta för Salesforce-marknadsföringsanvändare:</b> Kryssrutan Marknadsföringsanvändare tillåter användare att skapa kampanjer och använda guiden för kampanjimport.
    <br>
    <b>Marketo Measure Standard User:</b> Ger en användare möjlighet att läsa poster från Marketo Measure-objekt.
    <p>
    <b>Salesforce-standardfältbehörigheter</b>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce-standardobjekt och -åtkomst</a>
    <p>
    <b>Salesforce-anpassade fältbehörigheter</b>
    <br>
    Vi tillhandahåller funktionsinställningar för anpassade Salesforce-fält som kunderna kan använda. Om de här funktionsinställningarna definieras behöver vi läsåtkomst till alla Salesforce-fält som sparats i funktionsinställningen (om inställningsvärdet CustomLeadSourceField är lika med "LeadSource__c" kräver vi läsbehörighet till det här fältet).
    </td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
