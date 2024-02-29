---
description: Förklaring av kontaktpunktspositioner och generering över BT och BAT - [!DNL Marketo Measure]
title: Förklaring av kontaktpunktspositioner och generering över BT:er och [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Förklaring av kontaktpunktspositioner och generering över BT:er och [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generering av kontaktpunktspositioner och -flöde via köparresan**

Att förstå Buyer Touchpoint-positioner och hur de aktiveras är avgörande för att kunna rapportera framgångsrikt med [!DNL Marketo Measure] data. Ni vill ha en tydlig förståelse för vad era potentiella kunder gjorde när de rörde sig genom köparens resa och i sin tur hur det kommer att se ut i kontaktpunktsinformationen. Om du vill ha mer information om det här ämnet rekommenderar vi att du läser [[!UICONTROL Touchpoint Generation & Mapping]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md) artikel.

[!DNL Marketo Measure] har en mängd olika Touchpoint-positioner som aktiveras av olika steg i köparens resa. Vid rapportering på [!DNL Marketo Measure] data finns det två uppsättningar Touchpoint-data, Buyer Touchpoints (BT) och Buyer Attribution Touchpoints (BAT). Du kan lägga märke till att dessa datauppsättningar har lite olika positioner eftersom de relaterar till olika objekt. Om du vill ha mer information om det här ämnet rekommenderar vi att du läser [Skillnad mellan Buyer Touchpoints (BT) och Buyer Attribution Touchpoints (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md) artikel.

**Buyer Touchpoints (BT)**: Detta är de kontaktytor som är kopplade till en enskild person och deras resa och kommer att vara unika för den personen. Följande ur kartongrapporter är inbyggda i Buyer Touchpoint-data.

* [!DNL Marketo Measure] 101: Leads efter ID
* [!DNL Marketo Measure] 101: Leads efter kanal
* [!DNL Marketo Measure] 101: Lead/kontakt efter ID
* [!DNL Marketo Measure] 101: Lead/kontakt efter kanal

Nedan beskrivs Buyer Touchpoint-positionerna som beskriver var en individ befinner sig på sin resa och vilka åtgärder de vidtagit för att tjäna den positionen.

<table> 
 <tbody>
  <tr>
   <th>Affärsposition för köparens kontaktpunkt</th> 
   <th>Kontaktpunktstyp (åtgärd som kan utlösa kontaktyta)</th> 
   <th>Beskrivning av kontaktyta</th> 
  </tr>
  <tr>
   <td>Första beröring (FT)</td> 
   <td>Webbbesök</td> 
   <td>Den allra första marknadsföringsinteraktionen en individ har med ert varumärke</td> 
  </tr>
  <tr>
   <td>Skapa leads (LC)</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>Den allra första formulärfyllningen som en person har (vanligtvis en formulärinlämning men kan också vara en Campaign/Program-inkludering)</td> 
  </tr>
  <tr>
   <td>Post LC</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>Alla formulär som en enskild person fyller i efter sin LC (eller ett senare Kampanj-/programtillägg)</td> 
  </tr>
 </tbody>
</table>

**BATS (Buyer Attribution Touchpoints)**: Detta är de kontaktytor som är kopplade till ett säljprojekt och dess resa. Dessa kontaktytor kommer att kopplas till intäkterna eftersom de är kopplade till säljprojektet och dess kontakter. Följande ur kartongrapporter är inbyggda i data från Buyer Attribution Touchpoint.

* [!DNL Marketo Measure] 101: Affärsmöjligheter efter ID
* [!DNL Marketo Measure] 101: Affärsmöjligheter efter ID-kanal

<table> 
 <tbody>
  <tr>
   <th>BAT (Buyer Attribution Touchpoint) Position</th> 
   <th>Kontaktpunktstyp (åtgärd som kan utlösa kontaktyta)</th> 
   <th>Beskrivning av kontaktyta</th> 
  </tr>
  <tr>
   <td>Första beröring (FT)</td> 
   <td>Webbbesök</td> 
   <td>Den allra första marknadsföringsinteraktionen en kontakt hade med ert varumärke</td> 
  </tr>
  <tr>
   <td>Skapa leads (LC)</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>Den allra första formulärfyllningen som en kontakt hade (vanligtvis en formulärinlämning men kan också vara en Campaign/Program-inkludering)</td> 
  </tr>
  <tr>
   <td>Skapande av affärsmöjlighet</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Webbbesök <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>Marknadsföringsinteraktionen närmast när Opp skapas</td> 
  </tr> 
  <tr>
   <td>Stängd vunnen/förlorad</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Webbbesök <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>Marknadsföringsinteraktionen närmast när Opp stängs (Won eller Lost)</td> 
  </tr>
  <tr>
   <td>Mittpekningar</td> 
   <td>Formulärfyllning <strong>ELLER</strong> Kampanj-/programinkludering</td> 
   <td>När en kontakt fyller i ett onlineformulär och det inte sammanfaller med en milstolpe-kontaktyta</td> 
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] har dessa två uppsättningar med kontaktpunktsdata för att skapa en tydlig förståelse för en enskild persons resa och möjligheter. Dessa två datauppsättningar för kontaktpunkter ger dig en tydlig karta över vad som hände uppifrån och ned på tratten.

I följande exempel visas dataflödet från Buyer Touchpoints (BT) till Buyer Attribution Touchpoints (BAT). I det här exemplet är både person A och person B en del av samma möjlighet som har ett Skapat den 3 juli 2020 och ett stängningsdatum den 5 juni 2020.

**Person A** Buyer Touchpoint-datauppsättning

* First Touch (FT) - Paid Search.AdWords - 9/1/2019
* Lead Creation (LC) - Organic Search.Google - 20/11-11
* Post LC (form fill) - Webinar - 3/4/2020

**Person B** Buyer Touchpoint-datauppsättning

* First Touch (FT) - Paid Social.Facebook - 2019-08-26
* Leadprojekt - Organic Search.Yahoo - 2/20/2020
* Post LC (form fill) - Email - 5/1/2020

**Möjligheter** Kontaktpunktsdata för Buyer Attribution lästes så här..

* First Touch (FT) - Paid Social.Facebook - 2019-08-26
   * (från **Person B** eftersom de har det sanna _Första beröring_ för kontot/Opp)
* Lead Creation (LC) - Organic Search.Google - 20/11-11
   * (från **Person A** eftersom de har det sanna _Skapa leads_ för kontot/Opp)
* Skapande av affärsmöjligheter - webbinarium - 3/4/2020
   * (Post LC-kontaktyta från **Person A** skulle vara _OC-kontaktyta_ därför att det var den senaste interaktionen till den möjlighet som skapades den 3 juli 2020)
* Closed Won - Email - 5/1/2020
   * (Post LC-kontaktyta från **Person B** skulle vara _Sluten Won-kontaktyta_ eftersom det var den senaste interaktionen till att affärsmöjligheten stängdes den 5 juni 2020)
