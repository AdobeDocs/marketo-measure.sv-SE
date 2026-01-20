---
unique-page-id: 18874519
description: Lägger till [!DNL Marketo Measure] skript i ljuslådan Forms - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] skript i ljuslådan Forms
exl-id: fa9ce480-fc4f-4abd-8555-dbb74849747e
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] skript i ljuslådan Forms {#adding-marketo-measure-script-to-lightbox-forms}

Lär dig hur du lägger till JavaScript [!DNL Marketo Measure] i ett formulär i en ljuslåda.

En ljuslåda öppnar ett formulär framför innehållet när besökaren utför en viss åtgärd (det vill säga klickar på en viss del av sidan, tillbringar en viss tid på sidan och så vidare). Vanligtvis ber vi att få JavaScript [!DNL Marketo Measure] placerad i huvudet på landningssidan, men för formulär i en ljuslåda behövs ett extra steg.

Eftersom ett formulär i en ljuslåda i stort sett är ett formulär i en iFrame placeras skriptet inuti den iFrame.

Först letar du reda på iFrame som formuläret [!UICONTROL lightbox] finns i.

![](assets/1.png)

Placera sedan [!DNL Marketo Measure] JavaScript i iFrame.

![](assets/2.png)

När JavaScript har lagts till spåras formulärinskickat material enligt följande:

1. Kopiera URL-adressen till landningssidan som innehåller formuläret [!UICONTROL lightbox].
1. Öppna en Incognito-webbläsare och klistra in URL:en.
1. Skicka formuläret med en unik e-postadress.
1. Bekräfta att testet spårades genom att kontrollera CRM för den unika e-postadressen som används och kontrollera att data från slutpunkten fylls i.
