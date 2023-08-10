---
description: "[!DNL Marketo Measure] Installation och konfiguration av Salesforce-paket - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] [!DNL Salesforce] Paketinstallation och konfiguration"
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# [!DNL Marketo Measure] Installation och konfiguration av Salesforce-paket {#marketo-measure-salesforce-package-installation-and-set-up}

Innan du installerar [!DNL Marketo Measure] [!DNL Salesforce] baspaket måste du avgöra om du ska installera det i en [!DNL Salesforce] sandlåda innan du går till din Salesforce-produktionsinstans.

>[!NOTE]
>
>När du [!DNL Marketo Measure] kontot är anslutet till ett [!DNL Salesforce] -instans. Du kan inte flytta bakåt och ansluta till en sandlåda. Dessutom har [!DNL Marketo Measure] kontot kan bara anslutas till ett [!DNL Salesforce] produktionsinstans.

The [!DNL Marketo Measure] Baspaketet innehåller:

* 7 Anpassad [!DNL Marketo Measure] Objekt
* Egen [!DNL Marketo Measure] Fält
* 25 [!DNL Stock] Rapporter

[!DNL Marketo Measure] kan läsa standard [!DNL Salesforce] Objekt, fält och poster, [!DNL Marketo Measure] kommer aldrig att uppdatera eller skicka data till dem. Alla data som samlats in av [!DNL Marketo Measure] Javascript kommer att finnas i [!DNL Marketo Measure] Anpassade objekt och fält.

Följ stegen nedan för att installera [!DNL Marketo Measure Salesforce] baspaket.

1. Gå till [Salesforce Appexchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} och logga in.

1. Installera i [!DNL Marketo Measure] paket i sandlåda eller produktion.

1. Logga in på [!DNL Salesforce] som administratör.

1. Välj **[!UICONTROL Install]för alla användare**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. När installationen är klar kan du visa den.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

När du är klar med installationen kan du uppdatera [[!DNL Salesforce] sidlayout](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} med [!DNL Marketo Measure] fält om så önskas.

>[!NOTE]
>
>Läs om [!DNL Marketo Measure] Behörighetsuppsättningar har skapats och [hur de kommer att användas](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Installera [!DNL Marketo Measure] Instrumentpanelspaket {#install-marketo-measure-dashboard-package}

The [!UICONTROL Dashboard] Tilläggspaketet innehåller tre fördefinierade kontrollpaneler. Vi rekommenderar installation [!UICONTROL within] Produktion för alla användare.

1. Installera paketet från [[!DNL Salesforce] Appexchange](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t610000001jI6){target="_blank"}.

1. Välj **[!UICONTROL Install for All Users]**.

   ![](assets/marketo-measure-salesforce-package-installation-and-set-up-3.png)

## Skapa en [!DNL Marketo Measure] Profil och användare {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] skickar och tar emot data via en ansluten [!DNL Salesforce] användare inom [!DNL Marketo Measure] app.

För att skicka data till kontaktytan [!DNL Salesforce] -instans måste den anslutna användaren ha åtkomst till [!DNL Marketo Measure] anpassade objekt (t.ex. Buyer Touchpoint och Buyer Attribution Touchpoint) samt standard [!DNL Salesforce] objekt som Leads och Kontakter.

Skapa en [!DNL Marketo Measure] för att säkerställa att du inte stöter på valideringsfel när du överför data till Salesforce.

Steg 1: Skapa en specifik [!DNL Marketo Measure] profil

1. Tilldela följande behörigheter:

* &quot;[!DNL Marketo Measure] Behörighetsuppsättning för administratör&quot;
   * Den hanterade behörighetsgruppen ger en SFDC-administratör möjlighet att skapa, läsa, skriva, ta bort poster från [!DNL Marketo Measure] objekt.
* &quot;Visa och redigera behörighetsgrupp för konverterade leads&quot;
   * Detta gör att [!DNL Marketo Measure] för att dekorera leads efter att de har konverterats till kontakter. Om den här behörighetsgruppen inte är aktiverad kan det finnas stora luckor i dataspårningen.

>[!NOTE]
>
>Den här profilen kan vara en klon av en systemadministratörsprofil.

Steg 2: Skapa en dedikerad [!DNL Marketo Measure] så att du kan spåra effekten av [!DNL Marketo Measure] på [!DNL Salesforce] instance

1. Tilldela den nya [!DNL Marketo Measure] Profil för den användaren.

1. Aktivera&quot;Marknadsförare&quot; som behörighet på användarnivå.

* The [!UICONTROL Marketing User] Med kryssrutan kan användaren skapa kampanjer och använda guiden för kampanjimport. Om det här alternativet inte är markerat kan användaren bara visa kampanjer och avancerade kampanjinställningar, redigera kampanjhistoriken för en enskild lead eller kontakt och köra kampanjrapporter. [!DNL Marketo Measure] måste kunna läsa och skriva till kampanjobjektet.

Steg 3: Uteslut den här profilen från alla utlösare, arbetsflöden och processer

Steg 4: Logga in på [!DNL Marketo Measure] Konto och återauktorisera [!DNL Salesforce] anslutning till den nya användaren

1. Gå till apps.bizible.com och logga in med den nya användarproduktionen [!DNL Salesforce] autentiseringsuppgifter.

1. Välj **[!UICONTROL Settings]** inom **[!UICONTROL My Account]** nedrullningsbar meny.

1. Välj **[!UICONTROL Connections]** inom **[!UICONTROL Integrations]** gruppering.

1. Klicka på nyckelikonen till höger om den aktuella anslutna enheten [!DNL Salesforce] anslutning och välj att **Återauktorisera med produktion**. Logga in med de nya inloggningsuppgifterna igen (om du uppmanas till det).
