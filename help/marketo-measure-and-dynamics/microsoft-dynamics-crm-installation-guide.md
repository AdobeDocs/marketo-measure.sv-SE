---
description: Installationshandbok för [!DNL Microsoft Dynamics] CRM
title: Installationshandbok för [!DNL Microsoft Dynamics] CRM
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 0%

---


# Installationshandbok för [!DNL Microsoft Dynamics] CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se Bizible i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

## Versioner {#supported-versions}

[!DNL Marketo Measure] stöder följande [!DNL Microsoft Dynamics CRM]-versioner:

* [!DNL Microsoft Dynamics 2016] (online och lokalt)
* [!DNL Microsoft Dynamics 365] (online och lokalt)

För anslutning och autentisering stöder [!DNL Marketo Measure] följande Active Directory Federated Services-versioner (ADFS):

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installera den hanterade lösningen {#install-the-managed-solution}

[Hämta och installera](assets/marketo-measure-dynamics-extension.zip) zip-filen i Dynamics CRM.

**[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Import]** (knapp) > **[!UICONTROL Choose File]**.

![Importskärmen för Dynamics CRM-lösningar med importknappen ](assets/1.png)

>[!NOTE]
>Följande två skärmbilder kan skilja sig något från dina, eftersom de togs under en uppgradering.

![Guiden för lösningsimport visar paketval](assets/2.png)

![Bekräftelseskärm för lösningsimport](assets/3.png)

## Skapar en [!DNL Marketo Measure]-användare {#creating-a-marketo-measure-user}

Vi rekommenderar att du skapar en dedikerad Marketo Measure-användare som en&quot;programanvändare&quot; i Dynamics för att exportera och importera data till för att undvika problem med andra användare i CRM. Observera användarnamn och lösenord samt slutpunkts-URL, som de används när [!DNL Marketo Measure]-kontot skapas.

## Säkerhetsroller {#security-roles}

Om din organisation använder Dynamics-säkerhetsroller måste du kontrollera att den anslutna användaren eller den dedikerade [!DNL Marketo Measure]-användaren har tillräcklig läs-/skrivbehörighet för de nödvändiga entiteterna.

Säkerhetsroller finns här: **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Security Roles]**.

För [!DNL Marketo Measure] anpassade entiteter behöver vi fullständig behörighet för alla våra entiteter.

Kampanjens&quot;Skapa&quot;-behörigheter krävs också, utöver läs- och skrivbehörigheterna för standardenheter.

>[!NOTE]
>Användare som stänger affärsmöjligheter behöver också fullständig behörighet.

![Konfigurationsskärmen Dynamics Security Roles visar behörigheter](assets/4.png)

För Dynamics-standardentiteter, se [!DNL Marketo Measure] Dynamics-schemadokumentet. På en hög nivå läser [!DNL Marketo Measure] in vissa entiteter för att samla in lämpliga data och skriva till anpassade fält som är installerade med den hanterade lösningen. Standardposter skapas inte och standardfält uppdateras inte.

## Inkludera kontaktpunkter i sidlayouter: {#include-touchpoints-on-page-layouts}

1. Navigera till Formulärredigeraren för varje entitet. Du kan antingen hitta detta under **[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Customize the System]** > `[Entity]` > **[!UICONTROL Forms]**. Du kan också hitta den i inställningarna när du visar en post.

   * De enheter som ska konfigureras: Konto, Möjlighet, Kontakt, Lead och Campaign.

   * Om du vill konfigurera kampanjer måste du aktivera alternativet för kampanjsynkronisering i **[!UICONTROL CRM]** > **[!UICONTROL Campaigns]**.

   ![Växla kampanjsynkronisering i Marketo Measure-inställningarna](assets/5.png)

1. Sidlayouter: lägg först till en [!UICONTROL One Column]-ruta i det avsnitt som du vill att Touchpoints ska vara aktiva. I den nya kolumnen måste ett underrutnät läggas till i varje formulär inom dina kontoenheter, säljprojekt, kontakter och lead-enheter.

   ![Formulärredigeraren visar avsnittslayout för en kolumn](assets/6.png)

   ![Delstödrasterkomponent läggs till i formulärlayouten](assets/7.png)

1. Markera objektet (Buyer Attribution Touchpoints eller Buyer Touchpoints) som ska återges i underrutnätet, vilket beror på objektrelationen. Du kan också ändra kolumnerna som visas genom att klicka på knappen Redigera. Standardlayouten anges av den hanterade lösningen.

   Buyer Attribution Touchpoint underrutnät - Konton, säljprojekt och kontakt
Buyer Touchpoint underrutnät - Leads och kontakter

   ![Dialogrutan Egenskaper för delstödraster visar alternativ för objektmarkering](assets/8.png)

1. När du är klar med att uppdatera formuläret kan du publicera och spara ändringarna.

## Schemarelaterade överväganden {#schema-related-considerations}

**Intäkter**

[!DNL Marketo Measure] pekar som standard på standardfältet Faktisk omsättning. Om du inte använder detta kan du förklara hur du rapporterar om intäkter till din lösningstekniker eller Success Manager som ett anpassat arbetsflöde kommer att behövas.

**Stäng datum**

[!DNL Marketo Measure] pekar på fältet Faktiskt stängningsdatum utanför rutan. Om du inte använder detta eller också använder fältet Beräknat stängningsdatum, förklara processen för din lösningstekniker eller Success Manager. Det kan behövas ett anpassat arbetsflöde för att ta hänsyn till båda fälten.

