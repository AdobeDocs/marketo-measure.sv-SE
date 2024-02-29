---
unique-page-id: 18874763
description: '"[!DNL Microsoft Dynamics] Installationshandbok för CRM - Marketo Measure - produktdokumentation'
title: "[!DNL Microsoft Dynamics] Installationshandbok för CRM"
exl-id: bc422c98-60bb-49ea-9bd1-c4149ae628b1
feature: Installation, Microsoft Dynamics
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# [!DNL Microsoft Dynamics] Installationshandbok för CRM {#microsoft-dynamics-crm-installation-guide}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

## Versioner {#supported-versions}

[!DNL Marketo Measure] stöder följande [!DNL Microsoft Dynamics CRM] versioner:

* [!DNL Microsoft Dynamics 2016] (Online och On-Premise)
* [!DNL Microsoft Dynamics 365] (Online och On-Premise)

För anslutning och autentisering [!DNL Marketo Measure] har stöd för följande AD FS-versioner (Active Directory Federated Services):

* ADFS 4.0 - [!DNL Windows Server 2016]
* ADFS 5.0 - [!DNL Windows Server 2019]

## Installera den hanterade lösningen {#install-the-managed-solution}

[Hämta och installera](assets/marketo-measure-dynamics-extension.zip) ZIP-filen i Dynamics CRM.

**[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Solutions]** > **[!UICONTROL Import]** (button) > **[!UICONTROL Choose File]**.

![](assets/1.png)

>[!NOTE]
>
>Följande två skärmbilder kan skilja sig något från dina, eftersom de togs under en uppgradering.

![](assets/2.png)

![](assets/3.png)

## Skapa en [!DNL Marketo Measure] Användare {#creating-a-marketo-measure-user}

Vi rekommenderar att du skapar en dedikerad Marketo Measure-användare som en&quot;programanvändare&quot; i Dynamics för att kunna exportera och importera data till för att undvika problem med andra användare i CRM. Notera användarnamn och lösenord samt slutpunkts-URL, eftersom de kommer att användas när du skapar [!DNL Marketo Measure] konto.

## Säkerhetsroller {#security-roles}

Om din organisation använder Dynamics-säkerhetsroller ska du kontrollera att den anslutna användaren eller den dedikerade [!DNL Marketo Measure] Användaren har tillräcklig läs-/skrivbehörighet för de begärda entiteterna.

Säkerhetsroller finns här: **[!UICONTROL Settings]** > **[!UICONTROL Security]** > **[!UICONTROL Security Roles]**.

För [!DNL Marketo Measure] anpassade enheter behöver vi fullständig behörighet för alla våra enheter.

>[!NOTE]
>
>Användare som stänger affärsmöjligheter behöver också fullständig behörighet.

![](assets/4.png)

För Dynamics-standardenheter, se [!DNL Marketo Measure] Dynamics-schemadokument. På en hög nivå [!DNL Marketo Measure] behöver bara läsa in vissa enheter för att samla in lämpliga data och skriva till anpassade fält som installeras med den hanterade lösningen. Vi kommer inte att skapa nya standardposter och vi kommer inte heller att uppdatera några standardfält.

## Inkludera kontaktpunkter i sidlayouter: {#include-touchpoints-on-page-layouts}

1. Navigera till Formulärredigeraren för varje entitet. Du kan antingen hitta det här under **[!UICONTROL Settings]** > **[!UICONTROL Customizations]** > **[!UICONTROL Customize the System]** > `[Entity]` > **[!UICONTROL Forms]**. Du kan också hitta den i inställningarna när du visar en post.

   * De enheter som ska konfigureras: Konto, Möjlighet, Kontakt, Lead och Campaign.

   * Om du vill konfigurera kampanjer måste du aktivera alternativet&quot;Kampanjsynkronisering&quot; i **[!UICONTROL CRM]** > **[!UICONTROL Campaigns]**.

   ![](assets/5.png)

1. Sidlayout: lägg först till en[!UICONTROL One Column]&quot; i det avsnitt där du vill att Touchpoints ska vara aktiva. I den nya kolumnen måste ett underrutnät läggas till i varje formulär inom dina konton, säljprojekt, kontakter och lead-enheter.

   ![](assets/6.png)

   ![](assets/7.png)

1. Markera objektet (Buyer Attribution Touchpoints eller Buyer Touchpoints) som ska återges i underrutnätet, vilket beror på objektrelationen. Du kan också ändra kolumnerna som ska visas genom att klicka på knappen Redigera. En standardlayout har angetts av den hanterade lösningen.

   Slutpunktsrutnät för Buyer Attribution - konton, säljprojekt och kontakt\
   Buyer Touchpoint Subgrid - Leads and Contacts

   ![](assets/8.png)

1. När du är klar med att uppdatera formuläret kan du publicera och spara ändringarna.

## Schemarelaterade överväganden {#schema-related-considerations}

**Intäkter**

[!DNL Marketo Measure] pekar på standardfältet Faktisk omsättning. Om du inte använder detta kan du förklara hur du rapporterar om intäkter till din lösningstekniker eller Success Manager som ett anpassat arbetsflöde kommer att behövas.

**Stängningsdatum**

