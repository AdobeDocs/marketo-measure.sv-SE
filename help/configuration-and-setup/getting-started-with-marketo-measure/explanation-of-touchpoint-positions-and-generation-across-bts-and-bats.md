---
description: Förklaring av Touchpoint-positioner och generering över BT och BAT - [!DNL Marketo Measure]
title: Förklaring av Touchpoint-positioner och generering över BT:er och  [!DNL BATs]
exl-id: 4903f917-a366-4767-a126-5216d2377399
feature: Touchpoints
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---


# Förklaring av Touchpoint-positioner och generering över BT:er och [!DNL BATs] {#explanation-of-touchpoint-positions-and-generation-across-bts-and-bats}

**Generering av positionering och flöde för kontaktpunkter via köparresan**

Att förstå Buyer Touchpoint-positioner och hur de aktiveras är avgörande för att kunna rapportera med [!DNL Marketo Measure]-data. Ni vill ha en tydlig förståelse för vad era potentiella kunder gjorde när de rörde sig genom köparens resa och i sin tur hur det kommer att se ut i kontaktpunktsinformationen. Om du vill ha mer kontext om det här avsnittet rekommenderar vi att du läser artikeln [[!UICONTROL Touchpoint Generation & Mapping]](/help/configuration-and-setup/getting-started-with-marketo-measure/touchpoint-generation-and-mapping.md).

[!DNL Marketo Measure] har en rad olika Touchpoint-positioner som aktiveras av olika steg i köparens resa. Vid rapportering av [!DNL Marketo Measure]-data finns det två uppsättningar Touchpoint-data, Buyer Touchpoints (BT) och Buyer Attribution Touchpoints (BAT). Du kan lägga märke till att dessa datauppsättningar har lite olika positioner eftersom de relaterar till olika objekt. Om du vill ha mer kontext om det här avsnittet rekommenderar vi att du läser artikeln [Differens mellan Buyer Touchpoints (BT) &amp; Buyer Attribution Touchpoints (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md).

**Buyer Touchpoints (BT)**: Dessa är de kontaktytor som är kopplade till en enskild person och deras resa och är unika för den personen. Följande rapporter är inbyggda i Buyer Touchpoint-data.

* [!DNL Marketo Measure] 101: Leads efter ID
* [!DNL Marketo Measure] 101: Leads efter kanal
* [!DNL Marketo Measure] 101: Lead/kontakt efter ID
* [!DNL Marketo Measure] 101: Lead/kontakt efter kanal

Nedan beskrivs Buyer Touchpoint ståndpunkter som beskriver var en individ befinner sig på sin resa och vilka åtgärder de vidtagit för att tjäna denna tjänst.

<table>
 <tbody>
  <tr>
   <th>Buyer Touchpoint-position (BT)</th>
   <th>Kontaktpunktstyp (åtgärd som kan utlösa kontaktyta)</th>
   <th>Beskrivning av kontaktyta</th>
  </tr>
  <tr>
   <td>Första beröring (FT)</td>
   <td>Webbbesök</td>
   <td>Den första marknadsföringsinteraktionen som en individ har med ert varumärke</td>
  </tr>
  <tr>
   <td>Skapa leads (LC)</td>
   <td>Formulärfyllning <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>Det första formuläret fyller i en individ (vanligtvis en formulärinlämning men kan även vara en Campaign/Program-inkludering)</td>
  </tr>
  <tr>
   <td>Post LC</td>
   <td>Formulärfyllning <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>Alla formulär som en enskild person fyller i efter sin LC (eller ett senare Kampanj-/programtillägg)</td>
  </tr>
 </tbody>
</table>

**Buyer Attribution Touchpoints (BATS)**: Detta är de kontaktytor som är kopplade till ett säljprojekt och dess resa. Dessa kontaktytor är kopplade till intäkterna eftersom de är kopplade till säljprojektet och dess kontakter. Följande rapporter är inbyggda i Buyer Attribution Touchpoint-data.

* [!DNL Marketo Measure] 101: Affärsmöjligheter efter ID
* [!DNL Marketo Measure] 101: Affärsmöjligheter efter ID-kanal

<table>
 <tbody>
  <tr>
   <th>Buyer Attribution Touchpoint-position (BAT)</th>
   <th>Kontaktpunktstyp (åtgärd som kan utlösa kontaktyta)</th>
   <th>Beskrivning av kontaktyta</th>
  </tr>
  <tr>
   <td>Första beröring (FT)</td>
   <td>Webbbesök</td>
   <td>Den första marknadsföringsinteraktionen som en kontakt hade med ert varumärke</td>
  </tr>
  <tr>
   <td>Skapa leads (LC)</td>
   <td>Formulärfyllning <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>Den första formulärfyllningen som en kontakt hade (vanligtvis en formulärinlämning men kan också vara en Campaign/Program-inkludering)</td>
  </tr>
  <tr>
   <td>Skapande av affärsmöjlighet</td>
   <td>Formulärfyllning <strong>ELLER</strong>, webbbesök <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>Marknadsföringsinteraktionen närmast när Opp skapas</td>
  </tr>
  <tr>
   <td>Stängd vunnen/förlorad</td>
   <td>Formulärfyllning <strong>ELLER</strong>, webbbesök <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>Marknadsföringsinteraktionen närmast när Opp stängs (Won eller Lost)</td>
  </tr>
  <tr>
   <td>Mittpekningar</td>
   <td>Formulärfyllning <strong>ELLER</strong>, kampanj-/programinkludering</td>
   <td>När en kontakt fyller i ett onlineformulär och det inte sammanfaller med en milstolpe-kontaktyta</td>
  </tr>
 </tbody>
</table>

[!DNL Marketo Measure] har dessa två uppsättningar Touchpoint-data för att skapa en tydlig förståelse för en enskild persons resa och möjligheterna. Dessa två datauppsättningar för kontaktpunkter ger dig en tydlig karta över vad som hände uppifrån och ned på funnel.

I följande exempel visas dataflödet från Buyer Touchpoints (BT) till Buyer Attribution Touchpoints (BAT). I det här exemplet är både person A och person B en del av samma möjlighet som har ett Skapat den 3 juli 2020 och ett stängningsdatum den 5 juni 2020.

**Person A** Buyer Touchpoint-datauppsättning

* First Touch (FT) - Paid Search.AdWords - 9/1/2019
* Lead Creation (LC) - Organic Search.Google - 20/11-11
* Post LC (form fill) - Webinar - 3/4/2020

**Person B** Buyer Touchpoint-datauppsättning

* First Touch (FT) - Paid Social.Facebook - 2019-08-26
* Leadprojekt - Organic Search.Yahoo - 2/20/2020
* Post LC (form fill) - Email - 5/1/2020

**Affärsmöjligheter** Buyer Attribution Touchpoint-data skulle läsas enligt följande...

* First Touch (FT) - Paid Social.Facebook - 2019-08-26
   * (från **person B** eftersom de har _First Touch_ för kontot/Opp)
* Lead Creation (LC) - Organic Search.Google - 20/11-11
   * (från **person A** eftersom de har värdet _Lead Creation_ för kontot/Opp)
* Skapande av affärsmöjligheter - webbinarium - 3/4/2020
   * (kontaktpunkten efter LC från **person A** skulle vara _OC Touchpoint_ eftersom det var den senaste interaktionen till den möjlighet som skapades den 3/7/2020)
* Closed Won - Email - 5/1/2020
   * (kontaktpunkten efter LC från **person B** skulle vara _sluten Won-kontaktyta_ eftersom det var den senaste interaktionen till den affärsmöjlighet som stängdes den 5 juni 2020)
