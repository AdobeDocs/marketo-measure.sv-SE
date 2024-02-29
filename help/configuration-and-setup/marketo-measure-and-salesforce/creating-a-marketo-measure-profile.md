---
unique-page-id: 18874698
description: Skapa en [!DNL Marketo Measure] Profil - [!DNL Marketo Measure]
title: Skapa en [!DNL Marketo Measure] Profil
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
feature: Salesforce
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Skapa en [!DNL Marketo Measure] Profil {#creating-a-marketo-measure-profile}

Lär dig skapa en [!DNL Marketo Measure] profil. Skapa en [!DNL Marketo Measure] profiler säkerställer att vi inte stöter på valideringsfel när vi överför data till CRM.

1. Skapa en specifik [!DNL Marketo Measure] profil:

   * Tilldela [!DNL Marketo Measure] Behörighetsuppsättning för administratör
   * Aktivera behörighet att visa och redigera konverterade leads

   >[!NOTE]
   >
   >Den här profilen kan vara en klon av en [!DNL System Admin] profil

1. Skapade en dedikerad [!DNL Marketo Measure] användare:

   * Tilldela den nya [!DNL Marketo Measure] Profil till den användaren
   * Aktivera&quot;Marknadsförare&quot; som användarbehörighet

1. Undanta den här profilen från alla utlösare, arbetsflöden och processer.
1. Logga in på [!DNL Marketo Measure] Konto och auktorisera om [!DNL Salesforce] anslutning till den nya användaren:

   * Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och logga in med Salesforce-inloggningsuppgifterna för den nya användarproduktionen
   * Välj &quot;[!UICONTROL Settings]&quot; i &quot;[!UICONTROL My Account]&quot; nedrullningsbar meny
   * Välj &quot;[!UICONTROL Connections]&quot; i &quot;[!UICONTROL Integrations]&quot; gruppera
   * Klicka på nyckelikonen till höger om den aktuella anslutna enheten [!DNL Salesforce] och väljer att återauktorisera med produktion. Logga sedan in med de nya inloggningsuppgifterna igen om du uppmanas till det

   Klart!

   Om du har några frågor om hur du skapar en dedikerad [!DNL Marketo Measure] profil, kontakta kontoteamet på Adobe (din kontohanterare) eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
