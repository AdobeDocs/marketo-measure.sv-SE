---
description: Report Marketing Spend guidelines for Marketo Measure users
title: Utgift för rapportmarknadsföring
exl-id: 46b0f81c-acd1-47a5-bf75-6a943edb9009
feature: Reporting, Spend Management
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Utgift för rapportmarknadsföring {#report-marketing-spend}

## Utgiftstabell för marknadsföring {#marketing-spend-table}

Tabellen Marketing Spend innehåller en ny kolumn som visar valutan för varje kanal, delkanal och kampanjrad. Den här nya kolumnen visas för alla kunder, även om flera valutor inte är aktiverade.

Tabellen innehåller en blandning av olika valutor. Gå till kontrollpanelen Marketing Spend för att få en summa av alla kanaler, delkanaler eller kampanjer i en enda valuta.

## Överföringskostnader {#upload-costs}

När en användare hämtar kostnadsfilen innehåller filen också en ny kolumn med valutan för varje rad. De enda giltiga valutorna är de som har angetts och lagrats i CRM. Du måste känna till den förkortade 3-bokstavskoden för din valuta (USD, CAD, JPY, EUR) och om en fil överförs med en okänd valuta misslyckas filöverföringen.

## Kostnader för annonseringsintegreringar {#costs-from-ad-integrations}

När [!DNL Marketo Measure] importerar kostnaden från anslutna plattformar som AdWords, Bing, Facebook eller Doubleclick använder vi även den rapporterade valutan. Valutan visas tillsammans med Channel, Subchannel och Campaign i tabellen Marketing Spend.

Om valutan från annonseringsprovidern inte matchar en valuta som hämtas från CRM kan felet Blandade valutor visas i [!DNL Marketo Measure Discover]. För att åtgärda detta måste CRM-administratören lägga till en konvertering för den okända valutan.

## Migrera till konverterad marknadsföringsutgift {#migrate-to-converted-marketing-spend}

Eftersom marknadsföringsutgifterna historiskt sett bara har varit i en enda valuta (USD) behövs ett litet arbete för att ändra alla rapporterade utgifter till den nya valutan. Även om kontot inte har flera valutor aktiverade bör du göra den här migreringen om du har en enda företagsvaluta som inte är USD.

1. Hämta den aktuella utgiftsfilen till en CSV-fil
1. Valutakolumnen visar [!UICONTROL USD] som antagen valuta. Du kan antingen ersätta alla förekomster av [!UICONTROL USD] manuellt eller använda Sök+Ersätt om du vill ändra alla [!UICONTROL USD]-förekomster till din egen företagsvaluta, till exempel [!UICONTROL EUR] eller [!UICONTROL GBP].
1. Spara filen och överför den sedan tillbaka till [!DNL Marketo Measure].
1. Alla rapporterade kostnader visas nu som ny valuta.
