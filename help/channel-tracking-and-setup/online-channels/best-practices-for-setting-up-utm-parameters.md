---
unique-page-id: 18874732
description: Bästa metoder för att konfigurera UTM-parametrar - [!DNL Marketo Measure] - Produktdokumentation
title: Metodtips för att konfigurera UTM-parametrar
exl-id: 56019f41-b6ba-48c1-9bef-2a5f56d2d5f4
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# Metodtips för att konfigurera UTM-parametrar {#best-practices-for-setting-up-utm-parameters}

UTM-parametrar är ett bra sätt att segmentera och minska era marknadsföringsdata. [!DNL Marketo Measure] använder och hämtar alla UTM-parametrar för att fylla i fält i Salesforce och i [!DNL Marketo Measure] app. Med den här informationen får du en detaljerad förståelse för var era leads, affärsmöjligheter och avslutade/vunna avtal kommer ifrån.

Du kan använda [Google URL Builder](https://support.google.com/analytics/answer/1033867?hl=en){target=&quot;_blank&quot;} för att konfigurera UTM-parametrarna och lägga till dem i länkarna i marknadsföringsarbetet. Använd den här [Google kalkylblad](https://docs.google.com/spreadsheets/d/1QCIr1WUJQHE68cA4VTks2XE7nxuryaUymCEy_23-Oew/edit#gid=0){target=&quot;_blank&quot;} om du vill ha ett enklare sätt att hålla reda på alla UTM-länkar.

## Värden på hög nivå för varje parameter {#high-level-values-for-each-parameter}

**utm_medium**: Det här fältet mappas till fältet Medel. Använd utm_medium för att beteckna högnivåkanalen.

t.ex.: [!UICONTROL Social], CPC, e-post, webb, organisk

Använd inte det här fältet för att anropa underkanalen.

**utm_source**: Det här fältet mappar till fältet Källa för pekpunkt. Använd utm_source för att definiera den delkanal som leadet kommer från.

t.ex.: Facebook, Twitter, Linkedin, Drip_email, Email_blast, nyhetsbrev.

Gör det enkelt. Använd inte den här parametern för att ange annonstyp, som återannonsering, sponsring osv. Lägg inte till utm_source = hemsida, webdirect, webbplats. [!DNL Marketo Measure] fyller i informationen automatiskt.

**utm_campaign**: Det här fältet mappar till annonskampanjens namn. Använd utm_campaign för att ange kampanjens titel så som den finns i annonsplattformen, eller så som den hänvisas till internt.

Det här är också en bra parameter för att beteckna Geolocation, Ad-nätverkstyp (display v. search) osv.

Vi rekommenderar att du använder understreck i stället för mellanslag och undviker att använda interpunktion. Detta minskar risken för kodningsfel i webbläsare när du läser parametrar.

t.ex.: AU_Idea_for_an_App_50k

**utm_content**: Detta mappas till annonsinnehåll. Använd annonstiteln i parametern utm_content. Om det är en bildannons använder du annonsrubriken och inkluderar annonsdimensionerna.

t.ex.: [annonsrubrik] 200x400px

**utm_term**: Detta mappas till Nyckelordstext. Använd den här parametern för att ange nyckelordet som är relaterat till annonsens bränning.

Om det inte finns något nyckelord relaterat till annonsen lämnar du den här parametern tom.

t.ex.: iPhone App Ideas

**Gör det enkelt och koncist. Duplicera inte ansträngningar, termer och kanaler.**

Vi tror att UTM-hierarkin ser ut så här:

Medel > [!UICONTROL Source] > [!UICONTROL Campaign] > [!UICONTROL Content/Term]

t.ex.: Om en [!UICONTROL display] och som finns på Facebook rekommenderar vi följande:

fakewebsite.com/

?utm_medium=social

&amp;utm_source=facebook

&amp;utm_campaign=Display_campaign_ID

&amp;utm_content=content_of_campaign

Observera att termer/kanal inte dupliceras och utm_term används inte i det här fallet.

Om du har några frågor kan du kontakta din Customer Success Manager eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.