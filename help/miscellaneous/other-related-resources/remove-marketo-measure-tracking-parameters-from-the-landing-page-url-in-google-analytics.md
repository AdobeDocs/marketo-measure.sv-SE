---
unique-page-id: 18874736
description: Ta bort [!DNL Marketo Measure] spårningsparametrar från landningssidans URL i Google Analytics - [!DNL Marketo Measure]
title: Ta bort  [!DNL Marketo Measure] spårningsparametrar från landningssidans URL i Google Analytics
exl-id: ec81ba4a-bb10-49fd-b62e-5a1bc9e1a023
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Ta bort [!DNL Marketo Measure] spårningsparametrar från landningssidans URL i Google Analytics {#remove-marketo-measure-tracking-parameters-from-the-landing-page-url-in-google-analytics}

När du visar landningssidor i [!DNL Google Analytics] kanske du vill ta bort spårningsparametrar från URL-adresserna. Annars delas de upp i enskilda rader.

Som tur är är det här en enkel fix.

1. Gå till [!DNL Google Analytics] >[!UICONTROL Admin] >[!UICONTROL View Settings] i [!UICONTROL Exclude URL Query Parameters].
1. Skriv &quot;_bt,_bk,_bm,_bn,_bg&quot; i rutan (minus citattecknen).
1. Rulla ned och klicka på **[!UICONTROL Save]**.

   Tänk på att [!DNL Google Analytics] inte bearbetar om data. Ändringen kommer därför endast att speglas om du går framåt, och dina tidigare data kommer fortfarande att visas med parametrarna bt, bk och bm.
