---
unique-page-id: 18874646
description: Skillnaden mellan Buyer Touchpoints och Buyer Attribution Touchpoints - [!DNL Marketo Measure] - Produktdokumentation
title: Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints
exl-id: 19109271-7b59-44c0-b1ff-e3b0bba9f5ce
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Skillnad mellan Buyer Touchpoints och Buyer Attribution Touchpoints {#difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints}

Lär dig vad som definierar en kontaktyta för köpare (BT) och Buyer Attribution Touchpoint (BAT), skillnaderna mellan de båda samt svara på vanliga frågor.

Den viktigaste skillnaden mellan Buyer Touchpoints och Buyer Attribution Touchpoints är deras relation till [!DNL Salesforce] Objekt. BT relaterar till lead-, kontakt- och case-objekten, men inte till säljprojektsobjektet. Betyder att det aldrig kommer att finnas intäkter kopplade till Buyer Touchpoints.

Buyer Attribution Touchpoint-objektet är relaterat till objekten Kontakt, Konto och säljprojekt, men inte Lead-objektet. Betyder att det aldrig kommer att finnas kontaktytor för Buyer Attribution kopplade till Leads. BAT-objektet är där du ser intäkter kopplade till specifika marknadsföringsinteraktioner.

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

## Vanliga frågor {#faq}

**När blir en Buyer Touchpoint en Buyer Attribution Touchpoint?**

Ett BT blir en BAT när detta BT har kopplats till en kontakt som har en associerad möjlighet. En mycket viktig sak att förstå är att en specifik marknadsföringsinteraktion kan vara BT och BAT.

**Kan en köpkontaktyta ha en kontaktpunktsposition för att skapa säljprojekt?**

En Buyer Touchpoint har bara en Touchpoint-position som antingen First Touch (FT), Lead Creation (LC) eller Form Submit (mellanliggande kontaktytor). Eftersom affärsmöjligheter inte är relaterade till affärsmöjligheter är det inte möjligt för ett affärsföretag att ha en kontaktpunktsposition för skapande av säljprojekt eller stängt.

**Hur används Buyer Touchpoint-data?**

Normalt utnyttjar kunderna Buyer Touchpoint-data för att förstå Top of the Trnel &amp; Middle of the Tratt engagement. Betydelse [!DNL Marketo Measure] användare vet vem som skickar in formulär, vem som visar sin webbplats, vilket blogginlägg som fungerar bra, vad AdWords och som leder till konvertering osv. Buyer Touchpoint-data är bra för att förstå engagemanget hos era leads och kontakter.

**Hur ser en Buyer Touchpoint ut i Salesforce?**

Här är en skärmbild av ett BT i [!DNL Salesforce]:

![](assets/1.png)

**Hur ser en Buyer Attribution Touchpoint ut i Salesforce?**

Här är en skärmbild av en BAT i [!DNL Salesforce]:

![](assets/2.png)
