---
description: Beskriver hur du konfigurerar och använder ett läsarkonto för att få åtkomst till Marketo Measure datalager
title: Data Warehouse Access - Reader-konto
exl-id: 2aa73c41-47ab-4f11-96d8-dafb642308fc
feature: Data Warehouse
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 1%

---

# Data Warehouse Access - Reader-konto {#data-warehouse-access-reader-account}

## Snowflake Access Link {#snowflake-access-link}

Om du vill få tillgång till ditt Snowflake datalager måste du navigera till den specifika URL:en för ditt Snowflake-konto. Du hittar den här åtkomstlänken genom att logga in på [!DNL Marketo Measure] och följa stegen nedan för att navigera till informationssidan för Data Warehouse.

1. I [!DNL Marketo Measure], överst på sidan, klickar du på **[!UICONTROL My Account]** > **[!UICONTROL Settings]**.

   ![1. Klicka ](assets/data-account-7.png) överst på sidan i Marketo Measure

1. Klicka på **[!UICONTROL Data Warehouse]** under Säkerhet på den vänstra menyn.

   ![1. Klicka på Data Warehouse under Säkerhet på den vänstra menyn.](assets/data-account-8.png)

1. Den här sidan har länken till ditt Snowflake datalager och ditt användarnamn.

   ![1. Den här sidan har länken till ditt Snowflake datalager och ](assets/data-account-9.png)

   >[!NOTE]
   >
   >Det här är ett skrivskyddat konto som är tillgängligt för din organisation, inte bara för en enskild användare. Alla användare i organisationen som har åtkomst till [!DNL Marketo Measure] kan använda det här kontot för att logga in på Snowflake Data Warehouse Reader-kontot.

1. Klicka på länken som finns i Snowflake URL, så kommer du till inloggningssidan för Snowflake där du anger ditt användarnamn och lösenord. _Om du inte har ditt lösenord läser du stegen nedan för att återställa det_.

   ![1. Klicka på länken som anges i Snowflake-URL:en. Detta tar dig](assets/data-account-5.png)

1. När du är inloggad klickar du på **[!UICONTROL Worksheets]** överst på sidan.

   ![1. När du är inloggad klickar du på Kalkylblad överst i ](assets/data-account-6.png)

1. Databasobjekten BIZIBLE_ROI_V3 finns till vänster på skärmen. Ange lagerställe, databas och schema i listrutan längst upp i frågefönstret. Det ska bara finnas ett alternativ för varje. Nu kan du köra frågor i Snowflake frågeredigerare.

   ![1. Databasobjekten BIZIBLEROIV3 finns till vänster om ](assets/data-account-4.png)

## Återställ lösenordet {#reset-your-password}

[!DNL Marketo Measure] har inte åtkomst till ditt inloggningslösenord för Snowflake. Om du måste återställa ditt lösenord klickar du på knappen [!UICONTROL Reset Password] på informationssidan för Data Warehouse och följer instruktionerna. Ett tillfälligt lösenord visas omedelbart i användargränssnittet. Du uppmanas att skapa ett eget lösenord på nästa inloggning på datalagret.

>[!NOTE]
>
>* Om du återställer lösenordet återställs det för alla [!DNL Marketo Measure] användare i organisationen, inte bara för den användare som är inloggad för tillfället.
>* Vi visar bara det tillfälliga lösenordet i användargränssnittet. Inget e-postmeddelande skickas.

![Det tillfälliga lösenordet visas bara i användargränssnittet. Ett e-postmeddelande ](assets/data-account-3.png)

![Det tillfälliga lösenordet visas bara i användargränssnittet. Ett e-postmeddelande ](assets/data-account-1.png)

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

  ![Lagerstället är det som kör frågor i Snowflake. Det är den beräknade ](assets/data-account-2.png)
