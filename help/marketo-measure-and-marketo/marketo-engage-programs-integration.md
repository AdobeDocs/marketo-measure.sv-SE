---
description: Integrering av [!DNL Marketo Engage] program - [!DNL Marketo Measure]
title: Integrering av [!DNL Marketo Engage] program
exl-id: c26087e3-d821-4fe7-bacd-eeaa1530a4b0
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 0%

---


# Integrering av [!DNL Marketo Engage] program {#marketo-engage-programs-integration}

Genom integreringen av [!DNL Marketo Measure] med [!DNL Marketo Engage]-program kan våra kunder börja skapa kontaktytor för attribueringsspårning från Marketo-programmedlemskap. Med den här funktionen kan marknadsförare börja spåra programmedlemskap från e-post eller engagemangsprogram som annars inte syns av [!DNL Marketo Measure] javascript och som ska mätas inom attribueringsresan.

## Tillgänglighet {#availability}

Alla lager.

## Krav {#requirements}

* Production Marketo, instans
* Production Salesforce eller Microsoft Dynamics
* Valfri betald [!DNL Marketo Measure]-prenumeration
* Synkronisering av Marketo-användare har aktiverats ([!DNL Marketo Measure] inställningar)
* Marketo-program har aktiverats ([!DNL Marketo Measure] inställningar)

## Inställningar {#setup}

**Regler**

1. Om du vill börja konfigurera regler för Marketo-program går du till **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Programs]**. Klicka på ikonen **+** för att börja skapa din första regel.

   ![Sidan Programinställningar i Marketo Measure-kontot](assets/one.png)

   ![Dialogrutan Skapa ny regel med knappen Lägg till](assets/two.png)

1. Du kan också ange ett namn för regeln om det gör det lättare att hålla reda på dem. först markerar du fältet för att definiera regeln i listan över fält för program- och programmedlemskap. Fortsätt att skapa regeln genom att markera operatorn och det förväntade värdet som ska kontrolleras.

   ![Regelverktyget med listruta för fältval och operatörsalternativ](assets/three.png)

1. Lägg till en annan programsats i samma ruta för att ställa in ett &quot;och&quot;-villkor i regeln eller klicka på +-ikonen utanför rutan för att ställa in en &quot;eller&quot;-programsats.

   ![Regelverktyget visar flera villkor med och/eller logikalternativ](assets/four.png)

1. Välj vilket datum eller datum/tid-fält som ska användas för att mappa till slutpunktsdatumet. Om du vill visa en lista med värden som är tillgängliga från Marketo anger du klammerparentesen `{` så visas de tillgängliga fälten.

   ![Mappning av datumfält med automatisk ifyllning som visar tillgängliga fält](assets/five.png)

   >[!NOTE]
   >Om din regel vill hämta aktivitetsdatumet, eller det datum då en programmedlem uppnådde en viss status, vill du använda aktivitetsintegrationen [!DNL Marketo Engage] och ställa in en regel för aktivitetstypen Ändra status i progression.

   ![Regelkonfigurationen har slutförts och visar fältmappningar och villkor](assets/six.png)

Den färdiga regeln ska se ut ungefär så här:

## Test {#test}

När du har skapat några regler kanske du vill testa dem för att verifiera att satsen matchar dina program.

1. Om du vill köra ett test klickar du på knappen **[!UICONTROL TEST]** så som visas nedan.

   ![Knappen Testa i programregelgränssnittet](assets/seven.png)

1. En modal visas där du kan ange program-ID från Marketo.

   ![Testa modal dialogruta med indatafält för program-ID](assets/eight.png)

   När du anger ID:t och klickar på knappen [!UICONTROL Test] går vår regelmotor igenom varje regel och avgör om programmet passar in i någon av reglerna eller inte. I exemplet nedan ser du att Program 1002, som kallas [!DNL Marketo Measure] Ebook, har fem programmedlemmar och är berättigade på grund av den regel som visas.

   Reglerna körs på en exempelstorlek på 5 000 medlemmar. Om ditt program innehåller fler än 5 000 medlemmar är det möjligt att vi inte kontrollerar kompatibiliteten för alla medlemmar. Det här verktyget fungerar bara som ett sätt att kontrollera att reglerna är korrekt konstruerade.

   ![Testresultat som visar matchat program med medlemsantal](assets/nine.png)

   Du kan klicka på Antal medlemmar för att visa en lista över Marketo People ID:n som är berättigade inom programmet.

   ![Lista över Marketo-id:n som är berättigade från testresultaten](assets/ten.png)

## Kanalmappning {#channel-mapping}

I listan över Marketo-programkanaler vill du mappa värdena till de [!DNL Marketo Measure] anpassade marknadsföringskanalerna som du har skapat i Inställningar. Alla kontaktytor som genereras av dessa program ärver kanalnamn och underkanalsnamn som du väljer här.

1. Börja med att gå till **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

1. Överst har du möjlighet att mappa till dina CRM-kampanjtyper. Nedan visas alternativen för dina Marketo-programkanaler.

1. Markera först den kanal som ska mappas till värdet och välj sedan delkanalen om du vill. Klicka **[!UICONTROL Save]** längst ned när du är klar.

   ![Inställningar för offlinekanaler som visar mappningsalternativ för Marketo-programkanal](assets/eleven.png)

