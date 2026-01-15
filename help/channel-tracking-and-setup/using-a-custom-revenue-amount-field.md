---
description: Använda vägledningen i fältet Anpassat intäktsbelopp för Marketo Measure-användare
title: Använda fältet Anpassat intäktsbelopp
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
feature: Custom Revenue Amount
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 2%

---

# Använda fältet Anpassat intäktsbelopp {#using-a-custom-revenue-amount-field}

Som standard hämtar Buyer Attribution Touchpoints säljprojektsbeloppet från ett av två fält:

* Belopp (SFDC-standard)
* [!DNL Marketo Measure] säljprojektsbelopp (anpassat)

Om du använder ett anpassat beloppsfält för dina affärsmöjligheter måste vi konfigurera ett arbetsflöde för att kunna beräkna Buyer Touchpoint intäkt. Detta kräver mer avancerade kunskaper om [!DNL Salesforce], så du kan behöva hjälp av din SFDC-administratör.

Vi behöver följande information:

* API-namn för beloppsfältet

Här börjar vi skapa arbetsflödet.

## Skapa arbetsflödet i Salesforce Lightning {#create-the-workflow-in-salesforce-lightning}

Följande steg gäller för Salesforce Lightning-användare. Om du fortfarande använder Salesforce Classic visas stegen [nedan](#create-the-workflow-in-salesforce-classic).

1. I installationsprogrammet skriver du Flöden i snabbsökningsrutan och väljer **[!UICONTROL Flows]** för att starta Flow Builder. Klicka på knappen **[!UICONTROL New Flow]** i den högra panelen.

   ![1. I installationsprogrammet skriver du &quot;Flöden&quot; i snabbsökningsrutan och väljer &#x200B;](assets/custom-amount-1.png)

1. Markera **[!UICONTROL Record-Triggered Flow]** och klicka på **[!UICONTROL Create]** längst ned till höger.

   ![1. Välj Postutlöst flöde och klicka på Skapa längst ned &#x200B;](assets/custom-amount-10.png)

1. Välj objektet säljprojekt i fönstret Konfigurera start. Välj [!UICONTROL Configure Trigger] i avsnittet **[!UICONTROL A record is created or updated]**.

   ![1. Välj objektet säljprojekt i fönstret Konfigurera start. Från &#x200B;](assets/custom-amount-11.png)

1. Välj [!UICONTROL Condition Requirements] under **[!UICONTROL Custom Condition Logic Is Met]** i avsnittet Ange anmälningsvillkor.
   * Välj ditt anpassade beloppsfält från sökfältet.
   * Ange operatorn som **Är null** och värdet som **[!UICONTROL False]**.
   * Ange utvärderingskriterierna till **[!UICONTROL Every time a record is updated and meets the condition requirements]**.

   ![Ange utvärderingskriterierna till Varje gång en post uppdateras](assets/custom-amount-12.png)

1. Välj **[!UICONTROL Fast Field Updates]** under Optimera flödet för. Klicka på **[!UICONTROL Done]** längst ned till höger.

   ![1. Välj Snabbfält &#x200B;](assets/custom-amount-13.png) under Optimera flödet för

1. Om du vill lägga till elementet klickar du på plusikonen (+) och väljer **[!UICONTROL Update Triggering Record]**.

   ![1. Om du vill lägga till elementet klickar du på plusikonen (+) och väljer &#x200B;](assets/custom-amount-14.png)

1. Ange följande i fönstret Ny uppdatering av poster:

   * Ange en etikett - API-namnet genereras automatiskt
   * Under &quot;How to Find Records to Update and Set their Values&quot; väljer du **[!UICONTROL Use the opportunity record that triggered the flow]**.
   * I avsnittet [!UICONTROL Set Filter Conditions] väljer du **[!UICONTROL Always Update Record]** som ett villkorskrav för att uppdatera posten.
   * I [!UICONTROL Set Field Values for the Campaign Record], från fältet, väljer du Marketo Measure-säljprojektsbelopp och från-värde. Välj sedan det anpassade mängdfältet.
   * Klicka på **[!UICONTROL Done]**.

   ![Klicka på Klar.](assets/custom-amount-15.png)

1. Klicka på **[!UICONTROL Save]**. Ett popup-fönster visas. Skriv Flow Label i fönstret Save the Flow (Flow API Name will be generated automatically). Klicka på **[!UICONTROL Save]** igen.

   ![1. Klicka på Spara. Ett popup-fönster visas. Skriv Flow Label i &#x200B;](assets/custom-amount-2.png)

1. Klicka på knappen **[!UICONTROL Activate]** för att aktivera flödet.

   ![1. Klicka på knappen Aktivera för att aktivera flödet.](assets/custom-amount-3.png)

## Skapa arbetsflödet i Salesforce Classic {#create-the-workflow-in-salesforce-classic}

Följande steg gäller för Salesforce Classic-användare. Om du har växlat till Salesforce Lightning hittar du de stegen [ovan](#create-the-workflow-in-salesforce-lightning).

1. Navigera till **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![1. Navigera till Skapa arbetsflöde och godkännanden](assets/custom-amount-4.png)

1. Välj **[!UICONTROL New Rule]**, ange objektet som säljprojekt och klicka på **[!UICONTROL Next]**.

   ![1. Välj Ny regel, ange objektet som säljprojekt och klicka på](assets/custom-amount-5.png)

   ![1. Välj Ny regel, ange objektet som säljprojekt och klicka på](assets/custom-amount-6.png)

1. Konfigurera arbetsflödet. Ange regelnamnet som&quot;Uppdatera säljprojektsbelopp för [!DNL Marketo Measure]&quot;. Ställ in utvärderingsvillkoren på&quot;Skapad och varje gång den redigeras&quot;. För Regelkriterier markerar du det anpassade beloppsfältet och väljer Operator [!UICONTROL as "Not Equal To"]. Lämna fältet Värde tomt.

   ![1. Konfigurera arbetsflödet. Ange regelnamnet Uppdatera Marketo](assets/custom-amount-7.png)

1. Lägg till en arbetsflödesåtgärd. Ange den här listan till [!UICONTROL New Field Update].
   ![1. Lägg till en arbetsflödesåtgärd. Ange den här listan till Nytt fält &#x200B;](assets/custom-amount-8.png)

1. Här fyller du i fältinformation. I fältet Namn rekommenderar vi att du använder följande namn: [!DNL Marketo Measure] Opp Amount. &quot;Unikt namn&quot; fylls i automatiskt baserat på fältet &quot;Namn&quot;. Välj [!DNL Marketo Measure]-säljprojektsbelopp i listan Fält att uppdatera. När du har markerat fältet markerar du rutan &quot;Utvärdera arbetsflödesregler igen efter fältändring&quot;. Välj &quot;Använd en formel för att ange det nya värdet&quot; i rutan &quot;Ange nytt fältvärde&quot;. Släpp API-namnet för det anpassade beloppsfältet i den tomma rutan. Klicka på **[!UICONTROL Save]**.

   ![1. Här fyller du i fältinformation. I fältet Namn:](assets/custom-amount-9.png)

1. kommer du tillbaka till en startsida för ditt arbetsflöde, se till att&quot;Aktivera&quot; så är du redo att gå. Aktivera genom att klicka på **[!UICONTROL Edit]** bredvid det nya arbetsflödet och sedan klicka på **[!UICONTROL Activate]**.

   När du har slutfört de här stegen måste affärsmöjligheterna uppdateras för att arbetsflödet ska få det nya värdet från fältet [!UICONTROL custom opportunity].

   Detta kan du uppnå genom att köra dina affärsmöjligheter via Data Loader i SFDC. Mer information om hur du använder datainläsaren finns i [den här artikeln](/help/channel-tracking-and-setup/using-data-loader-to-update-marketo-measure-custom-amount-field.md).

Om det finns några frågor längs vägen går det bra att kontakta Adobe Account Team (din kontohanterare) eller [[!DNL Marketo] Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
