---
unique-page-id: 18874797
description: Lägger till [!DNL Marketo Measure] Skript via [!DNL Google Tag Manager] - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] Skript via [!DNL Google Tag Manager]
exl-id: 539efb10-35cb-4146-8eea-728c3948a11e
source-git-commit: 82cc8269bfdb26b6acf039d0ce0e06564f5e2612
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] Skript via [!DNL Google Tag Manager] {#adding-marketo-measure-script-via-google-tag-manager}

När du installerar [!DNL Marketo Measure] javascript, vi rekommenderar starkt [hårdkoda skriptet](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md){target=&quot;_blank&quot;} direkt till din plats. Om det inte är möjligt kan du även använda [!DNL Google Tag Manager] (GTM) för att läsa in [!DNL Marketo Measure] JS. Observera att [!DNL Marketo Measure] JS som läses in via GTM är känsligt för fördröjning. Latens orsakar en fördröjning av skriptinläsningstiden, vilket kan leda till att cirka 3-5 % av alla formulärinskickade formulär saknas.

Om du lägger till vårt skript via GTM, vänligen ange [!DNL Marketo Measure] skript med högsta prioritet i din startordning och se till att det inte finns några synkrona skript framför [!DNL Marketo Measure] för att minska eventuella effekter från GTM-fördröjning.

>[!NOTE]
>
>Använd den här [supportartikel av Google](https://support.google.com/tagmanager/answer/2772421?hl=en){target=&quot;_blank&quot;} om du vill veta mer.

## Lägga till [!DNL Marketo Measure] JS via [!DNL Google Tag Manager] {#how-to-add-marketo-measure-js-via-google-tag-manager}

1. Öppna GTM och lägg till [!DNL Marketo Measure] skript i webbplatsbehållaren. Se till att du väljer **[!UICONTROL Custom HTML tag]**.

1. Använd [!DNL Marketo Measure] nedan och lägg in det i behållaren.

   `<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

1. Klicka **[!UICONTROL Add a Firing Rule]** så att du kan ange att Google ska läsa in fragmentet *Alla sidor*.

1. Gå till avsnittet Översikt över behållarutkast till vänster. Klicka på knappen för att skapa en ny version av behållaren och publicera ändringarna.