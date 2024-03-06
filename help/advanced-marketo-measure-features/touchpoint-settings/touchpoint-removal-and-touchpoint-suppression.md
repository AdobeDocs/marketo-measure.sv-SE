---
unique-page-id: 18874710
description: Borttagning av pekpunkter och inaktivering av pekpunkter - [!DNL Marketo Measure]
title: Borttagning av pekpunkter och inaktivering av pekpunkter
exl-id: 201af648-6525-4a80-a7e5-3cbeeb1670b6
feature: Touchpoints
source-git-commit: 1a274c83814f4d729053bb36548ee544b973dff5
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Borttagning av pekpunkter och inaktivering av pekpunkter {#touchpoint-removal-and-touchpoint-suppression}

Lär dig hur du tar bort eller inaktiverar kontaktpunkter som uppfyller specifika villkor i CRM. Detta kan vara praktiskt när du vill frigöra dataminne om du har [!DNL Salesforce] begränsningar för datalagring.

Det finns en viktig skillnad mellan reglerna för borttagning av pekpunkter och reglerna för inaktivering av pekpunkter:

* Borttagning av pekpunkt - [!DNL Marketo Measure] tar bort alla beröringspunkter från CRM som uppfyller regelvillkoren. Data _kan_ rapporteras på [!DNL Marketo Measure] ROI Dashboard, men inte längre i CRM.
* Inaktivering av pekpunkter - Liknar borttagning av pekpunkter, men det går inte att rapportera data på ROI-instrumentpanelen.

Innan du börjar skapa regler för borttagning/inaktivering av slutpunkter är det en bra idé att dela implementeringsplanen med marknadsförings- och säljteamet. Du bör redan ha en uppfattning om vilka typer eller värden du vill ta bort. Några vanliga användningsområden är:

* Ta bort kontaktpunkter från stängda förlorade affärsmöjligheter
* Ta bort kontaktpunkter från mycket gamla leads
* Ta bort kontaktpunkter från okvalificerade leads

När reglerna har sparats [!DNL Marketo Measure] kommer att rensa upp och distribuera din attribueringsmodell. Detta innebär att milstolparna och positionerna kommer att förändras och kanalens attribueringskrediter kommer att ändras! Detta ändrar dina data, så kontakta din Success Manager om du behöver hjälp.

`1)` Det finns två avsnitt för inställningar för borttagning/undertryckning. Du kan ställa in den för Buyer Touchpoints (Leads and Contacts) eller Buyer Attribution Touchpoints (Kontakter, Affärsmöjligheter och Konton).

Börja med att lägga till en regel och markera fältet som definierar dina villkor.

Välj i en lista över operatorer som ska relatera till nästa uppsättning värden, som du lägger till i nästa kolumn.

![](assets/1-1.png)

>[!TIP]
>
>Om du vill lägga till flera värden i ett fält använder du operatorn&quot;matchar alla&quot; med kommatecken som avgränsar varje värde.

>[!TIP]
>
>Om du vill ta hänsyn till ett tomt eller NULL-värde i ett fält lämnar du bara fältet [!UICONTROL Value] rutan är tom. Detta tar hänsyn till scenarier som att utvärdera mot en kontaktyta utan formulär-URL.

>[!NOTE]
>
>Formelfält kan inte användas i reglerna och visas inte i plocklistan. Eftersom formler beräknas i bakgrunden och inte ändrar en post, [!DNL Marketo Measure] kan inte identifiera om en post passar en regel eller inte.

`2)` Lägg till regler i samma grupp för att använda&quot;AND&quot;-logiken i programsatsen.
Du kan också lägga till nya programsatser utanför gruppen för att använda &quot;OR&quot;-logiken i programsatsen.

![](assets/2.png)

`3)` Om reglerna blir komplicerade och du behöver återskapa grupper och göra små ändringar i varje sats använder du [!UICONTROL Clone] för att förenkla.

![](assets/3.png)

Om du gör ett misstag, oroa dig inte. Du kan också ta bort enskilda rader i programsatsen eller hela grupper.

![](assets/4.png)

`4)` Ställ in regler för Buyer Attribution Touchpoints om du vill att de ska tillämpas på båda objekten. Tack vare vår flexibilitet kan du ange regler för ett eller båda objekt och du kan välja att ställa in dem för båda om de är tillämpliga.

![](assets/5.png)

Till slut [!UICONTROL Save and Process] era regler. Om du gör många ändringar måste du spara ändringarna under tiden. [!DNL Marketo Measure] tar inte bort dina kontaktytor förrän du klickar
[!UICONTROL **Spara och bearbeta**].

| **Operator** | **Användningsfall** |
|---|---|
| Är lika med | Enskilt värde - exakt matchning |
| Innehåller | Enskilt värde - innehåller värde |
| Matchar alla | Flera värden - exakt matchning |
| Matchar alla (innehåller) | Flera värden - &#42;value&#42;, &#42;värde, &#42;value&#42; |

För kunder som använder Dynamics och som vill ställa in undertryckningsregler baserade på status och/eller statskod krävs följande formatering när regeln konfigureras: `[Object].Statecode` är lika med/inte lika med `[Status Value]`. Om till exempel statskoden i Dynamics har värdet 1 för en kontakt och statusen är Inaktiv och du vill inaktivera alla sådana kontakter, skulle följande format vara felaktigt för din Suppression-regel: Contact.StatusCode är lika med 1. I stället vill du använda följande format - eftersom statskod och status fungerar som ett par, [!DNL Marketo Measure] läser värdet från Status i vår fråga: Contact.StatusCode är lika med Inactive.
