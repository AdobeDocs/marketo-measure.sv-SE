---
description: Synkronisera offlinekampanjer för Marketo Measure-användare
title: Synkronisera offlinekampanjer
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Synkronisera offlinekampanjer {#syncing-offline-campaigns}

Det kan vara svårt att spåra offlinekampanjer korrekt och förstå hur de står sig jämfört med era digitala marknadsföringssatsningar. Med [!DNL Marketo Measure] kan du spåra och tilldela kontaktytor till offlinekampanjer i [!DNL Salesforce], även i situationer när en [!DNL Salesforce]-kampanj inte skapas förrän några veckor efter händelsen.

>[!NOTE]
>
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användare att använda den [nya, förbättrade processen i appen](/help/channel-tracking-and-setup/custom-campaign-sync.md){target="_blank"}.

## Innan du synkroniserar {#before-you-sync}

Här följer några tips om en effektiv synkroniseringsprocess:

* Offlinekampanjer avser marknadsföringsinteraktioner som inte sker online. Dessa omfattar marknadsföringskanaler som event, webbinarier och mässor. Inkludera endast offline-marknadsföringskampanjer.
* Om du vill inkludera kampanjer som spårade onlineaktiviteter innan du installerade [!DNL Marketo Measure] måste du ange slutdatumet för slutpunkten som det datum då JavaScript distribuerades på din webbplats.
* Det är praktiskt att ha appen [!DNL Marketo Measure] öppen på sidan Offlinekanaler så att det är enkelt att identifiera de olika kampanjtyperna, tillsammans med vilken marknadsföringskanal som kontaktytorna ska paketeras i.

* Dubbelkontrollera allt innan du trycker på knappen [!UICONTROL Save]!

## Uppdatera Touchpoint-datum gruppvis {#bulk-update-touchpoint-date}

I [!DNL Salesforce] anger fältet Skapat den i Campaign-medlemsobjektet det datum då kampanjmedlemmen lades till i kampanjen. För att synkroniseringsprocessen ska gå smidigt måste Buyer Touchpoint Date Field ha samma datum som Salesforce Campaign-medlemsobjektet. Det här steget utförs med alternativet [!UICONTROL Bulk Update Touchpoint Date button], _före_, i fältet Aktivera slutpunkter för köpare. [!UICONTROL picklist]

Varför är detta viktigt? Tänk dig att ert företag sponsrade en monter på en konferens i januari. På konferensen visade 100 personer intresse för din produkt och tillhandahöll sin kontaktinformation för att få uppdateringar via e-post. Tre veckor senare skapade du äntligen en kampanj i [!DNL Salesforce] för att spåra resultatet av konferensen.

Ditt överföringsdatum skulle vara tre veckor senare än konferensdatumet. Om du vill åtgärda den här skillnaden kan du använda knappen [!UICONTROL Bulk Update Touchpoint Date] för att ange rätt datum. Knappen visas i bilden nedan.

![Överföringsdatumet är tre veckor senare än konferensdatumet.](assets/dynamics-lists-1.png)

I det här fallet fyller den upp-datumet med tre veckor. Det här steget bör utföras innan du ställer in fältet [!UICONTROL Enable Buyer Touchpoints].

Sammanfattningsvis, om du använder knappen [!UICONTROL Bulk Update Touchpoint Date] och ändrar slutpunktsdatumet till datumet för händelsen, genererar [!DNL Marketo Measure] slutpunkter för det faktiska datumet för händelsen, inte datumet för överföringen.

Du kan också uppdatera datumen för alla kampanjmedlemmar i en befintlig kampanj. När du gör det ska du kontrollera att datumet för kontaktpunkten är datumet för medlemmens interaktion. Klicka på Uppdatera Buyer Touchpoint-datum gruppvis, filtrera listan med kampanjmedlemmar efter behov och lägg till samma datum som händelsen ägde rum i alternativet [!UICONTROL Select Date] ovanför listan med kampanjmedlemmar.

>[!CAUTION]
>
>Se till att du uppdaterar slutpunktsdatumet _före_ när du aktiverar slutpunkter för alla kampanjmedlemmar.

![Uppdatera slutpunktsdatumet innan du aktiverar slutpunkter för &#x200B;](assets/dynamics-lists-10.png)

## Så här skapar du en Campaign och synkroniserar kontaktytor för köpare {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Om du vill skapa en kampanj i [!DNL Salesforce] går du till fliken [!UICONTROL Campaigns] och väljer [!UICONTROL New] enligt bilden nedan. Beroende på hur [!DNL Salesforce] är konfigurerat kan du behöva lägga till kampanjer i det övre fältet genom att klicka på plusikonen (+).

![Navigera till Campaigns](assets/dynamics-lists-2.png) om du vill skapa en kampanj i Salesforce.

När du skapar den här kampanjen klickar du på fältet [!UICONTROL Enable Buyer Touchpoints] och väljer något av följande alternativ i listan:

![När du skapar den här kampanjen klickar du på&quot;Enable Buyer Touchpoints&quot; &#x200B;](assets/dynamics-lists-3.png)

* **Inkludera alla kampanjmedlemmar**
   * Det här alternativet gör att [!DNL Marketo Measure] kan tilldela en kontaktyta till varje kampanjmedlem.

* **Inkludera kampanjmedlemmar som har svarat.**
   * Med det här alternativet används kontaktytor för kampanjmedlemmar som har statusen&quot;Responded&quot; (Svarat).

* **Uteslut alla kampanjmedlemmar.**
   * Det här alternativet tilldelar inte Touchpoints till några medlemmar i kampanjen och fungerar som en flagga för att kampanjen avsiktligt har undantagits från [!DNL Marketo Measure]. Om du någon gång synkroniserar en kampanj med Buyer Touchpoints vid en olycka kan du ändra statusen till&quot;Uteslut alla kampanjmedlemmar&quot;, så tas Touchpoints bort.

När ett av dessa val har valts kommer [!DNL Marketo Measure] att tilldela varje kampanjmedlem en kontaktpunkt om tillämpligt. Lead eller kontakt som läggs till i kampanjen _måste_ ha en e-postadress kopplad till sin post för att [!DNL Marketo Measure] ska kunna skapa en kontaktyta. Utan en e-postadress kommer [!DNL Marketo Measure] inte att tilldela kampanjmedlemmen någon kontaktyta.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Självstudiekurser: Mappa offlinekanaler](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
>
>[[!DNL Marketo Measure] Självstudiekurser: Kampanjobjektfält](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/campaign-object-fields){target="_blank"}
