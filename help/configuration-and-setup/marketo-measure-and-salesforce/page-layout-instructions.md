---
description: Instruktioner för sidlayout - [!DNL Marketo Measure]
title: Instruktioner för sidlayout
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 1%

---


# Instruktioner för sidlayout {#page-layout-instructions}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Du bör uppdatera sidlayouterna för objekten [!DNL Marketo Measure], [!UICONTROL Account], [!UICONTROL Contact], [!UICONTROL Lead] och [!UICONTROL Opportunity] för att enkelt kunna se [!UICONTROL Campaign]-data. Instruktionerna är uppdelade för varje objektsidlayout nedan.

Börja med att navigera till inställningarna för [!DNL Salesforce]-installationen och leta upp fliken [!UICONTROL Customize].

## Kampanjobjekt {#campaign-object}

Vi rekommenderar att du lägger till fälten [!DNL Marketo Measure] i din SFDC Campaign endast för din sandlåda. Fälten kan användas för att testa generering av kontaktpunkter. Vi rekommenderar att du bara lägger till knappen [!DNL Marketo Measure] Uppdatera slutpunktsdatum gruppvis i produktionen. Vi rekommenderar inte att du lägger till fälten [!DNL Marketo Measure] i produktionen eftersom du kan skapa en regel för kampanjsynkronisering.

1. Välj **[!UICONTROL Campaigns]** i alternativet Build.

1. Klicka på **[!UICONTROL Page Layouts]**.

   ![Salesforce-inställningar som visar alternativet Sidlayout under kampanjer](assets/1-1.jpg)

