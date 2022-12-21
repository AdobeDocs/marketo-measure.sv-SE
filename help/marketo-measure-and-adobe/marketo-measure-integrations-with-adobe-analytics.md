---
description: "[!DNL Marketo Measure] Integrering med Adobe Analytics - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Integrering med [!DNL Adobe Analytics]"
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrering med Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

Integreringen av B2B-kundattribut möjliggör för användare av [!DNL Marketo Measure] och Adobe Analytics [!DNL Adobe Analytics] användarprofiler med värdefull metadata som härleds från [!DNL Marketo Measure] attribueringsmotor och synkningsförmåga med CRM:er ([!DNL Microsoft Dynamics] och [!DNL Salesforce]). Det är kostnadsfritt för alla kunder som använder [!DNL Adobe Analytics] och [!DNL Marketo Measure].

>[!PREREQUISITES]
>
>Du måste ha aktiva prenumerationer på båda [!DNL Marketo Measure] och [!DNL Adobe Analytics].

## Konfigurera integreringen {#configuring-the-integration}

1. Börja med att skapa en ny datakälla för kundattribut i Experience Cloud-konsolen. Detaljerade instruktioner [finns här](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/t-crs-usecase.html).

   Observera följande information som du behöver för några av de senare stegen i processen:

   * Alias-ID, som kan vara vilket värde som helst som du vill att det ska vara. Vi rekommenderar&quot;marketomeasure_id&quot;

   * FTP-serverns värdnamn och autentiseringsuppgifter (användarnamn och lösenord)

1. När datakällan för kundattribut har skapats fortsätter du konfigurationsprocessen genom att gå till **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** i [!DNL Marketo Measure] admin-menyn.

1. Klicka på **[!UICONTROL Set Up New Customer Attributes Connection]** och följ instruktionerna för att konfigurera integreringen av kundattribut. Användargränssnittet uppmanar dig att ange den anslutningsinformation för alias-ID och FTP som du fick när du skapade kundattributskällan i din Core Services Console samt att välja den uppsättning kontoattribut som du vill synkronisera med [!DNL Adobe Analytics] konto.

   Du måste också ange ditt Adobe IMS-org-ID. Detta ID visas i det nedre högra hörnet av Adobe Experience Cloud Admin Console. Om du vill ha mer hjälp med att hitta det här ID:t kontaktar du din Customer Success Manager.

1. När du har skapat anslutningen i [!DNL Marketo Measure] måste du gå tillbaka till Experience Cloud-konsolen för att kunna [validera schemat](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/validate-schema.html). Du behöver inte bekymra dig om FTP-filöverföringen, [!DNL Marketo Measure] har automatiserat den delen åt dig. Allt du behöver göra är att gå till schemaskärmen Visa/redigera för den Customer Attribute Source du skapade i steg 1 och tala om för Adobe vilka datatyper som finns för vart och ett av attributen [!DNL Marketo Measure] har överförts åt dig. Du kan också skapa nya visningsvänliga namn för de överförda attributen om du vill.

   Om du har valt att synkronisera attribut från CRM-kontoobjektet rekommenderar vi att du väljer nya visningsnamn för dem, som [!DNL Marketo Measure] fyller bara i API-nivånamn för dessa attribut, som vanligtvis inte är rapporteringsvänliga.

1. Det sista steget är att konfigurera attributprenumerationer för de Experience Cloud-program som du vill använda attributen i.  Du kan konfigurera prenumerationer för [!DNL Adobe Analytics] eller [!DNL Adobe Target].  Mer information om hur du gör det [finns här](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/subscription.html).

## Attributbeskrivningar {#attribute-descriptions}

När du skapar en ny B2B-anslutning för kundattribut, [!DNL Marketo Measure] skapar automatiskt en standarduppsättning B2B-kundattribut åt dig. Dessa attribut beskrivs i tabellen nedan.

