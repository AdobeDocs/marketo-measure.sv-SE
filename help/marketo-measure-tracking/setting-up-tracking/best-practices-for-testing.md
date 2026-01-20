---
unique-page-id: 18874722
description: Bästa praxis för testning - [!DNL Marketo Measure]
title: Bästa metoder för testning
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
feature: Tracking
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Bästa metoder för testning {#best-practices-for-testing}

Du bör testa alla olika typer av formulär för att se till att JavaScript [!DNL Marketo Measure] fungerar som det ska.

## Rekommenderad testprocess {#recommended-test-process}

1. Använd en inkognitiv webbläsare eller rensa dina cookies mellan varje formulärtest _och_ använder olika e-postadresser varje gång.

   >[!TIP]
   >
   >Ett bra tillvägagångssätt är att använda ett falskt e-postmeddelande som innehåller något som tyder på att det är ett test, liksom tidpunkten på dagen. Till exempel: `testing830am@test.com`.

1. Starta sökningen i en sökmotor (t.ex. `google.com`) eller navigera direkt till ett formulär.

1. Skicka formuläret till din webbplats med en unik e-postadress.

1. Registrera URL-adressen till sidan som du skickar formuläret på och den e-postadress som används.

1. Leta reda på den post som skapats i CRM (lead eller kontakt) för den formuläröverföringen och kontrollera att en kontaktyta skapats på rätt sätt.

>[!NOTE]
>
>Du kan använda en [!DNL Marketo Measure]-stockrapport, till exempel Leads med [!DNL Marketo Measure] Touchpoints, eller titta på sidlayouten Lead/Kontakt om du valde att uppdatera sidlayouten med [!DNL Marketo Measure] information. Detta kan ta en stund innan data kan bearbetas.
