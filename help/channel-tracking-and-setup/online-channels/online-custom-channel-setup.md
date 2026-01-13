---
description: Anpassad kanalkonfiguration online - [!DNL Marketo Measure]
title: Anpassad kanalinställning online
exl-id: 170ac564-6cdd-4036-abf0-b9b230bed4f7
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1294'
ht-degree: 0%

---


# Anpassad kanalinställning online {#online-custom-channel-setup}

För att få korrekt rapportering måste marknadsföringskanalerna konfigureras för att återspegla er organisations UTM-strategi. Den här guiden tar dig igenom det bästa sättet att konfigurera dina anpassade kanalregler.

## Innan du börjar {#before-you-begin}

Innan du börjar skapa kanalregler för [!DNL Marketo Measure] bör du tänka på hur era marknadsföringskampanjer är organiserade och hur de passar in i ramverket för [!DNL Marketo Measure]. Bestäm vilka kanaler, delkanaler, kampanjer och refererande webbplatser du vill spåra.

Tänk på följande:

* Organisationen kan skapa maximalt 40 anpassade marknadsföringskanaler. Detta gäller både offline- och onlinekanaler.
* Organisationen kan skapa upp till 200 underkanaler.
* Varje datainsamling, eller bucket, måste ha en egen regel (rad i kalkylbladet) för att specificera hur data ska ordnas. Var så specifik som möjligt.
* [!DNL Marketo Measure]-logiken prioriterar data i fallande ordning med början på kalkylbladets översta rad och sedan nedåt. Den läser varje bucket, eller cell, rad för rad och söker efter den första passningen. Data sorteras sedan enligt värdena i dessa bucket. Mer om detta nedan.
* Sortera inte bladet i alfabetisk ordning eftersom det stör logikreglerna.
* När filen har överförts kan du inte ändra någon av reglerna i sju dagar. [!DNL Marketo Measure] använder den här tiden för att bearbeta och uppdatera Touchpoints.

## [!DNL Marketo Measure] logik och prioriteringar {#marketo-measure-logic-and-priorities}

Det första steget är att hämta det anpassade kanalkalkylbladet från appen [!DNL Marketo Measure]. Gå till **Inställningar** på fliken **Mitt konto** och välj **Online**. Du kan antingen välja **Hämta ursprunglig mall** eller **Hämta aktuella regler**.

