---
description: Konfigurera Marketo Connection - [!DNL Marketo Measure]
title: Konfigurera Marketo Connection
exl-id: 11660539-1cc5-4768-8f22-d6f7cd0b94f3
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---


# Konfigurera Marketo Connection {#set-up-marketo-connection}

Så här konfigurerar du anslutningen till Marketo.

>[!PREREQUISITES]
>
>[Skapa endast en API-användarroll](https://experienceleague.adobe.com/docs/marketo/using/product-docs/administration/users-and-roles/create-an-api-only-user.html){target="_blank"} för anslutningen [!DNL Marketo Measure]/Marketo Engage.

1. I [!DNL Marketo Measure] klickar du på listrutan **[!UICONTROL My Account]** och väljer **[!UICONTROL Settings]**.

   ![Marketo Measure-listrutan Mitt konto med alternativet Inställningar](assets/set-up-marketo-connection-1.png)

1. Klicka på [!UICONTROL Integrations] under **[!UICONTROL Connections]**.

   ![Integrationsmenyn med alternativet Anslutningar](assets/set-up-marketo-connection-2.png)

1. Klicka på **[!UICONTROL Set Up New CRM Connection]**.

   ![Knappen Konfigurera ny CRM-anslutning](assets/set-up-marketo-connection-3.png)

1. Klicka på knappen **[!UICONTROL Connect]** bredvid Marketo.

   ![Knappen Anslut bredvid integreringsalternativet Marketo](assets/set-up-marketo-connection-4.png)

1. Logga in på ditt Marketo Engage-konto på en ny flik. Gå till **Admin** > **Webbtjänster**. Bläddra ned till REST API. Markera och spara URL:en för slutpunkten och identitetstjänsten. Du behöver dem i följande steg.

   ![Marketo webbtjänstsida med REST API-slutpunkt och identitets-URL:er](assets/set-up-marketo-connection-5.png)

1. I Marketo Engage väljer du **LaunchPoint** i trädet till vänster. Hitta den anpassade tjänst som du vill ansluta till Marketo Measure och klicka på **Visa information**.

   ![LaunchPoint-menyn med anpassad tjänst och alternativet Visa detaljer](assets/set-up-marketo-connection-6.png)

1. Markera och spara klient-ID och klienthemlighet. Klicka på **Stäng**.

   ![Information om LaunchPoint-tjänsten som visar klient-ID och klienthemlighet](assets/set-up-marketo-connection-7.png)

1. Fyll i fälten i [!DNL Marketo Measure] med de data du har samlat in.

   ![Marketo-anslutningsformulär med slutpunkts- och autentiseringsfält](assets/set-up-marketo-connection-8.png)

1. När du har angett värdena klickar du på **[!UICONTROL Authenticate]**. Ditt Marketo Engage-konto är anslutet till [!DNL Marketo Measure].

   ![Bekräftelsemeddelande för Marketo-anslutning har slutförts](assets/set-up-marketo-connection-9.png)

   >[!NOTE]
   >[!DNL Marketo Measure] anropar Marketo API åt dig utan att använda några av dina Marketo API-begränsningar, så du behöver inte bekymra dig om tak och kreditallokering med andra integreringar.
