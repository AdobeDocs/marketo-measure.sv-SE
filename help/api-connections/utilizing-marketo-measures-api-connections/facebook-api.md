---
unique-page-id: 18874680
description: "[!DNL Facebook] API - [!DNL Marketo Measure]"
title: "[!DNL Facebook] API"
exl-id: d6d18545-baae-4103-b0a6-c3de681ec833
feature: APIs, Integration, UTM Parameters
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# [!DNL Facebook] API {#facebook-api}

## Introduktion {#introduction}

Liknar våra AdWords &amp; [!DNL Bing Ads] integreringar, vår [!DNL Facebook] integrering innebär två grundläggande åtgärder:

* Tagga alla automatiskt [!DNL Facebook] Ads with a [!DNL Marketo Measure] parameter (_bf)
* Ladda ned kostnadsinformation för alla aktiva Facebook-annonser

## Konfigurera [!DNL Facebook] Integrering {#how-to-configure-the-facebook-integration}

När det gäller konfiguration finns det sju steg att slutföra i [!DNL Marketo Measure] app.

1. Navigera till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och logga in.
1. Välj under Mitt konto **[!UICONTROL Settings]**.
1. Under Integreringar väljer du **[!UICONTROL Connections]**.
1. Välj **[!UICONTROL Set Up New Ads Connection]** och ett popup-fönster visas. Välj **[!UICONTROL Facebook]** och logga in med dina Facebook-uppgifter.

   >[!NOTE]
   >
   >Personen som ansluter [!DNL Facebook Ads] kontot måste vara en administratör inom [!DNL Facebook Ads] konto.

1. En gång [!DNL Marketo Measure] är ansluten till ditt Facebook-konto och klickar på pennikonen bredvid kontot.
1. Flytta &quot;Automatisk taggning?&quot; i den här vyn växla till Ja. Markera sedan kryssrutan i dialogrutan [!UICONTROL Learn More] för att godkänna villkoren. Se till att [!UICONTROL Auto-tagging] växlingen är fortfarande inställd på &#39;[!UICONTROL Yes]&#39;.

## Ansluter kontot {#connecting-the-account}

![](assets/1.gif)

## Aktivera automatisk taggning {#enabling-autotagging}

>[!NOTE]
>
>Om du aktiverar automatisk taggning återställer vi konverteringshistoriken och det sociala beviset för alla annonser som vi taggar. Vi rekommenderar [exportera dessa data som en CSV](https://www.facebook.com/business/help/205067636197240) innan du aktiverar automatisk taggning.

![](assets/2-2.png)

När du har aktiverat integreringen [!DNL Marketo Measure] börjar ladda ned annonskostnad till [!DNL Marketo Measure Marketing ROI] Instrumentpanel.

För att integreringen ska fungera på rätt sätt måste du aktivera automatisk taggning på [!DNL Facebook] konto. Detta gör att vårt system kan lägga till en _bf-parameter för alla annonslänkar. Den här processen lägger till den nya parametern ovanpå andra spårningsparametrar som du redan har lagt till i din [!DNL Facebook] annonser.

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
   <td><p>[[!DNL Facebook] Kampanj-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonskampanj </p></td> 
   <td><p>[[!DNL Facebook] Kampanjnamn], eller [utm_campaign] om det finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Annonsgrupp-ID</p></td> 
   <td><p>[[!DNL Facebook] Annonsuppsättnings-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Namn på annonsgrupp</p></td> 
   <td><p>[[!DNL Facebook] Annonsuppsättningsnamn]</p></td> 
  </tr> 
  <tr> 
   <td><p>Kontaktpunktskälla</p></td> 
   <td><p>"[!DNL Facebook]", eller [utm_source] om det finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Medel</p></td> 
   <td><p>"Social", eller [utm_medium] om sådan finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Annons-ID eller Creative_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[anpassat ID genererat från utm_content]</p></td> 
  </tr> 
  <tr> 
   <td><p>Lägg till innehåll eller Creative_Name (Data Warehouse)</p></td> 
   <td><p>[utm_content] om det finns</p></td> 
  </tr> 
  <tr> 
   <td><p>Nyckelordstext eller Nyckelordsnamn (Data Warehouse)</p></td> 
   <td><p>[utm_term] om den anges</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Unique_Id (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Annons-ID]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_name (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Annonsnamn]</p></td> 
  </tr> 
  <tr> 
   <td><p>Nyckelord_Unikt_ID (Data Warehouse)</p></td> 
   <td><p>[anpassat ID genererat från utm_term]</p></td> 
  </tr> 
  <tr> 
   <td><p>Ad_Provider (Data Warehouse)</p></td> 
   <td><p>"[!DNL Facebook]"</p></td> 
  </tr> 
  <tr> 
   <td><p>Account_Unique_ID (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Kontonr]</p></td> 
  </tr> 
  <tr> 
   <td><p>Kontonamn (Data Warehouse)</p></td> 
   <td><p>[[!DNL Facebook] Kontonamn</p></td> 
  </tr> 
 </tbody> 
</table>

## Vanliga frågor och svar {#faq}

**Fråga: Vad [!DNL Facebook] Annonserna stöds av [!DNL Marketo Measure]?**

A: Carousel, en bild. Inte video, bildspel eller samling just nu.

**Fråga: Vad är socialt bevis?**

S: Det sociala korrekturet är ett synligt engagemang som gilla-markeringar, klickningar, kommentarer och delningar.

**F: Vad händer när [!DNL Marketo Measure] taggar annonsen?**

S: [!DNL Facebook] tillåter inte att annonser redigeras så [!DNL Marketo Measure] måste ta bort den kreativa delen, som innehåller mål-URL:en, och sedan återskapa annonsen med de nya parametrarna.

**F: Varför gör det? [!DNL Marketo Measure] uppdatera alla [!DNL Facebook] Ads?**

A: [!DNL Marketo Measure] processen är att tagga alla annonser om de återaktiveras.

**F: Vilken behörighet behöver den anslutna användaren?**

A: ads_management, e-post

**F: Hur lång tid tar det att importera utgiftsdata?**

A: 1 timme

**F: Hur lång tid tar det att importera annonsdata?**

A: 4 timmar