[!DNL Marketo Measure] pekar på fältet Faktiskt stängningsdatum utanför rutan. Om du inte använder detta eller också använder fältet Beräknat stängningsdatum, förklara processen för din lösningstekniker eller Success Manager. Ett anpassat arbetsflöde kan behöva användas för båda fälten.

## Konfigurera dina anslutningar och dataleverantörer {#configuring-your-connections-and-data-providers}

När du har loggat in på [!DNL Marketo Measure] och har konfigurerats som användare i Adobe Admin Console är nästa steg att konfigurera dina olika dataanslutningar.

**CRM som dataleverantör**

1. I [!DNL Marketo Measure] klickar du på **[!UICONTROL My Account]** nedrullningsbar meny och välj **[!UICONTROL Settings]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-16.png)

1. Under [!UICONTROL Integrations] i vänstra navigeringen klickar du på **[!UICONTROL Connections]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-17.png)

1. Klicka på **[!UICONTROL Set Up New CRM Connection]** -knappen.

   ![](assets/microsoft-dynamics-crm-installation-guide-18.png)

1. Nästa till [!UICONTROL Microsoft Dynamics CRM]klickar du på **[!UICONTROL Connect]** -knappen.

   ![](assets/microsoft-dynamics-crm-installation-guide-19.png)

1. Välj [!UICONTROL Credentials] eller [!UICONTROL OAuth].

   ![](assets/microsoft-dynamics-crm-installation-guide-20.png)

   >[!NOTE]
   >
   >Mer information om OAuth finns på [den här artikeln](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/oauth-with-azure-active-directory-for-dynamics-crm.md). Om du har frågor om processen kan du kontakta [!DNL Marketo Measure] Kontorepresentant.

1. I det här exemplet har vi valt autentiseringsuppgifter. Ange dina uppgifter och klicka på **[!UICONTROL Next]**.

När du har anslutit visas information om din Dynamics-anslutning i listan CRM/MAP-anslutningar.

**Ad Account Connections**

Koppla samman annonskonton med [!DNL Marketo Measure], börja med att besöka [!UICONTROL Connections] -fliken i [!DNL Marketo Measure] program.

1. Följ steg 1 och 2 ovan _CRM som dataleverantör_ -avsnitt.

1. Klicka på **[!UICONTROL Set up New CRM Connection]** -knappen.

   ![](assets/microsoft-dynamics-crm-installation-guide-21.png)

1. Välj plattform.

   ![](assets/microsoft-dynamics-crm-installation-guide-22.png)

**[!DNL Marketo Measure]Javascript**

För att [!DNL Marketo Measure] för att spåra dina webbaktiviteter finns det flera steg för konfiguration.

1. Klicka på **[!UICONTROL My Account]** nedrullningsbar meny och välj **[!UICONTROL Account Configuration]**.

   ![](assets/microsoft-dynamics-crm-installation-guide-23.png)

1. Ange ditt telefonnummer. Ange din primära rotdomän som ska användas för webbplatsen [!DNL Marketo Measure] spårning på din webbplats. Klicka **[!UICONTROL Save]** när det är klart.

   ![](assets/microsoft-dynamics-crm-installation-guide-24.png)

   >[!NOTE]
   >
   >Om du vill lägga till flera rotdomäner kontaktar du [!DNL Marketo Measure] Kontorepresentant.

1. The [[!DNL Marketo Measure] JavaScript](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script.md) måste sedan placeras över hela sajten och landningssidorna. Vi rekommenderar att skriptet hårdkodas i huvudet på landningssidorna eller läggs till via ett Tag Management-system som [Google Tag Manager](/help/marketo-measure-tracking/setting-up-tracking/adding-marketo-measure-script-via-google-tag-manager.md).

   >[!NOTE]
   >
   >Som standard [!DNL Marketo Measure] exporterar 200 poster per API-kredit varje gång ett jobb skickar data till din CRM. För de flesta kunder ger detta den optimala balansen mellan API-krediter som [!DNL Marketo Measure] och CPU-resurskrav för CRM. För kunder med komplexa CRM-konfigurationer, till exempel arbetsflöden och utlösare, kan en mindre gruppstorlek vara användbar för att förbättra CRM-prestanda. I detta syfte [!DNL Marketo Measure] gör det möjligt för kunder att konfigurera batchstorleken för CRM-export. Den här inställningen är tillgänglig på sidan Inställningar > CRM > Allmänt i dialogrutan [!DNL Marketo Measure] webbprogram och kunder kan välja mellan gruppstorlekar på 200 (standard), 100, 50 eller 25.
   >
   >När du ändrar den här inställningen bör du tänka på att mindre gruppstorlekar förbrukar fler API-krediter från din CRM. Du bör bara minska batchstorleken om du har CPU-timeout eller hög CPU-belastning i CRM.

   >[!NOTE]
   >
   >När du inaktiverar Marketo Measure export av data till Dynamics tas inga befintliga data bort. Kontakta Dynamics Support om du behöver hjälp med att ta bort befintliga data.

   >[!MORELIKETHIS]
   >
   >[Felmeddelanden](/help/configuration-and-setup/getting-started-with-marketo-measure/error-notifications.md){target="_blank"}