Förutom de som listas nedan kan du även överföra attribut som är kopplade till kontoobjektet i CRM. Om mer än ett konto är knutet till den angivna användaren, [!DNL Marketo Measure] fyller i alla matchande kontoattributvärden i en semikolonavgränsad lista.

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td><b>Attributnamn</b></td> 
   <td><b>Beskrivning</b></td>
  </tr> 
  <tr> 
   <td>Account.Name</td> 
   <td>Kontonamnen som är associerade med den angivna webbbesökaren. Om mer än ett konto är knutet till den angivna användaren, [!DNL Marketo Measure] fyller i alla matchande kontonamn i en semikolonavgränsad lista.<br/>
   <strong>Obs!</strong> account.name är Salesforce-API-nivånamnet för name-attributet på account-objektet. Du kan välja ett bättre visningsnamn (t.ex. "Företag") för det här attributet under schemaverifieringssteget i integreringskonfigurationen (steg 4).</td>
  </tr>
  <tr> 
   <td>Attribuerad intäkt -¡ MODEL›</td> 
   <td>Intäkterna som tillskrivs den här kunden genom deras koppling till stängda affärsmöjligheter i CRM, enligt beräkning i [!DNL Marketo Measure] attribueringsmotor.<br/>
   Det kommer att finnas ett av dessa attribut för varje attribueringsmodell som [!DNL Marketo Measure] prenumerationer är tillåtna (t.ex. "Attributed Revenue - Full Path").</td>
  </tr>
  <tr> 
   <td>Fördjupad trattfas</td> 
   <td>Den djupaste trattfasen för alla öppna affärsmöjligheter som är associerade med den angivna användaren.</td>
  </tr>
  <tr> 
   <td>Öppna affärsmöjligheter</td> 
   <td>En semikolonavgränsad lista över de affärsmöjlighets-ID som den angivna användaren är kopplad till enligt dina CRM-data.</td>
  </tr> 
 </tbody> 
</table>

**En anteckning om attributbegränsningar**

Observera att attributen som uppstår via den här integreringen fortfarande kommer att räknas av mot dina avtalsbegränsningar för attribut i [!DNL Adobe Analytics] och [!DNL Adobe Target]. Endast attribut som påträffas via en attributprenumeration (steg 5 i [Konfigurera integreringen](#configuring-the-integration)) räknas av mot gränsen för det prenumererade programmet.

## Vanliga frågor {#faqs}

**Hur ändrar jag den uppsättning attribut jag vill dela via den här integreringen?**

För ett attribut som delas av [!DNL Marketo Measure] till din Adobe IMS-organisation via den här integreringen för att synas och användas i [!DNL Adobe Analytics]måste den nås via en attributprenumeration som konfigurerats i Core Services Console. Om du vill ta bort ett attribut så att det inte längre visas i [!DNL Adobe Analytics]kan du uppnå detta genom att helt enkelt ta bort attributprenumerationen.

Du kan även ta bort B2B-anslutningen för kundattribut i [!DNL Marketo Measure] och återskapa det med det attribut du inte längre vill dela exkluderat från anslutningskonfigurationen. Om du vill lägga till attribut i integreringen måste du ta bort den befintliga anslutningen och skapa en ny med de attribut som du vill lägga till i konfigurationen.

Med tanke på ovanstående rekommenderar vi att du är så inkluderande som möjligt när du konfigurerar attributanslutningen för första gången när du väljer attribut.

**Vilka är några exempel på användningsexempel för den här integreringen?**

1. Kontobaserade trafikvärden: Med hjälp av attributet för kontonamn kan du skapa segment för ett eller flera målkonton i Adobe Analytics och analysera platstrafiken för endast den delmängd av trafiken som kommer från målkonton.
1. Innehållsanalys: Använd intäktsmåtten för att analysera vilket webbplatsinnehåll som är mest engagerande för kunder som till slut köper en produkt eller tjänst, eller för dem som uppnår ett visst trattstadium.
1. Live-deal: Ge säljteamet användbar information genom att analysera webbplatsbeteenden för användare som är kopplade till en viss öppen affärsmöjlighet i CRM.
