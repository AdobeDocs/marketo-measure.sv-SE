---
unique-page-id: 27656745
description: Vanliga frågor (flervaluta) - [!DNL Marketo Measure]
title: Vanliga frågor (flervaluta)
exl-id: 1d0936fb-4e66-4877-98d2-32c678a7ef3e
feature: Multi-Currency
source-git-commit: 3b14e758e81f237406da4e0fe1682a02b7a841fd
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Vanliga frågor (flervaluta) {#faq-multi-currency}

**Hur vet jag vilken funktionsbit jag vill aktivera?**

Kom ihåg att det finns två olika funktionsbitar för den här funktionen. Båda finns på fliken [!UICONTROL General] i CRM-avsnittet i Inställningar: Flera valutor och Avancerade valutor. Flera valutor bör aktiveras om kunden använder mer än en valuta, medan tilläggsfunktionen Avancerade valutor kan aktiveras om kunden använder funktionen Avancerad valutahantering i [!DNL Salesforce] där användaren kan ange ett tidsbaserat intervall för konverteringsgrader.

Marketo Measure hämtar automatiskt valutainställningen från kundens CRM. Manuell konfiguration i Marketo Measure för att matcha CRM krävs inte längre. Valutainställningen finns på sidan Allmänt under CRM.

**Varför ger mitt annonskonto mig ett varningsmeddelande?**

Ett varningsmeddelande visas bredvid ditt annonskonto som kan ha valutor som kommer in från en valuta som inte stöds. Om det inträffar kommer instrumentpanelerna att innehålla rutor med meddelandet&quot;Blandade valutor&quot;. Vi rekommenderar att du samarbetar med din CRM-administratör för att kontrollera att den här okända valutan innehåller en konvertering i din CRM.

**Vad betyder &quot;Blandade valutor&quot; på instrumentpanelen?**

Om du har en panel som har ett meddelande om &quot;blandade valutor&quot; längst ned, innebär det att vi har importerat vissa kostnader som är mappade till en valuta som vi inte känner igen. Eftersom alla våra konverteringar måste komma från CRM med en faktisk konverteringsgrad, innebär det att CRM saknar denna valuta. Vi rekommenderar att du samarbetar med din CRM-administratör för att kontrollera att den här okända valutan innehåller en konvertering i din CRM.

**Hur kan jag åtgärda felet &quot;Blandade valutor&quot; som orsakas av ogiltiga valutor?**

Vårt system uppdaterar okända valutor till &quot;XXX&quot;. Om du vill utesluta affärsmöjligheter med ogiltiga valutor skapar du en undertryckningsregel på sidan Inställningar för slutpunkt för att förhindra kontaktytor för affärsmöjligheter med valutan &quot;XXX&quot;. När vi har bearbetat rapporten rapporterar vi bara om kända valutor.

**Hur lägger jag till en ny valuta eller konverteringsgrad?**

Deklaration av en ny valuta eller konverteringsgrad kan bara göras i [!DNL Salesforce] eller [!DNL Dynamics], så att det bara finns en enda källa till sanning för dessa värden. När en ny valuta eller konverteringsgrad har identifierats hämtar [!DNL Marketo Measure] den och gör den tillgänglig för dig. Vi erbjuder inte något område att delta i dessa priser.

**Valutan visas inte i rätt format. Hur kan jag ändra detta?**

Vi förstår att vissa länder har ett annat sätt att formatera belopp (t.ex. 1,234,00, 1,234, 1 234). Men vi inför en annan nivå av komplexitet om vi inte bara måste fastställa en användares valuta, utan även deras ursprungsland, eftersom olika länder och valutor kan hanteras på olika sätt. Det konsekventa format vi har valt är 1 234,00. Detta kan inte ändras.

**Varför kan du inte visa valutasymbolen för min valda valuta?**

[!DNL Salesforce] och [!DNL Dynamics] visar sina belopp med konverteringskoden med tre bokstäver. Därför visas de konverterade beloppen också med konverteringskoden på tre bokstäver och inte med symbolen.

**Vad ska min kund se om flervaluta inte är aktiverad?**

Om kunden inte har funktionen för flera valutor använder vi standardinställningen deras nationella valutor i CRM och ändrar alla ISO-koder som visar deras utgifter och intäkter i företagsvalutan. Om detta är felaktigt och kunden använder olika valutor, skulle lösningen vara att uppgradera för att få tillgång till flervalutafunktionen.

**Hur påverkar den här funktionen kontaktpunktsbaserade rapporter i CRM?**

För [!DNL Dynamics]- och [!DNL Salesforce]-kunder som bara använder grundläggande (ej avancerad) valutahantering bör intäktsbelopp för kontaktytor konverteras korrekt, så CRM-rapporter ska fungera som förväntat.

Tyvärr finns det en viss nyans i hur detta fungerar för användare av [!DNL Salesforce] Advanced Currency Management, på grund av en långvarig begränsning på [!DNL Salesforce]. Det korta svaret på&quot;vad gör vi i det här fallet&quot; är att vi konverterar intäktsbelopp med hjälp av de schablonbelopp som definieras på den grundläggande (dvs. icke-avancerade) fliken&quot;Hantera valutor&quot;. Med andra ord ignorerar vi helt och hållet de daterade växelkurserna trots att kunden har definierat daterade valutakurser.

För den intresserade läsaren, här är varför det fungerar så här. Våra kontaktytor använder formelfält för att beräkna intäkter (som hämtas från det associerade affärsmöjlighetsbeloppet). [!DNL Salesforce] har inbyggt stöd för valutakonvertering för dessa formelberäkningar, men endast för deras grundläggande variant av valutastöd. Det är omöjligt för oss att definiera ett formelfält som refererar till daterade valutakurser. [!DNL Salesforce] stöder helt enkelt inte den funktionen, så vi har inget sätt att referera till datumen i våra intäktsberäkningar trots det faktum att dessa datumsiffror finns i [!DNL Salesforce] (det låter galet, men det är så det fungerar.)

**Om min kund använde ett arbetsflöde för att fylla i ett konverterat fält, hur ska de använda det här fältet för att gå framåt?**

Eftersom våra erbjudanden nu hanterar konverteringarna för kunden rekommenderar vi att de tar bort arbetsflödena och det anpassade fältet så att vi kan importera deras rådatamängd.

>[!MORELIKETHIS]
>
>[Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
