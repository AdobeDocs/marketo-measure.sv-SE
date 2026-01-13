---
description: Attributmappningsmetod - [!DNL Marketo Measure]
title: Metod för attribueringsmappning
exl-id: 4d54dd20-9a82-4b87-8908-ced2bd9c0f2f
feature: Attribution
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---


# Metod för attribueringsmappning {#attribution-mapping-methodology}

Metoden för attribueringsmappning är processen att hitta vissa objekt i CRM (kontakter, säljprojekt, konton) för att skapa attribueringskontaktytor i den associerade affärsmöjligheten. Med andra ord är det [!DNL Marketo Measure]-sättet att förstå vilka kontaktytor som ska inkluderas i attribueringsmodellen baserat på din aktuella CRM-process.

## Mappning av konto-ID {#account-id-mapping}

[!DNL Marketo Measure] tillhandahåller mappning av konto-ID. Det innebär att [!DNL Marketo Measure] tittar på marknadsföringsinformationen för kontot och dess kontakter för att skapa attribueringsslutpunkter som är associerade med affärsmöjligheten. Nedan visas en enkel representation av den processen.

![ 1](assets/1-1.png)

Tänk på att **inte alla** kontaktytor från dina kontakter överförs till säljprojektet som attribueringsslutpunkter. Affärsmöjlighetens tidslinje (dess första pekdatum - slutdatum) avgör om en kontaktyta räknas som en påverkare av affärsmöjligheten. Om en kontaktyta på kontakt A inträffade efter att affärsmöjligheten stängdes, Won/Lost, kommer [!DNL Marketo Measure] inte att skicka kontaktytan till affärsmöjligheten. Den här tidslinjeproceduren följs för alla andra attribueringsobjektmappningar.

Pros: Den här attribueringsmetoden är mycket effektiv för de flesta företag. Marknadsföringsteamet behöver inte förlita sig på säljteamet för att koppla alla kontakter till en viss affärsmöjlighet (vilket ofta är ett problem). Även om ett säljteam associerar kontaktroller kan många andra kontakters interaktioner med marknadsföringsmaterial missas. Slutligen är denna metod ett stöd för ABM-strategi som syftar till att påverka hela kontot snarare än specifika faktorer.

Kon: Om det finns starka SLA för marknadsföring och försäljning som definierar vem som ska få krediter för vad, kan den här metoden vara problematisk. Om man inte använder kontohierarkier för att definiera specifika affärsenheter inom ett större konto (t.ex. IBM) kan dessutom marknadsföringsinteraktioner som är specifika för en affärsenhet spridas över andra affärsenhetsmöjligheter.

## Mappning av säljprojektskontaktroll {#opportunity-contact-role-mapping}

>[!NOTE]
>
>Mappningsmetoder för kontaktroller är bara tillgängliga för dem som använder Salesforce som CRM. Det är inte tillgängligt för Microsoft Dynamics-användare eftersom det saknas ett kontaktroll-objekt i CRM.

De flesta klienter använder mappning av konto-ID, men [!DNL Marketo Measure] kan slå upp till kontaktrollerna (kontakter som är kopplade till säljprojektet) i ett säljprojekt för att dela upp attribueringsprocessen. Det innebär att [!DNL Marketo Measure] bara skickar marknadsföringsinteraktioner som är associerade med kontaktrollerna i affärsmöjligheten som Touchpoints för Buyer-attribuering. Nedan visas en representation av den här processen.

![ 1](assets/2-1.png)

Pros: Om ditt team har en väldefinierad process för kontaktroller kan den här typen av attribueringsmappning vara idealisk för dig. Det hjälper till att anpassa försäljning och marknadsföring lite mer eftersom alla skulle förstå hur attribueringen bryts ned. Den här processen är också användbar när organisationer riktar sig till flera olika affärsenheter inom ett stort företag och när de säljer olika produkter samtidigt.

Kon: Men om det inte finns någon process för kontaktroll förlorar marknadsföringen en massa marknadsföringsdata och teamet får i slutändan mycket mindre beröm för sina marknadsföringssatsningar som påverkar möjligheterna.

## Rollmappning för primär kontakt för affärsmöjlighet {#opportunity-primary-contact-role-mapping}

Förutom att bara titta på kontaktrollerna för affärsmöjligheten kan [!DNL Marketo Measure] fokusera ännu mer på att bara titta på de primära kontakterna för en affärsmöjlighet. Med den här konfigurationen i åtanke hämtar [!DNL Marketo Measure] bara den kontaktyta för marknadsföring som är associerad med de primära kontakterna för en affärsmöjlighet och överför informationen till attribueringsberättelsen för den specifika affärsmöjligheten. Se bilden nedan.

![Diagram över attribueringsmappning med enbart primära kontaktroller](assets/3.png)

Pros: Om ditt team bara är intresserade av att förstå hur marknadsföringen påverkar kontakter som är inställda som&quot;primära&quot; för affärsmöjligheten passar den här typen av mappning bäst.

Kon: Detta är definitivt den minst använda mappningsprocessen och kan i hög grad undergräva påverkan på marknadsföring som rör nålen över andra kontakter vid en möjlighet.
