---
unique-page-id: 27656737
description: Utgift för rapportmarknadsföring - [!DNL Marketo Measure] - Produktdokumentation
title: Utgift för rapportmarknadsföring
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Utgift för rapportmarknadsföring {#report-marketing-spend}

## Utgiftstabell för marknadsföring {#marketing-spend-table}

Tabellen Marketing Spend kommer nu att innehålla en ny kolumn som visar valutan för varje kanal, delkanal och kampanjrad. Den nya kolumnen visas för alla kunder, även om flera valutor inte är aktiverade.

Tabellen kommer nu att innehålla en blandning av olika valutor. Se kontrollpanelen för Marketing Spend om du behöver få en summa av alla kanaler, delkanaler eller kampanjer i en enda valuta.

## Överföringskostnader {#upload-costs}

När en användare hämtar kostnadsfilen innehåller filen också en ny kolumn med valutan för varje rad. De enda giltiga valutorna är de som har angetts och lagrats i CRM. Du måste känna till den förkortade 3-bokstavskoden för din valuta (dvs. USD, CAD, JPY, EUR) och om en fil överförs med en okänd valuta kommer filöverföringen att misslyckas.

## Kostnader för annonseringsintegreringar {#costs-from-ad-integrations}

När [!DNL Marketo Measure] importerar kostnaden från anslutna plattformar som AdWords, Bing, Facebook eller Doubleclick använder vi även den rapporterade valutan. Valutan visas tillsammans med Channel, Subchannel och Campaign i tabellen Marketing Spend.

Om valutan från annonseringsprovidern inte matchar en valuta som hämtas från CRM kan felet&quot;Blandade valutor&quot; visas i [!DNL Marketo Measure Discover] eftersom vi inte kunde göra en konvertering av den valutan. För att åtgärda detta måste CRM-administratören lägga till en konvertering för den okända valutan.

## Migrera till konverterad marknadsföringsutgift {#migrate-to-converted-marketing-spend}

Eftersom våra marknadsföringsutgifter historiskt sett bara har varit i en enda valuta (USD), behövs ett litet arbete för att ändra alla rapporterade utgifter till den nya valutan. Även om ditt konto inte har flera valutor aktiverat kan du göra migreringen om du har en enda företagsvaluta som inte är USD.

1. Hämta den aktuella utgiftsfilen till en CSV-fil
1. Valutakolumnen visar &quot;[!UICONTROL USD]&quot; som den antagna valutan. Du kan antingen ersätta alla förekomster av[!UICONTROL USD]&quot; eller använd Sök+Ersätt för att ändra alla &quot;[!UICONTROL USD]&quot; till er egen företagsvaluta, som &quot;[!UICONTROL EUR]&quot; eller &quot;[!UICONTROL GBP]&quot;, till exempel.
1. Spara filen och ladda upp den igen [!DNL Marketo Measure].
1. Alla rapporterade kostnader visas nu som ny valuta.
