---
description: Konfigurerar Boomerang-stadier - [!DNL Marketo Measure]
title: Konfigurera Boomerang Stages
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Konfigurera Boomerang Stages {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>Funktionen Boomerang är bara aktiverad för Tier 2- och Tier 3-kunder. Om du vill beställa en högre kontonivå kontaktar du Adobe Account Team (din kontohanterare).

Om du vill aktivera [!UICONTROL Boomerang] steg för ditt konto måste du vara kontoadministratör. Du kan också aktivera den genom att kontakta [Marketo support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. När funktionen är aktiverad följer du dessa anvisningar för att konfigurera dem.

## Inställning av Boomerang-scenen {#boomerang-stage-setup}

1. Gå till [!UICONTROL Stage Mapping]. Markera rutorna intill de stadier du vill spåra i kolumnen [!UICONTROL Boomerang].

   ![Gränssnittet för scenmappning visar en boomerang-kolumn med kryssrutor för scenval](assets/1-2.png)

1. Gå till fliken [!UICONTROL Attribution Settings] och ange antalet kontaktytor för varje fas som du vill se. Vi tillåter högst 10. Standardvärdet är 1.

   ![Fliken Attributinställningar som visar indatafält för antal kontaktytor för varje boomerang-scen](assets/2-2.png)

1. Klicka på **[!UICONTROL Save]**.

   >[!NOTE]
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.

## Konfiguration av Boomerang-scenen med anpassad modellattribuering {#boomerang-stage-setup-with-custom-model-attribution}

1. Gå till [!UICONTROL Stage Mapping]. Markera rutorna intill de stadier du vill spåra i kolumnen [!UICONTROL Boomerang].

   ![Gränssnitt för scenmappning med Boomerang- och Custom Model Model-kolumner för scenval](assets/3-1.png)

1. Om du även vill att dessa Boomerang-stadier ska ingå i din anpassade modell och få attribueringskrediter måste du även markera rutan under kolumnen [!UICONTROL Custom Model].

   ![Stage Mapping visar kryssrutor för anpassade modellkolumner som har markerats för sammansatta stadier](assets/4-1.png)

1. Gå till fliken [!UICONTROL Attribution Settings]. Bestäm hur du vill att attribueringen för dina panoreringsfaser ska viktas. Alternativen är att väga attribueringen mot den första förekomsten, den sista förekomsten, eller att låta den delas jämnt över alla förekomster.

   ![Attributinställningar som visar boomerangs viktningsalternativ för första, sista eller till och med dela](assets/5-1.png)

1. Ange antalet förekomster av varje scen som du vill se. Vi kan tillåta maximalt 10. Standardvärdet är 1.

   ![Attributinställningar som visar indatafält för förekomstantal för varje boomerang-scen](assets/6-1.png)

1. Ange den attribueringsprocent som du vill tilldela de Boomerang-scener som du har inkluderat i den anpassade modellen. Se till att den totala attribueringen för alla faser uppgår till 100 %. Klicka på **[!UICONTROL Save and Process]**.

   ![Attributinställningar som visar procentallokeringsfält för boomerang-stadier i anpassad modell](assets/7-1.png)

   >[!NOTE]
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.
