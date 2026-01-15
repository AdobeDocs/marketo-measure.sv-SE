---
description: Använda datainläsaren för att uppdatera Marketo Measure vägledning för anpassade beloppsfält för Marketo Measure-användare
title: Uppdatera Marketo Measure fält för anpassat belopp med datainläsaren
exl-id: 55e91ac4-a835-48e0-a6ce-1d85b32aeac0
feature: Custom Revenue Amount
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Använder datainläsaren för att uppdatera fältet för anpassat belopp för [!DNL Marketo Measure] {#using-data-loader-to-update-marketo-measure-custom-amount-field}

[!DNL Marketo Measure] rekommenderar att du använder datainläsaren som ett bekvämt alternativ för att uppdatera affärsmöjlighetsvärden när du använder ett anpassat intäktsfält (fältet Belopp används inte i rutan) i [!DNL Marketo Measure]. Datainläsaren prioriteras framför att använda uppdateringsskriptet [!DNL Marketo Measure] eftersom skriptet kräver att användare inaktiverar alla Salesforce-valideringsregler medan skriptet [!DNL Marketo Measure] körs.

## Använder datainläsaren för att uppdatera fältet för anpassat belopp för [!DNL Marketo Measure]{#using-data-loader-to-update-marketo-measure-custom-amount-field-1}

1. Skapa ett Excel-blad med:

   * Affärsmöjlighets-ID
   * Fältet Eget belopp för affärsmöjlighet (det intäktsfält du föredrar)
   * Fältet [!DNL Marketo Measure] Affärsmöjlighetens belopp

1. Kopiera och klistra in värdena från det intäktsfält du föredrar i fältet [!UICONTROL [!DNL Marketo Measure] Opportunity Amount]. Uppdatera sedan alternativen med CSV-filen.

**_Du kan också gå till Salesforce och använda en anpassad listvy för att massredigera alla möjligheter.._**

1. Skapa en anpassad listvy för alla affärsmöjligheter.
1. Lägg till ett filter för fältet för föredragen intäkt är inte tomt _och fältet_ [!UICONTROL Marketo] Mät mängd för affärsmöjlighet är tomt.
1. Klicka på **[!UICONTROL Mass Edit]**, men ändra ingenting.
1. Klicka på **[!UICONTROL Save]**. Detta kommer att utlösa arbetsflödet för att fylla i fälten för säljprojektsbelopp i [!DNL Marketo Measure] med fältet Programvaruintäkt.
