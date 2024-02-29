---
unique-page-id: 18874652
description: "[!DNL Marketo Measure] Visa via Vanliga frågor om attribut - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Visa via Vanliga frågor om attribut"
exl-id: d20e88f3-3ff8-4381-a4b8-6862798caa74
feature: Attribution
source-git-commit: 518a984b0d8d640290bd9b637221fcdc0948e5b9
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# [!DNL Marketo Measure] Visa via Vanliga frågor om attribut {#marketo-measure-view-through-attribution-faq}

## Vad är Visa genom attribuering? {#what-is-view-through-attribution}

The [!DNL Marketo Measure] [!UICONTROL View Through Attribution] kan inkludera annonsvisningar i attribueringsmodellen.

## Varför [!UICONTROL View Through Attribution] Viktigt? {#why-is-view-through-attribution-important}

Historiskt sett har återmarknadsföring eller tryckannonsering varit svår att ta hänsyn till i attribueringsanalysen. Potentiella kunder kan, när som helst, exponeras för annonser med ny inriktning, men det är osannolikt att de faktiskt klickar på någon av dessa annonser och fyller i ett formulär under samma session. Vår View Through Attribution-lösning kan nu spåra om någon exponerats för en annons eller inte. Denna kontaktyta läggs till den enskilda posten och kommer att fortsätta tills den potentiella kunden blir kund. Med den här informationen får marknadsföraren nu bättre insikt i hur deras återmarknadsföring fungerar.

## Vad ingår i konfigurationen? {#what-is-involved-in-setting-this-up}

För att [!DNL Marketo Measure] för att börja mäta annonsintrycken finns det en tagg som måste placeras i Doubleclick Campaign Manager. När taggen har implementerats lagras avtrycken i våra loggar och vi tar hand om resten. Kontakta en Success Manager om du är intresserad av att mäta vyn genom attribuering.

## Vilka annonsplattformar stöds? {#which-ad-platforms-are-supported}

Vi har för närvarande support [!DNL Doubleclick] Campaign Manager.

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
   <td>100 %</td> 
   <td>0 %</td> 
   <td>35 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Egen</td> 
  </tr> 
  <tr> 
   <td><strong>LC</strong></td> 
   <td>0 %</td> 
   <td>100 %</td> 
   <td>35 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Egen</td> 
  </tr> 
  <tr> 
   <td><strong>OC</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>26,6 %</td> 
   <td>20 %</td> 
   <td>Egen</td> 
  </tr> 
  <tr> 
   <td><strong>Stängd</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>20 %</td> 
   <td>Egen</td> 
  </tr> 
  <tr> 
   <td><strong>Mitten</strong></td> 
   <td>0 %</td> 
   <td>0 %</td> 
   <td>20 %</td> 
   <td>10 %</td> 
   <td>10 %</td> 
   <td>Egen</td> 
  </tr> 
 </tbody> 
</table>

## Hur ser det ut i [!DNL Salesforce?] {#what-will-this-look-like-in-salesforce}

[!DNL Marketo Measure] skapar en enda tryckkontaktyta på en lead som exponerats för displayannonsen. Vi kan mappa användaren även efter att de först har kommit till din webbplats (FT) och fyllt i ett formulär (LC). Slutpunkten kommer att innehålla annonsinformation som annonskampanjens namn/ID, annons-ID, annonsinnehåll, webbplatsnamn/ID, placeringsnamn/ID, marknadsföringskanal, geor, referenssida med mera.

Den genomskinliga attribueringsmodellen beror på klienten och deras data.
