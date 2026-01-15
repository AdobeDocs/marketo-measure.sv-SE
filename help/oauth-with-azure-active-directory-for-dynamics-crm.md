---
description: OAuth med [!DNL Azure Active Directory] för Dynamics CRM-vägledning för Marketo Measure-användare
title: OAuth med [!DNL Azure Active Directory] för Dynamics CRM
exl-id: 0a2f6b29-541d-4965-a460-e6f19b934edb
feature: Microsoft Dynamics
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 1%

---

# OAuth med [!DNL Azure Active Directory] för Dynamics CRM {#oauth-with-azure-active-directory-for-dynamics-crm}

## Vem påverkas? {#who-s-affected}

Den här konfigurationen är avsedd för nya [!DNL Marketo Measure]-kunder som använder Dynamics CRM med ett [!DNL Azure Active Directory] (AAD)-konto, eller för kunder som vill migrera från sitt gamla användarnamn och lösenord till [!DNL Azure Active Directory] med OAuth.

>[!NOTE]
>
>För båda dessa scenarier konfigureras AAD här för att underlätta anslutningen av Dynamics-instansen i [!DNL Marketo Measure] som en Data Provider.

## Konfigurera nytt program {#set-up-new-application}

1. Logga in på din [Azure-portal](https://portal.azure.com/#home).

1. Välj Azure AD-klientorganisation genom att klicka på ditt konto i det övre högra hörnet på sidan, följt av att klicka på navigeringen Byt katalog och sedan välja lämplig klientorganisation. Hoppa över det här steget om du bara har en Azure AD-klientorganisation under ditt konto eller om du redan har valt lämplig Azure AD-klientorganisation.

   ![1. Välj Azure AD-klientorganisation genom att klicka på ditt konto i &#x200B;](assets/bizible-taxonomy-1.png)

1. Sök efter [!DNL Azure Active Directory] i sökfältet och klicka på namnet som du vill öppna.

   ![1. Sök efter Azure Active Directory i sökfältet och](assets/microsoft-guide-1.png)

1. Klicka på **[!UICONTROL App Registrations]** på den vänstra menyn.

   ![1. Klicka på Appregistreringar på den vänstra menyn.](assets/microsoft-guide-2.png)

1. Klicka på **[!UICONTROL New Registration]** överst.

   ![1. Klicka på Ny registrering överst.](assets/microsoft-guide-3.png)

1. Följ instruktionerna och skapa ett program. Det spelar ingen roll om det är ett webbprogram eller ett offentligt klientprogram (mobil och dator), men om du vill ha specifika exempel för webbprogram eller offentliga klientprogram ska du ta en titt på [snabbstarterna](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-overview).
a. Namn är programnamnet och beskriver programmet för slutanvändarna.
b. Under Kontotyper som stöds väljer du Konton i valfri organisationskatalog och personliga Microsoft-konton.
c. Ange omdirigerings-URI. För webbprogram är detta den grundläggande URL:en för ditt program där användare kan logga in. Exempel: `http://localhost:12345`. För offentliga klienter (mobil och dator) använder Azure AD det för att returnera tokensvar. Ange ett värde som är specifikt för programmet. Exempel: `http://MyFirstAADApp`.

1. När du har slutfört registreringen tilldelar Azure AD ditt program en unik klientidentifierare (program-ID). Du behöver det här värdet i nästa avsnitt, så kopiera det från programsidan.

1. Om du vill hitta ditt program i Azure-portalen klickar du på **[!UICONTROL App Registrations]** och sedan på **[!UICONTROL All Applications]**. Öppna ditt nyskapade program

1. Klicka på **[!UICONTROL Authentication]** på den vänstra menyn.

   ![1. Klicka på Autentisering på den vänstra menyn.](assets/microsoft-guide-4.png)

1. Lägg till [!DNL Marketo Measure] omdirigerings-URL:er: `https://apps.bizible.com/OAuth2` och `https://apps.bizible.com/OAuth2?identityOnly=true` i listan över omdirigerings-URL:er.

   ![1. Lägg till Marketo Measure omdirigerings-URL:er: https://apps.bizible.com/OAuth2 och https://apps.bizible.com/OAuth2?identityOnly=true till](assets/microsoft-guide-5.png)

1. Navigera till fliken API-behörigheter och kontrollera att rätt behörigheter har tilldelats programmet.

   ![1. Navigera till fliken API-behörigheter och kontrollera att &#x200B;](assets/microsoft-guide-6.png)

1. Här anger du [!UICONTROL enterprise] i sökrutan och klickar på **[!UICONTROL Enterprise Applications]**.

   ![1. Här anger du&quot;enterprise&quot; i sökrutan och klickar på](assets/microsoft-guide-7.png)

1. Hitta och öppna det nya programmet igen från listan över program.

1. Klicka på **[!UICONTROL Grant Admin Consent for (instance name)]** på fliken Behörigheter.

   ![1. På fliken Behörigheter klickar du på Bevilja administratörsgodkännande för (instans &#x200B;](assets/microsoft-guide-8.png))

1. Klicka på **[!UICONTROL Accept]**.

   ![1. Klicka på Godkänn.](assets/microsoft-guide-9.png)

1. På fliken [!UICONTROL Users and Groups] kontrollerar du att giltiga &quot;Användare och grupper&quot; har tilldelats programmet.

   ![1. På fliken Användare och grupper kontrollerar du att &#x200B;](assets/microsoft-guide-10.png)

## Skapa en programanvändare {#creating-an-application-user}

När programregistreringen är klar kan en programanvändare skapas.

1. Navigera till din gemensamma datatjänstmiljö (`https://[org].crm.dynamics.com`).

1. Navigera till **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Välj **[!UICONTROL Application Users]** i visningsfiltret.

1. Välj **[!UICONTROL + New]**.

1. Ange nödvändig information i formuläret Application User.

   >[!NOTE]
   >
   >* Användarnamnsinformationen får inte matcha en användare i [!DNL Azure Active Directory].
   >
   >* I fältet Program-ID anger du program-ID:t för det program du registrerade tidigare i Azure AD.

1. Om konfigurationen är korrekt fylls fälten **[!UICONTROL Save]** och **[!UICONTROL Application ID URI]** automatiskt i med korrekta värden när du har valt **[!UICONTROL Azure AD Object Id]**.

1. Innan du avslutar användarformuläret väljer du **[!UICONTROL Manage Roles]** och tilldelar en säkerhetsroll till den här programanvändaren så att programanvändaren kan komma åt önskad organisationsinformation.

## Ansluta Dynamics-instansen via OAuth {#connecting-your-dynamics-instance-via-oAuth}

1. När du konfigurerar Dynamics-anslutningen för första gången följer du steg 1-5 i avsnittet CRM som en dataleverantör i [den här artikeln](/help/microsoft-dynamics-crm-installation-guide.md).

1. När du uppmanas att ange OAuth-autentiseringsuppgifter fyller du i klient-ID, klienthemlighet och URI för program-ID som konfigurerats i avsnittet ovan.

a. Klient-ID är ID:t från steg 7 i avsnittet ovan. Om du inte skrev ned det visas program-ID:t i inställningarna för appregistreringen.

b. Klienthemlighet är den programhemlighet som skapas i Azure Portal för ditt program under Certifikat och hemligheter.

![b. Klienthemlighet är den programhemlighet som skapas i Azure Portal &#x200B;](assets/microsoft-guide-11.png)

c. Program-ID-URI är URL:en för mål-webb-API:t (skyddad resurs). Om du vill hitta app-ID-URL:en klickar du på [!DNL Azure Active Directory] på Azure-portalen, klickar på Programregistreringar, öppnar programmets inställningssida och klickar sedan på Egenskaper. Det kan också vara en extern resurs som `https://graph.microsoft.com`. Detta är vanligtvis Dynamics-instansens URL.

1. När du har klickat på **[!UICONTROL Submit]** uppmanas du att logga in med [!DNL Azure Active Directory]. När autentiseringen lyckas är ditt Dynamics-konto anslutet som en dataleverantör i [!DNL Marketo Measure].

## Återautentiserar ditt Dynamics-konto {#re-authenticating-your-dynamics-account}

1. Gå till [!DNL Marketo Measure] > **[!UICONTROL My Settings]** > **[!UICONTROL Settings]** när du är i programmet **[!UICONTROL Connections]**.

1. Klicka på nyckelikonen i CRM-avsnittet bredvid Dynamics-anslutningen.

1. När användaren klickar på nyckeln visas ett popup-fönster där du uppmanas att ange klient-ID, klienthemlighet och URI för program-ID, som liknar registreringsflödet.

   ![1. När du klickar på tangenten visas ett popup-fönster och du är &#x200B;](assets/microsoft-guide-12.png)

1. När du har klickat på **[!UICONTROL Submit]** uppmanas du att logga in med [!DNL Azure Active Directory]. När autentiseringen är klar auktoriseras ditt Dynamics-konto på nytt inom [!DNL Marketo Measure].
