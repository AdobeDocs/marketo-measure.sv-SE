---
unique-page-id: 37356030
description: Parametern för e-postspårning - [!DNL Marketo Measure]
title: Spårningsparameter för e-post
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Spårningsparameter för e-post {#email-tracking-parameter}

Parametern för e-postspårning i [!DNL Marketo Measure] gör att marknadsförare kan behandla e-postklick som inskickade formulär så att kontaktytor genereras för dessa åtgärder. Utan att använda en parameter för e-postspårning behandlas genomklickningar från ett e-postmeddelande endast som&quot;webbbesök&quot; tills användaren faktiskt engagerar webbplatsen via ett formulär eller en webbchatt.

## Användningsfall  {#use-cases}

**Registrering av webbinarium**: Marknadsföringsteamet skickar en e-postinbjudan med en enda knapp för att registrera sig för ett webbinarium. Eftersom e-postmeddelandet redan innehåller information om personen registrerar det automatiskt med ett enda klick. Landningssidan innehåller e-postspårningsparametern, så när de klickar igenom och landar på bekräftelsesidan kan [!DNL Marketo Measure] hämta e-postadressen och behandla genomklickningen som en formulärfyllning, som genererar en kontaktyta.

**Hämtning av innehåll**: Content Marketing-teamet vill befordra en nyligen publicerad e-bok som de har publicerat med en direkt nedladdningslänk från ett e-postmeddelande. När e-postmallen skapas innehåller bekräftelsesidan e-postspårningsparametern så att [!DNL Marketo Measure] kan registrera e-postadressen när de klickar igenom. Utan att behöva fylla i ett formulär på webbplatsen kan [!DNL Marketo Measure] generera en kontaktyta för innehållsnedladdningen. Detta beror på att e-postmeddelandet landade dem på bekräftelsesidan med e-postspårningsparametern.

## Så här fungerar det {#how-it-works}

När en besökare anländer till din webbplats förväntar sig [!DNL Marketo Measure] att hitta en landningssida med antingen en e-postadress eller ett [!DNL Salesforce]-ID så att vi kan koppla besöket till en&quot;formulärsändning&quot; och generera en kontaktyta för aktiviteten.

Som kund skapar du en e-postmall på samma sätt som du brukar göra. När det är dags att lägga till i landningssidan för den åtgärd som du vill spåra måste du fastställa antingen variabelkoden, variabelkoden eller makrot som din Marketing Automation Platform accepterar för att dynamiskt visa värdet för varje individ.

Marketo Measure godkänner följande värden: E-postadress, Salesforce lead-ID eller Salesforce Contact-ID.

## Exempel på taggar {#tag-examples}

<table> 
 <colgroup> 
  <col> 
  <col> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th><p>Marknadsföringsautomatisering</p></th> 
   <th><p>Token / Tagg / Makro </p></th> 
   <th><p>Exempel</p></th> 
   <th><p>Stödmaterial</p></th> 
  </tr> 
  <tr> 
   <td><p>Marketo</p></td> 
   <td><p>{{lead.Email Address}} </p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}</p></td> 
   <td><p>https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html</p></td> 
  </tr> 
  <tr> 
   <td><p>Pardot</p></td> 
   <td><p>%%email%% </p><p>eller</p><p>%%user_crm_id%%</p></td> 
   <td><p>https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%</p></td> 
   <td><p>https://help.salesforce.com/s/articleView?language=en_US&amp;id=pardot_variable_tags_reference.htm&amp;type=5</p></td> 
  </tr> 
  <tr> 
   <td><p>Hubspot</p></td> 
   <td><p>(infogat via Redigeraren)</p></td> 
   <td><p>n/a</p></td> 
   <td><p>https://knowledge.hubspot.com/website-pages/personalize-your-content</p></td> 
  </tr> 
  <tr> 
   <td><p>Aktiv-på</p></td> 
   <td><p>(infogat via Message Composer)</p></td> 
   <td><p>n/a</p></td> 
   <td><p>https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data</p></td> 
  </tr> 
 </tbody> 
</table>

Slutligen, inom [!DNL Marketo Measure] måste du ange spårningsparametern så att [!DNL Marketo Measure] kan hitta e-postadressen eller ID-värdet. Standardvärdet är &quot;mailId&quot; enligt exemplen ovan och skärmbilden nedan. Ange värdet i inställningarna i [!DNL Marketo Measure] och klicka sedan på **[!UICONTROL Save]**.

![](assets/one.png)
