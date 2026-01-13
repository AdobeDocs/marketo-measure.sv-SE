---
description: '[!DNL Marketo Measure] fält i  [!DNL Salesforce] Standard-objekt - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] fält i  [!DNL Salesforce] standardobjekt'
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# [!DNL Marketo Measure] fält i [!DNL Salesforce] standardobjekt {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Lär dig mer om de olika [!DNL Marketo Measure] fälten som läggs till i [!DNL Salesforce] standardobjekt.

## Konto {#account}

Predictive Engagement Score: Det här fältet används med funktionen ABM för att ge en poäng som relaterar till hur engagerat kontot är och som tar hänsyn till många faktorer som t.ex. senaste sidvisningar, hur många kontakter som är kopplade till kontot, om det finns en stängd popup, osv.

## Campaign {#campaign}

Endast fyra fält har lagts till, en knapp och en valideringsregel.

Unikt ID: Det här fältet används internt för oss för att spåra de olika kampanjer som synkroniseras med [!DNL Marketo Measure].

Aktivera Buyer Touchpoints: Det här fältet är till för den faktiska synkroniseringen av kampanjer för offlineattribuering och historiska data.

Startdatum för kontaktyta: Det här fältet används för att ange ett startdatum när kontaktytor ska tillämpas på historiska kampanjer.

Slutdatum för slutpunkt: Det här fältet används för att ange ett slutdatum för användning av kontaktytor på historiska kampanjer. Ett vanligt exempel är om digitala kampanjer inkluderas före [!DNL Marketo Measure] och sedan anger slutdatumet som den dag skriptet tillämpades.

Uppdatera slutpunktsdatum gruppvis (knapp): Den här knappen används för att hantera slutpunktsdatumet för kampanjmedlemmarna när kampanjen synkroniseras, eftersom vi refererar till antingen kampanjmedlemskapsdatumet eller det första svarsdatumet i rutan. Om dessa datumfält inte är en korrekt representation av det faktiska beröringspunktsdatumet använder vi den här knappen för att ange kontaktpunktsdatumet.

Uppdatera [!DNL Marketo Measure]-attribut (verifieringsregel): Den här regeln har tagits bort efter paketversion 6.0.

## Kampanjmedlem {#campaign-member}

Det finns fem fält och en Apex-utlösare har lagts till i paketet.

Touchpoint Status (Lead): Detta är ett diagnostiskt fält som relaterar till en funktion som inte är aktiverad utanför rutan. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade lead-posten eller, om inte, varför.

Kontaktpunktsstatus (kontakt): Det här är ett diagnostiskt fält som relaterar till en funktion som inte är påslagen. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade kontaktposten eller, om inte, varför.

Touchpoint-status (säljprojekt): Det här är ett diagnostiskt fält som relaterar till en funktion som inte är aktiverad utanför rutan. Vi använder det här för att förstå om en slutpunkt skapades mot den relaterade säljprojektsposten eller, om inte, varför.

Statusdatum för kontaktpunkt: Detta är det datum då diagnosfälten fylldes i.

Buyer Touchpoint Date: Detta är relaterat till knappen [!UICONTROL Bulk Update Touchpoint date] från Campaign-objektet. När det används använder vi det definierade slutpunktsdatumet för kampanjmedlemmen.

OnCampaignMemberDelete: Utanför rutan visas inte [!DNL Salesforce] när Campaign-medlemmar tas bort, vilket kan orsaka problem med korrekt attribueringsrapportering. När en kampanjmedlem tas bort, aktiveras detta för att informera [!DNL Marketo Measure] om att ta bort de kontaktytor som är relaterade till den icke-befintliga kampanjmedlemmen.

## Lead {#lead}

Fältet Bizible Account används för att mappa lead till konto för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Konto {#account-1}

Detta används för vår lead-to-account-mappning för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Möjligheter {#opportunity}

[!DNL Marketo Measure] Affärsmöjlighetsbelopp: Det här fältet används i scenariot där ett anpassat beloppsfält används för affärsmöjligheten. Vi mappar det anpassade fältvärdet till [!DNL Marketo Measure] säljprojektsbelopp med ett arbetsflöde och läser sedan det här fältet för våra intäktsattribueringsfält på Buyer Attribution Touchpoint-objektet.

## Aktivitet {#activity}

BizibleID: Det här är till för att vi ska kunna koppla en kontaktyta till aktiviteter för vår aktivitetsattribuering och integrering av calltracking-mätvärden.

Buyer Touchpoint Date: Det här är ett fält som kan fyllas i via ett arbetsflöde och användas som datum för aktivitetsattribuering. Det fylls i så att vår integrering med anropsmätvärden kan veta när interaktionen inträffade.
