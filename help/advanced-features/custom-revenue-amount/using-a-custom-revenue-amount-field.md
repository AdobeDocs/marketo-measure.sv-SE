---
description: Använder ett fält för anpassat intäktsbelopp - [!DNL Marketo Measure]
title: Använda fältet Anpassat intäktsbelopp
exl-id: 517ea4f9-aa83-48d0-8ce7-003f4a907430
feature: Custom Revenue Amount
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

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

   ![Salesforce Flow Builder med knappen Nytt flöde](assets/using-a-custom-revenue-amount-field-1.png)

1. Markera **[!UICONTROL Record-Triggered Flow]** och klicka på **[!UICONTROL Create]** längst ned till höger.

   ![Val av flödestyp med alternativet Postutlöst flöde](assets/using-a-custom-revenue-amount-field-2.png)

1. Välj objektet säljprojekt i fönstret Konfigurera start. Välj [!UICONTROL Configure Trigger] i avsnittet **[!UICONTROL A record is created or updated]**.

   ![Konfigurera startfönstret med ett säljprojektsobjekt valt](assets/using-a-custom-revenue-amount-field-3.png)

1. Välj [!UICONTROL Condition Requirements] under **[!UICONTROL Custom Condition Logic Is Met]** i avsnittet Ange anmälningsvillkor.
   * Välj ditt anpassade beloppsfält från sökfältet.
   * Ange operatorn som **Är null** och värdet som **[!UICONTROL False]**.
   * Ange utvärderingskriterierna till **[!UICONTROL Every time a record is updated and meets the condition requirements]**.

   ![Konfiguration av anmälningsvillkor med anpassad villkorslogik](assets/using-a-custom-revenue-amount-field-4.png)

1. Välj **[!UICONTROL Fast Field Updates]** under Optimera flödet för. Klicka på **[!UICONTROL Done]** längst ned till höger.

   ![Optimera flödesinställningar med snabbfältsuppdateringar markerade](assets/using-a-custom-revenue-amount-field-5.png)

1. Om du vill lägga till elementet klickar du på plusikonen (+) och väljer **[!UICONTROL Update Triggering Record]**.

   ![Flödeselementmeny med alternativet Uppdatera utlösande post](assets/using-a-custom-revenue-amount-field-6.png)

1. Ange följande i fönstret Ny uppdatering av poster:

   * Ange en etikett - API-namnet genereras automatiskt
   * Under &quot;How to Find Records to Update and Set their Values&quot; väljer du **[!UICONTROL Use the opportunity record that triggered the flow]**.
   * I avsnittet [!UICONTROL Set Filter Conditions] väljer du **[!UICONTROL Always Update Record]** som ett villkorskrav för att uppdatera posten.
   * I fältet [!UICONTROL Set Field Values for the Campaign Record] från väljer du Marketo Measure-säljprojektsbelopp (**bizible2_Bizible_Opportunity_Amount__c**) och från värde. Välj sedan det anpassade mängdfältet.
   * Klicka på **[!UICONTROL Done]**.

   ![Uppdatera postkonfiguration med fältvärdesmappningar](assets/using-a-custom-revenue-amount-field-7.png)

1. Klicka på **[!UICONTROL Save]**. Ett popup-fönster visas. Skriv Flow Label i fönstret Save the Flow (Flow API Name will be generated automatically). Klicka på **[!UICONTROL Save]** igen.

   ![Spara dialogrutan Flöde med etikettfält](assets/using-a-custom-revenue-amount-field-8.png)

1. Klicka på knappen **[!UICONTROL Activate]** för att aktivera flödet.

   ![Flödessammanfattning med knappen Aktivera](assets/using-a-custom-revenue-amount-field-9.png)

## Skapa arbetsflödet i Salesforce Classic {#create-the-workflow-in-salesforce-classic}

Följande steg gäller för Salesforce Classic-användare. Om du har växlat till Salesforce Lightning hittar du de stegen [ovan](#create-the-workflow-in-salesforce-lightning).

1. Navigera till **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Workflow & Approvals]** > **[!UICONTROL Workflow Rules]**.

   ![Salesforce Classic-navigeringsmenyn med arbetsflödesregler](assets/using-a-custom-revenue-amount-field-10.png)

1. Välj **[!UICONTROL New Rule]**, ange objektet som säljprojekt och klicka på **[!UICONTROL Next]**.

   ![Sidan Arbetsflödesregler med knappen Ny regel](assets/using-a-custom-revenue-amount-field-11.png)

   ![Objektmarkering för arbetsflödesregel inställd på säljprojekt](assets/using-a-custom-revenue-amount-field-12.png)

1. Konfigurera arbetsflödet. Ange regelnamnet som&quot;Uppdatera säljprojektsbelopp för [!DNL Marketo Measure]&quot;. Ställ in utvärderingsvillkoren på&quot;Skapad och varje gång den redigeras&quot;. För Regelkriterier markerar du det anpassade beloppsfältet och väljer Operator [!UICONTROL as "Not Equal To"]. Lämna fältet Värde tomt.

   ![Arbetsflödeskonfiguration med regelvillkor och utvärderingsinställningar](assets/using-a-custom-revenue-amount-field-13.png)

1. Lägg till en arbetsflödesåtgärd. Ange den här listan till [!UICONTROL New Field Update].
   ![Dialogrutan Lägg till arbetsflödesåtgärd med alternativet Ny fältuppdatering](assets/using-a-custom-revenue-amount-field-14.png)

1. Här fyller du i fältinformation. I fältet Namn rekommenderar vi att du använder följande namn: [!DNL Marketo Measure] Opp Amount. &quot;Unikt namn&quot; fylls i automatiskt baserat på fältet &quot;Namn&quot;. Välj [!DNL Marketo Measure]-säljprojektsbelopp i listan Fält att uppdatera. När du har markerat fältet markerar du rutan &quot;Utvärdera arbetsflödesregler igen efter fältändring&quot;. Välj &quot;Använd en formel för att ange det nya värdet&quot; i rutan &quot;Ange nytt fältvärde&quot;. Släpp API-namnet för det anpassade beloppsfältet i den tomma rutan. Klicka på **[!UICONTROL Save]**.

   ![Fältuppdateringskonfiguration som visar namn, fältmappning och formelinställningar](assets/using-a-custom-revenue-amount-field-15.png)

1. kommer du tillbaka till en startsida för ditt arbetsflöde, se till att&quot;Aktivera&quot; så är du redo att gå. Aktivera genom att klicka på **[!UICONTROL Edit]** bredvid det nya arbetsflödet och sedan klicka på **[!UICONTROL Activate]**.

   När du har slutfört de här stegen måste affärsmöjligheterna uppdateras för att arbetsflödet ska få det nya värdet från fältet [!UICONTROL custom opportunity].

   Detta kan du uppnå genom att köra dina affärsmöjligheter via Data Loader i SFDC. Mer information om hur du använder datainläsaren finns i [den här artikeln](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md){target="_blank"}.

Om det finns några frågor längs vägen går det bra att kontakta Adobe Account Team (din kontohanterare) eller [[!DNL Marketo] Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