![Sidan Inställningar som visar konfigurationen för onlinekanalen med alternativen Hämta ursprunglig mall och Hämta aktuella regler &#x200B;](assets/1.png)

Kalkylbladet har sju kolumner:

![Anpassat kanalkalkylblad med sju kolumner: Channel, Subchannel, Campaign, Medium, Source, Landing Page och Reference Website](assets/2.png)

* **Kanal:** lägger till olika marknadsföringskanaler här
* **Delkanal:** lägger till motsvarande delkanaler här
* **Kampanj:** Lägg till kampanjnamn här, oavsett om värdet kommer från UTM-program eller Salesforce Campaigns för aktivitetsfunktionen [!DNL Marketo Measure]
* **Medium:**, medelkolumnen representerar värdet för parametern utm_medium
* **Source:** källkolumnen representerar värdet för parametern utm_source
* **Landningssida:** lägg till landningssida här
* **Refererande webbplats:** URL:er för webbplatser som refererar till trafik till dina sidor eller inbyggd [!DNL Marketo Measure]-logik (anges med hakparenteser)

Den åttonde kolumnen anger vilka regler som du inte kan ta bort från kalkylbladet med &quot;Ta inte bort&quot;. Kalkylbladets överkant har standardkanalregler som [!DNL Marketo Measure] rekommenderar att du inte ändrar eller tar bort även om du inte använder dessa kanaler. [!DNL Marketo Measure] har djupgående integreringar med de här plattformarna, så de inkluderas som standard.

Raderna representerar regler och den ordning i vilken [!DNL Marketo Measure] prioriterar data. Den första raden har prioritet över den andra raden, den andra raden har prioritet över den tredje raden och så vidare. När [!DNL Marketo Measure] avgör vilken marknadsföringskanal och underkanal som kontaktytorna ska bucklas in i, läses uppifrån och ned, från vänster till höger, tills en rad som uppfyller villkoren för kontaktytan hittas. (Om en kontaktyta har en `utm_source=Facebook` blockeras kontaktytan i Social.Facebook-kanalen på grund av regel 15 i skärmbilden).

![Kalkylblad med kanalregler som visar prioritetsordning högst upp-ned med Social.Exempel på Facebook-regel markerat](assets/3.png)

[!DNL Marketo Measure] innehåller 12 standardkanaler som du kan använda. De här kanalerna korrelerar till plattformar som [!DNL Marketo Measure] är helt integrerad med. Oavsett om du använder dem eller inte ska du inte ta bort dem. Om du använder någon av dessa plattformar, till exempel Bing Ads, men föredrar att använda en annan namnkonvention för kanalen eller underkanalen, kan du uppdatera namnet. Ett exempel visas i bilden nedan.

![Standardkanalregler som visar 12 integrerade plattformar med anpassningsbara kanal- och delkanalsnamn](assets/4.png)

Reglernas struktur är också viktig. Reglerna kan se ut som upprepad information och data som saknas, men strukturen är avsiktlig. För korrekt datasortering är det nödvändigt att mappa varje enskild källa till rätt kanal separat, även källor som delar delkanaler och kanaler. Ju mer detaljerade och detaljerade reglerna är, desto mer insiktsfulla blir resultaten. Det är i princip bäst att skriva en detaljerad regel för varje marknadsföringsarbete som du vill spåra.

Tänk på följande situation: du har andra annonser som du inte vill spåra av någon anledning, eller du får besök på webbplatsen från en välbekant kanal, men inte en välbekant källa. Den här situationen kan leda till dataförlust om [!DNL Marketo Measure] inte kan hitta rätt regel att använda för att sortera data. För att förhindra att detta händer rekommenderar [!DNL Marketo Measure] att du bryter regeln över flera rader.

Varje parameter eller komponent i regeln mappas separat till kanalen. Om [!DNL Marketo Measure] till exempel har [!DNL Facebook] data att sortera söker den efter regler som är relaterade till [!DNL Facebook]. Den skannas uppifrån och ned. I exemplet nedan skulle [!DNL Marketo Measure] förstå att för den första [!DNL Facebook]-underkanalen behöver den bara läsa källparametern för att släppa data i den regelns bucket.

![Exempel på Facebook-kanalregler visar flera rader med olika parametrar mappade till delkanaler](assets/5.png)

Nästa regel frågar bara efter parametern medium, så alla data med den parametern blockeras i den här kanalen. Till sist för [!DNL Facebook] placeras alla data som kommer från Facebooks URL i den sista Facebook-haken.

Standardkanalen Övrigt finns för att hämta data som inte uppfyller några regelvillkor. Observera att vissa av bucketerna i den andra kanalen innehåller asterisker (&#42;). Dessa asterisker representerar jokertecken som fungerar som en&quot;catch-all&quot;.

![Andra kanalregler som visar asterisker med jokertecken som&quot;catch-all&quot;-bucket för omatchade data](assets/6.png)

På grund av att logiken [!DNL Marketo Measure] fungerar uppifrån och ned bör jokerteckendlinjen, som anges med en asterisk (&#42;), placeras i slutet av regelbladet. Alla data som inte fångas eller sorteras av de andra reglerna läggs till i jokertecknet.

Nedan finns fler exempel på logik för jokertecken:

* &#42;email&#42; = innehåller &quot;email&quot;
* &#42;email = slut med &quot;email&quot;
* e-post &#42; = [!UICONTROL starts with email]

Observera dessutom att om du skapar en underkanal för en av kanalerna måste du skapa en underkanal för alla regler under den kanalen. Om du skapar en underkanal kan du alltså inte lämna resten av kolumnerna tomma.

## Konfigurera anpassade kanalregler {#setting-up-your-custom-channels-rules}

När du har bestämt hur du vill ordna och prioritera dina data är du redo att lägga till reglerna i kalkylbladet. Nedan följer några metodtips:

* Behåll reglerna så enkelt som möjligt från början. Ni kan alltid bygga vidare på reglerna medan ni går vidare.
* Lägg inte till några specialtecken i kanalnamnen (till exempel $%#&amp;&#42;@)
* Redigera inte reglerna som är kopplade till BingAds och AdWords. Dessa regler är viktiga för att lagra data som automatiskt kommer från API-integreringen [!DNL Marketo Measure] med dessa plattformar. Att ändra underkanals- och kanalnamnet så att det passar dina behov är dock inget problem.
* Ta inte bort reglerna som innehåller en&quot;Ta inte bort&quot;-anteckning.
* Organisativa sökregler placeras alltid efter [!UICONTROL Paid Search rules]
* Du kan inte skapa regler baserade på olika underdomäner.
* Om du har fler än ett värde att lägga till i en cell i kalkylbladet måste du separera värdena med semikolon `;`. Inga kommatecken eller mellanslag.
* Du behöver inte lägga till dot-com (.com) i slutet av den refererande URL:en.
* När du lägger till en refererande URL-adress ska du inte placera den inom hakparenteser som de andra API-relaterade reglerna.

## Överför regler för anpassade kanaler {#uploading-your-custom-channels-rules}

Kontrollera att alla nya kanal- och delkanalsvärden som du lägger till i CSV-filen redan har lagts till i kanalinställningsområdet för ditt Bizible-konto. Dubbelkontrollera alla kanal- och delkanalsnamn i CSV-filen med kanalinställningsområdet för ditt [!DNL Marketo Measure]-konto. Kontrollera om det finns kommatecken och blanksteg.

Om du får ett felmeddelande under överföringen kan du åtgärda problemet och ladda upp igen. Om inget felmeddelande tas emot klickar du på **Spara och bearbeta** längst ned på sidan.
