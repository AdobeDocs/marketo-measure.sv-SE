---
unique-page-id: 18874736
description: Ta bort [!DNL Marketo Measure] Spårningsparametrar från landningssidans URL i Google Analytics - [!DNL Marketo Measure] - Produktdokumentation
title: Ta bort [!DNL Marketo Measure] Spårningsparametrar från landningssidans URL i Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Ta bort [!DNL Marketo Measure] Spårningsparametrar från landningssidans URL i Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

Ibland när du visar landningssidor i [!DNL Google Analytics]ska du ta bort spårningsparametrar från URL-adresserna. Annars delas de upp i enskilda rader.

Som tur är är det här en enkel fix.

1. I [!DNL Google Analytics], gå till [!UICONTROL Admin] >[!UICONTROL View Settings] >[!UICONTROL Exclude URL Query Parameters].
1. Skriv &quot;_bt,_bk,_bm,_bn,_bg&quot; i rutan (minus citattecknen).
1. Rulla ned och klicka **[!UICONTROL Save]**.

   Kom ihåg att [!DNL Google Analytics] bearbetar inte data igen. Ändringen kommer därför endast att speglas om du går framåt, och dina tidigare data kommer fortfarande att visas med parametrarna bt, bk och bm.
