---
description: Översikt över integreringsbehörigheter - [!DNL Marketo Measure] - Produktdokumentation
title: Översikt över integreringsbehörigheter
feature: APIs, Integration
source-git-commit: b7aea1e0789b2f4f3fd4b250c0f66595618317bb
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 0%

---

# Översikt över integreringsbehörigheter {#integration-permissions-overview}

I den här guiden beskrivs de nödvändiga behörigheterna för smidig integrering med Marketo Measure, så att varje integrering fungerar effektivt och utan problem.

<table>
<thead>
  <tr>
    <th style="width:10%">Integrering</th>
    <th style="width:25%">Datatyp
    <li>Webbinteraktionsdata</li>
    <li>Systemdata för B2B</li>
    <li>Ad Platform Data</li></th>
    <th style="width:25%">Vad vi spårar</th>
    <th style="width:40%">Behörighetskrav</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Salesforce</td>
    <td>Systemdata för B2B    
</td>
    <td>Marketo Measure spårar:
    <p>
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
<p>
Kontaktpunkter som skapats och andra data skrivs in i anpassade bizibla fält på konto, Campaign, CampaignMember, Case, Contact, Lead och Opportunity.</td>
    <td><b>Salesforce-användarbehörigheter (krävs)</b>
    <p>
    <b>Behörighetsuppsättning för Marketo Measure-administratör för dedikerad användare:</b> Tillåt SFDC-administratörer att utföra CRUD-åtgärder på markering för att mäta objekt.
    <br>
    <b>Visa och redigera behörighetsgrupp för konverterade leads:</b> På så sätt kan Marketo Measure dekorera leads efter att de har konverterats till kontakter.
    <br>
    <b>Kryssruta för Salesforce-marknadsföringsanvändare:</b> Kryssrutan Marknadsföringsanvändare tillåter användare att skapa kampanjer och använda guiden för kampanjimport.
    <br>
    <b>Marketo Measure Standard User:</b> Ger en användare möjlighet att läsa poster från Marketo Measure-objekt.
    <p>
    <b>Salesforce-standardfältbehörigheter</b>
    <br>
    <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce-standardobjekt och -åtkomst</a>
    <p>
    <b>Salesforce-anpassade fältbehörigheter</b>
    <br>
    Vi tillhandahåller funktionsinställningar för anpassade Salesforce-fält som kunderna kan använda. Om de här funktionsinställningarna definieras behöver vi läsåtkomst till alla Salesforce-fält som sparats i funktionsinställningen (om inställningsvärdet CustomLeadSourceField är lika med "LeadSource__c" kräver vi läsbehörighet till det här fältet).
    </td>
  </tr>
  <tr>
    <td>Dynamics</td>
    <td>Systemdata för B2B</td>
    <td>Marketo Measure spårar:
    <p>
    <li>Konto
<li>ActivityParty
<li>ActivityPointer
<li>Campaign
<li>CampaignItem (CampaignList i vårt system)
<li>CampaignResponse (CampaignMember i vårt system)
<li>Kontakt
<li>Lead
<li>List (MarketingList in our system)
<li>ListMember (MarketingListMember i vårt system)
<li>Möjligheter
<li>Organisation
<li>TransactionCurrency (CurrencyConversionRange och CurrencyStatus i vårt system)
<li>Avtalad tid, CampaignActivity, E-post, Fax, IncidentResolution, Letter, PhoneCall, RecurringAppointMaster, ServiceAppotion, Task
<li>bizible2_bizible_abtest
<li>bizible2_bizible_attribution_touchpoint
<li>bizible2_bizible_event
<li>bizible2_bizible_history
<li>bizible2_bizible_touchpoint
<p>
Kontaktpunkter som skapats och andra data skrivs in i anpassade bizibla fält på konto, Campaign, CampaignResponse, Contact, Lead, List, Opportunity och PhoneCall</td>
    <td><b>Marketo Measure användarbehörigheter</b>
<br>
Vi rekommenderar att du skapar en dedikerad Marketo Measure-användare i Dynamics så att du kan exportera och importera data till för att undvika problem med andra användare i CRM. Notera användarnamn och lösenord liksom URL-adressen till slutpunkten som kommer att användas när du skapar Marketo Measure-kontot.
<p>
<b>Säkerhetsroller</b>
<br>
Om din organisation använder Dynamics-säkerhetsroller måste du kontrollera att den anslutna användaren eller den dedikerade Marketo Measure-användaren har tillräcklig läs-/skrivbehörighet för de nödvändiga enheterna.
<br>
Säkerhetsroller finns här: Inställningar &gt; Säkerhet &gt; Säkerhetsroller
<br>
För anpassade Marketo Measure-enheter behöver vi fullständig behörighet för alla våra enheter.
<p>
<b>Fältbehörigheter i Dynamics Standard</b>
<br>
<a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Marketo Measure Dynamics Schema</a>
<p>
<b>Anpassade Dynamics-fältbehörigheter</b>
<br>
Vi behöver läsåtkomst för alla fält på lead- eller kontaktenheten som kunden vill använda för anpassade regler för utelämna/ta bort kontaktpunktsinställningar.
<br>
Vi behöver läsåtkomst för alla fält i lead- eller säljprojektsenheten som kunden vill använda för segmentregler eller för Stage Mapping.
<br>
Vi behöver läsåtkomst för alla fält i Campaign-, CampaignResponse- och List-entiteterna som kunden vill använda för att synkronisera Campaign-/MarketingList-medlemmar.
</td>
  </tr>
  <tr>
    <td>Facebook</td>
    <td>Ad Platform Data</td>
    <td>Vi kan integrera med Facebook för att
