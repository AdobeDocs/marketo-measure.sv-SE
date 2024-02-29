---
unique-page-id: 18874600
description: Synkroniserar offlinekampanjer - [!DNL Marketo Measure]
title: Synkronisera offlinekampanjer
exl-id: a6f9e217-ff6e-474d-9f14-c6f6238c9e84
feature: Channels
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# Synkronisera offlinekampanjer {#syncing-offline-campaigns}

Det kan vara svårt att spåra offlinekampanjer korrekt och förstå hur de står sig jämfört med era digitala marknadsföringssatsningar. [!DNL Marketo Measure] gör det möjligt att spåra och tilldela kontaktytor till offlinekampanjer i [!DNL Salesforce], även i situationer när en [!DNL Salesforce] kampanjen skapas inte förrän några veckor efter händelsen.

>[!NOTE]
>
>Den här artikeln handlar om en föråldrad process. Vi uppmuntrar användarna att använda [ny, förbättrad process i appen](/help/channel-tracking-and-setup/offline-channels/custom-campaign-sync.md){target="_blank"}.

## Innan du synkroniserar {#before-you-sync}

Här följer några tips om en effektiv synkroniseringsprocess:

* Offlinekampanjer avser marknadsföringsinteraktioner som inte sker online. Dessa omfattar marknadsföringskanaler som event, webbinarier och mässor. Inkludera endast offline-marknadsföringskampanjer.
* Om du vill inkludera kampanjer som spårade onlineaktiviteter innan du installerade [!DNL Marketo Measure]ska du ange slutdatumet för slutpunkten som det datum då JavaScript distribuerades på din webbplats.
* Det är praktiskt att behålla [!DNL Marketo Measure] appen öppnas på sidan Offlinekanaler så att det är enkelt att identifiera de olika kampanjtyperna, tillsammans med vilken marknadsföringskanal som kontaktytorna ska paketeras i.

* Kontrollera allt innan du trycker på[!UICONTROL Save]&quot;!

## Uppdatera Touchpoint-datum gruppvis {#bulk-update-touchpoint-date}

I [!DNL Salesforce]anger fältet Skapat den i Campaign-medlemsobjektet det datum då kampanjmedlemmen lades till i kampanjen. För att synkroniseringsprocessen ska gå smidigt måste datumfältet för köparens slutpunkt ha samma datum som datumet på Salesforce Campaign-medlemsobjektet. Det här steget utförs med hjälp av[!UICONTROL Bulk Update Touchpoint Date button],&quot; _före_ du väljer [!UICONTROL picklist] i fältet Enable Buyer Touchpoints.

Varför är detta viktigt? Tänk dig att ert företag sponsrade en monter på en konferens i januari. På konferensen visade 100 personer intresse för din produkt och tillhandahöll sin kontaktinformation för att få uppdateringar via e-post. Tre veckor senare skapade ni äntligen en kampanj på [!DNL Salesforce] för att följa upp resultatet av konferensen.

Ditt överföringsdatum skulle vara tre veckor senare än konferensdatumet. För att åtgärda den här skillnaden [!UICONTROL Bulk Update Touchpoint Date] kan användas för att ställa in rätt datum. Knappen visas i bilden nedan.

![](assets/1-3.png)

I det här fallet fyller den upp-datumet med tre veckor. Det här steget bör utföras innan du ställer in &quot;[!UICONTROL Enable Buyer Touchpoints]&quot;.

Sammanfattningsvis, om du använder [!UICONTROL Bulk Update Touchpoint Date] och ändra slutpunktsdatumet till datumet för händelsen, [!DNL Marketo Measure] genererar kontaktpunkter för det faktiska datumet för händelsen, inte datumet för överföringen.

Du kan också uppdatera datumen för alla kampanjmedlemmar i en befintlig kampanj. När du gör det ska du kontrollera att datumet för kontaktpunkten är datumet för medlemmens interaktion. Klicka bara på Buyer Touchpoint Date för gruppuppdatering, filtrera listan över kampanjmedlemmar efter behov och i &quot;[!UICONTROL Select Date]&quot; ovanför listan med kampanjmedlemmar lägger du till samma datum som det datum då händelsen ägde rum.

>[!CAUTION]
>
>Kontrollera att du har uppdaterat slutpunktsdatumet _före_ du aktiverar kontaktpunkter för alla kampanjmedlemmar.

![](assets/2-3.png)

## Så här skapar du en Campaign och synkroniserar kontaktytor för köpare {#how-to-create-a-campaign-and-sync-buyer-touchpoints}

Skapa en kampanj i [!DNL Salesforce], navigera till [!UICONTROL Campaigns] och välj &#39;[!UICONTROL New]&#39; som visas i bilden nedan. Beroende på din [!DNL Salesforce] kan du behöva lägga till kampanjer i det övre fältet genom att klicka på plusikonen (+).

![](assets/3-3.png)

När du skapar kampanjen klickar du på[!UICONTROL Enable Buyer Touchpoints]&quot; och välj något av följande alternativ i listrutan:

![](assets/4-3.png)

* **Inkludera alla kampanjmedlemmar**
   * Det här alternativet aktiverar [!DNL Marketo Measure] för att tilldela varje kampanjmedlem en kontaktpunkt.

* **Inkludera kampanjmedlemmar som svarar.**
   * Med det här alternativet används kontaktytor för kampanjmedlemmar som har statusen&quot;Responded&quot; (Svarat).

* **Uteslut alla kampanjmedlemmar.**
   * Det här alternativet tilldelar inte Touchpoints till några medlemmar i kampanjen och fungerar som en flagga för att kampanjen avsiktligt har uteslutits från [!DNL Marketo Measure]. Om du någon gång synkroniserar en kampanj med Buyer Touchpoints vid en olycka kan du ändra statusen till&quot;Uteslut alla kampanjmedlemmar&quot;, så tas Touchpoints bort.

När en av dessa markeringar har valts, [!DNL Marketo Measure] tilldelar varje kampanjmedlem en kontaktpunkt, om tillämpligt. Lead eller kontakt som lagts till i kampanjen _måste_ har en e-postadress som är kopplad till posten för att [!DNL Marketo Measure] för att skapa en kontaktyta. Utan e-postadress [!DNL Marketo Measure] tilldelar inte någon kontaktyta till kampanjmedlemmen.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Universitet: Mappa offlinekanaler](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>[[!DNL Marketo Measure] Universitet: fält för kampanjobjekt](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63007334d9f0367662b758)
