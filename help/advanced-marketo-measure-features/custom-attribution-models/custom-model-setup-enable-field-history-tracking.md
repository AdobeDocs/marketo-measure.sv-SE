---
unique-page-id: 18874777
description: Anpassad modellinställning - Aktivera spårning av fälthistorik - [!DNL Marketo Measure]
title: Anpassad modellinställning - Aktivera spårning av fälthistorik
exl-id: 70328e67-051b-4864-891b-b251e49859c2
feature: Custom Models
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Anpassad modellinställning: Aktivera spårning av fälthistorik {#custom-model-setup-enable-field-history-tracking}

## Varför och när spårning av fälthistorik ska aktiveras {#why-and-when-to-enable-field-history-tracking}

Om du bestämmer dig för att ta med ett anpassat fält som en fas i din anpassade attribueringsmodell, spårning av fälthistorik **måste vara aktiverat** för detta fält. Aktivering av spårning av fälthistorik tillåter [!DNL Salesforce] om du vill spåra varje gång det anpassade fältet redigeras genom att skapa en post i historikspårningstabellen. [!DNL Marketo Measure] kan hämta tabellen och använda den här informationen för att mäta när och när en övergång inträffade. Utan fälthistorikspårning [!DNL Marketo Measure] kan inte spåra ändringar som rör det här fältet.

Endast [!UICONTROL Lead Status] Om du använder säljprojektsstadier i den anpassade modellen behöver du inte aktivera spårning av fälthistorik eftersom den spåras automatiskt som en scenövergång.

Följ instruktionerna nedan om du vill aktivera spårning av fälthistorik.

## Aktivera spårning av fälthistorik {#enable-field-history-tracking}

>[!NOTE]
>
>Du måste vara systemadministratör för att kunna göra dessa ändringar i fälten på lead-/kontakt-/säljprojektsobjektet.

1. Gå till objektet där det anpassade fältet finns och klicka på **[!UICONTROL Set History Tracking]** -knappen.

   ![](assets/1.png)

1. Markera de fält som du vill spåra ändringar i.

   ![](assets/2.png)

[!DNL Marketo Measure] kan endast importera om en post om den ser att posten nyligen har ändrats. Formelfält ändrar tekniskt inte en post när den ändras eftersom den utför beräkningen i bakgrunden. Vi har sett problem där en regel hoppas över eftersom [!DNL Marketo Measure] kunde inte se ändringen av posten, så vi rekommenderar att du **använd inte formelfält i regeldefinitioner**. Lösningen är att skapa ett textfält och använda ett arbetsflöde för att fylla i fältet med rätt värde eller beräkning när posten redigeras eller passar villkoren. Detta kräver att alla poster redigeras så att arbetsflödet kan arbeta retroaktivt på gamla poster.
