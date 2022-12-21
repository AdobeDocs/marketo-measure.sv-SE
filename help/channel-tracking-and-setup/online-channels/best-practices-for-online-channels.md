---
description: Bästa praxis för onlinekanaler - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa praxis för onlinekanaler
exl-id: 766cb01c-98b3-492d-bb35-e0a78b76333a
source-git-commit: 02f686645e942089df92800d8d14c76215ae558f
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Bästa praxis för onlinekanaler {#best-practices-for-online-channels}

## Översikt {#overview}

Att ha korrekta [!DNL Marketo Measure] rapporter måste era marknadsföringskanaler vara korrekt konfigurerade. Marknadsföringskanalfältet visar den grupp av marknadsföringsaktiviteter på högsta nivå som en kontaktyta kan tillhöra (t.ex. betalsökning, direkt, socialt osv.).

Det finns två sätt att skapa marknadsföringskanaler: online och offline. Det här dokumentet fokuserar på [!DNL Marketo Measure] rekommendationer för hur du konfigurerar och underhåller onlinekanaler.

Reglerna för onlinekanaler är riktlinjer för hur [!DNL Marketo Measure] mappar dina digitala kontaktytor, dvs. alla kontaktytor som spåras och skapas via [!DNL Marketo Measure] JS på er webbplats. Om dessa regler inte är heltäckande, eller inte är korrekt ordnade, kan kontaktytor tillskrivas den felaktiga kanalen, vilket minskar rapporteringsnoggrannheten. Se till att era regler för onlinekanaler är korrekta och aktuella och garanterar att era digitala data tilldelas rätt kanal och underkanaler i era [!DNL Marketo Measure] Rapportering.

## Bästa praxis {#best-practice}

Oavsett om du konfigurerar reglerna för första gången eller bara granskar dem för att kontrollera om de är korrekta bör du tänka på följande bästa praxis.

Ta dig tid att fundera över hur era marknadsföringskampanjer är organiserade och hur de passar in i [!DNL Marketo Measure] ramverk. Bestäm vilka kanaler och underkanaler som ska visas i onlinekanalerna samt vilka kampanjer, UTM-parametrar eller refererande webbplatser som skiljer dessa kanaler från varandra.

Tänk på följande:

* Alla digitala kanaler och underkanaler ska representeras med minst en regel
   * Om kanalen inte leder personer till din webbplats är det inte en onlinekanal
* Det går bra att ha flera regler för en kanal/underkanal
   * Flera regler kan ses som&quot;datatypsbyte av ett bredare nät&quot; för att säkerställa att varje kontaktyta mappas korrekt. Parametrar kan ofta läggas till eller missas helt och hållet, och därför är det bra att ha flera regler för att hämta en kanal/underkanal för att säkerställa att mappningen är korrekt.
* [!DNL Marketo Measure] logik prioriterar kontaktpunktsmappning i fallande ordning med början på kalkylbladets översta rad och sedan nedåt
   * [!DNL Marketo Measure] läser varje regel (rad) och söker efter true och first fit. Kontaktpunkten mappas sedan till den kanalen/underkanalen
   * Sortera inte bladet i alfabetisk ordning eftersom detta påverkar logikreglerna.
* Bevara reglerna inom hakparenteser, redigera eller lägg inte till reglerna inom hakparenteser (exempel: [AdWords Paid Search] eller [Facebook Betald] )
   * De här är ur lådan [!DNL Marketo Measure] regler som har inbyggd logik, som är knutna till [!DNL Marketo Measure] integreringar. Ge de här reglerna högsta prioritet för den kanalen/delkanalsavsnittet för att säkerställa att [!DNL Marketo Measure] integreringar kan fungera som avsett.
* När filen har överförts kan du inte ändra någon av reglerna på sju dagar
   * [!DNL Marketo Measure] använder den här tiden för att bearbeta och uppdatera Touchpoints, och därför bör du kontrollera reglerna innan du överför dem.

## Bästa praxis för underhåll {#best-practice-for-maintenace}

När de har sparats och bearbetats fungerar reglerna för onlinekanaler kontinuerligt för att få fler digitala kontaktytor. Vissa ändringar eller scenarier gör att du vill granska onlinekanalinställningarna. [!DNL Marketo Measure] rekommenderar att du granskar dina regler för onlinekanaler en gång var sjätte månad. Detta säkerställer att [!DNL Marketo Measure] data är anpassade till era interna definitioner av onlinekanaler/underkanaler och er användning av UTM-kanaler.

Andra saker som kan få ditt team att göra onlinekanalunderhåll är ....

* Ny digital kanal/underkanal startas
* UTM-parametrar uppdateras eller ändras
* Ändringar i kanalorganisationen eller namnkonventioner
* Omsättning i marknadsföringsteamet

Om ditt team nyligen har haft något av ovanstående [!DNL Marketo Measure] rekommenderar att du granskar reglerna för dina onlinekanaler och gör lämpliga ändringar.

>[!MORELIKETHIS]
>
>* [Inställningar för onlinekanal](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md)
>* [UTM-parametrar](/help/channel-tracking-and-setup/online-channels/utm-parameters.md)
>* [Marknadsföringskanal och delkanal](/help/channel-tracking-and-setup/online-channels/marketing-channels-and-subchannels.md)
>* [UTM Best Practices](/help/channel-tracking-and-setup/online-channels/best-practices-for-setting-up-utm-parameters.md)

