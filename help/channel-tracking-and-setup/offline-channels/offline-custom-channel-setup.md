---
unique-page-id: 18874598
description: Anpassad kanalinställning offline - [!DNL Marketo Measure] - Produktdokumentation
title: Anpassad kanalinställning offline
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
feature: Channels
source-git-commit: 3df1bd288ebd65f75a2ed52d7c8a6faf50c7ff1f
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---

# Anpassad kanalinställning offline {#offline-custom-channel-setup}

## Komma igång {#getting-started}

Jämfört med hur [!DNL Marketo Measure] hanterar regler för onlinekanaler. Du kommer att lägga märke till att reglerna för offlinekanaler inte kräver att kalkylblad används. Det finns dock fortfarande ett blad i implementeringsplanen, eftersom det kan vara bra att tänka igenom hur du vill organisera dina offlinekanaler.

Kalkylbladet har tre kolumner:

![](assets/1-2.png)

**[!UICONTROL Salesforce]Kampanjtyp** - lägg till kampanjtyper som identifieras i [!DNL Salesforce] här

* Det kan till exempel vara ett e-postmeddelande, ett webbinarium, en konferens eller andra värden som du har skapat för det här fältet som du vill tilldela Touchpoints.

**[!UICONTROL Channel]** - lägg till olika marknadsföringskanaler här

**[!UICONTROL Subchannel]** - lägg till motsvarande delkanaler här

## Offlinekanallogik {#offline-channel-logic}

[!DNL Marketo Measure] offlinekanallogiken bestäms av Campaign-objektet, särskilt [!DNL Salesforce] Kampanjtyp. Varje offlineåtgärd måste ha en [!DNL Salesforce] Kampanjtyp, till exempel middag eller mässor, eftersom [!DNL Marketo Measure] förlitar sig på det här fältet för att förstå vilken kanal och underkanal som ska mappas till.

SFDC-kampanjtyperna visas på fliken Offlinekanal, som listas under [!DNL Salesforce] Kampanjtyp. Observera att [!DNL Marketo Measure] kan bara importera SFDC-kampanjtyper för kampanjer som har associerade köpkontaktytor.

![](assets/2-2.png)

Här kan du skapa kanalmappning/delkanalsmappning i dialogrutan [!DNL Marketo Measure] app. Det här kommer antagligen att innebära att du skapar nya kanaler och delkanaler i [!DNL Marketo Measure] appen, som görs i delen Skapa kanaler i appen, som visas i bilden nedan. Nya kanaler och underkanaler måste skapas för [!DNL Marketo Measure] för att förstå var du ska trycka på kontaktytor. Du kan bestämma hur du vill att kampanjtyperna ska mappas.

![](assets/3-2.png)

## Exempel på kanalmappning {#channel-mapping-example}

Tänk dig till exempel att du går på två [!DNL Salesforce] konferenser om året. Varje konferens är dock mycket annorlunda och har en unik målgrupp. Du vill veta vilken av de två som ger mer värde. I [!DNL Salesforce] kan du ge januarihändelsen namnet &quot;Conference&quot; av kampanjtypen &quot;channel&quot;, kalla din kanal &quot;[!DNL Salesforce]och din subkanal&quot;January Conference&quot;.

Nu vill du göra samma sak med konferensen i juni. Eftersom det här är en konferens kan den också få samma kampanjtyp, i det här fallet &quot;Conference&quot;. Kanalen är densamma [!DNL Salesforce]och delkanalen till den andra konferensen är&quot;Junikonferensen&quot;. Detta är begripligt ur ett organisatoriskt perspektiv. Men det är väldigt förvirrande för [!DNL Marketo Measure] logik för att läsa och tillämpa dessa regler eftersom båda kampanjerna har samma kampanjtyp. [!DNL Marketo Measure] skriptet kan inte mappa data från en typ till två olika underkanaler. Det innebär att ni måste skapa en ny Campaign-typ för varje underkanal, men att underkanalerna kan ha samma kanal.

Nedan visas ett exempel på logik som [!DNL Marketo Measure] skulle inte kunna läsa:

