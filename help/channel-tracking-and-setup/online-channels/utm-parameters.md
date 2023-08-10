---
unique-page-id: 18874606
description: UTM-parametrar - [!DNL Marketo Measure] - Produktdokumentation
title: UTM-parametrar
exl-id: 2b20f3c4-1f39-4ac5-bad1-cb1d630d60e9
feature: UTM Parameters
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# UTM-parametrar {#utm-parameters}

Att tagga URL:er är ett enkelt och effektivt sätt att samla in data om era digitala marknadsföringssatsningar. Det är processen att lägga till parametrar i slutet av URL:er som samlar in och registrerar data. De vanligaste parametrarna är UTM-moduler (Urchin Tracking Modules), som stöds av Google. Det finns fem huvudsakliga UTM-parametrar: Medium, Källa, Campaign, Innehåll och Term. Dessa diskuteras mer ingående i nästa avsnitt.

UTM-parametrar kan läggas till manuellt i URL-adresser eller läggas till via automatisk taggning med vissa plattformar, till exempel AdWords. Automatisk taggning automatiserar processen att lägga till parametrar till URL-adresser. Det finns också möjlighet att [URL-verktyg](https://ga-dev-tools.appspot.com/campaign-url-builder/){target="_blank"} om du vill att taggar URL-adresser ska gå snabbare manuellt. Med ett URL-verktyg behöver du bara ange vilka värden som ska användas för varje parameter så formaterar verktyget URL:en åt dig.

## Vad är UTM-parametrar? {#what-are-utm-parameters}

För att förstå hur UTM-parametrar fungerar ska vi titta på en vanlig URL utan UTM:

`http://www.adobe.com`

Nu ska vi kolla in en URL med UTM:

`http://www.adobe.com?utm_medium=socialmedia&utm_source =facebook&utm_campaign=seasonal-sale&utm_content=photo-400x700px`

Som du ser innehåller den andra länken mycket mer text. UTM-parametrar följer alltid den översta domänen (.com i det här exemplet) och börjar med ett frågetecken. Därefter spelar parametrarnas ordning ingen roll, men du bör följa en konsekvent namnkonvention. Expanderingar måste placeras mellan varje parameter för att separera varje UTM. Nu kan vi gå in på mer detaljerad information om vad varje parameter representerar.

Läs mer om [bästa sättet att ställa in UTM-parametrar](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md).

**utm_medium**

* Medium identifierar de fordon som du använder för att marknadsföra ditt företag.
* Det besvarar frågan:&quot;Hur kommer de åt dig?&quot;
* Det betecknar kanalen på den högsta nivån.
* Sociala medier, e-post, organisk sökning och betald sökning är alla exempel på potentiella medelvärden.
* Den här parametern mappar data till [!DNL Marketo Measure] Fältet Medium.
* _[!DNL Marketo Measure]God praxis:_ Använd inte det här fältet för att anropa en delkanal, annars kan du få problem med att generera rapporter på den faktiska kanalen. Använd det för att identifiera ert marknadsföringsfordon eller er marknadsföringskanal. Om du till exempel vill använda e-post för att marknadsföra produkten är mediet e-post.

**utm_source**

* Källa identifierar den delkanal som är trafikens källa.
* Det besvarar frågan: &quot;Var kommer den här personen ifrån?&quot;
* I ett exempel på sociala medier är trafikkällan den plattform för sociala medier som används.
   * I detta exempel [!DNL Facebook] är källvärdet. Andra exempel är Twitter och Instagram. Om UTM-mediet är [!DNL Paid Search]UTM-källan kan däremot vara AdWords eller BingAds.

* Den här parametern mappar till [!DNL Marketo Measure] Fältet &#39;Källa för kontaktpunkt&#39; i SFDC.
* _[!DNL Marketo Measure]God praxis:_ Den här parametern spårar trafikens källa, så det är inte lämpligt att använda den för att ange annonstypen, t.ex. återmarknadsföring, sponsring osv. Den används bäst för att spåra underkanalen på den högre nivån. Kom ihåg, du svarar på frågan &quot;varifrån kommer min trafik?&quot; Du letar efter referenten. I det här exemplet är UTM-källan den plats där annonsen finns (inte den faktiska webbsidan, eftersom den automatiskt spåras utanför taggarna). Om du håller på att spåra en drop-email-kampanj är drop-e-post källan.

**utm_campaign**

* Campaign används för att identifiera en viss marknadsföringskampanj.
* Det besvarar frågan:&quot;Varför kommer de till dig?&quot;
* Använd den här taggen för att ange namnet på annonskampanjen som den finns i [!DNL Google AdWords] eller [!DNL BingAds], eller för att ange namnet som används för att identifiera kampanjen internt. Du kan till och med använda den här taggen för att ange annan information som geopositionering eller annonsnätverkstyp.
* Den här parametern mappar till [!DNL Marketo Measure] Ad Campaign Name field i SFDC.
* _[!DNL Marketo Measure]Bästa praxis_: När kampanjnamn ska fastställas bör du undvika att använda skiljetecken eller tomma mellanslag mellan orden, eftersom det kan leda till webbläsarkodningsfel. För bästa resultat bör du använda understreck i stället.

**utm_content**

* Använd parametern UTM Content när du vill spåra mer än en marknadsföringsbit som finns på en enda webbsida. Om du till exempel har knappen &quot;Begär en demo&quot; och knappen &quot;Registrera dig för vårt veckonyhetsbrev&quot; och vill veta vilken som genererar mest trafik, skulle du namnge var och en och använda en UTM-innehållstagg för att spåra dem. Namnet på varje del av &quot;innehåll&quot; är taggens värde.
* Den här parametern mappar till [!DNL Marketo Measure] Ad Content-fältet i SFDC.
* _[!DNL Marketo Measure]Bästa praxis_: Detta är ett valfritt värde, men [!DNL Marketo Measure] rekommenderar att du använder den. Den här taggen är associerad med titeln på den annons eller det marknadsföringsmaterial som du vill spåra. Om du använder en bildannons måste du skriva bildens dimensioner i dess titel.

**utm_term**

* Termen liknar parametern UTM Content. Termen är bra för att identifiera nyckelord i annonser för betalda kampanjer. Om du använder funktionen för automatisk taggning gör du detta åt dig. Om du inte använder annonsplattformens funktion för automatisk taggning ska du lägga till alla nyckelord du vill spåra noggrant.
* Den här parametern mappar till [!DNL Marketo Measure] Fältet Nyckelordstext i SFDC.
* _[!DNL Marketo Measure]Bästa praxis_: UTM-termtaggen är valfri men passar bra för att spåra nyckelord. Dubbelkontrollera stavningen och undvik att använda specialtecken. Om mer än ett ord behövs kan du försöka med att använda understreck eller inga mellanslag alls.

Varje parameter samlar in information som är relevant för det tilldelade värdet. Värdet för varje tagg gör att ni kan spåra och sortera alla era digitala kampanjer och besvara frågorna: var, hur och varför?

Här följer ett diagram över UTM-parametrar [!DNL Marketo Measure] parser och motsvarande Touchpoint-fält som de är knutna till:

| **UTM-parameter** | **Motsvarande [!DNL Marketo Measure] Fält** |
|---|---|
| utm_medium | Medel |
| utm_source | Kontaktpunktskälla |
| utm_campaign | Namn på annonskampanj |
| utm_content | Annonsinnehåll |
| utm_term | Nyckelord |
