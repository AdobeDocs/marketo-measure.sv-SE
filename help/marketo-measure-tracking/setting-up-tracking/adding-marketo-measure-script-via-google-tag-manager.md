---
unique-page-id: 18874797
description: Lägger till [!DNL Marketo Measure] skript via [!DNL Google Tag Manager] - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] skript via [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] skript via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

När du installerar [!DNL Marketo Measure] JavaScript rekommenderar vi att du [hårdkodar skriptet](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target="_blank"} direkt till platsen. Om det inte är möjligt kan du även använda [!DNL Google Tag Manager] (GTM) för att läsa in JS:en för [!DNL Marketo Measure]. Observera att [!DNL Marketo Measure] JS som läses in via GTM kan fördröjas. Latens orsakar en fördröjning av skriptinläsningstiden, vilket kan leda till att cirka 3-5 % av alla formulärinskickade formulär saknas.

Om du bestämmer dig för att lägga till vårt skript via GTM ska du ställa in [!DNL Marketo Measure]-skriptet till högsta prioritet i den inledande ordningen och se till att det inte finns några synkrona skript framför [!DNL Marketo Measure] -taggen för att minska eventuella effekter från GTM-latens.

>[!NOTE]
>
>Läs den här [supportartikeln från Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target="_blank"} om du vill veta mer.

## Lägga till [!DNL Marketo Measure] JS via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Öppna GTM och lägg till skriptet [!DNL Marketo Measure] i webbplatsbehållaren. Var noga med att välja **[!UICONTROL Custom HTML tag]**.

1. Använd skriptet [!DNL Marketo Measure] nedan och införliva det i behållaren.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Klicka på **[!UICONTROL Add a Firing Rule]** så att du kan ange att Google ska läsa in fragmentet på *Alla sidor*.

1. Gå till avsnittet Översikt över behållarutkast till vänster. Klicka på knappen för att skapa en version av behållaren och publicera ändringarna.
