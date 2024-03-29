---
unique-page-id: 18874708
description: Attribut för Salesforce-aktiviteter - [!DNL Marketo Measure]
title: Salesforce-aktivitetsattribuering
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Salesforce-aktivitetsattribuering {#salesforce-activities-attribution}

The [!DNL Marketo Measure] Salesforce-integreringen av aktiviteter inkluderar specifika uppgifts- och händelseposter i din attribueringsmodell. Börja spåra saker som säljmejl eller telefonsamtal som inte fick någon kredit. Om du vill konfigurera din aktivitetsregel går du till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"}. Därifrån går du till **[!UICONTROL Settings]** och klicka på **[!UICONTROL Activities]** -fliken.

![](assets/1.png)

Vi introducerar ett nytt koncept som kallas [!DNL Marketo Measure] Campaign. För varje regel som du definierar ska du spara posterna i en [!DNL Marketo Measure] Kampanj som du kan namnge. Lägg till flera kampanjer efter behov. Tänk dig att mäta effektiviteten i en utgående försäljningskampanj bredvid en betald mediekampanj!

Du kommer att använda den här [!DNL Marketo Measure] Kampanjnamn som anger vilken kanal den ska mappas till. Om du fortfarande funderar på utgående försäljning kanske alla utgående försäljningskampanjer ska placeras i en BDR-kanal.

Bekanta dig med hierarkin:

* Kanal
   * Delkanal
      * Campaign
      * Campaign
   * Delkanal
      * Campaign

>[!TIP]
>
>Om du till exempel vill ange en unik kampanj för varje säljare använder du dynamiska ersättningsparametrar för att fylla i [!DNL Marketo Measure] Kampanjnamn. I samma exempel kan du skriva `"Outbound Sales - {AssignedTo}"` och det ändras till något som `"Outbound Sales - Jill"` eller `"Outbound Sales - Jack."`

![](assets/2.png)

När du [!DNL Marketo Measure] Kampanjnamn är inställt. Det är dags att ställa in dina aktivitetsregler.

Reglerna fungerar som ett filter som anger vilka poster som är berättigade till attribuering. Tänk dig att du skapar en rapport i CRM med liknande logik för att generera rapporten. Du kan använda en kombination av och/eller programsatser och olika operatorer som `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Definiera `and` programsatser i en rutregel eller ett lager `or` -programsatser utanför paketet.

![](assets/3.png)

>[!NOTE]
>
>Formelfält kan inte användas i reglerna och visas inte i plocklistan. Eftersom formler beräknas i bakgrunden och inte ändrar en post, [!DNL Marketo Measure] kan inte identifiera om en post passar en regel eller inte.
>
>Se till att använda rätt värden för ID-fält som CrmEvent.CreatedById. [!DNL Salesforce IDs] är 18 tecken långa ( 0054H00007WmrfQAC).

Välj slutligen ett datum- eller datum-/tidsfält som ska användas som slutpunktsdatum för köpare. Det går att välja både standardfält och anpassade fält.

>[!TIP]
>
>Med paketinstallationen [!DNL Marketo Measure] innehåller ett anpassat fält för Buyer Touchpoint-datum i Activity-posten. Om du vill använda ett dynamiskt datum, t.ex. det datum då en status ändras, går det att använda ett CRM-arbetsflöde för att ange&quot;Buyer Touchpoint Date&quot; och sedan välja Buyer Touchpoint Date här i det här steget.

![](assets/4.png)

Glöm inte att ange olika regler för aktiviteter eller händelser. Du måste veta vilket objekt ditt säljteam använder för att registrera sina aktiviteter.

![](assets/5.png)

Du vill förmodligen placera dessa nya kontaktytor i rätt ställe [Marknadsföringskanal](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"}. Det gör du genom att definiera kanalen med den nya Campaign-mappningen som precis skapades.

>[!TIP]
>
>När du lägger till en kanaldefinition bör du använda värden för jokertecken, ett enklare sätt att ange operatorer som:
>
>börjar med ( utgående&#42; )
>
contains ( &#42;Utgående&#42; )
>
slutar med ( &#42;Utgående)
>
Inget jokertecken betyder i princip&quot;är lika med&quot;, så se till att använda dem efter behov.

| **Operator** | **Användningsfall** |
|---|---|
| Är lika med | Enskilt värde - exakt matchning |
| Innehåller | Enskilt värde - innehåller värde |
| Matchar alla | Flera värden - exakt matchning |
| Matchar alla (innehåller) | Flera värden - &#42;value&#42;, &#42;värde, &#42;value&#42; |

![](assets/6.png)

Och sist men inte minst har ni möjlighet att ange kostnader för era nya kanaler. The [Marknadsföringsutgift - överföring](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&amp;id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} gör att du kan ange dina utgifter på kanalnivå, delkanalsnivå eller kampanjnivå. Med nya [!DNL Marketo Measure] I kampanjer kan ni lägga till de relaterade kostnaderna per månad och sedan se avkastningen för varje kampanj!

![](assets/7.png)

>[!MORELIKETHIS]
>
[Vanliga frågor om aktivitetsattribut](/help/advanced-marketo-measure-features/activities-attribution/activities-attribution-faq.md)
