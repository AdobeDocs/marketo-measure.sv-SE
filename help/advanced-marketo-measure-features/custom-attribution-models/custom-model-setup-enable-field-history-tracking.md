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

Om du bestämmer dig för att ta med ett anpassat fält som en fas i din anpassade attribueringsmodell, måste fälthistorikspårning **aktiveras** för det här fältet. Om du aktiverar spårning av fälthistorik kan [!DNL Salesforce] spåra varje gång det anpassade fältet redigeras genom att skapa en post i historikspårningstabellen. [!DNL Marketo Measure] kan hämta tabellen och använda den här informationen för att mäta tiden och dagen då en övergång inträffade. Utan spårning av fälthistorik kan [!DNL Marketo Measure] inte spåra ändringar som är relaterade till det här fältet.

Om bara [!UICONTROL Lead Status] eller säljprojektsstadier används i den anpassade modellen behöver du inte aktivera spårning av fälthistorik eftersom den spåras automatiskt som en scenövergång.

Följ instruktionerna nedan om du vill aktivera spårning av fälthistorik.

## Aktivera spårning av fälthistorik {#enable-field-history-tracking}

>[!NOTE]
>
>Du måste vara systemadministratör för att kunna göra dessa ändringar i fälten på lead-/kontakt-/säljprojektsobjektet.

1. Gå till objektet där det anpassade fältet finns och klicka på knappen **[!UICONTROL Set History Tracking]**.

   ![](assets/1.png)

1. Markera de fält som du vill spåra ändringar i.

   ![](assets/2.png)

[!DNL Marketo Measure] kan bara importera om en post om den ser att posten nyligen har ändrats. Formelfält ändrar tekniskt inte en post när den ändras eftersom den utför beräkningen i bakgrunden. Vi har sett problem där en regel hoppas över eftersom [!DNL Marketo Measure] inte kunde se poständringen, så vi rekommenderar att du **inte använder formelfält i regeldefinitioner**. Lösningen är att skapa ett textfält och använda ett arbetsflöde för att fylla i fältet med rätt värde eller beräkning när posten redigeras eller passar villkoren. Detta kräver att alla poster redigeras så att arbetsflödet kan arbeta retroaktivt på gamla poster.
