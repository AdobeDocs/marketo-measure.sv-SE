---
description: '[!DNL Salesforce] Paketkonsolidering - [!DNL Marketo Measure]'
title: '[!DNL Salesforce] Paketkonsolidering'
exl-id: ae559f5f-91bf-4504-9d5a-af47f95ca01f
feature: Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# [!DNL Salesforce] Paketkonsolidering {#salesforce-package-consolidation}

För att förbättra användarupplevelsen och förenkla användningen sammanställs befintliga paket till ett enda heltäckande paket.

## Paketpensionering {#package-retirement}

Som en följd av denna konsolidering kommer det aktuella paketet V1, V2_EXT, V2_Security och alla rapporteringsprogram att kasseras efter augusti 2023. Om du redan har installerat V2-paketet måste du uppdatera det till den nya konsoliderade versionen.

## Nytt konsoliderat paket {#new-consolidated-package}

Det nya konsoliderade V2-paketet innehåller alla funktioner och funktioner som fanns i de tidigare paketen, vilket ger en bättre användarupplevelse. Det uppdaterade paketet ger effektivare spårning av marknadsförings- och försäljningsprestanda och ger djupare insikter om kundbeteenden.

Det finns två nya fält som förbättrar dina rapporteringsfunktioner:

* form_name: Detta fält är nu tillgängligt i BT/BAT-objekt och gör att användare kan skapa rapporter baserade på formulärnamn.
* user_touchpoint_id: Det här fältet gör att användare kan skapa rapporter med unika användarkontaktpunkter (`bizible2__User_Touchpoint_V2__c` i Salesforce).

## Support och övergångar {#support-and-transition}

[Supportteamet](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} är tillgängligt för att svara på eventuella frågor och hjälpa till att säkerställa en smidig övergång till det nya konsoliderade paketet.

## Nödvändiga åtgärder {#retired-actions}

* Om du redan har installerat V2-paketet måste du uppdatera det till den nya konsoliderade versionen.
* Om du har rapporter eller kontrollpaneler från ett Rapporteringspaket kan du enkelt återskapa dem utan några ändringar, eftersom alla fält finns i det konsoliderade paketet.
* Om du har rapporter med hjälp av fält i V2_EXT-paketet kan du återskapa dem i det konsoliderade paketet genom att följa stegen nedan:
   * Alla data i V2_EXT-fälten är tillgängliga i Touchpoint-fält, så du kan ändra dina rapporter och hämta data från motsvarande V2-kontaktpunktsfält genom att lägga till ett filter på pekpunktspositionen.
   * Exempelrapport som hämtar alla leads med Ad Content FT som innehåller texten&quot;Outreach&quot;.
      * V2_EXT-fråga:
         * bizible2_ext_Ad_Content_FT__c contains Outreach

![bizible2extAdContentFTc innehåller Outreach](assets/bizible-full-1.png)

* Motsvarande fråga i det konsoliderade paketet:
   * bizible2_Touchpoint_Position__c innehåller FT AND
   * bizible2_Ad_Content__c contains Outreach

![bizible2AdContentc innehåller Outreach](assets/bizible-taxonomy-1.png)

## Vanliga frågor och svar {#faq}

**Kommer det konsoliderade paketet att ha konflikter med fält i mitt befintliga paket?**

Du behöver inte avinstallera paketet innan du installerar det konsoliderade paketet. Det finns inga konflikter i fält eftersom de finns i ett annat namnutrymme.

**Hur kan jag fylla i data från mina aktuella paket i bakgrunden?**

Du kan arkivera en biljett [med support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} för att fylla i och bearbeta BT/BAT-data för att fylla i fält för kontaktpunkts-ID och formulär-ID.

**Kommer fälten i V1- och V2_EXT-paket att vara tillgängliga i det konsoliderade paketet?**

Ja. Det konsoliderade paketet innehåller samma fält i V1 med ytterligare uppdelning efter objekt och V2_EXT-fält via Touchpoint-fält.

**Kan rapporter som använder V2_EXT-fält återskapas i det konsoliderade paketet?**

Ja. Följ stegen i avsnittet [Obligatoriska åtgärder](#retired-actions).
