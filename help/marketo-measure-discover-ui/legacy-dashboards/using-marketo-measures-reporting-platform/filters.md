---
unique-page-id: 18874656
description: Filter - [!DNL Marketo Measure] - Produktdokumentation
title: Filter
exl-id: 249266c8-9ff5-4895-979c-4f377423d031
feature: Reporting
source-git-commit: e24e01a03218252c06c9a776e0519afbddbe2b8c
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Filter {#filters}

Läs mer om de olika filter som finns i Discover och hur du kan använda dem.

>[!NOTE]
>
>Operatorerna &quot;matchar ett användarattribut&quot; och &quot;matchar (avancerat)&quot; i Discover-filtren är helt administrativa och kan ignoreras.

**Konto-ID**

_Används i: Kontobaserad marknadsföring_

Markera eller klistra in ett antal konto-ID:n från CRM för att filtrera resultaten. Konto-ID är mer unikt än kontonamn eftersom namn kan vara samma.

**Kontonamn**

_Används i: Kontobaserad marknadsföring_

Markera eller klistra in en serie kontonamn från CRM för att filtrera resultatet. Strängar kan ha dubbletter, så det är möjligt att ha flera[!DNL Marketo Measure]till exempel konton. Om ett enda konto behövs i det här fallet använder du filtret för konto-ID i stället.

**Attributionsmodell**

_Används i: Översikt, marknadsföringsutgifter, annonsavkastning, kontobaserad marknadsföring, webbtrafik, marknadschef, betalmedia, innehållsmarknadsföring, Passport_

Välj en enda attribueringsmodell som ska användas på ritytan: First Touch, Lead Creation Touch, U-Shaped, W-Shaped, Full Path eller Custom Model. Fullständig sökväg och Anpassad modell är inte tillgängliga i alla lager.

**Campaign**

_Används i: Översikt, Tillväxt, annonsavkastning, webbtrafik, marknadschef, betalmedia, innehållsmarknadsföring, Passport_

Filtrera styrelsen med ett eller flera kampanjnamn. Operatorer ger filtret ytterligare flexibilitet, t.ex. med operatorerna &quot;contains&quot; och &quot;begin with&quot;. Om ett kanal- eller delkanalsfilter har tillämpats är den lista med kampanjer som visas en delmängd av de använda filtren.

**Kategori 1-10**

_Används i: Översikt, Tillväxt, Annonsering, ROI, marknadschef, Betalda media, Innehållsmarknadsföring, Snapshot, Snapshot, Kohort-tratt, Passport_

Använd segmentfilter på ritytan med de kategorier och segment som du har skapat i [!DNL Marketo Measure] Inställningar. Listan med kategorier som du har skapat visas på filtermenyn, så om inga kategorier har ställts in finns det inga kategorifilter på menyn. Segmentkategorier är inte tillgängliga i alla nivåer, och antalet tillgängliga kategorier varierar också mellan olika nivåer.

**Kanal**

_Används i: Översikt, Tillväxt, Marknadsföringsutgifter, Annonsering, ROI, Web Traffic, CMO, Betald media, Innehållsmarknadsföring, Snabb, Passport_

Filtrera styrelsen med en eller flera kanaler. Operatorer ger filtret ytterligare flexibilitet, t.ex. med operatorerna &quot;contains&quot; och &quot;begin with&quot;. När en kanal har angetts hämtas de värden som visas i filtren Subkanal och Campaign från det använda delkanalsfiltret.

**Kohortestet**

_Används i: Kohorttratt_

Markera scenen som du vill visa en kohort av. Scenen som du väljer visas högst upp i tratten, där alla konverteringar löper nedåt från början.

**Datum**

_Används i: Översikt, Tillväxt, Marknadsföringsutgifter, annonserings-ROI, kontobaserad marknadsföring, webbtrafik, marknadschef, betald media, innehållsmarknadsföring, snabbhet, ögonblicksbild, kohorttratt, Passport_

Välj ett datumintervall om du vill filtrera data i ritytorna med flexibla datumoperatorer som &quot;finns i intervallet&quot;, &quot;finns i året&quot; eller &quot;är före&quot; till exempel. Undantaget är Ögonblicksbild, där du väljer ett enstaka datum för att visa en ögonblicksbild av data.

**Datumtyp**

_Används i: Översikt, Tillväxt, Marknadsföringsutgifter, Annonsering, kontobaserad marknadsföring, webbtrafik, marknadschef, Betald media, Innehållsmarknadsföring, Passport_

Välj den typ av datum som du vill använda, som är knuten till datumfiltret. Standarddatumtypen varierar beroende på rityta. Slutpunktsdatum avser det datum då marknadsföringsaktiviteten ägde rum, Skapad är det datum då lead eller kontakt eller säljprojekt skapades i CRM och Stängningsdatum är det datum då affärsmöjligheten stängdes.

**Dimension**

_Används i: Betalda media_

Dimensionen liknar funktionen Gruppera efter, förutom att den används på betald mediakort på ett något annorlunda sätt. I stället för att stapla ett diagram ändrar Dimension raderna i översiktsdiagrammet och det inledande objektet i tabellerna.

![](assets/1.png)

Som standard är Dimensionen delkanal och kan ändras till:

* Ingen: Visar allt i en mängd utan någon brytning
* Kanal: Visar data per marknadsföringskanal
* Delkanal: Visar data per marknadsföringsunderkanal
* Campaign: Visar data per kampanj
* Konto: Visar data per konto. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Annonsgrupp: Visar data per annonsgrupp. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Annons: Visar data efter annons. Gäller för annonser i dubbelklickning, så om dubbelklickning inte används visas inga resultat
* Annonsör: Visar en lista över data per annonsörer. Gäller för Doubleclick-annonseraren, så om Doubleclick inte används visas inga resultat
* Kreativ: Visar data efter kreativitet. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Nyckelord: Visar data efter nyckelord. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Placering: Visar data efter placering. Gäller för dubbelklicka-placeringar, så om dubbelklickning inte används visas inga resultat
* Plats: Visar data per plats. Gäller för dubbelklickswebbplatser, så om dubbelklickning inte används visas inga resultat

**Gruppera efter**

_Används i: Översikt, tillväxt, marknadsföringsutgifter, kontobaserad marknadsföring, webbtrafik, marknadschef_

Justerar diagram för att ändra dimensionerna som staplas och grupperas tillsammans. Som standard är Gruppera efter inställt på Kanal och kan ändras till:

* Ingen: Visar allt i en mängd utan någon brytning
* Kanal: Grupperar data efter marknadsföringskanal
* Delkanal: Grupperar data efter marknadsföringsunderkanal
* Campaign: Grupperar data efter kampanj
* Konto: Grupperar data efter konto. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Annonsgrupp: Grupperar data efter annonsgrupp. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Annons: Grupperar data efter annons. Gäller för annonser i dubbelklickning, så om dubbelklickning inte används visas inga resultat
* Annonsör: Grupperar data efter annonsören. Gäller för Doubleclick-annonseraren, så om Doubleclick inte används visas inga resultat
* Kreativ: Grupperar data efter kreativitet. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Nyckelord: Grupperar data efter nyckelord. Gäller för [!DNL AdWords], [!DNL Bing]och [!DNL Facebook].
* Placering: Grupperar data efter placering. Gäller för dubbelklicka-placeringar, så om dubbelklickning inte används visas inga resultat
* Plats: Grupperar data per plats. Gäller för dubbelklickswebbplatser, så om dubbelklickning inte används visas inga resultat

![](assets/2.png)

**Landningssida**

_Används i: Innehållsmarknadsföring_

Granska resultatet av en enda landningssida, eller kanske landningssidor som innehåller ett visst ord, t.ex.&quot;blogg&quot;.

**Mått**

_Används i: Översikt, webbtrafik, marknadschef, betalmedia, innehållsmarknadsföring_

Det finns två olika mätväljare som används för olika paneler. Måttväljaren ändrar måttet i ett diagram så att du kan växla mellan att visa intäkter eller utgifter eller till exempel visningar.

På översikts- och CMO-ritytorna finns det en förkortad lista med värden som relaterar till ROI-mått:

* Intäkter
* Utgift
* Erbjudanden
* Försäljningsförlopp
* Möjligheter
* Kontakter
* Leads

På webbplattorna Betalda media och Innehållsmarknadsföring finns det en längre lista över värden som är relaterade till både ROI- och trattmått:

* Intäkter
* Utgift
* Erbjudanden
* Försäljningsförlopp
* Möjligheter
* Kontakter
* Leads
* Klickningar
* visningar
* Besök
* Unika besök
* Sidvyer
* Forms

**Scen**

_Används i: Hastighet_

Som standard visar snabbpanelen tider för alla steg, men om du vill gå in på en viss scen använder du scenfiltret för att markera scenen.

**Delkanal**

_Används i: Översikt, Tillväxt, Marknadsföringsutgift, annonsavkastning, webbtrafik, marknadschef, betald media, innehållsmarknadsföring, Passport_

Filtrera ritytan med en eller flera underkanaler. Operatorer ger filtret ytterligare flexibilitet, t.ex. med operatorerna &quot;contains&quot; och &quot;begin with&quot;. Om ett kanalfilter har använts kommer listan med delkanaler som visas att vara en delmängd av de använda filtren. När en delkanal har angetts hämtas de värden som visas i Campaign-filtren från det använda delkanalsfiltret.

**URL**

_Används i: webbtrafik_

Granska trafiken i en enda URL, eller kanske URL:er som innehåller ett visst ord, t.ex. &quot;product&quot;.

**Won**

_Används i: Hastighet_

Som standard rapporterar Snabbhetsstyrelsen bara stängda vunna affärsmöjligheter, men justera det här filtret för att se hur snabbt det går att hitta stängda, vunna eller stängda förlorade affärsmöjligheter.
