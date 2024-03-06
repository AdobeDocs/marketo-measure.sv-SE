---
unique-page-id: 18874795
description: Lägger till [!DNL Marketo Measure] Skript - [!DNL Marketo Measure]
title: Lägger till [!DNL Marketo Measure] Skript
exl-id: f8773037-04d7-4308-ba04-440e9b990d92
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---

# Lägger till [!DNL Marketo Measure] Skript {#adding-marketo-measure-script}

[!DNL Marketo Measure] JavaScript som du vill spåra av [!DNL Marketo Measure] ska läggas till i alla webbegenskaper så snart som möjligt. När JavaScript har distribuerats [!DNL Marketo Measure] börjar samla in digitala data. I den här artikeln beskrivs metoderna för distribution [!DNL Marketo Measure] JavaScript och andra överväganden.

>[!NOTE]
>
>Se till att du [har gjort anspråk på alla lämpliga domäner i [!DNL Adobe Admin Console]](/help/marketo-measure-and-adobe/domain-management.md){target="_blank"} förutom att distribuera [!DNL Marketo Measure] JavaScript.

När du börjar med [!DNL Marketo Measure]kan du lägga till [!DNL Marketo Measure] JavaScript till din webbplats:

* Hård kodning
* Tag Management Systems

## Hård kodning {#hard-coding}

