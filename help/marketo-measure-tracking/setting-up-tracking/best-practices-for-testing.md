---
unique-page-id: 18874722
description: Best Practices for Testing - [!DNL Marketo Measure] - Produktdokumentation
title: Bästa metoder för testning
exl-id: ff95a1a9-d324-47f5-b47d-39014dff77e4
source-git-commit: 993a326c377b3b6ff48c4e0114b59297f9ca2ca6
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---

# Bästa metoder för testning {#best-practices-for-testing}

Du bör testa alla olika typer av formulär för att säkerställa att [!DNL Marketo Measure] JavaScript fungerar som det ska.

## Rekommenderad testprocess {#recommended-test-process}

1. Använd en inkognitiv webbläsare eller rensa dina cookies mellan varje test av att skicka formulär _och_ använd olika e-postadresser varje gång.

   >[!TIP]
   >
   >Ett bra tillvägagångssätt är att använda ett falskt e-postmeddelande som innehåller något som tyder på att det är ett test, liksom tidpunkten på dagen. Exempel: `testing830am@test.com`.

1. Starta sökningen i en sökmotor (t.ex. `google.com`) eller navigera direkt till ett formulär.

1. Skicka formuläret till din webbplats med en unik e-postadress.

1. Registrera URL-adressen till sidan som du skickar formuläret på och den e-postadress som används.

1. Leta reda på den post som skapats i CRM (lead eller kontakt) för den formuläröverföringen och kontrollera att en kontaktyta skapats på rätt sätt.

>[!NOTE]
>
>Du kan använda en [!DNL Marketo Measure] aktierapport som Leads med [!DNL Marketo Measure] Kontaktpunkter eller titta på sidlayouten Lead/Kontakt om du valde att uppdatera sidlayouten med [!DNL Marketo Measure] information. Detta kan ta en stund innan data kan bearbetas.
