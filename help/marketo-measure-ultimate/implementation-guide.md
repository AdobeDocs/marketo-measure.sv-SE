---
description: '[!DNL Marketo Measure] Implementeringshandbok för Ultimate - [!DNL Marketo Measure]'
title: Implementeringshandbok för [!DNL Marketo Measure] Ultimate
feature: Integration, Tracking, Attribution
exl-id: 0c707875-5d05-49b9-b1ff-c3f7b711ebd1
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---


# Implementeringshandbok för [!DNL Marketo Measure] Ultimate {#marketo-measure-ultimate-implementation-guide}

Den här artikeln är en implementeringshandbok för Marketo Measure Ultimate som innehåller tydliga steg och insikter för att säkerställa en lyckad integrering och användning.

## De viktigaste skillnaderna vid användning av Ultimate jämfört med standardnivåer {#main-differences-when-using-ultimate-over-standard-tiers}

Importera B2B-data via AEP: Marknadsförarna förväntas hämta B2B-data (till exempel konto, säljprojekt, kontakt, lead, kampanj, kampanjmedlem, aktivitet) via AEP. Hämta in alla data för attribuering genom att hämta in data från nästan vilken datakälla som helst och från flera datakällor av samma typ.

* Använd med nästan alla CRM-system, inte bara Salesforce och Dynamics.
* Koppla ihop flera CRM-instanser och/eller MAP-instanser till en Marketo Measure-instans.
* Hämta in registrerings- och deltagardata för webbinarium från tredje part.

De direkta CRM- och Marketo Engage-anslutningarna är inte längre tillgängliga för Ultimate.

* Ultimate skickar inte tillbaka data till CRM. Kunder kan förbruka data från datalagret.
* Marknadsförarna fortsätter att föra in data från annonsplattformen via direktanslutningar och spåra webbaktiviteter via Marketo Measure javascript.

Ultimate-användare etableras som AEP. Om de redan har AEP kommer vi inte att ometablera en ny instans.

* AEP-versionen innehåller alla källanslutningar, schemadatamodellering, datauppsättningar, ad hoc-frågetjänst och ett mål endast för Marketo Measure.

Läs mer om [Marketo Measure Ultimate](/help/marketo-measure-ultimate/overview.md){target="_blank"}.

## Scheman och datauppsättningar {#schemas-and-datasets}

