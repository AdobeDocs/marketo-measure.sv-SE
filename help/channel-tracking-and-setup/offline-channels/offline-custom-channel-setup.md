---
description: Inställningar för anpassad offlinekanal - [!DNL Marketo Measure]
title: Anpassad kanalinställning offline
exl-id: c5697714-1a79-40bd-8b7c-e10768f4ef67
feature: Channels
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Anpassad kanalinställning offline {#offline-custom-channel-setup}

## Komma igång {#getting-started}

Jämfört med hur [!DNL Marketo Measure] hanterar regler för onlinekanaler kommer du att märka att reglerna för offlinekanaler inte kräver att ett kalkylblad används. Det finns dock fortfarande ett blad i implementeringsplanen, eftersom det kan vara bra att tänka igenom hur du vill organisera dina offlinekanaler.

Kalkylbladet har tre kolumner:

![Kalkylbladsmall med tre kolumner för Salesforce Campaign-typen, Kanal och Delkanal](assets/1-2.png)

**[!UICONTROL Salesforce]kampanjtyp** - lägg till kampanjtyper som identifieras i [!DNL Salesforce] här

* Det kan till exempel vara ett e-postmeddelande, ett webbinarium, en konferens eller andra värden som du har skapat för det här fältet som du vill tilldela Touchpoints.

**[!UICONTROL Channel]** - lägg till dina olika marknadsföringskanaler här

**[!UICONTROL Subchannel]** - lägg till motsvarande delkanaler här

## Offlinekanallogik {#offline-channel-logic}

[!DNL Marketo Measure] offlinekanallogik bestäms av Campaign-objektet, särskilt [!DNL Salesforce] Campaign-typen. Varje offlineåtgärd måste ha en [!DNL Salesforce]-kampanjtyp, till exempel middag eller bildspel, eftersom [!DNL Marketo Measure] förlitar sig på det här fältet för att förstå vilken kanal och underkanal som ska mappas till.

Kampanjtyperna för SFDC visas på fliken Offlinekanal, som listas under [!DNL Salesforce] Kampanjtyp. Observera att [!DNL Marketo Measure] bara kan importera SFDC Campaign-typer för kampanjer som har associerade Buyer-kontaktytor.

![Fliken Offlinekanaler som visar Salesforce Campaign-typlistan](assets/2-2.png)

Här kan du skapa kanalmappning/delkanalsmappning i appen [!DNL Marketo Measure]. Detta innebär sannolikt att nya kanaler och underkanaler skapas i appen [!DNL Marketo Measure], vilket görs i appens avsnitt Skapa kanaler, som visas i bilden nedan. Nya kanaler och underkanaler måste skapas för att [!DNL Marketo Measure] ska förstå var pekpunkterna ska skickas. Du kan bestämma hur du vill att kampanjtyperna ska mappas.

![Avsnittet Skapa kanaler visar gränssnitt för att skapa nya kanaler och delkanaler](assets/3-2.png)

## Exempel på kanalmappning {#channel-mapping-example}

Tänk dig till exempel att du går på två [!DNL Salesforce] konferenser om året. Varje konferens är dock mycket annorlunda och har en unik målgrupp. Du vill veta vilken av de två som ger mer värde. I din [!DNL Salesforce]-miljö kan du ge Januari-evenemanget kampanjtypen &quot;Conference&quot;, ge kanalen &quot;[!DNL Salesforce]&quot; och din underkanal &quot;January Conference&quot;.

Nu vill du göra samma sak med konferensen i juni. Eftersom det här är en konferens kan den också få samma kampanjtyp, i det här fallet &quot;Conference&quot;. Kanalen är densamma, [!DNL Salesforce], och delkanalen för den andra konferensen är&quot;Juni Conference&quot;. Detta är begripligt ur ett organisatoriskt perspektiv. Det är emellertid väldigt förvirrande för logiken i [!DNL Marketo Measure] att läsa och tillämpa dessa regler eftersom båda kampanjerna har samma kampanjtyp. Skriptet [!DNL Marketo Measure] kan inte mappa data från en typ till två olika underkanaler. Det innebär att ni måste skapa en ny Campaign-typ för varje underkanal, men att underkanalerna kan ha samma kanal.

Nedan visas ett exempel på logik som [!DNL Marketo Measure] inte kan läsa:

![Felaktig kanalmappning som visar samma kampanjtyp mappad till olika underkanaler](assets/4-2.png)

I scenariot ovan vill du skapa en unik kampanjtyp eftersom du inte kan mappa samma kampanjtyp till två olika underkanaler. I stället vill du konfigurera unika typer som följande:

![Korrigera kanalmappning som visar unika kampanjtyper för olika underkanaler](assets/5-2.png)

Alla befintliga kampanjtyper måste inkluderas i din kanalkarta och&quot;NULL&quot; ska läggas till som kanal.

Ta tid till att gå in i [!DNL Salesforce] för att fastställa antalet och typen av befintliga posttyper som du vill inkludera och om du behöver skapa ytterligare kampanjer baserat på informationen ovan. När du har fyllt i all nödvändig information är du redo att överföra.

Läs mer om [synkronisering av offlinekampanjer [!DNL Salesforce] med [!DNL Marketo Measure]](/help/channel-tracking-and-setup/offline-channels/legacy-processes/syncing-offline-campaigns.md).

## Hantera SFDC Campaigns för onlinemarknadsföringsaktiviteter {#handling-sfdc-campaigns-for-online-marketing-efforts}

Det är vanligt att marknadsföringsteamen skapar [!DNL Salesforce]-kampanjer för att spåra olika digitala marknadsföringssatsningar. Det finns inga problem med denna praxis, men det är viktigt att behandla dessa kampanjer annorlunda än verkliga offlinekampanjer, som direktreklam eller konferenser, till exempel. Kampanjer som är relaterade till digitala händelser (interaktioner som sker på din webbplats) ska inte synkroniseras med [!DNL Marketo Measure]. Synkronisering av de här kampanjerna resulterar i duplicering av kontaktpunkter eftersom JavaScript [!DNL Marketo Measure] redan håller på att spåra onlineaktiviteter.

Ett annat tips för att hantera kampanjer för onlineaktiviteter är att mappa kampanjtypen [!DNL Salesforce] till NULL. Om du vill göra det skapar du först en kanal i appen [!DNL Marketo Measure] med namnet NULL, vilket visas i bilden nedan. Detta finns i appen [!DNL Marketo Measure] under avsnittet **Skapa kanaler**. Detta är praktiskt om en kampanj som inte ska synkroniseras av misstag synkroniseras. Det är enkelt att hitta kampanjen och korrigera synkroniseringsstatusen genom att titta på allt som är inramat under NULL.

![Avsnittet Skapa kanaler visar NULL-kanalskapande för onlinekampanjer](assets/6-2.png)

## Ange dina regler för offlinekanal i appen {#entering-your-offline-channel-rules-to-the-app}

När du har redigerat och uppdaterat kalkylbladet med dina anpassade regler är nästa steg att återskapa den här kanalmappningen i appen [!DNL Marketo Measure] - du kommer egentligen inte att överföra ett kalkylblad för offlinekanaler. I stället anger du informationen i listrutorna enligt bilden nedan. Det här hittas genom att klicka på **[!UICONTROL Offline Channels]** under avsnittet **[!UICONTROL Channels]**.

![Gränssnitt för offlinekanaler med listrutor för att ange kanalmappningsregler](assets/7-2.png)

>[!TIP]
>Vill du ta reda på när _när_ en [!DNL Salesforce] kampanjtyp hämtas till kanalmappningen [!DNL Marketo Measure]? Gå till **[!UICONTROL Setup]** > **[!UICONTROL Campaigns]** > **[!UICONTROL Fields]** > **[!UICONTROL Type]**. Du kan sedan se vilka värden som finns i listan och vilka som är inaktiva. Inaktiva typer visas inte som en valbar typ i avsnittet [!UICONTROL Offline Channels]. Observera att den här processen kan ta var som helst från några minuter upp till 48 timmar.

Klicka på **[!UICONTROL Save]** när du är klar och [!DNL Marketo Measure] överför ändringarna och bearbetar om data.

>[!MORELIKETHIS]
> [[!DNL Marketo Measure] Självstudiekurser: Mappa offlinekanaler](https://experienceleague.adobe.com/sv/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/mapping-offline-channels){target="_blank"}
> [[!DNL Marketo Measure] Självstudiekurser: Synkroniserar offlinekampanjer &#x200B;](https://experienceleague.adobe.com/sv/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-salesforce/syncing-offline-campaigns){target="_blank"}
> [Integrering av Marketo Engage-program](/help/marketo-measure-and-marketo/marketo-engage-programs-integration.md#channel-mapping){target="_blank"}
