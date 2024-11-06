---
unique-page-id: 18874672
description: Hur [!DNL Marketo Measure] och [!DNL Salesforce] interagerar - Marketo Measure - Produktdokumentation
title: Hur [!DNL Marketo Measure] och [!DNL Salesforce] interagerar
exl-id: c2f9d7ce-c5b8-4664-8f92-cb54255190cd
feature: Salesforce
source-git-commit: 9ef6d16a73ef25846b90902eb22a544432c33931
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 6%

---

# Så här interagerar [!DNL Marketo Measure] och [!DNL Salesforce] {#how-marketo-measure-and-salesforce-interact}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Låt oss titta närmare på relationen mellan [!DNL Marketo Measure] och Salesforce.

## Salesforce och [!DNL Marketo Measure] {#salesforce-and-marketo-measure}

När [!DNL Marketo Measure]-kontot har skapats och [!DNL Salesforce] har anslutits börjar [!DNL Marketo Measure] överföra marknadsföringsdata till CRM-instansen så länge det [!DNL Marketo Measure] hanterade paketet är installerat och [!DNL Marketo Measure] Salesforce-användaren har redigeringsbehörighet.

Om du inte har installerat Salesforce-paketet [!DNL Marketo Measure] skriver [!DNL Marketo Measure] inga data till din Salesforce-instans.

![](assets/1-3.png)

Som standard exporterar [!DNL Marketo Measure] 200 poster per API-kredit varje gång ett jobb skickar data till din CRM. För de flesta kunder ger detta den optimala balansen mellan API-krediter som används av [!DNL Marketo Measure] och CPU-resurskrav i CRM. För kunder med komplexa CRM-konfigurationer, till exempel arbetsflöden och utlösare, kan en mindre gruppstorlek vara användbar för att förbättra CRM-prestanda. Därför tillåter [!DNL Marketo Measure] kunder att konfigurera CRM-exportens batchstorlek. Den här inställningen är tillgänglig på sidan [!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL General] i webbprogrammet [!DNL Marketo Measure] och kunderna kan välja mellan gruppstorlekar på 200 (standard), 100, 50 eller 25.

![](assets/how-bizible-and-salesforce-interact-2.png)

När du ändrar den här inställningen bör du tänka på att mindre gruppstorlekar förbrukar fler API-krediter från din CRM. Du bör bara minska batchstorleken om du har CPU-timeout eller hög CPU-belastning i CRM.

## Salesforce-användarbehörigheter {#salesforce-connected-user-permissions}

**Marketo Measure Administrator Permission Set for Dedicated User**: Låter SFDC-administratören utföra CRUD-åtgärder på Marketo Measure-objekt.

**Visa och redigera behörighetsgrupp för konverterade leads**: Detta gör att Marketo Measure kan dekorera leads efter att de har konverterats till kontakter.

**Kryssruta för användare av Salesforce-marknadsföring**: Tillåter användare att skapa kampanjer och använda guiden för kampanjimport.

* Vi behöver ytterligare behörigheter för Campaign&quot;Create&quot; och&quot;Update&quot; i dina CRM.

* När en kontaktyta skapas från en webbaktivitet måste vi länka den till en kampanj. Eftersom webbaktiviteter inte har motsvarande CRM-kampanjer måste vi skapa en för att skapa den här länken. Detta gäller både lead- och säljkontaktytor. Uppdateringsbehörighet krävs eftersom anropet vi använder är &quot;upsert&quot; - om posten finns uppdaterar vi den, annars skapar vi den. Detta gäller endast kampanjer vi skapar.

**Marketo Measure Standard User**: Ger en användare möjlighet att läsa poster från Marketo Measure-objekt.

## Salesforce Standard Objects och Access {#salesforce-standard-objects-and-access}

Här visas [!DNL Salesforce] standardobjekt som [!DNL Marketo Measure] interagerar med och de anpassade fält som vi lägger till i dessa objekt när anslutningen har upprättats och [!DNL Marketo Measure]-paketet har installerats. [!DNL Marketo Measure] skrivs INTE i några vanliga [!DNL Salesforce]-objektfält.

**Lead**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>E-post</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SkapadDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedContactId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ConvertedOpportunityId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsConverted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Webbplats</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Företag</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2__Account__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr>
 </tbody> 
</table>

**Kontakt**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>Konto</td> 
   <td>Standard</td> 
   <td><span>x</span></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>E-post</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Skapad den</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr>
 </tbody> 
</table>

**Konto**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Webbplats</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2_Engagement_Score__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

