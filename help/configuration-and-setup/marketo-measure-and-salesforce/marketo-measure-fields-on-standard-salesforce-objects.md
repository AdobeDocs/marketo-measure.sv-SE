---
unique-page-id: 18874574
description: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt"
exl-id: c9d5254f-06bd-4813-bb29-1a4955b37041
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 0%

---

# [!DNL Marketo Measure] Fält i Standard [!DNL Salesforce] Objekt {#marketo-measure-fields-on-standard-salesforce-objects}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Läs om de olika [!DNL Marketo Measure] fält som lagts till i [!DNL Salesforce] standardobjekt.

## Konto {#account}

Predictive Engagement Score: Det här fältet används tillsammans med funktionen ABM för att ge en poäng som relaterar till hur engagerat kontot är och som tar hänsyn till många faktorer som t.ex. senaste sidvisningar, hur många kontakter som är kopplade till kontot, om det finns ett stängt fönster osv.

## Skiftläge {#case}

Vi lägger till fält i Case-objektet som är relaterade till beröringspunkterna First touch och Lead Creation. Detta är till för kunder som använder Case-objektet i stället för lead eller kontakt och även har som syfte att på ett annat sätt visa data ifall kunden inte ville att vi skulle skapa kontaktpunktsposter.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Det här är marknadsföringskanalen i den första beröringsinteraktionen.

Marknadsföringskanal: Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för den första beröringsinteraktionen.

Namn på annonskampanj (LC): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för [!UICONTROL lead creation] pekinteraktion.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landningssida (LC): Detta är landningssidan för [!UICONTROL lead creation] pekinteraktion.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Kontaktpunktsdatum (LC): Det här är datumet för den beröringsinteraktion som har skapats för lead.

## Campaign {#campaign}

Endast fyra fält har lagts till, en knapp och en valideringsregel.

Unikt ID: Det här fältet används internt av oss för att spåra de olika kampanjer som synkroniseras med [!DNL Marketo Measure].

Aktivera slutpunkter för köpare: Det här fältet är avsett för den faktiska synkroniseringen av kampanjer för offlineattribuering och historiska data.

Startdatum för kontaktpunkt: Det här fältet används för att ange ett startdatum när kontaktytor ska tillämpas på historiska kampanjer.

Slutdatum för slutpunkt: Det här fältet används för att ange ett slutdatum för användning av kontaktytor på historiska kampanjer. Ett vanligt exempel är digitala kampanjer innan[!DNL Marketo Measure] och sedan ange slutdatumet som den dag skriptet tillämpades.

Uppdatera Touchpoint-datum gruppvis (knapp): Den här knappen används för att hantera slutpunktsdatumet för Campaign-medlemmar när Campaign synkroniseras, eftersom vi refererar till antingen kampanjmedlemskapsdatumet eller det första svarsdatumet i paketet. Om dessa datumfält inte är en korrekt representation av det faktiska beröringspunktsdatumet använder vi den här knappen för att ange kontaktpunktsdatumet.

Uppdatera [!DNL Marketo Measure] Attribution (valideringsregel): Den här regeln har tagits bort efter paketversion 6.0.

## Kampanjmedlem {#campaign-member}

Det finns fem fält och en Apex-utlösare har lagts till i paketet.

Status för kontaktpunkt (lead): Det här är ett diagnostiskt fält som är relaterat till en funktion som inte är påslagen. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade lead-posten eller, om inte, varför.

Status för kontaktpunkt (kontakt): Det här är ett diagnostiskt fält som är relaterat till en funktion som inte är påslagen. Vi använder det här för att förstå om en kontaktpunkt skapades mot den relaterade kontaktposten eller, om inte, varför.

Status för kontaktpunkt (säljprojekt): Det här är ett diagnostiskt fält som är relaterat till en funktion som inte är påslagen. Vi använder det här för att förstå om en slutpunkt skapades mot den relaterade säljprojektsposten eller, om inte, varför.

Status för kontaktpunkt: Detta är det datum som diagnosfälten fylldes i.

Datum för köparens kontaktpunkt: Detta är relaterat till [!UICONTROL Bulk Update Touchpoint date] från Campaign-objektet. När det används använder vi det definierade slutpunktsdatumet för kampanjmedlemmen.

