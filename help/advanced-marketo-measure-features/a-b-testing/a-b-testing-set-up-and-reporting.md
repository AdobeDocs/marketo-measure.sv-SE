---
unique-page-id: 18874773
description: A/B-testkonfiguration och -rapportering - [!DNL Marketo Measure]
title: A/B-testkonfiguration och -rapportering
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
feature: A/B Testing
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# A/B-testkonfiguration och -rapportering {#a-b-testing-set-up-and-reporting}

The [!DNL Marketo Measure] Tack vare A/B Test-integreringen kan du spåra intäktseffekten i dina [Optimalt](https://www.optimizely.com/){target="_blank"} och VWO-webbplatsexperiment. I den här artikeln finns anvisningar om hur du lägger till [!DNL Marketo Measure] A/B Test sections to the Lead, [!UICONTROL Contact], skiftläge och [!UICONTROL Opportunity] sidlayouter. Här beskrivs även allmän rapporthantering och rekommendationer för att köra [!DNL Marketo Measure] A/B-rapporttyper.

## Konfigurera {#set-up}

Lägg till [!DNL Marketo Measure] A/B-testsektioner om lead, kontakt, ärende och säljprojekt. [!DNL Marketo Measure] Tack vare A/B Test-integreringen kan du spåra intäktseffekten i dina [Optimalt](https://www.optimizely.com/){target="_blank"} and [VWO](https://vwo.com/){target="_blank"} webbplatsexperiment.

1. Kontrollera att du använder paketet [!DNL Marketo Measure] v3.9 eller senare. Du kan göra detta genom att gå vidare [!UICONTROL Salesforce] >[!UICONTROL Set Up] > [!UICONTROL Installed packages].
1. Redigera sidlayouten Lead och lägg till **[!DNL Marketo Measure]A/B-tester** Relaterad lista till sidan.

   ![](assets/1.png)

1. Klicka på [!UICONTROL Wrench] -knappen. Ta bort fältet &quot;ID&quot; från listan med valda fält. Lägg till **[!UICONTROL Experiment]**, **[!UICONTROL Variation]** och **[!UICONTROL DateReported]** fält. Ändra &quot;[!UICONTROL Sort by]&quot; till **[!UICONTROL Date Reported]** och markera **[!UICONTROL Descending]** i listrutan.

   ![](assets/2.png)

1. Under [!UICONTROL Buttons], avmarkera **[!UICONTROL New]**.

   ![](assets/3.png)

1. Kontakta [!DNL Marketo Measure] rep [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} för att aktivera funktionen.

## Rapportering {#reporting}

Kunderna har tillgång till ett par [!DNL Marketo Measure] Rapporttyper för A/B som gör att du kan rapportera om A/B-tester i relation till leads, kontakter och säljprojekt:

* [!DNL Marketo Measure] A/BTests
* [!DNL Marketo Measure] A/BTest med kontakt
* [!DNL Marketo Measure] A/BTest med lead
* [!DNL Marketo Measure] A/BTest med möjlighet

![](assets/4.png)

A/B-rapporttyper används för att rapportera om vilken lead, kontakt eller säljprojekt som har exponerats för ett A/B-test. De här rapporterna visar också de intäkter som är knutna till ett säljprojekt som exponerats för ett A/B-test.

Det är viktigt att komma ihåg att Optimizely/VWO är en plattform för innehållsvariationer och inte en marknadsföringskanal. Därför bör dessa [!DNL Marketo Measure] A/B-rapporttyper används på ett annat sätt än Buyer Touchpoint-rapporter. Rapporttyper för inköpskontaktytor används för att förstå vilken marknadsföringskanal (betalannonsering, webbdirektreklam, sociala medier) som körde en lead eller kontakt till en viss sida. Men [!DNL Marketo Measure] A/B-rapporttyper kan inte användas för att rapportera om hur en variation påverkar en lead eller möjlighet. Eftersom en A/B-testvariant inte är en kanal visas inte information om variationen på köparens kontaktyta.

Här följer några rekommenderade fält som ska användas vid rapportering av A/B-tester för att öka klarheten och insikt:

* Lead konverterad
* Experimentera
* Experiment-ID
* Variation
* Variations-ID
* Rapportdatum

## [!DNL Salesforce] Exempelrapporter {#salesforce-example-reports}

**[!DNL Marketo Measure]A/B-test med lead**

![](assets/5.png)

**[!DNL Marketo Measure]A/B-test med möjlighet**

![](assets/6.png)
