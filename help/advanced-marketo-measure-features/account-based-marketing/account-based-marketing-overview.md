---
unique-page-id: 18874730
description: Läs om Account-Based Marketing (ABM) och hur Adobe Marketo Measure hjälper marknadsförings- och säljteam att genomföra framgångsrika ABM-strategier.
title: Kontobaserad marknadsföring - översikt
exl-id: 2ead69c0-66da-439d-a0ba-25c73c4b308c
feature: Account-based Marketing
source-git-commit: e2165fea3e76baeedf9b22247d005578d6c6da5d
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Kontobaserad marknadsföring - översikt {#account-based-marketing-overview}

I följande avsnitt ges en kort översikt över ABM, komponenterna i [!DNL Marketo Measure] ABM-funktionen och hur du lägger till den i [!DNL Salesforce] sidlayout. Läs mer om ABM på Adobe [ABM-blogg](https://business.adobe.com/blog/basics/account-based-marketing){target="_blank"}.

Detaljerade anvisningar om hur du konfigurerar ABM i [!DNL Salesforce] -instans, gå till [Konfigurera ABM-sidlayout i Salesforce](/help/advanced-marketo-measure-features/account-based-marketing/account-based-marketing-overview.md#setting-up-abm-page-layout-in-salesforce){target="_blank"}.

## Vad är ABM? {#what-is-abm}

Kontobaserad marknadsföring, ABM, är en marknadsföringsstrategi där ni inriktar er på och säljer till företag och konton som helhet, inte bara som individer. [!DNL Marketo Measure] hjälper marknadsförings- och säljteam att implementera framgångsrika ABM-strategier med hjälp av funktionen för att mappa lead-till-konto och prediktiv engagemangspoäng.

För att vår kontobaserade marknadsföringsmodell ska börja fylla i din CRM-information [!DNL Marketo Measure] måste följande kriterier vara uppfyllda:

* CRM behöver minst 25 konton som har minst ett stängt Won-säljprojekt på dem för att bättre kunna mäta gemensamma funktioner för ett framgångsrikt konto/affärsmöjlighet.
* På andra sidan av myntet behöver din CRM minst 25 konton utan stängda vinstmöjligheter (alla alternativ måste antingen vara i kategorin&quot;Öppen&quot; eller i kategorin&quot;Stängd förlorad&quot;) - det hjälper oss att mäta vad som blir ett lägre betyg i din organisation.

>[!NOTE]
>
>Ovannämnda &quot;dåliga&quot; konton måste vara öppna i minst 12 månader utan att ackumulera ett Closed Won op; det är den grundläggande riktlinjen för om en Opp har blivit inaktuell för modellens syften.

## Lead till konto-mappning {#lead-to-account-mapping}

Mappning av lead-till-konto är en viktig del i ett effektivt ABM-tillvägagångssätt. Med lead-to-account-mappning grupperas potentiella kunder eller leads i samma företagskonto som de interagerar med ert varumärke. På så sätt kan ni inrikta er på och sälja till personer från samma företag på ett konsekvent sätt. Det finns ingen ytterligare [!DNL Salesforce] som krävs för att börja dra nytta av den här funktionen. The [!DNL Marketo Measure] Lead till kontomappning med olika matchningsmetoder:

* Lead-webbplats till kontowebbplats
* Lead-e-postdomän till kontots webbplatsdomän
* Lead-företagsnamn till kontonamn
* Lead-företag till webbplatsens kontodomän
* Lead-webbplatsen till e-postdomänen för kontokontakter
* Lead-e-postdomän till kontokontaktens e-postdomän
* Lead-webbplats till e-postdomänen för kontoansvariga
* Lead-e-postdomän till kontoledares e-postdomän

Kontots leads/kontakter valideras av deras e-post-/webbplatsdomäner och matchas mot den ledande e-postwebbplatsens domän eller underdomän. Det konto som har flest träffar används.

>[!NOTE]
>
>Varje lead försöker matcha sig mot ett konto i den förmånsordning som anges i metoderna ovan. När en matchning har gjorts anges AccountId omedelbart på Lead och matchas inte med en annan metod.

## Prediktiv engagemangspoäng {#predictive-engagement-score}

The [!DNL Marketo Measure] Predictive Engagement Score, eller PES, är ett dynamiskt värde som illustrerar hur engagerat ett visst konto är i er marknadsföring. Den här poängen är användbar när det gäller att segmentera konton. Det är ett värdefullt verktyg för att identifiera konton och målinrikta dem effektivare.

Det finns många komponenter som går in i algoritmen som beräknar de offentliga arbetsförmedlingarna. Nyhet och ålder har stor inverkan på poängförändringar, tillsammans med senaste beröringspunktsaktivitet eller sidvyer. Om du lägger till nya kontakter i ett konto påverkas också de offentliga arbetsförmedlingarna. Nedan finns en lista över några indata från PES:

* Totalt antal sidvisningar från kontot
* Genomsnittligt antal sidvisningar
* Genomsnittligt antal personer på kontot
* Ålder för senaste sidvy
* Genomsnittlig ålder för sidvisningar
* Antal personer på kontot
* Specifika viktiga sidor och om det har varit ett besök de senaste 30/60/90 dagarna
* Om kontot har en avbruten/vunnen affär
* Hur sannolikt är att du stänger förlorade/vunna?

>[!NOTE]
>
>Du kan lägga märke till en klass av &quot;N/A&quot; eller &quot;-&quot; (strecksymbolen) i Predictive Engagement Score för vissa konton.

_En grad av&quot;N/A&quot; innebär helt enkelt att det inte finns tillräckligt med data på det kontot för att modellen ska kunna generera en verklig klass - med mer data får man en grad till slut._
_En grad av&quot;-&quot; (strecksymbolen) innebär att det här kontot ännu inte har bearbetats av ABM-processen på grund av tidsbegränsningar, ibland missade processer osv. Om du anser att ett konto bör ha en betygsättning, baserat på andra liknande konton eller tidsramar, kan du kontakta och låta [!DNL Marketo Measure] Jag vet._

## Konfigurera ABM-sidlayout i [!DNL Salesforce] {#setting-up-abm-page-layout-in-salesforce}

Om du vill börja använda PES måste du lägga till fältet PES och Related List i rätt sidlayout i [!DNL Salesforce].

1. Navigera till **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Accounts]** > **[!UICONTROL Page Layout]**. Markera sedan den sidlayout som du vill redigera.
1. Gå till [!UICONTROL Fields] och flytta fältet Predictive Engagement Score till ditt kontoinformationsavsnitt.

   ![](assets/1.png)

1. Till sist går du till [!UICONTROL Related Lists] och flytta&quot;Leads&quot;-relaterad lista till sidlayouten.

   ![](assets/2.png)

1. Navigera sedan till **[!UICONTROL Setup]** > **[!UICONTROL Customize]** > **[!UICONTROL Leads]** > **[!UICONTROL Page Layout]** och välj de sidlayouter du vill redigera.
1. Klicka **[!UICONTROL Fields]** och lägg till [!UICONTROL Account] fält där du ser passform på sidan.

   ![](assets/3.png)

Du är redo!

