---
description: Bästa praxis för implementering av [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure]
title: Bästa tillvägagångssätt för att implementera [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
feature: Tracking
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Metodtips för att implementera [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Översikt {#overview}

JavaScript ([!DNL Marketo Measure]) spårar dina webbbesökares digitala marknadsföringsinteraktioner och är avgörande för att [!DNL Marketo Measure] ska kunna skapa online-Touchpoint-data. Om JavaScript [!DNL Marketo Measure] distribueras korrekt och heltäckande på hela webbplatsen/platserna säkerställer du att de sessionsdata som samlas in genererar korrekta kontaktpunktsdata.

Inkonsekvenser i distributionen av JavaScript [!DNL Marketo Measure] orsakar avbrott i sessionsdata, vilket kan resultera i följande:

* Felaktig attribuering av kanaler/delkanaler
* Förlorade källdata
* Höga nivåer av felaktig direkttrafik
* Inkonsekvent rapportering

[!DNL Marketo Measure] JavaScript är en grundläggande del av ditt [!DNL Marketo Measure]-konto och nyckeln till framgång!

## Bästa praxis {#best-practice}

När det gäller att implementera och hantera din [!DNL Marketo Measure] JavaScript bör du tänka på följande bästa praxis.

* Bekräfta att alla dina domäner är listade i ditt [!DNL Marketo Measure]-konto
   * Om du är orolig för dina domäner kontaktar du support
* Distribuera JavaScript på ALLA sidor.
   * Om du bara placerar JavaScript på vissa sidor kommer sessionsdata att brytas vilket kommer att orsaka felaktiga [!DNL Marketo Measure]-data
* För ett formulär på din webbplats som du inte vill skapa kontaktpunkter från måste du lägga till [!DNL Marketo Measure] Exkludera skript
   * Detta exkluderingsskript säkerställer att sessionsdata för [!DNL Marketo Measure] inte avbryts och att källdata finns kvar
      * Exempel på vanliga formulär som ska undertryckas är:
         * Kundinloggningar
         * Glömt lösenordsformulär
         * Avbeställ blanketter
         * Yrkesansökningsformulär
* Granska avsnitten&quot;Ytterligare överväganden&quot; och&quot;Forms att betala extra uppmärksamhet&quot; i Adding [!DNL Marketo Measure] Script-resursen som listas nedan för att kontrollera om det finns några scenarier som kan behöva specialhantering

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Konfigurationen av JavaScript [!DNL Marketo Measure] täcks under den inledande implementeringen, men ändringar av webbplatsen eller teamet som hanterar den kan leda till avbrott i [!DNL Marketo Measure]-spårningen. Vi rekommenderar att du bekräftar att JavaScript [!DNL Marketo Measure] distribueras korrekt och utförligt en gång om året. Om din organisation har någon typ av ändringsprotokolldokumentation för webbplatsen kontrollerar du att det finns en del som förklarar att [!DNL Marketo Measure] JavaScript ska behållas/läggas till på alla nya sidor.

Andra orsaker till detta kan utlösa en granskning av din JavaScript-konfiguration är ...

* Omsättning i marknadsföringsteamet
* Ändringar och uppdateringar av webbplatsstrukturen
* Webbplatsmigreringar
* Ändringar i din domän
* Förvärv av andra företag och deras webbresurser
