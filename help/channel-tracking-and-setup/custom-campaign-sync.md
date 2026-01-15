---
description: Anpassad guide för kampanjsynkronisering för Marketo Measure-användare
title: Synkronisering av anpassad kampanj
exl-id: 66f0e4e3-c1b6-443e-8ffa-06b67862b855
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# Synkronisering av anpassad kampanj {#custom-campaign-sync}

I dag, med det installerade [!DNL Marketo Measure]-paketet, kan du ange vilka kampanjer som ska inkluderas som en giltig kontaktyta. Det finns många hinder för detta som det var tidigare. När [!DNL Marketo Measure]-paketet har installerats i CRM kan det ta tid att godkänna det av ditt säkerhetsteam. Det finns dessutom bristande flexibilitet när det gäller att använda en enda plocklista i Campaign-objektet. Med den här nya funktionen krävs ingen paketinstallation för att börja använda poster för Campaign- och Campaign-medlemmar. Regler kan skapas för att definiera exakt vilka poster som kan skapas för att definiera exakt vilka poster som är kvalificerade.

## Krav {#requirements}

* Kampanjsynkronisering finns i alla nivåer
* Du måste fortfarande ansluta CRM till ditt [!DNL Marketo Measure]-konto för att kunna importera data

## Så här fungerar det {#how-it-works}

1. Med AccountAdmin-behörigheter kan du navigera till **[!UICONTROL Settings]** > **[!UICONTROL Campaigns]** och se regelgränssnittet för synkronisering av kampanjmedlemmar.
1. Klicka på ikonen **+** för att börja skapa en regel.

   ![1. Klicka på ikonen + för att börja skapa en regel.](assets/offline-channels-1.png)

1. Du kan skapa en regel från [!UICONTROL Campaign]- eller [!UICONTROL Campaign Member]-fält. Fyll i resten av regeln med operatorn och värdet som vi förväntas validera. I exemplet nedan söker vi efter en viss kampanj efter namnet.

   ![1. Du kan skapa en regel från Campaign](assets/offline-channels-10.jpg)

   >[!NOTE]
   >
   >Formelfält kan inte användas i reglerna och visas inte i plocklistan. Eftersom formler beräknas i bakgrunden och inte ändrar en post, kan [!DNL Marketo Measure] inte identifiera om en post passar in i en regel eller inte.

1. Välj slutpunktsdatum. Listan med möjliga datum visas när du har angett klammerparentesen `{` - du kan välja vilket datum du vill använda för alla beröringspunkter som skapas från regeln.

   ![1. Välj slutpunktsdatum. Listan över möjliga datum visas](assets/offline-channels-11.png)

   >[!NOTE]
   >
   >Om du använder regler för anpassad kampanjsynkronisering läser [!DNL Marketo Measure] inte några uppdateringar som du har gjort med knappen Kontaktpunktsdatum för gruppuppdatering.

1. Klicka på bockmarkeringen och lägg sedan till ytterligare regler för ytterligare kampanjer efter behov.

   ![1. Klicka på bockmarkeringen och lägg sedan till ytterligare regler för ytterligare kampanjer som ](assets/offline-channels-12.png)

   >[!NOTE]
   >
   >Nu när reglerna definieras tillsammans med CRM-synkroniseringen börjar de angivna reglerna naturligtvis att hamna i konflikt. Om du väljer att fortsätta använda både den anpassade kampanjsynkroniseringen _och_ CRM-synkroniseringstypen är det viktigt att skapa regler så att CRM-synkroniseringstyperna inte ignoreras.

   ![Nu definieras reglerna bredvid CRM-synkroniseringen, reglerna som](assets/offline-channels-13.png)

   >[!NOTE]
   >
   >Om du funderar på att till slut stoppa användaren av [!UICONTROL CRM Sync Type] är det idealiskt att skapa regler som inte refererar till Synkroniseringstyp, men _still_ behåller de aktuella CRM-kontaktytorna. På så sätt fungerar reglerna fortfarande om/när den ändringen görs.

Här är ett exempel på hur det skulle se ut, så att inga befintliga CRM-kontaktytor försvinner:

## Validering {#validation}

Du kan enkelt kontrollera Buyer Touchpoints och Buyer Attribution Touchpoint-poster i Campaign för att se till att reglerna fungerar som de ska. Här är en BAT som [!DNL Marketo Measure] har skapat med rätt datum för dynamisk kontaktpunkt, hämtad från Campaign. Fältet Skapat den finns i bilden nedanför det.

![Du kan enkelt kontrollera Buyer Touchpoints och Buyer Attribution Touchpoint records](assets/offline-channels-14.png)

## Testning {#testing}

1. Funktionen Kampanjsynkronisering innehåller en testfunktion så att du kan kontrollera om reglerna som du har skapat verkligen uppfyller Campaign-villkoren. Börja med att klicka på knappen [!UICONTROL Test]. Reglerna måste sparas innan du kan börja testa.

   ![1. Funktionen för kampanjsynkronisering har en testfunktion så att ](assets/offline-channels-15.jpg)

   Ett popup-fönster visas där du kan ange ett kampanj-ID (15 eller 18 tecken från CRM) att testa. Poängen är att ange det kampanj-ID från CRM som du försökte synkronisera för att se till att det matchar regeln som du skapade.

   ![Ett popup-fönster visas där du kan ange ett kampanj-ID (antingen](assets/offline-channels-16.png)

1. När du har klickat på [!UICONTROL Test] ser du namnet på Campaign och antalet Campaign-medlemmar som är berättigade till kontaktytor. En tabell visas nedan som visar alla regler som matchar ditt kampanj-ID. Endast matchningarna visas.

   ![1. När du har klickat på Testa visas namnet på ](assets/offline-channels-17.png)

1. Du kan också klicka på medlemsantalet för att visa en lista över de leads och kontakter och deras ID:n som ingår i kampanjregelns berättigande. Detta är bara en exempeluppsättning som visas upp till 50 så att du kan få en uppfattning om vilka poster som är kvalificerade.

   ![1. Du kan också klicka på medlemsantalet för att visa en lista ](assets/offline-channels-18.jpg)
