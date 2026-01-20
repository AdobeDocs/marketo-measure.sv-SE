---
description: Data Warehouse Access - Reader Account - produktdokumentation
title: Data Warehouse Access - Reader-konto
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Data Warehouse Access - Reader-konto {#data-warehouse-access-reader-account}

## Snowflake Access Link {#snowflake-access-link}

Om du vill få tillgång till ditt Snowflake datalager måste du navigera till den specifika URL:en för ditt Snowflake-konto. Du hittar den här åtkomstlänken genom att logga in på [!DNL Marketo Measure] och följa stegen nedan för att navigera till informationssidan för Data Warehouse.

1. I [!DNL Marketo Measure], överst på sidan, klickar du på **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![](assets/data-warehouse-access-reader-account-1.png)

1. Klicka på **[!UICONTROL Data Warehouse]** under Säkerhet på den vänstra menyn.

   ![](assets/data-warehouse-access-reader-account-2.png)

1. Den här sidan har länken till ditt Snowflake datalager och ditt användarnamn.

   ![](assets/data-warehouse-access-reader-account-3.png)

   >[!NOTE]
   >
   >Det här är ett skrivskyddat konto som är tillgängligt för din organisation, inte bara för en enskild användare. Alla användare i organisationen som har åtkomst till [!DNL Marketo Measure] kan använda det här kontot för att logga in på Snowflake Data Warehouse Reader-kontot.

1. Klicka på länken som finns i Snowflake URL, så kommer du till inloggningssidan för Snowflake där du anger ditt användarnamn och lösenord. _Om du inte har ditt lösenord läser du stegen nedan för att återställa det_.

   ![](assets/data-warehouse-access-reader-account-4.png)

1. När du är inloggad klickar du på **[!UICONTROL Worksheets]** överst på sidan.

   ![](assets/data-warehouse-access-reader-account-5.png)

1. Databasobjekten BIZIBLE_ROI_V3 finns till vänster på skärmen. Ange lagerställe, databas och schema i listrutan längst upp i frågefönstret. Det ska bara finnas ett alternativ för varje. Nu kan du köra frågor i Snowflake frågeredigerare.

   ![](assets/data-warehouse-access-reader-account-6.png)

## Återställ lösenordet {#reset-your-password}

[!DNL Marketo Measure] har inte åtkomst till ditt inloggningslösenord för Snowflake. Om du måste återställa ditt lösenord klickar du på knappen [!UICONTROL Reset Password] på informationssidan för Data Warehouse och följer instruktionerna. Ett tillfälligt lösenord visas omedelbart i användargränssnittet. Du uppmanas att skapa ett eget lösenord på nästa inloggning på datalagret.

>[!NOTE]
>
>* Om du återställer lösenordet återställs det för alla [!DNL Marketo Measure] användare i organisationen, inte bara för den användare som är inloggad för tillfället.
>* Vi visar bara det tillfälliga lösenordet i användargränssnittet. Inget e-postmeddelande skickas.

![](assets/data-warehouse-access-reader-account-7.png)

![](assets/data-warehouse-access-reader-account-8.png)

## Ansluta till Snowflake via tredjepartsverktyg {#connecting-to-snowflake-via-third-party-tools}

Du måste ange några uppgifter för att kunna koppla ditt Snowflake datalager till ett tredjepartsverktyg.

>[!NOTE]
>
>Varje verktyg har olika anslutningskrav. Vi rekommenderar att du läser dokumentationen för det specifika verktyg som du försöker ansluta till.

* **URI** (alltid obligatoriskt)
   * Detta är domännamnet för Snowflake-kontot. Den finns i en del av inloggningslänken för Snowflake.
* **Användarnamn** (alltid obligatoriskt)
   * Användarnamnet visas på informationssidan för Data Warehouse i [!DNL Marketo Measure].
* **Lösenord** (alltid obligatoriskt)
   * Det här är lösenordet som du angav första gången du loggade in på ditt Snowflake-konto. Information om hur du återställer lösenordet finns i instruktionerna ovan.
* **Databasnamn** (krävs inte alltid)
   * Databasen är den som lagrar data i Snowflake. Det är lagringsresursen. Databasnamnet visas på informationssidan för Data Warehouse i [!DNL Marketo Measure].
* **Namn på lagerställe** (krävs inte alltid)
   * Det är lagerstället som kör frågor i Snowflake. Det är den beräknade resursen. Lagerställets namn visas på informationssidan för Data Warehouse i [!DNL Marketo Measure].

  ![](assets/data-warehouse-access-reader-account-9.png)