>[!NOTE]
>Kolla in [Byggblock för ett schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en#building-blocks-of-a-schema){target="_blank"} om du vill ha en översikt över scheman, klasser och fältgrupper.

**XDM-schema = klass + schemafältgrupp&#42;**

* Obligatoriska fält kan inte ändras. Kunderna kan skapa och lägga till anpassade fält efter behov.
* Exempel på fältnamn baserat på hierarki: accountOrganization.annualRevenue.amount

&#42; _Ett schema består av en klass och noll eller flera schemafältgrupper. Det innebär att du kan skapa ett datauppsättningsschema utan att använda fältgrupper._

![Schemastrukturdiagram som visar klass- och fältgruppsrelationer](assets/marketo-measure-ultimate-implementation-guide-1.png)

[Datauppsättningsöversikt](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html){target="_blank"}: Alla data som har importerats till AEP lagras i Data Lake som datauppsättningar. En datauppsättning är en lagrings- och hanteringskonstruktion för en datamängd, vanligtvis en tabell, som innehåller ett schema (kolumner) och fält (rader).

## Skapa ett schema {#creating-a-schema}

Vi rekommenderar att du använder ett autogenereringsverktyg för att skapa tio standardscheman för B2B.

* Steg för att hämta och konfigurera verktyget [finns här](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces.html#set-up-b2b-namespaces-and-schema-auto-generation-utility){target="_blank"}.

För dem med ett _**CDP-berättigande**_: Skapa scheman genom att gå till sidan Källor.

* Välj Lägg till data > Använd mallar från en källa

![Källsida med alternativen Lägg till data och Använd mallar](assets/marketo-measure-ultimate-implementation-guide-2.png)

* Välj ett konto och alla B2B-mallar för att skapa tio standardscheman för B2B.

![Mallval som visar B2B-schemamallar för kontokonfiguration](assets/marketo-measure-ultimate-implementation-guide-3.png)

## Dataflöden {#dataflows}

>[!IMPORTANT]
>När du lägger till en ny datauppsättning rekommenderar vi att du skapar ett flöde i stället för att använda en befintlig.

[Dataflöden - översikt](https://experienceleague.adobe.com/docs/experience-platform/dataflows/home.html){target="_blank"}

**Steg för att skapa ett dataflöde:**

1. Välj en Source.
1. Välj ett befintligt konto eller skapa ett konto.
1. Välj en datatyp i listan med tillgängliga typer att importera från Source.
1. Välj en befintlig datauppsättning eller skapa en datauppsättning.
1. Mappa fälten från Source till schemat.

   >[!NOTE]
   > Om du mappar en schematyp till en annan, görs det automatiskt.
   > Du kan också importera mappning från ett annat flöde i systemet.
   > Du kan mappa ett Source-fält till flera målfält, men inte tvärtom.
   > Du kan skapa beräknade fält ([Förmappningsfunktioner för dataprep](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html){target="_blank"}).

   >[!CAUTION]
   > Du kan redigera ett dataflöde, men data fylls inte i i efterhand när en mappning ändras.
   > Om ett obligatoriskt fält är NULL, avvisas hela flödet.

   >[!NOTE]
   >[Marketo Measure Ultimate dataintegritetskrav](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}

1. Ange en datainläsningskadens.
1. Granska och slutför.
1. Gå till sidan Kontostatus i Inställningar för måttanvändargränssnitt för att se dataflödesstatus.

**Övervakning:**

Källor > Dataflöden för att kontrollera dataflödenas status

* Om du vill visa aktivitetsinformation för en datauppsättning klickar du bara på datauppsättningen.
* Om du vill visa dataflödesfel markerar du ett dataflöde, väljer ett dataflöde och klickar på Förhandsgranska feldiagnostik.

## Datainspektion {#data-inspection}

Alternativ 1: Om du vill köra frågor direkt från användargränssnittet går du till fliken Frågor under Datahantering.

![Fliken Frågor i Datahantering visar frågegränssnittet](assets/marketo-measure-ultimate-implementation-guide-4.png)

Alternativ 2: [Hämta och använd PSQL](https://experienceleague.adobe.com/docs/experience-platform/query/clients/psql.html){target="_blank"} (snabbare och mer tillförlitligt).

## Aktivera datauppsättning för Marketo Measure {#activate-dataset-for-marketo-measure}

Innan du börjar går du till avsnittet&quot;Experience Platform > Sandlådemappning&quot; i inställningarna för måttgränssnittet och mappar en sandlåda.

>[!CAUTION]
>Det här kan inte ändras när du väl har valt det.

1. I AEP går du till Destinationer > Marketo Measure-sida för att exportera datauppsättningar.
1. Konfigurera mål.
1. Aktivera datauppsättning.
1. Gå till sidan Kontostatus i Inställningar för måttanvändargränssnitt för dataflödesstatus.

>[!NOTE]
> Vi rekommenderar att du bara inkluderar en datauppsättning per dataflöde.
> Data för en given entitet (till exempel Konto) från en viss källa kan bara placeras i en datamängd. Varje datauppsättning kan bara inkluderas i ett dataflöde. Överträdelser stoppar dataflödet vid körning.
> Ta bort hela destinationen i AEP för att ta bort data i Mått. Om du inaktiverar stoppas export av nya data och gamla data behålls.
> Måttkonfigurationen ser oftast likadan ut, men vissa delar, som Stage Mapping, ser annorlunda ut.
> Det tar några timmar för ett nytt dataflöde att generera en flödeskörning och sedan inträffar de med regelbundna timintervall.

I Mått måste standardvalutan anges i avsnittet Valuta.

* Om du använder flera valutor måste valutakonverteringsschemat fyllas i i AEP för att vi ska kunna läsa och använda för konverteringar.

**Stage Mapping:**

Vi importerar inte automatiskt faser från användardata, så alla faser måste mappas manuellt.

* Användare kan mappa faser från olika källor.

![Gränssnittet för scenmappning visar scenkonfigurationen från flera källor](assets/marketo-measure-ultimate-implementation-guide-5.png)

Om faserna inte mappas kommer systemet inte att fungera eftersom det inte kommer att finnas någon plats för data.

Om du använder Marketo Measure Ultimate och har angett ditt standardinstrumentpanelsobjekt som kontakt ska du inte använda de två fält nedan som är specifika för lead ([läs mer här](/help/marketo-measure-ultimate/data-integrity-requirement.md){target="_blank"}).

* b2b.personStatus
* b2b.isConverted

**Kampanjmedlemsregler:**

Välj en datauppsättning och ange regler för varje.

**Regler för upplevelsehändelser:**

Välj en datauppsättning och välj aktivitetstyper.

* Anpassade aktiviteter stöds inte ännu.
* Om kunden har aktiviteter som inte passar de tillgängliga alternativen föreslår vi att de kategoriseras som&quot;Intressanta stunder&quot; och att anpassade fält används för att skilja dem åt.

**Offlinekanaler:**

* Vi gör inte datauppsättningsspecifika kanalmappningsregler, så det skulle vara globalt.
* Vi måste matcha både CRM Campaign-typen och Channel till slut, men för tillfället kan vi mappa kanalnamnet till båda fälten som en tillfällig lösning.
* **Kanalregler: Data som inte har fyllts i har inga scenövergångsdata.**

Inställningarna för slutpunkt och segment ändras inte.
