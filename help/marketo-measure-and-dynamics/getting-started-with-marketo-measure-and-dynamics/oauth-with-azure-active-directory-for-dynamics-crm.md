---
unique-page-id: 37357059
description: OAuth med [!DNL Azure Active Directory] för Dynamics CRM - [!DNL Marketo Measure]
title: OAuth med [!DNL Azure Active Directory] för Dynamics CRM
exl-id: 0a2f6b29-541d-4965-a460-e6f19b934edb
feature: Microsoft Dynamics
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---

# OAuth med [!DNL Azure Active Directory] för Dynamics CRM {#oauth-with-azure-active-directory-for-dynamics-crm}

## Vem påverkas? {#who-s-affected}

Den här inställningen är till för nya [!DNL Marketo Measure] kunder som använder Dynamics CRM med [!DNL Azure Active Directory] (AAD) eller för kunder som vill migrera från sitt gamla användarnamn och lösenord till [!DNL Azure Active Directory] med OAuth.

>[!NOTE]
>
>För båda dessa scenarier konfigureras AAD här för att underlätta anslutningen av Dynamics-instansen i [!DNL Marketo Measure] som DataProvider.

## Konfigurera nytt program {#set-up-new-application}

1. Logga in på [Azure Portal](https://portal.azure.com/#home).

1. Välj din Azure AD-klient genom att klicka på ditt konto i det övre högra hörnet på sidan, följt av att klicka på navigeringen i Byt katalog och sedan välja lämplig klientorganisation (hoppa över det här steget om du bara har en Azure AD-klientorganisation under ditt konto eller om du redan har valt lämplig Azure AD-klientorganisation).

   ![](assets/setup-2.png)

1. Sök efter &quot;[!DNL Azure Active Directory]&quot; i sökfältet och klicka på namnet som du vill öppna.

   ![](assets/setup-3.png)

1. Klicka **[!UICONTROL App Registrations]** i den vänstra menyn.

   ![](assets/setup-4.png)

1. Klicka **[!UICONTROL New Registration]** överst.

   ![](assets/setup-5.png)

1. Följ instruktionerna och skapa ett nytt program. Det spelar ingen roll om det är ett webbprogram eller ett offentligt klientprogram (mobil och dator), men om du vill ha specifika exempel för webbprogram eller offentliga klientprogram ska du kolla in våra [snabbstarter](https://docs.microsoft.com/en-us/azure/active-directory/develop/v1-overview).\
   a. Namn är programnamnet och beskriver programmet för slutanvändarna.\
   b. Under Kontotyper som stöds väljer du Konton i valfri organisationskatalog och personliga Microsoft-konton.\
   c. Ange omdirigerings-URI. För webbprogram är detta den grundläggande URL:en för ditt program där användare kan logga in. Till exempel: `http://localhost:12345`. För offentlig klient (mobil och dator) använder Azure AD den för att returnera tokensvar. Ange ett värde som är specifikt för programmet. Till exempel: `http://MyFirstAADApp`.

1. När du har slutfört registreringen tilldelar Azure AD ditt program en unik klientidentifierare (program-ID). Du behöver det här värdet i nästa avsnitt, så kopiera det från programsidan.

1. Om du vill hitta ditt program i Azure-portalen klickar du på **[!UICONTROL App Registrations]** och sedan klicka **[!UICONTROL All Applications]**. Öppna ditt nyskapade program

1. Klicka **[!UICONTROL Authentication]** i den vänstra menyn.

   ![](assets/setup-9.png)

1. Lägg till [!DNL Marketo Measure] omdirigerings-URL: `https://apps.bizible.com/OAuth2` och `https://apps.bizible.com/OAuth2?identityOnly=true` till listan över omdirigerings-URL:er.

   ![](assets/setup-10.png)

1. Navigera till fliken API-behörigheter och kontrollera att rätt behörigheter har tilldelats programmet.

   ![](assets/setup-10a.png)

1. Här anger du &quot;[!UICONTROL enterprise]&quot; i sökrutan och klicka på **[!UICONTROL Enterprise Applications]**.

   ![](assets/setup-11.png)

1. Hitta och öppna det nya programmet igen från listan över program.

1. Klicka på fliken Behörigheter **[!UICONTROL Grant Admin Consent for (instance name)]**.

   ![](assets/setup-13a.png)

1. Klicka på **[!UICONTROL Accept]**.

   ![](assets/setup-13b.png)

1. Från &quot;[!UICONTROL Users and Groups]&quot; kontrollerar du att giltiga &quot;Användare och grupper&quot; är tilldelade programmet.

   ![](assets/setup-14.png)

## Skapa en programanvändare {#creating-an-application-user}

När programregistreringen är klar kan en programanvändare skapas.

1. Navigera till din Common Data Service-miljö (`https://[org].crm.dynamics.com`).

1. Navigera till **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Välj **[!UICONTROL Application Users]** i visningsfiltret.

1. Välj **[!UICONTROL + New]**.

1. Ange nödvändig information i formuläret Application User.

   >[!NOTE]
   >
   >* Användarnamnsinformationen får inte matcha en användare som finns i [!DNL Azure Active Directory].
   >
   >* I fältet Program-ID anger du program-ID:t för det program du registrerade tidigare i Azure AD.

1. Om inställningarna är korrekta, efter att du har valt **[!UICONTROL Save]**, **[!UICONTROL Application ID URI]** och **[!UICONTROL Azure AD Object Id]** fält fylls i automatiskt med korrekta värden.

1. Innan du avslutar användarformuläret väljer du **[!UICONTROL Manage Roles]** och tilldela en säkerhetsroll till den här programanvändaren så att programanvändaren kan komma åt önskad organisationsinformation.

## Ansluta Dynamics-instansen via OAuth {#connecting-your-dynamics-instance-via-oAuth}

1. När du konfigurerar Dynamics-anslutningen för första gången följer du steg 1-5 i avsnittet CRM som en dataleverantör i [den här artikeln](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

1. När du uppmanas att ange OAuth-autentiseringsuppgifter fyller du i klient-ID, klienthemlighet och URI för program-ID som konfigurerats i avsnittet ovan.

a. Klient-ID är ID:t från steg 7 i avsnittet ovan. Om du inte skrev ned det visas program-ID:t i inställningarna för appregistreringen.

b. Klienthemlighet är den programhemlighet som skapas i Azure Portal för ditt program under Certifikat och hemligheter.

![](assets/creating-2e.png)

c. Program-ID-URI är URL:en för mål-webb-API:t (skyddad resurs). Om du vill hitta app-ID-URL:en i Azure Portal klickar du på [!DNL Azure Active Directory], klickar du på Programregistreringar, öppnar programmets inställningssida och klickar sedan på Egenskaper. Det kan också vara en extern resurs som `https://graph.microsoft.com`. Detta är vanligtvis Dynamics-instansens URL.

1. När du klickat **[!UICONTROL Submit]** uppmanas du att logga in med [!DNL Azure Active Directory]. När autentiseringen är slutförd ansluts ditt Dynamics-konto som dataleverantör inom [!DNL Marketo Measure].

## Autentiserar ditt Dynamics-konto igen {#re-authenticating-your-dynamics-account}

1. När du är i [!DNL Marketo Measure] program, gå till **[!UICONTROL My Settings]** > **[!UICONTROL Settings]** > **[!UICONTROL Connections]**.

1. Klicka på nyckelikonen i CRM-avsnittet bredvid Dynamics-anslutningen.

1. När användaren klickar på nyckeln visas ett popup-fönster och du uppmanas att ange klient-ID, klienthemlighet och URI för program-ID, som liknar registreringsflödet.

   ![](assets/re-authenticating-3.png)

1. När du klickat **[!UICONTROL Submit]** uppmanas du att logga in med [!DNL Azure Active Directory]. När autentiseringen är klar kommer ditt Dynamics-konto att återauktoriseras inom [!DNL Marketo Measure].
