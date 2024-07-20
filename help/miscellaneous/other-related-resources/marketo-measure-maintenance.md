---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] Underhåll - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure]-underhåll"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
feature: Tracking
source-git-commit: fca2db86611d16f4e74467405521a89dd5d825ab
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# [!DNL Marketo Measure]-underhåll {#marketo-measure-maintenance}

[!DNL Marketo Measure] hämtar nästan allt som den behöver från din CRM dagligen, men det finns några underhållsåtgärder som du bör schemalägga regelbundet för att hålla [!DNL Marketo Measure] nedstämd och skicka ut så korrekt information som möjligt.

**Synkronisera kontaktytor för köpare för nya offlinekampanjer (2x/månad)**

Som du lärde dig under introduktionen får [!DNL Marketo Measure] information om era offlinemarknadsföringssatsningar genom att synkronisera med era CRM-kampanjer. När ni lanserar nya kampanjer måste ni se till att aktivera Buyer Touchpoints för varje kampanj efter behov.

**Utgift för överföring för alla kanaler (1x/månad)**

Om du vill utnyttja alla intäkts- och avkastningsrapporteringsfunktioner för [!DNL Marketo Measure] måste du tala om för [!DNL Marketo Measure] hur mycket du spenderar på varje marknadsföringskanal och underkanal. Ange ägaren till varje kanal/underkanal och låt dessa personer rapportera utgifter till en enda part som ansvarar för att överföra ny kostnadsinformation på månadsbasis.

Uppdatera ditt minne om hur du överför kostnadsinformation genom att läsa [den här artikeln](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Uppdatera lista med domäner som ska spåras (1x/månad)**

Marketo Measure spårar alla sidor och underdomäner där Javascript är aktivt, men bara för domäner som vi känner till. Om du nyligen har debiterat en ny domän, expanderat internationellt eller ändrat din primära domän kontaktar du [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} för att försäkra dig om att vi uppdaterar ditt konto därefter.

**Granska anpassad kanalmappning för precision (1x/månad)**

Under introduktionen ställer ni in anpassad kanalmappning för era marknadsföringssatsningar online och offline. Efterhand som er marknadsföringsstrategi och användning av Marketo Measure utvecklas vill ni hålla ett öga på mappningslogiken för att se till att alla era kontaktytor kategoriseras på rätt sätt.

Kom ihåg att [!DNL Marketo Measure] bearbetar dina data igen när du redigerar mappningslogik, så du kan inte ändra dessa regler mer än en gång var sjunde dag.

Referera till [den här artikeln](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) för onlinekonfiguration, [den här artikeln](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) för offlinekonfiguration och den här listan över bästa praxis från våra kunder:

* Granska de kontaktpunkter som för närvarande tillhör någon annan eller NULL-kanal som du har konfigurerat. Om det behövs kan du uppdatera mappningslogiken för att kategorisera dessa kontaktytor i mer korrekta kanaler.
* Granska de kontaktytor som för närvarande faller inom era direktkanaler. Om några av era e-postmarknadsföringskampanjer eller andra satsningar saknar UTM-parametrar, finns det en bra chans att trafik felaktigt paketeras i en direktkanal. Överväg att uppdatera UTM-parametrarna för att hämta den refererande källan.

**Utvärdera inställningar för inaktivering av kontaktpunkter (1x/kvartal)**

Om du ser många kontaktytor som du inte vill ta hänsyn till i din attribueringsartikel (från t.ex. [!DNL Login] eller [!DNL Unsubscribe forms], en karriärsida eller en intern app) kanske du vill utvärdera dina befintliga inställningar för inaktivering av kontaktytor. En gång i kvartalet kan du identifiera grupper av kontaktytor som skapar onödigt brus och uppdatera din undertryckningslogik på lämpligt sätt. [Här är en användbar artikel ](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md) med handledningar.

**Granska anpassad scenmappning för precision (1x/kvartal) (om tillämpligt)**

Om du använder några anpassade [!UICONTROL Lead]-, [!UICONTROL Contact]- eller [!UICONTROL Opportunities]-faser kan du också ha anpassat vilken del av pipelinen som de här faserna ska mappas till och om de ska inkluderas i en anpassad attribueringsmodell. En gång i kvartalet kan du besöka [den här artikeln](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) för att uppdatera minnet på den anpassade scenmappningen och säkerställa att du spårar dina anpassade stadier korrekt.

**Jämför maskininlärningsmodell med anpassad modellvikt (1x/kvartal) (om tillämpligt)**

Om du är licensierad för den anpassade modellen [!DNL Marketo Measure] har du även data tillgängliga från vår Machine Learning Model (MLM) i [!UICONTROL Settings] > [!UICONTROL Attribution Settings]. MLM beräknar vikten av varje fas med hjälp av kontaktpunktsdata från ditt konto och kan hjälpa dig att bestämma hur attribueringsvikten ska fördelas i din anpassade modell. Vi rekommenderar att du jämför MLM med din anpassade modell en gång per kvartal och diskuterar konsekvenserna av eventuella ändringar i din anpassade modell med din SM.

Mer information om [!DNL Marketo Measure] Machine Learning Model finns i [den här artikeln](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
