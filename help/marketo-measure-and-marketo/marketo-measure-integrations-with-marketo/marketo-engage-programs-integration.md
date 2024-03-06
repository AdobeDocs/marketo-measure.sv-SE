---
unique-page-id: 42762729
description: "[!DNL Marketo Engage] Programintegrering - [!DNL Marketo Measure]"
title: "[!DNL Marketo Engage] Programintegrering"
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
feature: Integration
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---

# [!DNL Marketo Engage] Programintegrering {#marketo-engage-programs-integration}

Via [!DNL Marketo Measure] integrering med [!DNL Marketo Engage] Med program kan våra kunder börja skapa kontaktytor för attribueringsspårning från Marketo-programmedlemskap. Med den här funktionen kan marknadsförare börja spåra programmedlemskap från e-post eller engagemangsprogram som annars inte syns av [!DNL Marketo Measure] javascript och ska mätas inom attribueringsresan.

## Tillgänglighet {#availability}

Alla lager.

## Krav {#requirements}

* Production Marketo, instans
* Production Salesforce eller Microsoft Dynamics-instans
* Valfritt [!DNL Marketo Measure] prenumeration
* Synkronisering av Marketo-användare har aktiverats ([!DNL Marketo Measure] Inställningar)
* Marketo-program aktiverade ([!DNL Marketo Measure] Inställningar)

## Inställningar {#setup}

**Regler**

1. Om du vill börja konfigurera regler för Marketo-program går du till **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Programs]**. Klicka på **+** för att börja skapa din första regel.

   ![](assets/one.png)

   ![](assets/two.png)

1. Du kan också ange ett namn för regeln om det gör det lättare att hålla reda på dem. först markerar du fältet för att definiera regeln i listan över fält för program- och programmedlemskap. Fortsätt att skapa regeln genom att markera operatorn och det förväntade värdet som ska kontrolleras.

   ![](assets/three.png)

1. Lägg till en annan programsats i samma ruta för att ställa in ett &quot;och&quot;-villkor i regeln eller klicka på +-ikonen utanför rutan för att ställa in en &quot;eller&quot;-programsats.

   ![](assets/four.png)

1. Välj vilket datum eller datum/tid-fält som ska användas för att mappa till slutpunktsdatumet. Ange en klammerparentes om du vill se en lista över värden som är tillgängliga från Marketo `{` så visas de tillgängliga fälten.

   ![](assets/five.png)

   >[!NOTE]
   >
   >Om din regel vill hämta aktivitetsdatumet, eller det datum då en programmedlem uppnådde en viss status, vill du använda [!DNL Marketo Engage] Aktivitetsintegrering och ange en regel för aktivitetstypen Ändra status i progression.

   ![](assets/six.png)

Den färdiga regeln ska se ut ungefär så här:

## Testa {#test}

När du har skapat några regler kanske du vill testa dem för att verifiera att satsen matchar dina program.

1. Om du vill köra ett test klickar du på **[!UICONTROL TEST]** enligt nedan.

   ![](assets/seven.png)

1. En modal visas där du kan ange program-ID från Marketo.

   ![](assets/eight.png)

   När du har angett ID:t klickar du på [!UICONTROL Test] -knappen kommer vår regelmotor att gå igenom varje regel och avgöra om programmet passar in i någon av reglerna eller inte. I exemplet nedan kan du se att Program 1002, som kallas [!DNL Marketo Measure] Ebook har fem programmedlemmar och är berättigad på grund av den regel som visas.

   Reglerna körs på en exempelstorlek på 5 000 medlemmar. Om ditt program innehåller fler än 5 000 medlemmar är det möjligt att vi inte kontrollerar kompatibiliteten för alla medlemmar. Det här verktyget fungerar bara som ett sätt att kontrollera att reglerna är korrekt konstruerade.

   ![](assets/nine.png)

   Du kan klicka på Antal medlemmar för att visa en lista över Marketo People ID:n som är berättigade inom programmet.

   ![](assets/ten.png)

## Kanalmappning {#channel-mapping}

I listan över Marketo-programkanaler vill du mappa värdena till [!DNL Marketo Measure] anpassade marknadsföringskanaler som du har skapat i Inställningar. Alla kontaktytor som genereras av dessa program ärver kanalnamn och underkanalsnamn som du väljer här.

1. Börja med att navigera till **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

1. Överst har du möjlighet att mappa till dina CRM-kampanjtyper. Nedan visas alternativen för dina Marketo-programkanaler.

1. Markera först den kanal som ska mappas till värdet och välj sedan delkanalen om du vill. Klicka på **[!UICONTROL Save]** längst ned.

   ![](assets/eleven.png)

## Programkostnader {#program-costs}

Genom dataimporten av Marketo-program laddas kostnaderna automatiskt ned från Period-kostnader och den rapporterade kostnaden i Marketo fördelas över den tilldelade månaden. Om till exempel $1000 rapporteras för januari 2021 delas $1000 upp på 31 dagar. Kostnaderna finns i [!DNL Marketo Measure Discover].

## Så här fungerar det {#how-it-works}

**Fältmappningar**

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <th>biz_ad_campaign</th> 
   <th>Marketo</th> 
  </tr> 
  <tr> 
   <td>ID</td> 
   <td>id</td> 
  </tr> 
  <tr> 
   <td>IS_DELETED</td> 
   <td>(kontrollera om programmet fortfarande finns via API)</td> 
  </tr> 
  <tr> 
   <td><p>NAMN</p></td> 
   <td>name</td> 
  </tr> 
 </tbody> 
