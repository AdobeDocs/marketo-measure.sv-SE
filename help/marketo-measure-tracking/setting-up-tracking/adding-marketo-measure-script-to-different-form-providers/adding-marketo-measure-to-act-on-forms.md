---
unique-page-id: 18874753
description: Lägger till [!DNL Marketo Measure] till Act-On Forms - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] till Act-On Forms
exl-id: 3d246e6a-ad3b-4683-b2b7-ab3f0f4c5ab2
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] till Act-On Forms {#adding-marketo-measure-to-act-on-forms}

## Riktningar {#directions}

1. I det formulär som du redigerar väljer du **[!UICONTROL Settings]** i det högra hörnet.
1. Leta efter ett område med etiketten [!UICONTROL "External Web Analytics."] Här släpper du [!DNL Marketo Measure] spåra kodfragment.

## [!DNL Marketo Measure] JavaScript {#marketo-measure-javascript}

`script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

>[!NOTE]
>
>Det kan redan finnas andra kodfragment för spårning i det här området, som [!DNL Google Analytics] kod. Var noga med att separera dem med ett semikolon `;` och ett enda blanksteg:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>**; **<script async="true" type="someothercode" src="someotherfile.js" ></script>`
