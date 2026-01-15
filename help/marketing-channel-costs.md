---
description: Riktlinjer för kostnader för marknadsföringskanaler för Marketo Measure-användare
title: Marknadsföringskanalkostnader
exl-id: 36ccaff3-db55-47bd-a24e-4aa1894f13e0
feature: Channels, Spend Management
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---

# Marknadsföringskanalkostnader {#marketing-channel-costs}

En av de mest grundläggande fördelarna med att använda [!DNL Marketo Measure] är möjligheten att koppla marknadsföringssatsningarna direkt till effekten på intäkterna - med så mycket detaljrikedom som önskas. Det är möjligt att se avkastningen på investeringar på kontaktytpunktsnivå. Om du vill utnyttja den här förmånen måste kanalkostnaderna överföras till appen [!DNL Marketo Measure]. Avkastningsrapporter skapas automatiskt och är tillgängliga i **kontrollpanelen för marknadsföringsavkastning** i [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}.

[Klicka här om du vill gå direkt till instruktionerna.](/help/marketing-channel-costs.md)

Med funktionen [!DNL Marketo Measure] Marketing Spend kan kunder överföra sina utgifter över alla kanaler, underkanaler och kampanjer. Ju mer data kunderna lägger till, desto mer avkastningsbaserad rapportering visas på kontrollpanelen för intäktsattribuering.

Kostnader som rapporteras och importeras från direkta annonsanslutningar dras automatiskt in på den mest detaljerade nivån och behöver inte överföras. Detta inkluderar våra nuvarande integreringar med Google AdWords, Bing Ads, Doubleclick och Facebook.

[Klicka här för att gå direkt till Frågor och svar.](/help/marketing-channel-costs.md)

## Definitioner {#definitions}

**Utgifter per kampanj**

På den mest detaljerade nivån kan kunderna ange utgifter per enskild kampanj, grupperade i sin respektive kanal. För CRM-kampanjer har [!DNL Marketo Measure] samlat in kampanj-ID i en separat kolumn som hjälper dig att mappa utgifter för offlinekampanjer från CRM till den här tabellen. Genom att lägga till utgifter på den här nivån kan kunderna visa avkastningen på kampanjinvesteringen och optimera resultatet för Campaign.

Summan av alla kampanjer behöver inte summera några värden som har angetts i delkanalen eller kanalen, men det får inte vara mer än några värden som har angetts i delkanalen eller kanalen. Om summan är mindre än värdet som anges i delkanalen eller kanalen lägger [!DNL Marketo Measure] automatiskt till en rad för &quot;Annan&quot; för att täcka skillnaden och fylla i eventuella luckor.

**Utgift per delkanal**

På en högre nivå kan kunderna ange utgifter per underkanal, grupperade under dess kanal. Genom att lägga till utgifter på den här nivån kan kunderna se avkastningen på investeringar i subkanaler och optimera prestanda per subkanal.

Summan av alla delkanaler behöver inte summera några värden som har angetts vid kanalen, men det får inte vara mer än några värden som har angetts vid kanalen. Om summan är mindre än värdet som anges i kanalen lägger [!DNL Marketo Measure] automatiskt till en rad för &quot;Annan&quot; för att täcka skillnaden och fylla i eventuella luckor.

**Utgift per kanal**

På den högsta nivån kan kunderna ange utgifter per kanal. Genom att lägga till utgifter på den här nivån kan kunderna se kanalens avkastning och optimera prestanda per kanal.

**Datumväljaren**

Standarddatumintervallet börjar från ditt startdatum med [!DNL Marketo Measure] upp till den aktuella månaden. För att säkerställa att kostnaderna förblir korrekta kan du inte ange kostnader för kommande månader, men du kan ange kostnader för månader innan ditt partnerskap med [!DNL Marketo Measure].

**Filter**

Om du vill begränsa resultaten i marknadsföringsbudgeten markerar du en kanal längst upp för att filtrera bort andra kanaler. Det här är praktiskt när ett team har en enda kanal i fokus.

**Sök**

Använd sökrutan för att hitta matchande text från kanaler, delkanaler eller kampanjer.

**Ladda ned aktuella kostnader**

Den hämtade CSV-filen hämtar resultaten från den aktuella skärmen, vilket innebär att alla datum, filter eller sökningar som tillämpas hämtas som de är.

**Överför CSV**

Oavsett vilken vy som visas i webbläsaren kan du överföra en CSV-fil om det är en filtrerad vy eller standardvy med alla datum och kanaler.

Det vanligaste felet är datumkolumnernas format, som inträffar om datumformatet ändras och kan inträffa avsiktligt om du flyttar mellan Excel och/eller Google-blad. Tänk på att datumet bör vara MM-YY, så den 12 september och inte 12 september eller maj-12 och inte 05-12.

## Innan du börjar {#before-you-begin}

