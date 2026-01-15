---
description: Konfigurera Marketo Connection-vägledning för Marketo Measure-användare
title: Konfigurera Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 3%

---

# Konfigurera Marketo Connection {#set-up-marketo-connection}

Så här konfigurerar du anslutningen till Marketo.

>[!PREREQUISITES]
>
>[Skapa endast en API-användarroll](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html) för anslutningen [!DNL Marketo Measure]/Marketo Engage.

1. I [!DNL Marketo Measure] klickar du på listrutan **[!UICONTROL My Account]** och väljer **[!UICONTROL Settings]**.

   ![1. I Marketo Measure klickar du på listrutan Mitt konto och &#x200B;](assets/set-connection-7.png)

1. Klicka på [!UICONTROL Integrations] under **[!UICONTROL Connections]**.

   ![1. Klicka på Anslutningar under Integreringar.](assets/set-connection-8.png)

1. Klicka på **[!UICONTROL Set Up New CRM Connection]**.

   ![1. Klicka på Konfigurera ny CRM-anslutning.](assets/set-connection-9.png)

1. Klicka på knappen **[!UICONTROL Connect]** bredvid Marketo.

   ![1. Klicka på knappen Anslut bredvid Marketo.](assets/set-connection-5.png)

1. Logga in på ditt Marketo Engage-konto på en ny flik. Gå till **Admin** > **Webbtjänster**. Bläddra ned till REST API. Markera och spara URL:en för slutpunkten och identitetstjänsten. Du behöver dem i följande steg.

   ![1. Logga in på ditt Marketo Engage-konto på en ny flik.](assets/set-connection-6.png)

1. I Marketo Engage väljer du **LaunchPoint** i trädet till vänster. Hitta den anpassade tjänst som du vill ansluta till Marketo Measure och klicka på **Visa information**.

   ![1. I Marketo Engage väljer du LaunchPoint i trädet på &#x200B;](assets/set-connection-4.png)

1. Markera och spara klient-ID och klienthemlighet. Klicka på **Stäng**.

   ![1. Markera och spara klient-ID och klienthemlighet. Klicka på Stäng.](assets/set-connection-3.png)

1. Fyll i fälten i [!DNL Marketo Measure] med de data du har samlat in.

   ![1. I Marketo Measure fyller du i fälten med data &#x200B;](assets/set-connection-1.png)

1. När du har angett värdena klickar du på **[!UICONTROL Authenticate]**. Ditt Marketo Engage-konto är anslutet till [!DNL Marketo Measure].

   ![1. När du har angett värdena klickar du på Autentisera. Din Marketo Engage](assets/set-connection-2.png)

   >[!NOTE]
   >
   >[!DNL Marketo Measure] anropar Marketo API åt dig utan att använda några av dina Marketo API-begränsningar, så du behöver inte bekymra dig om tak och kreditallokering med andra integreringar.
