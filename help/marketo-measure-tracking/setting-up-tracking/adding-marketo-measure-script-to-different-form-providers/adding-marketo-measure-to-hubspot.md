---
unique-page-id: 18874759
description: Lägger till [!DNL Marketo Measure] till [!DNL Hubspot] - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] till [!DNL Hubspot]
exl-id: 633e7ef7-7959-461e-881f-dcc543595b66
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] till [!DNL Hubspot] {#adding-marketo-measure-to-hubspot}

Lär dig hur du lägger till [!DNL Marketo Measure] JavaScript för att spåra [!DNL Hubspot] landningssidor och inskickade formulär.

Hubspot skiljer sig något från andra automatiserade marknadsföringssystem genom att den kan hantera dina landningssidor/formulär OCH din webbplats. Det är viktigt att notera att instruktionerna nedan gäller [!DNL Marketo Measure] spåra aktivitet på [!DNL Hubspot]webbsidor. Om du ger din webbplats ett annat CMS-system än [!DNL Hubspot] (till exempel Wordpress) måste du lägga till [!DNL Marketo Measure] JavaScript-skript till CMS-systemet också.

>[!NOTE]
>
>Om du distribuerar JavaScript via en tagghanteringsleverantör som [!DNL Google Tag Manager]behöver du inte hårdkoda [!DNL Marketo Measure] JavaScript på din webbplats.

## Komma igång {#getting-started}

När du har loggat in på [!DNL Hubspot] gör så här:

1. Navigera till Innehåll.

1. Klicka på **[!UICONTROL Content Settings]**.

1. Inom [!UICONTROL Content Settings]klickar du på HTML för webbplatshuvudet (se bilden nedan).

1. Lägg till följande skript i `<header>`:

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

   Det borde se ut så här:

```text
<!-- Marketo Measure Javascript -->
<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="">
```

>[!TIP]
>
>Det kan redan finnas andra kodfragment för spårning i det här området, till exempel en Google Analytics-kod. Var noga med att separera dem med ett semikolon `;` och ett enda blanksteg:
>
>`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>; <script async="true" type="someothercode" src="someotherfile.js" ></script>`
