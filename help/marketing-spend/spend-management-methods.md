---
description: Metoder för utgiftshantering - [!DNL Marketo Measure]
title: Metoder för utgiftshantering
exl-id: 36478d8d-986c-4d4f-8854-3287d6c57a9d
feature: Spend Management
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---


# Metoder för utgiftshantering {#spend-management-methods}

Utgiftsdata är avgörande för att ROI-rapportering med [!DNL Marketo Measure] ska lyckas. För att få en korrekt och heltäckande rapportering om avkastning på investerat kapital i alla kanaler och underkanaler måste du se till att rätt utgiftsdata hämtas till [!DNL Marketo Measure].

Det finns tre sätt att hämta utgiftsdata till [!DNL Marketo Measure]. Varje metod är utformad för att hämta utgiftsdata från vissa dataindata.

**1 API-anslutna konton**

Alla annonskonton som du har anslutit till [!DNL Marketo Measure] via ett API får sina utgifter automatiskt i [!DNL Marketo Measure] för ROI-rapportering. Om du vill kontrollera vilka konton du har anslutit och därmed ta in utgifter går du till din [!DNL Marketo Measure]-app och väljer fliken [!UICONTROL Connections] under avsnittet [!UICONTROL Integrations]. Mer information om hur du konfigurerar dina API-anslutningar finns i [Integrerade annonsplattformar](/help/api-connections/integrated-ad-platforms.md#how-to-connect-ad-platforms).

**2 CRM Kampanjkostnadssynkronisering**

Alla [!DNL Marketo Measure]-konton har åtkomst till en funktion som kallas [Synkronisera CRM-kampanjkostnader](/help/marketing-spend/crm-campaign-costs.md#availability). Som standard är den här funktionsbiten inställd på Nej, men den kan aktiveras när som helst.

![Sidan Anslutningsinställningar visar växlingsknappen för CRM-kampanjens kostnadssynkronisering](assets/spend-management-methods-1.png)

När den här funktionen är aktiverad hämtas utgifter automatiskt in från alla CRM-kampanjer/program som uppfyller följande kriterier:

i. [!DNL Marketo Measure] kontrollerar först om kampanjen/programmet skapar kontaktytor, antingen från en matchande [kampanjsynkroniseringsregel](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md) som skapades, eller från en matchande [programsynkroniseringsregel](/help/marketo-measure-and-marketo/marketo-engage-programs-integration.md) som skapades, eller om [Aktivera slutpunktsvärdet för köpare](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md#how-to-create-a-campaign-and-sync-buyer-touchpoints) är Inkludera alla kampanjmedlemmar eller Inkludera responderade kampanjmedlemmar.

ii. Ett startdatum måste anges för kampanjen/programmet

iii. Ett slutdatum måste anges i kampanjen/programmet

iv. Faktisk kostnad (för kampanjer i SFDC) eller Periodkostnad (för program i Marketo) måste anges.

**3 Manuell kostnadsöverföring**

Med den här metoden kan du [manuellt överföra utgiftsdata](/help/marketing-spend/marketing-channel-costs.md#uploading-marketing-costs) för de kanaler och underkanaler som inte omfattas av API-anslutna konton eller CRM Campaign-kostnadssynk. Genom att gå till avsnittet Marketing Spend i inställningarna för [!DNL Marketo Measure] kan du överföra utgiftsdata via en CSV-fil för alla dina kanaler.

Kunder kan använda en kombination av alla dessa tre metoder för att hantera sina utgifter, beroende på den specifika konfigurationen för [!DNL Marketo Measure]. Eftersom det finns tre sätt att importera utgifter till [!DNL Marketo Measure] rekommenderar vi starkt att du använder din Marketing Spend board som finns i Discover för att få en heltäckande bild av alla utgiftsdata. Den här styrelsen är den enda plats där du kan se alla dina kanaler och deras associerade utgifter. Marketing Spend board kan hjälpa er att snabbt identifiera var era utgiftsdata kan vara och hur ni kan förbättra avkastningen på er rapportering.
