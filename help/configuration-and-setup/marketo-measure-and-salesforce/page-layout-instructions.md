---
unique-page-id: 18874799
description: Instruktioner för sidlayout - [!DNL Marketo Measure] - Produktdokumentation
title: Instruktioner för sidlayout
exl-id: 627377f0-d0cf-448c-a7b5-7eb5634b9627
source-git-commit: b910e5aedb9e178058f7af9a6907a1039458ce7a
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 1%

---

# Instruktioner för sidlayout {#page-layout-instructions}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

Se [!DNL Marketo Measure] rekommenderar vi att du uppdaterar sidlayouter för [!UICONTROL Account], [!UICONTROL Contact], [!UICONTROL Lead], [!UICONTROL Opportunity]och [!UICONTROL Campaign] Objekt. Instruktionerna är uppdelade för varje objektsidlayout nedan.

Börja med att navigera till [!DNL Salesforce] Konfigurera inställningar och leta upp [!UICONTROL Customize] -fliken.

## Kampanjobjekt {#campaign-object}

Vi rekommenderar att du lägger till [!DNL Marketo Measure] fält till din SFDC-kampanj för enbart din sandlåda. Fälten kan användas för att testa generering av kontaktpunkter. I produktion rekommenderar vi bara att du lägger till [!DNL Marketo Measure] Knappen Uppdatera slutpunktsdatum gruppvis. Vi rekommenderar inte att du lägger till [!DNL Marketo Measure] fält till produktion eftersom du kan skapa regelregler för kampanjsynkronisering.

1. Välj **[!UICONTROL Campaigns]**.

1. Klicka på **[!UICONTROL Page Layouts]**.

   ![](assets/1-1.jpg)

1. Klicka **[!UICONTROL Edit]** bredvid den sidlayout som du vill uppdatera.

   ![](assets/2-1.jpg)

1. I [!UICONTROL fields] väljer du **[!UICONTROL Enable Buyer Touchpoints]** och dra den dit du vill på sidan. Lägg sedan till **[!UICONTROL Touchpoint Start Date]** och **[!UICONTROL Touchpoint End Date]** fält.

   ![](assets/3-2.png)

1. Klicka sedan på[!UICONTROL Buttons]&quot; i snabbsökningsmenyn.

1. Dra **[!UICONTROL Bulk Update Touchpoint Date]** till det anpassade knappavsnittet.

   ![](assets/4-1.jpg)

1. Klicka på **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Om du använder flera Campaign-posttyper är plocklistevärdena för **[!UICONTROL Enable Buyer Touchpoints]** fältet måste uppdateras. Referens [den här artikeln](/help/channel-tracking-and-setup/offline-channels/configurations-for-multiple-campaign-record-types.md) för instruktioner.

## Leads {#leads}

1. Välj **[!UICONTROL Leads]**.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Klicka **[!UICONTROL Edit]** bredvid den sidlayout som du vill uppdatera. Tänk på att flera sidlayouter kan innehålla Buyer Touchpoints-avsnitten.

1. Klicka på alternativet VisualForce-sida till vänster i snabbsökningsmenyn.

1. Skapa ett nytt avsnitt och kalla det&quot;Buyer Touchpoints&quot;.

   >[!NOTE]
   >
   >Välj formatet &quot;en kolumn&quot; för vart och ett av dessa avsnitt.

1. Dra **[!UICONTROL Marketo Measure Lead Related List]** VisualForce-sidan in i sidlayoutavsnittet.

   ![](assets/5-1.png)

1. Klicka på växeln i dialogrutan [!DNL VisualForce] och ändra höjden till 100 och aktivera rullningslister.

1. Gå tillbaka till menyn och välj [!UICONTROL Canvas Apps] och skapa ett nytt avsnitt som kallas&quot;Marketo Measure Insights&quot; under Touchpoints [!DNL VisualForce] som du just skapade.

   >[!NOTE]
   >
   >Välj formatet &quot;en kolumn&quot; för vart och ett av dessa avsnitt.

