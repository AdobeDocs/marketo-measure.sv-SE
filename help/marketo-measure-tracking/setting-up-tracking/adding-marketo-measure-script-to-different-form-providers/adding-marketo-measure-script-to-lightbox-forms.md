---
unique-page-id: 18874519
description: Lägger till [!DNL Marketo Measure] Skript till ljuslåda Forms - [!DNL Marketo Measure] - Produktdokumentation
title: Lägger till [!DNL Marketo Measure] Skript till Lightroom Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] Skript till Lightroom Forms {#adding-marketo-measure-script-to-lightbox-forms}

Lär dig hur du lägger till [!DNL Marketo Measure] JavaScript till ett formulär i en ljuslåda.

En ljuslåda öppnar ett formulär framför innehållet när besökaren utför en viss åtgärd (t.ex. klickar på en viss del av sidan, tillbringar en viss tid på sidan osv.). Vanligtvis ber vi bara att få [!DNL Marketo Measure] JavaScript placerat i huvudet på landningssidan, men för formulär i en ljuslåda behövs ett extra steg.

Eftersom ett formulär i en ljuslåda i stort sett är ett formulär i en iFrame måste vi ha skriptet placerat i den iFrame.

Först letar du reda på iFrame i [!UICONTROL lightbox] formaten lever i.

![](assets/1.png)

Placera sedan [!DNL Marketo Measure] JavaScript i iFrame.

![](assets/2.png)

När JavaScript läggs till rekommenderar vi att du kontrollerar formulärinskickade formulär enligt följande:

1. Kopiera URL-adressen till landningssidan med [!UICONTROL lightbox] formulär.
1. Öppna en Incognito-webbläsare och klistra in URL:en.
1. Skicka formuläret med en unik e-postadress.
1. Bekräfta att testet spårades genom att kontrollera CRM för den unika e-postadressen som användes, kontrollera att data från kontaktpunkten fylls i.
