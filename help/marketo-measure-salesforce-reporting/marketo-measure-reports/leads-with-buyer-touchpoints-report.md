---
description: Leads med Buyer Touchpoints Report - [!DNL Marketo Measure]
title: Leads med Buyer Touchpoints Report
exl-id: 0376abb0-5eed-41bb-ab4f-3c204ab437df
feature: Touchpoints, Reporting
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---


# Leads med Buyer Touchpoints Report {#leads-with-buyer-touchpoints-report}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se [!DNL Bizible] i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När det gäller [!DNL Marketo Measure] har du tillgång till många rapporteringsfunktioner som du kan använda, men det finns ytterligare rapporttyper som vi rekommenderar att du skapar. Lär dig hur du skapar inkluderande leads med rapporttypen Buyer Touchpoints nedan.

1. Navigera till inställningsalternativet i [!DNL Salesforce]. Utöka grupperingen&quot;Skapa&quot; och välj **[!UICONTROL Report Types]**.

   ![Sidan Rapporttyper för Salesforce visar leads med inställningen för Buyer Touchpoints](assets/1.jpg)

1. Välj **[!UICONTROL New Custom Report Type]**.

   ![Guiden Ny anpassad rapporttyp i Salesforce](assets/2.jpg)

1. Ange det primära objektet som&quot;Leads&quot; och i indata&quot;Leads with Buyer Touchpoints - Inclusive&quot; i&quot;Report Type Label&quot;. Lagra rapporten i kategorin Leads och ändra distributionsstatusen till **[!UICONTROL Deployed]**. Välj sedan **[!UICONTROL Next]**.

   ![Rapporttypsinformation med Leads som primärt objekt](assets/3.jpg)

1. För objektrelationerna väljer du objektet **[!DNL Marketo Measure]Personer** som det sekundära objektet. Välj relationen A till B som &quot;Varje &#39;A&#39;-post måste ha minst en relaterad &#39;B&#39;-post.&quot; Därifrån relaterar du&quot;Buyer Touchpoint&quot;-objektet och väljer samma relation mellan B- och C-objekten.

   ![Markering av objektrelation inklusive Marketo Measure-personer och Buyer Touchpoints](assets/4.jpg)

1. Spara och börja skapa rapporter!
