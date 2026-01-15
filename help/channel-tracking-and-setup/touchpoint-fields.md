---
description: Riktlinjer för kontaktpunktsfält för Marketo Measure-användare
title: Touchpoint-fält
exl-id: d6c2bd60-5341-4a52-939a-942afc093306
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 0%

---

# Touchpoint-fält {#touchpoint-fields}

Historiskt sett, när kunder är med på [!DNL Marketo Measure] och om vi inte har någon direkt taggningsintegrering, utbildar vårt Customer Success-team våra kunder om hur de ska tagga sina landningssidor så att de använder rätt UTM-format och vi kan lösa deras annonser. Vissa av dessa kunder använder inte UTM-moduler utan använder sina egna taggningsparametrar, vilket innebär att det kan vara mycket tidskrävande att redigera alla sina landningssidor i alla sina annonsnätverk med en ny taggningsstruktur som [!DNL Marketo Measure] tillämpar. För att anpassa sig till deras taggningsstruktur godkänner vi nu anpassade parametrar som kan mappas med våra regeldefinitioner. Målet är att anpassa sig till kundernas användning av sina anpassade spårningsparametrar så att vi inte behöver kräva att de ändrar sin URL-struktur.

>[!AVAILABILITY]
>
>Finns nu med fullständig segmentering i nivå 2 och nivå 3.

>[!NOTE]
>
>Det här är en avancerad funktion som endast ska konfigureras av Professional Services.

## Aktivera funktionen {#enabling-the-feature}

Navigera från menyn Inställningar för [!DNL Marketo Measure] till sidan Fält för slutpunkt. Därifrån kan du aktivera funktionen genom att välja **Yes** under **Enable Calculated Fields**. När funktionen är aktiverad kan du skapa Touchpoint-fält.

![Navigera till Touchpoint-fält från inställningsmenyn i Marketo Measure ](assets/touchpoint-fields-1.png)

## Använda {#how-to}

Om du vill skapa ett beräkningsfält bör du tänka på att det finns tre olika åtgärder som en användare kan utföra: extrahera, mappa till och sammanfoga. De kallas också operatorer för att definiera ett beräkningsfält.

Extraheringar

Operatorn [!UICONTROL extracts] hämtar värdet från ett fält från en annan plats, till exempel ett kampanjfält, ett Lead-fält eller i ett mer avancerat fall, [extrahera anpassade parametrar från landningssidan](https://docs.google.com/document/d/1NRViyCsXvPKbCTfGW32Yi2vWBjMDRF7bzkzKj9s2DDA/edit?ts=5e20b482#heading=h.xxwtissvw4){target="_blank"}. Sedan placeras det i ett Touchpoint-fält (se [Mappar till exempel](https://docs.google.com/document/d/1NRViyCsXvPKbCTfGW32Yi2vWBjMDRF7bzkzKj9s2DDA/edit?ts=5e20b482#heading=h.xxwtissvw4){target="_blank"} #2).

**Exempel 1**

Det finns ett anpassat fält på kontakten, campaign_source__c, som kunden vill släppa på kontaktytan för rapportering. Du kan definiera en regel för att skapa ett beräkningsfält med namnet&quot;Campaign Source&quot; och släppa värdet i det fältet.

Mål: Använd värdet för ett anpassat fält och placera det i Touchpoint-objektet för enklare rapportering.

* Skapa ett beräkningsfält och ge det etiketten&quot;Campaign Source&quot;
* Definiera regeln genom att börja söka efter fältet Contact.Campaign_Source__c
* Använd operatorn &quot;extracts&quot; eftersom vi måste ta ut värdet från parametern
* För att extrahera hela strängen från fältet använder vi uttrycket &quot;(.&#42;)&quot;

   * **(**) markerar början på extraheringen
   * **)** markerar slutet av extraheringen
   * **.&#42;** meddelar oss att vi extraherar den fullständiga strängen

![.&amp;42; meddelar oss att vi extraherar den fullständiga strängen ](assets/touchpoint-fields-10.png)

**Exempel nr 2**

Ett vanligt användningsfall som den här funktionen aktiverar är att hämta värden från anpassade parametrar i en URL-sträng. Detta är användbart om du använder andra parametrar än UTM men vill analysera värdena till kontaktpunktsfält.

**Länk:** `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=5OFF` eller `https://www.adobe.com/blog/marketing-revenue-reporting-overview?promo=25OFF`.\
**Mål:** Skapa ett anpassat fält med namnet &quot;Rabattkod&quot; och släpp värdet &quot;5OFF&quot; eller &quot;25OFF&quot;, vilket värde som än skickas.

* Skapa ett beräkningsfält och ge det etiketten&quot;Rabattkod&quot;
* Definiera regeln genom att börja söka efter fältet Touchpoint.Session.LandingPage
* Använd operatorn &quot;extracts&quot; eftersom vi måste ta ut värdet från parametern
* För att extrahera kampanjvärdet definierar vi värdet som &quot;promo=(\w+)&quot;

   * **(**) markerar början på extraheringen
   * **)** markerar slutet av extraheringen
   * **\w** säger att vi extraherar ett ord som innehåller 0-9
   * **+** extraherar parameterns fullständiga värde utan teckenbegränsning
   * Observera att du använder ett snedstreck och inte ett omvänt snedstreck

