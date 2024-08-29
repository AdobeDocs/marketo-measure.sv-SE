---
description: Lär dig hur du hanterar fel i CRM-exporter
title: Felhantering för CRM-export
feature: Salesforce
source-git-commit: 8fa33a363b9e853dd074848032e1810b72fe169c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Felhantering för CRM-export

Inställningen Pausa vid exportfel finns under **Mitt konto** > **Inställningar** > **CRM** > **Allmänt**. Den här funktionen är bara synlig om du har aktiverat funktionen Exportera till CRM. Du kan styra om CRM-exportjobb ska pausa när ett fel på postnivå påträffas.

När den här funktionen är aktiverad upphör exportjobbet att bearbetas och finns kvar på den post där felet inträffade, tills problemet är löst. Felen beror vanligtvis på att behörigheter saknas, att anpassade valideringsregler har tillämpats felaktigt eller att arbetsflöden/utlösare inte fungerar som de ska. Jobbet kommer att fortsätta att köras som schemalagt och kommer automatiskt att försöka exportera den misslyckade posten igen tills det lyckas.

Om du väljer att inaktivera den här funktionen visas ett varningsmeddelande som informerar dig om att detta kan leda till inkonsekvenser i data. Det är ditt ansvar att ta itu med eventuella problem som kan uppstå till följd av dessa inkonsekvenser.

I båda fallen, oavsett om funktionen är aktiverad eller inaktiverad, loggas alla fel på postnivå i tabellen `ExportErrors` och `CRMExport_ExportError`-jobbet försöker automatiskt återexportera dessa poster varje dag. På så sätt elimineras behovet av en supportförfrågan om att starta en ny export, eftersom detta sker automatiskt utan något ingripande från utvecklaren.

Varför krävs det att jobbet avbryts med tanke på funktionen `ExportErrors`? Genom att avbryta de vanliga CRM-exportjobben vid en viss post blir felsökningen mycket enklare. Det gör att du kan köra jobb lokalt och förhindra att ett potentiellt stort antal ExportErrors skapas, som måste hämtas och bearbetas under återexporten.

Den här funktionen kan aktiveras och inaktiveras beroende på vilket beteende du föredrar. Om du till exempel råkar ut för en särskilt svår felkod och föredrar att ta emot&quot;ofullständiga&quot; data tillfälligt, kan du inaktivera funktionen. När problemet är löst kan du aktivera funktionen igen för att säkerställa att framtida exporter är fullständiga och korrekta.