**Möjlighet**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>Namn</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>Konto</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SkapadDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsWon</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>ÄrStängd</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CloseDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>StageName</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Belopp</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2_Bizible_Opportunity_Amount__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

**Roll för säljprojektskontakt**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SkapadDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr>
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>OpportunityId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>KontaktID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr>

<tr> 
   <td>ÄrPrimär</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Roll</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Campaign**

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>E-post</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SkapadDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Webbplats</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Företag</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>Typ</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td><br></td> 
  </tr>
  <tr> 
   <td>Namn</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td>x</td> 
  </tr>
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>

**Kampanjmedlem**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SkapadDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>SenastÄndradDatum</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsDeleted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>FirstRespondedDate</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>hasResponded</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>KontaktID</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>LeadId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>IsConverted</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>CampaignId</td> 
   <td>Standard</td> 
   <td>x</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>bizible2_Bizible_Touchpoint_Date__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Status_Date__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Status_Contact__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Status_Leade__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Status_Opportunity__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>För att Marketo Measure ska kunna hantera borttagningshändelser på ditt Salesforce-konto måste du ha replikeringsbar behörighet för objekten nedan. Replikerbara behörigheter levereras som standard med följande objekt:
>
>* Konto
>* Campaign
>* Kampanjmedlem
>* Kontakt
>* Händelse
>* Lead
>* Möjligheter
>* Uppgift


## [!DNL Marketo Measure] anpassade objekt i [!DNL Salesforce] {#marketo-measure-custom-objects-in-salesforce}

Förutom att skapa anpassade fält i SFDC Standard Objects skapas ett par anpassade objekt när [!DNL Marketo Measure]-paketet har installerats. Nedan visas en lista över de här anpassade objekten tillsammans med en tabell som anger de fält som [!DNL Marketo Measure] ska skriva till.

**Buyer Touchpoint**

Buyer Touchpoint är ett anpassat [!DNL Marketo Measure]-objekt som kapslar in marknadsföringsinteraktioner för kontakter, leads och ärenden.

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>bizible2_Bizible_Person__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_SF_Campaign__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Marketing_Channel__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Marketing_Channel_Path_c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Type__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Content__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Group_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Group_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Campaign_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Campaign_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Placement_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Placement_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Form_URL__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Form_URL_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Platform__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Browser__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_City__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Country__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Region__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_MatchType__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Position__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_Text__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Landing_Page__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Landing_Page_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Medium__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Referrer_Page__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Referrer_Page_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Search_Phrase__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Date__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Source__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Segment__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_First_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_Lead_Creation_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_U_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Destination_URL__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Case__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>

**[!DNL Marketo Measure]person**

Personen [!DNL Marketo Measure] är ett anpassat [!DNL Marketo Measure]-objekt som är relaterat till både lead-, kontakt- och case-objekt.

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Lead_c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Case__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x </td> 
  </tr> 
 </tbody> 
</table>

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

Buyer Attribution Touchpoint är ett anpassat [!DNL Marketo Measure]-objekt som kapslar in marknadsföringens påverkan på affärsmöjligheter.

**Buyer Attribution Touchpoint**

<table> 
 <tbody> 
  <tr> 
   <th>Fält</th> 
   <th>Standard/anpassad</th> 
   <th>Läs</th> 
   <th>Skriv</th> 
  </tr> 
  <tr> 
   <td>bizible2__Account__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_SF_Campaign__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Contact__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Opportunity__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__UniqueId__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Marketing_Channel__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Marketing_Channel_Path_c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Type__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Ad_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Content__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Group_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Group_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Campaign_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Campaign_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Placement_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Placement_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Site_Name__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Form_URL__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Form_URL_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Platform__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Browser__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_City__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Country__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Geo_Region__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_Id__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_MatchType__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Position__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Keyword_Text__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Landing_Page__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Landing_Page_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Medium__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Referrer_Page__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Referrer_Page_Raw__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Search_Phrase__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Date__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Touchpoint_Source__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2__Segment__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_First_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_Lead_Conversion_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_U_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_W_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_Custom_Model__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Attribution_Custom_Model_2__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_First_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_Lead_Creation_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_U_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_W_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_Custom_Model__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Count_Custom_Model_2__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Ad_Destination_URL__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_First_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_Lead_Creation_Touch__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_U_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_W_Shaped__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_Custom_Model__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
  <tr> 
   <td>bizible2_Revenue_Custom_Model_2__c</td> 
   <td>Egen</td> 
   <td>x</td> 
   <td>x</td> 
  </tr> 
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>[Översikt över integreringsbehörigheter](/help/api-connections/utilizing-marketo-measures-api-connections/integration-permissions-overview.md){target="_blank"}
