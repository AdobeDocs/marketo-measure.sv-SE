---
description: Vägledning om omauktorisering av anslutna konton för Marketo Measure-användare
title: Återauktoriserar anslutna konton
exl-id: 7abd1d67-5bed-45bb-844f-0ffd23c3d7f8
feature: APIs, Integration
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Återauktoriserar anslutna konton {#reauthorizing-connected-accounts}

När ett konto kopplas bort från ditt [!DNL Marketo Measure]-konto ändras plattformens status till Autentisering krävs och en röd nyckelikon visas.

Om annonsplattformen kopplas från kan [!DNL Marketo Measure] inte hämta kostnadsdata eller, om du har autotagging aktiverat, lägga till [!DNL Marketo Measure] UTM-parametrarna till nya annonser. [!DNL Marketo Measure] kan inte lägga till UTM-parametrar retroaktivt till kontaktytor som skapats från annonsplattformen när kontot kopplades från.

Om din CRM-plattform kopplas från kan [!DNL Marketo Measure] inte uppdatera [!DNL Marketo Measure]-data eller överföra nya kontaktytor till din organisation. När CRM-anslutningen har återupprättats skickar [!DNL Marketo Measure] alla data som missats när kontot kopplades från.

![Om din CRM-plattform kopplas från blir Marketo Measure inte](assets/utilizing-connections-7.png)

## Återauktoriserar frånkopplade konton {#re-authorizing-disconnected-accounts}

1. Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} och logga in.
1. Välj **[!UICONTROL Settings]** under fliken [!UICONTROL My Account] i det övre vänstra hörnet.
1. Gå till avsnittet Integrationer till vänster och klicka på **[!UICONTROL Connections]**.
1. Markera den röda nyckelsymbolen bredvid det konto som ska återanslutas.
1. Ett popup-fönster visas där du uppmanas att ange inloggningsinformation för kontot.
