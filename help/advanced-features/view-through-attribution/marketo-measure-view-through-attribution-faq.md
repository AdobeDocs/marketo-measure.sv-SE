---
description: '[!DNL Marketo Measure] Visa via Vanliga frågor om attribuering - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] Visa genom attribut - frågor och svar'
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 1%

---


# [!DNL Marketo Measure] Visa genom attribut - frågor och svar {#marketo-measure-view-through-attribution-faq}

## Vad är Visa genom attribuering? {#what-is-view-through-attribution}

Funktionen [!DNL Marketo Measure] [!UICONTROL View Through Attribution] innehåller möjligheten att inkludera annonsvisningar i attribueringsmodellen.

>[!IMPORTANT]
>På grund av integritetsproblem är cookies från tredje part på väg ut. Google Chrome presenterade borttagning av cookies från tredje part under tredje kvartalet 2024 vilket effektivt markerar slutet på den här typen av spårning. Detta innebär att Adobe tar bort Marketo Measure-funktioner som är beroende av cookies från tredje part, närmare bestämt Cross-Domain Tracking och View-through Attribution, som använder Google/DoubleClick-cookie. Inga andra funktioner i Marketo Measure påverkas. Användning av cookies från första part påverkas inte heller. Mot bakgrund av Google tidsplan är det förväntade borttagningsdatumet för de två funktionerna ovan 6/1/2024. Relaterade data som samlats in före detta datum är fortfarande tillgängliga för Adobe-kunder.

## Varför är [!UICONTROL View Through Attribution] viktigt? {#why-is-view-through-attribution-important}

Historiskt sett har återmarknadsföring eller tryckannonsering varit svår att ta hänsyn till i attribueringsanalysen. Potentiella kunder kan, när som helst, exponeras för annonser med ny inriktning, men det är osannolikt att de faktiskt klickar på en av dessa annonser och fyller i ett formulär under samma session. Vår View Through Attribution-lösning kan nu spåra om någon exponerats för en annons eller inte. Denna kontaktyta läggs till den enskilda posten och kommer att fortsätta tills den potentiella kunden blir kund. Med den här informationen får marknadsföraren nu bättre insikt i hur deras återmarknadsföring fungerar.

## Vad ingår i konfigurationen? {#what-is-involved-in-setting-this-up}

För att [!DNL Marketo Measure] ska kunna börja mäta annonsintrycken finns det en tagg som måste placeras i Doubleclick Campaign Manager. När taggen har implementerats lagras avtrycken i våra loggar och vi tar hand om resten. Kontakta en Success Manager om du är intresserad av att mäta vyn genom attribuering.

## Vilka annonsplattformar stöds? {#which-ad-platforms-are-supported}

Vi har för närvarande stöd för [!DNL Doubleclick] Campaign Manager.

## Hur beräknas attribueringen? {#how-is-the-attribution-calculated}

Vi gjorde en noggrann analys av insiktsdata och dess påverkan på konverteringar i alla faser och marknadsföringskanaler. Fördelningen varierar beroende på modell, vilket framgår av tabellen nedan:

<table>
 <colgroup>
  <col>
  <col>
  <col>
  <col>
  <col>
  <col>
  <col>
 </colgroup>
 <tbody>
  <tr>
   <th><br></th>
   <th>Första beröring</th>
   <th>Skapa leads</th>
   <th>U-formad</th>
   <th>W-Shape</th>
   <th>Fullständig sökväg</th>
   <th>Anpassad modell</th>
  </tr>
  <tr>
   <td><strong>Impressions</strong></td>
   <td>0 %</td>
   <td>0 %</td>
   <td>10 %</td>
   <td>10 %</td>
   <td>10 %</td>
   <td>Egen</td>
  </tr>
  <tr>
   <td><strong>FT</strong></td>
   <td>100 %</td>
   <td>0 %</td>
   <td>35 %</td>
   <td>26,6 %</td>
   <td>20%</td>
   <td>Egen</td>
  </tr>
  <tr>
   <td><strong>LC</strong></td>
   <td>0 %</td>
   <td>100 %</td>
   <td>35 %</td>
   <td>26,6 %</td>
   <td>20%</td>
   <td>Egen</td>
  </tr>
  <tr>
   <td><strong>OC</strong></td>
   <td>0 %</td>
   <td>0 %</td>
   <td>0 %</td>
   <td>26,6 %</td>
   <td>20%</td>
   <td>Egen</td>
  </tr>
  <tr>
   <td><strong>Stängd</strong></td>
   <td>0 %</td>
   <td>0 %</td>
   <td>0 %</td>
   <td>0 %</td>
   <td>20%</td>
   <td>Egen</td>
  </tr>
  <tr>
   <td><strong>Mitten</strong></td>
   <td>0 %</td>
   <td>0 %</td>
   <td>20%</td>
   <td>10 %</td>
   <td>10 %</td>
   <td>Egen</td>
  </tr>
 </tbody>
</table>

## Hur kommer det här att se ut i [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] skapar en enda tryckkontaktyta på en lead som exponerats för visningsannonsen. Vi kan mappa användaren även efter att de först har kommit till din webbplats (FT) och fyllt i ett formulär (LC). Slutpunkten kommer att innehålla annonsinformation som annonskampanjens namn/ID, annons-ID, annonsinnehåll, webbplatsnamn/ID, placeringsnamn/ID, marknadsföringskanal, geor, referenssida med mera.

Den genomskinliga attribueringsmodellen beror på klienten och deras data.
