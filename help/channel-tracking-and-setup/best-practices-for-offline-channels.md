---
description: Best Practices for Offline Channels guidelines for Marketo Measure users
title: Bästa praxis för offlinekanaler
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---


# Bästa praxis för offlinekanaler {#best-practices-for-offline-channels}

## Översikt {#overview}

Om du vill ha korrekt [!DNL Marketo Measure]-rapportering måste du konfigurera dina marknadsföringskanaler korrekt. Fältet [!UICONTROL Marketing Channel] visar den grupp av marknadsföringstaktik på den högsta nivån som en kontaktyta kan tillhöra (till exempel Händelser, webbinarier, Innehållssyndikering och så vidare).

Det finns två aspekter av att konfigurera era marknadsföringskanaler: online och offline. Det här dokumentet fokuserar på [!DNL Marketo Measure] rekommendationer om god praxis för att konfigurera och underhålla offlinekanaler och hur de synkroniseras med [!DNL Marketo Measure] via CRM-kampanjer.

Offlinekanaler har två viktiga aspekter:

1. Offlinekanalsmappning, som är ramverket som anger vilken kanal och underkanal som offlinekontaktpunkten tillhör för [!DNL Marketo Measure]
1. Synkronisering av offlinekampanj, som skapar kontaktytor offline

Offlinekontaktpunkter skapas från en CRM-kampanj och är avsedda att spåra alla marknadsföringsinteraktioner som inte kan spåras digitalt via den [!DNL Marketo Measure] JavaScript som implementeras på webbplatsens sidor. När en CRM-kampanj synkroniseras med [!DNL Marketo Measure] skapas kontaktytor för de definierade kampanjmedlemmarna i kampanjen.

Värdet för marknadsföringskanal för de här kontaktytorna baseras på fältet Typ i Campaign. Mappningen av CRM-kampanjtyp till Marknadskanal och Delkanal hanteras på fliken Offlinekanaler i kontoinställningarna för [!DNL Marketo Measure]. Om du ser till att din offlinekanalmappning är korrekt och aktuell kan du garantera att dina offlinedata för kontaktytor kan tillskrivas rätt marknadsföringskanaler och underkanaler i din [!DNL Marketo Measure]-rapportering.

## Bästa praxis | Offlinekanalmappning {#best-practice-offline-channel-mapping}

Oavsett om du mappar dina offlinekanaler för första gången eller bara granskar dem för att kontrollera om de är korrekta bör du tänka på följande bästa praxis.

* Skapa ett avsiktligt ramverk för offlinekanaler
   * Ta dig tid att tänka på hur era marknadsföringskampanjer är organiserade och hur de passar in i ramverket [!DNL Marketo Measure]. Bestäm vilka kanaler och underkanaler som ska visas i dina offlinekanaler och vilka CRM Campaign-typer som skiljer dessa kanaler från varandra
* Arbeta för att använda dina aktuella CRM-kampanjvärden av typen först
   * Offlinekanaler definieras av CRM-kampanjen &quot;Typ&quot;, men det anpassade CRM-kampanjens &quot;Typ&quot;-värde kan behöva skapas för att passa idealiska offlinekanaler och delkanalsvärden. Idealiska anpassade CRM-Campaign-typvärden ska ha den namnkonvention som visas nedan:
      * KANAL - SUBKANAL
      * Exempel: Event - Tradeshow
      * Detta garanterar att mappningen till delkanalsnivån är så enkel och ren som möjligt
* En underkanal kan bara mappas till en CRM-kampanj av typen
   * Flera CRM-kampanjtyper kan mappas till en enda kanal, men bara en CRM-kampanjtyp kan mappas till varje underkanal inom varje kanal
* Endast OFFLINE CRM-kampanjen Types ska mappas till offlinekanaler eftersom endast offlinekampanjer ska synkroniseras med [!DNL Marketo Measure] för att skapa kontaktytor:
   * ONLINE CRM-kampanjen Types ska mappas till [!UICONTROL Marketing Channel] = NULL. Det här värdet rekommenderas eftersom det fungerar som en&quot;röd flagga&quot; som anger att dina offlinekanaler har granskats och eventuell CRM-kampanjtyp som har mappats till&quot;NULL&quot; är en ONLINE-typ och ska inte synkroniseras med [!DNL Marketo Measure]. Kontaktpunkter som är relaterade till CRM-kampanjen Typer för Online spåras redan via funktionen och kanalerna [!DNL Marketo Measure] online. Om du synkroniserar dessa kampanjer riskerar du att få &quot;dubbletter&quot;-kontaktytor/dubbelräkning

## Bästa praxis | Synkronisering av offlinekampanj {#best-practice-offline-campaign-sync}

* Kontrollera att fältet Typ är korrekt för varje CRM-kampanj
   * Type avgör marknadsföringskanalen och subkanalen för alla kontaktytor som kommer från Campaign när de har synkroniserats