![](assets/4-2.png)

I scenariot ovan vill du skapa en unik kampanjtyp eftersom du inte kan mappa samma kampanjtyp till två olika underkanaler. I stället vill du konfigurera unika typer som följande:

![](assets/5-2.png)

Alla befintliga kampanjtyper måste inkluderas i din kanalkarta och&quot;NULL&quot; ska läggas till som kanal.

Ta dig tid att gå in [!DNL Salesforce] för att fastställa antalet och typen av befintliga posttyper, som du vill inkludera, och om du behöver skapa ytterligare kampanjer baserat på informationen ovan. När du har fyllt i all nödvändig information är du redo att överföra.

Läs mer om [synka offline [!DNL Salesforce] Kampanjer med [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/deprecated-processes/syncing-offline-campaigns.md).

## Hantera SFDC-kampanjer för onlinemarknadsföring {#handling-sfdc-campaigns-for-online-marketing-efforts}

Det är vanligt att marknadsföringsteamen skapar [!DNL Salesforce] kampanjer för att spåra olika aktiviteter inom digital marknadsföring. Det finns inga problem med denna praxis, men det är viktigt att behandla dessa kampanjer annorlunda än verkliga offlinekampanjer, som direktreklam eller konferenser, till exempel. Kampanjer som är relaterade till digitala händelser (interaktioner som sker på er webbplats) bör inte synkroniseras med [!DNL Marketo Measure]. Synkronisering av dessa kampanjer skulle leda till duplicering av kontaktpunkter eftersom [!DNL Marketo Measure] JavaScript håller redan på att spåra onlineaktiviteter.

Ett annat tips för att hantera kampanjer för onlineaktiviteter är att mappa [!DNL Salesforce] Kampanjtyp till NULL. Om du vill göra det skapar du först en kanal i [!DNL Marketo Measure] app med namnet NULL enligt bilden nedan. Detta finns i [!DNL Marketo Measure] app under **Skapa kanaler** -avsnitt. Detta är praktiskt om en kampanj som inte ska synkroniseras av misstag synkroniseras. Det är enkelt att hitta kampanjen och korrigera synkroniseringsstatusen genom att titta på allt som är inramat under NULL.

![](assets/6-2.png)

## Ange dina regler för offlinekanal i appen {#entering-your-offline-channel-rules-to-the-app}

När du har redigerat och uppdaterat kalkylbladet med dina anpassade regler är nästa steg att återskapa den här kanalmappningen i [!DNL Marketo Measure] app - du kommer inte att överföra kalkylblad för offlinekanaler. I stället anger du informationen i listrutorna enligt bilden nedan. Det här hittas genom att klicka **[!UICONTROL Offline Channels]** under **[!UICONTROL Channels]** -avsnitt.

![](assets/7-2.png)

>[!TIP]
>
>Vill bestämma _när_ a [!DNL Salesforce] Campaign Type dras ner i [!DNL Marketo Measure] kanalmappning? Gå bara till **[!UICONTROL Setup]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Fields]** > **[!UICONTROL Type]**. Du kan sedan se vilka värden som finns i listan och vilka som är inaktiva. Inaktiva typer visas inte som en valbar typ i vår[!UICONTROL Offline Channels]&quot;. Observera att detta kan ta mellan några minuter och 48 timmar.

Klicka **[!UICONTROL Save]** när du är klar och [!DNL Marketo Measure] kommer att överföra ändringarna och bearbeta om data.

>[!MORELIKETHIS]
>
>* [[!DNL Marketo Measure] Universitet: Mappa offlinekanaler](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c630eca34d9f0367662b77f)
>
>* [[!DNL Marketo Measure] Universitet: Synkronisera offlinekampanjer](https://universityonline.marketo.com/courses/bizible-fundamentals-channel-management/#/page/5c63286e34d9f0367662b78b)
>
>* [Integrering av Marketo Engage-program](/help/marketo-measure-and-marketo/marketo-measure-integrations-with-marketo/marketo-engage-programs-integration.md#channel-mapping)