1. Dra [!DNL Marketo Measure Insights] Arbetsyteappen i det nya avsnittet. Klicka **Spara**. Ibland är det nödvändigt att spara sidlayouten först innan du släpper i Canvas-appen eftersom Salesforce inte känner igen den direkt. När du har skapat det nya avsnittet sparar du sidlayouten och redigerar sedan om för att dra arbetsyteprogrammet inom det avsnittet. Detta gäller alla objekt.

   >[!NOTE]
   >
   >För [!DNL Marketo Measure Insights] Canvas-appen fungerar som den ska, [behörigheter måste konfigureras korrekt](/help/configuration-and-setup/marketo-measure-insights-canvas-app/marketo-measure-insights-configuration.md).

   >[!TIP]
   >
   >De flesta kunder använder inte fälten som slutar med (FT) eller (LC) eftersom de är äldre fält från före [!DNL Marketo Measure] Pekpunkten fanns som ett objekt.

Om du använder [!DNL Marketo Measure] ABM-funktion, [klicka här för ytterligare instruktioner om sidlayout](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).

## Kontakter {#contacts}

1. Välj **[!UICONTROL Contacts]**.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Markera den sidlayout som du vill redigera.

   Gå till alternativet Relaterade listor på snabbsökningsmenyn och lägg till **[!UICONTROL Buyer Touchpoints]** relaterad lista.

1. Klicka på skiftnyckelsikonen och lägg till följande kolumner i den här ordningen:

   * Kontaktpunkt för köpare
   * Marknadsföringskanal
   * Kontaktpunktskälla
   * Namn på annonskampanj
   * Pekpunktsposition
   * Kontaktpunktsdatum

1. Sortera efter: Touchpoint-datum, stigande.

   ![](assets/6.jpg)

1. Expandera alternativet Knappar och avmarkera **[!UICONTROL New]**.

   ![](assets/7.png)

1. Gå tillbaka till [!UICONTROL Related List] på menyn och lägg nu till **[!UICONTROL Buyer Attribution Touchpoint]** relaterad lista.

1. Klicka på skiftnyckelsikonen och lägg till följande kolumner i den här ordningen:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Möjligheter
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Intäkter - W-form (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter kontaktpunkt [!UICONTROL Date] > [!UICONTROL Ascending].

1. Expandera knappavsnittet och avmarkera **[!UICONTROL New]**.

1. Klicka på **[!UICONTROL Save]**.

## Möjligheter {#opportunities}

1. Välj **[!UICONTROL Opportunities]**.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Markera den sidlayout som du vill redigera.

1. Lägg till **[!UICONTROL Buyer Attribution Touchpoint]** Relaterad lista och klicka på växeln för att lägga till följande kolumner för affärsmöjligheter:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Kontakt
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Intäkter - W-form (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter [!UICONTROL Touchpoint Date] > [!UICONTROL Ascending].

1. Avmarkera **[!UICONTROL New]** inom [!UICONTROL Buttons] -avsnitt.

1. Klicka på **[!UICONTROL Save]**.

## Konton {#accounts}

1. Välj **[!UICONTROL Accounts]**.

1. Klicka på **[!UICONTROL Page Layouts]**.

1. Markera den sidlayout som du vill redigera.

1. Lägg till **[!UICONTROL Buyer Attribution Touchpoint]** Relaterad lista och klicka på växeln för att lägga till följande kolumner:

   * Attribution Touchpoint
   * Marknadsföringskanal
   * Möjligheter
   * Namn på annonskampanj
   * Kontaktpunktstyp
   * Pekpunktsposition
   * Attribution % W-Shaped (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Intäkter - W-form (_eller den mest robusta attribueringsmodellen som fullständig sökväg eller anpassad_)
   * Kontaktpunktsdatum

1. Sortera efter Touchpoint-datum > Stigande.

1. Avmarkera **[!UICONTROL New]** inom [!UICONTROL Buttons] -avsnitt.

1. Klicka på **[!UICONTROL Save]**.

Om du använder [!DNL Marketo Measure] ABM-funktion,  [klicka här för ytterligare instruktioner om sidlayout](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md).
