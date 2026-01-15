---
description: Salesforce Activities Attribution guidelines för Marketo Measure-användare
title: Attribut för Salesforce-aktiviteter
exl-id: 1dc6f15b-2a45-4ed3-9fa3-5267366d1f45
feature: Attribution, Salesforce
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# Attribut för Salesforce-aktiviteter {#salesforce-activities-attribution}

Integreringen av [!DNL Marketo Measure] Salesforce-aktiviteter inkluderar specifika aktivitets- och händelseposter i din attribueringsmodell. Börja spåra saker som säljmejl eller telefonsamtal som inte fick någon kredit. Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target="_blank"} om du vill konfigurera din aktivitetsregel. Gå sedan till fliken **[!UICONTROL Settings]** och klicka på fliken **[!UICONTROL Activities]**.

![Integreringen av Marketo Measure Salesforce Activity (Aktiviteter) innehåller en specifik aktivitet och](assets/activities-attribution-10.png)

Till att börja med introducerar vi ett nytt koncept som kallas [!DNL Marketo Measure]-kampanj. För varje regel som du definierar kommer du att spara posterna i en [!DNL Marketo Measure]-kampanj som du kan namnge. Lägg till flera kampanjer efter behov. Tänk dig att mäta effektiviteten i en utgående försäljningskampanj bredvid en betald mediekampanj!

Du kommer att använda det här [!DNL Marketo Measure]-kampanjnamnet för att ange vilken kanal det ska mappas till. Om du fortfarande funderar på utgående försäljning kanske alla utgående försäljningskampanjer ska placeras i en BDR-kanal.

Bekanta dig med hierarkin:

* Kanal
   * Delkanal
      * Campaign
      * Campaign
   * Delkanal
      * Campaign

>[!TIP]
>
>Om du till exempel vill ange en unik kampanj för varje säljare använder du dynamiska ersättningsparametrar för att fylla i kampanjnamnet [!DNL Marketo Measure]. I samma exempel kan du ange `"Outbound Sales - {AssignedTo}"` och det ändras till något som `"Outbound Sales - Jill"` eller `"Outbound Sales - Jack."`

![Om du vill ange en unik kampanj för varje säljare](assets/activities-attribution-11.png)

När kampanjnamnet [!DNL Marketo Measure] har angetts är det dags att konfigurera aktivitetsreglerna.

Reglerna fungerar som ett filter som anger vilka poster som är berättigade till attribuering. Tänk dig att du skapar en rapport i CRM med liknande logik för att generera rapporten. Du kan använda en kombination av och/eller programsatser och olika operatorer som `matches any`, `contains`, `starts with`, `ends with`, `is equal to`. Definiera `and`-programsatser i en boxed-regel eller `or`-lagerprogramsatser utanför rutan.

![Reglerna fungerar som ett filter som anger vilka poster som är ](assets/activities-attribution-12.png)

>[!NOTE]
>
>Formelfält kan inte användas i reglerna och visas inte i plocklistan. Eftersom formler beräknas i bakgrunden och inte ändrar en post, kan [!DNL Marketo Measure] inte identifiera om en post passar in i en regel eller inte.
>
>Se till att använda rätt värden för ID-fält som CrmEvent.CreatedById. [!DNL Salesforce IDs] är 18 tecken långt ( 0054H00007WmrfQAC).

Välj sedan ett datum- eller datum-/tidsfält som ska användas som Buyer Touchpoint-datum. Det går att välja både standardfält och anpassade fält.

>[!TIP]
>
>Under paketinstallationen inkluderar [!DNL Marketo Measure] ett anpassat Buyer Touchpoint Date-fält i aktivitetsposten. Om du vill använda ett dynamiskt datum, t.ex. det datum då en status ändras, går det att använda ett CRM-arbetsflöde för att ange&quot;Buyer Touchpoint Date&quot; och sedan välja Buyer Touchpoint Date här i det här steget.

![Med paketinstallationen inkluderar Marketo Measure en anpassad Buyer Touchpoint](assets/activities-attribution-13.png)

Glöm inte att ange olika regler för aktiviteter eller händelser. Du måste veta vilket objekt ditt säljteam använder för att registrera sina aktiviteter.

![Glöm inte att ange olika regler för aktiviteter eller händelser. Du](assets/activities-attribution-5.png)

Du vill förmodligen placera dessa nya kontaktytor i deras lämpliga [marknadsföringskanal](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Channels.Online%20Channels){target="_blank"}. Det gör du genom att definiera kanalen med den nya Campaign-mappningen som precis skapades.

>[!TIP]
>
>När du lägger till en kanaldefinition bör du använda värden för jokertecken, ett enklare sätt att ange operatorer som:
>
>börjar med ( Outbound&#42; )
>
>innehåller ( &#42;Utgående&#42; )
>
>slutar med ( &#42;utgående)
>
>Inget jokertecken betyder i princip&quot;är lika med&quot;, så se till att använda dem efter behov.

| **Operator** | **Använd skiftläge** |
|---|---|
| Är lika med | Enskilt värde - exakt matchning |
| Innehåller | Enskilt värde - innehåller värde |
| Matchar alla | Flera värden - exakt matchning |
| Matchar alla (innehåller) | Flera värden - &#42;värde&#42;, &#42;värde, &#42;värde&#42; |

![| Matchar alla (innehåller) | Flera värden - &amp;42;värde&amp;42;, &amp;42;värde, &amp;42;värde&amp;42; |](assets/activities-attribution-8.png)

Och sist men inte minst har ni möjlighet att ange kostnader för era nya kanaler. Med [Utgiftsöverföring för marknadsföring](https://experience.adobe.com/#/marketo-measure/MyAccount/Business?busView=false&id=10#/!/MyAccount/Business/Account.Settings.SettingsHome?tab=Reporting.Marketing%20Spend){target="_blank"} kan du ange din utgift på kanalnivå, delkanalsnivå eller kampanjnivå. Med dina nya [!DNL Marketo Measure]-kampanjer kan du lägga till de relaterade kostnaderna per månad och sedan se avkastningen för varje kampanj!

![Och sist men inte minst kan du ange kostnader](assets/activities-attribution-9.png)

>[!MORELIKETHIS]
>
>[Vanliga frågor om aktivitetsattribuering](/help/channel-tracking-and-setup/activities-attribution-faq.md)
