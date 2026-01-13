---
description: Skapar en [!DNL Marketo Measure] profil - [!DNL Marketo Measure]
title: Skapar en [!DNL Marketo Measure] profil
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Skapar en [!DNL Marketo Measure]-profil {#creating-a-marketo-measure-profile}

Lär dig skapa en [!DNL Marketo Measure]-profil. Genom att skapa en [!DNL Marketo Measure]-profil slipper vi valideringsfel när vi skickar data till CRM.

1. Skapa en specifik [!DNL Marketo Measure]-profil:

   * Tilldela administratörsbehörighetsuppsättningen [!DNL Marketo Measure]
   * Aktivera behörighet att visa och redigera konverterade leads

   >[!NOTE]
   >Den här profilen kan vara en klon av en [!DNL System Admin]-profil

1. Skapade en dedikerad [!DNL Marketo Measure]-användare:

   * Tilldela den nya [!DNL Marketo Measure]-profilen till den användaren
   * Aktivera&quot;Marknadsförare&quot; som användarbehörighet

1. Undanta den här profilen från alla utlösare, arbetsflöden och processer.
1. Logga in på ditt [!DNL Marketo Measure]-konto och återauktorisera [!DNL Salesforce]-anslutningen med den nya användaren:

   * Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och logga in med de nya inloggningsuppgifterna för Salesforce-användarproduktionen
   * Välj [!UICONTROL Settings] i listrutan [!UICONTROL My Account]
   * Välj [!UICONTROL Connections] i grupperingen [!UICONTROL Integrations]
   * Klicka på nyckelikonen till höger om den aktuella anslutna [!DNL Salesforce]-anslutningen och välj Återauktorisera med produktion. Logga sedan in med de nya inloggningsuppgifterna igen om du uppmanas till det

   Klart!

   Om du har några frågor om hur du skapar en dedikerad [!DNL Marketo Measure]-profil kan du kontakta Adobe Account Team (din kontohanterare) eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
