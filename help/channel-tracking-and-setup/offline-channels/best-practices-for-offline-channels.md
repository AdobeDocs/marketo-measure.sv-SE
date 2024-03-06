---
description: Bästa praxis för offlinekanaler - [!DNL Marketo Measure]
title: Bästa praxis för offlinekanaler
exl-id: 71c50614-8d5b-469f-bc02-3cc489464a4e
feature: Channels
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# Bästa praxis för offlinekanaler {#best-practices-for-offline-channels}

## Översikt {#overview}

Att ha korrekta [!DNL Marketo Measure] rapporter måste era marknadsföringskanaler vara korrekt konfigurerade. The[!UICONTROL Marketing Channel]&#39; visas den grupp av marknadsföringsstrategier på högsta nivå som en kontaktyta kan tillhöra (till exempel Händelser, Webbinarier, Innehållssyndikering och så vidare).

Det finns två aspekter av att konfigurera era marknadsföringskanaler: online och offline. Det här dokumentet fokuserar på [!DNL Marketo Measure] rekommendationer för hur du konfigurerar och underhåller offlinekanaler och hur de synkroniseras med [!DNL Marketo Measure] via CRM Campaigns.

Offlinekanaler har två viktiga aspekter:

1. Offline Channel Mapping, som är ramverket som anger [!DNL Marketo Measure] vilken kanal och vilka subkanaler som kontaktytan offline tillhör
1. Synkronisering av offlinekampanj, som skapar kontaktytor offline

Offlinekontaktpunkter skapas från en CRM-kampanj och är avsedda att spåra all marknadsföringsinteraktion som inte kan spåras digitalt via [!DNL Marketo Measure] JavaScript som implementeras på webbplatsens sidor. När en CRM-kampanj synkroniseras med [!DNL Marketo Measure], skapas kontaktytor för de definierade kampanjmedlemmarna i Campaign.

Värdet för marknadsföringskanal för de här kontaktytorna baseras på fältet Typ i Campaign. Mappningen av CRM Campaign Type till Marketing Channel och Subchannel hanteras på fliken Offline Channels i [!DNL Marketo Measure] Kontoinställningar. Om du ser till att mappningen av offlinekanaler är korrekt och aktuell kan du garantera att dina offlinedata för kontaktytor kan tillskrivas rätt marknadsföringskanaler och underkanaler inom dina [!DNL Marketo Measure] Rapportering.

## Bästa praxis | Offlinekanalmappning {#best-practice-offline-channel-mapping}

Oavsett om du mappar dina offlinekanaler för första gången eller bara granskar dem för att kontrollera om de är korrekta bör du tänka på följande bästa praxis.

* Skapa ett avsiktligt ramverk för offlinekanaler
   * Ta dig tid att fundera över hur era marknadsföringskampanjer är organiserade och hur de passar in i [!DNL Marketo Measure] ramverk. Bestäm vilka kanaler och underkanaler som ska visas i dina offlinekanaler och vilka CRM Campaign-typer som skiljer dessa kanaler från varandra
* Arbeta för att använda dina aktuella CRM-kampanjvärden av typen först
   * Offlinekanaler definieras av CRM-kampanjen &quot;Typ&quot;, men det anpassade CRM-kampanjens &quot;Typ&quot;-värde kan behöva skapas för att passa idealiska offlinekanaler och delkanalsvärden. Idealiska anpassade CRM-Campaign-typvärden ska ha den namnkonvention som visas nedan:
      * KANAL - SUBKANAL
      * Exempel: Event - Tradeshow
      * Detta garanterar att mappningen till delkanalsnivån är så enkel och ren som möjligt
* En underkanal kan bara mappas till en CRM-kampanj av typen
   * Flera CRM-kampanjtyper kan mappas till en enda kanal, men bara en CRM-kampanjtyp kan mappas till varje underkanal inom varje kanal
* Endast OFFLINE CRM-kampanjen Types ska mappas till Offline-kanaler eftersom endast offlinekampanjer ska synkroniseras med [!DNL Marketo Measure] för att skapa kontaktytor:
   * ONLINE CRM-kampanjen Types ska mappas till en [!UICONTROL Marketing Channel] = &quot;NULL&quot;. Det här värdet rekommenderas eftersom det fungerar som en&quot;röd flagga&quot; som anger att dina offlinekanaler har granskats och all CRM-kampanjtyp som mappas till&quot;NULL&quot; är en ONLINE-typ och ska inte synkroniseras med [!DNL Marketo Measure]. Kontaktpunkter som rör CRM-kampanjen&quot;Typer&quot; online spåras redan via [!DNL Marketo Measure] Onlinefunktioner och kanaler. Om du synkroniserar dessa kampanjer riskerar du att få &quot;dubbletter&quot;-kontaktytor/dubbelräkning

