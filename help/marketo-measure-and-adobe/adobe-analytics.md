---
description: '[!DNL Marketo Measure] integreringar med Adobe Analytics - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] integreringar med  [!DNL Adobe Analytics]'
exl-id: 3a125a15-eb74-454a-afb3-75746a1dfac6
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---


# [!DNL Marketo Measure] integreringar med Adobe Analytics {#marketo-measure-integrations-with-adobe-analytics}

Tack vare integreringen av B2B-kundattribut kan gemensamma användare av [!DNL Marketo Measure] och Adobe Analytics förfina sina [!DNL Adobe Analytics]-användarprofiler med värdefulla metadata som härleds från [!DNL Marketo Measure]-attribueringsmotorn och genom synkroniseringsfunktionerna med CRM:er ([!DNL Microsoft Dynamics] och [!DNL Salesforce]). Den är tillgänglig kostnadsfritt för alla kunder som använder [!DNL Adobe Analytics] och [!DNL Marketo Measure].

>[!PREREQUISITES]
>Du måste ha aktiva prenumerationer på både [!DNL Marketo Measure] och [!DNL Adobe Analytics].

## Konfigurera integreringen {#configuring-the-integration}

1. Skapa ett nytt kundattribut Data Source i din Experience Cloud-konsol. Detaljerade instruktioner [finns här](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html).

   Observera följande information som behövs i de senare stegen:

   * Alias-ID, som kan vara vilket värde som helst. Vi rekommenderar&quot;marketomeasure_id&quot;

   * FTP-serverns värdnamn och autentiseringsuppgifter (användarnamn och lösenord)

1. När kundattributsdata för Source har skapats fortsätter du konfigurationsprocessen genom att gå till skärmen **[!UICONTROL Integrations]** > **[!UICONTROL Connections]** på admin-menyn i [!DNL Marketo Measure].

1. Klicka på knappen **[!UICONTROL Set Up New Customer Attributes Connection]** och följ instruktionerna för att konfigurera integreringen av kundattribut. Användargränssnittet uppmanar dig att ange den anslutningsinformation för Alias ID och FTP som du fick när du skapade kundattributen Source i din Core Services Console. Välj den uppsättning kontoattribut som du vill synkronisera med ditt [!DNL Adobe Analytics]-konto.

   Ange ditt Adobe IMS-organisations-ID. Detta ID visas i det nedre högra hörnet av din Adobe Experience Cloud Admin Console. Mer hjälp om hur du hittar detta ID finns i Adobe Account Team (din kontoansvarige).

1. När du har skapat anslutningen i ditt [!DNL Marketo Measure]-konto måste du gå tillbaka till din Experience Cloud-konsol för att [verifiera schemat](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/validate-schema.html?lang=en). Du behöver inte bekymra dig om FTP-filöverföringen. [!DNL Marketo Measure] har automatiserat den delen åt dig. Gå till schemaskärmen Visa/redigera för det kundattribut Source du skapade i steg 1 och tala om för Adobe vilka datatyper som finns för vart och ett av de attribut som [!DNL Marketo Measure] har överfört åt dig. Du kan också skapa nya visningsvänliga namn för de överförda attributen om du vill.

   Om du har valt att synkronisera attribut från CRM-kontoobjektet rekommenderar vi att du väljer nya visningsnamn för dem, eftersom [!DNL Marketo Measure] bara fyller i API-nivånamnen för dessa attribut, som vanligtvis inte är rapporteringsvänliga.

1. Det sista steget är att konfigurera attributprenumerationer för de Experience Cloud-program som du vill använda attributen i. Du kan konfigurera prenumerationer för [!DNL Adobe Analytics] eller [!DNL Adobe Target].  Mer information om hur du gör [finns här](https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/subscription.html).

## Attributbeskrivningar {#attribute-descriptions}

När du skapar en B2B-kundattributanslutning skapar [!DNL Marketo Measure] automatiskt en standarduppsättning med B2B-kundattribut åt dig. Dessa attribut beskrivs i tabellen nedan.

