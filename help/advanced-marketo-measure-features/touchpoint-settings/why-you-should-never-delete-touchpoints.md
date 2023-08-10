---
unique-page-id: 18874560
description: Därför ska du aldrig ta bort kontaktpunkter - [!DNL Marketo Measure] - Produktdokumentation
title: Varför ska du aldrig ta bort kontaktpunkter?
exl-id: e74c14ff-0399-4ee9-b732-6686823ff5c7
feature: Touchpoints
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Varför ska du aldrig ta bort kontaktpunkter? {#why-you-should-never-delete-touchpoints}

Om du upptäcker att det finns en kontaktyta om ett säljprojekt som tilldelas attribueringskrediter felaktigt ber vi dig kontakta din Account Manager för att få reda på vad som kommer att hända. I dessa situationer rekommenderar vi att du använder funktionen för inaktivering av kontaktpunkter för att ta bort kontaktytan från SFDC och kontrollpanelen för avkastning. Kontohanteraren kan hjälpa dig att skapa dessa regler. Ta inte bort dessa kontaktytor manuellt.

The [!DNL Marketo Measure] bearbetningssystemet registrerar inte att en kontaktyta har tagits bort manuellt från SFDC. Från och med idag finns det ingen utlösare som signalerar till vårt system att justera data. [!DNL Marketo Measure] flyttar inte automatiskt ytterligare en kontaktyta för att ersätta den som togs bort och tilldelar inte heller touchpoint-positionen eller attribueringen till efterföljande kontaktyta.

När en kontaktyta tas bort skapas ett hål i attribueringsinformationen. Vanligtvis visas detta i attribueringens kontaktytor för ett säljprojekt. I bilden nedan hade kontaktytan som skulle ha fått frågan om att skapa säljprojekt tagits bort. Därför saknas OC-kontaktytan och attribueringsprocenten för Opp kommer inte att öka till 100 %.

![](assets/1.png)

Om kontaktytor har tagits bort från din SFDC kan du kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} för att begära en återimport av dina data.
