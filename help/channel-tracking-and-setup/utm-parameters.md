---
description: UTM-parametervägledning för Marketo Measure-användare
title: UTM-parametrar
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
feature: UTM Parameters
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---

# UTM-parametrar {#utm-parameters}

Att tagga URL:er är ett enkelt och effektivt sätt att samla in data om era digitala marknadsföringssatsningar. Det är processen att lägga till parametrar i slutet av URL:er som samlar in och registrerar data. De vanligaste parametrarna är UTM-moduler (Urchin Tracking Modules), som stöds av Google. Det finns fem huvudsakliga UTM-parametrar: Medium, Source, Campaign, Content och Term. Dessa diskuteras mer ingående i nästa avsnitt.

UTM-parametrar kan läggas till manuellt i URL-adresser eller läggas till via automatisk taggning med vissa plattformar, till exempel AdWords . Automatisk taggning automatiserar processen att lägga till parametrar till URL-adresser. Det finns också ett alternativ för [URL-byggare](https://ga-dev-tools.web.app/campaign-url-builder/){target="_blank"} som kan göra att URL-taggningar kan snabbas upp manuellt. Med ett URL-verktyg anger du bara vilka värden som ska användas för varje parameter så formaterar verktyget URL:en åt dig.

## Vad är UTM-parametrar? {#what-are-utm-parameters}

För att förstå hur UTM-parametrar fungerar ska vi titta på en vanlig URL utan UTM:

`http://www.adobe.com`

Nu ska vi kolla in en URL med UTM:

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Den andra länken innehåller mer text. UTM-parametrar följer alltid den översta domänen (.com i det här exemplet) och börjar med ett frågetecken. Därefter spelar parametrarnas ordning ingen roll, men du bör följa en konsekvent namnkonvention. Expanderingar måste placeras mellan varje parameter för att varje UTM ska separeras. Nu kan vi gå in på mer detaljerad information om vad varje parameter representerar.

Lär dig mer om [de bästa sätten att konfigurera UTM-parametrar](/help/channel-tracking-and-setup/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Medium identifierar de fordon som du använder för att marknadsföra ditt företag.
* Det besvarar frågan:&quot;Hur kommer de åt dig?&quot;
* Det betecknar kanalen på den högsta nivån.
* Sociala medier, e-post, organisk sökning och betalsökning är alla exempel på potentiella Medium-värden.
* Den här parametern mappar data till fältet [!DNL Marketo Measure] &quot;Medium&quot;.
* _[!DNL Marketo Measure] Bästa praxis :_Använd inte det här fältet för att anropa en underkanal, annars kan du få problem med att generera rapporter på den faktiska kanalen. Använd det för att identifiera ert marknadsföringsfordon eller er marknadsföringskanal. Om du till exempel vill använda e-post för att marknadsföra produkten är mediet e-post.

**utm_source**

* Source identifierar den underkanal som är trafikens källa.
* Det besvarar frågan: &quot;Var kommer den här personen ifrån?&quot;
* I ett exempel på sociala medier är trafikkällan den plattform för sociala medier som används.
   * I det här exemplet är [!DNL Facebook] Source Value. Andra exempel är Twitter och Instagram. Om UTM Medium är [!DNL Paid Search] kan UTM Source däremot vara AdWords eller BingAds.

* Den här parametern mappas till [!DNL Marketo Measure] Touchpoint Source i SFDC.
* _[!DNL Marketo Measure] Bästa praxis :_Den här parametern spårar trafikens källa, så det är inte lämpligt att använda den för att ange annonstypen, till exempel återmarknadsföring, sponsring osv. Den används bäst för att spåra underkanalen på högre nivå. Kom ihåg, du svarar på frågan &quot;varifrån kommer min trafik?&quot; Du letar efter referenten. I det här exemplet är UTM Source den plats där annonsen finns (inte den faktiska webbsidan, eftersom den automatiskt spåras utanför taggarna). Om du håller på att spåra en drop-email-kampanj är drop-e-post källan.

**utm_campaign**

* Campaign används för att identifiera en viss marknadsföringskampanj.
* Det besvarar frågan:&quot;Varför kommer de till dig?&quot;
* Använd den här taggen för att ange namnet på annonskampanjen så som den finns i [!DNL Google AdWords] eller [!DNL BingAds], eller för att ange namnet som du identifierar kampanjen med internt. Du kan till och med använda den här taggen för att ange annan information som geopositionering eller annonsnätverkstyp.
* Den här parametern mappar till fältet [!DNL Marketo Measure]&quot;Ad Campaign Name&quot; i SFDC.
* _[!DNL Marketo Measure]Bästa praxis_: Undvik att använda skiljetecken eller tomma mellanslag mellan orden när kampanjnamnen bestäms, eftersom det kan leda till webbläsarkodningsfel om de används. För bästa resultat bör du använda understreck i stället.

**utm_content**

* Använd parametern UTM Content när du vill spåra mer än en marknadsföringsbit som finns på en enda webbsida. Om du till exempel har knappen &quot;Begär en demo&quot; och knappen &quot;Registrera dig för vårt veckonyhetsbrev&quot; och vill veta vilken som genererar mest trafik, skulle du namnge var och en och använda en UTM-innehållstagg för att spåra dem. Namnet på varje del av &quot;innehåll&quot; är taggens värde.
* Den här parametern mappar till fältet [!DNL Marketo Measure] &#39;Ad Content&#39; i SFDC.
* _[!DNL Marketo Measure]Best Practice_: Detta är ett valfritt värde, men [!DNL Marketo Measure] rekommenderar att du använder det. Den här taggen är associerad med titeln på den annons eller det marknadsföringsmaterial som du vill spåra. Om du använder en bildannons måste du skriva bildens dimensioner i dess titel.

**utm_term**

* Termen liknar parametern UTM Content. Termen är bra för att identifiera nyckelord i annonser för betalda kampanjer. Om du använder funktionen för automatisk taggning gör du detta åt dig. Om du inte använder annonsplattformens funktion för automatisk taggning ska du lägga till alla nyckelord du vill spåra noggrant.
* Den här parametern mappar till fältet [!DNL Marketo Measure] Nyckelordstext i SFDC.
* _[!DNL Marketo Measure]Bästa praxis_: UTM-termtaggen är valfri men bra för att spåra nyckelord. Dubbelkontrollera stavningen och undvik att använda specialtecken. Om mer än ett ord behövs kan du försöka med att använda understreck eller inga mellanslag alls.

Varje parameter samlar in information som är relevant för det tilldelade värdet. Värdet för varje tagg gör att ni kan spåra och sortera alla era digitala kampanjer och besvara frågorna: var, hur och varför?

Här följer ett diagram över UTM-parametrarna [!DNL Marketo Measure] och motsvarande Touchpoint-fält som de är kopplade till:

| **UTM-parameter** | **Motsvarande [!DNL Marketo Measure]-fält** |
|---|---|
| utm_medium | Medium |
| utm_source | Touchpoint Source |
| utm_campaign | Namn på annonskampanj |
| utm_content | Annonsinnehåll |
| utm_term | Nyckelord |
