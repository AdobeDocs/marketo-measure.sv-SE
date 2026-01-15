---
description: Konfigurera Boomerang Stages-vägledning för Marketo Measure-användare
title: Konfigurera Boomerang Stages
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# Konfigurera Boomerang Stages {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>
>Funktionen Boomerang är bara aktiverad för Tier 2- och Tier 3-kunder. Om du vill beställa en högre kontonivå kontaktar du Adobe Account Team (din kontohanterare).

Om du vill aktivera [!UICONTROL Boomerang] steg för ditt konto måste du vara kontoadministratör. Du kan också aktivera den genom att kontakta [Marketo support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. När funktionen är aktiverad följer du dessa anvisningar för att konfigurera dem.

## Inställning av Boomerang-scenen {#boomerang-stage-setup}

1. Gå till [!UICONTROL Stage Mapping]. Markera rutorna intill de stadier du vill spåra i kolumnen [!UICONTROL Boomerang].

   ![1. Gå till Stage Mapping. Under kolumnen med namnet&quot;Boomerang&quot;,](assets/boomerang-stages-18.png)

1. Gå till fliken [!UICONTROL Attribution Settings] och ange antalet kontaktytor för varje fas som du vill se. Vi tillåter högst 10. Standardvärdet är 1.

   ![1. Gå till fliken Attribution Settings och ange talet ](assets/boomerang-stages-19.png)

1. Klicka på **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.

## Konfiguration av Boomerang-scenen med anpassad modellattribuering {#boomerang-stage-setup-with-custom-model-attribution}

1. Gå till [!UICONTROL Stage Mapping]. Markera rutorna intill de stadier du vill spåra i kolumnen [!UICONTROL Boomerang].

   ![1. Gå till Stage Mapping. Under kolumnen med namnet&quot;Boomerang&quot;,](assets/boomerang-stages-20.png)

1. Om du även vill att dessa Boomerang-stadier ska ingå i din anpassade modell och få attribueringskrediter måste du även markera rutan under kolumnen [!UICONTROL Custom Model].

   ![1. Om du även vill att de här Boomerang-faserna ska inkluderas](assets/boomerang-stages-21.png)

1. Gå till fliken [!UICONTROL Attribution Settings]. Bestäm hur du vill att attribueringen för dina panoreringsfaser ska viktas. Alternativen är att väga attribueringen mot den första förekomsten, den sista förekomsten, eller att låta den delas jämnt över alla förekomster.

   ![1. Gå till fliken Attributinställningar. Bestäm hur du vill ](assets/boomerang-stages-22.png)

1. Ange antalet förekomster av varje scen som du vill se. Vi kan tillåta maximalt 10. Standardvärdet är 1.

   ![1. Ange antalet förekomster av varje fas som du vill ha ](assets/boomerang-stages-23.png)

1. Ange den attribueringsprocent som du vill tilldela de Boomerang-scener som du har inkluderat i den anpassade modellen. Se till att den totala attribueringen för alla faser uppgår till 100 %. Klicka på **[!UICONTROL Save and Process]**.

   ![1. Ange den attribueringsprocent som du vill tilldela ](assets/boomerang-stages-24.png)

   >[!NOTE]
   >
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.