[!DNL Marketo Measure] innehåller 13 standardkanaler som kan användas eller expanderas efter. Dessutom kan upp till 40 online- och offlinekanaler skapas för att passa er unika marknadsföringsstruktur. På grundval av detta kan sammanlagt 200 delkanaler skapas för att stödja dessa online- och offlinekanaler.

[!DNL Marketo Measure] hämtar automatiskt marknadsföringskanalkostnader från plattformar som den har en API-integrering med, till exempel Bing Ads och Google AdWords. Kostnader för plattformar som inte är integrerade med [!DNL Marketo Measure] måste överföras manuellt. Marknadsföringskanalerna bör skapas innan kostnadsdata överförs.

## Överför marknadsföringskostnader {#uploading-marketing-costs}

När marknadsföringskanaler och regler har skapats eller uppdaterats kan de tillhörande kostnaderna överföras. Gör så här:

**Steg 1: Navigera till sidan Marketing Spend i [!DNL Marketo Measure] App.**

Gå till menyn **[!UICONTROL My Account]**, klicka på **[!UICONTROL Settings]** och navigera sedan till alternativet **[!UICONTROL Marketing Spend]** på vänster sidofält under avsnittet **[!UICONTROL Reporting]**.

![Gå till menyn Mitt konto, klicka på Inställningar och sedan](assets/spend-management-4.png)

**Steg 2: Hämta CSV-filen för aktuella kostnader**

Navigera till höger på skärmen och klicka på **[!UICONTROL Download Current Costs].** Med det här alternativet kan du hämta ett kalkylblad i CSV-format.

![Navigera till höger på skärmen och klicka på Hämta aktuell](assets/spend-management-1.png)

**Steg 3: Öppna CSV-filen och gör ändringar**

Du kan importera filen och öppna den med Google Sheets, Apple Numbers, Microsoft Excel eller med något annat program. [!DNL Marketo Measure] rekommenderar att du använder Google Sheets.

När du har importerat kalkylbladet kan du göra önskade ändringar, till exempel lägga till kostnader i kanaler och underkanaler eller uppdatera befintlig information.

Kontrollera logikreglerna i bladet. Varje rad ska innehålla en kanal och en av dess delkanaler avgränsade med en (.) punkt i slutet. Det är viktigt att använda detta format konsekvent.

Om du till exempel vill ange Facebook som underkanal och social som kanal ska regeln skrivas så här:&quot;Social.Facebook&quot;. Om du vill spåra en offlinehändelse bör kanalsyntaxen vara:&quot;Events.Big Conference&quot;. Exempel visas i bilden nedan:

![Om du till exempel vill ange Facebook som underkanal och social som ](assets/spend-management-2.png)

_Ytterligare information_:

Ändra inte datumen i kalkylbladet eftersom det kan orsaka problem när dokumentet överförs.

Lämna inga fält tomma. Även om det inte finns något dollarvärde att lägga till anger du $0 som dollarbelopp.

Bing Ads- och Google AdWords-kostnader behöver inte anges eller uppdateras eftersom [!DNL Marketo Measure] automatiskt hämtar dessa data från sin API-anslutning till dessa plattformar.

**Steg 4: Spara filen i CSV-format**

Om du arbetar i Google Sheets måste du hämta filen först. Undvik eller ta bort månadsdata eftersom det orsakar problem när CSV-filen ska överföras till [!DNL Marketo Measure] senare.

**Steg 5: Överför CSV-filen**

Gå till avsnittet **[!UICONTROL Cost]** i appen [!DNL Marketo Measure] och klicka på **[!UICONTROL Upload.CSV]**. Systemet uppdateras och den nya informationen visas.

## Vanliga frågor och svar {#faq}

**Varför visas siffror i CSV**?

Om inget värde anges på en högre nivå, som Kanal eller Delkanal, kommer [!DNL Marketo Measure] automatiskt att summera de underordnade nivåerna för dig, som presenteras när filen har överförts. Om summan av de underordnade är mindre än ett värde som angetts för det överordnade objektet lägger [!DNL Marketo Measure] till en&quot;Annan&quot;-rad för att visa skillnaden i summan.

**Hur bestäms kampanjerna i listan som jag ser?**

För närvarande listar våra resultat kampanjer som vi har sett bli meriter med en kontaktyta. Om det fanns aktivitet från en kampanj visar vi att Campaign baseras på det slutpunktsdatum som den inträffade.

**Det finns för många rader och kolumner att gå igenom. Kan jag konsolidera vyn?**

Eftersom du kan ändra datumintervallet, filtrera kanalen eller söka efter värden, kan du konsolidera tabellresultaten så att de passar dina behov bättre.

**Varför kan jag inte överföra en fil?**

Vi har olika behörighetsgrupper i appen [!DNL Marketo Measure]. Om du vill överföra en fil måste du vara en AccountAdmin. Du kan kringgå detta genom att begära åtkomst från din AccountAdmin eller låta din AccountAdmin överföra filen åt dig. En lista över användare och deras roller finns under **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL View/Add Account Users]**.
