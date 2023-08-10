---
unique-page-id: 37356027
description: "[!DNL Marketo Measure] Integrering utan CRM-paket - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Integrering utan CRM-paket"
exl-id: a4f31d82-63ec-4bb2-bc8b-d3495e61af4f
feature: Integration
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# [!DNL Marketo Measure] Integrering utan CRM-paket {#marketo-measure-crm-packageless-integration}

Vi förstår att inte alla marknadsföringsteam vill (eller har tillgång till) köra marknadsföringsrapporter från CRM, vare sig det beror på begränsad åtkomst, CRM-ägarskap, längre tid till värde eller juridiska konsekvenser. Gå längs vägen för [!DNL Marketo Measure] Med Snabbstart kan du implementera och köra [!DNL Marketo Measure] med så lite förlitan på CRM som möjligt.

## Standard [!DNL Marketo Measure] Installation {#standard-marketo-measure-installation}

Genom standarden [!DNL Marketo Measure] måste du installera en [!DNL Salesforce] Paket eller en [!DNL Microsoft Dynamics] Hanterad lösning. Installationen innehåller anpassade objekt/entiteter och anpassade fält som läggs till i CRM-filen som [!DNL Marketo Measure] kan sedan skriva data till.

En paketlös integrering med [!DNL Marketo Measure] är till för kunder som inte vill skapa anpassade objekt/entiteter eller anpassade fält i CRM. Det är också ett bra alternativ för kunder som använder en extern data warehouse.

## Behörigheter {#permissions}

A [!DNL Marketo Measure] Integrering utan CRM-paket kräver fortfarande åtkomst till CRM-standardobjekt som leads och kontakter. Vi rekommenderar starkt att en dedikerad användare fungerar som den anslutna användaren, eftersom de har rätt dataåtkomstbehörighet.

För att alla data ska kunna hämtas korrekt från din CRM behöver vi följande säkerhets- och tillgänglighetsinställningar: Visa alla data för den dedikerade användarens profil. Den här behörighetsgruppen ger [!DNL Marketo Measure] den åtkomst som behövs för att hämta data från standardobjekt. Den här behörighetsgruppen är på profilnivå.

## Konfigurera din identitetsleverantör och dataanslutningar {#setup-your-identity-provider-and-data-connections}

I guiderna nedan hoppar du över stegen för att installera [!DNL Salesforce] paket eller [!DNL Microsoft Dynamics] Hanterad lösning och följ bara behörigheter och integreringsinstruktioner.

[!DNL Salesforce] kunder, klicka [här](/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md).

[!DNL Microsoft Dynamics] kunder, klicka [här](/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md).

När du är klar med alla ovanstående steg är du redo att gå. Om du stöter på några problem under tiden kan du kontakta din [!DNL Marketo Measure] representant eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

>[!NOTE]
>
>Om du börjar med [!DNL Marketo Measure] Integrering utan CRM-paket gör att du kan installera Salesforce-paketet eller Microsoft Dynamics Managed Solution senare.
