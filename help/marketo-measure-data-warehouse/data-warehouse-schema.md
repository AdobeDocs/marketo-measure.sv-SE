---
unique-page-id: 35586140
description: Data Warehouse Schema - Marketo Measure - Produktdokumentation
title: Data Warehouse Schema
exl-id: f1895eb1-a32d-4c43-93fb-0aa838527946
feature: Data Warehouse
source-git-commit: 3165d821000a1369ed6fdff3f786ae6632ea39f4
workflow-type: tm+mt
source-wordcount: '20697'
ht-degree: 0%

---

# Data Warehouse Schema {#data-warehouse-schema}

Med Data Warehouse kan ni spåra så mycket ni vill, rapportera om era attribueringsdata var ni vill och koppla in dem i andra datauppsättningar.

>[!IMPORTANT]
>
>* Rader med ett värde för _DELETED_DATE behålls i 7 dagar och tas sedan bort från Snowflake.
>* De tidszoner som används i Snowflake följer UTC (Coordinated Universal Time).

>[!NOTE]
>
>[Klicka här](#sample-queries) om du vill visa exempelfrågor längst ned i den här artikeln.

## Entitetsrelationsdiagram {#entity-relationship-diagrams}

The _Datans Warehouse datamodell_ ERD visar hur data i datalagret är avsedda att flöda och länkas samman. Det här diagrammet innehåller inte alla tabeller som är tillgängliga i datalagret eftersom vissa av dem representerar mappningstabeller, vyer av andra tabeller som redan finns eller borttagna tabeller som vi inte rekommenderar att du använder fler. Se de detaljerade beskrivningarna av tabeller och kolumner som finns i datalagret nedan. Många av dessa tabeller innehåller deformerade fält, men det här diagrammet är den rekommenderade datamodellen, som i stället utnyttjar data från dimensionella tabeller.

Ytterligare _Annonserar dimensionell datamodell_ ERD visar hur tabeller för annonser som är specifika dimensioner bäst kan länkas tillbaka till tabellerna i huvuddatamodellen. Även om annonsdimensionerna även är denormaliserade i andra tabeller representerar detta den rekommenderade modellen för att förena de här dimensionerna.

_Klicka på en bild för att se dess fullstorleksversion_

<table style="table-layout:auto"> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><strong>Datans Warehouse datamodell</strong></td> 
   <td><strong>Annonserar dimensionell datamodell</strong></td> 
  </tr> 
  <tr> 
   <td> 
    <div> 
     <p><a href="assets/data-warehouse-data-model.pdf"><img src="assets/data-warehouse-data-model-thumb.png"></a></p> 
    </div></td>
   <td> 
    <div> 
     <p><a href="assets/ads-dimensional-data-model.pdf"><img src="assets/ads-dimensional-data-model-thumb.png"></a></p>
    </div></td> 
  </tr> 
 </tbody> 
</table>

## Vyer {#views}

### BIZ_ACCOUNTS {#biz-accounts}

Konton som importerats från källsystemet.

<table>
  <tbody>
    <tr>
      <th><strong>Kolumn</strong></th>
      <th><strong>Datatyp</strong></th>
      <th><strong>Beskrivning</strong></th>
      <th><strong>Exempeldata</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Konto-ID från källsystemet.</td>
      <td>0013100001kpAZxAAM</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Skapad av kontot från källsystemet.</td>
      <td>2016-08-28 00:32:55 000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Det senast ändrade datumet för kontot från källsystemet.</td>
      <td>2018-08-01 17:38:30 000</td>
    </tr>
    <tr>
      <td>NAMN</td>
      <td>varchar</td>
      <td>Kontonamnet från källsystemet.</td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>WEB_SITE</td>
      <td>varchar</td>
      <td>Webbplats för kontot, som den registrerats i källsystemet, används för mappning av lead till konto.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_RATING</td>
      <td>varchar</td>
      <td>A letter grade (A, B, C, D, N/A) that generated from the [!DNL Marketo Measure] Machine Learning-modell. Detta blir null om ABM är inaktiverat.</td>
      <td>B</td>
    </tr>
    <tr>
      <td>ENGAGEMENT_SCORE</td>
      <td>tal(38,19)</td>
      <td>En numerisk poäng beräknad med [!DNL Marketo Measure] Maskininlärning för att generera Predictive Engagement Score (Engagement_Rating). Detta blir null om ABM är inaktiverat.</td>
      <td>0,1417350147058800000</td>
    </tr>
    <tr>
      <td>DOMÄN</td>
      <td>varchar</td>
      <td>Den tolkade versionen av webbplatsen, endast domänen lagrades.</td>
      <td>adobe</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolesk</td>
      <td>Anger om posten tas bort i källsystemet eller inte.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Account_Type__c": "Security", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACCOUNT_TO_EMAILS {#biz-account-to-emails}

Mappningstabell mellan kända lead-/kontaktadresser och konton. Tabellen är tom om ABM är inaktiverat.

<table>
  <tbody>
    <tr>
    <th><strong>Kolumn</strong></th>
      <th><strong>Datatyp</strong></th>
      <th><strong>Beskrivning</strong></th>
      <th><strong>Exempeldata</strong></th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Ett unikt ID för posten.</td>
      <td>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13 000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för källsystemkonto.</p>
      </td>
      <td>
        <p>0013100001phrBAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-postadress som har mappats till kontot, antingen via kontaktrelationer eller lead-till-konto-mappning.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det senast ändrade datumet för kontot från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-31 23:53:39 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Skapad av kontot från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-18 22:01:32 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten betraktas som borttagen eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_ACTIVITIES {#biz-activities}

Aktiviteter som importerats från ett källsystem eller ett anslutet annonskonto.

<table>
  <tbody>
  <tr>
    <th><strong>Kolumn</strong></th>
    <th><strong>Datatyp</strong></th>
    <th><strong>Beskrivning</strong></th>
    <th><strong>Exempeldata</strong></th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Aktivitets-ID från källsystemet.</p>
      </td>
      <td>
        <p>1678625515</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för den lead som är associerad med aktiviteten.</td>
      <td>
        <p>15530482</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är associerad med aktiviteten.</p>
      </td>
      <td>
        <p>13792552</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för aktivitetstypen från källsystemet.</p>
      </td>
      <td>
        <p>104</p>
      </td>
    </tr>
    <tr>
      <td>ACTIVITY_TYPE_NAME</td>
      <td>varchar</td>
      <td>Aktivitetsnamnet från källsystemet.</td>
      <td>
        <p>ändra status för progression</p>
      </td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Startdatum för aktiviteten från källsystemet.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestapm_ntz</td>
      <td>Slutdatum för aktiviteten från källsystemet.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>CAMPAIGN_ID</td>
      <td>varchar</td>
      <td>Id för den kampanj som aktiviteten är en del av, från källsystemet.</td>
      <td>
        <p>li.508038570.147643566</p>
      </td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Identifierar källsystemets typ.</td>
      <td>Marketo</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Det datum då raden skapades i källsystemet.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum då raden senast ändrades i källsystemet.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>IS_DELETD</td>
      <td>boolesk</td>
      <td>Anger om posten betraktas som borttagen i källsystemet.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>AD_FORM_ID</td>
      <td>varchar</td>
      <td>ID för annonseringsformuläret som aktiviteten är en del av, från källsystemet.</td>
      <td>li.507063119.3757704</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADS {#biz-ads}

Annonser som importerats från anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p><strong>Kolumn</strong></p>
      </th>
      <th>
        <p><strong>Datatyp</strong></p>
      </th>
      <th>
        <p><strong>Beskrivning</strong></p>
      </th>
      <th>
        <p><strong>Exempeldata</strong></p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för annonsen.</p>
      </td>
      <td>
        <p>fb.106851586409075.605204428804.605204429004.60534570 66804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annons-ID från källsystemet.</p>
      </td>
      <td>
        <p>6053457066804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen importerades från.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som annonsen importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Konto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för annonsören för annonsen, speciellt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsören för annonsen, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsgruppen.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsgruppens namn.</p>
      </td>
      <td>
        <p>Annonsuppsättning för annons B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanj för annonsen.</p>
      </td>
      <td>
        <p>fb.106851586409075.6052044288804</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskampanjen.</p>
      </td>
      <td>
        <p>Kampanj för generering av leads</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida annonsen fortfarande är aktiv i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om annonsen har tagits bort i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen, från källsystemet.</p>
      </td>
      <td>
        <p>Annons 2</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonsen behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td>
        <p>fb.106851586409075.6052044288804.6052044290004</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet "Ad".</p>
      </td>
      <td>
        <p>Annons</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsprovidern för annonsen.</p>
      </td>
      <td>
        <p>Facebook</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL-adressen till landningssidan.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tidigare värde för URL_CURRENT.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vad URL:en kommer att dekoreras med [!DNL Marketo Measure] parametrar.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_ALTENATIVES</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Importerad från källsystemet.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_ADVERTISERS {#biz-advertisers}

Annonsörer importerade från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för Advertiser.</p>
      </td>
      <td>
        <p>dc.6114.9143143</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Advertiser-ID:t från källsystemet.</td>
      <td>9143143</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen importerades från.</p>
      </td>
      <td>
        <p>fb.106851586409075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som annonsen importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Konto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Advertiser, speciellt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Advertiser, speciellt Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför Advertiser i någon annonshierarki.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför Advertiser i någon annonshierarki.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon annonskampanj ovanför Advertiser i någon annonshierarki.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon kampanj ovanför annonskampanjen i någon annonshierarki.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om Advertiser fortfarande är aktiv i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om Advertiser har tagits bort eller inte i källsystemet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:59 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Advertiser-namnet från källsystemet.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonseraren behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"Advertiser".</p>
      </td>
      <td>
        <p>Annonsör</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsleverantören för Advertiser.</p>
      </td>
      <td>
        <p>Dubbelklicka</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_ACCOUNTS {#biz-ad-accounts}

Annonskonton som importerats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En unik identifierare för annonskontot.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för annonskonto från källsystemet.</td>
      <td>
        <p>6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Förväntades vara null eftersom detta är posten för annonskonton i annonshierarkin.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Förväntades vara null eftersom detta är posten för annonskonton i annonshierarkin.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntade att bli null eftersom det inte finns någon annonsör ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntade att bli null eftersom det inte finns någon annonsör ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon annonsgrupp ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon annonsgrupp ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon annonskampanj ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntas vara null eftersom det inte finns någon annonskampanj ovanför annonskonton i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonskontot fortfarande är aktivt i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om annonskontot har tagits bort i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-09-06 12:54:37 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Namn på annonskontot från källsystemet.</td>
      <td>
        <p>[!DNL Marketo Measure] Annonskonto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonseraren behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet "Konto".</p>
      </td>
      <td>
        <p>Konto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseringsprovidern för annonskontot.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_CURRENCY_UNIT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Valutakoden som används för annonskontot från källsystemet.</p>
      </td>
      <td>
        <p>USD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COMPANY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern bearbetning.</td>
      <td>1933789</td>
    </tr>
    <tr>
      <td>
        <p>KÄLLA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Tolkad från URL:en från utm_source.</td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Tolkad från URL:en från utm_medium.</td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_COST</p>
      </td>
      <td>
        <p>tal(38,19)</p>
      </td>
      <td>
        <p>Mängden utgift som importerats under de senaste 30 dagarna, endast för AdWords.</p>
      </td>
      <td>
        <p>17260,000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_IMPRESSIONS</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Antalet visningar från de senaste 30 dagarna, endast för AdWords.</p>
      </td>
      <td>
        <p>730060</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CLICKS</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Antalet klick från de senaste 30 dagarna som endast gäller för AdWords.</p>
      </td>
      <td>
        <p>3400</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_30_DAYS_CONVERSIONS</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Antalet konverteringar som rapporterats från de senaste 30 dagarna och som endast gäller för AdWords.</p>
      </td>
      <td>
        <p>180</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Spårningsmallen som lagts till på nivå Ad Account för AdWords eller Bing för taggning av landningssidor.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_CAMPAIGNS {#biz-ad-campaigns}

Kampanjer som importerats från anslutna annonskonton, källsystem, utm och självrapporterade.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Unikt ID för kampanjen.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Kampanj-ID:t från källsystemet.</td>
      <td>
        <p>285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som kampanjen importerades från.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som kampanjen importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Campaigns annonsörer, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på Advertiser för Campaign, speciellt för Doubleclick.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns någon annonsgrupp ovanför Campaign i någon annonshierarki.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns någon annonsgrupp ovanför Campaign i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Unikt ID för kampanjen, använd fältet ID i stället.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Campaign, använd fältet Namn i stället.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida Campaign fortfarande är aktivt i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om Campaign har tagits bort eller inte i källsystemet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen.</p>
      </td>
      <td>
        <p>Återmarknadsföring för partners</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om kampanjen behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"Campaign".</p>
      </td>
      <td>
        <p>Campaign</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseringsprovidern för kampanjen.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DAILY_BUDGET</p>
      </td>
      <td>
        <p>tal(38,19)</p>
      </td>
      <td>
        <p>Den dagliga budget som anges i annonsplattformen för Campaign.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Spårningsmallen som lagts till på Campaign-nivån för AdWords eller Bing för taggning av landningssidor.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_FORMS {#biz-ad-forms}

Lägg till Forms som importerats från alla anslutna annonskonton.

<table>
  <tr>
    <th>
      <p>Kolumn</p>
    </th>
    <th>
      <p>Datatyp</p>
    </th>
    <th>
      <p>Beskrivning</p>
    </th>
    <th>
      <p>Exempeldata</p>
    </th>
  </tr>
  <tbody>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för annonsformuläret.</p>
      </td>
      <td>
        <p>li.507063119.3757704</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonseringsformuläret importerades från.</p>
      </td>
      <td>
        <p>li.507063119</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som annonseringsformuläret importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Borttagen status från källsystemet. Ange som borttagen om statusen är Utkast, Arkiverat eller Avbrutet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:35:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsformulärets namn.</p>
      </td>
      <td>
        <p>NSPA Ebook LGF (maj 2020)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"AdForm".</p>
      </td>
      <td>
        <p>AdForm</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsprovidern för annonsformuläret.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BESKRIVNING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Beskrivning av annonsformuläret.</p>
      </td>
      <td>
        <p>Läs om hur intelligent automatisering kan öka effektiviteten i processer vid låneansökningar.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Rubrik för annonsformuläret.</td>
      <td>
        <p>Det är dags att automatisera refinansieringsprocessen</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Landnings-URL för annonseringsformuläret.</td>
      <td>
        <p>https://adobe.com/blog/refinancing-application-process/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FRÅGOR</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Lista med frågor för annonsformuläret.</td>
      <td>
        <p>Förnamn:Efternamn:E-postadress:Land/region:Jobbtitel:Företagsnamn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Status för annonsformuläret.</p>
      </td>
      <td>
        <p>skickat</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>ID för källan som posten kommer från.</td>
      <td>aw.3284209</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_GROUPS {#biz-ad-groups}

Annonsgrupper som importerats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för annonsgruppen.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955.23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Annonsgrupps-ID:t från källsystemet.</td>
      <td>
        <p>23105326115</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonskonfigurationen importerades från.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som annonskonfigurationen importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp i annonshierarkin i dubbelklickning.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp i annonshierarkin i dubbelklickning.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det här är posten för annonsgruppen i hierarkin.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det här är posten för annonsgruppen i hierarkin.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanj för annonskoncern.</p>
      </td>
      <td>
        <p>aw.6601259029.317737955</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på kampanj för annonskoncern.</p>
      </td>
      <td>
        <p>Intäktsfördelning</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonskontot fortfarande är aktivt i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om annonskontot har tagits bort i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:14.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsgruppens namn.</p>
      </td>
      <td>
        <p>Intäktsattribuering - kontobaserad</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om annonseraren behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"AdGroup".</p>
      </td>
      <td>
        <p>AdGroup</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsprovidern för annonskoncern.</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NETWORK_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Mediet/medierna som annonskoncernen körs på.</p>
      </td>
      <td>
        <p>Sök, visa, YouTube_Search, YouTube_Watch</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Spårningsmallen som lagts till på nivå Ad Account för AdWords eller Bing för taggning av landningssidor.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-5594512713562690000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_AD_PROVIDERS

<p>Annonsleverantörer från alla anslutna annonskonton, inklusive en post för självrapporterade om tillämpligt.</p>

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för annonseringsprovidern.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsleverantörens namn.</p>
      </td>
      <td>
        <p>Bing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>4783788151269206864</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_ATTRIBUTION_TOUCHPOINTS {#biz-attribution-touchpoints}

<p>Buyer Attribution Touchpoints, alla kontaktytor som är kopplade till en möjlighet.</p>
<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för Buyer Attribution Touchpoint (BAT).</p>
      </td>
      <td>
        <p>BAT2_0060Z00000lFHtOQAW_</p>
        <p>0030Z0003K5bpKQAR_2017-06-20:01-05-20-6193330.0b5c5678807c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-09-01 04:53:53 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för affärsmöjligheten som BAT är hänförligt till.</p>
      </td>
      <td>
        <p>0060Z00000lFHtOQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är kopplad till BAT.</p>
      </td>
      <td>
        <p>0030Z00003K5bpKQAR</p>
      </td>
    </tr>
    <tr>
      <td>E-POST</td>
      <td>varchar</td>
      <td>E-postadress som är kopplad till BAT.</td>
      <td>person@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det konto som BAT tilldelas.</p>
      </td>
      <td>
        <p>0013100001otbIAAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för användarkontaktpunkten som genererade BAT.</p>
      </td>
      <td>
        <p>person@adobe.com_00v1B00003ZbWzHQAV</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum för kontaktytan.</p>
      </td>
      <td>
        <p>2017-06-20 01:05:20 000</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>ID för besökaren som är kopplad till BAT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Typ av aktivitet, webbbesök, webbformulär, webbchatt, telefonsamtal, [CRM]-kampanj eller [CRM]-aktivitet. I CRM kallas det"Touchpoint Type".</p>
      </td>
      <td>
        <p>Webbformulär</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kanalen som kontaktytan hamnar i, enligt definition i de anpassade kanaldefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till som"Marknadskanal - Sökväg".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den första kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</p>
      </td>
      <td>
        <p>ABC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den andra kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</p>
      </td>
      <td>
        <p>Ja</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den tredje kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</p>
      </td>
      <td>
        <p>SMB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den fjärde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td>
        <p>Nytt företag</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den femte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den sjätte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den sjunde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den åttonde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den nionde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den tionde kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den elfte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den tolfte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den 13:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den 14:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den 15:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till"Segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen upptäckte den webbläsare som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Krom</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av webbläsaren som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade plattform som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av plattformen som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. I CRM kallas den"landningssida".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-äs sanning bakom kostnad per lead</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. En rå landningssida kommer att innehålla alla frågeparametrar i URL:en. I CRM kallas det"landningssida - Raw".</p>
      </td>
      <td>
        <p>http://www.adobe.com/blog/uncover-truth?utm_content=2732869&amp;utm_medium=social&amp;utm_source=linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. I CRM kallas det"Refererarsida".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. En råhänvisningssida kan innehålla frågeparametrar i URL:en. I CRM refereras till"Refererarsida - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i tabellen Attribution_Touchpoints, utan i tabellen Form_Submits. I CRM refereras till som "formulär-URL".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i tabellen Attribution_Touchpoints, utan i tabellen Form_Submits. En sida med Raw-formulär kan innehålla frågeparametrar i URL:en. I CRM refereras till"Form URL - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/intro-guide-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när formuläret skickades.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades den ort som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>San Francisco</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är det område som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>Kalifornien</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAND</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades det land som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>USA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera mediet som resulterade i kontaktytan. Detta kan antingen tolkas ut från URL:en från utm_medium. Eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "cpc" eller "display".</p>
      </td>
      <td>
        <p>social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera källan som resulterade i kontaktytan. Detta kan tolkas från URL:en från utm_source, vanligtvis inställd som CRM Campaign om den synkroniserades från CRM, eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "Google AdWords" eller "Facebook". Refereras i CRM till"Kontaktpunktskälla".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Värdet som användaren angav i webbläsaren för att söka efter och hamnade på webbplatsen. Beroende på nyckelordsköp kan det här matcha nyckelorden som köpts från plattformen Betald sökning eller inte.</p>
      </td>
      <td>
        <p>google [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsplattform [!DNL Marketo Measure] har kunnat lösa sig från, vanligtvis en av våra integreringspartners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonseraren från annonskontot som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseraren från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för webbplatsen från annonskontot där annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatsen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>Marknadsattribuering</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google AdWords.</p>
      </td>
      <td>
        <p>Marknadsattribuering - allmänt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen från annonskontot som annonsen löstes från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>
        <p>dc.6114.8882972.25272734.492579576</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen från annonskontot där annonsen löstes. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>
        <p>Webbinarium - marginallist</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Creative-objektet från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.182716179597</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det Creative-objekt från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>B2B Marketing Attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Ladda ned guiden för marknadschefer</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den andra raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Läs om hur attribuering mäter avkastningen genom att koppla marknadsföringsaktiviteter till intäkter</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Landningssidan som klickas igenom från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det egna URL-namn som visas på sökannonsen, hämtat från annonskontot som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>http://info.adobe.com/CMOs-Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för nyckelordet som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.317738075.23105327435.4838421670</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det nyckelord som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning)</p>
      </td>
      <td>
        <p>marknadsattribuering</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den typ av matchning som hittas mellan sökfrasen och det köpta nyckelordet.</p>
      </td>
      <td>
        <p>Exakt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida denna kontaktyta behandlas som den första kontakten i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som den inledande kontakten i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som ett sätt att skapa affärsmöjligheter i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida denna kontaktyta behandlas som den slutna kontakten i affärsmöjlighetsresan eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGES_TOUCHED</p>
      </td>
      <td>varchar</td>
      <td>Det här fältet har tagits bort. Använd Stage_Transitions-tabellerna för sceninformation.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om kontaktytan hade en formulärfyllning under sessionen eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som det första intrycket av affärsmöjlighetens resa</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är en första beröring (se Is_First_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är en beröring för att skapa leads (se Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en oformad beröring (se Is_First_Touch och Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en w-formad beröring (se Is_First_Touch, Is_Lead_Creation_Touch och Is_Opp_Creation_Touch).</p>
      </td>
      <td>
        <p>0,0153374234214425</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en fullständig banmodell (se Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</p>
      </td>
      <td>
        <p>0,0143061513081193</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>number(22,19)</td>
      <td>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en anpassad modell (se Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch).</td>
      <td>0,0143061513081193</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om den här kontaktytan tas bort.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_ROW_KEY</p>
      </td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CAMPAIGN_MEMBERS {#biz-campaign-members}

Kampanjmedlemmar importerade från källsystemet. Det här registret är tomt om Campaign Sync är inaktiverat.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kampanjmedlems-ID från källsystemet.</p>
      </td>
      <td>
        <p>00v0Z00001VzdLQAT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det senaste ändringsdatumet för Campaign-medlemmen från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Skapad av Campaign-medlemmen från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-31 20:49:54.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_TOUCH_POINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum och tid som kunden ställer in för att åsidosätta kampanjdatumet och använd värdet för slutpunktsdatumet i stället.</p>
      </td>
      <td>
        <p>2018-08-30 18:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den lead som kampanjmedlemmen är knuten till.</p>
      </td>
      <td>
        <p>00Q0Z00013dw4GUAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post till den lead som kampanjmedlemmen är knuten till.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som kampanjmedlemmen är knuten till.</p>
      </td>
      <td>
        <p>00331000032hMxRAAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post till den kontakt som kampanjmedlemmen är knuten till.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Status för Campaign-medlemmen, vanligtvis inställd på Skickat eller Svarat eller ett annat anpassat värde. Den här statusen är kopplad till Campaign_Sync_Type för att avgöra vilka kampanjmedlemmar som kontaktytorna ska skapas för.</p>
      </td>
      <td>
        <p>Skickat</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_RESPONDED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om kampanjmedlemmen har markerats som"Responded" i statusväljaren.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_RESPONDED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då kampanjmedlemmen först svarade.</p>
      </td>
      <td>
        <p>2018-08-30 07:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den relaterade kampanj som kampanjmedlemmen är en del av.</p>
      </td>
      <td>
        <p>Snabba CMO-intervjuer</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den relaterade kampanj som kampanjmedlemmen är en del av.</p>
      </td>
      <td>
        <p>7010Z00001TcKlQAK</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Typen som valts för den relaterade kampanj som kampanjmedlemmen är en del av. Typen används för att mappa marknadsföringskanalen.</p>
      </td>
      <td>
        <p>Offline</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_SYNC_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Avgör vilka Campaign-medlemmar som kontaktytor ska skapas för. Möjliga värden är: Include_All, Include_Responded, Exclude_All.</p>
      </td>
      <td>
        <p>Include_All</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Granskningsfält, anger om en Buyer Touchpoint skapades för leadet eller inte. Om ingen kontaktyta skapades anges orsaken till varför den inte var berättigad.</p>
      </td>
      <td>
        <p>Ingen kontaktyta: Datum utanför modell</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Granskningsfält, anger om en Buyer Touchpoint skapades för kontakten eller inte. Om ingen kontaktyta skapades anges orsaken till varför den inte var berättigad.</p>
      </td>
      <td>
        <p>Kontaktpunkten har skapats</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_SYNC_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Granskningsfält, anger om en slutpunkt för Buyer-attribut har skapats för säljprojektet eller inte. Om ingen kontaktyta skapades anges orsaken till varför den inte var berättigad.</p>
      </td>
      <td>
        <p>Kontaktpunkten har skapats</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten betraktas som borttagen i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Campaign_Type__c":"Dinners","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CHANNELS {#biz-channels}

Marknadsföringskanaler, som de skapats i [!DNL Marketo Measure] program.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för kanalen.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på kanalen.</p>
      </td>
      <td>
        <p>Organic Search.Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>6008900572523230000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datumet då posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datumet då posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datumet då posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONTACTS {#biz-contacts}

Kontakter som har importerats från källsystemet.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kontakt-ID:t från källsystemet.</p>
      </td>
      <td>
        <p>0030Z00003OzioeQAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när kontaktposten senast ändrades från källsystemet.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:53 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum kontaktposten skapades från källsystemet.</p>
      </td>
      <td>
        <p>2018-09-05 05:17:51 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kontaktens e-postadress från källsystemet.</p>
      </td>
      <td>
        <p>persona@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KONTO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det konto som är relaterat till kontakten.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Källa där lead skapades.</p>
      </td>
      <td>
        <p>Annons</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Aktuell fas av kontakten, identifieras som en anpassad fas som kan skapas i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>Demo schemalagd</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Alla tidigare steg för kontakten, identifieras som anpassade steg som kan skapas i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>Öppna - kontakt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>tal(38,19)</p>
      </td>
      <td>
        <p>Den här funktionen har tagits bort. Använd inte den här kolumnen.</p>
      </td>
      <td>
        <p>Ej tillämpligt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie-ID som används för att fylla i från en integrationspartner för att mappa en offlinehändelse till en webbsession. Krav: Aktivera samtalsspårning: Sant</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om posten tas bort i källsystemet eller inte.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolesk</td>
      <td>Används för att deduplicera poster om både en CRM- och Marketo-integrering har konfigurerats. Om det finns dubbletter markeras Marketo Contact som true.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Anger om posten kommer från en CRM- eller Marketo-integrering.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappar en person från en Marketo-integrering med en kontakt från en CRM-integrering. Om det finns både en CRM- och Marketo-integrering är värdet motsvarande ID.</td>
      <td>1234 / 00Q0Z00001OhgTUAR</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>3263982503087870000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CONVERSION_RATES {#biz-conversion-rates}

Valutakonverteringsgrader som importerats från källsystemet.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>tal(38,0)</td>
      <td>Ett unikt ID för posten.</td>
      <td>-5942345438803054604</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>tal(38,0)</td>
      <td>ID-värde för valutan.</td>
      <td>7493833133899044458</td>
    </tr>
    <tr>
      <td>SOURCE_ISO_CODE</td>
      <td>varchar</td>
      <td>ISO-valutakod från källsystemet.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>START_DATE</td>
      <td>timestamp_ntz</td>
      <td>Startdatum för konverteringsgraden.</td>
      <td>2018-11-01 00:00:00,000</td>
    </tr>
    <tr>
      <td>END_DATE</td>
      <td>timestamp_ntz</td>
      <td>Nästa startdatum för konverteringsgraden. (Slutdatumet för konverteringsgraden är end_date minus 1 dag.)</td>
      <td>2018-09-01 00:00:00,000</td>
    </tr>
    <tr>
      <td>CONVERSION_RATE</td>
      <td>tal(38,0)</td>
      <td>Kursen som används för att konvertera valutan till företagets valuta.</td>
      <td>0,76728300</td>
    </tr>
    <tr>
      <td>IS_CURRENT</td>
      <td>boolesk</td>
      <td>Semantiken för det här fältet har skadats. Använd inte.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Det datum då posten skapades i källsystemet.</td>
      <td>2019-03-30 00:54:50 000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i källsystemet.</td>
      <td>2019-03-30 00:54:50 000</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolesk</td>
      <td>Anger om posten betraktas som borttagen i källsystemet.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_COSTS {#biz-costs}

Kostnadsdata som importerats från anslutna annonskonton eller självrapporterade marknadsföringsutgifter.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Ett unikt ID för kostnadsposten.</td>
      <td>aw.6601259029.28514995.21703163075.[AdWords Display]_2018-09-06</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades.</td>
      <td>2018-09-06 12:22:45 000</td>
    </tr>
    <tr>
      <td>COST_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när kostnaden uppkom (eller tillskrevs).</td>
      <td>2018-09-06 00:00:00,000</td>
    </tr>
    <tr>
      <td>KÄLLA</td>
      <td>varchar</td>
      <td>Källa för den rapporterade kostnaden.</td>
      <td>[AdWords display]</td>
    </tr>
    <tr>
      <td>COST_IN_MICRO</td>
      <td>tal(38,0)</td>
      <td>Kostnadsbelopp i miljoner. Användaren måste dividera värdet med 100000.</td>
      <td>1410000</td>
    </tr>
    <tr>
      <td>KLICK</td>
      <td>tal(38,0)</td>
      <td>Antal klick som rapporterats för gruppen för dagen.</td>
      <td>4</td>
    </tr>
    <tr>
      <td>IMPRESSIONER</td>
      <td>tal(38,0)</td>
      <td>Antal visningar som rapporterats för gruppen för dagen.</td>
      <td>4187</td>
    </tr>
    <tr>
      <td>ESTIMATED_TOTAL_POSSIBLE_IMPRESSIONS</td>
      <td>tal(38,0)</td>
      <td>Totalt antal uppskattade visningar från DCM för gruppen för dagen.</td>
      <td>5024</td>
    </tr>
    <tr>
      <td>AD_PROVIDER</td>
      <td>varchar</td>
      <td>Leverantör för vilken kostnaden hämtades.</td>
      <td>Google</td>
    </tr>
    <tr>
      <td>CHANNEL_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID för marknadsföringskanalen, skapad av [!DNL Marketo Measure].</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_NAME</td>
      <td>varchar</td>
      <td>Namn på marknadsföringskanalen som skapats av kunden i [!DNL Marketo Measure] app.</td>
      <td>Display.Google</td>
    </tr>
    <tr>
      <td>CHANNEL_IS_AGGREGATABLE_COST</td>
      <td>boolesk</td>
      <td>Anger om raden innehåller kostnad som kan summeras av kanal. (d.v.s. för att hämta kanalkostnad, summeringsrader där den här kolumnen är lika med true.)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>ADVERTISER_UNIQUE_ID</td>
      <td>varchar</td>
      <td>ID för Advertiser som hämtats från annonsanslutningen, särskilt för Doubleclick-anslutningar.</td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>ADVERTISER_NAME</td>
      <td>varchar</td>
      <td>Namnet på den Advertiser som hämtats från annonsanslutningen, särskilt för Doubleclick-anslutningar.</td>
      <td>[!DNL Marketo Measure] Marknadsföringsanalys</td>
    </tr>
    <tr>
      <td>ADVERTISER_IS_AGGREGATABLE_COST</td>
      <td>boolesk</td>
      <td>Anger om raden innehåller Kostnad som kan summeras av Advertiser. (d.v.s. för att hämta Advertiser-kostnad, summeringsrader där den här kolumnen är lika med true.)</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av konto. (d.v.s. för att hämta kontokostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Campaign som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den kampanj som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>Återmarknadsföring för partners</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av Campaign. (d.v.s. för att få kampanjkostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskoncern som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.21703163075</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskoncern som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>Attributhanteringsprogram | Fras</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av annonsgrupp. (d.v.s. om du vill hämta annonsgruppskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>dc.6114.9131003.24149929.467969200</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den annons som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>Annonsnamn: Ad3-320x50.gif; 320 x 50</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av annons. (d.v.s. för att hämta annonskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den Creative som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>aw.6601259029.285114995.51749608028.266050115160</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den Creative som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>Gartner Magic Quadrant 2019</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller Kostnad som kan summeras av Creative Cloud. (d.v.s. för att få Creative Cost, summerar rader där kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för nyckelordet som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>aw.6601259029.669328935.39419128772.99608705795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det nyckelord som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>sfdc-marknadsattribuering</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av nyckelord. (d.v.s. för att hämta nyckelordskostnad, summerar rader där kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för placeringen som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av montering. (d.v.s. för att hämta placeringskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den webbplats som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den webbplats som hämtats från annonsanslutningen.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_IS_AGGREGATABLE_COST</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av platsen. (d.v.s. för att hämta webbplatskostnad, summerar rader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten betraktas som borttagen i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ISO_CURRENCY_CODE</td>
      <td>varchar</td>
      <td>ISO-kod för valutan, importerad från källsystemet.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>SOURCE_ID</td>
      <td>varchar</td>
      <td>ID för källan som posten kommer från.</td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>tal(38,0)</td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ROW_KEY</p>
      </td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>tal(38,0)</td>
      <td>ID-värde för postens valuta.</td>
      <td>
        <p>-3253183181619994799</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CREATIVES {#biz-creatives}

Kreatörer som har importerats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för den kreativa.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Creative-ID:t från källsystemet.</td>
      <td>
        <p>10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som Creative Cloud importerades från.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som Creative Cloud importerades från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Advertiser for the Creative, specifikt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på Advertiser for the Creative, speciellt for Doubleclick.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsgruppen för Creative Cloud.</p>
      </td>
      <td>fb.106851586409075.6052044288804.6052044290004</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsgruppen för Creative Cloud.</p>
      </td>
      <td>Annonsuppsättning för annons B</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Campaign for the Creative.</p>
      </td>
      <td>
        <p>ba.3284209.132855866</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Campaign for the Creative.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida Creative-programmet fortfarande är aktivt i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om Creative Cloud har tagits bort eller inte i källsystemet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:36:25 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den kreativa, från källsystemet.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om Creative Cloud behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"Creative".</p>
      </td>
      <td>
        <p>Kreativ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsleverantören för Creative Cloud.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den aktuella versionen av URL:en inklusive alla taggar.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td>
        <p>cdn.adobe.com/redir?lp=http%3a%2f%2fwww.pipelinemarketing.com%2f&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}&amp;utm_content={adid}&amp;utm_term={keyword}&amp;utm_campaign=PipelineMarketing.com&amp;utm_source=bing&amp;utm_medium=cpc</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_DISPLAY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den förkortade och egna URL:en som visas i Creative Cloud.</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tidigare värde för URL_CURRENT.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vad URL:en kommer att dekoreras med [!DNL Marketo Measure] parametrar.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_SHORTENED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Den förkortade och egna URL:en som visas i Creative Cloud. (Används endast för LinkedIn Ads.)</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Typen av kreativ, som kan vara Text eller Display</p>
      </td>
      <td>
        <p>Text</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Oavsett om den kreativa personen använder uppgraderade URL:er eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HEADLINE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den kreativa världens främsta rubrik</p>
      </td>
      <td>
        <p>PipelineMarketing.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The copy from the first line of the creative</p>
      </td>
      <td>
        <p>Koppla upp dig och lär dig av intäktsdrivna B2B-marknadsförare. Gå med i communityn.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DESCRIPTION_LINE_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The copy from the second line of the creative</p>
      </td>
      <td>
        <p>Har ni använt analyser? Lämna en recension idag!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Diagnostikfält, för intern bearbetning.</p>
      </td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SHARE_URN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Resurs-ID. (Används endast för LinkedIn Ads.)</p>
      </td>
      <td>
        <p>urn:li:dela:6376987561897848832</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_EVENTS {#biz-crm-events}

Händelser som importerats från källsystemet. Det här registret kommer att vara tomt om aktivitetssynkronisering är inaktiverat.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Händelse-ID:t från källsystemet.</p>
      </td>
      <td>
        <p>00U3100000VLUnEEAX</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då händelsen skapades från källsystemet.</p>
      </td>
      <td>
        <p>2016-12-12 19:32:53 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då händelsen senast ändrades från källsystemet.</p>
      </td>
      <td>
        <p>2018-09-03 08:39:51 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den lead som är associerad med händelsen.</p>
      </td>
      <td>
        <p>00Q0Z00013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post för den lead som är associerad med händelsen.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är associerad med händelsen.</p>
      </td>
      <td>
        <p>0030Z00003OyjbOQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post till kontakten som är kopplad till händelsen.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie-ID som används för att fylla i från en integrationspartner för att mappa en offlinehändelse till en webbsession. Krav: Aktivera samtalsspårning: Sant</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på aktivitetstyp från källsystemet.</p>
      </td>
      <td>
        <p>E-post</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_START_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Startdatum för händelsen, ett av de alternativ som används för att fastställa slutpunktsdatumet.</p>
      </td>
      <td>
        <p>2016-12-16 19:30:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_END_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Slutdatum för händelsen, ett av de alternativ som används för att bestämma slutpunktsdatumet.</p>
      </td>
      <td>
        <p>2016-12-16 21:30:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om posten betraktas som borttagen i källsystemet.</td>
      <td>
        <p>Falskt</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Contact_Type__c":"CMO","Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CRM_TASKS {#biz-crm-tasks}

Uppgifter som importerats från källsystemet. Det här registret fylls i om Aktiviteter, synkronisering eller samtalsspårning är aktiverat.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Aktivitets-ID från källsystemet.</p>
      </td>
      <td>
        <p>00T0Z0004Rf62rUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då uppgiften skapades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-27 18:30:25 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då aktiviteten senast ändrades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-27 18:31:53 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den lead som är associerad med uppgiften.</p>
      </td>
      <td>
        <p>00Q0Z00013eVrxUAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post för den lead som är associerad med uppgiften.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är associerad med uppgiften.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-post till kontakten som är associerad med uppgiften.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie-ID som används för att fylla i från en integrationspartner för att mappa en offlinehändelse till en webbsession. Krav: Aktivera samtalsspårning: Sant</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på aktivitetstyp från källsystemet.</p>
      </td>
      <td>
        <p>Utlysning</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACTIVITY_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum aktiviteten utfördes, ett av alternativen som användes för att fastställa slutpunktsdatumet.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om posten betraktas som borttagen i källsystemet.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Contact_Type__c":"CMO", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CURRENCIES {#biz-currencies}

Tabell över alla ISO-valutor.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>tal(38,0)</td>
      <td>Ett unikt ID för valutaposten.</td>
      <td>139474809945095870</td>
    </tr>
    <tr>
      <td>ISO_CODE</td>
      <td>varchar</td>
      <td>ISO-kod för valutan.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>IS_CORPORATE</td>
      <td>boolesk</td>
      <td>Anger om valutan är företagsvalutan.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_ENABLED</td>
      <td>boolesk</td>
      <td>Anger om valutan är aktiverad i källsystemet.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum då posten senast ändrades [!DNL Marketo Measure].</td>
      <td>2018-08-27 18:30:25 000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i källsystemet.</td>
      <td>2018-08-27 18:30:25 000</td>
    </tr>
    <tr>
      <td>CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i [!DNL Marketo Measure]</td>
      <td>2018-08-27 18:30:25 000</td>
    </tr>
    <tr>
      <td>CREATED_DATE_CRM</td>
      <td>timestamp_ntz</td>
      <td>Det datum då posten skapades i källsystemet.</td>
      <td>2018-08-27 18:30:25 000</td>
    </tr>
    <tr>
      <td>ISO_NUMERIC</td>
      <td>tal(38,0)</td>
      <td>Numerisk kod enligt ISO-standard.</td>
      <td>048</td>
    </tr>
    <tr>
      <td>EXPONENT</td>
      <td>tal(38,0)</td>
      <td>Antalet decimaler mellan den minsta definierade valutaenheten och en hel valutaenhet.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>NAMN</td>
      <td>varchar</td>
      <td>Namnet på valutan.</td>
      <td>Argentinsk peso</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_AB_TESTS {#biz-customer-ab-tests}

AB-tester har registrerats. Det här registret kommer att vara tomt om AB-tester inte är aktiverade.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första cookie-ID:t för det relaterade besökar-ID:t.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t när händelsen loggades.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när chatten loggades.</p>
      </td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen när experimentet loggades.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID:t för experimentet som hämtats från AB:s testplattform.</p>
      </td>
      <td>123</td>
    </tr>
    <tr>
      <td>
        <p>EXPERIMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på försöket som hämtats från AB:s testplattform.</p>
      </td>
      <td>Experimentera A</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Variations-ID för försöket som hämtats från AB:s testplattform.</p>
      </td>
      <td>456</td>
    </tr>
    <tr>
      <td>
        <p>VARIATION_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Variationsnamnet för det experiment som hämtats från AB:s testplattform.</p>
      </td>
      <td>Blått test</td>
    </tr>
    <tr>
      <td>
        <p>ABTEST_USER_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den användare som betjänade experimentet som hämtats från AB:s testplattform.</p>
      </td>
      <td>584d64et</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten har tagits bort eller inte, används för diagnostik och granskning.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOMER_EVENTS {#biz-customer-events}

Webbhändelser som har spelats in med anpassade händelser i JavaScript. Tabellen är tom om [!DNL Marketo Measure] Händelser är inte aktiverade.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första cookie-ID:t för det relaterade besökar-ID:t.</p>
      </td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t när händelsen utlöstes från det anpassade javascript-skriptet.</p>
      </td>
      <td>36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum som händelsen utlöstes från det anpassade javascript-skriptet.</p>
      </td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Det senaste datumet som posten ändrades.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen när händelsen utlöstes från det anpassade javascript-skriptet.</p>
      </td>
      <td>192.0.2.1</td>
    </tr>
    <tr>
      <td>
        <p>NYCKEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet som ges till händelsen som utlöstes från det anpassade javascript-skriptet.</p>
      </td>
      <td>Videovy</td>
    </tr>
    <tr>
      <td>
        <p>VÄRDE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Värdet som har tilldelats händelsen som utlöstes från det anpassade javascript-skriptet.</p>
      </td>
      <td>75 % visade</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten har tagits bort eller inte, används för diagnostik och granskning.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_CUSTOM_LANDING_PAGES {#biz-custom-landing-pages}

Landningssidor som hämtats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för posten.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för annonskontot som landningssidan importerades från.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Namn på det annonskonto från vilket landningssidan importerades</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Advertiser för landningssidan, speciellt för Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Advertiser för landningssidan, speciellt för Doubleclick.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för annonskoncern för landningssidan.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsgruppen för landningssidan.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Campaign för landningssidan.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Campaign för landningssidan.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Radens senast ändrade datum</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_EMAIL_TO_VISITOR_IDS {#biz-email-to-visitor-ids}

Mappningstabell för e-postadresser och besökar-ID.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Ett unikt ID för posten.</td>
      <td>
        <p>0013800001MMPPiAAP_person@adobe.com|2022-01-05 17:22:13 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En känd e-postadress som är kopplad till ett visst besökar-ID från en session</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första cookien för det relaterade besökar-ID:t</p>
      </td>
      <td>
        <p>v_36ec805b4db344d6e92c972c86aee34a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Radens senast ändrade datum</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Radens skapade datum</p>
      </td>
      <td>
        <p>2018-08-14 23:55:03,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om posten betraktas som borttagen eller inte, används för diagnostik och granskning.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>IS_IGNORE</td>
      <td>boolesk</td>
      <td>Anger om e-postadressen eller besökar-ID:t betraktas som brus eller skräppost, som används för intern bearbetning.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_FACTS {#biz-facts}

Unions innehåller Impressions, Page Views, Visits, Form Submits, User Touchpoints, Touchpoint (BT), Attribution Touchpoints (BAT) och Cost Data. Används internt som stöd [!DNL Marketo Measure] rapportering.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>COST_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att gå med i kostnadstabellen.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>ATP_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till tabellen Attribution Touchpoints.</td>
      <td>2672629811884560039</td>
    </tr>
    <tr>
      <td>TP_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till Touchpoints- eller User Touchpoints-tabellerna.</td>
      <td>5028390208679093800</td>
    </tr>
    <tr>
      <td>PAGE_VIEW_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till tabellen Sidvyer.</td>
      <td>-8044063242541720607</td>
    </tr>
    <tr>
      <td>SESSION_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till sessionstabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Det första cookie-ID:t för det relaterade besökar-ID:t.</td>
      <td>v_530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>COOKIE_ID</td>
      <td>varchar</td>
      <td>Det inspelade cookie-ID:t när händelsen loggades.</td>
      <td>530d8334c455460df0d48f48270a4b23</td>
    </tr>
    <tr>
      <td>FORM_SUBMIT_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till tabellen Formuläröverföringar.</td>
      <td>-8659572802702769670</td>
    </tr>
    <tr>
      <td>IMPRESSION_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till Impressions-tabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till URL-tabellen.</td>
      <td>4079876040770132443</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till URL-tabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till URL-tabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>AD_PROVIDER_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att ansluta till tabellen Ad Providers.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>
        <p>CHANNEL_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till tabellen Kanaler.</p>
      </td>
      <td>
        <p>-1921844114032355934</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att gå med i tabellen Annonskampanjer.</p>
      </td>
      <td>
        <p>252687814634577606</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till nyckelordstabellen.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till Ads-tabellen.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till tabellen Ad Groups.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att delta i tabellen Creative.</p>
      </td>
      <td>
        <p>-2333871387956621113</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till tabellen Platser.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till Advertisers-tabellen.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att ansluta till tabellen Annonskonton.</p>
      </td>
      <td>
        <p>1825012532740770032</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Används för att koppla till tabellen Placements.</p>
      </td>
      <td>
        <p>8817975702393619368</p>
      </td>
    </tr>
    <tr>
      <td>CATEGORY_01_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_02_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_03_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_04_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_05_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_06_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_07_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_08_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_09_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_10_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_11_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_12_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>-2333871387956621113</td>
    </tr>
    <tr>
      <td>CATEGORY_13_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_14_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>CATEGORY_15_KEY</td>
      <td>tal(38,0)</td>
      <td>Används för att koppla till segmenttabellen.</td>
      <td>8817975702393619368</td>
    </tr>
    <tr>
      <td>TYP</td>
      <td>tal(38,0)</td>
      <td>Anger radens fakttyp. 1 = Buyer Attribution Touchpoint 2 = cost 3 = Buyer Touchpoint 4 = User Touchpoint 5 = Page View 6 = Session 7 = Form Submit 8 = Impression</td>
      <td>3</td>
    </tr>
    <tr>
      <td>DATUM</td>
      <td>datum</td>
      <td>Datum då händelsen inträffade.</td>
      <td>2018-08-28</td>
    </tr>
    <tr>
      <td>TIDSSTÄMPEL</td>
      <td>timestamp_ntz</td>
      <td>Datum och tid då händelsen inträffade.</td>
      <td>2018-08-28 19:39:15 000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då raden senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-29 00:46:47 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COST_IN_MICRO</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Kostnadsbelopp i miljoner. Användaren måste dividera värdet med 100000.</p>
      </td>
      <td>
        <p>27370000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSIONER</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Antal visningar som rapporterats för gruppen för dagen.</p>
      </td>
      <td>
        <p>340</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KLICK</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Antal klick som rapporterats för gruppen för dagen.</p>
      </td>
      <td>4</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är en första beröring.</p>
      </td>
      <td>0,0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är ett tips om att skapa leads.</p>
      </td>
      <td>100,0000000000000000000</td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelas den här kontaktytan eftersom den är en del av en oformad beröring.</p>
      </td>
      <td>
        <p>100,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelas till den här kontaktytan eftersom den är en del av en bländare.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelas den här kontaktytan eftersom den ingår i en fullständig banmodell.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CUSTOM_MODEL_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelas den här kontaktytan eftersom den ingår i en anpassad modell.</p>
      </td>
      <td>
        <p>0,0000000000000000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BELOPP</p>
      </td>
      <td>
        <p>tal(38,8)</p>
      </td>
      <td>
        <p>Mängd säljprojekt från källsystemet.</p>
      </td>
      <td>
        <p>42000,00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om affärsmöjligheten har flyttats till en fas som har klassificerats som vunnen.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CLOSED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om affärsmöjligheten har flyttats till en fas som klassificeras som stängd.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Affärsmöjlighets-ID från källsystemet.</p>
      </td>
      <td>
        <p>0060Z00000nFEfEQAW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då affärsmöjligheten skapades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-31 15:45:47 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPP_CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Stängningsdatum för affärsmöjligheten från källsystemet.</p>
      </td>
      <td>
        <p>2018-12-31 07:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum kontaktposten skapades från källsystemet.</p>
      </td>
      <td>2017-04-28 00:21:52 000</td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kontakt-ID från källsystemet.</p>
      </td>
      <td>
        <p>0030Z00003ORVJmQAP</p>
      </td>
    </tr>
    <tr>
      <td>E-POST</td>
      <td>varchar</td>
      <td>E-postadress för posten.</td>
      <td>personb@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>LEAD_CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då lead-posten skapades från källsystemet.</p>
      </td>
      <td>
        <p>2017-04-28 00:21:52 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Lead-ID från källsystemet.</p>
      </td>
      <td>
        <p>00Q3100001GMPIsEAP</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av annons. (d.v.s. för att hämta annonskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_ADVERTISER</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller Kostnad som kan summeras av Advertiser. (d.v.s. för att hämta Advertiser-kostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_Account</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av konto. (d.v.s. för att hämta kontokostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_AD_GROUP</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av annonsgrupp. (d.v.s. om du vill hämta annonsgruppskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CAMPAIGN</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av Campaign. (d.v.s. för att få kampanjkostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CHANNEL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av kanal. (d.v.s. för att hämta kanalkostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_CREATIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller Kostnad som kan summeras av Creative Cloud. (d.v.s. för att få Creative Cost, summerar rader där kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_KEYWORD</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av nyckelord. (d.v.s. för att hämta nyckelordskostnad, summerar rader där kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_PLACEMENT</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av montering. (d.v.s. för att hämta placeringskostnad, summeringsrader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_AGGREGATABLE_COST_SITE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden innehåller kostnad som kan summeras av platsen. (d.v.s. för att hämta webbplatskostnad, summerar rader där den här kolumnen är lika med true.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Oavsett om posten har tagits bort eller inte används den som ett granskningsspår.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>tal(38,0)</td>
      <td>ID-värde för postens valuta.</td>
      <td>-3253183181619994799</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_FORM_SUBMITS {#biz-forms-submits}

Insamlade formulärinskickat material.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för att skicka formulär.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-21-927280.9bc63c34482f4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t när formuläret skickades loggades.</p>
      </td>
      <td>
        <p>9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första cookie-ID:t för det relaterade besökar-ID:t. Om posten är markerad som is_duplicated = true, kommer det här fältet att vara null.</p>
      </td>
      <td>
        <p>v_9bc63c34482f4de8c2e3b9d8d9f0df56</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade sessions-ID:t när formuläret skickades loggades. Om posten är markerad som is_duplicated = true, kommer det här fältet att vara null.</p>
      </td>
      <td>
        <p>2018-08-06:01-35-24-1231230.9bc63c34482f</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då formuläret skickades.</p>
      </td>
      <td>
        <p>2018-08-06 01:35:21 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-07 23:09:52 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där formuläret skickades, utan frågeparametrar.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där formuläret skickades, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>
        <p>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOAH Nwdml3YZBZDPF dXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen när formuläret skickades.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYP</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger händelsetypen.</td>
      <td>
        <p>FormSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Enhet och webbläsare som spelades in när formuläret skickades.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, t.ex. Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger i vilken ordning sidvyn skapades i sessionen.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern revision och bearbetning.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om posten betraktas som en dubblett.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Används för intern bearbetning.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-postadress som finns i formuläret, enligt javascript.</p>
      </td>
      <td>
        <p>personc@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger vilken typ av formulär som har skickats.</td>
      <td>
        <p>Chatt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Anger den metod som används för att identifiera formuläret, till exempel onSubmit eller AjaxIntercept</p>
      </td>
      <td>
        <p>onSubmit</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_IDENTIFIER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID-värde för formuläret.</td>
      <td>
        <p>-956012665</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Sekundärnyckel till URL-tabellen.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_IMPRESSIONS {#biz-impressions}

Impressioner avfyrade och inspelade. Den här tabellen kräver en DoubleClick-anslutning och Aktivera View Through inställd på True.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för Impression.</p>
      </td>
      <td>
        <p>6acd7b43290490fe5c53eed31281d09a|2020-05-18:22:20:59|0000|0|2869369052</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t vid tidpunkten för Impression.</p>
      </td>
      <td>08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första cookie-ID:t för det relaterade besökar-ID:t.</p>
      </td>
      <td>v_08c1063cb0a64349ad0d2d862f5cc700</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade sessions-ID:t när Impression loggades.</p>
      </td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då Impression opererades.</p>
      </td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där Impression hanterades, utan frågeparametrar.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact</td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där Impression utfördes, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>https://info.adobe.com/webinar-marketo-measure-impact?utm_source=partner&amp;mkt_tok=eyJpIjoiTnpBeE1EVml PV0UyWlRObSIsInQiOiI3MEFIek04ZVJiWm9renc1Z29RXC9kXC92YkxycFRYclE0MVhOAH Nwdml3YZBZDPF dXh4Q0RmcnBJWXhwZTF1Z0RrbXlDVmxJNzIwNkhW</td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen vid tidpunkten för Impression.</p>
      </td>
      <td>174.127.184.158</td>
    </tr>
    <tr>
      <td>
        <p>TYP</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger händelsetypen.</td>
      <td>Impression</td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Enhet och webbläsare som spelades in när formuläret skickades.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/605.1.15 (KHTML, t.ex. Gecko) Version/11.1.2 Safari/605.1.15</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger i vilken ordning sidvyn skapades i sessionen.</td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern revision och bearbetning.</td>
      <td>
        <p>20042b6b7af44512b43f6244d86faf4c</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om posten betraktas som en dubblett.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Används för intern bearbetning.</td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. I CRM kallas det"Refererarsida".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE-RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. En råhänvisningssida kan innehålla frågeparametrar i URL:en. I CRM refereras till"Refererarsida - Raw".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>ORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den matchade staden från IP-adressen.</p>
      </td>
      <td>
        <p>Seattle</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den matchade regionen från IP-adressen.</p>
      </td>
      <td>
        <p>Washington</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAND</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det lösta landet från IP-adressen.</p>
      </td>
      <td>
        <p>USA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Internetleverantören, som används av kunder med avancerad IP-spårning för geo.</p>
      </td>
      <td>
        <p>AT&amp;T U-verterad</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsplattform [!DNL Marketo Measure] har kunnat lösa sig från, vanligtvis en av våra integreringspartners.</p>
      </td>
      <td>Google</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen löstes från.</p>
      </td>
      <td>aw.6601259029</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som annonsen löstes från.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonseraren från annonskontot som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseraren från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marknadsmätningsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för webbplatsen från annonskontot där annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatsen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>aw.6601259029.317738075</td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>Marknadsattribuering</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp i dubbelsidig hierarki för visningar</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp i dubbelsidig hierarki för visningar</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen från annonskontot som annonsen löstes från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>
        <p>68035923</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen från annonskontot där annonsen löstes. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>
        <p>centurylink_banner_98121</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något Creative-värde i Dubbelklicka-hierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något nyckelord i dubbelklickningshierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något nyckelord i dubbelklickningshierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något nyckelord i dubbelklickningshierarkin för Impressions.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen upptäckte den webbläsare som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Krom</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av webbläsaren som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade plattform som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av plattformen som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn BIZ_FACTS.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_KEY</p>
      </td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_KEYWORDS {#biz-keywords}

Nyckelord som importerats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för nyckelordet.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365.39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Nyckelords-ID från källsystemet.</td>
      <td>
        <p>39464932147</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som nyckelordet importerades från.</p>
      </td>
      <td>fb.106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som nyckelordet importerades från.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något nyckelord i dubbelklickningshierarkin för Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntades vara null eftersom det inte finns något nyckelord i dubbelklickningshierarkin för Impressions.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsgruppen för nyckelordet.</p>
      </td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsgruppen för nyckelordet.</p>
      </td>
      <td>
        <p>Intäktsattribuering - B2B</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Campaign för nyckelordet.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Campaign för nyckelordet.</p>
      </td>
      <td>
        <p>Intäktsfördelning</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om nyckelordet fortfarande är aktivt i källsystemet eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om nyckelordet har tagits bort eller inte i källsystemet.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>2018-08-02 06:37:29 000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-02 06:37:29 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på nyckelordet från källsystemet.</p>
      </td>
      <td>
        <p>[intäktsattribuering b2b]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om nyckelordet behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används för intern bearbetning.)</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td>
        <p>ba.3284209.132630532.3646889365</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"Nyckelord".</p>
      </td>
      <td>
        <p>Nyckelord</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsprovidern för nyckelordet.</p>
      </td>
      <td>
        <p>BingAds</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL-adressen till landningssidan.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tidigare värde för URL_CURRENT.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>URL_REQUESTED</td>
      <td>varchar</td>
      <td>
        <p>URL:en för landningssidan med [!DNL Marketo Measure] parametrar.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_UPGRADED_URL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WORD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Sökfasen som användaren angav.</td>
      <td>
        <p>intäktsattribuering b2b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den typ av matchning som hittades mellan sökfrasen och nyckelordet.</p>
      </td>
      <td>
        <p>Exakt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern diagnostik.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>TRACKING_URL_TEMPLATE_APPLIED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL-spårningsmallen [!DNL Marketo Measure] läggs till i nyckelordet.</td>
      <td>
        <p>http://cdn.adobe.com/redir?lp={lpurl}&amp;_bt={creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>-2712935512233520000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_LANDING_PAGES {#biz-landing-pages}

Landningssidor som importerats från alla anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för landningssidan.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för annonskontot som landningssidan importerades från.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Namnet på annonskontot som landningssidan importerades från.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Advertiser för landningssidan, speciellt för Doubleclick.</p>
      </td>
      <td>300181641</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Advertiser för landningssidan, speciellt för Doubleclick.</p>
      </td>
      <td>Marknadsföringsanalys</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>ID för annonskoncern för landningssidan.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Namn på annonsgruppen för landningssidan.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Id för Campaign för landningssidan.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Namnet på Campaign för landningssidan.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Radens senaste ändringsdatum.</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEADS {#biz-leads}

Leads som importerats från källsystemet.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Lead-ID:t från källsystemet.</p>
      </td>
      <td>
        <p>00Q0Z00001MZcj8UAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när lead-posten senast ändrades från källsystemet.</p>
      </td>
      <td>
        <p>2018-08-27 21:52:10 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då lead-posten skapades från källsystemet.</p>
      </td>
      <td>2018-08-27 21:52:10 000</td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Leadens e-postadress från källsystemet.</p>
      </td>
      <td>persona@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>WEB_SITE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Webbplats som anges för Lead, från källsystemet, används för lead2Account-mappning.</p>
      </td>
      <td>
        <p>adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FÖRETAG</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Företagsnamn som anges för Lead, från källsystemet, används för lead2Account-mappning.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Källa där lead skapades.</p>
      </td>
      <td>
        <p>Annons</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CONVERTED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om leadet har konverterats till en kontakt eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den relaterade affärsmöjligheten när leadet har konverterats.</p>
      </td>
      <td>
        <p>0013100001b44aGAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när leadet konverterades till en kontakt.</p>
      </td>
      <td>
        <p>2018-08-27 07:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den relaterade kontakten när leadet har konverterats.</p>
      </td>
      <td>
        <p>0030Z00003Oyp25QAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KONTO</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det mappade kontot. Krav: Aktivera ABM</p>
      </td>
      <td>
        <p>0010Z000236F9GQAU</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Aktuell fas av lead, känns igen som en anpassad fas som kan skapas i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>Demo schemalagd</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Alla tidigare faser för lead, identifieras som anpassade stadier som kan skapas i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>MQL</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>tal(38,19)</p>
      </td>
      <td>
        <p>Den här funktionen har tagits bort. Använd inte den här kolumnen.</p>
      </td>
      <td>
        <p>Ej tillämpligt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_MODEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(borttagen)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_SCORE_RESULTS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>(borttagen)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>The [!DNL Marketo Measure] Cookie-ID som används för att fylla i från en integrationspartner för att mappa en offlinehändelse till en webbsession. Krav: Aktivera samtalsspårning: Sant</p>
      </td>
      <td>
        <p>08c1063cb0a64349ad0d2d862f5cc700</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om posten tas bort i källsystemet eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>3263982503087870000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Lead_Type__c":"Försäljning skapad", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>IS_DUPLICATE</td>
      <td>boolesk</td>
      <td>Används för att deduplicera poster om både en CRM- och Marketo-integrering har konfigurerats. Om det finns dubbletter markeras Marketo Lead som true.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>SOURCE_SYSTEM</td>
      <td>varchar</td>
      <td>Anger om posten kommer från en CRM- eller Marketo-integrering.</td>
      <td>Crm</td>
    </tr>
    <tr>
      <td>OTHER_SYSTEM_ID</td>
      <td>varchar</td>
      <td>Mappar en person från en Marketo-integrering med en lead från en CRM-integrering. Om det finns både en CRM- och Marketo-integrering är värdet motsvarande ID.</td>
      <td>1234</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_LEAD_STAGE_TRANSITIONS {#biz-lead-stage-transitions}

Scenövergångar för Leads eller Kontakter.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för övergången.</p>
      </td>
      <td>
        <p>ST_0030Z0003FhkRXQAZ__FT-1_TP2_Person_0030Z0003FhkRXQAZ_2018-08-27:17-05-45-94 74800.0d5c18c29d7b</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den angivna e-postadressen för den relaterade lead/kontakten.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den lead som är associerad med övergången.</p>
      </td>
      <td>
        <p>00Q3100001Fx6AlEAJ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är kopplad till övergången.</p>
      </td>
      <td>
        <p>0033100003Aq9grAAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Buyer Touchpoint som är knuten till övergången.</p>
      </td>
      <td>
        <p>TP2_Person_00Q310001Fx6AlEAJ_2018-08-28:14-41-06-1674260.d00ceb09fbd3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten överfördes till scenen.</p>
      </td>
      <td>
        <p>2018-08-27 16:05:34.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID-värdet för fasen för övergången.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SCEN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på fasen för övergången.</p>
      </td>
      <td>
        <p>FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Scenens numeriska rankning, enligt ordningen i [!DNL Marketo Measure] Inställningar för scenmappning.</p>
      </td>
      <td>
        <p>5</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Används i intern bearbetning för indexering och beställning av sammansatta stadier.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>Används i intern bearbetning för indexering och beställning av sammansatta stadier.</td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om kontaktytan anses vara väntande och inte stängd än. Detta gäller endast kunder med en fullständig sökvägsattribueringsmodell.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden är knuten till en övergång i milstolpe-stadiet. Om det till exempel finns tre faser/poster (FT, LC, MQL) och fyra kontaktytor betraktas kontaktytan 1 utan en scen på den som"icke-övergångsfas", så värdet skulle vara lika med true.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Övergångsdatum för föregående fas, enligt scenrankningen.</p>
      </td>
      <td>
        <p>2017-11-28 21:26:44 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Övergångsdatum för nästa fas, enligt scenrankningen.</p>
      </td>
      <td>
        <p>2017-12-11 22:39:17 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Senaste ändringsdatum för posten.</p>
      </td>
      <td>
        <p>2018-08-28 15:31:10 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om övergångsposten betraktas som borttagen eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPPORTUNITIES {#biz-opportunities}

Möjligheter som importerats från källsystemet.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Affärsmöjlighets-ID från källsystemet.</p>
      </td>
      <td>
        <p>0060Z0000o89I4QAI</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Senaste ändringsdatum för affärsmöjligheten från källsystemet.</p>
      </td>
      <td>2017-11-28 21:26:44 000</td>
    </tr>
    <tr>
      <td>
        <p>CREATED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Skapat datum för affärsmöjligheten från källsystemet.</p>
      </td>
      <td>2017-11-28 21:26:44 000</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det relaterade kontot.</p>
      </td>
      <td>
        <p>001i000000qbyeoAAA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Affärsmöjlighetens namn från källsystemet.</p>
      </td>
      <td>
        <p>Mareketo Mät förnyelse</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_WON</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om affärsmöjligheten har flyttats till en aktuell fas.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om affärsmöjligheten har flyttats till en fas som anses vara stängd.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLOSE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Förväntat eller faktiskt slutdatum för affärsmöjligheten från källsystemet.</p>
      </td>
      <td>
        <p>2019-08-28 07:00:00,000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_CUSTOM_MODEL_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>(borttagen)</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BELOPP</p>
      </td>
      <td>
        <p>tal(38,8)</p>
      </td>
      <td>
        <p>Avtalsbelopp som förväntas eller stängs från säljprojektet, från källsystemet.</p>
      </td>
      <td>
        <p>8988,00000000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den relaterade lead som har konverterats till denna möjlighet.</p>
        <p>Observera att det här fältet inte är inställt och returnerar null i Snowflake för alla kunder.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONVERTED_FROM_LEAD_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-postadressen till den relaterade lead som har konverterats till det här säljprojektet.</p>
        <p>Observera att det här fältet inte är inställt och returnerar null i Snowflake för alla kunder.</p>
      </td>
      <td>
        <p>null</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Om Roll för primär kontakt används, ID:t för den relaterade kontakten listas som den primära kontaktrollen.</p>
      </td>
      <td>
        <p>00331000038uGfhAAE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PRIMARY_CONTACT_EMAIL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Om Roll för primär kontakt används, e-postadressen till den relaterade kontakten som anges som den primära kontaktrollen.</p>
      </td>
      <td>
        <p>personb@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ODDS_OF_CONVERSION</p>
      </td>
      <td>
        <p>tal(38,19)</p>
      </td>
      <td>
        <p>Den här funktionen har tagits bort. Använd inte den här kolumnen.</p>
      </td>
      <td>
        <p>Ej tillämpligt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Affärsmöjlighetens aktuella fas, enligt definitionen i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>DM Demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>BIZIBLE_STAGE_PREVIOUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>En sträng med alla stadier som säljprojektet tidigare gått igenom, enligt definitionen i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>Kvalificerad identifiering, demo schemalagd</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om posten tas bort i källsystemet eller inte.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>4609512587744160000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENCY_ISO_CODE</td>
      <td>varchar</td>
      <td>ISO-kod för valutan, importerad från källsystemet.</td>
      <td>USD</td>
    </tr>
    <tr>
      <td>CURRENCY_ID</td>
      <td>tal(38,0)</td>
      <td>ID-värde för postens valuta.</td>
      <td>4609512587744160000</td>
    </tr>
    <tr>
      <td>CUSTOM_PROPERTIES</td>
      <td>varchar</td>
      <td>Anpassade egenskaper som [!DNL Marketo Measure] har importerats från källsystemet i JSON-format.</td>
      <td>{"Opportunity_Location__c":"Seattle", "Foo":"Bar"}</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_OPP_STAGE_TRANSITIONS {#biz-opp-stage-transitions}

Scenövergångar för affärsmöjligheter.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för övergången.</p>
      </td>
      <td>
        <p>ST_0060Z00000nEgjlQAC_0030Z0003IjojKQAR_Demo Scheduled-1_BAT2_0060Z0000nEgjlQAC_0030n Z00003IjojKQAR_2018-06-01:19-51-38-1685390.beec556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontot som är associerat med affärsmöjligheten.</p>
      </td>
      <td>
        <p>0013100001b44nTAAQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>OPPORTUNITY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för affärsmöjligheten som är associerad med övergången.</p>
      </td>
      <td>
        <p>0060Z0000nEgjlQAC</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kontakten som är kopplad till övergången.</p>
      </td>
      <td>
        <p>0030Z00003IjojKQAR</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den angivna e-postadressen för den relaterade kontakten.</p>
      </td>
      <td>
        <p>persone@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Buyer Attribution Touchpoint som är knuten till övergången.</p>
      </td>
      <td>
        <p>BAT2_0060Z00000nEgjlQAC_0030Z0003IjojKQAR_2018-06-01:19-51-38-1685390.beec 556e7757</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TRANSITION_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten överfördes till scenen.</p>
      </td>
      <td>
        <p>2018-05-26 07:29:43 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SCEN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på fasen för övergången.</p>
      </td>
      <td>
        <p>Demo schemalagd</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID-värdet för fasen för övergången.</p>
      </td>
      <td>
        <p>_bizible_FT</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Scenens numeriska rankning, enligt ordningen i [!DNL Marketo Measure] Inställningar för scenmappning.</p>
      </td>
      <td>
        <p>4</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Används i intern bearbetning för indexering och beställning av sammansatta stadier.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>LAST_INDEX</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Används i intern bearbetning för indexering och beställning av sammansatta stadier.</p>
      </td>
      <td>1</td>
    </tr>
    <tr>
      <td>
        <p>IS_PENDING</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om kontaktytan anses vara väntande och inte stängd än. Detta gäller endast kunder med en fullständig sökvägsattribueringsmodell.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_NON_TRANSITIONAL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om raden är knuten till en övergång i milstolpe-stadiet. Om det till exempel finns tre faser/poster (FT, LC, MQL) och fyra kontaktytor betraktas kontaktytan 1 utan en scen på den som"icke-övergångsfas", så värdet skulle vara lika med true.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PREVIOUS_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Övergångsdatum för föregående fas, enligt scenrankningen.</p>
      </td>
      <td>
        <p>2015-07-16 17:41:49 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NEXT_STAGE_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Övergångsdatum för nästa fas, enligt scenrankningen.</p>
      </td>
      <td>
        <p>2018-08-27 19:40:52 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Senaste ändringsdatum för posten.</p>
      </td>
      <td>
        <p>2018-08-28 03:53:33 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om övergångsposten betraktas som borttagen eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_PAGE_VIEWS {#biz-page-views}

Sidvyer som samlats in från webbbesök. Flera sidvyer kan bestå av en enda session.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för sidvyn.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t när sidvyn loggades.</p>
      </td>
      <td>
        <p>277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första cookien för det relaterade besökar-ID:t.</p>
      </td>
      <td>
        <p>v_277d79d01678498fea067c9b631bf6df</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Sessions-ID som är kopplat till sidvyn.</p>
      </td>
      <td>
        <p>2018-08-19:16-49-58-24340.277d79d0167849</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när sidvyn skapades.</p>
      </td>
      <td>
        <p>2018-08-19 16:49:58 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-19 16:55:37 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL för sidvyn, utan frågeparametrar.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CURRENT_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL för sidvyn, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo?hsCtaTracking=207219e9-87b6-4105-8f4b-0a3b62ae1af8%7C48060522-3aeb-4c72-8ce5-fd4b1017f069</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen när formuläret skickades.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TYP</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger händelsetypen.</td>
      <td>
        <p>PageView</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_AGENT_STRING</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Enhet och webbläsare som spelades in när formuläret skickades.</p>
      </td>
      <td>
        <p>Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Firefox/52.0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_SEQUENCE</p>
      </td>
      <td>
        <p>varchar(1)</p>
      </td>
      <td>
        <p>Anger i vilken ordning sidvyn skapades i sessionen.</p>
      </td>
      <td>
        <p>1</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CLIENT_RANDOM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Används för intern revision och bearbetning.</td>
      <td>
        <p>103532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DUPLICATED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om posten betraktas som en dubblett.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>IS_PROCESSED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Används för intern bearbetning.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där sidvyn kom från, utan frågeparametrar.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL:en som sidvyn kommer från, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>
        <p>http://info.adobe.com/cmos-guide-to-b2b-marketing-attribution?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU%20-%20CMO%20JT&amp;utm_content=CMOs%20Guide&amp;utm_term=lisu05091601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Sidans namn.</p>
      </td>
      <td>
        <p>The CMO's Guide to B2B Marketing Attribution Download</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-postadress som anges i ett formulär, som hämtats från javascript.</p>
      </td>
      <td>personc@adobe.com</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-6255315750913680000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Sekundärnyckel till URL-tabellen.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td>Sekundärnyckel till URL-tabellen.</td>
      <td>6255315750913680000</td>
    </tr>
    <tr>
      <td>HAS_USER_CONSENT</td>
      <td>boolesk</td>
      <td>Anger om användaren har godkänt spårning. Falskt betyder att sidvyn har samlats in eftersom användargodkännande inte krävs. Sant innebär att sidvyn har samlats in och att användaren har gett sitt medgivande till att spåras.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_PLACEMENTS {#biz-placements}

Tabell som lagrar alla placeringar som hämtats från anslutna annonskonton, ett objekt från Dubbelklicka-integreringen.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för placeringen.</p>
      </td>
      <td>
        <p>ba.3284209.132855866.4556709270.10426699711</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Placement-ID:t från källsystemet.</td>
      <td>10426699711</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som placeringen importerades från.</p>
      </td>
      <td>fb. 106851586409075</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som placeringen importerades från.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för annonsören för placeringen, speciellt för Doubleclick.</p>
      </td>
      <td>300184624</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonsören för placeringen, speciellt för Doubleclick.</p>
      </td>
      <td>[!DNL Marketo Measure] Analyser</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför placeringen i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför placeringen i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för Campaign för placeringen.</p>
      </td>
      <td>ba.3284209.132855866</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen för placeringen.</p>
      </td>
      <td>Pipeline Marketing</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om placeringen fortfarande är aktiv i källsystemet eller inte.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om placeringen har tagits bort i källsystemet eller inte.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>2018-08-02 06:36:25 000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>2018-08-02 06:36:25 000</td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen, från källsystemet.</p>
      </td>
      <td>marknad</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om placeringen behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används av intern bearbetning.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet "Placement".</p>
      </td>
      <td>Placement</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonseringsprovidern för placeringen.</p>
      </td>
      <td>BingAds</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>6008900572523230000</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake skapade datumet för inspelningen</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake modifierat datumet för inspelningen</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake har raderat posten om den har tagits bort</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENTS {#biz-segments}

Segmentvärden som definieras i [!DNL Marketo Measure] program.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för segmentet.</p>
      </td>
      <td>
        <p>Nytt företag</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentets namn.</p>
      </td>
      <td>
        <p>Nytt företag</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_SEGMENT_NAME {#biz-segment-names}

Kopplar namnet på det anpassade segmentet till dess kategorivärde. (Detta mappar kolumnnamnen till kolumnrubrikerna Kategori1-15 i kontakttabellerna.)

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>KATEGORI</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Anger kategorin som segmentnamnet mappas till.</p>
      </td>
      <td>
        <p>KategoriOne</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2022-02-28 18:12:35 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEGMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det segment som är mappat till kategorin.</p>
      </td>
      <td>
        <p>1028715376434030000</p>
      </td>
    </tr>
    <tr>
      <td>IS_ACTIVE</td>
      <td>boolesk</td>
      <td>Anger om kategorin används.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>IS_DELETED</td>
      <td>boolesk</td>
      <td>Anger om posten har tagits bort.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_SESSIONS {#biz-sessions}

Sessioner som har bearbetats från sidvyer. Flera sidvyer kan bestå av en session och ett enda besökar-ID kan kopplas till flera sessioner.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för sessionen.</p>
      </td>
      <td>
        <p>2016-08-01:14-24-21-9079480.33163948f0a3</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första cookien för det relaterade besökar-ID:t.</p>
      </td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det inspelade cookie-ID:t för sessionen.</p>
      </td>
      <td>277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum för sessionen.</p>
      </td>
      <td>
        <p>2016-08-01 14:24:21 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ÄNDRAT DATUM</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-09-01 03:49:10 000</p>
      </td>
    </tr>
    <tr>
      <td>IS_FIRST_SESSION</td>
      <td>boolesk</td>
      <td>Anger om detta är den första sessionen för besökar-ID:t.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>KANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kanal som är tilldelad sessionen, enligt definition i kanaldefinitionerna i [!DNL Marketo Measure] program.</p>
      </td>
      <td>
        <p>Betalsökning.AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PAGE_TITLE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Webbsidans namn.</p>
      </td>
      <td>
        <p>Salesforce Google Analytics | [!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL för sessionens första sidvy, utan frågeparametrar.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL för sessionens första sidvy, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics?_bt=83558988035&amp;_bk=google%20analytics%20salesforce&amp;_bm= p&amp;gclid=CMvd5YTLo84CFUI9gQodd-kLEQ</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL där sessionen kom från, utan frågeparametrar.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL dit sessionen kom, inklusive eventuella frågeparametrar.</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på referenssidan.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Värdet som användaren angav i webbläsaren för att söka efter och hamnade på webbplatsen.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] google salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera källan som resulterade i sessionen. Detta kan tolkas ut från URL:en från utm_source eller anges till en annonsleverantör om [!DNL Marketo Measure] kan åtgärda en annons.</p>
      </td>
      <td>
        <p>Google AdWord</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_FORM</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om sessionen innehöll en formulärfyllning eller inte</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CHAT</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om sessionen innehöll en webbchatt eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_EMAIL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om sessionen har en e-postadress eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>HAS_CRM_ACTIVITY</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om sessionen kom från en CRM-aktivitetspost eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENHET</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Användarens webbläsare och operativsystem under sessionen.</p>
      </td>
      <td>
        <p>Chrome (65.0), Windows (6.1)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ad Platform [!DNL Marketo Measure] som vi har löst från, vanligtvis en av våra integreringspartners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonseraren som annonsen löstes från, specifikt från Doubleclick-anslutningen.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseraren som annonsen löstes från, särskilt från Doubleclick-anslutningen.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för webbplatsen som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatsen som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den palett som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den kampanj som annonsen löstes från.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den kampanj som annonsen löstes från.</p>
      </td>
      <td>
        <p>Planera webbinariet Budget</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskoncern som annonsen löstes från. Detta gäller endast Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskoncern som annonsen löstes från. Detta gäller endast Google Adwords.</p>
      </td>
      <td>
        <p>Salesforce - Google Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen som lösts från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>aw.6601259029.321586235.23182235435</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen som lösts från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>Vinter-kampanj - grön</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den Creative som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.8358988035</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på den Creative-fil som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Integrera GA och Salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Integrera Salesforce och Analytics för att</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den andra raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Optimera för intäkter. Lär dig hur.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Landningssidan som klickas igenom från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>http://www.adobe.com/salesforce-google-analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det egna URL-namn som visas på sökannonsen, hämtat från annonskontot som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>adobe.com/Salesforce-for-GA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för nyckelordet som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.321586235.23182235435.3593468937</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på nyckelordet som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>google analytics salesforce</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den typ av matchning som hittas mellan sökfrasen och det köpta nyckelordet.</p>
      </td>
      <td>
        <p>Fras</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KAMPANJ</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tolkad från URL:en från utm_campaign.</p>
      </td>
      <td>
        <p>SU - ABC-konton - Betalda mediekunskaper</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KÄLLA</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tolkad från URL:en från utm_source.</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tolkad från URL:en från utm_medium.</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>TERM</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tolkad från URL:en från utm_term.</p>
      </td>
      <td>
        <p>lisu07261601</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>INNEHÅLL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tolkad från URL:en från utm_content.</p>
      </td>
      <td>
        <p>2016 AdWords Benchmark Report</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den matchade staden från IP-adressen.</p>
      </td>
      <td>Vancouver</td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den matchade regionen från IP-adressen.</p>
      </td>
      <td>British Columbia</td>
    </tr>
    <tr>
      <td>
        <p>LAND</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det lösta landet från IP-adressen.</p>
      </td>
      <td>Kanada</td>
    </tr>
    <tr>
      <td>
        <p>ISP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Användarens internetleverantör</p>
      </td>
      <td>
        <p>AT&amp;T U-verterad</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IP_ADDRESS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den registrerade IP-adressen vid tiden för sessionen.</p>
      </td>
      <td>
        <p>174.127.184.158</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Avgör om den här sessionen har sammanfogats med en annan och ska tas bort.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERTISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITES {#biz-sites}

Webbplatser som importerats från anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för platsen.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Plats-ID:t från källsystemet.</td>
      <td>39464932147</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som webbplatsen importerades från.</p>
      </td>
      <td>aw.3284209</td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskontot som webbplatsen importerades från.</p>
      </td>
      <td>[!DNL Marketo Measure]</td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för annonsören för webbplatsen, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsören för webbplatsen, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför Webbplats i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Förväntad att vara null eftersom det inte finns någon annonsgrupp ovanför Webbplats i någon annonshierarki.</p>
      </td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Webbplatsens kampanj.</p>
      </td>
      <td>
        <p>ba.3284209.132630532</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på Webbplatsens kampanj.</p>
      </td>
      <td>Återvinningsattribuering</td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om Webbplatsen fortfarande är aktiv i källsystemet eller inte.</p>
      </td>
      <td>true</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om platsen har tagits bort i källsystemet eller inte.</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>2018-08-02 06:37:29 000</td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum då posten först importerades från källsystemet.</p>
      </td>
      <td>2018-08-02 06:37:29 000</td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på platsen, från källsystemet.</p>
      </td>
      <td>Intäkter</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om webbplatsen behöver uppdateras för [!DNL Marketo Measure] taggning.</p>
        <p>(Diagnostikfält, används för intern bearbetning.)</p>
      </td>
      <td>false</td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Diagnostikfält, används för intern bearbetning.</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet"Plats".</p>
      </td>
      <td>Plats</td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonseringsprovidern för platsen.</p>
      </td>
      <td>AdWords</td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-2712935512233520000</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_SITE_LINKS {#biz-site-links}

Webbplatslänkar från anslutna annonskonton.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för platslänken</p>
      </td>
      <td>
        <p>aw.6601259029.285077795.1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>DISPLAY_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>1654234342</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det anslutna annonskontot för webbplatslänken</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det anslutna annonskontot för webbplatslänken</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Id för annonsören för webbplatslänken, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsören för webbplatslänken, särskilt för Doubleclick.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsgruppen för platslänken</p>
      </td>
      <td>aw.6601259029.208548635.16750166675</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsgruppen för webbplatslänken</p>
      </td>
      <td>Märke - kärna</td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanjen för webbplatslänken</p>
      </td>
      <td>
        <p>aw.6601259029.28507795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen för webbplatslänken</p>
      </td>
      <td>
        <p>Varumärke</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_ACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om webbplatslänken fortfarande är aktiv i annonskontot eller inte</p>
      </td>
      <td>
        <p>TRUE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om webbplatslänken har tagits bort eller inte i annonskontot</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Radens senast ändrade datum</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_IMPORTED</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Det datum då platslänken hämtades för första gången [!DNL Marketo Measure]</p>
      </td>
      <td>
        <p>2018-08-02 06:36:50 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatslänken</p>
      </td>
      <td>Länka A</td>
    </tr>
    <tr>
      <td>
        <p>NEEDS_UPDATE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om webbplatslänken behöver uppdateras för att Marekto-mättaggen ska kunna hämtas eller inte</p>
      </td>
      <td>
        <p>FALSE</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>GROUPING_KEY</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td></td>
      <td>
        <p>aw.6601259029.28507795</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ENTITY_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Huvudobjektet eller entiteten för det här registret. I det här fallet "SiteLink"</p>
      </td>
      <td>
        <p>SiteLink</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PROVIDER_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseringsprovidern för webbplatslänken</p>
      </td>
      <td>
        <p>AdWords</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_CURRENT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>URL-adressen till landningssidan.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td>
        <p>http://adobe.com/b2b-marketing-attribution?_bt =</p>
        <p>{creative}&amp;_bk={keyword}&amp;_bm={matchType}</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>URL_OLD</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Tidigare värde för URL_CURRENT.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>URL_REQUESTED</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vad URL:en kommer att dekoreras med [!DNL Marketo Measure] parametrar.</p>
        <p>(Diagnostikfält, för intern bearbetning.)</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake skapade datumet för inspelningen</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake modifierat datumet för inspelningen</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Snowflake har raderat posten om den har tagits bort</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_STAGE_DEFINITIONS {#biz-stage-definitions}

Lista över stadier som importerats eller definierats i [!DNL Marketo Measure] program.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för scenen.</p>
      </td>
      <td>
        <p>01J3100000QE753EAD</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-22 17:27:27 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Scenens namn.</p>
      </td>
      <td>
        <p>Verbal</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_INACTIVE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om scenen betraktas som inaktiv.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IN_CUSTOM_MODEL</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om scenen är markerad för spårning i den anpassade modellen.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_BOOMERANG</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om scenen är markerad för att spåras som en boomerang-scen.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_TRANSITION_TRACKING</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om scenen är markerad för att spåra övergångar.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>STAGE_STATUS</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Status för scenen, enligt definition i [!DNL Marketo Measure] Programscenmappning.</p>
      </td>
      <td>
        <p>Öppna</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FROM_SALESFORCE</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om scenen importeras från ett externt källsystem.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DEFAULT</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>Anger om scenen är inställd som standard.</td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>RANK</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Scenens numeriska rankning, som används för att sortera scener i övergångsordning.</p>
      </td>
      <td>
        <p>53</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om scenen har tagits bort eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_TOUCHPOINTS {#biz-touchpoints}

Buyer Touchpoints, alla kontaktytor som är kopplade till en lead eller kontakt. Tabellen är tom om kontaktpunkterna för lead eller kontakten är inaktiverade.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för Buyer Touchpoint (BT).</p>
      </td>
      <td>
        <p>TP2_Person_00Q0Z00013e2PYUAY_2018-08-27:20-04-40-565690.1ee8567c175a</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-08-29:29:30 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>E-postadress som är associerad med BT.</td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den kontakt som är associerad med BT.</p>
      </td>
      <td>0030Z00003K5bpKQAR</td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för det konto som är associerat med BT.</p>
      </td>
      <td>
        <p>0013100001lSLScAO</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den lead som är associerad med BT.</p>
      </td>
      <td>
        <p>00Q0Z00013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>UNIQUE_ID_PERSON</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den överordnade personposten som är relaterad till en lead eller kontakt.</p>
      </td>
      <td>
        <p>Person_00Q0Z00013e2PYUAY</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>USER_TOUCHPOINT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för användarkontaktpunkten som genererade BT:n.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-08-29:18-14-53-8102030.10df92cbb414</p>
      </td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>ID för besökaren som är associerad med BT.</td>
      <td>v_277d79d01678498fea067c9b631bf6df</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum för kontaktytan.</p>
      </td>
      <td>
        <p>2018-08-27 20:04:40 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Typ av aktivitet, webbbesök, webbformulär, webbchatt, telefonsamtal, [CRM]-kampanj eller [CRM]-aktivitet. I CRM kallas det"Touchpoint Type".</p>
      </td>
      <td>
        <p>Webbformulär</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kanalen som kontaktytan hamnar i, enligt definition i de anpassade kanaldefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till som"Marknadskanal - Sökväg".</p>
      </td>
      <td>Social.LinkedIn</td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den första kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td>ABC</td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den andra kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td>
        <p>Ja</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI3</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den tredje kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td>
        <p>Övrigt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI4</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den fjärde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td>
        <p>Partner</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI5</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den femte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI6</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den sjätte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI7</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den sjunde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI8</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den åttonde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI9</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den nionde kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI10</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den tionde kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI11</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den elfte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI12</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den tolfte kategorin som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI13</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Segmentvärdet för den 13:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI14</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den 14:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>KATEGORI15</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Segmentvärdet för den 15:e kategori som kontaktytan tillhör, enligt definition i segmentdefinitionerna i [!DNL Marketo Measure] App. I CRM kallas det"segment".</p>
      </td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen upptäckte den webbläsare som användaren var på under sessionen.</p>
      </td>
      <td>Krom</td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av webbläsaren som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>68</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade plattform som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Windows</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av plattformen som användaren var på under sessionen.</p>
      </td>
      <td>10_12</td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. I CRM kallas den"landningssida".</p>
      </td>
      <td>
        <p>https://info.adobe.com/definitive-guide-to-pipeline-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. En rå landningssida kommer att innehålla alla frågeparametrar i URL:en. I CRM kallas det"landningssida - Raw".</p>
      </td>
      <td>
        <p>https://info.adpbe.com/definitive-guide-to-pipeline-marketing?utm_source=linkedin&amp;utm_medium=Social&amp;utm_campaign=SU_COM_Demand_ Skills&amp;utm_content=DGPM&amp;utm_term=lisu03151846&amp;_bl=66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. I CRM kallas det"Refererarsida".</p>
      </td>
      <td>https://www.linkedin.com/</td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. En råhänvisningssida kan innehålla frågeparametrar i URL:en. I CRM refereras till"Refererarsida - Raw".</p>
      </td>
      <td>
        <p>https://www.linkedin.com/feed</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i Touchpoints-tabellen, utan i Form_Submits-tabellen. I CRM refereras till som "formulär-URL".</p>
      </td>
      <td>
        <p>https://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>FORM_PAGE_RAW</td>
      <td>varchar</td>
      <td>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i Touchpoints-tabellen, utan i Form_Submits-tabellen. En sida med Raw-formulär kan innehålla frågeparametrar i URL:en. I CRM refereras till"Form URL - Raw".</td>
      <td>https://info.adobe.com/demo?hsCtaTracking=98adcc2f-afe2-40c4-9d79-40dcc41663ee%7C3cfaa909-39cb-4f5d-93eb-be05de6b0180</td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när formuläret skickades.</p>
      </td>
      <td>
        <p>2017-06-20 01:06:41 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades den ort som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är det område som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>New York</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAND</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades det land som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>USA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera mediet som resulterade i kontaktytan. Detta kan antingen tolkas ut från URL:en från utm_medium. Eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "cpc" eller "display".</p>
      </td>
      <td>
        <p>Social</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera källan som resulterade i kontaktytan. Detta kan tolkas från URL:en från utm_source, vanligtvis inställd som CRM Campaign om den synkroniserades från CRM, eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "Google AdWords" eller "Facebook". Refereras i CRM till"Kontaktpunktskälla".</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Värdet som användaren angav i webbläsaren för att söka efter och hamnade på webbplatsen. Beroende på nyckelordsköp kan det här matcha nyckelorden som köpts från plattformen Betald sökning eller inte.</p>
      </td>
      <td>
        <p>marknadsattribuering</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsplattform [!DNL Marketo Measure] har kunnat lösa sig från, vanligtvis en av våra integreringspartners.</p>
      </td>
      <td>
        <p>LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>li.502664737</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>MM SC 2016_14605342_3/7-3/31/16</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonseraren från annonskontot som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseraren från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marketo Marketing Analytics</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för webbplatsen från annonskontot där annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatsen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>li.502664737.138949954</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>SU - COM Accounts - Demand Skills</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google Adwords.</p>
      </td>
      <td>aw.6601259029.317738075.23105327435</td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google AdWords.</p>
      </td>
      <td>Marknadsattribuering - allmänt</td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen från annonskontot som annonsen löstes från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen från annonskontot där annonsen löstes. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>Webbinarium - marginallist</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Creative-objektet från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>li.502664737.138949954.66452504</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det Creative-objekt från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Leadgenet är klart</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den andra raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Ladda ned den definitiva guiden för marknadsföring i pipeline: https://lnkd.in/e9xYj5M</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Landningssidan som klickas igenom från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>https://image-store.slidesharecdn.com/d29165c0-1e0b-4ffc-a494-d2c77e7cd4a6-large.jpeg</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det egna URL-namn som visas på sökannonsen, hämtat från annonskontot som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>marektomeasure.com/guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för nyckelordet som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>__GAId_lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det nyckelord som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning)</p>
      </td>
      <td>
        <p>lisu03151846</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den typ av matchning som hittas mellan sökfrasen och det köpta nyckelordet.</p>
      </td>
      <td>
        <p>Bred</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FIRST_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida denna kontaktyta behandlas som den första kontakten i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_LEAD_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som den inledande kontakten i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_OPP_CREATION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som ett sätt att skapa affärsmöjligheter i affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_CLOSED_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida denna kontaktyta behandlas som den slutna kontakten i affärsmöjlighetsresan eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>STAGES_TOUCHED</td>
      <td>varchar</td>
      <td>Det här fältet har tagits bort. Använd Stage_Transitions-tabellerna för sceninformation.</td>
      <td>null</td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om kontaktytan hade en formulärfyllning under sessionen eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som det första intrycket av affärsmöjlighetens resa</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FIRST_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är en första beröring (se Is_First_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAST_ANON_CLICK_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom det är en beröring för att skapa leads (se Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>U_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en oformad beröring (se Is_First_Touch och Is_Lead_Creation_Touch).</p>
      </td>
      <td>
        <p>100</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>W_SHAPE_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en w-formad beröring (se Is_First_Touch, Is_Lead_Creation_Touch och Is_Opp_Creation_Touch). Förväntas vara 0 eftersom detta är ett BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FULL_PATH_PERCENTAGE</p>
      </td>
      <td>
        <p>number(22,19)</p>
      </td>
      <td>
        <p>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en fullständig banmodell (se Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Förväntas vara 0 eftersom detta är ett BT.</p>
      </td>
      <td>
        <p>0</p>
      </td>
    </tr>
    <tr>
      <td>CUSTOM_MODEL_PERCENTAGE</td>
      <td>number(22,19)</td>
      <td>Den beräknade procentandelen som tilldelats den här kontaktytan eftersom den ingår i en anpassad modell (se Is_First_Touch, Is_Lead_Creation_Touch, Is_Opp_Creation_Touch, Is_Closed_Touch). Förväntas vara 0 eftersom detta är ett BT.</p>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Anger om den här kontaktytan tas bort.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td>
        <p>Sekundärnyckel till vyn Biz_Facts.</p>
      </td>
      <td>
        <p>-9004910726709710000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CONTACT_ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>
        <p>LEAD_ROW_KEY</p>
      </td>
      <td>
        <p>tal(38,0)</p>
      </td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_URLS {#biz-urls}

Sammanställning av URL-adresser från landningssidor, referenssidor och sidvyer.

<table>
  <tbody>
    <tr>
      <th>Kolumn</th>
      <th>Datatyp</th>
      <th>Beskrivning</th>
      <th>Exempeldata</th>
    </tr>
    <tr>
      <td>ID</td>
      <td>varchar</td>
      <td>Den fullständiga URL:en,</td>
      <td>https://www.adobe.com/blog/strategic-marketing-plangoals</td>
    </tr>
    <tr>
      <td>SCHEME</td>
      <td>varchar</td>
      <td>Säker kommunikation av webbsidan via nätverket.</td>
      <td>https</td>
    </tr>
    <tr>
      <td>VÄRD</td>
      <td>varchar</td>
      <td>Domänen för URL:en, med eventuella underdomäner.</td>
      <td>www.adobe.com</td>
    </tr>
    <tr>
      <td>PAGE_TITLE</td>
      <td>varchar</td>
      <td>Sidans namn.</td>
      <td>The CMO's Guide to B2B Marketing Attribution Download</td>
    </tr>
    <tr>
      <td>BANA</td>
      <td>varchar</td>
      <td>Den del av URL:en som pekar på en viss plats på värden.</td>
      <td>/blog/strategy-marketing-planaim</td>
    </tr>
    <tr>
      <td>PORT</td>
      <td>varchar</td>
      <td>Porten från en Internetvärd, valfri i en URL.</td>
      <td>584</td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>tal(38,0)</td>
      <td>Sekundärnyckel till vyn Biz_Facts.</td>
      <td>5686109553536636820</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_USER_TOUCHPOINTS {#biz-user-touchpoints}

Alla kontaktpunkter som skapats från en händelse som är kopplad till ett e-postmeddelande.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Ett unikt ID för användarens kontaktyta.</p>
      </td>
      <td>
        <p>person@adobe.com_2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2018-09-05 23:30:53 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>E-POST</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>E-postadress som är kopplad till användarkontaktpunkten.</p>
      </td>
      <td>
        <p>person@adobe.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för sessionen som skapade användarkontaktpunkten.</p>
      </td>
      <td>
        <p>2018-01-05:16-47-02-8803320.ddf67c101f58</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_Member_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Campaign-medlemmen som skapade användarkontaktpunkten.</p>
      </td>
      <td>
        <p>00v0Z0001VTgv1QAD</p>
      </td>
    </tr>
    <tr>
      <td>CRM_ACTIVITY_ID</td>
      <td>varchar</td>
      <td>ID för aktiviteten som skapade användarkontaktpunkten.</td>
      <td>1678625515</td>
    </tr>
    <tr>
      <td>
        <p>CRM_EVENT_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för den händelse som skapade användarkontaktpunkten.</p>
      </td>
      <td>
        <p>00U0Z0000pCZmyUAG</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CRM_TASK_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>TId för aktiviteten som skapade användarkontaktpunkten.</p>
      </td>
      <td>
        <p>00T0Z00004Qbd1jUAB</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IMPRESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Impression som skapade användarkontaktpunkten.</p>
      </td>
      <td>00T0Z00004Qbd1jUAB</td>
    </tr>
    <tr>
      <td>IS_FIRST_KNOWN_TOUCH</td>
      <td>boolesk</td>
      <td>Huruvida denna kontaktyta behandlas som den första kontakten i affärsmöjlighetens resa eller inte.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>VISITOR_ID</td>
      <td>varchar</td>
      <td>Det första cookie-ID:t för det relaterade besökar-ID:t.</td>
      <td>v_36ec805b4db344d6e92c972c86aee34a</td>
    </tr>
    <tr>
      <td>
        <p>TOUCHPOINT_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när användarkontaktpunkten inträffade.</p>
      </td>
      <td>
        <p>2018-01-05 16:47:02.000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MARKETING_TOUCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Typ av aktivitet, webbbesök, webbformulär, webbchatt, telefonsamtal, [CRM]-kampanj eller [CRM]-aktivitet. I CRM kallas det"Touchpoint Type".</p>
      </td>
      <td>
        <p>Webbformulär</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KANAL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Kanalen som kontaktytan hamnar i, enligt definition i de anpassade kanaldefinitionerna i [!DNL Marketo Measure] App. I CRM refereras till som"Marknadskanal - Sökväg".</p>
      </td>
      <td>
        <p>Social.LinkedIn</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_NAMN</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen upptäckte den webbläsare som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Firefox</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEBBLÄSARE_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av webbläsaren som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>33</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade plattform som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>Mac</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLATFORM_VERSION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är den identifierade versionen av plattformen som användaren var på under sessionen.</p>
      </td>
      <td>
        <p>10_12</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. I CRM kallas den"landningssida".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LANDING_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första landningssidan i sessionen som resulterade i en kontaktyta. En rå landningssida kommer att innehålla alla frågeparametrar i URL:en. I CRM kallas det"landningssida - Raw".</p>
      </td>
      <td>
        <p>https://www.adobe.com/blog/budget-and-planning-maturity-model-b2b-marketing?utm_source=feedburner&amp;utm_medium=feed&amp;utm_campaign=Feed%3A+ marketo+%mät%27s+Pipeline+Marketing+Blog%29</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. I CRM kallas det"Refererarsida".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REFERRER_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Vanligtvis den externa landningssidan omedelbart innan användaren kommer till webbplatsen. En råhänvisningssida kan innehålla frågeparametrar i URL:en. I CRM refereras till"Refererarsida - Raw".</p>
      </td>
      <td>
        <p>https://www.google.com/</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i tabellen Attribution_Touchpoints, utan i tabellen Form_Submits. I CRM refereras till som "formulär-URL".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_PAGE_RAW</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det första formuläret som spelats in i en session som resulterade i en kontaktyta. Efterföljande formuläröverföringar visas inte i tabellen Attribution_Touchpoints, utan i tabellen Form_Submits. En sida med Raw-formulär kan innehålla frågeparametrar i URL:en. I CRM refereras till"Form URL - Raw".</p>
      </td>
      <td>
        <p>http://info.adobe.com/adwords-for-lead-generation?utm_source=linkedin&amp;utm_medium=paid&amp;utm_content=sfskill&amp;utm _campaign=Content%20-%20AdWords%20Guide</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>FORM_DATE</p>
      </td>
      <td>
        <p>timestamp_ntz</p>
      </td>
      <td>
        <p>Datum när formuläret skickades.</p>
      </td>
      <td>
        <p>2015-06-03 17:49:10 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ORT</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades den ort som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>Oakland</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>REGION</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen är det område som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>Kalifornien</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>LAND</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Från javascript- och IP-adressen identifierades det land som användaren befann sig i under sessionen.</p>
      </td>
      <td>
        <p>USA</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MEDEL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera mediet som resulterade i kontaktytan. Detta kan antingen tolkas ut från URL:en från utm_medium. Eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "cpc" eller "display".</p>
      </td>
      <td>
        <p>betald</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>WEB_SOURCE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Används för att definiera källan som resulterade i kontaktytan. Detta kan tolkas från URL:en från utm_source, vanligtvis inställd som CRM Campaign om den synkroniserades från CRM, eller om [!DNL Marketo Measure] kan tolka en annons, det kan vara värden som "Google AdWords" eller "Facebook". Refereras i CRM till"Kontaktpunktskälla".</p>
      </td>
      <td>
        <p>linkedin</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SEARCH_PHRASE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Värdet som användaren angav i webbläsaren för att söka efter och hamnade på webbplatsen. Beroende på nyckelordsköp kan det här matcha nyckelorden som köpts från plattformen Betald sökning eller inte.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_PROVIDER</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Annonsplattform [!DNL Marketo Measure] har kunnat lösa sig från, vanligtvis en av våra integreringspartners.</p>
      </td>
      <td>
        <p>Google</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>aw.6601259029</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ACCOUNT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonskontot som annonsen löstes från.</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Konto</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonseraren från annonskontot som annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>300181641</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>ADVERTISER_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonseraren från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Marknadsföringsanalys</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för webbplatsen från annonskontot där annonsen löstes från. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>1695651</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>SITE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på webbplatsen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>Quora.com</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>120839827</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>PLACEMENT_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på placeringen från annonskontot där annonsen löstes. Detta gäller endast för Doubleclick Campaign Manager.</p>
      </td>
      <td>
        <p>vägspärr</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CAMPAIGN_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på kampanjen från annonskontot där annonsen löstes.</p>
      </td>
      <td>
        <p>Varumärke</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google Adwords.</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.16750166675</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_GROUP_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namn på annonskoncern från annonskontot där annonsen löstes från. Detta gäller endast Google AdWords.</p>
      </td>
      <td>
        <p>Märke - kärna</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>AD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för annonsen från annonskontot som annonsen löstes från. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>dc.6114.8882972.25272734.492579576</td>
    </tr>
    <tr>
      <td>
        <p>AD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på annonsen från annonskontot där annonsen löstes. Detta gäller för Doubleclick Campaign Manager och Facebook (displayannonser).</p>
      </td>
      <td>Webbinarium - marginallist</td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för Creative-objektet från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.1675016675.195329631298</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det Creative-objekt från annonskontot där annonsen löstes. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>[!DNL Marketo Measure] Officiell webbplats</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_1</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den första raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Intäktsplanering och attribuering</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESCRIPTION_2</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den andra raden i Creative från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>Läs varför över 250 företag väljer [!DNL Marketo Measure] för marknadsattribuering. Hämta en demo!</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DESTINATION_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Landningssidan som klickas igenom från sökannonsen, hämtad från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>http://info.adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>CREATIVE_DISPLAY_URL</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Det egna URL-namn som visas på sökannonsen, hämtat från annonskontot som annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>adobe.com/demo</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_UNIQUE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>ID för nyckelordet som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning).</p>
      </td>
      <td>
        <p>aw.6601259029.208548635.1675016675.46267805426</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_NAME</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Namnet på det nyckelord som köpts från köpet av betald sökning, hämtat från annonskontot där annonsen löstes från. Detta gäller Google AdWords och Bing Ads (sökning)</p>
      </td>
      <td>
        <p>[marketo]</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>KEYWORD_MATCH_TYPE</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>
        <p>Den typ av matchning som hittas mellan sökfrasen och det köpta nyckelordet.</p>
      </td>
      <td>
        <p>Exakt</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_FORM_SUBMISSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om kontaktytan hade en formulärfyllning under sessionen eller inte.</p>
      </td>
      <td>
        <p>true</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_IMPRESSION_TOUCH</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Huruvida den här kontaktytan behandlas som den första tryckningen av affärsmöjlighetens resa eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>IS_DELETED</p>
      </td>
      <td>
        <p>boolesk</p>
      </td>
      <td>
        <p>Om kontaktytan tas bort eller inte.</p>
      </td>
      <td>
        <p>false</p>
      </td>
    </tr>
    <tr>
      <td>ROW_KEY</td>
      <td>tal(38,0)</td>
      <td>Sekundärnyckel till vyn Biz_Facts.</td>
      <td>-5269090762570690000</td>
    </tr>
    <tr>
      <td>LANDING_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>REFERRER_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>FORM_PAGE_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ACCOUNT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>ADVERISER_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>SITE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>PLACEMENT_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CAMPAIGN_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>AD_GROUP_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>CREATIVE_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>KEYWORD_ROW_KEY</td>
      <td>tal(38,0)</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

### BIZ_WEB_HOST_MAPPINGS {#biz-web-host-mappings}

Mappa tabell till mappning [!DNL Marketo Measure] Sessions-ID till Adobe ECID och Munckin ID.

<table>
  <tbody>
    <tr>
      <th>
        <p>Kolumn</p>
      </th>
      <th>
        <p>Datatyp</p>
      </th>
      <th>
        <p>Beskrivning</p>
      </th>
      <th>
        <p>Exempeldata</p>
      </th>
    </tr>
    <tr>
      <td>
        <p>ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Ett unikt ID för mappningsposten.</td>
      <td>
        <p>0d643578c0c74753eff91abe668ed328|2020-06-17:19:03:36|0002|0|568668</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>COOKIE_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>The [!DNL Marketo Measure] inspelat cookie-id.</td>
      <td>0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>VISITOR_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>Det första cookie-ID:t för det relaterade besökar-ID:t.</td>
      <td>v_0d643578c0c74753eff91abe668ed328</td>
    </tr>
    <tr>
      <td>
        <p>SESSION_ID</p>
      </td>
      <td>
        <p>varchar</p>
      </td>
      <td>The [!DNL Marketo Measure] Sessions-ID.</td>
      <td>2018-08-06:01-35-24-1231230.9bc63c34482f</td>
    </tr>
    <tr>
      <td>
        <p>EVENT_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>Datum när mappningen registrerades.</td>
      <td>
        <p>2020-06-17 19:03:36 000</p>
      </td>
    </tr>
    <tr>
      <td>
        <p>MODIFIED_DATE</p>
      </td>
      <td>timestamp_ntz</td>
      <td>
        <p>Datum när posten senast ändrades.</p>
      </td>
      <td>
        <p>2020-06-17 19:03:36 000</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL för sidvyn, utan frågeparametrar.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html</p>
      </td>
    </tr>
    <tr>
      <td>CURRENT_PAGE_RAW</td>
      <td>
        <p>varchar</p>
      </td>
      <td>URL för sidvyn, inklusive eventuella frågeparametrar.</td>
      <td>
        <p>https://learn.atest.com/simplify-retention-starter-kit.html?x=nGfrBF&amp;utm_medium=cpc&amp;utm_source=intensify</p>
      </td>
    </tr>
    <tr>
      <td>IP_ADDRESS</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Den registrerade IP-adressen.</td>
      <td>
        <p>159.203.142.127</p>
      </td>
    </tr>
    <tr>
      <td>TYP</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Anger händelsetypen.</td>
      <td>
        <p>HostMapping</p>
      </td>
    </tr>
    <tr>
      <td>USER_AGENT_STRING</td>
      <td>
        <p>varchar</p>
      </td>
      <td>Enhet och webbläsare som spelades in när sidvyn skapades.</td>
      <td>
        <p>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, t.ex. Gecko) Chrome/79.0.3945.130 Safari/537.36</p>
      </td>
    </tr>
    <tr>
      <td>CLIENT_SEQUENCE</td>
      <td>varchar</td>
      <td>Anger i vilken ordning sidvyn skapades i sessionen.</td>
      <td>2</td>
    </tr>
    <tr>
      <td>CLIENT_RANDOM</td>
      <td>varchar</td>
      <td>Används för intern revision och bearbetning.</td>
      <td>566868</td>
    </tr>
    <tr>
      <td>IS_DUPLICATED</td>
      <td>boolesk</td>
      <td>Anger om posten betraktas som en dubblett.</td>
      <td>false</td>
    </tr>
    <tr>
      <td>IS_PROCESSED</td>
      <td>boolesk</td>
      <td>Används för intern bearbetning.</td>
      <td>true</td>
    </tr>
    <tr>
      <td>MAPPING_TYPE</td>
      <td>varchar</td>
      <td>Typen av ID som är mappad till [!DNL Marketo Measure] cookie-ID.</td>
      <td>Adobe_orgId_eccid</td>
    </tr>
    <tr>
      <td>MAPPING_ORD_ID</td>
      <td>varchar</td>
      <td>Adobe IMS-organisation-ID.</td>
      <td>8CC867C25245ADC30A490D4C</td>
    </tr>
    <tr>
      <td>MAPPING_COOKIE_ID</td>
      <td>varchar</td>
      <td>Adobe ECID för angivet Org ID.</td>
      <td>09860926390077352923264316157493772857</td>
    </tr>
    <tr>
      <td>_CREATED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten skapades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_MODIFIED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten senast ändrades i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
    <tr>
      <td>_DELETED_DATE</td>
      <td>timestamp_ntz</td>
      <td>Datum när posten markerades som borttagen i Snowflake.</td>
      <td>2020-01-01 01:01:00,000</td>
    </tr>
  </tbody>
</table>

## Exempelfrågor {#sample-queries}

**Hur många Buyer Touchpoints (BT) fanns det för varje kanal/underkanal förra månaden?**

```
--Note: This query can quickly be modified to show Buyer Attribution Touchpoint (BAT) counts by switching the biz_touchpoints table to the biz_attribution_touchpoints table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,trim(split(ch.name,'.')[1])  as subchannel
      ,count(bt.id)                 as buyer_touchpoint_count
  from biz_user_touchpoints     ut
       left outer join
       biz_touchpoints          bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_channels             ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
   and ut.touchpoint_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
group by 1,2
```

**Hur mycket av de tilldelade intäkterna för varje kanal stängdes under den senaste månaden, för den fullständiga vägattribueringsmodellen?**

```
--Note: This query does not perform any currency conversion.  If your data contains multiple currencies, you will need to add in logic to perform the conversion to the desired currency using the biz_conversion_rates table.
 
select trim(split(ch.name,'.')[0])  as channel
      ,sum(opp.amount*(bat.full_path_percentage/100))   as attributed_revenue
  from biz_user_touchpoints         ut
       inner join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       inner join
       biz_opportunities            opp
        on bat.opportunity_id       = opp.id
       and opp._deleted_date        is null
       and opp.is_closed            = true
       and opp.is_won               = true
       and opp.close_date between add_months(date_trunc(month,current_date),-1) and last_day(dateadd(month,-1,current_date))
       left outer join
       biz_channels                 ch
        on ut.channel               = ch.id
       and ch._deleted_date         is null
 where ut._deleted_date is null
group by 1
```

**Vad är hela resan för en person?  (Visa alla kontaktpunkter för en enda e-postadress.)**

```
select ut.touchpoint_date
      ,ut.marketing_touch_type
      ,listagg(distinct ifnull(sdl.stage_name,sdo.stage_name),',')           as touchpoint_position
  from biz_user_touchpoints         ut
       left outer join
       biz_touchpoints              bt
        on bt.user_touchpoint_id    = ut.id
       and bt._deleted_date         is null
       left outer join
       biz_attribution_touchpoints  bat
        on bat.user_touchpoint_id   = ut.id
       and bat._deleted_date        is null
       left outer join
       biz_lead_stage_transitions   lst
        on lst.touchpoint_id        = bt.id
       and lst._deleted_date        is null
       and lst.is_pending           = false
       and lst.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdl
        on lst.stage_id             = sdl.id
       and sdl._deleted_date        is null
       left outer join
       biz_opp_stage_transitions    ost
        on ost.touchpoint_id        = bat.id
       and ost._deleted_date        is null
       and ost.is_pending           = false
       and ost.is_non_transitional  = false
       left outer join
       biz_stage_definitions        sdo
        on ost.stage_id             = sdo.id
       and sdo._deleted_date        is null
 where ut._deleted_date     is null
   and ut.email             = [email address]
group by 1,2
order by 1
```

**Visa alla Buyer Attribution Touchpoints (BAT) och deras tilldelade intäkter för en enda möjlighet.**

>[!NOTE]
>
>Den här frågan returnerar tilldelad intäkt för w-formmodellen. Ändra modellen genom att uppdatera fältet i beräkningen av tillskrivna intäkter.

```
select bat.id
      ,bat.touchpoint_date
      ,bat.email
      ,opp.amount*(bat.w_shape_percentage/100)             as attributed_revenue
      ,listagg(osd.stage_name,', ')                        as touchpoint_position
  from biz_opportunities               opp
       inner join
       biz_attribution_touchpoints     bat
        on bat.opportunity_id      = opp.id
       and bat._deleted_date       is null
       left outer join
       biz_opp_stage_transitions       ost
        on ost.touchpoint_id       = bat.id
       and ost._deleted_date       is null
       and ost.is_pending          = false
       and ost.is_non_transitional = false
       left outer join
       biz_stage_definitions            osd
        on ost.stage_id             = osd.id
       and osd._deleted_date        is null
 where opp._deleted_date    is null
   and opp.id               = [opportunity id]
group by 1,2,3,4
order by touchpoint_date
```

[Tillbaka till början](#data-warehouse-schema)
