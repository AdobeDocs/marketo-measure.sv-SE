---
unique-page-id: 18874732
description: Bästa tillvägagångssätt för att konfigurera UTM-parametrar - [!DNL Marketo Measure]
title: Metodtips för att konfigurera UTM-parametrar
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
feature: UTM Parameters
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Metodtips för att konfigurera UTM-parametrar {#best-practices-for-setting-up-utm-parameters}

UTM-parametrar är ett bra sätt att segmentera och minska era marknadsföringsdata. [!DNL Marketo Measure] använder och hämtar alla UTM-parametrar för att fylla i fält i Salesforce och i appen [!DNL Marketo Measure]. Med den här informationen kan du få en detaljerad förståelse för var era leads, affärsmöjligheter och avslutade/vunna avtal kommer ifrån.

Du kan använda [Google URL Builder](https://support.google.com/analytics/answer/1033867?hl=en){target="_blank"} för att konfigurera UTM-parametrar och lägga till dem i länkarna i dina marknadsföringssatsningar. Använd det här [Google-kalkylbladet](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target="_blank"} om du vill ha ett enklare sätt att spåra alla UTM-länkar.

## Högnivåvärden för varje parameter {#high-level-values-for-each-parameter}

**utm_medium**: Det här fältet mappar till fältet Medium. Använd utm_medium för att ange kanal på hög nivå.

Till exempel [!UICONTROL Social], CPC, e-post, webb, organisk

Använd inte det här fältet för att anropa underkanalen.

**utm_source**: Det här fältet mappar till Source-fältet för slutpunkt. Använd utm_source för att definiera den delkanal som leadet kommer från.

Exempel: Facebook, Twitter, Linkedin, Drip_email, Email_blast, newsletter.

Gör det enkelt. Använd inte den här parametern för att beteckna annonstyper, som återannonsering eller sponsring. Lägg inte till utm_source = hemsida, webdirect, webbplats. [!DNL Marketo Measure] fyller automatiskt i den här informationen åt dig.

**utm_campaign**: Det här fältet mappar till annonskampanjens namn. Använd utm_campaign för att ange kampanjens titel så som den finns i annonsplattformen, eller så som den hänvisas till internt.

Det här är också en bra parameter för att beteckna Geolocation, Ad-nätverkstyp (display v. search) osv.

Du bör använda understreck i stället för mellanslag och undvika att använda interpunktion. Detta minskar risken för kodningsfel i webbläsare när du läser parametrar.

Exempel: AU_Idea_for_an_App_50k

**utm_content**: Detta mappar till annonsinnehåll. Använd annonstiteln i parametern utm_content. Om det är en bildannons använder du annonsrubriken och inkluderar annonsdimensionerna.

Exempel: [annonsrubrik] 200x400px

**utm_term**: Detta mappar till nyckelordstext. Använd den här parametern för att ange nyckelordet som är relaterat till annonsens bränning.

Om det inte finns något nyckelord relaterat till annonsen lämnar du den här parametern tom.

Exempel: iPhone App Ideas

**Håll det enkelt och koncist. Duplicera inte ansträngningar, termer och kanaler.**

Vi tror att UTM-hierarkin ser ut så här:

Medium > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

Om en [!UICONTROL display]-annons till exempel placeras på Facebook rekommenderar vi följande:

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Observera att termer/kanal inte dupliceras och utm_term används inte i det här fallet.

Om du har frågor kan du kontakta Adobe Account Team (din kontohanterare) eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
