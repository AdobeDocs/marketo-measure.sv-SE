---
unique-page-id: 18874793
description: Använda ett fält för anpassat intäktsbelopp - [!DNL Marketo Measure] - Produktdokumentation
title: Använda fältet Anpassat intäktsbelopp
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Använda fältet Anpassat intäktsbelopp {#using-a-custom-revenue-amount-field}

Som standard hämtar Buyer Attribution Touchpoints säljprojektsbeloppet från ett av två fält:

* Belopp (SFDC-standard)
* [!DNL Marketo Measure] Affärsmöjlighet - belopp (anpassat)

Om du använder ett anpassat beloppsfält för dina affärsmöjligheter måste vi konfigurera ett arbetsflöde för att kunna beräkna Buyer Touchpoint-intäkterna. Detta kräver mer avancerade kunskaper om [!DNL Salesforce]så det kan behöva hjälp av SFDC-administratören.

Vi behöver följande information:

* API-namn för beloppsfältet

Här börjar vi skapa arbetsflödet.

1. Navigera till **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![](assets/1.jpg)

1. Välj **[!UICONTROL New Rule]**, ange objektet som säljprojekt och klicka på **[!UICONTROL Next]**.

   ![](assets/2.jpg)

   ![](assets/3.jpg)

1. Konfigurera arbetsflödet. Ange regelnamnet &quot;Uppdatera [!DNL Marketo Measure] Belopp för affärsmöjlighet.&quot; Ställ in utvärderingsvillkoren på&quot;Skapad och varje gång den redigeras&quot;. För regelvillkoret väljer du det anpassade mängdfältet och sedan Operator [!UICONTROL as "Not Equal To"] och lämna fältet&quot;Värde&quot; tomt.

   ![](assets/4.jpg)

1. Lägg till en arbetsflödesåtgärd. Ange den här listan som[!UICONTROL New Field Update].&quot;

   ![](assets/5.jpg)

1. Här fyller du i fältinformation. I fältet Namn rekommenderar vi att du använder följande namn: &quot;[!DNL Marketo Measure] Opp-belopp.&quot; &quot;Unikt namn&quot; fylls i automatiskt baserat på fältet &quot;Namn&quot;. Välj &quot;[!DNL Marketo Measure] Belopp för affärsmöjlighet.&quot; När du har markerat fältet markerar du rutan &quot;Utvärdera arbetsflödesregler igen efter fältändring&quot;. Välj &quot;Använd en formel för att ange det nya värdet&quot; i rutan &quot;Ange nytt fältvärde&quot;. Släpp API-namnet för det anpassade beloppsfältet i den tomma rutan. Klicka på **[!UICONTROL Save]**.

   ![](assets/6.png)

1. Du kommer tillbaka till en startsida för ditt arbetsflöde, se till att&quot;Aktivera&quot; så är du redo att gå. Aktivera genom att klicka på **Redigera** bredvid ditt nya arbetsflöde och klicka sedan på **Aktivera**.

   När du har slutfört de här stegen måste du uppdatera affärsmöjligheterna för att få det nya värdet från [!UICONTROL custom opportunity] fält.

   Detta kan uppnås genom att du kör dina affärsmöjligheter via Data Loader i SFDC. Mer information om hur du använder Data Loader i [den här artikeln](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

Om du har några frågor kan du kontakta din Customer Success Manager eller [[!DNL Marketo] Support](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.
