---
unique-page-id: 27656735
description: Översikt - [!DNL Marketo Measure] - Produktdokumentation
title: Översikt
exl-id: 2076521c-b579-457c-ab1c-263b1da4dd89
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Översikt {#overview}

Idag [!DNL Marketo Measure] applikationen stöder bara en enda valuta (som antas vara USD), medan vi vet och är medvetna om att vi har kunder runt om i världen som behöver rapportera sina egna företags- och användarvalutor. Den här funktionen gör det möjligt för användare att växla mellan olika valutor när de tittar på antingen rapporterade utgifter eller försäljningsintäkter.

## Tillgänglighet {#availability}

Steg 2 och högre.

## Krav {#requirements}

I [!DNL Salesforce]måste kunden aktivera Aktivera flera valutor. Alternativt kan kunden även välja&quot;Ja, jag vill aktivera avancerad valutahantering&quot;.

I Dynamics kan kunden ange statiska valutakurser i sina inställningar för flera valutor. Det finns inget koncept för&quot;avancerad valutahantering&quot; i Dynamics.

## Villkor {#terms}

| **Villkor** | Beskrivning |
|---|---|
| **Avancerad valuta** | Kunden har Avancerad valutahantering och Flera valutor aktiverat, vilket innebär att de kan ha olika konverteringsgrader för olika tidsperioder. |
| **Företagsvaluta** | Detta är de olika valutor som anges och deklareras av en organisation i CRM, alla med konverteringsgrader. [!DNL Marketo Measure] kommer att importera dessa värden och göra dessa valutor tillgängliga för användare i vår produkt. |
| **Språk för valuta** | Den valuta som används för en organisation, som anges på sidan Företagsinformation. |
| **Lokal valuta (eller användarvaluta)** | Valutan som angetts för en enskild användare i användarprofilen, så att användaren kan visa vilket belopp som helst i sin egen lokala valuta. Organisationen måste deklarera och ställa in valutan innan användaren kan välja lokal valuta. |
| **En valuta** | Används för kunder som inte använder flera valutor i CRM, men deras organisation körs i en annan valuta, så de har en &quot;Valutaspråkinställning&quot;. Detta är fortfarande en gemensam valuta för organisationen, men utan konvertering. |
| **Enkel valuta** | Kunden har flera valutor aktiverade, men har en statisk konverteringsgrad per valuta. |
