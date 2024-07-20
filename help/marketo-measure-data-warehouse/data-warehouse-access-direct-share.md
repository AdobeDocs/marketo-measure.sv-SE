---
description: Data Warehouse Access - Direct Share - Product Documentation
title: Åtkomst till Data Warehouse - direktdelning
exl-id: 940c3316-5f94-4aa2-a656-aec5eb7b7450
feature: Data Warehouse
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# Åtkomst till Data Warehouse - direktdelning {#data-warehouse-access-direct-share}

## Krav {#requirements}

För att [!DNL Marketo Measure] ska kunna konfigurera en direkt resurs till datalagret måste du uppfylla följande krav.

* Du har en egen Snowflake-instans.
* Din Snowflake-instans finns i Azure East US 2 Snowflake.
* Du ger [!DNL Marketo Measure] ditt konto-ID för Snowflake.

## Begränsningar {#limitations}

[!DNL Marketo Measure] kan bara konfigurera Snowflake Direct Shares med konton i Azure East US 2 på grund av nuvarande Snowflake Direct Share-begränsningar. Om du vill att dina data ska vara tillgängliga i andra Snowflake-regioner rekommenderar vi att du skapar en kopia av data i ett Snowflake-konto i Azure East US 2 och använder funktionen [Snowflake Database Replication](https://docs.snowflake.com/en/user-guide/database-replication-intro.html){target="_blank"} för att kopiera dina data i valfritt Snowflake-område/konto.

## Ange konto-ID för Snowflake {#enter-snowflake-account-id}

Öppna avsnittet **Inställningar** i Marketo Measure-appen och gå till sidan **Data Warehouse**. I avsnittet **Direktdelning** anger du ditt [Snowflake-konto-ID](https://docs.snowflake.com/en/user-guide/admin-account-identifier.html){target="_blank"} i rutan som visas och klickar på **Anslut**.

![](assets/data-warehouse-access-direct-share-1.png)

## Åtkomst till resursen {#accessing-the-share}

När resursen har skapats för det konto-ID som anges måste du slutföra [konfigurationsstegen](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"} i din Snowflake-instans för att komma åt data.

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

Mer detaljerade instruktioner och steg för att utföra dessa steg från användargränssnittet i Snowflake finns i [Snowflake-dokumentationen direkt](https://docs.snowflake.com/en/user-guide/data-share-consumers.html){target="_blank"}.
