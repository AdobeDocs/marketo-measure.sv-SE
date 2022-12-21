---
description: Bästa praxis för implementering [!DNL Marketo Measure] JavaScript - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa praxis för implementering [!DNL Marketo Measure] JavaScript
exl-id: 0359ad27-81e8-4902-a23a-49a5646a44d0
source-git-commit: cf144eb4bc9282ae6a260acd3735f24644292a19
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Bästa praxis för implementering [!DNL Marketo Measure] JavaScript {#best-practices-for-implementing-marketo-measure-javascript}

## Översikt {#overview}

The [!DNL Marketo Measure] JavaScript spårar era webbbesökare digitala marknadsföringsinteraktioner och är nyckeln till [!DNL Marketo Measure] möjlighet att skapa online-data för kontaktpunkter. Med [!DNL Marketo Measure] JavaScript-kod som används korrekt och omfattande på hela webbplatsen/platserna säkerställer att de sessionsdata som samlas in genererar korrekta kontaktpunktsdata.

Inkonsekvenser i distributionen av [!DNL Marketo Measure] JavaScript orsakar avbrott i sessionsdata vilket kan resultera i följande:

* Felaktig kanal-/delkanalsattribuering
* Förlorade källdata
* Höga nivåer av felaktig direkttrafik
* Inkonsekvent rapportering

[!DNL Marketo Measure] JavaScript är en grundläggande del av [!DNL Marketo Measure] och nyckeln till framgång!

## Bästa praxis {#best-practice}

När det gäller implementering och hantering av [!DNL Marketo Measure] JavaScript bör du tänka på följande bästa praxis:

* Bekräfta att alla dina domäner är listade i din [!DNL Marketo Measure] konto
   * Kontakta support om du är orolig över dina domäner
* Distribuera JavaScript på ALLA sidor.
   * Om du bara placerar JavaScript på vissa sidor uppstår avbrott i sessionsdata, vilket kan orsaka felaktiga [!DNL Marketo Measure] data
* För ett formulär på din webbplats som du inte vill skapa kontaktpunkter från måste du lägga till [!DNL Marketo Measure] Exkludera skript
   * Detta exkluderingsskript säkerställer att [!DNL Marketo Measure] sessionsdata kommer inte att avbrytas och källdata finns kvar
      * Exempel på vanliga formulär som ska undertryckas är:
         * Kundinloggningar
         * Glömt lösenordsformulär
         * Avbeställ blanketter
         * Yrkesansökningsformulär
* Se avsnitten &quot;Additional Considerations&quot; och &quot;Forms to Pay Extra Attention To&quot; i Adding [!DNL Marketo Measure] Skriptresurs som listas nedan för att söka efter scenarier som kan behöva specialhantering

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Under konfigurationen av [!DNL Marketo Measure] JavaScript täcks under den inledande implementeringen, ändringar av webbplatsen eller det team som hanterar den kan leda till störningar i [!DNL Marketo Measure] spårning. Vi rekommenderar att du bekräftar [!DNL Marketo Measure] JavaScript distribueras korrekt och omfattande en gång per år. Om din organisation har någon typ av ändringsprotokolldokumentation för webbplatsen ska du dessutom se till att det finns en del som förklarar att [!DNL Marketo Measure] JavaScript ska behållas/läggas till på alla nya sidor.

Andra orsaker till detta kan utlösa en granskning av JavaScript-konfigurationen är ...

* Omsättning i marknadsföringsteamet
* Ändringar och uppdateringar av webbplatsstrukturen
* Webbplatsmigreringar
* Ändringar i din domän
* Förvärv av andra företag och deras webbegenskaper
