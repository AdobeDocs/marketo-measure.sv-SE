---
description: A/B-testkonfiguration och rapportvägledning för Marketo Measure-användare
title: A/B-testkonfiguration och -rapportering
exl-id: 9a3f0731-5909-4fbf-a35a-9608ff561061
feature: A/B Testing
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# A/B-testkonfiguration och -rapportering {#a-b-testing-set-up-and-reporting}

Med A/B-testintegrationen i [!DNL Marketo Measure] kan du spåra intäktseffekten av dina [Optimalt](https://www.optimizely.com/){target="_blank"} - och VWO-webbplatsexperiment. Den här artikeln innehåller anvisningar om hur du lägger till [!DNL Marketo Measure] A/B-testavsnitt i sidlayouterna Lead, [!UICONTROL Contact], Case och [!UICONTROL Opportunity]. Här beskrivs även allmän rapporthantering och rekommendationer för att köra [!DNL Marketo Measure] A/B-rapporttyper.

## Konfigurera {#set-up}

Lägg till A/B-testavsnitten [!DNL Marketo Measure] på Lead, Contact, Case och Opportunity. Med [!DNL Marketo Measure] A/B-testintegration kan du spåra intäktseffekten av dina [optimalt](https://www.optimizely.com/){target="_blank"} - och [VWO](https://vwo.com/){target="_blank"} -webbplatsexperiment.

1. Kontrollera att du använder paketet [!DNL Marketo Measure] v3.9 eller senare. Du kan göra detta genom att gå till [!UICONTROL Salesforce] >[!UICONTROL Set Up] > [!UICONTROL Installed packages].
1. Redigera sidlayouten för lead och lägg till den **[!DNL Marketo Measure]A/B-testlistan** till sidan.

   ![1. Redigera sidlayouten Lead och lägg till Marketo Measure](assets/advanced-features-2.png)

1. Klicka på knappen [!UICONTROL Wrench]. Ta bort fältet &quot;ID&quot; från listan med valda fält. Lägg till **[!UICONTROL Experiment]**-, **[!UICONTROL Variation]**- och **[!UICONTROL DateReported]**-fält. Ändra [!UICONTROL Sort by] till **[!UICONTROL Date Reported]** och välj **[!UICONTROL Descending]** i listrutan.

   ![1. Klicka på knappen skiftnyckel. Ta bort fältet &quot;ID&quot; från](assets/advanced-features-3.png)

1. Avmarkera [!UICONTROL Buttons] under **[!UICONTROL New]**.

   ![1. Avmarkera Ny under Knappar.](assets/advanced-features-7.png)

1. Kontakta din [!DNL Marketo Measure]-representant eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} om du vill aktivera funktionen.

## Rapportering {#reporting}

Kunder har tillgång till ett par [!DNL Marketo Measure] A/B-rapporttyper som gör att du kan rapportera A/B-tester i relation till leads, kontakter och säljprojekt:

* [!DNL Marketo Measure] A/BTests
* [!DNL Marketo Measure] A/BTest med kontakt
* [!DNL Marketo Measure] A/BTests med Lead
* [!DNL Marketo Measure] A/BTets med möjlighet

![Marketo Measure A/BTets with Opportunity](assets/advanced-features-8.png)

A/B-rapporttyper används för att rapportera om vilken lead, kontakt eller säljprojekt som har exponerats för ett A/B-test. De här rapporterna visar också de intäkter som är knutna till ett säljprojekt som exponerats för ett A/B-test.

Det är viktigt att komma ihåg att Optimizely/VWO är en plattform för innehållsvariationer och inte en marknadsföringskanal. Därför används dessa [!DNL Marketo Measure] A/B-rapporttyper på ett annat sätt än Buyer Touchpoint-rapporter. Rapporttyper för inköpskontaktytor används för att förstå vilken marknadsföringskanal (betalannonsering, webbdirektreklam, sociala medier) som körde en lead eller kontakt till en viss sida. [!DNL Marketo Measure] A/B-rapporttyper kan dock inte användas för att rapportera hur en variation påverkade en lead eller möjlighet. Eftersom en A/B-testvariant inte är en kanal visas inte information om variationen på köparens kontaktyta.

Här följer några rekommenderade fält som ska användas vid rapportering av A/B-tester för att öka klarheten och insikt:

* Lead konverterad
* Experimentera
* Experiment-ID
* Variation
* Variations-ID
* Rapportdatum

## [!DNL Salesforce] exempelrapporter {#salesforce-example-reports}

**[!DNL Marketo Measure]A/B-test med lead**

![Marketo Measure A/B-test med lead](assets/advanced-features-9.png)

**[!DNL Marketo Measure]A/B-test med säljprojekt**

![Marketo Measure A/B-test med möjlighet](assets/advanced-features-10.png)
