---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: 05ba9e487d492ba4352a7f0577c7221f6ec9567e
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# [!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Läs om de olika [!DNL Marketo Measure] fält som lagts till i [!DNL Salesforce] standardobjekt.

## Konto {#account}

Predictive Engagement Score: Det här fältet används med funktionen ABM för att ge en poäng som relaterar till hur engagerat kontot är och som tar hänsyn till många faktorer som t.ex. senaste sidvisningar, hur många kontakter som är kopplade till kontot, om det finns en stängd popup, osv.

## Campaign {#campaign}

Endast fyra fält har lagts till, en knapp och en valideringsregel.

Unikt ID: Det här fältet används internt för att spåra de olika kampanjer som synkroniseras med [!DNL Marketo Measure].

Aktivera Buyer Touchpoints: Det här fältet är till för den faktiska synkroniseringen av kampanjer för offlineattribuering och historiska data.

Startdatum för kontaktyta: Det här fältet används för att ange ett startdatum när kontaktytor ska tillämpas på historiska kampanjer.

Slutdatum för slutpunkt: Det här fältet används för att ange ett slutdatum för användning av kontaktytor på historiska kampanjer. Ett vanligt exempel är digitala kampanjer före[!DNL Marketo Measure] och sedan ange slutdatumet som den dag skriptet tillämpades.

Uppdatera slutpunktsdatum gruppvis (knapp): Den här knappen används för att hantera slutpunktsdatumet för kampanjmedlemmarna när kampanjen synkroniseras, eftersom vi refererar till antingen kampanjmedlemskapsdatumet eller det första svarsdatumet i rutan. Om dessa datumfält inte är en korrekt representation av det faktiska beröringspunktsdatumet använder vi den här knappen för att ange kontaktpunktsdatumet.

Uppdatera [!DNL Marketo Measure] Attribution (Validation Rule): Den här regeln är inaktuell efter paketversion 6.0.

## Kampanjmedlem {#campaign-member}

Det finns fem fält och en Apex-utlösare har lagts till i paketet.

Touchpoint Status (Lead): Detta är ett diagnostiskt fält som relaterar till en funktion som inte är aktiverad utanför rutan. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade lead-posten eller, om inte, varför.

Kontaktpunktsstatus (kontakt): Det här är ett diagnostiskt fält som relaterar till en funktion som inte är påslagen. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade kontaktposten eller, om inte, varför.

Touchpoint-status (säljprojekt): Det här är ett diagnostiskt fält som relaterar till en funktion som inte är aktiverad utanför rutan. Vi använder det här för att förstå om en slutpunkt skapades mot den relaterade säljprojektsposten eller, om inte, varför.

Statusdatum för kontaktpunkt: Detta är det datum då diagnosfälten fylldes i.

Buyer Touchpoint Date: This is related to the [!UICONTROL Bulk Update Touchpoint date] från Campaign-objektet. När det används använder vi det definierade slutpunktsdatumet för kampanjmedlemmen.

OnCampaignMemberDelete: Utanför paketet, [!DNL Salesforce] visas inte när Campaign-medlemmar tas bort, vilket kan orsaka problem med korrekt attribueringsrapportering. När en kampanjmedlem tas bort aktiveras detta för att informera [!DNL Marketo Measure] för att ta bort kontaktytor som är relaterade till den icke-befintliga kampanjmedlemmen.

## Lead {#lead}

Fältet Bizible Account används för att mappa lead till konto för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Konto {#account-1}

Detta används för vår lead-to-account-mappning för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Möjligheter {#opportunity}

[!DNL Marketo Measure] Affärsmöjlighet: Det här fältet används i scenariot där ett anpassat beloppsfält används för affärsmöjligheten. Vi mappar det anpassade fältvärdet till [!DNL Marketo Measure] Affärsmöjlighet med hjälp av ett arbetsflöde och läs sedan det här fältet för våra intäktsattribueringsfält i Buyer Attribution Touchpoint-objektet.

## Aktivitet {#activity}

BizibleID: Det här är till för att vi ska kunna koppla en kontaktyta till aktiviteter för vår aktivitetsattribuering och integrering av calltracking-mätvärden.

Buyer Touchpoint Date: Det här är ett fält som kan fyllas i via ett arbetsflöde och användas som datum för aktivitetsattribuering. Det fylls i så att vår integrering med anropsmätvärden kan veta när interaktionen inträffade.
