---
description: Metoder för utgiftshantering - [!DNL Marketo Measure]
title: Metoder för utgiftshantering
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Metoder för utgiftshantering {#spend-management-methods}

Utgiftsdata är avgörande för att avkastningen ska kunna rapporteras med [!DNL Marketo Measure]. För att få en korrekt och heltäckande rapportering om avkastning på investering i alla kanaler och underkanaler måste ni se till att ni har rätt utgiftsdata insamlade i [!DNL Marketo Measure].

Det finns tre sätt att få in utgiftsdata i [!DNL Marketo Measure]. Varje metod är utformad för att hämta utgiftsdata från vissa dataindata.

**1 API-anslutna konton**

Alla annonskonton som du har anslutit till [!DNL Marketo Measure] genom ett API får man automatiskt in [!DNL Marketo Measure] för avkastningsrapportering. Om du vill kontrollera vilka konton du har kopplat in och därmed ta in utgifter går du till [!DNL Marketo Measure] App och välj [!UICONTROL Connections] under [!UICONTROL Integrations] -avsnitt. Mer information om hur du konfigurerar dina API-anslutningar finns i [Integrerade annonsplattformar](/help/api-connections/utilizing-marketo-measures-api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms).

**2 CRM Kampanjkostnadssynkronisering**

Varje [!DNL Marketo Measure] kontot har åtkomst till en funktion som kallas [Synkronisera CRM-kampanjkostnader](/help/marketing-spend/spend-management/crm-campaign-costs.md#availability). Som standard är den här funktionsbiten inställd på Nej, men den kan aktiveras när som helst.

![](assets/spend-management-methods-1.png)

När den här funktionen är aktiverad hämtas utgifter automatiskt in från alla CRM-kampanjer/program som uppfyller följande kriterier:

i. [!DNL Marketo Measure] tittar först för att se om Campaign/Program skapar kontaktytor, antingen från en matchande [Synkroniseringsregel för kampanj](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) som skapades, eller en matchning [Regel för programsynkronisering](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md) som skapades, eller [Aktivera slutpunktsvärde för köpare](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) är &quot;Inkludera alla kampanjmedlemmar&quot; eller &quot;Inkludera &#39;responded&#39;-kampanjmedlemmar.&quot;

ii. Ett startdatum måste anges för kampanjen/programmet

iii. Ett slutdatum måste anges i kampanjen/programmet

iv. Faktisk kostnad (för kampanjer i SFDC) eller Periodkostnad (för program i Marketo) måste anges.

**3 Manuell kostnadsöverföring**

Med den här metoden kan du [överföra utgiftsdata manuellt](/help/marketing-spend/spend-management/marketing-channel-costs.md#uploading-marketing-costs) för de kanaler och underkanaler som inte omfattas av API-anslutna konton eller CRM Campaign Cost Sync. Genom att gå till avsnittet Marketing Spend i [!DNL Marketo Measure] -inställningar kan du överföra utgiftsdata via en CSV-fil för alla dina kanaler.

Kunderna kan använda en kombination av alla dessa tre metoder för att hantera sina utgifter, beroende på den specifika konfigurationen av [!DNL Marketo Measure]. Eftersom det finns tre sätt att importera utgifter till [!DNL Marketo Measure]rekommenderar vi starkt att du använder din Marketing Spend Board som finns i Discover för att få en heltäckande bild av alla utgiftsdata. Den här styrelsen är den enda plats där du kan se alla dina kanaler och deras associerade utgifter. Marketing Spend board kan hjälpa er att snabbt identifiera var era utgiftsdata kan vara och hur ni kan förbättra avkastningen på er rapportering.
