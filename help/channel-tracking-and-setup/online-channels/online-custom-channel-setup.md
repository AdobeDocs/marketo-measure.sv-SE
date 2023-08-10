---
unique-page-id: 18874596
description: Anpassad kanalkonfiguration online - [!DNL Marketo Measure] - Produktdokumentation
title: Anpassad kanalinställning online
exl-id: 170ac564-6cdd-4036-abf0-b9b230bed4f7
feature: Channels
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 0%

---

# Anpassad kanalinställning online {#online-custom-channel-setup}

För att få korrekt rapportering måste marknadsföringskanaler skapas för att återspegla er organisations UTM-strategi. Den här guiden tar dig igenom det bästa sättet att konfigurera dina anpassade kanalregler.

## Innan du börjar {#before-you-begin}

Innan du börjar skapa kanalregler för [!DNL Marketo Measure], ta lite tid att fundera över hur era marknadsföringskampanjer ska organiseras och hur de passar in i [!DNL Marketo Measure] ramverk. Du bör avgöra vilka kanaler, delkanaler, kampanjer och hänvisande webbplatser du vill spåra.

Tänk på följande:

* Organisationen kan skapa maximalt 40 anpassade marknadsföringskanaler. Detta gäller både offline- och onlinekanaler.
* Organisationen kan skapa upp till 200 underkanaler.
* Varje datainsamling, eller bucket, måste ha en egen regel (rad i kalkylbladet) för att specificera hur data ska ordnas. Var så specifik som möjligt.
* [!DNL Marketo Measure] logiken prioriterar data i fallande ordning med början på den översta raden i kalkylbladet och sedan nedåt. Den läser varje bucket, eller cell, rad för rad och söker efter den första passningen. Data sorteras sedan enligt värdena i dessa bucket. Mer om detta nedan.
* Sortera inte bladet i alfabetisk ordning eftersom detta påverkar logikreglerna.
* När filen har överförts kan du inte ändra någon av reglerna i sju dagar. [!DNL Marketo Measure] använder den här tiden för att bearbeta och uppdatera Touchpoints.

## [!DNL Marketo Measure] Logik och prioriteringar {#marketo-measure-logic-and-priorities}

Det första steget är att hämta kalkylbladet för den anpassade kanalen från [!DNL Marketo Measure] app. Navigera till **Inställningar** under **Mitt konto** och markera **Online**. Du kan välja antingen **Hämta ursprunglig mall** eller **Hämta aktuella regler**.

![](assets/1.png)

Kalkylbladet har 7 kolumner:

![](assets/2.png)

* **Kanal:** lägg till olika marknadsföringskanaler här
* **Delkanal:** lägg till motsvarande delkanaler här
* **Campaign:** lägg till kampanjnamn här, oavsett om värdet kommer från UTM eller Salesforce-kampanjer för [!DNL Marketo Measure] Funktionalitet
* **Medel:** medelkolumnen representerar värdet för parametern utm_medium
* **Källa:** källkolumnen representerar värdet på parametern utm_source
* **Landningssida:** lägg till landningssida här
* **Refererande webbplats:** URL:er till webbplatser som refererar till trafik till dina sidor eller inbyggda [!DNL Marketo Measure] logik (anges med hakparenteser)

I den åttonde kolumnen beskrivs vilka regler som du inte kan ta bort från kalkylbladet med &quot;Ta inte bort&quot;. Kalkylbladets överkant har standardkanalregler som [!DNL Marketo Measure] rekommenderar att du inte ändrar eller tar bort även om du inte använder dessa kanaler. [!DNL Marketo Measure] har djupgående integreringar med dessa plattformar så att de inkluderas som standard.

Raderna representerar regler och den ordning i vilken de [!DNL Marketo Measure] prioriterar data. Den första raden har prioritet över den andra raden, den andra raden har prioritet över den tredje raden och så vidare. När du avgör vilken marknadsföringskanal och underkanal som kontaktytor ska ingå i, [!DNL Marketo Measure] läser uppifrån och ned, från vänster till höger, tills en rad som uppfyller villkoren för kontaktytan hittas. (IE om en kontaktyta har en utm_source=Facebook, kommer kontaktytan att klistras in i Social.Facebook-kanalen på grund av regel 15 i skärmbilden).

![](assets/3.png)

[!DNL Marketo Measure] innehåller 12 standardkanaler som du kan använda. Dessa kanaler korrelerar med plattformar som [!DNL Marketo Measure] är helt integrerad. Oavsett om du använder dem eller inte, ta inte bort dem. Om du använder någon av dessa plattformar, till exempel Bing Ads, men föredrar att använda en annan namnkonvention för kanalen eller underkanalen, kan du uppdatera namnet. Ett exempel visas i bilden nedan.

