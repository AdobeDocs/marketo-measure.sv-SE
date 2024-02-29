---
unique-page-id: 18874646
description: Skillnaden mellan Buyer Touchpoints och Buyer Attribution Touchpoints - [!DNL Marketo Measure]
title: Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
feature: Touchpoints
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Lär dig vad som definierar en kontaktyta för köpare (BT) och Buyer Attribution Touchpoint (BAT), skillnaderna mellan de båda samt svara på vanliga frågor.

Den viktigaste skillnaden mellan Buyer Touchpoints och Buyer Attribution Touchpoints är deras relation till [!DNL Salesforce] Objekt. BT:er relaterar till lead-, kontakt- och case-objekten, men inte till säljprojektsobjektet. Betyder att det aldrig finns några intäkter kopplade till Buyer Touchpoints.

Kontaktpunktsobjektet för Buyer-attribuering är relaterat till objekten för kontakt, konto och säljprojekt, men inte till Lead-objektet. Kontaktpunkterna för Buyer-attribuering är inte knutna till leads. BAT-objektet är där du ser intäkter kopplade till specifika marknadsföringsinteraktioner.

Skillnad mellan BT och BAT:

<table> 
 <colgroup> 
  <col> 
  <col> 
 </colgroup> 
 <tbody> 
  <tr> 
   <td>Kontaktpunkt för köpare (BT)</td> 
   <td>Kontaktpunkt för Buyer Attribution (BAT)</td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>Relaterar till lead-, kontakt- och case-objekt</li> 
     <li>Relaterar inte objektet säljprojekt</li> 
     <li>Intäkter är inte associerade med en köpkontaktyta</li> 
    </ul></td> 
   <td> 
    <ul> 
     <li>Relaterar till kontakt-, konto- och säljprojektsobjekt</li> 
     <li>Relaterar inte lead-objektet</li> 
     <li>Eftersom en Buyer Attribution Touchpoint är kopplad till ett säljprojekt har alla BAT-enheter intäkter kopplade till dem</li> 
    </ul></td> 
  </tr> 
 </tbody> 
</table>

## Vanliga frågor och svar {#faq}

**När blir en Buyer Touchpoint en Buyer Attribution Touchpoint?**

Ett BT blir en BAT när detta BT har kopplats till en kontakt som har en associerad möjlighet. En viktig sak att förstå är att en specifik marknadsföringsinteraktion kan vara BT och BAT.

**Kan en köpkontaktyta ha en kontaktpunktsposition för att skapa säljprojekt?**

En Buyer Touchpoint har bara en Touchpoint-position som antingen First Touch (FT), Lead Creation (LC) eller Form Submit (mellanliggande kontaktytor). Eftersom affärsmöjligheter inte är relaterade till affärsmöjligheter är det inte möjligt för ett affärsföretag att ha en kontaktpunktsposition för skapande av säljprojekt eller stängt.

**Hur används Buyer Touchpoint-data?**

Vanligtvis använder kunderna Buyer Touchpoint-data för att förstå Top of the Trnel &amp; Middle of the Tratt Engagement. Betydelse [!DNL Marketo Measure] användare vet vem som skickar in formulär, vem som visar sin webbplats, vilket blogginlägg som fungerar bra, vad AdWords och driver leder till konverteringar och så vidare. Buyer Touchpoint-data är bra för att förstå engagemanget hos era leads och kontakter.

**Hur ser en Buyer Touchpoint ut i Salesforce?**

Här är en skärmbild av ett BT i [!DNL Salesforce]:

![](assets/1.png)

**Hur ser en Buyer Attribution Touchpoint ut i Salesforce?**

Här är en skärmbild av en BAT i [!DNL Salesforce]:

![](assets/2.png)
