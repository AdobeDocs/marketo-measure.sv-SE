---
description: "[!DNL Salesforce] Paketkonsolidering - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Salesforce] Paketkonsolidering"
hide: true
hidefromtoc: true
source-git-commit: 502a08b9a670c0b9a997a0fbb238a4db865f79d2
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# [!DNL Salesforce] Paketkonsolidering {#salesforce-package-consolidation}

Vi är glada över att kunna meddela kommande ändringar av Marketo Measure Salesforce-paketen. För att förbättra användarupplevelsen och förenkla användningen konsoliderar vi alla befintliga paket till ett enda heltäckande paket.

## Paketpensionering {#package-retirement}

Som en följd av denna konsolidering kommer det aktuella paketet V1, V2_EXT, V2_Security och alla rapporteringsprogram att kasseras efter augusti 2023. Om du redan har installerat V2-paketet måste du uppdatera det till den nya konsoliderade versionen.

## Nytt konsoliderat paket {#new-consolidated-package}

Det nya konsoliderade V2-paketet innehåller alla funktioner och funktioner som fanns i de tidigare paketen, vilket ger en bättre användarupplevelse. Det uppdaterade paketet ger effektivare spårning av marknadsförings- och försäljningsprestanda och ger djupare insikter om kundbeteenden.

## Support och övergång {#support-and-transition}

Vi är medvetna om att denna förändring kan kräva justeringar, och vi strävar efter att stödja dig under hela processen. Våra [supportteam](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} är lätt tillgängliga för att svara på eventuella frågor och bidra till en smidig övergång till det nya konsoliderade paketet.

## Nödvändiga åtgärder {#retired-actions}

* Om du redan har installerat V2-paketet måste du uppdatera det till den nya konsoliderade versionen.
* Om du har rapporter eller kontrollpaneler från ett Rapporteringspaket kan du enkelt återskapa dem utan några ändringar, eftersom alla fält som används finns i det konsoliderade paketet.
* Om du har rapporter med hjälp av fält i V2_EXT-paketet kan du återskapa dem i det konsoliderade paketet genom att följa stegen nedan:
   * Alla data i V2_EXT-fälten är tillgängliga i Touchpoint-fält, så du kan ändra dina rapporter och hämta data från motsvarande V2-kontaktpunktsfält genom att lägga till ett filter på pekpunktspositionen.
   * Exempelrapport som hämtar alla leads med Ad Content FT som innehåller texten&quot;Outreach&quot;.
      * V2_EXT-fråga:
         * bizible2_ext_Ad_Content_FT__c contains Outreach

![](assets/salesforce-package-consolidation-1.png)

* Motsvarande fråga i det konsoliderade paketet:
   * bizible2_Touchpoint_Position__c innehåller FT AND
   * bizible2_Ad_Content__c contains Outreach

![](assets/salesforce-package-consolidation-2.png)

## Vanliga frågor {#faq}

**Kommer det konsoliderade paketet att innehålla konflikter med fält i mitt befintliga paket?**

Du behöver inte avinstallera paketet innan du installerar det konsoliderade paketet. Det finns inga konflikter i fält eftersom de kommer att finnas i ett annat namnutrymme.

**Hur kan jag fylla i data från mina aktuella paket baklänges?**

Du kan registrera en biljett [med support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} för att fylla i och bearbeta BT/BAT-data baklänges och fylla i fält för kontaktpunkts-ID och formulär-ID.

**Kommer fälten i V1- och V2_EXT-paketen att vara tillgängliga i det konsoliderade paketet?**

Ja. Det konsoliderade paketet innehåller samma fält i V1 med ytterligare indelningar efter objekt och V2_EXT-fält via Touchpoint-fält.

**Kan rapporter som använder V2_EXT-fält återskapas i det konsoliderade paketet?**

Ja. Följ stegen i [Nödvändiga åtgärder](#retired-actions) ovan.
