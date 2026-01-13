---
description: Lägger till [!DNL Marketo Measure] skript - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] skript
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---


# Lägger till [!DNL Marketo Measure] skript {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript som du vill spåra av [!DNL Marketo Measure] bör läggas till i alla webbegenskaper så snart som möjligt. När JavaScript har distribuerats börjar [!DNL Marketo Measure] samla in dina digitala data. I den här artikeln beskrivs metoderna för att distribuera [!DNL Marketo Measure] JavaScript och andra överväganden.

>[!NOTE]
>Kontrollera att du har [gjort anspråk på alla lämpliga domäner i  [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} förutom att distribuera [!DNL Marketo Measure] JavaScript.

När du börjar med [!DNL Marketo Measure] finns det två sätt att lägga till JavaScript [!DNL Marketo Measure] på din webbplats:

* Hård kodning
* Tag Management Systems

## Hård kodning {#hard-coding}

Vi rekommenderar starkt att du kodar [!DNL Marketo Measure] JavaScript för dina webbegenskaper. Om du vill hårdkoda skriptet måste du placera skriptet före den avslutande `</head>` på alla sidor på webbplatsen.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Om du hårdkodar JavaScript i `<head>` på sidorna ser du till att skriptet [!DNL Marketo Measure] läses in först och att hänvisningsinformationen inte missas. JavaScript [!DNL Marketo Measure] läses in asynkront. Vid hårdkodning måste JavaScript läggas till manuellt i Marketing Automation.

>[!TIP]
>Lär dig hur du kontrollerar att skriptet är [GDPR-kompatibelt](/help/security/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Tag Management Systems {#tag-management-systems}

Om det inte går att lägga till [!DNL Marketo Measure] JavaScript via maskinkodning är ett annat alternativ att lägga till [!DNL Marketo Measure]-skriptet med ett Tag Management-system som [!DNL Google Tag Manager] (GTM) eller Tealium.

Om du använder tagghanteringssystem för att distribuera [!DNL Marketo Measure] JS kan det resultera i en potentiell dataförlust på 5-10 % på grund av fördröjning vid skriptinläsning. Om tagghanteringsverktyget inte läses in tillräckligt snabbt kan [!DNL Marketo Measure] JS inte heller läsas in tillräckligt snabbt och kan förlora den första referensinformationen.

Ett vanligt tillvägagångssätt är att distribuera [!DNL Marketo Measure] JS via ett tagghanteringsverktyg tills timing/resource är bättre för att gå över till hårdkodning.

Om du vill lägga till [!DNL Marketo Measure]-skript via en tagghanteringslösning måste du skapa en tagg och lägga till din JavaScript i den. Använd den här taggen på alla sidor på webbplatsen som du vill spåra.

[!DNL Marketo Measure] rekommenderar att alla sidvyer orsakar fel i taggen. Det är också bäst att ge [!DNL Marketo Measure] högsta prioritet i den inledande ordningen och se till att det inte finns några synkrona skript framför taggen [!DNL Marketo Measure] för att säkerställa högsta datakvalitet.

Mer information finns [här](/help/marketo-measure-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Ytterligare överväganden {#additional-considerations}

[!DNL Marketo Measure] JavaScript är domänbaserat, så det kan automatiskt hantera alla underdomäner så länge som JavaScript finns på sidorna och rotdomänen är densamma som den domän som användes för att skapa Marketo Measure-kontot.

Om du använder separata eller internationella domäner måste du dock informera din [!DNL Marketo Measure]-konsult. Domänerna måste läggas till manuellt i ditt konto i [!DNL Marketo Measure]-änden så att [!DNL Marketo Measure] kan koppla de ytterligare domänernas data till ditt konto. Skicka därför alla separata/internationella domäner till din [!DNL Marketo Measure]-konsult.

Om du använder någon tredjepartssida kan du diskutera ditt användningsfall med din [!DNL Marketo Measure]-konsult. I allmänhet vill du veta om du kan lägga till en anpassad version av [!DNL Marketo Measure] JavaScript för att spåra de sidorna om det är lämpligt. Om detta inte är möjligt kommer spårning via CRM Campaign-kontaktytor att utforskas med din [!DNL Marketo Measure]-konsult.

Har du några formulär som INTE ska spåras av [!DNL Marketo Measure] eftersom de inte nödvändigtvis är lämpliga för attribuering (t.ex. för att avbryta prenumerationer, kundinloggningar och så vidare)? I så fall vill du lägga till exkluderingskoden [i den här artikeln](/help/marketo-measure-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} i varje formulär

Har du några sidor som inte är säkra? Du bör skydda dem när du navigerar mellan en säker/osäker sida och avbryter spårningssessionen.

Se till att du har en konversation med ditt webbteam så att de vet att [!DNL Marketo Measure] JavaScript alltid ska finnas på rätt webbegenskaper. Om nya sidor/formulär/platser introduceras måste du se till att distributionen av [!DNL Marketo Measure] JavaScript ingår i protokollet.

Om en [!DNL Web Application Firewall (WAF)]-varning utlöses under JavaScript-konfigurationen kan användare antingen inaktivera den WAF-regeln eller tillåtslista cookies, som i följande exempel:

![Exempel på WAF-varningsmeddelande för Marketo Measure-skriptet](assets/adding-marketo-measure-script-1.png)

## Forms to Pay Extra Attention To {#forms-to-pay-extra-attention-to}

**Skicka flera formulär**

* Problem: Om du har flera länkade formulär som en del av en enda formulärinlämning, är det möjligt att det första formuläret genererar en kontaktyta även om det fullständiga formuläret inte har skickats.
* Lösning: Du måste tvinga ett av formulären att rapportera användaren till [!DNL Marketo Measure] baserat på cachelagrade data och diskutera övergivningsmetoder. Vanligtvis kan [rapportera användarkod](/help/marketo-measure-tracking/ajax-form-handling.md){target="_blank"} lösa detta.

**Kontoinloggning (inte skapande)**

* Problem: [!DNL Marketo Measure] rekommenderar att du inte skapar kontaktytor för efterföljande kontoinloggningar eftersom dessa tenderar att späda ut attribueringsartikeln.
* Lösning: Lägg till undantagskod i inloggningsformuläret för konto/kund/partner.

>[!NOTE]
>Vi rekommenderar att du skapar en kontaktyta för att skapa ett konto eller en testversion.

**Ladda ned resurs**

* Problem: Om dina resurser är grupperade spåras hämtningarna i [!DNL Marketo Measure] när formuläret fylls i. Om resurserna inte är grupperade finns det begränsningar för vad vi kan rapportera om utan anpassning.
* Lösning: Hämta resursen om du vill att den ska spåras av [!DNL Marketo Measure] JavaScript. Om detta inte är ett alternativ och du fortfarande vill ha en kontaktyta för det, bör du överväga att synkronisera en CRM-kampanj i stället.

**iFrames**

* Problem: iFrames fungerar i stort sett som sidor på sidor.
* Lösning: JS-servern [!DNL Marketo Measure] måste distribueras direkt i iFrame-huvudet för att vi ska kunna koppla till formuläret korrekt.

**Ljuslådor**

* Ljuslådor är vanligtvis popup-fönster som innehåller iFrames
* Lösning: JS [!DNL Marketo Measure] måste distribueras inom huvudet för den värdbaserade iFrame.

**Flera formulär på en sida**

* Problem: Om det finns flera formulär på en sida kanske du inte kan se vilket formulär som fylldes i med fältet [!DNL Marketo Measure] Formulär-URL.
* Lösning: Om du måste veta vilket formulär som fylldes i kan du utforska hur du konfigurerar dynamiska URL-hashar med webbteamet.

**Forms ordnade i `<div>` format**

* Problem: [!DNL Marketo Measure] JS har en svår tid på sig att identifiera formulär som är organiserade i formatet `<div>` så att anpassad kod kan behövas.
* Lösning: Dessa [rapportanvändarmallar](/help/marketo-measure-tracking/ajax-form-handling.md){target="_blank"} kan användas av ditt webbdev-team för att lägga till den kod som behövs.

**Chatt**

* Problem: Om du använder en chattleverantör kan särskild hantering behövas.
* Lösning: [!DNL Marketo Measure] integreras med Drift, Olark, Livechat, LivePerson och SnapEngage. Alla andra plattformar måste spåras via medlemskap i CRM-kampanjer.

**Andra domänen**

* Problem: [!DNL Marketo Measure] JavaScript är domänspecifikt, så extra åtgärder måste vidtas för alla separata eller internationella domäner. [!DNL Marketo Measure] JS kan hantera underdomäner på samma rotdomän.
* Lösning: Om du äger flera rotdomäner som du vill ska spåras av [!DNL Marketo Measure] måste du lägga till JS i domänerna och meddela din [!DNL Marketo Measure]-konsult vilka domäner som ska kopplas till ditt [!DNL Marketo Measure]-konto manuellt.

## Testar [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Din [!DNL Marketo Measure]-konsult hjälper dig att hitta webbplatsen för att säkerställa att [!DNL Marketo Measure] JavaScript finns på alla sidor. En del av testningen är att en del formulärfyllningar skickas in med tydligt angivna testdetaljer för att säkerställa att spårningen returneras korrekt.

Din [!DNL Marketo Measure]-konsult är emellertid inte så bekant med din webbplats som ditt webbteam är. Därför är det mycket viktigt att webbteamet eller andra behöriga team noggrant kontrollerar webbplatsen, särskilt om komplexa formulär används, som de som nämns ovan. Teamet ansvarar för att säkerställa att alla nödvändiga webbegenskaper spåras korrekt, men om du är medveten om komplicerade formulär eller situationer kan du be din [!DNL Marketo Measure]-konsult om hjälp med att testa.

Så här testar du ett formulär själv:

1. Använd alltid en inkognitiv webbläsare eller rensa cacheminnet mellan varje formulärtest OCH använd olika e-postadresser varje gång.

   a. Ett bra tillvägagångssätt är att använda ett falskt e-postmeddelande som innehåller något som tyder på att det är ett test och tidpunkten på dagen. Till exempel: testing830am@test.com.

1. Registrera URL-adressen till sidan som du skickar formuläret och det e-postmeddelande som används.

1. Leta reda på den post som skapats i CRM (lead eller kontakt) för den formuläröverföringen och kontrollera att en kontaktyta skapats på rätt sätt.

   a. Du kan använda en [!DNL Marketo Measure]-arkivrapport, till exempel Leads med Buyer Touchpoints, eller titta på sidlayouten Lead/Kontakt om du valde att uppdatera sidlayouten med [!DNL Marketo Measure] information.

   b. Detta kan ta lite tid innan data bearbetas.
