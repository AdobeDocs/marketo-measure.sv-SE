---
description: Data warehouse Access - Reader Account - produktdokumentation
title: Data warehouse Access - Reader Account
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Data warehouse Access - Reader Account {#data-warehouse-access-reader-account}

## Snowflake Access Link {#snowflake-access-link}

Om du vill komma åt Snowflake data warehouse måste du navigera till den specifika URL:en för ditt Snowflake-konto. Du hittar den här länken genom att logga in [!DNL Marketo Measure] och följer stegen nedan för att navigera till informationssidan för Data warehouse.

1. I [!DNL Marketo Measure], längst upp på sidan, klicka på **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. På den vänstra menyn under Dokumentskydd klickar du på **[!UICONTROL Data Warehouse]**.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. På den här sidan hittar du länken till Snowflake data warehouse och ditt användarnamn.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Det här är ett skrivskyddat konto som är tillgängligt för din organisation, inte bara för en enskild användare. Alla användare i organisationen som har tillgång till [!DNL Marketo Measure] kan använda det här kontot för att logga in på läsarkontot i Snowflake Data warehouse.

1. Klicka på länken i Snowflake URL:en så kommer du till inloggningssidan för Snowflake där du anger ditt användarnamn och lösenord. _Om du inte har ditt lösenord läser du stegen nedan för att återställa det_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. När du är inloggad klickar du på **[!UICONTROL Worksheets]** överst på sidan.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Databasobjekten BIZIBLE_ROI_V3 finns till vänster på skärmen. Ange lagerställe, databas och schema i listrutan längst upp i frågefönstret. Det ska bara finnas ett alternativ för varje. Nu kan du köra frågor i Snowflake-frågeredigeraren.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Återställ lösenordet {#reset-your-password}

[!DNL Marketo Measure] har inte åtkomst till ditt inloggningslösenord för Snowflake. Om du behöver återställa ditt lösenord klickar du på [!UICONTROL Reset Password] på informationssidan för Data warehouse och följ instruktionerna. Ett tillfälligt lösenord visas omedelbart i användargränssnittet. Du uppmanas att skapa ett eget lösenord nästa gång du loggar in i data warehouse.

>[!NOTE]
>
>* Om du återställer lösenordet återställs det för alla [!DNL Marketo Measure] -användare i din organisation, inte bara den användare som är inloggad.
>* Vi visar bara det tillfälliga lösenordet i användargränssnittet. Inget e-postmeddelande skickas.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Ansluta till Snowflake via tredjepartsverktyg {#connecting-to-snowflake-via-third-party-tools}

Du måste ange några uppgifter för att kunna ansluta Snowflake data warehouse till ett tredjepartsverktyg.

>[!NOTE]
>
>Varje verktyg har olika anslutningskrav. Vi rekommenderar att du läser dokumentationen för det specifika verktyg som du försöker ansluta till.

* **URI** (alltid obligatoriskt)
   * Detta är domännamnet för Snowflake-kontot.  Den finns i en del av inloggningslänken för Snowflake.
* **Användarnamn** (alltid obligatoriskt)
   * Användarnamnet visas på informationssidan för Data warehouse i [!DNL Marketo Measure].
* **Lösenord** (alltid obligatoriskt)
   * Det här är det lösenord som du angav första gången du loggade in på ditt Snowflake-konto.  Information om hur du återställer lösenordet finns i instruktionerna ovan.
* **Databasnamn** (krävs inte alltid)
   * Databasen är den som lagrar data i Snowflake. Det är lagringsresursen. Databasnamnet visas på informationssidan i Data warehouse i [!DNL Marketo Measure].
* **Namn på lagerställe** (krävs inte alltid)
   * Det är lagerstället som kör frågor i Snowflake. Det är beräkningsresursen.  Lagerställets namn visas på informationssidan Data warehouse i [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