## Programkostnader {#program-costs}

Genom dataimporten av Marketo-program laddas kostnaderna automatiskt ned från Period-kostnader och den rapporterade kostnaden i Marketo fördelas över den tilldelade månaden. Om till exempel $1000 rapporteras för januari 2021 delas $1000 upp på 31 dagar. Kostnaderna finns i [!DNL Marketo Measure Discover].

>[!NOTE]
>
>Marketo Measure stöder endast en periodkostnadspost per månad. För att säkerställa att alla kostnader importeras, sammanställer du den totala månadskostnaden till ett enda bidrag. Det finns inte stöd för flera periodkostnadstransaktioner för samma månad.

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

Som ett resultat av integreringen av [!DNL Marketo Measure] med Marketo mappas och synkroniseras nu även cookie-ID:t [!DNL Marketo Measure] med [!DNL Marketo Munchkin Id]. Detta gör att luckan stängs så att den anonyma första beröringen kan kopplas till en webbsession i stället för att både FT- och LC-beröringen kan kopplas till en Marketo-aktivitet. Tänk dig detta scenario:

Markera klickar på en [!DNL Facebook]-annons och går till wayneenterprises.com där han eller hon cookies med [!DNL Marketo Measure] Id 123 och [!DNL Marketo Munchkin Id] 456. Ingen formulärifyllning sker.

Wayne Enterprises Marketing-teamet skickar ett e-postmeddelande till specifika riktade leads, varav en är `mark@email.com`.

`mark@email.com` får e-postmeddelandet och klickar igenom och får plats på wayneenterprises.com. Detta blir `mark@email.com's` andra besök på `wayneenterprise.com` med samma cookie-id, men det fanns ingen formulärfyllning, så för [!DNL Marketo Measure] är de fortfarande en anonym besökare.

Wayne Enterprises Marketing-teamet skapar en aktivitetsregel för Marketo för att generera kontaktytor för aktivitetstypen&quot;Click Email&quot;.

Dagens implementering skulle skapa en enda FT- och LC-kontaktyta för `mark@email.com` från Marketo Activity från aktivitetstypen Click Email.

Den här förbättringen av cookie-mappningen innebär att FT återgår och krediteras [!DNL Facebook]-annonsen och att LC:n krediteras e-postmeddelandet.

>[!NOTE]
>Med funktionen för cookie-mappning kan du hitta några LC-kontaktytor som kommer från ett webbbesök. Det är möjligt att ett lead visades i Marketo utan någon associerad aktivitet. [!DNL Marketo Measure] laddade sedan ned leadet, matchade de associerade cookies och spårade det sedan till den senaste webbsessionen, även om det inte fanns någon formuläraktivitet som skapade leadet.

## Vanliga frågor och svar {#faq}

**Hur anger jag att slutpunktsdatumet ska vara progressionsdatumet eller datumet då statusändringen inträffade för min programmedlem?**

Om din regel vill hämta aktivitetsdatumet, eller det datum då en programmedlem uppnådde en viss status, vill du använda aktivitetsintegrationen [!DNL Marketo Engage] och ställa in en regel för aktivitetstypen Ändra status i progression. I annat fall blir medlemskapsdatumet (Membership Date) bara tillgängligt i [!DNL Marketo Engage]-programintegreringen, vilket är det första datum som tog med Marketo-personen till programmet, även om det finns flera statusvärden.

**Kan jag hämta en lista med datumalternativ för slutpunktsdatumet?**

Om du vill aktivera den automatiska slutföringen börjar du med att ange klammerparentesen `{` i textfältet. Då visas de tillgängliga fälten.

**Om jag skapar Marketo-programregler och även har CRM Campaign-regler, kommer de att räknas två gånger?**

Det beror på din regeldefinition, men möjligen, ja. du vill utvärdera din regeluppsättning så att du inte har regler som omfattar ett program och en kampanj eftersom vi inte kommer att avduplicera eller upptäcka om du har liknande medlemskap. En möjlig lösning är att kopiera över Campaign-reglerna till Program om ni vill att Marketo ska vara den enda källan till sanning och sedan ta bort Campaign-reglerna. Ett annat alternativ är att lägga till ett&quot;CreatedOn&quot;- eller&quot;CreatedDate&quot;-villkor i reglerna, så att regler före ett visst datum kommer att använda kampanjregler och kampanjregler efter ett visst datum. Det finns många provisoriska lösningar, men det kommer att kräva viss planering och samordning.

**Kan anpassade fält för Marketo-programmedlemskap definieras?**

På grund av tekniska begränsningar kan vi för tillfället inte stödja anpassade fält för programmedlemskap. När dessa fält är tillgängliga via ytterligare Marketo API:er visas de för oss och visas för dig.

**Hur vet jag om jag ska använda program eller aktiviteter?**

Integreringen av [!DNL Marketo Engage]-program är ett enkelt sätt att generera kontaktytor baserat på om en person är programmedlem eller inte i ett program. Om du är intresserad av att definiera en regel baserat på den tid en person ändrar till en viss programstatus, kommer [!DNL Marketo Engage] aktivitetsintegrering att vara den inställning du vill ha, särskilt aktivitetstypen Ändra status i progression.
