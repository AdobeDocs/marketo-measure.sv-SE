---
unique-page-id: 18874614
description: Leads med Buyer Touchpoints Report - [!DNL Marketo Measure] - Produktdokumentation
title: Leads med Buyer Touchpoints Report
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---

# Leads med Buyer Touchpoints Report {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men fortfarande se &quot;[!DNL Bizible]&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Nu har du tillgång till många rapporteringsfunktioner när det gäller [!DNL Marketo Measure], men det finns några andra rapporttyper som vi rekommenderar att du skapar. Lär dig hur du skapar inkluderande leads med rapporttypen Buyer Touchpoints nedan.

1. Navigera till ditt inställningsalternativ i [!DNL Salesforce]. Expandera grupperingen&quot;Skapa&quot; och välj **[!UICONTROL Report Types]**.

   ![](assets/1.jpg)

1. Välj **[!UICONTROL New Custom Report Type]**.

   ![](assets/2.jpg)

1. Ange det primära objektet som&quot;Leads&quot; och i indata&quot;Leads with Buyer Touchpoints - Inclusive&quot; i&quot;Report Type Label&quot;. Lagra rapporten i kategorin Leads och ändra distributionsstatusen till **[!UICONTROL Deployed]**. Välj sedan **[!UICONTROL Next]**.

   ![](assets/3.jpg)

1. För objektrelationerna väljer du **[!DNL Marketo Measure]Personer** som det sekundära objektet. Välj relationen A till B som &quot;Varje &#39;A&#39;-post måste ha minst en relaterad &#39;B&#39;-post.&quot; Därifrån relaterar du&quot;Buyer Touchpoint&quot;-objektet och väljer samma relation mellan B- och C-objekten.

   ![](assets/4.jpg)

1. Spara och börja skapa rapporter!