Förutom de som listas nedan kan du även överföra attribut som är kopplade till kontoobjektet i CRM. Om mer än ett konto är knutet till den angivna användaren fyller [!DNL Marketo Measure] i alla matchande kontoattributvärden i en semikolonavgränsad lista.

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
   <td>Kontonamnen som är associerade med den angivna webbbesökaren. Om mer än ett konto är knutet till den angivna användaren fyller [!DNL Marketo Measure] i alla matchande kontonamn i en semikolonavgränsad lista.<br/>
   <strong>Obs!</strong> account.name är namn på Salesforce-API-nivå för name-attributet i kontoobjektet. Du kan välja ett bättre visningsnamn (till exempel "Företag") för det här attributet under schemaverifieringssteget i integreringskonfigurationen (steg 4).</td>
  </tr>
  <tr>
   <td>Attribuerad intäkt -¡ MODEL›</td>
   <td>Intäkterna som tillskrivs den här kunden genom deras association med stängda affärsmöjligheter i CRM, enligt beräkningen av attribueringsmotorn [!DNL Marketo Measure].<br/>
   Det finns ett av dessa attribut för varje attribueringsmodell som din [!DNL Marketo Measure] -prenumeration tillåter (t.ex. "Attributed Revenue - Full Path").</td>
  </tr>
  <tr>
   <td>Djupaste Funnel Stage</td>
   <td>Den djupaste funnel-fasen av alla öppna affärsmöjligheter som är kopplade till den angivna användaren.</td>
  </tr>
  <tr>
   <td>Öppna affärsmöjligheter</td>
   <td>En semikolonavgränsad lista över de affärsmöjlighets-ID som den angivna användaren är kopplad till enligt dina CRM-data.</td>
  </tr>
 </tbody>
</table>

**En anteckning om attributbegränsningar**

De attribut som uppträder via den här integreringen räknas mot dina avtalsattributsgränser i [!DNL Adobe Analytics] och [!DNL Adobe Target]. Endast attribut som påträffas via en attributprenumeration (steg 5 i [Konfigurera integreringen](#configuring-the-integration)) räknas mot din gräns för det prenumererade programmet.

## Vanliga frågor {#faqs}

**Hur ändrar jag den uppsättning attribut som jag vill dela via den här integreringen?**

För att ett attribut som delas av [!DNL Marketo Measure] till din Adobe IMS-organisation via den här integreringen ska vara synligt och användas i [!DNL Adobe Analytics] måste det hittas via en attributprenumeration som konfigurerats i Core Services Console. Om du vill ta bort ett attribut så att det inte längre visas i [!DNL Adobe Analytics] kan du uppnå detta genom att ta bort attributprenumerationen.

Du kan också ta bort B2B-anslutningen för kundattribut i [!DNL Marketo Measure] och återskapa den med det attribut som du inte längre vill dela exkluderat från anslutningskonfigurationen. Om du vill lägga till attribut i integreringen måste du ta bort den befintliga anslutningen och skapa en ny med de attribut som du vill lägga till i konfigurationen.

Med tanke på ovanstående rekommenderar vi att du är så inkluderande som möjligt när du konfigurerar attributanslutningen för första gången när du väljer attribut.

**Vilka är några exempel på användningsexempel för den här integreringen?**

1. Kontobaserade trafikmått: Med attributet kontonamn kan du skapa segment för ett eller flera målkonton i Adobe Analytics och analysera platstrafikstatistik för endast den delmängd av trafiken som kommer från målkonton.
1. Content Analytics: Använd intäktsmåtten för att analysera vilket webbplatsinnehåll som är mest engagerande för kunder som till slut köper en produkt eller tjänst, eller för dem som uppnår ett visst funnel-stadium.
1. Live-deal-support: Förse säljteamet med åtgärdbar kunskap genom att analysera webbplatsbeteenden för användare som är kopplade till en viss öppen affärsmöjlighet i CRM.