<p>
<li>Importera kundannonser</li>
<li>Importera kostnadsdata för kundannonser</li>
<li>Uppdatera klientens annonser genom att lägga till URL-parametrar</li>
<p>
Marketo Measure spårar konton, kampanjer, annonsgrupper, annonser, filter-ID och URL:er.</td>
    <td><li>Behörighet för annonshantering krävs för att skapa kampanjer, hantera annonser eller hämta annonsstatistik.</li>
<li>E-postbehörighet krävs för att användare ska kunna logga in på sin Facebook-e-postadress.</li>
<p>
<b>Omfång</b>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/ads_management/">ads_management</a>
<br>
<li>Skapa kampanjer, hantera annonser och hämta statistik via programmering.</li>
<li>Bygg annonsverktyg som ger innovativa lösningar och ett differentierat värde för annonsörer.</li>
<br>
<br>
<a href="https://developers.facebook.com/docs/permissions/reference/email">e-post</a>
<br>
<li>Kommunicera med människor och låt dem logga in i din app med den e-postadress som är kopplad till deras Facebook-profil.</li></td>
  </tr>
  <tr>
    <td>LinkedIn</td>
    <td>Ad Platform Data
    <p>
    Systemdata för B2B (Lead Gen-formulärdata, inklusive formulär och inskickade formulär, som kategoriseras som CRM-aktivitet).</td>
    <td>Marketo Measure håller på att spåra LinkedIn Ads Campaigns, Creative Cloud och kostnadsdata, liksom Lead Gen Forms och svar. Baserat på importerade data kan vi generera kontaktpunkter från LinkedIn och koppla leadformulärssvar till leads för kunder.</td>
    <td><li>Kampanjhanteraren eller kontohanterarrollen krävs för att Marketo Measure ska kunna hämta kostnadsdata. (Omfattningsrad 1)</li>
    <br>
    <li>För att Marketo Measure ska få åtkomst till data i lead-genererade formulär krävs superadmin (sidadministratörsroll, omfångsrad 2) eller lead-Gen Forms Manager (rollen för betald mediaadministratör, omfångsrad 3)</li>
    <br>
    <li>Superadmin (sidadministratörsroll, omfångsrad 2) eller sponsrad innehållsförhandsgranskning (rollen Betald medieadministratör, omfångsrad 3) krävs för att Marketo Measure ska kunna hantera automatisk taggning</li>
    <p>
    <b>Omfång</b>
    <br>
    <a href="https://www.linkedin.com/campaignmanager/accounts">Ställ in användarroll på portalen (kräver inloggning på LinkedIn-konto)</a> - <a href="https://www.linkedin.com/help/lms/answer/a425731/user-roles-and-functions-in-campaign-manager">Översikt över användarroller</a>: Användarroll, visa och hantera användarbehörighet, tilldela roller som kontohanterare eller kampanjhanterare
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Konfigurera sidadministratörsroll - <a href="https://www.linkedin.com/help/linkedin/answer/a541981/linkedin-page-admin-roles-overview">Rolldefinitioner för sidadministratör</a>: Sidadministratörsroll, på den önskade administratörssidan
    <p>
    <a href="https://www.linkedin.com/help/linkedin/answer/a570172/add-or-remove-admins-on-your-showcase-page?lang=en">Ställ in rollen för betald mediaadministratör (sök efter betald mediaadministratör) - <a href="https://www.linkedin.com/help/linkedin/answer/a554540">Definitioner för betald medieadministratör</a>: Roller för betald medieadministratör</td>
  </tr>
  <tr>
    <td>Dubbelklicka</td>
    <td>Ad Platform Data</td>
    <td>Marketo Measure håller på att spåra konton, annonsörer, kampanjer, (anpassade) landningssidor, annonser, kreatörer, praktik och webbplatser.</td>
    <td><li>Användarens primära e-postadress för Google-konto krävs</li>
