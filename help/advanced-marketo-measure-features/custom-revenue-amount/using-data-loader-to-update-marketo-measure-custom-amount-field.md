---
unique-page-id: 18874771
description: Uppdatera med datainläsaren [!DNL Marketo Measure] Anpassat beloppsfält - [!DNL Marketo Measure] - Produktdokumentation
title: Uppdatera Marketo Measure fält för anpassat belopp med datainläsaren
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Uppdatera med datainläsaren [!DNL Marketo Measure] Anpassat beloppsfält {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] rekommenderar att du använder Data Loader som ett bekvämt alternativ för att uppdatera affärsmöjlighetsvärden när du använder ett anpassat intäktsfält (fältet Belopp används inte) i [!DNL Marketo Measure]. Datainläsaren prioriteras framför att använda [!DNL Marketo Measure] uppdateringsskript när skriptet kräver att användare inaktiverar alla Salesforce-valideringsregler medan [!DNL Marketo Measure] skript körs.

## Uppdatera med datainläsaren [!DNL Marketo Measure] Anpassat beloppsfält{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Skapa ett Excel-blad med:

   * Affärsmöjlighets-ID
   * Fältet Eget belopp för affärsmöjlighet (det intäktsfält du föredrar)
   * [!DNL Marketo Measure] Fältet Affärsmöjlighet

1. Kopiera och klistra in värdena från det intäktsfält du föredrar i [!UICONTROL [!DNL Marketo Measure] Opportunity Amount] fält. Uppdatera sedan alternativen med CSV-filen.

**_Du kan också gå till Salesforce och använda en anpassad listvy för att massredigera alla möjligheter..._**

1. Skapa en anpassad listvy för alla affärsmöjligheter.
1. Lägg till ett filter för fältet för föredragen intäkt är inte tomt _och_ [!UICONTROL Marketo] Fältet Mät säljprojektsbelopp är tomt.
1. Klicka **[!UICONTROL Mass Edit]**, men ändra ingenting.
1. Klicka på **[!UICONTROL Save]**. Detta utlöser arbetsflödet för att fylla i [!DNL Marketo Measure] Fält för säljprojektsbelopp med fältet Programvaruintäkt.
