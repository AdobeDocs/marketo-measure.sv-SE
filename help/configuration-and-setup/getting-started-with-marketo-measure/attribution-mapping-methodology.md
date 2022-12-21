---
unique-page-id: 18874716
description: Attribution Mapping Method - [!DNL Marketo Measure] - Produktdokumentation
title: Attribution Mapping Method
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# Attribution Mapping Method {#attribution-mapping-methodology}

Metoden för attribueringsmappning är processen att hitta vissa objekt i CRM (kontakter, säljprojekt, konton) för att skapa attribueringskontaktytor i den associerade affärsmöjligheten. Med andra ord är det [!DNL Marketo Measure] sätt att förstå vilka kontaktytor som ska ingå i attribueringsmodellen baserat på era aktuella CRM-processer.

## Mappning av konto-ID {#account-id-mapping}

Ut ur lådan, [!DNL Marketo Measure] tillhandahåller mappning av konto-ID. Detta innebär att [!DNL Marketo Measure] tittar på marknadsföringsinformationen för kontot och dess kontakter för att skapa attribueringsslutpunkter som är kopplade till affärsmöjligheten. Nedan visas en enkel representation av den processen.

![](assets/1-1.png)

Kom ihåg att **inte alla** kontaktytor från dina kontakter kommer att flyttas in i säljprojektet som attribueringsslutpunkter. Affärsmöjlighetens tidslinje (det första pekdatumet - stängningsdatum) avgör om en kontaktyta ska räknas som en påverkare av affärsmöjligheten eller inte. Om en kontaktyta på kontakt A inträffade efter att affärsmöjligheten stängts, Won/Lost, [!DNL Marketo Measure] inte kommer att föra fram kontaktytan till säljprojektet. Den här tidslinjeproceduren följs för alla andra attribueringsobjektmappningar.

Pros: Den här attribueringsmetoden är mycket effektiv för de flesta företag. Marknadsföringsteamet behöver inte förlita sig på säljteamet för att koppla alla kontakter till en viss affärsmöjlighet (vilket ofta är ett problem). Även om ett säljteam associerar kontaktroller kan många andra kontakters interaktioner med marknadsföringsmaterial missas. Slutligen är metoden ett stöd för ABM-strategier som strävar efter att påverka hela kontot, snarare än specifika faktorer.

Kon: Om det finns starka SLA för marknadsföring och försäljning som definierar vem som ska få krediter för vad, kan den här metoden vara problematisk. Dessutom, om ingen använder kontohierarkier för att definiera specifika affärsenheter inom ett större konto (t.ex.: IBM) kan då marknadsföringsinteraktioner som är specifika för en affärsenhet spridas över andra affärsenhetsmöjligheter.

## Mappning av säljprojektskontaktroll {#opportunity-contact-role-mapping}

De flesta kunder utnyttjar mappning av konto-ID, [!DNL Marketo Measure] kan söka efter kontaktroller (kontakter som är kopplade till säljprojektet) inom ett säljprojekt för att dela upp attribueringsprocessen. Detta innebär att [!DNL Marketo Measure] push-erar bara marknadsföringsinteraktioner som är kopplade till kontaktrollerna i säljprojektet som Touchpoints för Buyer-attribuering. Nedan visas en representation av den här processen.

![](assets/2-1.png)

Pros: Om ditt team har en mycket väldefinierad process för kontaktroller kan den här typen av attribueringsmappning vara idealisk för dig. Det kommer att hjälpa till att anpassa försäljning och marknadsföring lite mer eftersom alla skulle förstå hur attribueringen bryts ned. Den här processen är också mycket användbar när organisationer riktar sig till flera olika affärsenheter inom ett stort företag, liksom när de säljer olika produkter samtidigt.

Kon: Men om det inte finns någon process för kontaktroll kommer marknadsföringen att förlora mycket marknadsföringsdata och teamet kommer att få mycket mindre beröm för sina marknadsföringssatsningar som påverkar möjligheterna.

## Rollmappning för primär kontakt för affärsmöjlighet {#opportunity-primary-contact-role-mapping}

Förutom att bara titta på kontaktrollerna för affärsmöjligheten, [!DNL Marketo Measure] kan fokusera ännu mer på att endast titta på de primära kontakterna i en säljprojekt. Med den här inställningen i åtanke [!DNL Marketo Measure] hämtar bara den kontaktyta som är kopplad till de primära kontakterna för en affärsmöjlighet och överför informationen till attribueringsberättelsen för den specifika affärsmöjligheten. Se bilden nedan.

![](assets/3.png)

Pros: Om ert team bara är intresserade av att förstå hur marknadsföringen påverkar kontakterna som sätts som&quot;primära&quot; för affärsmöjligheten, passar den här typen av karta bäst.

Kon: Detta är definitivt den minst använda mappningsprocessen och kan i hög grad undergräva påverkan på marknadsföring som flyttar nålen över andra kontakter vid en möjlighet.
