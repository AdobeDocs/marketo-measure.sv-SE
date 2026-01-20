---
unique-page-id: 18874753
description: Lägger till [!DNL Marketo Measure] i Active-On Forms - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] i Active-On Forms
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] i Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Riktningar {#directions}

1. Välj alternativet **[!UICONTROL Settings]** i det högra hörnet i det formulär som du redigerar.
1. Leta efter ett område med etiketten [!UICONTROL "External Web Analytics."] Det är här du släpper [!DNL Marketo Measure]-spårningskodfragmentet.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Det kan redan finnas andra spårningskod i det här området, till exempel en [!DNL Google Analytics]-kod. Se till att separera dem med ett semikolon `;` och ett enda mellanslag, som:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