<li>Behörigheter för Campaign Manager krävs för att få åtkomst till kontot för Campaign Manager 360</li>
<ul>
<li>Visa och hantera DoubleClick-annonsrapporter</li>
<li>Visa och hantera annonskampanjer för DoubleClick Campaign Managers</li>
<p>
    <b>Omfång</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a>: Se din primära e-postadress för Google-kontot
    <p>
     <a href="https://www.googleapis.com/auth/dfareporting">https://www.googleapis.com/auth/dfareporting</a>: Visa och hantera DoubleClick-rapporter för annonsörer
    <p>
     <a href="https://www.googleapis.com/auth/dfatrafficking">https://www.googleapis.com/auth/dfatrafficking</a>: Visa och hantera era DCM-annonskampanjer (DoubleClick Campaign Manager)</td>
  </tr>
  <tr>
    <td>AdWords</td>
    <td>Ad Platform Data</td>
    <td>Vi kan integrera med AdWords för att
<p>
<li>Importera kundannonser</li>
<li>Importera kostnadsdata för kundannonser</li>
<li>Uppdatera klientens annonser genom att lägga till URL-parametrar/uppdatera URL-spårningsmallar</li>
<p>
Marketo Measure spårar kampanjer, annonsgrupper, kreatörer, webbplatslänkar och nyckelord.</td>
    <td><li>Användarens primära e-postadress för Google-konto krävs</li>
<p>
    <b>Omfång</b>
    <br>
    <a href="https://www.googleapis.com/auth/userinfo.email">https://www.googleapis.com/auth/userinfo.email</a>: Se din primära e-postadress för Google-kontot</td>
  </tr>
  <tr>
    <td>Bing</td>
    <td>Ad Platform Data</td>
    <td>Marketo Measure spårar konton, kampanjer, annonsgrupper, kreatörer och nyckelord.</td>
    <td><li>Användaren måste ge "offlineåtkomst" via sitt Microsoft-konto (vilket ger Marketo Measure åtkomst till slutanvändarens UserInfo även om användaren inte är inloggad). Se <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access">Microsoft page</a> hur man gör.</li>
<p>
    <b>Omfång</b>
    <br>
    <a href="https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access">https://learn.microsoft.com/en-us/deployoffice/overview-extended-offline-access</a>: Bevara åtkomst till data som du har gett behörighet.</td>
  </tr>
  <tr>
    <td>Marketo Engage</td>
    <td>Systemdata för B2B</td>
    <td>Tack vare integreringen med Marketo kan Marketo Measure samla in Marketo aktiviteter, människor, program och programmedlemskap. Dessutom spårar Marketo Measure Marketo cookies (Munchkin ID) för att länka Marketo webbaktiviteter till Marketo Measure lead-kontaktytor, <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#cookie-mapping">enligt beskrivning här</a>:
    <p>
    <i>Som ett resultat av Marketo Measure-integrationen med Marketo mappas och synkroniseras Marketo Measure cookie-ID:t med Marketo Munchkin-ID:t. Detta gör att luckan stängs så att den anonyma första beröringen kan kopplas till en webbsession i stället för att både FT- och LC-beröringen kan kopplas till en Marketo-aktivitet.</i>
    </td>
    <td>Kunden måste skapa en dedikerad Marketo Engage API-användare och ange autentiseringsuppgifterna för Marketo Measure. Ingen ytterligare behörighetskonfiguration krävs. <a href="/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/set-up-marketo-connection.md#configuring-the-integration">Läs mer</a>.</td>
  </tr>
  <tr>
    <td>Adobe Analytics</td>
    <td>Systemdata för B2B</td>
    <td>Tack vare integreringen av B2B-kundattribut kan båda användare av Marketo Measure och Adobe Analytics berika sina Adobe Analytics-användarprofiler med värdefulla metadata som härleds från Marketo Measure attribueringsmotor och genom synkroniseringsmöjligheterna med CRM (Microsoft Dynamics och Salesforce). <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Läs mer</a>.</td>
    <td>Kunden måste förse Marketo Measure med autentiseringsuppgifter för Alias ID och FTP-server till en plats där data överförs till deras Analytics-instans.
    <p>
    Observera följande information som du behöver för några av de senare stegen i processen:
    <p>
    <li>Alias-ID, som kan vara vilket värde som helst. Vi rekommenderar"marketomeasure_id"</li>
    <li>FTP-serverns värdnamn och autentiseringsuppgifter (användarnamn och lösenord)</li>
    <p>
    <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md#configuring-the-integration">Läs mer</a></td>
  </tr>
  <tr>
    <td>Bizible Javascript</td>
    <td></td>
    <td><a href="/help/marketo-measure-tracking/setting-up-tracking/data-collected-by-javascript.md">Vilka data bizible.js samlar in</a>.</td>
    <td></td>
  </tr>
</tbody>
</table>

>[!MORELIKETHIS]
>
>[Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
