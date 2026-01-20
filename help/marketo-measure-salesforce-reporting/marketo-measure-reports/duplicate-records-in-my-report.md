---
unique-page-id: 18874634
description: Duplicera poster i min rapport - [!DNL Marketo Measure]
title: Duplicera poster i min rapport
exl-id: 4ee42371-5b67-4c69-9b49-3249f33614d0
feature: Reporting
source-git-commit: 666812e8bf095170d611cd694b5d0ac5151d8fdd
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Duplicera poster i min rapport {#duplicate-records-in-my-report}

>[!NOTE]
>
>Du kan se instruktioner som anger [!DNL Marketo Measure] i dokumentationen, men ändå se [!DNL Bizible] i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

När du dykar upp i [!DNL Marketo Measure] rapporter i [!DNL Salesforce] kan du börja hitta dubblettposter i dina rapporter. Den här känslan kommer troligen att uppstå när du granskar [!DNL Marketo Measure] färdiga rapporter.

När du rapporterar till Buyer Touchpoints-objektet eller Buyer Attribution Touchpoint-objektet är det viktigt att förstå att du inte längre rapporterar antalet leads, kontakter eller affärsmöjligheter, utan i stället rapporterar du antalet Buyer Touchpoints eller Buyer Attribution Touchpoints som är kopplade till dessa standardobjekt (leads, kontakter, affärsmöjligheter).

Låt oss ta följande rapport som exempel:

Det här är en **Kontakt med Buyer Touchpoints** -rapport. Återigen innebär det att vi tittar på antalet kontaktytor som är kopplade till en enskild kontakt.

![](assets/1.gif)

Som du ser ser ser det ut som om det finns tre James Williams-kontakter i rapporten, och därför kanske du tänker &quot;dubbletter!&quot;

Den här rapporten visar dock antalet kontaktytor som rör James. I rapporten ser du att James har en enskild FT (First Touch), en enskild LC, Form (Lead Creation Touch) och en PostLC-kontaktyta (en formulärinlämning som sker efter LC-kontaktytan).

Om du vill förstå antalet kontakter kan du sedan använda fälten Antal - första beröring, Antal - Lead - Skapa Touch eller Antal - U-Shaped för att förstå hur många kontakter som har haft marknadsföringsinteraktioner.

>[!MORELIKETHIS]
>
>[[!DNL Marketo Measure] Självstudiekurser: Stock SFDC-rapporter](https://experienceleague.adobe.com/en/docs/marketo-measure-learn/tutorials/onboarding/marketo-measure-102/stock-salesforce-reports){target="_blank"}
