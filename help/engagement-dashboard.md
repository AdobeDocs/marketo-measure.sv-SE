---
description: Upptäck Engagement-instrumentpanelen för att spåra kontaktytor som rörts och engagemanget i olika kanaler över tid
title: Instrumentpanel för engagemang
feature: Reporting
exl-id: dc8bcbe4-d470-4cd3-a2d9-804fdebe7121
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# Instrumentpanel för engagemang {#engagement-dashboard}

Instrumentpanelen för engagemang håller noggrann koll på användarnas engagemangsmått. Det visar kontaktytor, antalet engagerade och genomsnittliga kontaktytor per person. Använd tidsseriediagrammet för en månads-, kvartals- eller årsvy och stapeldiagrammet för detaljerade insikter om kanaler, delkanaler och kampanjer. Det här verktyget är nödvändigt för att förstå engagemangsmönster och för att finjustera era engagemangsstrategier.

Vi spårar varje kundinteraktion som användarkontaktpunkter (UT), de&quot;raw&quot; insamlade datapunkterna, som fungerar som grund för interaktionsstatistik på vår instrumentpanel. Alla användargränssnitten utvecklas inte till slutpunkter för köpare (BT) eller slutpunkter för kundattribuering (BAT), eftersom dessa är valda resultat för att tilldela specifika kundinteraktioner till intäktsrelaterade aktiviteter. Det är viktigt att komma ihåg att reglerna för inaktivering inte påverkar användargränssnitten eller instrumentpanelen för engagemang.

* **Användarkontaktytor**: Kontaktpunkter skapade från alla engagemang.
* **Kontaktpunkter för köpare**: Kontaktpunkter har valts för lead- och kontaktattribuering. BT:er är inte kopplade till säljprojekt och har inga tillhörande intäkter.
* **Slutpunkter för Buyer-attribuering**: Kontaktpunkter har valts för attribuering av säljprojekt. Bästa tillgängliga teknik har intäktskonsekvenser eftersom de är kopplade till säljprojekt.

Att endast använda BT eller BAT för att mäta engagemang skulle underskatta den verkliga omfattningen av kundinteraktioner eftersom engagemanget är bredare än bara attribuering.

Frågor som kontrollpanelen besvarar:

* Hur många människor var förlovade? Hur många beröringar per person har varit i genomsnitt?
* Hur är antalet kontaktytor jämfört med personer som berörts inom en viss kanal/underkanal/kampanj?
* Hur många kontaktytor fanns det på en viss kanal eller underkanal? Hur ändrades det över tid?

>[!NOTE]
>Uppgifter om konto- och säljprojektsengagemang planeras släppas under första halvåret 2024.

## Kontrollpanelskomponenter {#dashboard-components}

### KPI-paneler {#kpi-tiles}

* Kontaktpunkter: Det totala antalet råa kontaktytor som genereras.
   * Kontaktpunkter för Buyer Touchpoints och Buyer Attribution är attribueringsresultat som skapas genom att man väljer specifika kontaktytor för krediter. Alla kontaktytor väljs inte som BT och BAT.
* Kontakter: Det totala antalet personer som har några kontaktytor.
* Kontaktpunkter per person: Genomsnittligt antal kontaktytor per person som har berörts.

### Kontaktpunkter och personer som rör sig över tiden {#touchpoints-and-people-touched-over-time}

I tidsseriediagrammet visas antalet kontaktytor, kontaktpunkter och kontaktytor per person för varje månad, kvartal och år.

* använda detaljfunktionerna för att kategorisera data efter månad, kvartal eller år.
* Hovra över en stapel eller linje för att visa detaljerad information.

Frågor om diagramsvaren:

* Hur har antalet kontaktytor och Kontakter utvecklats över tiden?
* Hur skiljer sig kontaktytorna per person från ett kvartal per månad till nästa?

![Hur skiljer sig kontaktytorna per person från en fjärdedel/månad till &#x200B;](assets/engagement-dashboard-1.png)?

### Kontaktpunkter/Personer som berörs av kanal {#touchpoints-people-touched-by-channel}

Stolpdiagram som visar kontaktytor eller personer som berörts segmenterade efter kanal/underkanal/kampanj.

* använda detaljfunktionerna för att kategorisera data efter Subchannel och Campaign.
* Håll pekaren över varje fält för att visa kontaktytorna eller personer som berörts.

Frågor om diagramsvaren:

* Vilken kanal/underkanal/kampanj drev mest engagemang?
* Hur är antalet kontaktytor jämfört med personer som berörts inom en viss kanal/underkanal/kampanj?

![Hur många kontaktytor jämfört med personer som berörts i en &#x200B;](assets/engagement-dashboard-2.png)

## Filterruta {#filter-pane}

Kontrollpanelen är utrustad med följande inställningar och filter:

* Datum (baserat på slutpunktsdatum)
* Kanal, delkanal
* Campaign
