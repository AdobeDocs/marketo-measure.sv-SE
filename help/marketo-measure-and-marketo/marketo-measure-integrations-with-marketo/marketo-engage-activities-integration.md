---
unique-page-id: 42762749
description: "[!DNL Marketo Engage] Verksamhetsintegrering - [!DNL Marketo Measure]"
title: "[!DNL Marketo Engage] Verksamhetsintegrering"
exl-id: 463ad9b2-e1bd-49dd-8bf5-0da7b7132f05
feature: Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 0%

---

# [!DNL Marketo Engage] Integrering av aktiviteter {#marketo-engage-activities-integration}

Som en del av det övergripande [!DNL Marketo Measure] och [!DNL Marketo Engage] Integrationen innebär att den här satsningen på Marketo Activity spelar en stor roll. Genom Marketo-aktiviteter spårar systemet händelser som Click Email (E-post), Change Score (Ändra bakgrundsmusik) eller Change Status (Ändra status i progression) - dessa aktivitetstyper kan separeras och definieras för att välja en delmängd som är berättigad till kontaktytor. När kontaktytor har skapats för dessa aktiviteter spåras de i engagemangsresan och mäts tillsammans med andra marknadsföringskanaler som betalsökningar eller partnermarknadsföring.

## Krav {#requirements}

* Production Marketo, instans
* Produktion [!DNL Salesforce] eller [!DNL Microsoft Dynamics] instance
* Valfritt [!DNL Marketo Measure] prenumeration
* Synkronisering av Marketo-användare har aktiverats ([!DNL Marketo Measure] Inställningar)
* Marketo-program aktiverade ([!DNL Marketo Measure] Inställningar)
* Marketo-aktiviteter aktiverade ([!DNL Marketo Measure] Inställningar)

## Inställningar {#setup}

1. Börja konfigurera Marketo Activity genom att navigera till **Mitt konto** > **Inställningar** > **Verksamhet**.

   ![](assets/one-1.png)

   ![](assets/two-1.png)

   Det första som krävs är att välja en lista med aktivitetstyper som du tänker bygga regler på. Det behövs inget stort antal aktivitetstyper, men vi rekommenderar också att du inte överbelastar dina kontaktytor och tonar ned vikten av viktiga milstolpar. Därför behöver du kanske inte fler än fem aktivitetstyper för att spåra relevanta åtaganden.

1. Klicka på listrutan under [!UICONTROL Select Activities Types] för att börja välja de olika typerna.

   ![](assets/three-1.png)

1. När du har valt alla aktiviteter du behöver visas de också i [!UICONTROL Selected Activities List] samt under [!UICONTROL Define Rules].

   ![](assets/four-1.png)

1. För varje aktivitetstyp måste du definiera en eller flera regler som avgör vilka poster som är berättigade för kontaktytor. Vi ska till exempel lägga till en regel för aktivitetstypen&quot;Change Score&quot; så att systemet skapar en kontaktyta när en Marketo-person når en poäng på 90 eller högre.

1. Först, beroende på aktivitetstypen, kan du behöva konfigurera en [!DNL Marketo Measure] Kampanjnamn som kan användas senare för kanalmappning. [!DNL Marketo Measure] Kampanjnamn kan återanvändas i flera regler. Detta hjälper till att få bredare namn som kan användas i en kanalregel. Alla aktivitetstyper innehåller inte ett Marketo-program och därför behövs ett namn som första steg.

   Här är ett exempel på hur det här extra steget skulle se ut:

   ![](assets/five-1.png)

1. I vårt exempel&quot;Change Score&quot; behöver vi inte ange ett kampanjnamn eftersom vi kan hämta informationen från Marketo-programmet. Nu kan du skapa regeluttrycket. I följande exempel vill vi markera fältet &quot;[!UICONTROL New Value]&quot; med en operator i &quot;[!UICONTROL is greater than]&quot; med värdet 90.

   Du kan utöka reglerna och lägga till ytterligare filter eller villkor genom att lägga till programsatserna &quot;och&quot; eller &quot;eller&quot; för att begränsa resultatet.

   ![](assets/six-1.png)

   ![](assets/seven-1.png)

1. Välj slutligen det som ska användas som slutpunktsdatum. Alla tillgängliga datum- och datum-/tidsfält visas här från Marketo. Om du inte har anpassade datumfält visas &quot;[!UICONTROL Activity Date].&quot;

   ![](assets/eight-1.png)

1. Var noga med att klicka **[!UICONTROL Save As Draft]** längs vägen så att du inte förlorar ändringarna.

   ![](assets/nine-1.png)

1. Navigera till fliken **[!UICONTROL Attribute Mapping]**.

   ![](assets/ten-1.png)