![](assets/4.png)

Reglernas struktur är också viktig. Reglerna kan se ut som upprepad information och data som saknas, men strukturen är avsiktlig. För korrekt datasortering är det nödvändigt att mappa varje enskild källa till rätt kanal separat, även källor som delar delkanaler och kanaler. Ju mer detaljerade och detaljerade reglerna är, desto mer insiktsfulla blir resultaten. Det är i princip bäst att skriva en detaljerad regel för varje enskild marknadsföringsåtgärd som du vill spåra.

Tänk på följande situation: du har andra annonser som du inte vill spåra av någon anledning, eller du får besök på webbplatsen från en välbekant kanal, men inte en välbekant källa. Denna situation kan leda till dataförlust om [!DNL Marketo Measure] kan inte hitta rätt regel att använda för att sortera data. För att förhindra att detta händer [!DNL Marketo Measure] rekommenderar att du bryter regeln över flera rader.

Varje parameter eller komponent i regeln mappas separat till kanalen. Till exempel när [!DNL Marketo Measure] har [!DNL Facebook] data att sortera, söker efter regler relaterade till [!DNL Facebook]. Den skannas uppifrån och ned. I exemplet nedan [!DNL Marketo Measure] skulle förstå det för första [!DNL Facebook] underkanal behöver den bara läsa parametern source för att släppa data i regelns bucket.

![](assets/5.png)

Nästa regel frågar bara efter parametern medium, så alla data med den parametern kommer att paketeras i den här kanalen. Sist för [!DNL Facebook]kommer alla data som kommer från Facebook URL att placeras i den sista Facebook-haken.

Standardkanalen Övrigt finns för att hämta data som inte uppfyller några regelvillkor. Observera att vissa av bucketerna i den andra kanalen innehåller asterisker (&#42;). Dessa asterisker representerar jokertecken som fungerar som en&quot;catch-all&quot;.

![](assets/6.png)

Förfaller [!DNL Marketo Measure] logiken fungerar uppifrån och ned, observera att jokerteckendlinjen är markerad med en asterisk (&#42;), placeras i slutet av regelbladet. Alla data som inte fångas eller sorteras av de andra reglerna läggs automatiskt till i jokertecknet.

Nedan finns fler exempel på logik för jokertecken:

* &#42;e-post&#42; = innehåller &quot;email&quot;
* &#42;email = ends with &quot;email&quot;
* e-post&#42; = [!UICONTROL starts with email]

Observera dessutom att om du skapar en underkanal för en av kanalerna måste du skapa en underkanal för alla regler under den kanalen. Om du skapar en underkanal kan du alltså inte lämna resten av kolumnerna tomma.

## Konfigurera anpassade kanalregler {#setting-up-your-custom-channels-rules}

När du har bestämt hur du vill ordna och prioritera dina data är du redo att lägga till reglerna i kalkylbladet. Nedan följer några metodtips:

* Behåll reglerna så enkelt som möjligt från början. Ni kan alltid bygga vidare på reglerna medan ni går vidare.
* Lägg inte till några specialtecken i kanalnamnen (t.ex. $%#&amp;)&#42;@)
* Redigera inte reglerna som är kopplade till BingAds och AdWords. Dessa regler är avgörande för att lagra de uppgifter som automatiskt kommer från [!DNL Marketo Measure] API-integrering med dessa plattformar. Att ändra underkanals- och kanalnamnet så att det passar dina behov är dock inget problem.
* Ta inte bort reglerna som innehåller en&quot;Ta inte bort&quot;-anteckning.
* Reglerna för organisk sökning placeras alltid efter [!UICONTROL Paid Search rules]
* Du kan inte skapa regler baserade på olika underdomäner.
* Om du har flera värden att lägga till i en cell i kalkylbladet måste du separera värdena med ett semikolon `;` endast. Inga kommatecken eller mellanslag.
* Du behöver inte lägga till punkt com (.com) i slutet av den refererande URL:en.
* När du lägger till en refererande URL-adress ska du inte placera den inom hakparenteser som de andra API-relaterade reglerna.

## Överför regler för anpassade kanaler {#uploading-your-custom-channels-rules}

Kontrollera att alla nya kanal- och delkanalsvärden som du lägger till i CSV-filen redan har lagts till i kanalinställningsområdet för ditt Bizible-konto. Dubbelkontrollera alla kanal- och underkanalsnamn som matchar i CSV-filen med kanalinställningsområdet i [!DNL Marketo Measure] konto. Kontrollera om det finns kommatecken och blanksteg.

Om du får ett felmeddelande under överföringen kan du åtgärda problemet och överföra igen. Om inget felmeddelande tas emot klickar du på **Spara och bearbeta** längst ned på sidan.
