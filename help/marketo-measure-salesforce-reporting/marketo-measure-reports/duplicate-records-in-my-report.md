---
unique-page-id: 18874634
description: Duplicera poster i min rapport - [!DNL Marketo Measure]
title: Duplicera poster i min rapport
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
feature: Reporting
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Duplicera poster i min rapport {#duplicate-records-in-my-report}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i dokumentationen, men fortfarande se &quot;[!DNL Bizible]&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När du glider in i [!DNL Marketo Measure] Rapporter i [!DNL Salesforce]kan du börja hitta dubblettposter i dina rapporter. Du kommer antagligen att uppleva den här känslan när du granskar [!DNL Marketo Measure] färdiga rapporter.

När du rapporterar till Buyer Touchpoints-objektet eller Buyer Attribution Touchpoint-objektet är det viktigt att förstå att du inte längre rapporterar antalet leads, kontakter eller affärsmöjligheter, utan i stället rapporterar du antalet Buyer Touchpoints eller Buyer Attribution Touchpoints som är kopplade till dessa standardobjekt (leads, kontakter, affärsmöjligheter).

Låt oss ta följande rapport som exempel:

Det här är en **Kontakter med Buyer Touchpoints** rapport. Återigen innebär det att vi tittar på antalet kontaktytor som är kopplade till en enskild kontakt.

![](assets/1.gif)

Som du ser ser ser det ut som om det finns tre James Williams-kontakter i rapporten, och därför kanske du tänker &quot;dubbletter!&quot;

Den här rapporten visar dock antalet kontaktytor som rör James. I rapporten ser du att James har en enskild FT (First Touch), en enskild LC, Form (Lead Creation Touch) och en PostLC-kontaktyta (en formulärinlämning som sker efter LC-kontaktytan).

Om du vill förstå antalet kontakter kan du sedan använda fälten Antal - första beröring, Antal - Lead - Skapa Touch eller Antal - U-Shaped för att förstå hur många kontakter som har haft marknadsföringsinteraktioner.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Universitet: Stock SFDC-rapporter](https://universityonline.marketo.com/courses/bizible-fundamentals-bizible-102/#/page/5c5cb68dfb384d0c9fb96cc4)
