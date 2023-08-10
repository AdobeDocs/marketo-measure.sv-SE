---
unique-page-id: 18874558
description: Boomerang Stages och Touchpoints - [!DNL Marketo Measure] - Produktdokumentation
title: Boomerang Stages och Touchpoints
exl-id: e58169a3-3637-4878-8a0e-1920d873ff52
feature: Boomerang, Touchpoints
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Boomerang Stages och Touchpoints {#boomerang-stages-and-touchpoints}

>[!AVAILABILITY]
>
>Funktionen Boomerang är bara aktiverad för Tier 3-kunder. Om du vill begära en högre kontonivå kontaktar du kontoteamet (din kontoansvarige) på Adobe.

[!DNL Marketo Measure] har släppt vår funktion på Boomerang Stage! Funktionen Boomerang Stage skapades för att ge större insyn i kundresan för [!DNL Marketo Measure] kunder med långa säljcykler. Med den här funktionen kan marknadsförare skapa kontaktytor för alla scenövergångar som inträffar i säljprojektsresan, som när en kontakt-MQL, sedan går över till SAL och sedan återgår till MQL-steget. När kontakter&quot;återgår till MQL-stadiet&quot; eller&quot;omdirigera&quot; anser vi att MQL är ett boomerang-stadium. Funktionen Boomerang Stage fungerar tillsammans med [!DNL Marketo Measure] Anpassade steg.

## Vad den här funktionen gör {#what-this-feature-does}

* Skapar en&quot;boomerang&quot;-kontaktyta för alla scenövergångar som inträffar under en affärsmöjlighets resa
* Spårar upprepade övergångar mellan alla anpassade scener (t.ex. när en kontakt-MQL:er flyttas till SAL och sedan går tillbaka till MQL-steget)
* Gör att du kan ange hur många och vilka scenövergångar du vill inkludera i säljprojektet (t.ex. De första 10 MQL:erna ELLER de sista 5 MQL:erna)
* Om du är en användare av en anpassad modell kan du bestämma den attribueringsvikt och den procentuella kredit som du vill tilldela till var och en av dessa faser (t.ex. ange attribueringsvikt för den första eller sista MQL-förekomsten, eller fördela attribueringsviktningen jämnt mellan alla förekomster)

>[!NOTE]
>
>[Instruktioner för hur du konfigurerar Boomerang Stages](/help/advanced-marketo-measure-features/boomerang/setting-up-boomerang-stages.md).

## Hur Boomerang-scener och kontaktytor ser ut i din CRM {#what-boomerang-stages-and-touchpoints-look-like-in-your-crm}

Utan Boomerang-stadier (före) visas endast den senaste MQL-kontaktpunkten eller den senaste SQL-kontaktytan som är kopplad till en lead-/kontaktpost.

![](assets/1.png)

Med Boomerang-scener och kontaktytor ser du kontaktytor för varje scenövergång. Namnkonventionen för dessa boomerang-kontaktytor blir följande:

**[Scennamn]-00.**

Med exemplet nedan är detta [!DNL Marketo Measure] kontot har inkluderat MQL och SQL i sina boomerang-stadier och har valt att visa 2 boomerang-kontaktytor per scen.

![](assets/2.png)

**MQL-01** är den första MQL-scenövergången.

Det numeriska värdet i kontaktpunktspositionen anger ordningen i vilken scenövergången inträffade. Den sista boomerang-kontaktytan ska stämplas som:

MQL-02 **(Sista)**

## Hur Boomerang-scener ändrar dina befintliga data {#how-boomerang-stages-change-your-existing-data}

Boomerang Stages kommer att påverka

**Attribut per kanal**

* Sedan [!DNL Boomerang Stages] skapar fler kontaktytor, vilket ändrar hur attribueringen fördelas mellan de kontaktytor som för närvarande finns i dina data. Detta kan leda till att intäktsvärdet växlar mellan olika marknadsföringskanaler. Ta detta i beaktande innan du implementerar [!DNL Boomerang stages]eller kontakta din kontoansvarige om du vill ha mer information.

**Alla rapporter som använder &quot;lika med&quot; [Pekpunktsposition]&quot;**

* Boomerang-stadier kommer att ge era data nya kontaktytor. [!DNL Marketo Measure] ändrar formatet för Touchpoint-positionen så att den inkluderar scenens förekomst, som &quot;MQL-01&quot; eller &quot;MQL-05 (sist)&quot;. I det här exemplet kommer Boomerang Stages att påverka alla rapporter som använder&quot;Touchpoint Position is equal to MQL&quot;. För att justera dessa rapporter ska filtret använda operatorn&quot;contains&quot; i stället.

## Vanliga frågor {#faq}

**Hur många boomerang-stadier kan jag inkludera i min attribueringsmodell?**

Du kan välja upp till 15 steg.

**F: Hur många &quot;boomerang&quot;-kontaktytor kan jag ha per scen?**

Du kan välja upp till 10 boomerang-kontaktytor per scen.

**F: Varför begränsas vi bara till 10 boomeranger per fas?**

[!DNL Marketo Measure] måste fastställa en gräns för antalet etapper för att hålla bearbetningstiden under kontroll. Om du väljer att ta med alla 15 Boomerang-scener i din attribueringsmodell och 10 boomerang-kontaktytor per scen, kan du ha fler än 150 kontaktytor per lead-/kontaktpost.

**F: Jag har Data warehouse. Får jag alla data eller gäller boomerang Stages-taket mig också?**

Gränsvärdet kommer att gälla för Data warehouse och CRM på grund av de bearbetningsgränser som [!DNL Marketo Measure] har kommit. Data warehouse kommer också att se gränsen på 10 kontaktytor per etapp.

**F: Vilka är fördelarna med att använda Boomerang Stages med anpassad modellering?**

Använda [!UICONTROL Boomerang] Med hjälp av steg med anpassad modellering kan du tilldela attribueringsviktning till [!UICONTROL Boomerang] kontaktytor som tilldelar intäktskrediter till dessa faser.

Utan anpassad modellering [!DNL Marketo Measure] kommer att skapa kontaktytor för varje boomerang- och scenövergång, men tilldelar inga attribueringskrediter till dessa kontaktytor. De enda boomerang-kontaktytorna som får attribueringskrediter är kontaktytor för att skicka formulär. Utan anpassad modell [!DNL Boomerang] kontaktytor betraktas som&quot;mellanberöring&quot; och får attribueringskrediter i enlighet med detta.
