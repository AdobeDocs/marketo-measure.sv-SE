---
unique-page-id: 18874767
description: Konfigurera Boomerang-stadier - [!DNL Marketo Measure]
title: Konfigurera Boomerang Stages
exl-id: 00dd2826-27a3-462e-a70e-4cec90d07f92
feature: Boomerang
source-git-commit: ea113b02b910fbc894311200aff83286636d4b32
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Konfigurera Boomerang Stages {#setting-up-boomerang-stages}

>[!AVAILABILITY]
>
>Funktionen Boomerang är bara aktiverad för Tier 2- och Tier 3-kunder. Om du vill begära en högre kontonivå kontaktar du kontoteamet (din kontohanterare) på Adobe.

Aktivera [!UICONTROL Boomerang] Du måste vara kontoadministratör för ditt konto. Eller så kan det aktiveras genom att man når ut till [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}. När funktionen är aktiverad följer du dessa anvisningar för att konfigurera dem.

## Inställning av Boomerang-scenen {#boomerang-stage-setup}

1. Gå till [!UICONTROL Stage Mapping]. Under kolumnen med rubriken &quot;[!UICONTROL Boomerang],&quot; markerar du rutorna intill de stadier du vill spåra.

   ![](assets/1-2.png)

1. Gå till [!UICONTROL Attribution Settings] och ange antalet kontaktytor för varje scen som du vill se. Vi tillåter högst 10. Standardvärdet är 1.

   ![](assets/2-2.png)

1. Klicka på **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.

## Konfiguration av Boomerang-scenen med anpassad modellattribuering {#boomerang-stage-setup-with-custom-model-attribution}

1. Gå till [!UICONTROL Stage Mapping]. Under kolumnen med rubriken &quot;[!UICONTROL Boomerang],&quot; markerar du rutorna intill de stadier du vill spåra.

   ![](assets/3-1.png)

1. Om du även vill att de här Boomerang-faserna ska ingå i din anpassade modell och få attribueringskrediter måste du också markera rutan under &quot;[!UICONTROL Custom Model]&quot;.

   ![](assets/4-1.png)

1. Gå till [!UICONTROL Attribution Settings] -fliken. Bestäm hur du vill att attribueringen för dina panoreringsfaser ska viktas. Alternativen är att väga attribueringen mot den första förekomsten, den sista förekomsten, eller att låta den delas jämnt över alla förekomster.

   ![](assets/5-1.png)

1. Ange antalet förekomster av varje scen som du vill se. Vi kan tillåta maximalt 10. Standardvärdet är 1.

   ![](assets/6-1.png)

1. Ange den attribueringsprocent som du vill tilldela de Boomerang-scener som du har inkluderat i den anpassade modellen. Se till att den totala attribueringen för alla faser uppgår till 100 %. Klicka på **[!UICONTROL Save and Process]**.

   ![](assets/7-1.png)

   >[!NOTE]
   >
   >Det kan ta 24-48 timmar för dina data att bearbetas om enligt dessa ändringar.
