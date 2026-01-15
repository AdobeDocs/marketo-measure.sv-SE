---
description: Best Practices for Online Channels guidelines for Marketo Measure users
title: Bästa praxis för onlinekanaler
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---


# Bästa praxis för onlinekanaler {#best-practices-for-online-channels}

## Översikt {#overview}

För att få korrekt [!DNL Marketo Measure]-rapportering måste marknadsföringskanalerna vara korrekt konfigurerade. Marknadsföringskanalfältet visar den grupp av marknadsföringsaktiviteter på högsta nivå som en kontaktyta kan tillhöra (till exempel Betald sökning, Direkt, Social och så vidare).

Det finns två aspekter av att konfigurera era marknadsföringskanaler: online och offline. Det här dokumentet fokuserar på [!DNL Marketo Measure] rekommendationer för bästa praxis för att konfigurera och underhålla onlinekanaler.

Regler för onlinekanal är riktlinjer för hur [!DNL Marketo Measure] mappar dina digitala kontaktytor, det vill säga alla kontaktytor som spåras och skapas via [!DNL Marketo Measure] JS på din webbplats. Om dessa regler inte är heltäckande, eller inte är korrekt ordnade, kan kontaktytor tillskrivas den felaktiga kanalen, vilket minskar rapporteringsnoggrannheten. Om du ser till att dina regler för onlinekanal är korrekta och aktuella kan du vara säker på att dina digitala data tilldelas rätt kanal och underkanaler i din [!DNL Marketo Measure]-rapportering.

## Bästa praxis {#best-practice}

Oavsett om du konfigurerar reglerna för första gången eller bara granskar dem för att kontrollera om de är korrekta bör du tänka på följande bästa praxis.

Ta dig tid att tänka på hur era marknadsföringskampanjer är organiserade och hur de passar in i ramverket [!DNL Marketo Measure]. Bestäm vilka kanaler och underkanaler som ska visas i onlinekanalerna och vilka kampanjer, UTM-parametrar eller refererande webbplatser som skiljer dessa kanaler från varandra.

Tänk på följande:

* Alla digitala kanaler och underkanaler ska representeras med minst en regel
   * Om kanalen inte leder personer till din webbplats är det inte en onlinekanal
* Det går bra att ha flera regler för en kanal/underkanal
   * Flera regler kan ses som&quot;datatypsbyte av ett bredare nät&quot; för att säkerställa att varje kontaktyta mappas korrekt. Parametrar kan ofta läggas till eller missas helt och hållet, och därför är det bra att ha flera regler för att hämta en kanal/underkanal för att säkerställa att mappningen är korrekt.
* [!DNL Marketo Measure]-logiken prioriterar kontaktpunktsmappning i fallande ordning med början på den översta raden i kalkylbladet och gör den nedåt
   * [!DNL Marketo Measure] läser varje regel (rad) och söker efter true och first fit. Kontaktpunkten mappas sedan till den kanalen/underkanalen
   * Sortera inte bladet i alfabetisk ordning eftersom det stör logikreglerna.
* Behåll reglerna inom hakparenteser, redigera inte eller lägg till i reglerna inom hakparenteser (exempel: [AdWords Paid Search] eller [Facebook Paid] )
   * Dessa är utanför rutan [!DNL Marketo Measure]-regler som har inbyggd logik, som är knutna till [!DNL Marketo Measure]-integreringarna. Ge de här reglerna högsta prioritet för det kanal-/delkanalsavsnittet för att se till att [!DNL Marketo Measure]-integreringar kan fungera som de ska.
* När filen har överförts kan du inte ändra någon av reglerna på sju dagar
   * [!DNL Marketo Measure] använder den här tiden för att bearbeta och uppdatera Touchpoints, och därför måste du kontrollera reglerna innan du överför dem.

## Bästa praxis för underhåll {#best-practice-for-maintenace}

När reglerna för onlinekanaler har sparats och bearbetats arbetar de kontinuerligt för att få buggar på era digitala kontaktytor. Vissa ändringar eller scenarier gör att du vill granska onlinekanalinställningarna. [!DNL Marketo Measure] rekommenderar att du granskar dina regler för onlinekanaler en gång var sjätte månad. Detta garanterar att dina [!DNL Marketo Measure]-data är anpassade till dina interna definitioner av onlinekanaler/underkanaler och din användning av UTM-filer.

Andra objekt som kan få ditt team att göra onlinekanalunderhåll är bland annat ...

* Ny digital kanal/underkanal startas
* UTM-parametrar uppdateras eller ändras
* Ändringar i kanalorganisationen eller namnkonventioner
* Omsättning i marknadsföringsteamet

Om ditt team har upplevt något av ovanstående rekommenderar [!DNL Marketo Measure] att du granskar dina regler för onlinekanaler och gör lämpliga ändringar.

>[!MORELIKETHIS]
> [Inställningar för onlinekanal](/help/channel-tracking-and-setup/online-custom-channel-setup.md)
> [UTM-parametrar](/help/channel-tracking-and-setup/utm-parameters.md)
> [Marknadskanal och delkanal](/help/channel-tracking-and-setup/marketing-channels-and-subchannels.md)
> [UTM Best Practices](/help/channel-tracking-and-setup/best-practices-for-setting-up-utm-parameters.md)