## Bästa praxis | Synkronisering av offlinekampanj {#best-practice-offline-campaign-sync}

* Kontrollera att fältet Typ är korrekt för varje CRM-kampanj
   * Type avgör marknadsföringskanalen och subkanalen för alla kontaktytor som kommer från Campaign när de har synkroniserats
* Om den CRM-baserade kampanjsynkroniseringsmetoden (Aktivera kontaktytor för köpare) eller [!DNL Marketo Measure] App-baserad synkroniseringsmetod (anpassad kampanjsynkronisering i[!UICONTROL Campaigns]fliken &#39; [!UICONTROL Marketo Measure] Kontoinställningar) ska kontaktytor offline bara skapas om kampanjmedlemmen har ett verkligt offlineengagemang med kampanjen och ert varumärke:
   * För offlinekanaler som händelser eller webbinarier:&quot;registreringar&quot; spåras vanligtvis via formulärinlämningar på din webbplats och [!DNL Marketo Measure] Onlinefunktioner. Kampanjmedlemmar med statusen Registrerad bör därför inte få en offlinekontaktyta från Campaign för att undvika dubbelräkning. Kontaktpunkter offline ska endast representera &quot;närvaro&quot; för evenemanget eller webbinariet.
   * Vissa offlinekanaler som Innehållssyndikering är tydligare eftersom alla kampanjmedlemmar har samma svarsstatus som de faktiskt svarade på kampanjen, i det här fallet hämtar de innehåll på en tredjepartswebbplats och därför bör få en kontaktyta offline
* När du använder metoden för anpassad kampanjsynkronisering i [!DNL Marketo Measure] Appen, kontrollera att fältet &#39;Slutpunktsdatum&#39; är baserat på datumfältet från antingen Campaign- eller Campaign-medlemmen som mest indikerar när kontaktytpunktsinteraktionen faktiskt inträffade
* Använd knappen &#39;Uppdatera slutpunktsdatum gruppvis&#39; om du behöver åsidosätta &#39;slutpunktsdatumet&#39; för någon av de kontaktytor som är offline och som kommer från en CRM-kampanj. &#39;Slutpunktsdatum&#39; måste vara så exakt som möjligt för att säkerställa att kontaktytan innehåller den mest exakta &#39;slutpunktspositionen&#39; och därmed rätt mängd attribueringskredit

## Bästa praxis för underhåll {#best-practice-for-maintenance}

När du väl har konfigurerat offlinekanalen till att börja med fortsätter du att skapa kontaktpunkter offline utifrån detta. Vi rekommenderar att du granskar offlinekonfigurationen minst två gånger per år. Detta garanterar rena och korrekta data om köparens kontaktyta.

Om du ändrar något i din Campaign-hantering eller -processer måste du se till att du uppdaterar dina [!DNL Marketo Measure] Mappning av offlinekanaler och/eller synkroniseringsprocess.

Ändringar som kan göra att ditt team uppdaterar offlinekanalen i [!DNL Marketo Measure] kan omfatta:

* CRM-kampanjen Types har skapats eller redigerats
* Kampanjmedlemmens status har skapats eller redigerats
* Om du använder CRM Campaign Sync-metoden via fältet Enable Buyer Touchpoints (Aktivera kontaktytor för köpare), ska du se till att det här fältet granskas och uppdateras för varje CRM-kampanj som skapas. Om det här fältet ignoreras kommer det inte att finnas några relaterade offlinekontaktpunktsdata
* Om du stöter på kontaktytor offline från en CRM-kampanj som ser ut att vara kontaktytor online (marknadsföringskanal = NULL), kontrollerar du att den relaterade CRM-kampanjen granskas och att synkroniseringen är inaktiverad

Om ditt team nyligen har haft något av ovanstående: [!DNL Marketo Measure] rekommenderar att du granskar din kanalmappning offline och offlinekampanjer för att göra lämpliga ändringar och se till att de synkroniseras korrekt.

>[!MORELIKETHIS]
>
>* [Inställningar för offlinekanal](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md)
>* [Synkronisering av anpassad kampanj - appsynkronisering](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md)
>* [Synkronisera offlinekampanjer - CRM-synkronisering](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)
>* [Offlinekampanj- och kampanjmedlemmar - CRM-synkronisering](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaigns-and-campaign-members.md)
>* [Kampanjsynkroniseringsdatum - CRM-synkronisering](/help/channel-tracking-and-setup/offline-channels/legacy-processes/campaign-sync-dates.md)
>* [Konfigurationer för flera kampanjposttyper](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md)
>* [Skapa en kampanjlistvy](/help/channel-tracking-and-setup/offline-channels/legacy-processes/creating-a-campaign-list-view-for-salesforce-campaigns.md)
>* [Synkroniserar historiska data](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-historical-data.md)