OnCampaignMemberDelete: Ut ur lådan, [!DNL Salesforce] visas inte när Campaign-medlemmar tas bort, vilket kan orsaka problem med korrekt attribueringsrapportering. När en kampanjmedlem tas bort aktiveras detta för att informera [!DNL Marketo Measure] för att ta bort kontaktytor som är relaterade till den icke-befintliga kampanjmedlemmen.

## Kontakt {#contact}

Vi lägger till fält i kontaktobjektet som är relaterade till milstolparna Första beröringen och Lead Creation. Detta är till för kunder som hellre vill att attribuering ska rapporteras direkt till fält istället för att skapa Touchpoint-poster. De flesta av våra kunder följer med till posterrutten för slutpunkten, men använder även dessa fält inom deras automatiseringsplattform.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Det här är marknadsföringskanalen i den första beröringsinteraktionen.

Marknadsföringskanal: Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för den första beröringsinteraktionen.

Namn på annonskampanj (LC): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för [!UICONTROL lead creation] pekinteraktion.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landningssida (LC): Detta är landningssidan för [!UICONTROL lead creation] pekinteraktion.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Kontaktpunktsdatum (LC): Det här är datumet för den beröringsinteraktion som har skapats för lead.

BizibleID: Detta används i relation till vår aktivitetsattribuering och integrering med anropsmätvärden för kontaktsassociationen till kontaktytan.

## Lead {#lead}

Vi lägger till fält i Lead-objektet som hör till beröringspunkterna First touch och Lead Creation. Detta är till för kunder som hellre vill att attribuering ska rapporteras direkt till fält istället för att skapa Touchpoint-poster. De flesta av våra kunder följer med till posterrutten för slutpunkten, men använder även dessa fält inom deras automatiseringsplattform.

Kontaktpunktskälla (FT): Detta är källan till den första beröringsinteraktionen.

Kontaktpunktskälla (LC): Det här är källan till beröringsinteraktionen för att skapa leads.

Marknadsföringskanal (FT): Det här är marknadsföringskanalen i den första beröringsinteraktionen.

Marknadsföringskanal: Det här är marknadsföringskanalen för pekinteraktionen för att skapa leads.

Namn på annonskampanj (FT): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för den första beröringsinteraktionen.

Namn på annonskampanj (LC): Detta är UTM Campaign, Ad Campaign från annonsnätverken, eller [!DNL Salesforce] Kampanj för att skapa beröringsinteraktion för lead.

Landningssida (FT): Det här är landningssidan för den första beröringsinteraktionen.

Landningssida (LC): Det här är landningssidan för beröringsinteraktionen för att skapa leads.

Slutpunktsdatum (FT): Detta är datumet för den första beröringsinteraktionen.

Kontaktpunktsdatum (LC): Det här är datumet för den beröringsinteraktion som har skapats för lead.

BizibleID: Detta används i relation till vår aktivitetsattribuering och calltrackingmetrics-integrering för lead-associationen till kontaktytan.

## Konto {#account-1}

Detta används för vår lead-to-account-mappning för funktionen ABM. Vi fyller i det här fältet för att skapa sökningsförhållandet mellan de två objekten.

## Möjligheter {#opportunity}

[!DNL Marketo Measure] Affärsmöjlighet: Det här fältet används i scenariot där ett anpassat beloppsfält används för affärsmöjligheten. Vi mappar det anpassade fältvärdet till [!DNL Marketo Measure] Affärsmöjlighet med hjälp av ett arbetsflöde och läs sedan det här fältet för våra fält för intäktsattribuering i Buyer Attribution Touchpoint-objektet.

## Aktivitet {#activity}

BizibleID: Det här är till för oss att relatera en kontaktyta till aktiviteter för vår aktivitetsattribuering och integrering av calltracking-mätvärden.

Datum för köparens kontaktpunkt: Det här är ett fält som kan fyllas i via ett arbetsflöde och användas som datum för aktivitetsattribuering, och som fylls i för vår integrering med anropsstatistik för att veta när interaktionen inträffade.
