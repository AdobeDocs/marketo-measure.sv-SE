---
description: Läs om hur PostLC-kontaktytor skapas uppdaterade och begränsade för leads och kontakter
title: PostLC Touchpoints och Lead Engagement
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
feature: Touchpoints
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# PostLC Touchpoints och Lead Engagement {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] Post-Lead Creation-kontaktytor (PostLC) är tillgängliga för kunder som använder multitouch-attribueringsmodeller (W-Shape och högre). När en lead eller kontakt återvänder till webbplatsen och fortsätter att fylla i formulär registreras dessa formulärinskickade formulär som PostLC-kontaktytor. Dessa kontaktytor gör att ni kan se vilket innehåll som driver leads att fortsätta engagera er webbplats, långt efter den första konverteringen. PostLC-kontaktytor delar attribueringskrediter med alla mellanliggande kontaktytor inom ett säljprojekt. 10 % attribueringskrediter tilldelas mellanliggande kontaktytor och fördelas jämnt mellan alla kontaktytor.

![Marketo Measure Post-Lead Creation (PostLC)-kontaktytor är tillgängliga för kunder som använder ](assets/additional-functionality-1.png)

Du kan justera antalet PostLC-kontaktytor som visas i [!DNL SFDC]. Vanligtvis rekommenderar vi att du skjuter upp till fem PostLC-kontaktytor. Varje kontaktyta tar upp 1 kB i [!DNL SFDC].

>[!NOTE]
>
>Instruktioner om hur du justerar PostLC-kontaktpunktsinställningar finns i slutet av artikeln.

PostLC-kontaktytor är dynamiska. När en lead eller kontakt fortsätter att skicka PostLC-formulär uppdaterar [!DNL Marketo Measure] PostLC-kontaktytorna i CRM så att du ser deras senaste formulärinskickade formulär. Om du har angett en gräns på 5 PostLC-kontaktytor skickar [!DNL Marketo Measure] alltid de fem _senaste_ kontaktytorna till CRM.  I det här exemplet har det här kontot angett sin PostLC-gräns till fyra kontaktytor. Denna lead har redan nått maximalt antal PostLC-kontaktytor som den kan ha i din CRM. PostLC:s senaste beröring ägde rum den 6 juni 2018. Om den här personen skulle fylla i ett annat formulär nästa dag, kommer [!DNL Marketo Measure] att ta bort den första PostLC-kontaktytan från 9/11 2017 för att lägga till den senaste kontaktytan från 2/7/2018.

![PostLC-kontaktytor är dynamiska. Som lead eller kontakt fortsätter att skicka ](assets/additional-functionality-2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] uppdaterar bara PostLC-kontaktytor på leadet eller kontakten och uppdaterar inte PostLC-attribueringskontaktytorna på ett säljprojekt. Alla relevanta PostLC-kontaktytor på en kontakt ingår i säljprojektet.

## Ändra inställningar för PostLC-kontaktpunkt {#how-to-change-postlc-touchpoint-settings}

Följ instruktionerna nedan för att justera PostLC-kontaktpunktsinställningarna för dina leads eller kontakter.

**Leads**

1. Logga in på ditt [!DNL Marketo Measure]-konto på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och gå till [!UICONTROL Settings].

1. Välj **[!UICONTROL Leads]** under CRM.

1. Ange antalet postLC-kontaktytor som du vill skicka till dina leads och klicka på **[!UICONTROL Save]**.

   ![1. Ange antalet postLC-kontaktytor som du vill skicka till ](assets/additional-functionality-3.png)

**Kontakter**

1. Logga in på ditt [!DNL Marketo Measure]-konto på [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och gå till [!UICONTROL Settings].

1. Välj **[!UICONTROL Contacts]** under CRM.

1. Ange antalet postLC-kontaktytor som du vill skicka till dina kontakter och klicka på **[!UICONTROL Save]**.

   ![1. Ange antalet postLC-kontaktytor som du vill skicka till ](assets/additional-functionality-4.png)
