---
unique-page-id: 18874680
description: '[!DNL Facebook] API - [!DNL Marketo Measure]'
title: '[!DNL Facebook] API'
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 1%

---

# [!DNL Facebook] API {#facebook-api}

## Introduktion {#introduction}

Ungefär som i våra AdWords- och [!DNL Bing Ads]-integreringar utför vår [!DNL Facebook]-integrering två grundläggande åtgärder:

* Tagga alla [!DNL Facebook] annonser automatiskt med en [!DNL Marketo Measure]-parameter (_bf)
* Hämta annonsinformation för alla aktiva Facebook-annonser

## Konfigurera [!DNL Facebook]-integreringen {#how-to-configure-the-facebook-integration}

När det gäller konfiguration finns det sju steg att slutföra i appen [!DNL Marketo Measure].

1. Navigera till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och logga in.
1. Välj **[!UICONTROL Settings]** under Mitt konto.
1. Välj **[!UICONTROL Connections]** under Integreringar.
1. Välj **[!UICONTROL Set Up New Ads Connection]** så visas ett popup-fönster. Välj **[!UICONTROL Facebook]** och logga in med dina inloggningsuppgifter för Facebook.

   >[!NOTE]
   >
   >Personen som ansluter [!DNL Facebook Ads]-kontot måste vara en administratör inom [!DNL Facebook Ads]-kontot.

1. När [!DNL Marketo Measure] är ansluten till ditt Facebook-konto klickar du på pennikonen bredvid kontot.
1. Flytta &quot;Automatisk taggning?&quot; i den här vyn växla till Ja. Markera sedan kryssrutan i avsnittet [!UICONTROL Learn More] för att godkänna villkoren. Kontrollera att växlingsknappen [!UICONTROL Auto-tagging] fortfarande är inställd på [!UICONTROL Yes].

## Ansluter kontot {#connecting-the-account}

![](assets/1.gif)

## Aktivera automatisk taggning {#enabling-autotagging}

>[!NOTE]
>
>Om du aktiverar automatisk taggning återställer vi konverteringshistoriken och det sociala beviset för alla annonser som vi taggar. Vi rekommenderar att [exporterar dessa data som en CSV](https://www.facebook.com/business/help/205067636197240) innan du aktiverar automatisk taggning.

![](assets/2-2.png)

När du har aktiverat integreringen börjar [!DNL Marketo Measure] hämta annonskostnad till [!DNL Marketo Measure Marketing ROI]-instrumentpanelen.

För att integreringen ska fungera på rätt sätt måste du aktivera automatisk taggning på ditt [!DNL Facebook]-konto. Detta gör att vårt system kan lägga till en _bf-parameter för alla annonslänkar. Den här processen lägger till den nya parametern ovanpå andra spårningsparametrar som du redan har lagt till i dina [!DNL Facebook]-annonser.

![](assets/3.gif)

## Fältmappning {#field-mapping}

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p><strong>Touchpoint-fält</strong></p></th> 
   <th><p><strong>Värde</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>ID för annonskampanj</p></td> 
   <td><p>[[!DNL Facebook] kampanj-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonskampanj </p></td> 
   <td><p>[[!DNL Facebook] kampanjnamn], eller [utm_campaign] om det anges</p></td> 
  </tr> 
  <tr> 
   <td><p>Annonsgrupp-ID</p></td> 
   <td><p>[[!DNL Facebook] annonsuppsättnings-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonsgrupp</p></td> 
   <td><p>[[!DNL Facebook] annonsuppsättningsnamn]</p></td> 
  </tr> 
  <tr> 
   <td><p>Touchpoint Source</p></td> 
   <td><p>"[!DNL Facebook]", eller [utm_source] om angivet</p></td> 
  </tr> 
  <tr> 
   <td><p>Medium</p></td> 
   <td><p>"Social", eller [utm_medium] om sådan finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Annons-ID eller Creative_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[anpassat ID genererat från utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Lägg till innehåll eller Creative_namn (Data Warehouse)</p></td> 
   <td><p>[utm_content] om det finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Nyckelordstext eller Nyckelordsnamn (Data Warehouse)</p></td> 
   <td><p>[utm_term] om den anges</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] annons-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Name (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] annonsnamn]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nyckelord_Unikt_ID (Data Warehouse)</p></td> 
   <td><p>[anpassat ID genererat från utm_term]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Provider (Data Warehouse)</p></td> 
   <td><p>[!DNL Facebook]</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Unique_ID (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] kontonummer]</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Name (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] kontonamn]</p></td> 
  </tr> 
 </tbody> 
</table>

## Vanliga frågor och svar {#faq}

**F: Vilka [!DNL Facebook] annonser stöds av [!DNL Marketo Measure]?**

A: Carousel, en bild. Inte video, bildspel eller samling just nu.

**F: Vad är socialt bevis?**

S: Det sociala korrekturet är ett synligt engagemang som gilla-markeringar, klickningar, kommentarer och delningar.

**F: Vad händer när [!DNL Marketo Measure] taggar annonsen?**

S: [!DNL Facebook] tillåter inte att annonser redigeras, så [!DNL Marketo Measure] måste ta bort den kreativa delen, som innehåller mål-URL:en, och sedan återskapa annonsen med de nya parametrarna.

**F: Varför uppdaterar [!DNL Marketo Measure] alla [!DNL Facebook] annonser?**

S: Processen [!DNL Marketo Measure] är att tagga alla annonser om de återaktiveras.

**F: Vilken behörighet behöver den anslutna användaren?**

A: ads_management, e-post

**F: Hur lång tid kan det ta att importera utgiftsdata?**

A: 1 timme

**F: Hur lång tid tar det att importera annonsdata?**

A: 4 timmar
