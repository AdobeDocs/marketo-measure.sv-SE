---
unique-page-id: 42762762
description: Konfigurera Marketo Connection - [!DNL Marketo Measure]
title: Konfigurera Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Konfigurera Marketo Connection {#set-up-marketo-connection}

Så här konfigurerar du anslutningen till Marketo.

>[!PREREQUISITES]
>
>[Skapa en användarroll som endast är API](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) för [!DNL Marketo Measure]/Marketo Engage.

1. I [!DNL Marketo Measure]klickar du på **[!UICONTROL My Account]** nedrullningsbar meny och välj **[!UICONTROL Settings]**.

   ![](assets/set-up-marketo-connection-1.png)

1. Under [!UICONTROL Integrations], klicka **[!UICONTROL Connections]**.

   ![](assets/set-up-marketo-connection-2.png)

1. Klicka på **[!UICONTROL Set Up New CRM Connection]**.

   ![](assets/set-up-marketo-connection-3.png)

1. Klicka på **[!UICONTROL Connect]** intill Marketo.

   ![](assets/set-up-marketo-connection-4.png)

1. Logga in på ditt Marketo Engage-konto på en ny flik. Gå till **Administratör** > **Webbtjänster**. Bläddra ned till REST API. Markera och spara URL:en för slutpunkten och identitetstjänsten. behöver du dem om en stund.

   ![](assets/set-up-marketo-connection-5.png)

1. Stillbild i Marketo Engage, markera **LaunchPoint** i trädet till vänster. Hitta den anpassade tjänst du vill ansluta till Marketo Measure och klicka på **Visa detaljer**.

   ![](assets/set-up-marketo-connection-6.png)

1. Markera och spara klient-ID och klienthemlighet. Klicka **Stäng**.

   ![](assets/set-up-marketo-connection-7.png)

1. Tillbaka in [!DNL Marketo Measure]fyller du i fälten med de data som du precis har samlat in.

   ![](assets/set-up-marketo-connection-8.png)

1. När du har angett värdena klickar du på **[!UICONTROL Authenticate]**. Ditt Marketo Engage-konto kommer då att anslutas till [!DNL Marketo Measure].

   ![](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] kommer att ringa till Marketo API åt dig utan att använda några av dina Marketo API-begränsningar, så du behöver inte bekymra dig om tak och kredittilldelning med andra integreringar.