</table>

| biz_campaign_members | Marketo |
|---|---|
| ID | &quot;MarketoProgramMembership&quot;_ProgramId_Lead ID |
| MODIFIED_DATE | updatedAt |
| CREATED_DATE | membershipDate |
| LEAD_ID | ID (listmedlemskap) |
| LEAD_EMAIL | E-post (lista över medlemskap) |
| STATUS | progressStatus |
| HAS_RESPONDED | foundStatus |
| CAMPAIGN_NAME | programName |
| CAMPAIGN_ID | programId |
| CAMPAIGN_TYPE | kanal |

## Cookie-mappning {#cookie-mapping}

Som ett resultat av [!DNL Marketo Measure] integrering med Marketo, [!DNL Marketo Measure] Cookie-ID har nu också mappats och synkroniserats med [!DNL Marketo Munchkin Id]. Detta gör att luckan stängs så att den anonyma första beröringen kan kopplas till en webbsession i stället för att både FT- och LC-beröringen kan kopplas till en Marketo-aktivitet. Tänk dig detta scenario:

Markera klickar på en [!DNL Facebook] och får plats på wayneenterprises.com där han eller hon kan komma till [!DNL Marketo Measure] ID 123 och [!DNL Marketo Munchkin Id] 456. Ingen formulärifyllning sker.

Wayne Enterprises Marketing-teamet skickar ett e-postmeddelande till specifika riktade leads, där en av dem `mark@email.com`.

`mark@email.com` får e-post och klickningar igenom och får plats på wayneenterprises.com. Detta blir `mark@email.com's` andra besök på `wayneenterprise.com` med samma cookie-ID, men det fanns ingen formulärfyllning, så att [!DNL Marketo Measure]är de fortfarande anonyma besökare.

Wayne Enterprises Marketing-teamet skapar en aktivitetsregel för Marketo för att generera kontaktytor för aktivitetstypen&quot;Click Email&quot;.

Implementeringen skulle skapa en enda kontaktyta för FT och LC för `mark@email.com` från Marketo Activity från aktivitetstypen Click Email.

Tack vare den här förbättringen av cookie-mappningen går FT tillbaka och får ett kreditbetyg på [!DNL Facebook] och LC:n krediteras e-postmeddelandet.

>[!NOTE]
>
>Med funktionen för cookie-mappning kan du hitta några LC-kontaktytor som kommer från ett webbbesök. Det är möjligt att ett lead visades i Marketo utan någon tillhörande aktivitet, och sedan [!DNL Marketo Measure] ladda ned leadet, matchade de associerade cookies och spårade det sedan till den senaste webbsessionen, även om det inte fanns någon formuläraktivitet som skapade leadet.

## Vanliga frågor och svar {#faq}

**Hur anger jag att slutpunktsdatumet ska vara progressionsdatumet eller datumet då statusändringen inträffade för min programmedlem?**

Om din regel vill hämta aktivitetsdatumet, eller det datum då en programmedlem uppnådde en viss status, vill du använda [!DNL Marketo Engage] Aktivitetsintegrering och ange en regel för aktivitetstypen Ändra status i progression. I annat fall [!DNL Marketo Engage] Programintegrering gör bara Datum för medlemskap tillgängligt, vilket är det första datumet som tog med Marketo-personen till programmet, även om det finns flera statusar.

**Kan jag få en lista med datumalternativ för slutpunktsdatumet?**

Starta den automatiska kompletteringen genom att ange en klammerparentes `{` i textfältet visas de tillgängliga fälten.

**Om jag skapar Marketo-programregler och även har CRM Campaign-regler, kommer de då att räknas två gånger?**

Det beror på din regeldefinition, men möjligen, ja. du vill utvärdera din regeluppsättning så att du inte har regler som omfattar ett program och en kampanj eftersom vi inte kommer att avduplicera eller upptäcka om du har liknande medlemskap. En möjlig lösning är att kopiera över Campaign-reglerna till Program om ni vill att Marketo ska vara den enda källan till sanning och sedan ta bort Campaign-reglerna. Ett annat alternativ är att lägga till ett&quot;CreatedOn&quot;- eller&quot;CreatedDate&quot;-villkor i reglerna, så att regler före ett visst datum kommer att använda kampanjregler och kampanjregler efter ett visst datum. Det finns många provisoriska lösningar, men det kommer att kräva viss planering och samordning.

**Kan anpassade fält för Marketo-medlemskap definieras?**

På grund av tekniska begränsningar kan vi för tillfället inte stödja anpassade fält för programmedlemskap. När dessa fält är tillgängliga via ytterligare Marketo API:er visas de för oss och visas för dig.

**Hur vet jag om jag ska använda program eller aktiviteter?**

The [!DNL Marketo Engage] Programintegrering är ett enkelt sätt att generera kontaktytor baserat på om en person är programmedlem eller inte. Om du är intresserad av att definiera en regel baserat på den tidpunkt då en person ändrar till en viss programstatus, visas [!DNL Marketo Engage] Aktivitetsintegrering blir den inställning du vill ha, särskilt aktivitetstypen &quot;Ändra status i progression&quot;.