![Observera att du använder ett snedstreck och inte ett ](assets/touchpoint-fields-11.png)

**Exempel nr 3**

Låt oss testa ett liknande exempel där vi extraherar en spårningskod som: `https://www.adobe.com/blog/marketing-revenue-reporting-overview?cid=123456`.

**Mål:** Skapa ett beräkningsfält och ge det etiketten&quot;Adobe Campaign Id&quot; med värdet från cid-parametern.

* Skapa ett beräkningsfält och ge det etiketten&quot;Adobe Campaign ID&quot;
* Definiera regeln genom att börja söka efter fältet Touchpoint.Session.LandingPage
* Använd operatorn &quot;extracts&quot; eftersom vi måste ta ut värdet från parametern
* För att extrahera värdet &quot;123456&quot; definierar vi värdet som &quot;cid=(\d{6})&quot;

   * **(**) markerar början på extraheringen
   * **)** markerar slutet av extraheringen
   * **\d** säger att vi extraherar en&quot;siffra&quot;
   * **{6}** är antalet tecken som vi extraherar

![{6} är antalet tecken som vi extraherar](assets/touchpoint-fields-12.png)

**Exempel 4**

När landningssidorna blir mer komplicerade och du har flera spårningsparametrar kan du behöva skapa flera kontaktpunktsfält och extrahera värden flera gånger, som:
`https://www.adobe.com/blog/marketing-revenue-reporting-overview?trackID=123456&country=US&campaign_ID=7890`.

**Mål:** Skapa flera beräknade fält för &quot;målland&quot; och &quot;anpassat kampanj-ID&quot; med respektive värden från parametrarna.

* Skapa ett beräkningsfält och ge det etiketten&quot;Målland&quot;
* Definiera regeln genom att börja söka efter fältet Touchpoint.Session.LandingPage
* Använd operatorn &quot;extracts&quot; eftersom vi måste ta ut värdet från parametern
* För att extrahera &quot;US&quot;-värdet definierar vi värdet som &quot;country=(\w{2})&quot;

   * **(**) markerar början på extraheringen
   * **)** markerar slutet av extraheringen
   * **\w** säger att vi extraherar ett ord
   * **{2}** är antalet tecken som vi extraherar

* Skapa ett beräkningsfält och ge det etiketten&quot;Anpassat kampanj-ID&quot;
* Definiera regeln genom att börja söka efter fältet Touchpoint.Session.LandingPage
* Använd operatorn &quot;extracts&quot; eftersom vi måste ta ut värdet från parametern
* För att extrahera värdet &quot;123456&quot; definierar vi värdet som &quot;campaign_ID=(\d{6})&quot;

   * **(**) markerar början på extraheringen
   * **)** markerar slutet av extraheringen
   * **\d** säger att vi extraherar en&quot;siffra&quot;
   * **{6}** är antalet tecken som vi extraherar

![{6} är antalet tecken som vi extraherar](assets/touchpoint-fields-13.png)

**Mappar till**

