---
description: '[!DNL Marketo Measure] Installation och konfiguration av Salesforce-paket - [!DNL Marketo Measure]'
title: '[!DNL Marketo Measure] [!DNL Salesforce] Paketinstallation och konfiguration'
exl-id: ed58bc1e-cfb0-48db-aa53-96204e12de2e
feature: Installation, Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# [!DNL Marketo Measure] Installation och konfiguration av Salesforce-paket {#marketo-measure-salesforce-package-installation-and-set-up}

Innan du installerar baspaketet [!DNL Marketo Measure] [!DNL Salesforce] måste du avgöra om du först installerar det i en [!DNL Salesforce]-sandlåda innan du går till produktionsinstansen för Salesforce.

>[!NOTE]
>När ditt [!DNL Marketo Measure]-konto har anslutits till en [!DNL Salesforce]-produktionsinstans kan du inte flytta bakåt och ansluta till en sandlåda. Dessutom kan ett [!DNL Marketo Measure]-konto bara anslutas till en [!DNL Salesforce]-produktionsinstans.

Baspaketet [!DNL Marketo Measure] innehåller:

* 7 anpassade [!DNL Marketo Measure]-objekt
* Anpassade [!DNL Marketo Measure]-fält
* 25 [!DNL Stock] rapporter

[!DNL Marketo Measure] kan läsa [!DNL Salesforce] standardobjekt, fält och poster, men [!DNL Marketo Measure] kommer aldrig att uppdatera eller skicka data till dem. Alla data som samlas in av JavaScript [!DNL Marketo Measure] visas i anpassade objekt och fält i [!DNL Marketo Measure] .

Installera baspaketet [!DNL Marketo Measure Salesforce] genom att följa stegen nedan.

1. Gå till [Salesforce AppExchange](https://appexchange.salesforce.com/appxListingDetail?listingId=a0N3000000B3KLuEAN){target="_blank"} och logga in med en inkognitiv webbläsare.

1. Installera i paketet [!DNL Marketo Measure] i sandlådan eller i produktionen.

1. Logga in på [!DNL Salesforce] som administratör.

1. Välj **[!UICONTROL Install]för alla användare**.

   ![Salesforce AppExchange - installationsdialogruta för Marketo Measure-paketet](assets/marketo-measure-salesforce-package-installation-and-set-up-1.png)

1. När installationen är klar kan du visa den.

   ![Sidan med information om installerade Marketo Measure-paket i Salesforce](assets/marketo-measure-salesforce-package-installation-and-set-up-2.png)

När du har slutfört installationen kan du uppdatera dina [[!DNL Salesforce] sidlayouter](/help/configuration-and-setup/marketo-measure-and-salesforce/page-layout-instructions.md){target="_blank"} med [!DNL Marketo Measure]-fälten om du vill.

>[!NOTE]
>Läs om de [!DNL Marketo Measure] behörighetsuppsättningar som har skapats och [hur de används](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-permission-sets.md){target="_blank"}.

## Skapar en [!DNL Marketo Measure]-profil och användare {#creating-a-marketo-measure-profile-and-user}

[!DNL Marketo Measure] skickar och tar emot data via en ansluten [!DNL Salesforce]-användare i [!DNL Marketo Measure]-appen.

Om du vill skicka kontaktpunktsdata till [!DNL Salesforce]-instansen måste den anslutna användaren ha tillgång till [!DNL Marketo Measure] anpassade objekt (till exempel Buyer Touchpoint och Buyer Attribution Touchpoint) samt [!DNL Salesforce] standardobjekt som leads och kontakter.

Skapa en [!DNL Marketo Measure]-profil för att säkerställa att du inte stöter på valideringsfel när du överför data till Salesforce.

Steg 1: Skapa en specifik [!DNL Marketo Measure]-profil

1. Tilldela följande behörigheter:

* &quot;[!DNL Marketo Measure] behörighetsuppsättning för administratör&quot;
   * Den hanterade behörighetsgruppen ger en SFDC-administratör möjlighet att skapa, läsa, skriva och ta bort poster från [!DNL Marketo Measure]-objekt.
* &quot;Visa och redigera behörighetsgrupp för konverterade leads&quot;
   * Detta gör att [!DNL Marketo Measure] kan dekorera leads efter att de har konverterats till kontakter. Om den här behörighetsgruppen inte är aktiverad kan det finnas stora luckor i dataspårningen.

>[!NOTE]
>Den här profilen kan vara en klon av en systemadministratörsprofil.

Steg 2: Skapa en dedikerad [!DNL Marketo Measure]-användare så att du kan spåra effekten av [!DNL Marketo Measure] på din [!DNL Salesforce]-instans

1. Tilldela den nya [!DNL Marketo Measure]-profilen till den användaren.

1. Aktivera&quot;Marknadsförare&quot; som behörighet på användarnivå.

* Med kryssrutan [!UICONTROL Marketing User] kan användaren skapa kampanjer och använda guiden för kampanjimport. Om det här alternativet inte väljs kan användaren bara visa kampanjer och avancerade kampanjinställningar, redigera kampanjhistoriken för en enskild lead eller kontakt och köra kampanjrapporter. [!DNL Marketo Measure] måste kunna läsa och skriva till kampanjobjektet.

Steg 3: Uteslut den här profilen från alla utlösare, arbetsflöden och processer

Steg 4: Logga in på ditt [!DNL Marketo Measure]-konto och återauktorisera [!DNL Salesforce]-anslutningen med den nya användaren

1. Gå till apps.bizible.com och logga in med inloggningsuppgifterna för den nya användarproduktionen [!DNL Salesforce].

1. Välj **[!UICONTROL Settings]** i listrutan **[!UICONTROL My Account]**.

1. Välj **[!UICONTROL Connections]** i grupperingen **[!UICONTROL Integrations]**.

1. Klicka på nyckelikonen till höger om den aktuella anslutna [!DNL Salesforce]-anslutningen och välj **Återauktorisera med produktion**. Logga in med de nya inloggningsuppgifterna igen (om du uppmanas till det).

>[!MORELIKETHIS]
> [Översikt över integreringsbehörigheter](/help/api-connections/integration-permissions-overview.md){target="_blank"}
> [Adobe Admin Console Setup](/help/configuration-and-setup/getting-started-with-marketo-measure/adobe-admin-console-setup.md){target="_blank"}
