---
description: Riktlinjer för parametrar för e-postspårning för Marketo Measure-användare
title: Spårningsparameter för e-post
exl-id: e2cfd59e-ce4a-4cbb-b64a-828d1db7410f
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '427'
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

| Marknadsföringsautomatisering | Token / Tagg / Makro | Exempel | Stödmaterial |
| --- | --- | --- | --- |
| Marketo | {{lead.Email Address}} | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId={{lead.EmailAddress}}> | [Översikt över token](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/personalizing-landing-pages/tokens-overview.html) |
| Pardot | %%email%% eller %%user_crm_id%% | <https://engage.marketo.com/rs/460-TDH-945/images/BZ-B2B-Marketing-Attribution-101-ebook.pdf?mailId=%%email%%> | [Referens för punktvariabelmärkord](https://help.salesforce.com/s/articleView?language=en_US&id=pardot_variable_tags_reference.htm&type=5) |
| Hubspot | (infogat via Redigeraren) | n/a | [HubSpot-anpassning av innehåll](https://knowledge.hubspot.com/website-pages/personalize-your-content) |
| Aktiv-på | (infogat via Message Composer) | n/a | [Aktiv-på-anpassa e-postinnehåll](https://connect.act-on.com/hc/en-us/articles/360033436074-How-to-Personalize-Email-Content-with-CRM-Data) |

Slutligen, inom [!DNL Marketo Measure] måste du ange spårningsparametern så att [!DNL Marketo Measure] kan hitta e-postadressen eller ID-värdet. Standardvärdet är &quot;mailId&quot; enligt exemplen ovan och skärmbilden nedan. Ange värdet i inställningarna i [!DNL Marketo Measure] och klicka sedan på **[!UICONTROL Save]**.

![Och slutligen, inom Marketo Measure, måste du ange spårningsparametern](assets/marketo-engage-activities-01.png)
