---
unique-page-id: 42762648
description: Kohort Journey Dashboard Documentation - [!DNL Marketo Measure] - Produktdokumentation
title: Kohort Journey Dashboard Documentation
exl-id: b139f720-86ae-4f6d-9dfc-cc67b4186f88
source-git-commit: 68d860308fa1939a1c456314ade3d34f896df831
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Kohort Journey Dashboard Documentation {#cohort-journey-dashboard-documentation}

Med kontrollpanelerna Kohort Impact och Funnel kan marknadsförarna visa förloppet från en startkohortfas för en vald tidsram och mäta konverteringsgraden.

Den största skillnaden är hur vi räknar varje enhet från kohortfasen.

* Kohorttratt: Resultatet av varje fas härleds direkt från det föregående steget.

   * Endast poster som genomgick varje fas längre ned i tratten efter den angivna kohortstarttiden räknas.

![](assets/cohort-journey-dashboard-documentation-1.png)

* Kohortpåverkan: Resultatet av varje fas härleds från kohortfasen, inte från det tidigare stadiet.

   * Alla poster i varje fas räknas så länge som de inträffar efter den angivna kohortens starttid. Den här instrumentpanelen kommer naturligtvis att ha fler poster än Funnel Dashboard eftersom vi tittar på hur enheterna påverkades från kohortfasen, inte bara rörelsen genom tratten.

![](assets/cohort-journey-dashboard-documentation-2.png)

Varje kontrollpanel har två paneler:

* Kohortintäkter: Det totala affärsmöjlighetsbeloppet från alla möjligheter i avtalsfasen i Cohort Journey-gruppen.
* Kohort Journey: Förloppet till varje resefas från startkohortsteget för en vald tidsram.

>[!NOTE]
>
>På alla Discover-paneler kan bara ett personobjekt, antingen lead eller kontakt, rapporteras. Detta anges i [!UICONTROL Settings] > [!UICONTROL Reporting] > [!UICONTROL Attribution Settings] > [!UICONTROL Default Dashboard Object].

Kontrollpanelen har stöd för följande filter:

* Kohortfas: välj startkohortfas. Poster i alla följande steg utvecklas från posterna i kohortfasen.
* Kohortdatumintervall: Välj tidsram för den markerade kohortscenen. Tillsammans med kohortscenen definieras startdatauppsättningen.
* Brytdatum: Välj det datum då postens förlopp i alla följande steg måste inträffa. Standard är idag. Observera att detta gäller alla stadier utom kohortfasen.
* Kanal: filtrera posterna efter kanaler. En post kopplas till en kanal om någon av dess kontaktytor är kopplad till kanalen.
* Delkanal: filtrera posterna efter delkanaler. En post kopplas till en underkanal om någon av dess kontaktytor är kopplad till underkanalen.
* Campaign: filtrera posterna efter kampanjer. En post associeras med en kampanj om någon av dess kontaktytor är associerad med kampanjen.
* Kampanjkälla: filtrera posterna efter kampanjkällor. Exempel på kampanjkällor är [!DNL Adwords], [!DNL BingAds], [!DNL Facebook], [!DNL LinkedIn], osv. En post kopplas till en kampanjkälla om någon av dess kontaktytor är kopplad till kampanjkällan.
* Segmentfilter: filtrera posterna efter anpassade segment. En post kopplas till ett segment om någon av dess kontaktytor är kopplad till segmentet.

För alla filter används&quot;AND&quot;-logik.

>[!NOTE]
>
>Segmentfilter gäller endast för LC-scenen och efter. Om kohortscenen är okänd eller känd och ett av segmentfiltren har ett värde returnerar instrumentpanelen inga resultat.

![](assets/cohort-journey-dashboard-documentation-3.png)

Stegen är Okänd, Känd, LC, valda trattfaser i Öppet lead/kontaktsteg (Inställningar > CRM > Stage Mapping), OC, valda trattfaser i Öppna säljprojektsstadier (Inställningar > CRM > Stage Mapping) och avtal (stängda Won-affärsmöjligheter).

>[!NOTE]
>
>Posterna för en resefas, som definieras som en annan fas än kohortfasen, innehåller alla nya poster, som är relaterade till kohortposterna, som skapas efter startdatumet för den valda tidsramen och före brytdatumet. Detta är en slutsats om orsakssamband.

Du kan gå ned i varje fält för att visa posterna för varje scen.

* För Okänd visas anonym besökarinformation.
* För Känd visas information om besökare.
* För LC och Open Lead/Contact-stadier visas information om lead/kontakt.
* För OC, öppna säljprojektsfaser och erbjudanden visas information om säljprojekt.
