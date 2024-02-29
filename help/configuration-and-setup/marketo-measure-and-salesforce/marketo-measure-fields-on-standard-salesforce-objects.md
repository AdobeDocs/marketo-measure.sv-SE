---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 0%

---

# [!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Läs om de olika [!DNL Marketo Measure] fält som lagts till i [!DNL Salesforce] standardobjekt.

## Konto {#account}

Predictive Engagement Score: Det här fältet används med funktionen ABM för att ge en poäng som relaterar till hur engagerat kontot är och som tar hänsyn till många faktorer som t.ex. senaste sidvisningar, hur många kontakter som är kopplade till kontot, om det finns en stängd popup, osv.

## Case {#case}

Vi lägger till fält i Case-objektet som är relaterade till beröringspunkterna First touch och Lead Creation. Detta är till för kunder som använder Case-objektet i stället för lead eller kontakt och även har som syfte att på ett annat sätt visa data ifall kunden inte ville att vi skulle skapa kontaktpunktsposter.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Detta är marknadsföringskanalen för den första beröringsinteraktionen.

Marknadsföringskanal (LC): Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Campaign of the first touch interaction.

Namn på annonskampanj (LC): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Kampanj för [!UICONTROL lead creation] pekinteraktion.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landningssida (LC): Detta är landningssidan för [!UICONTROL lead creation] pekinteraktion.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Touchpoint Date (LC): Detta är datumet då pekinteraktionen för att skapa lead skapades.

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

Datum för köparens kontaktpunkt: Detta är relaterat till [!UICONTROL Bulk Update Touchpoint date] från Campaign-objektet. När det används använder vi det definierade slutpunktsdatumet för kampanjmedlemmen.

OnCampaignMemberDelete: Utanför paketet, [!DNL Salesforce] visas inte när Campaign-medlemmar tas bort, vilket kan orsaka problem med korrekt attribueringsrapportering. När en kampanjmedlem tas bort aktiveras detta för att informera [!DNL Marketo Measure] för att ta bort kontaktytor som är relaterade till den icke-befintliga kampanjmedlemmen.

## Kontakt {#contact}

Vi lägger till fält i kontaktobjektet som är relaterade till milstolparna Första beröringen och Lead Creation. Detta är till för kunder som hellre vill att attribuering ska rapporteras direkt till fält istället för att skapa Touchpoint-poster. De flesta av våra kunder följer med till posterrutten för slutpunkten, men använder även dessa fält inom deras automatiseringsplattform.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Detta är marknadsföringskanalen för den första beröringsinteraktionen.

Marknadsföringskanal (LC): Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Campaign of the first touch interaction.

Namn på annonskampanj (LC): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Kampanj för [!UICONTROL lead creation] pekinteraktion.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landningssida (LC): Detta är landningssidan för [!UICONTROL lead creation] pekinteraktion.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Touchpoint Date (LC): Detta är datumet då pekinteraktionen för att skapa lead skapades.

BizibleID: Detta används i relation till vår aktivitetsattribuering och calltrackingmetrics-integrering för kontaktassociation till kontaktytan.

## Lead {#lead}

Vi lägger till fält i Lead-objektet som hör till beröringspunkterna First touch och Lead Creation. Detta är till för kunder som hellre vill att attribuering ska rapporteras direkt till fält istället för att skapa Touchpoint-poster. De flesta av våra kunder följer med till posterrutten för slutpunkten, men använder även dessa fält inom deras automatiseringsplattform.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Detta är marknadsföringskanalen för den första beröringsinteraktionen.

Marknadsföringskanal (LC): Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Campaign of the first touch interaction.

Namn på annonskampanj (LC): Detta är UTM-kampanjen, annonskampanjen från annonsnätverken, eller [!DNL Salesforce] Kampanj för att skapa beröringsinteraktion för lead.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landing Page (LC): Det här är landningssidan för pekinteraktionen för att skapa leads.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Touchpoint Date (LC): Detta är datumet då pekinteraktionen för att skapa lead skapades.

BizibleID: Detta används i relation till vår aktivitetsattribution och calltrackingmetrics-integrering för lead-associationen till kontaktytan.

## Konto {#account-1}

Detta används för vår lead-to-account-mappning för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Möjligheter {#opportunity}

[!DNL Marketo Measure] Affärsmöjlighet: Det här fältet används i scenariot där ett anpassat beloppsfält används för affärsmöjligheten. Vi mappar det anpassade fältvärdet till [!DNL Marketo Measure] Affärsmöjlighet med hjälp av ett arbetsflöde och läs sedan det här fältet för våra fält för intäktsattribuering i Buyer Attribution Touchpoint-objektet.

## Aktivitet {#activity}

BizibleID: Det här är till för att vi ska kunna koppla en kontaktyta till aktiviteter för vår aktivitetsattribuering och integrering av calltracking-mätvärden.

Buyer Touchpoint-datum: Detta är ett fält som kan fyllas i via ett arbetsflöde och användas som datum för aktivitetsattribuering. Det fylls i så att vår integrering med anropsmätvärden kan veta när interaktionen inträffade.