* Oavsett om du använder den CRM-baserade synkroniseringsmetoden för kampanjer (Aktivera kontaktytor för köpare) eller den [!DNL Marketo Measure] appbaserade synkroniseringsmetoden (anpassad kampanjsynkronisering på fliken [!UICONTROL Campaigns] i kontoinställningarna för [!UICONTROL Marketo Measure]), bör offlinekontaktpunkter bara skapas om kampanjmedlemmen hade ett verkligt offlineengagemang med kampanjen och ert varumärke:
   * För offlinekanaler som händelser eller webbinarier:&quot;registreringar&quot; spåras vanligtvis via formulärinskickningar på din webbplats och [!DNL Marketo Measure] onlinefunktioner. Kampanjmedlemmar med statusen Registrerad bör därför inte få en offlinekontaktyta från Campaign för att undvika dubbelräkning. Kontaktpunkter offline ska endast representera &quot;närvaro&quot; för evenemanget eller webbinariet.
   * Vissa offlinekanaler som Innehållssyndikering är tydligare eftersom alla kampanjmedlemmar har samma svarsstatus som de faktiskt svarade på kampanjen, i det här fallet hämtar de innehåll på en tredjepartswebbplats och därför bör få en kontaktyta offline
* När du använder metoden för anpassad kampanjsynkronisering i appen [!DNL Marketo Measure] måste du se till att fältet &#39;Slutpunktsdatum&#39; är baserat på datumfältet från antingen Campaign- eller Campaign-medlemmen som mest indikerar när pekpunktsinteraktionen faktiskt inträffade
* Använd knappen &#39;Uppdatera slutpunktsdatum gruppvis&#39; om du behöver åsidosätta &#39;slutpunktsdatumet&#39; för någon av de kontaktytor som är offline och som kommer från en CRM-kampanj. &#39;Slutpunktsdatum&#39; måste vara så exakt som möjligt för att säkerställa att kontaktytan innehåller den mest exakta &#39;slutpunktspositionen&#39; och därmed rätt mängd attribueringskredit

## Bästa praxis för underhåll {#best-practice-for-maintenance}

När du väl har konfigurerat offlinekanalen till att börja med fortsätter du att skapa kontaktpunkter offline utifrån detta. Vi rekommenderar att du granskar offlinekonfigurationen minst två gånger per år. Detta garanterar rena och korrekta data om köparens kontaktyta.

Om du gör några ändringar i din kampanjhantering eller dina processer måste du se till att du uppdaterar din offlinekanalmappning och/eller synkroniseringsprocess för [!DNL Marketo Measure].

Ändringar som kan göra att ditt team uppdaterar offlinekanalen i [!DNL Marketo Measure] kan omfatta:

* CRM-kampanjen Types har skapats eller redigerats
* Kampanjmedlemmens status har skapats eller redigerats
* Om du använder CRM Campaign Sync-metoden via fältet Enable Buyer Touchpoints (Aktivera kontaktytor för köpare), ska du se till att det här fältet granskas och uppdateras för varje CRM-kampanj som skapas. Om det här fältet ignoreras kommer det inte att finnas några relaterade offlinekontaktpunktsdata
* Om du stöter på kontaktytor offline från en CRM-kampanj som ser ut att vara kontaktytor online (marknadsföringskanal = NULL), kontrollerar du att den relaterade CRM-kampanjen granskas och att synkroniseringen är inaktiverad

Om ditt team nyligen har använt något av ovanstående rekommenderar [!DNL Marketo Measure] att du granskar din offlinekanalsmappning och offlinekampanjer för att göra lämpliga ändringar och se till att de synkroniseras korrekt.

>[!MORELIKETHIS]
> [Inställningar för offlinekanal](/help/channel-tracking-and-setup/offline-custom-channel-setup.md)
> [Synkronisering av anpassad kampanj - appsynkronisering &#x200B;](/help/channel-tracking-and-setup/custom-campaign-sync.md)
> [Synkroniserar offlinekampanjer - CRM-synkronisering &#x200B;](/help/channel-tracking-and-setup/syncing-offline-campaigns.md)
> [Offlinekampanj- och kampanjmedlemmar - CRM-synkronisering &#x200B;](/help/channel-tracking-and-setup/campaigns-and-campaign-members.md)
> [Kampanjsynkroniseringsdatum - CRM-synkronisering &#x200B;](/help/channel-tracking-and-setup/campaign-sync-dates.md)
> [Konfigurationer för flera kampanjposttyper &#x200B;](/help/channel-tracking-and-setup/configurations-record-types.md)
> [Skapar en kampanjlistvy &#x200B;](/help/channel-tracking-and-setup/creating-a-campaign-list-view-for-salesforce-campaigns.md)
> [Synkroniserar historikdata &#x200B;](/help/channel-tracking-and-setup/syncing-historical-data.md)