1. För varje aktivitetstyp som du har valt kan du mappa ytterligare Marketo-attribut till Touchpoint-fält så att du kan visa och rapportera dessa värden i [!DNL Marketo Measure Discover] eller i CRM.

   Många av fälten har automatiskt mappats och kan inte ändras för att vara i linje med våra övriga integreringar. Se avsnittet Fältmappningar nedan för att hitta dessa värden. För vissa aktivitetstyper innehåller Marketo attribut för en landningssida, referenssida eller webbläsare som du kan mappa till ett Touchpoint-fält. I exemplet nedan har vi lagt till några förslag som kan tas bort.

1. Välj fältet Buyer Touchpoint i den vänstra kolumnen som du vill mappa till. Välj sedan det Marketo-attribut som du vill fylla i i fältet Buyer Touchpoint. Kom ihåg att dessa är valfria, extra mappningar utöver dem som [!DNL Marketo Measure] har redan etablerats.

   Mappningsbara fält:

   * Ort
   * Land
   * Län
   * Landningssida
   * Referentsida
   * Formulärsida
   * Formulärdatum
   * Plattform
   * Webbläsare

   >[!NOTE]
   >
   >Annonsfält som annonsinnehåll eller nyckelord är inte tillgängliga i den här listan eftersom de är reserverade för våra annonsplattformsintegreringar.

## Typ av aktivitet {#activity-types}

En del aktivitetstyper ger oss program-ID och programnamn, så det är enkelt att mappa det till kampanj-ID och kampanjnamn på Buyer Touchpoint. För andra finns det ingen programassociation, så en del av regeldefinitionen kräver att du skapar en [!DNL Marketo Measure] Kampanjnamn. Nedan finns en lista över varje kategori:

**Aktivitetstyper med program-ID**

Skicka e-post (6)\
E-post levererad (7)\
E-post studsad (8)\
Avbeställ e-post (9)\
Öppna e-post (10)\
Klicka på E-post (11)\
Ändra datavärde (13)\
Ändra poäng (22)\
Lägg till i lista (24)\
Ändra status i progression (104)\
Lägg till i struktur (113)\
Ändra vårdnad (115)

>[!NOTE]
>
>Av de aktivitetstyper där vi förväntar oss ett program-ID, om en aktivitet upptäcks utan ett program, [!DNL Marketo Measure] kommer inte att acceptera det som en giltig kontaktyta eftersom vi inte kan ha Null Campaign-värden.

**Aktivitetstyper utan program-ID**

Klicka på Länk (3)\
Ny lead (12)\
Synkronisera lead till SFDC (19)\
Konvertera lead (21)\
Ändra ägare (23)\
Ta bort från lista (25)\
SFDC-aktivitet (26)\
Mjuk e-postbaserad (27)\
Ta bort lead från SFDC (29)\
Sammanfoga leads (32)\
Lägg till i säljprojekt (34)\
Ta bort från affärsmöjlighet (35)\
Uppdatera säljprojekt (36)\
Ta bort lead (37)\
Skicka varning (38)\
Skicka e-post för försäljning (39)\
Open Sales Email (40)\
Klicka på E-postadress (41)\
Lägg till i SFDC-kampanj (42)\
Ta bort från SFDC-kampanj (43)\
Ändra status i SFDC-kampanj (44)\
Ta emot e-post för försäljning (45)\
Begär kampanj (47)\
E-postförsäljning studsad (48)\
Ändra intäktsfas (101)\
Ändra intäktsfas manuellt (102)\
Ändra segment (108)\
Ring Webkrok (110)\
Skickat Vidarebefordra till väns-e-post (111)\
Vidarebefordrad till väns-e-post (112)\
Change Nurture Track (114)\
Push Lead to Marketo (145)\
Synkronisera lead till Microsoft (300)\
Dialogrutan Dela innehåll (400) Aktiverad (158) Dokumentinteragerad med (159) Dialogrutans avtalade tid (160) Dialogrutan Mål har uppnåtts (161) Anpassad aktivitet (xxx)

## Kanalmappning {#channel-mapping}

För alla regler från en aktivitetstyp med ett program-ID bestäms Marketo-programkanalen av Programmet. Vi använder programkanalen för att mappa till dina anpassade offlinekanaler, så du måste se till att kanalerna är korrekt konfigurerade [enligt instruktionerna här](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping).

Och för alla regler från en aktivitetstyp utan program-ID var det första steget att skapa ett kampanjnamn. Använd det här kampanjnamnet för att konfigurera anpassade onlinekanaler [som anges här](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md).

Om kanalerna för dina Marketo-aktiviteter inte är korrekt konfigurerade, kommer troligtvis dina nya kontaktytor att hamna under andra kanaler.

