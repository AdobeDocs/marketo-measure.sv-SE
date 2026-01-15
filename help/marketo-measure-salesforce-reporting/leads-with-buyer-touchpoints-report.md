---
description: Leads med Buyer Touchpoints Report guidelines for Marketo Measure users
title: Leads med Buyer Touchpoints Report
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 2%

---

# Leads med Buyer Touchpoints Report {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se [!DNL Bizible] i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När det gäller [!DNL Marketo Measure] har du tillgång till många rapporteringsfunktioner som du kan använda, men det finns ytterligare rapporttyper som vi rekommenderar att du skapar. Lär dig hur du skapar inkluderande leads med rapporttypen Buyer Touchpoints nedan.

1. Navigera till inställningsalternativet i [!DNL Salesforce]. Utöka grupperingen&quot;Skapa&quot; och välj **[!UICONTROL Report Types]**.

   ![1. Navigera till inställningsalternativet i Salesforce. Expandera](assets/bizible-guide-1.png) därifrån

1. Välj **[!UICONTROL New Custom Report Type]**.

   ![1. Välj Ny anpassad rapporttyp.](assets/marketo-reports-17.jpg)

1. Ange det primära objektet som&quot;Leads&quot; och i indata&quot;Leads with Buyer Touchpoints - Inclusive&quot; i&quot;Report Type Label&quot;. Lagra rapporten i kategorin Leads och ändra distributionsstatusen till **[!UICONTROL Deployed]**. Välj sedan **[!UICONTROL Next]**.

   ![1. Ange det primära objektet som Leads och inom rapporttypen &#x200B;](assets/marketo-reports-18.jpg)

1. För objektrelationerna väljer du objektet **[!DNL Marketo Measure]Personer** som det sekundära objektet. Välj relationen A till B som &quot;Varje &#39;A&#39;-post måste ha minst en relaterad &#39;B&#39;-post.&quot; Därifrån relaterar du&quot;Buyer Touchpoint&quot;-objektet och väljer samma relation mellan B- och C-objekten.

   ![1. För objektrelationerna väljer du Marketo Measure People-objektet &#x200B;](assets/bizible-guide-2.png)

1. Spara och börja skapa rapporter!
