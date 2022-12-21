---
unique-page-id: 18874755
description: Lägger till [!DNL Marketo Measure] till [!DNL Marketo] Landningssidor - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] till Marketo landningssidor
exl-id: 3771d4d2-8723-452a-b23d-cea3b11ab9ee
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] till Marketo landningssidor {#adding-marketo-measure-to-marketo-landing-pages}

Lär dig hur du lägger till spårning i [!DNL Marketo Engage] Landningssidor när de kräver ytterligare hantering. [!DNL Marketo Measure] JavaScript måste finnas på plats både på landningssidan och på [!DNL Marketo Engage] själva. Om du vill göra det måste du läsa in [!DNL Marketo Measure] JavaScript till [!DNL Marketo Engage] enligt följande anvisningar.

>[!NOTE]
>
>Om du distribuerar JavaScript via en tagghanteringsleverantör som [!DNL Google Tag Manager]behöver du inte lägga till manuellt [!DNL Marketo Measure] JS till [!DNL Marketo Engage].

## Så här lägger du till [!DNL Marketo Measure] Skript till [!DNL Marketo Engage] Landningssidor {#how-to-add-marketo-measure-script-to-marketo-engage-landing-pages}

1. Logga in på [!DNL Marketo Engage] konto.
1. Välj landningssida och klicka på **[!UICONTROL Edit Draft]**.
1. Dra i elementet HTML.
1. Ange [!DNL Marketo Measure] JavaScript i [!UICONTROL head] avsnitt:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Exempel i skärmbild nedan

1. Klicka på **[!UICONTROL Save]**.

   ![](assets/adding-bizible-to-marketo-landing-pages-1.png)

## Ytterligare information {#additional-notes}

* Du kanske redan har andra spårningskodfragment på plats, till exempel en [!DNL Google Analytics] kod. Det finns inga problem med detta, se till att separera dem med ett semikolon `;` och ett enda utrymme. Ett exempel på hur detta skulle se ut är:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`

* Det är troligt att du använder flera mallsidor för landningssidor. Se till att du lägger till koden i alla mallar som har formulär.

* Ibland när du redigerar mallen för landningssidor måste du godkänna de sidor som landningssidan används av på nytt. Den här artikeln förklarar [massgodkänna](https://experienceleague.adobe.com/docs/marketo/using/product-docs/demand-generation/landing-pages/landing-page-actions/approve-multiple-landing-pages-at-once.html){target=&quot;_blank&quot;}.