1. Klicka på **[!UICONTROL Edit]** bredvid sidlayouten som du vill uppdatera.

   ![Lista över kampanjsidlayouter med knappen Redigera bredvid layoutnamnet &#x200B;](assets/2-1.jpg)

1. Markera fältet [!UICONTROL fields] i alternativet **[!UICONTROL Enable Buyer Touchpoints]** och dra det dit du vill på sidan. Lägg sedan till fälten **[!UICONTROL Touchpoint Start Date]** och **[!UICONTROL Touchpoint End Date]**.

   ![Sidlayoutredigeraren visar fältet Aktivera slutpunkter för köpare med fälten Startdatum och Slutdatum för slutpunkt &#x200B;](assets/3-2.png)

1. Klicka sedan på alternativet [!UICONTROL Buttons] längst upp på sidan på snabbsökningsmenyn.

1. Dra knappen **[!UICONTROL Bulk Update Touchpoint Date]** till det anpassade knappavsnittet.

   ![Sidlayoutredigeraren med knappen Uppdatera Touchpoint-datum gruppvis i det anpassade knappavsnittet](assets/4-1.jpg)

1. Klicka på **[!UICONTROL Save]**.

   >[!NOTE]
   >Om du använder flera Campaign-posttyper måste du uppdatera plocklistevärdena för fältet **[!UICONTROL Enable Buyer Touchpoints]**. Mer information finns i [den här artikeln](/help/channel-tracking-and-setup/offline-channels/configurations-record-types.md).

## Leads {#leads}

1. Välj **[!UICONTROL Leads]** i alternativet Build.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Klicka på **[!UICONTROL Edit]** bredvid sidlayouten som du vill uppdatera. Tänk på att flera sidlayouter kan innehålla Buyer Touchpoints-avsnitten.

1. Klicka på sidalternativet VisualForce till vänster i snabbsökningsmenyn.

1. Skapa ett avsnitt och kalla det&quot;Buyer Touchpoints&quot;.

   >[!NOTE]
   >Välj formatet &quot;en kolumn&quot; för vart och ett av dessa avsnitt.

1. Dra **[!UICONTROL Marketo Measure Lead Related List]** VisualForce-sidan till sidlayoutavsnittet.

   ![Leadsidlayoutredigeraren med Marketo Measure Lead Related List VisualForce-sida](assets/5-1.png)

1. Klicka på växeln på sidan [!DNL VisualForce] och ändra höjden till 100 och aktivera rullningslister.

1. Gå tillbaka till menyn, markera avsnittet [!UICONTROL Canvas Apps] och skapa ett avsnitt med namnet&quot;Marketo Measure Insights&quot; under avsnittet med kontaktpunkter [!DNL VisualForce] som du skapade.

   >[!NOTE]
   >Välj formatet &quot;en kolumn&quot; för vart och ett av dessa avsnitt.

1. Dra Canvas-appen [!DNL Marketo Measure Insights] till det nya avsnittet. Klicka på **Spara**. Ibland är det nödvändigt att spara sidlayouten innan du släpper i Canvas-appen eftersom Salesforce inte känner igen den omedelbart. När du har skapat avsnittet sparar du sidlayouten och redigerar sedan om för att dra arbetsytans app inom det avsnittet. Detta gäller alla objekt.

   >[!NOTE]
   >För att [!DNL Marketo Measure Insights] Canvas-appen ska fungera på rätt sätt måste [behörigheter konfigureras korrekt](/help/configuration-and-setup/marketo-measure-insights-canvas-app/marketo-measure-insights-configuration.md).

   >[!TIP]
   >De flesta kunder använder inte fälten som slutar med (FT) eller (LC) eftersom de är äldre fält från innan [!DNL Marketo Measure]-kontaktytan fanns som ett objekt.

Om du använder funktionen [!DNL Marketo Measure] ABM [klickar du här för ytterligare sidlayoutsinstruktioner](/help/advanced-features/account-based-marketing/account-based-marketing-overview.md).

## Kontakter {#contacts}

1. Välj **[!UICONTROL Contacts]** i alternativet Build.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Välj den sidlayout som du vill redigera.

   Gå till alternativet Relaterade listor på snabbsökningsmenyn och lägg till den **[!UICONTROL Buyer Touchpoints]** relaterade listan.

1. Klicka på skiftnyckelsikonen och lägg till följande kolumner i den här ordningen:

   * Buyer Touchpoint
   * Marknadsföringskanal
   * Touchpoint Source
   * Namn på annonskampanj
   * Pekpunktsposition
   * Kontaktpunktsdatum

1. Sortera efter: Slutpunktsdatum, stigande.

   ![Konfiguration av kontaktpunktsrelaterad lista för köpare med kolumner och inställningar för sorteringsordning](assets/6.jpg)

1. Expandera alternativet Knappar och avmarkera **[!UICONTROL New]**.

   ![Egenskaper för relaterad lista som visar knappen Ny avmarkerad i avsnittet Knappar](assets/7.png)

1. Gå tillbaka till alternativet [!UICONTROL Related List] på menyn och lägg nu till den **[!UICONTROL Buyer Attribution Touchpoint]** relaterade listan.

1. Klicka på skiftnyckelsikonen och lägg till följande kolumner i den här ordningen:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Möjligheter
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Full Path eller Custom_)
   * Intäkter W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Fullständig sökväg eller Anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter kontaktpunkt [!UICONTROL Date] > [!UICONTROL Ascending].

1. Expandera knappavsnittet och avmarkera **[!UICONTROL New]**.

1. Klicka på **[!UICONTROL Save]**.

## Möjligheter {#opportunities}

1. Välj **[!UICONTROL Opportunities]** i alternativet Build.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Välj den sidlayout som du vill redigera.

1. Lägg till den **[!UICONTROL Buyer Attribution Touchpoint]** relaterade listan och klicka på växeln för att lägga till följande kolumner för affärsmöjligheter:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Kontakt
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Full Path eller Custom_)
   * Intäkter W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Fullständig sökväg eller Anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter [!UICONTROL Touchpoint Date] > [!UICONTROL Ascending].

1. Avmarkera **[!UICONTROL New]** i avsnittet [!UICONTROL Buttons].

1. Klicka på **[!UICONTROL Save]**.

## Konton {#accounts}

1. Välj **[!UICONTROL Accounts]** i alternativet Build.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Välj den sidlayout som du vill redigera.

1. Lägg till den **[!UICONTROL Buyer Attribution Touchpoint]** relaterade listan och klicka på skiftnyckeln för att lägga till följande kolumner:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Möjligheter
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Full Path eller Custom_)
   * Intäkter W-Shaped (_eller den mest robusta attribueringsmodellen, till exempel Fullständig sökväg eller Anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter Touchpoint-datum > Stigande.

1. Avmarkera **[!UICONTROL New]** i avsnittet [!UICONTROL Buttons].

1. Klicka på **[!UICONTROL Save]**.

Om du använder funktionen [!DNL Marketo Measure] ABM läser du de [ytterligare sidlayoutinstruktionerna](/help/advanced-features/account-based-marketing/account-based-marketing-overview.md).
