---
unique-page-id: 18874556
description: "[!DNL Marketo Measure] Underhåll - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Underhåll"
exl-id: 4e1d53bb-0af8-4774-9f69-6a95516b3d11
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# [!DNL Marketo Measure] Underhåll {#marketo-measure-maintenance}

[!DNL Marketo Measure] hämtar så gott som allt det behöver från din CRM dagligen, men det finns några underhållsåtgärder som du regelbundet vill schemalägga för att behålla [!DNL Marketo Measure] ge mer exakt information.

**Synkronisera kontaktytor för köpare för nya offlinekampanjer (2x/månad)**

Som du lärde dig under introduktionen, [!DNL Marketo Measure] får information om era offlinemarknadsföringssatsningar genom att synkronisera med era CRM-kampanjer. När ni lanserar nya kampanjer måste ni se till att aktivera Buyer Touchpoints för varje kampanj efter behov. Checka ut [den här artikeln](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md)för mer information.

**Ladda upp utgifter för alla kanaler (1x/månad)**

Utnyttja alla intäkts- och avkastningsbaserade rapporteringsfunktioner för[!DNL Marketo Measure]måste du berätta [!DNL Marketo Measure] hur mycket ni spenderar på var och en av era marknadsföringskanaler och underkanaler. Vi rekommenderar att du utser ägaren av varje kanal/delkanal och att du rapporterar utgifter till en enda part som ansvarar för att överföra ny kostnadsinformation på månadsbasis.

Uppdatera minnet om hur du överför kostnadsinformation genom att läsa [den här artikeln](/help/marketing-spend/spend-management/marketing-channel-costs.md).

**Uppdatera lista med domäner som ska spåras (1x/månad)**

Marketo Measure spårar alla sidor och underdomäner där Javascript är aktivt, men bara för domäner som vi känner till. Om du nyligen har debiterat en ny domän, expanderat internationellt eller ändrat din primära domän kontaktar du [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"} så att vi kan uppdatera ditt konto.

**Granska anpassad kanalmappning för precision (1x/månad)**

Under introduktionen ställer ni in anpassad kanalmappning för era marknadsföringssatsningar online och offline. Efterhand som er marknadsföringsstrategi och användning av Marketo Measure utvecklas bör ni hålla ett öga på mappningslogiken för att se till att alla era kontaktytor kategoriseras på rätt sätt.

Kom ihåg: [!DNL Marketo Measure] bearbetar om data när du redigerar mappningslogik, så att du inte kan ändra dessa regler mer än en gång var 7:e dag.

Referens [den här artikeln](/help/channel-tracking-and-setup/online-channels/online-custom-channel-setup.md) för installation online, [den här artikeln](/help/channel-tracking-and-setup/offline-channels/offline-custom-channel-setup.md) för offlinekonfiguration och den här listan över bästa praxis från våra kunder:

* Granska de kontaktpunkter som för närvarande tillhör någon annan eller NULL-kanal som du har konfigurerat. Om det behövs kan du uppdatera mappningslogiken för att kategorisera om dessa kontaktytor i mer korrekta kanaler.
* Granska de kontaktytor som för närvarande faller inom era direktkanaler. Om några av era e-postmarknadsföringskampanjer eller andra satsningar saknar UTM-parametrar, finns det en bra chans att trafik felaktigt paketeras i en direktkanal. Överväg att uppdatera UTM-parametrarna för att hämta den refererande källan.

**Utvärdera inställningar för inaktivering av kontaktpunkter (1x/kvartal)**

Om du ser många kontaktytor som du inte vill ta med i attribueringsberättelsen (från en [!DNL Login] eller [!DNL Unsubscribe forms], en karriärsida eller ett internt program) kanske du vill utvärdera dina befintliga inställningar för inaktivering av kontaktpunkter. En gång i kvartalet kan du identifiera grupper av kontaktytor som skapar onödigt brus och uppdatera din undertryckningslogik på lämpligt sätt. [Här är en användbar artikel](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)  med instruktionerna.

**Granska anpassad scenmappning för precision (1x/kvartal) (om tillämpligt)**

Om du använder någon anpassad [!UICONTROL Lead], [!UICONTROL Contact], eller [!UICONTROL Opportunities] kan du också ha anpassat vilken del av pipeline som de här faserna är kopplade till och om dessa faser ingår i en anpassad attribueringsmodell eller inte. En gång i kvartalet, besök [den här artikeln](/help/advanced-marketo-measure-features/custom-attribution-models/custom-attribution-model-and-setup.md) för att uppdatera minnet på den anpassade scenmappningen och säkerställa att du spårar dina anpassade stadier korrekt.

**Jämför maskininlärningsmodell med anpassad modellvikt (1x/kvartal) (om tillämpligt)**

Om du har licens för [!DNL Marketo Measure] Anpassad modell, du har även data tillgängliga från vår Machine Learning Model (MLM) i [!UICONTROL Settings] > [!UICONTROL Attribution Settings]. MLM beräknar vikten av varje fas med hjälp av kontaktpunktsdata från ditt konto och kan hjälpa dig att bestämma hur attribueringsvikten ska fördelas i din anpassade modell. Vi rekommenderar att du jämför MLM med din anpassade modell en gång per kvartal och diskuterar konsekvenserna av eventuella ändringar i din anpassade modell med din SM.

Mer information om [!DNL Marketo Measure] Machine Learning Model, checka ut [den här artikeln](/help/advanced-marketo-measure-features/custom-attribution-models/machine-learning-model-faq.md).
