---
unique-page-id: 18874672
description: Hur [!DNL Marketo Measure] och [!DNL Salesforce] Interact - Marketo Measure - produktdokumentation
title: Hur [!DNL Marketo Measure] och [!DNL Salesforce] Interagera
exl-id: c2f9d7ce-c5b8-4664-8f92-cb54255190cd
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '1677'
ht-degree: 0%

---

# Hur [!DNL Marketo Measure] och [!DNL Salesforce] Interagera {#how-marketo-measure-and-salesforce-interact}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Låt oss titta på relationen mellan [!DNL Marketo Measure] och Salesforce.

## Salesforce och [!DNL Marketo Measure] {#salesforce-and-marketo-measure}

När [!DNL Marketo Measure] kontot skapas och [!DNL Salesforce] är ansluten, [!DNL Marketo Measure] kommer att börja skicka marknadsföringsdata till CRM-instansen så länge som [!DNL Marketo Measure] hanterat paket är installerat och [!DNL Marketo Measure] Salesforce-användare har redigeringsbehörigheter.

Om du inte har installerat [!DNL Marketo Measure] Salesforce-paket, [!DNL Marketo Measure] skriver inga data till din Salesforce-instans.

![](assets/1-3.png)

Som standard [!DNL Marketo Measure] exporterar 200 poster per API-kredit varje gång ett jobb skickar data till din CRM. För de flesta kunder ger detta den optimala balansen mellan API-krediter som används av [!DNL Marketo Measure] och CPU-resurskrav för CRM. För kunder med komplexa CRM-konfigurationer, till exempel arbetsflöden och utlösare, kan en mindre gruppstorlek vara användbar för att förbättra CRM-prestanda. I detta syfte [!DNL Marketo Measure] gör att kunderna kan konfigurera batchstorleken för CRM-export. Den här inställningen är tillgänglig på [!UICONTROL Settings] > [!UICONTROL CRM] > [!UICONTROL General] sidan i [!DNL Marketo Measure] webbprogram och kunder kan välja mellan gruppstorlekar på 200 (standard), 100, 50 eller 25.

![](assets/how-bizible-and-salesforce-interact-2.png)

När du ändrar den här inställningen bör du tänka på att mindre gruppstorlekar förbrukar fler API-krediter från din CRM. Du bör bara minska batchstorleken om du har CPU-timeout eller hög CPU-belastning i CRM.

## Salesforce-standardobjekt och -åtkomst {#salesforce-standard-objects-and-access}

I den här listan visas [!DNL Salesforce] Standardobjekt som [!DNL Marketo Measure] interagerar med, liksom med de anpassade fält som vi lägger till i dessa objekt när anslutningen har upprättats och [!DNL Marketo Measure] paketet är installerat. Ut ur lådan, [!DNL Marketo Measure] skriver INTE till någon standard [!DNL Salesforce] Objektfält.

**Lead**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-post</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Status</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SkapadDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedContactId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedOpportunityId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Webbplats</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Företag</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Account__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

**Kontakt**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>Konto</p></td> 
   <td><p>Standard</p></td> 
   <td><span>x</span></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-post</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Skapad den</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

**Skiftläge**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SkapadDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>AngivenE-post</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_FT__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_LC__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

**Konto**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Webbplats</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Engagement_Score__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

**Möjligheter**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>Konto</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td><br></td> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SkapadDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsWon</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ÄrStängd</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>CloseDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>StageName</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Belopp</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Opportunity_Amount__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
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
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>E-post</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Status</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SkapadDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedContactId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>ConvertedOpportunityId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Webbplats</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Företag</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>Typ</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td><br></td> 
  </tr> 
 </tbody> 
</table>

**Kampanjmedlem**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>ID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SkapadDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>SenastÄndradDatum</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsDeleted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>FirstRespondedDate</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>hasResponded</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>KontaktID</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>LeadId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>IsConverted</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>CampaignId</p></td> 
   <td><p>Standard</p></td> 
   <td><p>x</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Touchpoint_Date__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Date__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Contact__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Leade__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Status_Opportunity__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

## [!DNL Marketo Measure] Egna objekt i [!DNL Salesforce] {#marketo-measure-custom-objects-in-salesforce}

Förutom att skapa anpassade fält på SFDC:s standardobjekt, så måste du [!DNL Marketo Measure] paketet är installerat och skapar ett par anpassade objekt. Nedan visas en lista över de anpassade objekten tillsammans med en tabell som anger fälten som [!DNL Marketo Measure] skriver till.

**Kontaktpunkt för köpare**

Buyer Touchpoint är en [!DNL Marketo Measure] Anpassat objekt för att kapsla in marknadsföringsinteraktioner för Kontakter, Leads och Ärenden.

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2_Bizible_Person__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_SF_Campaign__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_Path_c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Type__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Content__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Platform__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Browser__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_City__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Country__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Region__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_MatchType__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Position__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Text__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Medium__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Search_Phrase__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Segment__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_First_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Lead_Creation_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_U_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Destination_URL__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Case__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>

**[!DNL Marketo Measure]Person**

The [!DNL Marketo Measure] Personen är en [!DNL Marketo Measure] Anpassat objekt som är relaterat till både lead-, kontakt- och case-objekt.

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Lead_c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Case__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x </p></td> 
  </tr> 
 </tbody> 
</table>

## Buyer Attribution Touchpoint {#buyer-attribution-touchpoint}

Buyer Attribution Touchpoint är en [!DNL Marketo Measure] Anpassat objekt som kapslar in marknadsföringens påverkan på affärsmöjligheter.

**Buyer Attribution Touchpoint**

<table> 
 <tbody> 
  <tr> 
   <th><p>Fält</p></th> 
   <th><p>Standard/anpassad</p></th> 
   <th><p>Läs</p></th> 
   <th><p>Skriv</p></th> 
  </tr> 
  <tr> 
   <td><p>bizible2__Account__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_SF_Campaign__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Contact__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Opportunity__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__UniqueId__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Marketing_Channel_Path_c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Type__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Ad_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Content__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Group_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Campaign_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Placement_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Site_Name__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Form_URL_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Platform__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Browser__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_City__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Country__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Geo_Region__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Id__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_MatchType__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Position__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Keyword_Text__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Landing_Page_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Medium__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Referrer_Page_Raw__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Search_Phrase__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Date__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Touchpoint_Source_c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2__Segment__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_First_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Lead_Conversion_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_U_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_W_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Custom_Model__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Attribution_Custom_Model_2__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_First_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Lead_Creation_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_U_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_W_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Custom_Model__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Count_Custom_Model_2__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Ad_Destination_URL__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_First_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Lead_Creation_Touch__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_U_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_W_Shaped__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Custom_Model__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
  <tr> 
   <td><p>bizible2_Revenue_Custom_Model_2__c</p></td> 
   <td><p>Egen</p></td> 
   <td><p>x</p></td> 
   <td><p>x</p></td> 
  </tr> 
 </tbody> 
</table>
