---
unique-page-id: 18874660
description: Frågor och svar - [!DNL Marketo Measure] - Produktdokumentation
title: Vanliga frågor och svar
exl-id: f1896bf8-2216-427e-ac3e-98d87efede76
feature: Reporting
source-git-commit: e24e01a03218252c06c9a776e0519afbddbe2b8c
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---

# Vanliga frågor och svar {#faq}

[!DNL Marketo Measure Discover]: Vanliga frågor.

**Hur sparar jag filtren i en rapport?**

Precis som i dag sparas frågeresultaten i URL:en och kan sparas eller delas med den kopierade URL:en.

**Hur använder jag förinställda datumintervall som Senaste året eller Aktuellt kvartal?**

I stället för att använda förinställda datumintervall har vi nu lagt till flexibilitet för datum. Du kan fortfarande ange Sista året, men du kan välja Senaste året, som är de sista 365 dagarna i dag, eller Senaste fullständiga året, som är det sista hela året från 1/1 till 12/31. Ett annat bra sätt att använda den nya datumväljaren är att ange ett relativt datumintervall, vilket ger ett rullande tidsfönster för ett flyttningsdatum.

**Hur hämtar jag CPL- eller CPC-data?**

Dessa mätvärden finns endast på betalmediapanelen.

**Varför visar du inte sidvyer på tillväxtpanelen?**

En av funktionerna i tillväxtpanelen är att du inte kan gruppera trenddiagram efter en dimension, som Channel eller Campaign. Vi har inte dessa data tillgängliga på sidvisningsnivå eftersom sidvyer inte alltid har en källa som Channel eller Campaign eftersom de inträffar mitt i webbbesöken. Använd betald media eller webbtrafik för att visa sidvisningsdata.

**När jag ändrar grupperingen är summorna inte alltid lika stora. Varför är det så?**

Det finns inga värden för varje enskild datahierarki eftersom hierarkin inte alltid är ett tydligt klippflöde. Om till exempel kostnaderna rapporteras själv eller importeras från en annonsleverantör kan den totala kostnaden för Kanal 1 vara 10 000 USD, men per enskild kampanj har bara 500 USD rapporterats, så när grupperingen ändras mellan Kanal och Campaign varierar totalsumman.

**Vad är &quot;matchar ett användarattribut&quot; i filteroperatorerna?**

Användarattribut gäller användare som företags-ID, förnamn eller efternamn, men eftersom våra användare är du (våra kunder) och inte dina kunder kan användarattributen inte användas i [!DNL Marketo Measure Discover] upplevelse. Du kan ignorera det här alternativet. Vi arbetar på en bättre anpassad filterupplevelse som tar bort filter som inte gäller våra kunder.

**Hur kommer det sig att vissa standarddatumintervall sträcker sig över den första i följande månad?**

Datumintervallet är inte alltid intuitivt, men standardfiltergränssnittet har den användbara&quot;före&quot;-texten som motsvarar slutdatumet, så detta bör påminna dig om att slutdatumet bör ligga 1 dag utanför det önskade intervallet.

**Vilken attribueringsmodell används för leads och kontakter?**

Kontaktpunkter för köpare som mappas till Leads och Kontakter mäts upp till beröringen Lead Creation, så modellen First Touch, Lead Creation och U-Shaped rekommenderas. Om du ändrar attribueringsmodellen till W-Shaped eller Full Path använder vi automatiskt U-Shaped-modellen för Leads och Contacts.

**Varför är mina besök, unika besök och Forms tomma på tillväxtpanelen?**

Om de här rutorna råkar vara 0 eller tomma i vyn innebär det att rutorna inte är tilldelade för ditt konto. Kontakta din Success Manager om du har några frågor om detta.

**För Leads över tid och Kontakter över tid, vilket är antalet som refererar?**

Den använder antalet kontaktytor, som distribueras av den attributmodell du väljer. Det blir det totala antalet leads och räkningar som fördelas över tiden. Det är inte ett unikt antal.

**Visar diagrammet för formulär-URL:er per kanal i Innehållsmarknadsföring webb- och formulärfyllningar?**

Dessa är endast spårade formulärfyllningar.

**Vilka är fördelarna med Discover framför Åtgärd?**

[!DNL Marketo Measure Discover] ger bättre funktionalitet, till exempel detaljrikedom, och bättre filtrering, till exempel delkanaler och kanaler. Vi solerar också måttet en tid 2019.

**I måttet kunde jag filtrera efter annonsgrupp och konto när de filtrerades till annonskonton - hur ser jag detta i Discover?**

Detta är endast tillgängligt med betald mediapanel.

**Hur skiljer sig Kohorttratten från Passport-tratten?**

Med Cohorttratten kan ni titta på hur stor konverteringsgraden för säljprocessen är och mäta effekten mellan olika faser. Du kan välja vilken scen du vill mäta från med hjälp av filtren, som gör att du kan visa konverteringsgraden från den scenen till alla efterföljande faser. Passport-styrelsen visar alla leads/kontakter och säljprojekt som har gått igenom varje pipeline inom en viss tidsram.

**Hur bestäms innehållet på det betalda mediakortet?**

På alla paneler har vi lagt till ett filter som endast inkluderar data där vi har en känd annonsleverantör från Facebook, Google, Bing, LinkedIn eller Doubleclick eftersom vår integrering gör att vi kan hämta annonsdata från dessa källor. Dessutom har vi lagt till ett oskarpt namn som matchar kanalerna och delkanalerna för visning, betald sökning, betald social, PPC, SEM, betald mobil, betald Twitter, Adroll, Terminus, Madison Logic, Madisonlogic och Demandbase.

**Vad är skillnaden mellan besök och unika besök?**

Unika besök är en delmängd av Besök. Besök räknas som en del av varje besök på platsen, men unika besök är unika cookies från dessa besök. En person kan redovisa flera unika besök om de returnerar med en annan cookie-identifierare.

**Räknas kontaktytan med antalet kontaktytor för köpare eller Buyer Attribution?**

Det är ett antal&quot;raw&quot; kontaktytor eller&quot;användarkontaktytor&quot; där det är en sammanställning av båda, plus kontaktytor som inte resulterade i någon kontaktyta på lead/kontakt eller säljprojekt.

**Varför visas bara $0,00 när jag filtrerar efter URL?**

Detta är det förväntade beteendet på grund av att vi inte har några kostnader segmenterade efter URL-adress, så det är inte tillämpligt i det scenariot.

**Varför visas inte alla segmentalternativ för mina kategorifilter?**

Endast de segment som har giltiga poster mappade till sig visas i segmentfiltret. Om det t.ex. inte finns några poster med segmentet &quot;Annat&quot; visas inte &quot;Annat&quot; som ett alternativ.

**Gör [!DNL Marketo Measure Discover] stöder du teckenuppsättningen GB18030?**

Discover använder verktyg från tredje part och stöder inte den GB18030-teckenuppsättning som angetts för tillfället.

**Varför visas ett 401-fel när jag läser in Discover med texten &quot;You are not authenticated to view this page&quot;?**

[!DNL Marketo Measure Discover] kräver att cookies från tredje part visas korrekt. Aktivera cookies från tredje part i webbläsaren och uppdatera sidan om du vill använda Discover.

>[!NOTE]
>
>I vissa webbläsare, bland annat Chrome i Incognito, inaktiveras cookies från tredje part som standard.

![](assets/faq-1.png)