Vi rekommenderar hårdkodning som en god praxis [!DNL Marketo Measure] JavaScript i webbegenskaperna. Om du vill hårdkoda skriptet måste du placera skriptet före slutet `</head>` på alla sidor på webbplatsen.

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async=""></script>`

Maskinkodning av JavaScript i `<head>` på sidorna säkerställer att [!DNL Marketo Measure] Skriptet läses in först och hänvisningsinformationen saknas inte. The [!DNL Marketo Measure] JavaScript läses in asynkront. Om det hårdkodas måste JavaScript läggas till manuellt i Marketing Automation.

>[!TIP]
>
>Lär dig hur du kontrollerar att skriptet är [GDPR-kompatibel](/help/security-and-compliance/compliance-related-resources/ensuring-consent-for-gdpr-in-marketo-measure-js.md){target="_blank"}.

## Tag Management Systems {#tag-management-systems}

Om du lägger till [!DNL Marketo Measure] JavaScript via hårdkodning är inte möjligt. Ett annat alternativ är att lägga till [!DNL Marketo Measure] skript med ett Tag Management-system som [!DNL Google Tag Manager] (GTM) eller Team.

Använda tagghanteringssystem för driftsättning [!DNL Marketo Measure] JS kan resultera i en potentiell 5-10-procentig dataförlust på grund av fördröjning vid skriptinläsning. Om tagghanteringsverktyget inte läses in tillräckligt snabbt, [!DNL Marketo Measure] JS kan inte heller läsa in tillräckligt snabbt och kan förlora den första referensinformationen.

Ett vanligt tillvägagångssätt är att driftsätta [!DNL Marketo Measure] JS via ett tagghanteringsverktyg tills timing/resurser är bättre för att gå över till hårdkodning.

Lägg till [!DNL Marketo Measure] genom en tagghanteringslösning måste du skapa en tagg och lägga till vårt JavaScript i den. Använd den här taggen på alla sidor på webbplatsen som du vill spåra.

[!DNL Marketo Measure] rekommenderar att alla sidvyer orsakar att taggen aktiveras. Dessutom är det bäst att ge [!DNL Marketo Measure] högsta prioritet i den inledande ordningen och se till att det inte finns några synkrona skript framför [!DNL Marketo Measure] -taggen för att säkerställa högsta datakvalitet.

Mer information kan [hittades här](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md){target="_blank"}.

## Ytterligare överväganden {#additional-considerations}

[!DNL Marketo Measure] JavaScript är domänbaserat, så det kan automatiskt hantera alla underdomäner så länge som JavaScript finns på sidorna och rotdomänen är densamma som den domän som används för att skapa Marketo Measure-kontot.

Om du använder en separat eller internationell domän måste du dock se till att [!DNL Marketo Measure] Konsulten vet. Domänerna måste läggas till manuellt i ditt konto på [!DNL Marketo Measure] avsluta så att [!DNL Marketo Measure] kan koppla data från ytterligare domäner till ditt konto. Så skicka alla separata/internationella domäner till [!DNL Marketo Measure] Konsult.

Om du använder någon tredjepartssida kan du diskutera din användning med [!DNL Marketo Measure] Konsult. Vanligtvis vill du veta om du kan lägga till en anpassad version av [!DNL Marketo Measure] JavaScript för att spåra sidorna om det är lämpligt. Om detta inte är möjligt kommer spårning via CRM Campaign-kontaktytorna att utforskas med [!DNL Marketo Measure] Konsult.

Har du formulär som INTE ska spåras av [!DNL Marketo Measure] eftersom de inte nödvändigtvis är lämpliga för attribuering (t.ex. för att avbeställa prenumerationsblanketter, kundinloggningar och så vidare)? I så fall vill du lägga till exkluderingskoden [i den här artikeln](/help/marketo-measure-tracking/setting-up-tracking/excluding-marketo-measure-from-specific-forms.md){target="_blank"} till varje formulär

Har du några sidor som inte är säkra? Du bör skydda dem när du navigerar mellan en säker/osäker sida och avbryter spårningssessionen.

Kom ihåg att ha en konversation med webbteamet så att de vet [!DNL Marketo Measure] JavaScript ska alltid finnas på rätt webbegenskaper. Om nya sidor/formulär/platser introduceras måste du se till att distribuera [!DNL Marketo Measure] JavaScript är en del av protokollet.

Om en [!DNL Web Application Firewall (WAF)] -varningen aktiveras under JavaScript-konfigurationen, kan användare antingen inaktivera den WAF-regeln eller tillåtslista cookies, som i följande exempel:

![](assets/adding-marketo-measure-script-1.png)

## Forms to Pay Extra Attention To {#forms-to-pay-extra-attention-to}

**Inlämning av flera formulär**

* Problem: Om du har flera länkade formulär som en del av en enda formulärinlämning, är det möjligt att det första formuläret genererar en kontaktyta även om det fullständiga formuläret inte har skickats.
* Lösning: Du måste tvinga ett av formulären att rapportera användaren till [!DNL Marketo Measure] baserat på cachelagrade data och diskutera övergivningsmetoder. I allmänhet [rapportanvändarkod](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} kan lösa det här.

**Kontoinloggning (inte skapande)**

* Problem: [!DNL Marketo Measure] rekommenderar att du inte skapar kontaktytor för efterföljande kontoinloggningar eftersom dessa tenderar att späda ut attribueringsartikeln.
* Lösning: Lägg till undantagskod i inloggningsformuläret för konto/kund/partner.

>[!NOTE]
>
>Vi rekommenderar att du skapar en kontaktyta för att skapa ett konto eller en testversion.

**Ladda ned resurs**

* Problem: Om dina resurser är grupperade, [!DNL Marketo Measure] spårar hämtningar när formulär fylls i. Om resurserna inte är grupperade finns det begränsningar för vad vi kan rapportera om utan anpassning.
* Lösning: Hämta resursen om du vill att den ska spåras av [!DNL Marketo Measure] JavaScript. Om detta inte är ett alternativ och du fortfarande vill ha en kontaktyta för det, bör du överväga att synkronisera en CRM-kampanj i stället.

**iFrames**

* Problem: iFrames fungerar i stort sett som sidor på sidor.
* Lösning: [!DNL Marketo Measure] JS måste distribueras direkt i iFrame-huvudet för att vi ska kunna bifoga till formuläret korrekt.

**Ljuslådor**

* Ljuslådor är vanligtvis popup-fönster som innehåller iFrames
* Lösning: [!DNL Marketo Measure] JS måste distribueras inom rubriken för den värdbaserade iFrame.

**Flera formulär på en sida**

* Problem: Om det finns flera formulär på en sida kanske du inte kan se vilket formulär som fylldes i med [!DNL Marketo Measure] Formulär-URL-fält.
* Lösning: Om du måste veta vilket formulär som fylldes i kan du utforska hur du konfigurerar dynamiska URL-hashar med webbteamet.

**Forms ordnade i `<div>` format**

* Problem: [!DNL Marketo Measure] JS har svårt att identifiera formulär som ordnats i `<div>` så att man kan behöva skapa egen kod.
* Lösning: [rapportanvändarmallar](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-to-different-form-providers/ajax-form-handling.md){target="_blank"} kan användas av ditt webbutvecklingsteam för att lägga till den kod som behövs.

**Chatt**

* Problem: Om du använder en chattleverantör kan särskild hantering behövas.
* Lösning: [!DNL Marketo Measure] integreras med Drift, Olark, Livechat, LivePerson och SnapEngage. Alla andra plattformar måste spåras via medlemskap i CRM-kampanjer.

**Andra domänen**

* Problem: [!DNL Marketo Measure] JavaScript är domänspecifikt, så extra steg måste vidtas för alla separata eller internationella domäner. [!DNL Marketo Measure] JS kan hantera underdomäner på samma rotdomän.
* Lösning: Om du äger flera rotdomäner vill du att de ska spåras av [!DNL Marketo Measure] se till att lägga till JS i domänerna OCH låta [!DNL Marketo Measure] Konsulten vet vilka domäner som manuellt ska kopplas till din [!DNL Marketo Measure] konto.

## Testning [!DNL Marketo Measure] JavaScript {#testing-marketo-measure-javascript}

Dina [!DNL Marketo Measure] Konsulten hjälper er att hitta rätt webbplats för att säkerställa att [!DNL Marketo Measure] JavaScript finns på alla sidor. En del av testningen är att en del formulärfyllningar skickas in med tydligt angivna testdetaljer för att säkerställa att spårningen returneras korrekt.

Men [!DNL Marketo Measure] Konsulten känner troligen inte till din webbplats lika bra som ditt webbteam. Därför är det mycket viktigt att webbteamet eller andra behöriga team noggrant kontrollerar webbplatsen, särskilt om komplexa formulär används, som de som nämns ovan. Teamet ansvarar för att alla webbegenskaper spåras korrekt, men om du känner till komplexa formulär eller situationer kan du fråga [!DNL Marketo Measure] Konsult för hjälp med testning.

Så här testar du ett formulär själv:

1. Använd alltid en inkognitiv webbläsare eller rensa cacheminnet mellan varje formulärtest OCH använd olika e-postadresser varje gång.

   a. Ett bra tillvägagångssätt är att använda ett falskt e-postmeddelande som innehåller något som tyder på att det är ett test och tidpunkten på dagen. Till exempel: testing830am@test.com.

1. Registrera URL-adressen till sidan som du skickar formuläret och det e-postmeddelande som används.

1. Leta reda på den post som skapats i CRM (lead eller kontakt) för den formuläröverföringen och kontrollera att en kontaktyta skapats på rätt sätt.

   a. Använd en [!DNL Marketo Measure] Stock-rapport, till exempel Leads med Buyer Touchpoints, eller se sidlayouten Lead/Kontakt om du valde att uppdatera sidlayouten med [!DNL Marketo Measure] information.

   b. Detta kan ta lite tid innan data bearbetas.
