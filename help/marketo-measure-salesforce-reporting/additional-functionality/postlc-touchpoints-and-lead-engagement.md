---
unique-page-id: 18874562
description: PostLC Touchpoints och Lead Engagement - Marketo Measurement - Produktdokumentation
title: PostLC Touchpoints och Lead Engagement
exl-id: 3ee5c571-195e-46c7-b150-fedcbc3614cb
source-git-commit: f13e55f009f33140ff36523212ed8b9ed5449a4d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# PostLC Touchpoints och Lead Engagement {#postlc-touchpoints-and-lead-engagement}

[!DNL Marketo Measure] PostLC-kontaktytor är tillgängliga för kunder som använder multitouch-attribueringsmodeller (W-Shape och högre). När en lead eller kontakt återvänder till webbplatsen och fortsätter att fylla i formulär registreras dessa formulärinskickade formulär som PostLC-kontaktytor. Dessa kontaktytor gör att ni kan se vilket innehåll som driver leads att fortsätta engagera er webbplats, långt efter den första konverteringen. PostLC-kontaktytor delar attribueringskrediter med alla mellanliggande kontaktytor inom ett säljprojekt. 10 % attribueringskrediter tilldelas mellanliggande kontaktytor och fördelas jämnt mellan alla kontaktytor.

![](assets/1.png)

Du kan justera antalet PostLC-kontaktytor som ska visas i [!DNL SFDC]. Vanligtvis rekommenderar vi att man skjuter upp till fem PostLC-kontaktytor. varje kontaktyta upptar 1 kB [!DNL SFDC].

>[!NOTE]
>
>Instruktioner om hur du justerar PostLC-kontaktpunktsinställningar finns i slutet av den här artikeln.

PostLC-kontaktytor är dynamiska. Som lead eller kontakt fortsätter att skicka PostLC-formulär, [!DNL Marketo Measure] uppdaterar PostLC-kontaktytorna i CRM så att du ser deras senaste formulärinskickade formulär. Om du har angett en gräns på 5 PostLC-kontaktytor [!DNL Marketo Measure] tryck alltid på 5 _senaste_ kontaktytor med CRM.  I det här exemplet har det här kontot angett sin PostLC-gräns till fyra kontaktytor. Denna lead har redan nått maximalt antal PostLC-kontaktytor i CRM. PostLC:s senaste beröring ägde rum den 6 juni 2018. Om den här personen fyller i ett annat formulär dagen efter, [!DNL Marketo Measure] kommer att ta bort den första PostLC-kontaktytan från och med 2017-11-9 för att lägga till den senaste kontaktytan från och med 2 juli 2018.

![](assets/2.png)

>[!NOTE]
>
>[!DNL Marketo Measure] uppdaterar bara PostLC-kontaktytor på lead eller kontakt, och uppdaterar inte kontaktytor för PostLC-attribuering på ett säljprojekt. Alla relevanta PostLC-kontaktytor på en kontakt inkluderas i säljprojektet.

## Ändra inställningar för PostLC-kontaktpunkt {#how-to-change-postlc-touchpoint-settings}

Följ instruktionerna nedan för att justera PostLC-kontaktpunktsinställningarna för dina leads eller kontakter.

**Leads**

1. Logga in på [!DNL Marketo Measure] konto [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} och gå till [!UICONTROL Settings].

1. Välj under CRM **[!UICONTROL Leads]**.

1. Ange antalet postLC-kontaktytor som du vill skicka till dina leads och klicka på **[!UICONTROL Save]**.

   ![](assets/3.png)

**Kontakter**

1. Logga in på [!DNL Marketo Measure] konto [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} och gå till [!UICONTROL Settings].

1. Välj under CRM **[!UICONTROL Contacts]**.

1. Ange antalet postLC-kontaktytor som du vill skicka till dina kontakter och klicka **[!UICONTROL Save]**.

   ![](assets/4.png)