Operatorn [!UICONTROL maps to] skapar en värdetabell som måste översättas eller klistras in i ett annat värde. Vanligtvis är det ett nyckelvärde där en kod representerar ett eget namn och måste mappas till det egna namnet.

**Exempel 1**

Det finns kampanjer som ni har skapat för en&quot;Sommarkampanj&quot; och&quot;Svart fredag-kampanj&quot; som kan köras i flera kanaler. Du vill skapa ett beräkningsfält som kallas&quot;Initiative&quot; (initiativet för initiativet) och du vill mappa alla kontaktytor med&quot;End of sommar-kampanjen&quot; eller&quot;Black Friday-kampanjen&quot; till ett Initiative-värde som&quot;Promotion&quot;, förutom andra möjliga värden.

![Det finns kampanjer som du har skapat för erbjudandet&quot;Sommarslut&quot;](assets/touchpoint-fields-2.png)

**Exempel nr 2**

Nu när vi har lärt oss att extrahera och mappa till fält kan vi kombinera dessa åtgärder för att först extrahera ett värde från en parameter och sedan mappa det till ett eget namn som är lite mer begripligt. Låt oss börja med den här landningssidan: `https://www.adobe.com/blog/marketing-revenue-reporting-overview?BZ=04-01-09-03-10`.

**Mål:** Skapa flera beräkningsfält, där det första numret mappar till en region, det andra till en produkt, det tredje till ett initiativ, det fjärde till en persona och det femte till en Media Platform. Mappa sedan det numeriska värdet till ett&quot;eget namn&quot;.

* Skapa ett beräkningsfält och ge det etiketten Region
* Definiera regeln genom att börja söka efter fältet Touchpoint.Session.LandingPage
* Använd operatorn [!UICONTROL extracts] eftersom vi måste ta ut värdet från parametern
* För att extrahera värdet &quot;04&quot; definierar vi värdet som &quot;BZ=(\d{2})-\d{2}-\d{2}-\d{2}-\d{2}&quot;

   * **(**) markerar början på extraheringen

      * Observera, att eftersom vi bara extraherar de 4 första siffrorna har bara den öppna parentesen
   * **)** markerar slutet av extraheringen

      * Observera, att eftersom vi bara extraherar de 4 första siffrorna har bara den avslutande parentesen
   * **\d** säger att vi extraherar en&quot;siffra&quot;
   * **{2}** är antalet tecken som vi extraherar



* Klicka på [!UICONTROL Save]. Du måste spara det nya fältet innan det kan användas för nästa regel!
* Därefter ska vi mappa alla möjliga värden för de första siffrorna till de egna namnen
* Skapa ett beräkningsfält och ge det etiketten&quot;Region_Name&quot;
* Definiera regeln genom att börja med att söka efter det extraherade fältet. I det här fallet [!DNL Touchpoint.Region]
* Använd operatorn [!UICONTROL maps to] eftersom vi vill skapa en mappning för varje nummer till dess värde
* Du får en tabell med en lista över varje mappning. Till slut kommer det att se ut ungefär så här:
* Baserat på mappningen och URL:en ovan är&quot;Region_Value&quot; för en kontaktyta med denna landningssida&quot;EMEA&quot;
* Upprepa extraheringen och mappningen för de återstående fyra sifferuppsättningarna

   * Om du vill extrahera 01 definierar du värdet som &quot;BZ=\d{2}-**(\d{2})**-\d{2}-\d{2}-\d{2}&quot;
   * Om du vill extrahera 09 definierar du värdet som &quot;BZ=\d{2}-\d{2}-**(\d{2})**-\d{2}-\d{2}&quot;
   * Om du vill extrahera 03 definierar du värdet som &quot;BZ=\d{2}-\d{2}-\d{2}-**(\d{2})**-\d{2}&quot;
   * Om du vill extrahera 10 definierar du värdet som &quot;BZ=\d{2}-\d{2}-\d{2}-\d{2}-**(\d{2})**&quot;

![Om du vill extrahera 10 definierar du värdet som &quot;BZ=\d{2}-\d{2}-\d{2}-\d{2}-(\d{2})&quot;{1\}](assets/touchpoint-fields-3.png)

**Sammanfogningar**

