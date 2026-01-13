---
description: Typ av rapportering för kontakter utan affärsmöjligheter
title: Typ av rapportering för kontakter utan affärsmöjligheter
exl-id: 255048be-16ff-4964-85fd-cc07888a05af
feature: Reporting
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Typ av rapportering för kontakter utan affärsmöjligheter {#report-type-for-contacts-without-opportunities}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se [!DNL Bizible] i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

För att kunna rapportera om kontakter med Buyer Touchpoints som inte är kopplade till ett säljprojekt måste du skapa en anpassad rapporttyp.

1. Gå till **[!UICONTROL Setup]** > **[!UICONTROL Create]** > **[!UICONTROL Report Types]**.

   ![Sidan Rapporttyper i Salesforce Setup](assets/1.jpg)

1. Välj **[!UICONTROL New Custom Report Type]**.

   ![Ny markeringsskärm för anpassad rapporttyp](assets/2.jpg)

1. Ange [!UICONTROL Primary Object] som [!UICONTROL Contacts]. Ange etiketten för rapporttypen som&quot;Kontakter med Buyer Touchpoints&quot;. Använd samma namn för rapporttypen Namn. I beskrivningen anges&quot;Kontakter med Buyer Touchpoints&quot;. Spara rapporten i [!UICONTROL Other] och ange rapporten till [!UICONTROL Deployed].

   ![Information om rapporttyp med kontakter som primärt objekt](assets/3.jpg)

1. Därifrån kommer du att länka Kontaktobjektet till Buyer Touchpoints-objektet. Se till att du väljer knappen &quot;Varje A-post måste ha minst en relaterad B-post.&quot;

   ![Objektrelationskonfiguration som länkar kontakter till Buyer Touchpoints](assets/4.jpg)

1. Klicka på **[!UICONTROL Save]** så är du klar!