## Programkostnader {#program-costs}

Genom dataimporten av Marketo-program laddas kostnaderna automatiskt ned från Period-kostnader och den rapporterade kostnaden i Marketo fördelas över den tilldelade månaden. Om till exempel $1000 rapporteras för januari 2021 delas $1000 upp på 31 dagar. Kostnaderna finns i [!DNL Marketo Measure Discover].

## Cookie-mappning {#cookie-mapping}

Som ett resultat av [!DNL Marketo Measure] integrering med Marketo, [!DNL Marketo Measure] Cookie-ID har nu också mappats och synkroniserats med [!DNL Marketo Munchkin Id]. Detta gör att luckan stängs så att den anonyma första beröringen kan kopplas till en webbsession i stället för att både FT- och LC-beröringen kan kopplas till en Marketo-aktivitet. Tänk dig detta scenario:

Markera klickar på en Facebook-annons och går till wayneenterprises.com där han eller hon cookas med [!DNL Marketo Measure] ID 123 och [!DNL Marketo Munchkin Id] 456. Ingen formulärifyllning sker.

Wayne Enterprises Marketing-teamet skickar ett e-postmeddelande till specifika riktade leads, där en av dem `mark@email.com`.

`mark@email.com` får e-postmeddelandet och klickningar och landar på `wayneenterprises.com`. Detta blir `mark@email.com's` andra besök på `wayneenterprise.com` med samma cookie-ID, men det fanns ingen formulärfyllning, så att [!DNL Marketo Measure]är de fortfarande anonyma besökare.

Wayne Enterprises Marketing-teamet skapar en aktivitetsregel för Marketo för att generera kontaktytor för aktivitetstypen&quot;Click Email&quot;.

Implementeringen skulle skapa en enda kontaktyta för FT och LC för `mark@email.com` från Marketo Activity från aktivitetstypen Click Email.

I och med den här förbättringen av cookie-mappningen kommer FT tillbaka och krediteras Facebook och LC:n kommer att krediteras e-postmeddelandet.

>[!NOTE]
>
>Med funktionen för cookie-mappning kan du hitta några LC-kontaktytor som kommer från ett webbbesök. Det är möjligt att ett lead visades i Marketo utan någon tillhörande aktivitet, och sedan [!DNL Marketo Measure] ladda ned leadet, matchade de associerade cookies och spårade det sedan till den senaste webbsessionen, även om det inte fanns någon formuläraktivitet som skapade leadet.

## Vanliga frågor och svar {#faq}

**Hur vet jag om jag ska skapa en regel för Marketo-program eller en regel för Marketo-aktiviteter?**

The [!DNL Marketo Engage] Programintegrering är ett enkelt sätt att generera kontaktytor baserat på om en person är programmedlem eller inte. Om du är intresserad av att definiera en regel baserat på den tidpunkt då en person ändrar till en viss programstatus, visas [!DNL Marketo Engage] Aktivitetsintegrering blir den inställning du vill ha, särskilt aktivitetstypen &quot;Ändra status i progression&quot; så att ditt slutpunktsdatum kan mappas till det systemgenererade aktivitetsdatumet.

**Varför trunkeras namnet på min Touchpoint-typ?**

Touchpoint-fältet skapades i [!DNL Marketo Measure] paket med 16 tecken. Om du ändrar teckengränsen för fältet måste det befintliga fältet tas bort och en ny skapas. Värdet för Touchpoint-typen är Aktivitetstyp, som också anges i fältet Medel.

**Varför visas inte min anpassade aktivitetstyp i listan över tillgängliga aktiviteter?**

Vi visar bara anpassade aktivitetstyper för Godkänd och inte Utkast eller Godkänd med Utkast.

**Hur avgör jag vilka aktivitetstyper jag vill generera en kontaktyta för?**

Även om det inte finns någon gräns för hur många aktivitetstyper du kan skapa rekommenderar vi vanligtvis inte fler än fem aktivitetstyper. Det tar tid att avgöra vilka marknadsföringsaktiviteter som är relevanta nog för att vara en del av kontaktytan. &quot;Avbeställ e-post&quot; kanske inte är en viktig kontaktyta att spåra, men &quot;Klicka på e-post&quot; med ytterligare filter kan vara bra. Det varierar mellan olika organisationer och team, så vi föreslår att ni samarbetar med era team för att brainstorma på den bästa metoden här.

**Varför är mitt webbläsarnamn inaktiverat?**

The [!DNL Marketo Measure] Webbläsarnamnet får innehålla högst 20 tecken, men användaragentvärdet som hämtas från Marketo kan vara en längre sträng.

BrowserInfo.Name\
BrowserInfo.Version\
PlatformInfo.Name\
PlatformInfo.Version