Operatorn [!UICONTROL concatenates] kombinerar värden från flera fält till ett enda fält. Det här är användbart om du vill skapa ett anpassat värde som hämtar data mellan olika fält för att skapa

**Exempel 1**

Det finns separata fält i objektet säljprojekt för Segment__c och Grade__c som användaren vill kombinera till ett enda fält i slutpunktsobjektet för rapportering. Genom att sammanfoga fälten ser du värden som Enterprise_A eller Mid-Market_B.

![Det finns separata fält för säljprojektsobjektet för segmentering och gradering](assets/touchpoint-fields-4.png)

## Touchpoint-fält och segment {#touchpoint-fields-and-segments}

Nu när värdena från URL:en har tolkats och finns på pekpunkten visas de nya fälten där Touchpoint-fält används, som att skapa segment eller definiera regler för borttagning av slutpunkt.

I den här produktversionen finns möjligheten att skapa segment med hjälp av Touchpoint-fält. Det gick inte att skapa segment med kontaktpunktsfält tidigare.

![Möjligheten att skapa segment med hjälp av Touchpoint-fält är tillgänglig med ](assets/touchpoint-fields-5.png)

För att göra det enklare att bygga ut segment är det nu möjligt att skapa dynamiska segment från de Touchpoint-fält som skapades. Om du till exempel har skapat ett Touchpoint-fält som tolkade en geografisk region, i stället för att skapa ett segment för varje möjlig region, kan du skapa ett segment och vi skapar segment för varje instans som ett nytt värde visas. Detta är mycket praktiskt om ett attribut som postnummer måste tolkas och användas som ett segment!

Din installation ser ut ungefär som skärmbilden nedan. Segmentnamnet hämtar dynamiskt värdet i Touchpoint-fältet med klammerparenteserna för att söka efter fältet.

![Din konfiguration ser ut ungefär som skärmbilden nedan. Segmentnamnet ](assets/touchpoint-fields-6.png)

Regeln refererar till samma Touchpoint-fält och söker efter värden som inte är lika med null.

![Regeln refererar till samma Touchpoint-fält och söker efter värden som ](assets/touchpoint-fields-7.png)

## Vanliga frågor och svar {#faq}

**Finns det ett maximalt antal Touchpoint-fält som kan skapas?**

Det finns en gräns på 100 fält.

**Jag ser inte mitt nya Touchpoint-fält som jag nyss skapade i listan. Var ligger den?**

Glöm inte att spara reglerna när du har skapat den. Om det nya fältet inte visas kontrollerar du om du har sparat det. Du måste spara det nya fältet innan det kan användas för nästa regel.

>[!NOTE]
>
>På grund av komplexiteten är ett Touchpoint-fält som använder operatorn &quot;mappar till&quot; inte tillgängligt för användning i ett annat Touchpoint-fält.

**Vilket uttryck använder jag för att extrahera flera parametrar från en enda landningssida?**

Precis som i Extract-exemplet nr 4 måste du skapa flera fält för att extrahera var och en av parametrarna. Så om du har fem olika värden skapar du fem Touchpoint-fält som du kan extrahera vart och ett av dem.

**Varför visas inte mina nya fält i [!DNL Marketo Measure]-schemat?**

Ytterligare arbete krävs för att visa de nya fälten i Data Warehouse-schemat [!DNL Marketo Measure]. För närvarande visas fält med inställningar och konfiguration så att du kan använda Touchpoint-fält när du skapar segment eller skapar regler för borttagning av pekpunkter.

**Hur verifierar jag att mitt extraheringsuttryck är giltigt och drar rätt värde?**

Det finns ett onlineverktyg ([[!DNL https]://regex101.com/](https://regex101.com/){target="_blank"}) som du kan köra och testa uttrycket. Uttrycket visas grönt om det är giltigt eller rött om det är ogiltigt. Dessutom är rutan [!UICONTROL explanation] högst upp till höger till hjälp och talar om vad du extraherar.

![Det finns ett onlineverktyg (https://regex101.com/(https://regex101.com/){target="blank"}) som du kan köra och testa](assets/touchpoint-fields-8.png)

![Det finns ett onlineverktyg (https://regex101.com/(https://regex101.com/){target="blank"}) som du kan köra och testa](assets/touchpoint-fields-9.png)
