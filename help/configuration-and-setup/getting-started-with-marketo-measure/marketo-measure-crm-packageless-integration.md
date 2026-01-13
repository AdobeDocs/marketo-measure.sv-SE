---
description: '[!DNL Marketo Measure] CRM-paketlös integrering - [!DNL Marketo Measure]'
title: Integrering utan CRM-paket för [!DNL Marketo Measure]
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Integrering utan CRM-paket för [!DNL Marketo Measure] {#marketo-measure-crm-packageless-integration}

Alla marknadsföringsteam vill inte (eller har tillgång till) köra marknadsföringsrapporter från CRM, vare sig det beror på begränsad åtkomst, CRM-ägarskap, längre tid till värde eller juridiska konsekvenser. Om du går nedåt i sökvägen för snabbstart [!DNL Marketo Measure] kan du effektivt implementera och köra [!DNL Marketo Measure] med så lite förlitlighet som möjligt på CRM.

## Standardinstallation av [!DNL Marketo Measure] {#standard-marketo-measure-installation}

Genom standardinstallationen av [!DNL Marketo Measure] måste du installera ett [!DNL Salesforce]-paket eller en [!DNL Microsoft Dynamics] hanterad lösning. Installationen innehåller anpassade objekt/entiteter och anpassade fält som har lagts till i CRM som [!DNL Marketo Measure] sedan kan skriva data till.

En paketfri integrering med [!DNL Marketo Measure] är till för kunder som inte vill skapa anpassade objekt/entiteter eller anpassade fält i CRM. Det är också ett bra alternativ för kunder som använder en extern Data Warehouse.

## Behörigheter {#permissions}

En [!DNL Marketo Measure] CRM-paketfri integrering kräver fortfarande åtkomst till CRM-standardobjekt som leads och kontakter. Vi rekommenderar att en dedikerad användare fungerar som den anslutna användaren eftersom de har rätt dataåtkomstbehörighet.

För att alla data ska kunna hämtas korrekt från din CRM behöver vi följande säkerhets- och tillgänglighetsinställningar: Visa alla data för den dedikerade användarens profil. Den här behörighetsgruppen ger [!DNL Marketo Measure] den åtkomst som krävs för att hämta data från standardobjekt. Den här behörighetsgruppen är på profilnivå.

## Konfigurera din identitetsleverantör och dataanslutningar {#setup-your-identity-provider-and-data-connections}

I guiderna nedan hoppar du över stegen för att installera [!DNL Salesforce]-paketet eller [!DNL Microsoft Dynamics] hanterad lösning och följer bara behörighets- och integreringsinstruktionerna.

[!DNL Salesforce] kunder klickar [här](/help/configuration-and-setup/marketo-measure-and-salesforce/install-set-up.md).

[!DNL Microsoft Dynamics] kunder klickar [här](/help/marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

När du är klar med dessa steg bör integreringen fungera. Kontakta din [!DNL Marketo Measure]-representant eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} om du får problem.

>[!NOTE]
>Om du börjar med den [!DNL Marketo Measure] CRM-paketlösa integreringen kan du installera Salesforce-paketet eller Microsoft Dynamics Managed Solution senare.
