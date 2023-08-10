---
description: Data warehouse Access - Direct Share - produktdokumentation
title: Data warehouse Access - direktdelning
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Data warehouse Access - direktdelning {#data-warehouse-access-direct-share}

## Krav {#requirements}

För att [!DNL Marketo Measure] om du vill lägga upp en direktdelning till data warehouse måste du uppfylla följande krav.

* Du har en egen Snowflake-instans.
* Din Snowflake-instans finns i Azure East US 2 Snowflake.
* Du anger [!DNL Marketo Measure] med ditt konto-ID för Snowflake.

## Begränsningar {#limitations}

[!DNL Marketo Measure] kommer endast att kunna ställa in Snowflake Direct Shares med konton i Azure East US 2 på grund av nuvarande begränsningar för Snowflake Direct Share. Om du vill att dina data ska vara tillgängliga i andra Snowflake-regioner rekommenderar vi att du skapar en kopia av data i ett Snowflake-konto som finns i Azure East US 2 och använder [Snowflake-databasreplikering](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} för att kopiera data i valfritt Snowflake-land/konto.

## Ange konto-ID för Snowflake {#enter-snowflake-account-id}

Öppna **Inställningar** i Marketo Measure och navigera till **Data warehouse** sida. I **Direktdelning** -avsnittet, ange [Snowflake account id](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} i rutan och klicka **Anslut**.

![](assets/data-warehouse-access-direct-share-1.png)

## Åtkomst till resursen {#accessing-the-share}

När resursen har skapats för konto-ID:t måste du slutföra [konfigurationssteg](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} i din Snowflake-instans för att få tillgång till data.

>[!NOTE]
>
>Du kan välja valfritt databasnamn. Du kan tilldela behörigheter till vilken roll du vill, så länge den finns i din Snowflake-instans.

* Använd rollen Kontoadministratör

```
USE ROLE ACCOUNTADMIN
```

* Visa tillgängliga resurser (här visas namnet på den tilldelade resursen)

```
SHOW SHARES
```

* Skapa en databas för resursen

```
CREATE DATABASE <database_name> FROM SHARE <provider_account>.<share_name>
```

* Bevilja privilegier för den delade databasen

```
GRANT IMPORTED PRIVILEGES ON DATABASE <database_name> TO ROLE <role_name>
GRANT IMPORTED PRIVILEGES ON ALL SCHEMAS IN DATABASE <database_name> TO ROLE <role_name>
```

Mer detaljerade anvisningar och steg för att utföra dessa steg från användargränssnittet i Snowflake finns i [Snowflake dokumentation direkt](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
