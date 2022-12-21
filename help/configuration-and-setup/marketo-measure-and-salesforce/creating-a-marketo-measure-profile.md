---
unique-page-id: 18874698
description: Skapa en [!DNL Marketo Measure] Profil - [!DNL Marketo Measure] - Produktdokumentation
title: Skapa en [!DNL Marketo Measure] Profil
exl-id: dab2e2cb-fbd3-464a-9bd7-e9bf153d9848
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Skapa en [!DNL Marketo Measure] Profil {#creating-a-marketo-measure-profile}

Lär dig hur du skapar en [!DNL Marketo Measure] profil. Skapa en [!DNL Marketo Measure] profiler säkerställer att vi inte stöter på valideringsfel när vi överför data till CRM.

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
1. Logga in på [!DNL Marketo Measure] Konto och återauktorisera [!DNL Salesforce] anslutning till den nya användaren:

   * Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} och logga in med Salesforce-inloggningsuppgifterna för den nya användarproduktionen
   * Välj &quot;[!UICONTROL Settings]&quot; i &quot;[!UICONTROL My Account]&quot; nedrullningsbar meny
   * Välj &quot;[!UICONTROL Connections]&quot; i &quot;[!UICONTROL Integrations]&quot; gruppera
   * Klicka på nyckelikonen till höger om den aktuella anslutna enheten [!DNL Salesforce] och väljer att återauktorisera med Produktion. Logga sedan in med de nya inloggningsuppgifterna igen om du uppmanas till det

   Klar!

   Om du har några frågor om hur du skapar en dedikerad [!DNL Marketo Measure] profil, kontakta din Customer Success Manager eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.
