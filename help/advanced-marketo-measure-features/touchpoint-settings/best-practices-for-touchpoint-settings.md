---
description: Bästa praxis för inställningar för kontaktpunkter - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa tillvägagångssätt för inställningar för kontaktpunkter
exl-id: 01e314a6-e33d-45cd-aaa3-c212afec07d1
feature: Touchpoints
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Bästa tillvägagångssätt för inställningar för kontaktpunkter {#best-practices-for-touchpoint-settings}

## Ökning {#overview}

Touchpoint-inställningsdelen av [!DNL Marketo Measure] kan du ange regler som inaktiverar eller tar bort kontaktytor från [!DNL Marketo Measure] data och relaterade system. Dessa regler kan hjälpa er att isolera vissa datauppsättningar som inte behöver representeras i era data för köparens kontaktyta eller som ni inte vill ta emot attribueringskrediter utan att störa er spårning och datainsamling.

**Borttagning av pekpunkt** medel [!DNL Marketo Measure] kommer att tömma (d.v.s. ta bort) alla beröringspunkter från CRM som passar regelvillkoren. Data kan rapporteras på i [!DNL Marketo Measure] Kontrollpanel för avkastning (Discover), men visas inte i CRM. Används vanligen för att minska stress i datalagringsgränserna i din CRM

**Inaktivering av kontaktpunkt** liknar Touchpoint Removal, men data kan INTE rapporteras på i ROI Dashboard. Eventuella kontaktpunkter som inaktiveras är inte tillgängliga i CRM eller Discover. Undertryckningen säkerställer att CRM-data och Discover-data matchar. Används vanligen för att finjustera och ytterligare specificera vilka slutpunktsdata du vill få attribueringskrediter.

I [!DNL Marketo Measure] app kommer avsnittet med inställningar för pekpunkter att delas upp i fyra huvudavsnitt. Varje avsnitt undertrycker eller tar bort olika datauppsättningar. Använd tangenten nedan för att kontrollera att reglerna inte visar eller tar bort de önskade kontaktytorna.

* Ta bort Buyer Touchpoints från CRM
   * Använd det här avsnittet när du vill skapa en regel som ska tas bort **Kontaktpunktsdata för köpare** (de kontaktytor som är kopplade till individen, inte möjligheten) från din **CRM**
* Utelämna slutpunkter för köpare från CRM
   * Använd det här avsnittet när du vill skapa en regel som ska tas bort **Kontaktpunktsdata för köpare** (de kontaktytor som är kopplade till individen, inte möjligheten) från din **CRM** och **Upptäck**
* Ta bort Touchpoints för Buyer-attribuering från CRM
   * Använd det här avsnittet när du vill skapa en regel som ska tas bort **Buyer Attribution Touchpoint** data (de kontaktytor som är kopplade till affärsmöjligheten och intäkterna) från **CRM**
* Utelämna slutpunkter för Buyer Attribution från CRM
   * Använd det här avsnittet när du vill skapa en regel som ska tas bort **Buyer Attribution Touchpoint** data (de kontaktytor som är kopplade till affärsmöjligheten och intäkterna) från **CRM** och **Upptäck**

## Bästa praxis {#best-practice}

Oavsett om du skapar regler för inställning av slutpunkt för första gången eller bara granskar dem för att kontrollera om de är korrekta bör du tänka på följande bästa praxis.

* Upprätta en lista med data som du vill inaktivera eller ta bort innan du skapar reglerna
* Identifiera exakt vilka fält som tydligt anger vilken regel eller vilka regler du konfigurerar
* Kontrollera att du har angett rätt operator för regeln
* Om du använder tangenten ovan kontrollerar du att regeln är angiven i rätt avsnitt i inställningarna för slutpunkten
* Testa reglerna innan du implementerar dem genom att replikera regellogiken i en Buyer-kontaktpunktsrapport i CRM för att säkerställa att den inaktiverar eller tar bort önskade data

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Det är viktigt att du granskar inställningarna för din kontaktpunkt eftersom de kan ändra dina data drastiskt när de inte är korrekt definierade. Vi rekommenderar att du minst två gånger per år granskar dina inställningar för kontaktpunkter. Det här är en enkel visuell granskning av reglerna som är konfigurerade i avsnittet Touchpoint-inställningar i [!DNL Marketo Measure] app. Med den här granskningen kan du känna dig säker på att dina Touchpoint-inställningar är aktuella och att eventuella ändringar kan göras.

Skäl att granska dina inställningar för slutpunkter är ...

* Omsättning i marknadsföringsteamet
* Viktiga uppdateringar av webbplatsens struktur
* Identifiering av kontaktpunktsdata som inte längre är användbara
   * Varje gång du stöter på kontaktpunktsdata som du tycker inte ska ta emot attribueringskrediter, är reglerna för att inaktivera kontaktytor funktionaliteten för att säkerställa att dina data är så rena och korrekta som möjligt.
* Ändringar i de fält som används för att definiera reglerna för inaktivering eller borttagning

>[!MORELIKETHIS]
>
>* [Översikt över borttagning och undertryckning av pekpunkter](/help/advanced-marketo-measure-features/touchpoint-settings/touchpoint-removal-and-touchpoint-suppression.md)
>* [Varför ska man aldrig ta bort kontaktytor?](/help/advanced-marketo-measure-features/touchpoint-settings/why-you-should-never-delete-touchpoints.md)
>* [Kontaktpunkter för köpare (BT) respektive Buyer Attribution Touchpoints (BAT)](/help/configuration-and-setup/getting-started-with-marketo-measure/difference-between-buyer-touchpoints-and-buyer-attribution-touchpoints.md)
