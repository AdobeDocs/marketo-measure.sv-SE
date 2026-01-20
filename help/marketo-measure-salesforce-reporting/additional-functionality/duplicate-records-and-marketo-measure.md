---
unique-page-id: 18874572
description: Duplicera poster och [!DNL Marketo Measure] - [!DNL Marketo Measure]
title: Duplicera poster och [!DNL Marketo Measure]
exl-id: e340100c-120a-4771-946d-336a1458da4e
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Duplicera poster och [!DNL Marketo Measure] {#duplicate-records-and-marketo-measure}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

[!DNL Marketo Measure] använder e-postadressen som en unik identifierare när data matchas mot en relaterad lead eller kontakt i CRM. När [!DNL Marketo Measure] hittar flera leads eller kontakter med samma e-postadress, visas samma data på alla poster. Effekten av detta uppstår när du rapporterar om leads eller kontakter med [!DNL Marketo Measure] och kan felaktigt öka antalet unika personer som har Buyer Touchpoints.

Hur ser det här ut i [!DNL Marketo Measure]-rapportering?

_Exempelrapport: [!DNL Marketo Measure] Personer med Buyer Touchpoints._

![](assets/1-1.png)

För person-ID:t [!DNL Marketo Measure] på kelsey@adobe.com kan du se att det finns både en lead och en kontakt med den e-postadressen. I den här rapporten rapporteras 2 First Touches, två Touches för leadskapande och två PostLC-interaktioner. Dessa dubblettposter delar information om kontaktpunkter och kontaktpunkter, vilket kan leda till slutsatsen att de är två olika personer trots att de är samma person.

**Rekommendation**

* För att maximera avkastningen i dina rapporter rekommenderar vi att du använder ett dedupliceringsverktyg i CRM för att vara säker på att du bara skapar nya, unika poster. Detta kan göras med verktyget för marknadsföringsautomatisering eller med en separat programvara som är installerad i CRM. [!DNL Marketo Measure] tar inte bort poster automatiskt och erbjuder inte den här tjänsten via vår programvara.
* Ett annat alternativ är att manuellt sammanfoga poster när du identifierar dubbletter. Denna process kan vara tidskrävande och tidskrävande, men resultatet av en korrekt rapportering är värt tidsinvesteringen.
