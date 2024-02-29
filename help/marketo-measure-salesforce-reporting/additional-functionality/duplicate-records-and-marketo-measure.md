---
unique-page-id: 18874572
description: Duplicera poster och [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Duplicera poster och [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Duplicera poster och [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

[!DNL Marketo Measure] använder e-postadressen som vår unika identifierare när data matchas mot en relaterad lead eller kontakt i CRM. När [!DNL Marketo Measure] hittar flera leads eller kontakter med samma e-postadress, så kommer vi att visa samma data på alla poster. Effekten av detta uppstår när du rapporterar om leads eller kontakter med [!DNL Marketo Measure] och på ett felaktigt sätt kan öka mängden unika personer som har Buyer Touchpoints.

Hur ser det här ut i [!DNL Marketo Measure] Rapportera?

_Exempel: [!DNL Marketo Measure] Personer med Buyer Touchpoints._

![](assets/1-1.png)

Du kan se [!DNL Marketo Measure] Person-ID för kelsey@adobe.com att det finns både en lead och en kontakt med den e-postadressen. I den här rapporten rapporteras 2 First Touches, 2 Lead Creation Touches och 2 PostLC-interaktion. Dessa dubblettposter har samma kontaktpunktsdatum och kontaktpunktsinformation, vilket kan leda till slutsatsen att de är två olika personer trots att de är samma person.

**Rekommendation**

* För att maximera avkastningen i dina rapporter rekommenderar vi att du använder ett dedupliceringsverktyg i CRM för att vara säker på att du bara skapar nya nettoposter. Detta kan göras med verktyget för marknadsföringsautomatisering eller med en separat programvara som är installerad i CRM. [!DNL Marketo Measure] skriver inte ut poster automatiskt och erbjuder inte den här tjänsten via vår programvara.
* Ett annat alternativ är att manuellt sammanfoga poster när du identifierar dubbletter. Denna process kan vara tidskrävande och tidskrävande, men resultatet av en korrekt rapportering är värt tidsinvesteringen.
