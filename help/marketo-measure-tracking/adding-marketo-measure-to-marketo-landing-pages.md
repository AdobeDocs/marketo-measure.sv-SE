---
description: Lägga till  [!DNL Marketo Measure] i Marketo landningssidans vägledning för Marketo Measure-användare
title: Lägger till  [!DNL Marketo Measure] till Marketo landningssidor
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
feature: Tracking
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] på Marketo landningssidor {#adding-marketo-measure-to-marketo-landing-pages}

Lär dig hur du lägger till spårning på [!DNL Marketo Engage] landningssidor när de behöver ytterligare hantering. [!DNL Marketo Measure] JavaScript måste finnas på plats både på landningssidan och i själva formuläret [!DNL Marketo Engage]. För att göra detta måste du läsa in [!DNL Marketo Measure] JavaScript till [!DNL Marketo Engage] enligt anvisningarna nedan.

>[!NOTE]
>
>Om du distribuerar JavaScript via en tagghanteringsleverantör som [!DNL Google Tag Manager] behöver du inte lägga till [!DNL Marketo Measure] JS manuellt i [!DNL Marketo Engage].

## Lägga till [!DNL Marketo Measure] skript på [!DNL Marketo Engage] landningssidor {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Logga in på ditt [!DNL Marketo Engage]-konto.
1. Välj din landningssida och klicka på **[!UICONTROL Edit Draft]**.
1. Dra i HTML-elementet.
1. Ange [!DNL Marketo Measure] JavaScript i avsnittet [!UICONTROL head]:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exempel i skärmbild nedan

1. Klicka på **[!UICONTROL Save]**.

   ![1. Klicka på Spara.](assets/adding-pages-1.png)

## Ytterligare information {#additional-notes}

* Du kanske redan har andra spårningskodfragment på plats, till exempel en [!DNL Google Analytics]-kod. Det finns inget problem med detta. Se till att separera dem med ett semikolon `;` och ett enda mellanslag. Ett exempel på hur detta skulle se ut är:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Det är troligt att du använder flera mallsidor för landningssidor. Se till att du lägger till koden i alla mallar som har formulär.

* Ibland när du redigerar mallen för landningssidor måste du omgodkänna de sidor som landningssidan används av. I den här artikeln förklaras [hur du masserar godkännande](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html?lang=sv-SE){target="_blank"}.