## Konfigurera dina anslutningar och dataleverantörer {#configuring-your-connections-and-data-providers}

När du har loggat in på programmet [!DNL Marketo Measure] och konfigurerats som användare i Adobe Admin Console är nästa steg att konfigurera dina olika dataanslutningar.

**CRM som Data Provider**

1. Klicka på listrutan [!DNL Marketo Measure] i ditt **[!UICONTROL My Account]**-konto och välj **[!UICONTROL Settings]**.

   ![Listrutan Mitt konto i Marketo Measure med alternativet Inställningar markerat](assets/microsoft-dynamics-crm-installation-guide-16.png)

1. Klicka på [!UICONTROL Integrations] under **[!UICONTROL Connections]** i den vänstra navigeringen.

   ![Sidan Inställningar med alternativet Anslutningar i vänster navigering](assets/microsoft-dynamics-crm-installation-guide-17.png)

1. Klicka på knappen **[!UICONTROL Set Up New CRM Connection]**.

   ![Sidan Anslutningar med knappen Konfigurera ny CRM-anslutning](assets/microsoft-dynamics-crm-installation-guide-18.png)

1. Klicka på knappen [!UICONTROL Microsoft Dynamics CRM] bredvid **[!UICONTROL Connect]**.

   ![Anslutningsalternativ för CRM som visar Microsoft Dynamics CRM med knappen Anslut](assets/microsoft-dynamics-crm-installation-guide-19.png)

1. Välj [!UICONTROL Credentials] eller [!UICONTROL OAuth].

   ![Välja autentiseringsmetod i Microsoft Dynamics CRM](assets/microsoft-dynamics-crm-installation-guide-20.png)

   >[!NOTE]
   >Mer information om OAuth finns på [den här artikeln](/help/marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md). Om du har några frågor om processen kontaktar du din [!DNL Marketo Measure]-kontorepresentant.

1. I det här exemplet har vi valt autentiseringsuppgifter. Ange dina autentiseringsuppgifter och klicka på **[!UICONTROL Next]**.

När du har anslutit visas information om din Dynamics-anslutning i listan CRM/MAP-anslutningar.

**Lägg till kontoanslutningar**

Om du vill ansluta dina annonskonton till [!DNL Marketo Measure] börjar du med att gå till fliken [!UICONTROL Connections] i programmet [!DNL Marketo Measure].

1. Följ steg 1 och 2 i avsnittet _CRM som Data Provider_ ovan.

1. Klicka på knappen **[!UICONTROL Set up New CRM Connection]**.

   ![Sidan Anslutningar visar knappen Konfigurera ny CRM-anslutning](assets/microsoft-dynamics-crm-installation-guide-21.png)

1. Välj plattform.

   ![Lägg till skärmen för val av plattform för konto med olika alternativ för annonseringsplattform](assets/microsoft-dynamics-crm-installation-guide-22.png)

**[!DNL Marketo Measure]JavaScript**

För att [!DNL Marketo Measure] ska kunna spåra dina webbaktiviteter finns det flera steg för konfiguration.

1. Klicka på listrutan **[!UICONTROL My Account]** och välj **[!UICONTROL Account Configuration]**.

   ![Listrutan Mitt konto med alternativet Kontokonfiguration](assets/microsoft-dynamics-crm-installation-guide-23.png)

1. Ange ditt telefonnummer. För Webbplats anger du den primära rotdomän som används för [!DNL Marketo Measure]-spårning på webbplatsen. Klicka på **[!UICONTROL Save]** när du är klar.

   ![Sidan Kontokonfiguration med telefonnummer och webbplatsfält](assets/microsoft-dynamics-crm-installation-guide-24.png)

   >[!NOTE]
   >Kontakta din [!DNL Marketo Measure]-kontorepresentant om du vill lägga till flera rotdomäner.

1. [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/adding-marketo-measure-script.md) måste sedan placeras över hela webbplatsen och landningssidorna. Vi rekommenderar att skriptet hårdkodas i huvudet på dina landningssidor eller läggs till via ett Tag Management-system som [Google Tag Manager](/help/marketo-measure-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >Som standard exporterar [!DNL Marketo Measure] 200 poster per API-kredit varje gång ett jobb skickar data till din CRM. För de flesta kunder ger detta den optimala balansen mellan API-krediter som används av [!DNL Marketo Measure] och CPU-resurskrav i CRM. För kunder med komplexa CRM-konfigurationer, till exempel arbetsflöden och utlösare, kan en mindre gruppstorlek vara användbar för att förbättra CRM-prestanda. Därför tillåter [!DNL Marketo Measure] kunder att konfigurera CRM-exportens batchstorlek. Den här inställningen är tillgänglig på sidan Inställningar > CRM > Allmänt i webbprogrammet [!DNL Marketo Measure] och kunderna kan välja mellan gruppstorlekar på 200 (standard), 100, 50 eller 25.
   >När du ändrar den här inställningen bör du tänka på att mindre gruppstorlekar förbrukar fler API-krediter från din CRM. Du bör bara minska batchstorleken om du har CPU-timeout eller hög CPU-belastning i CRM.

   >[!NOTE]
   >När du inaktiverar Marketo Measure export av data till Dynamics tas inga befintliga data bort. Kontakta Dynamics Support om du behöver hjälp med att ta bort befintliga data.

   >[!MORELIKETHIS]
   >[Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
