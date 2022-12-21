---
unique-page-id: 27656441
description: Vanliga frågor om integrering av drivrutiner - [!DNL Marketo Measure] - Produktdokumentation
title: Vanliga frågor om integrering av drivrutiner
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Vanliga frågor om integrering av drivrutiner {#drift-integration-faq}

Som en del av [!DNL Marketo Measure] integrering med Drift har vi skissat upp några av de vanligaste frågorna. Om det finns frågor som inte beskrivs nedan kontaktar du din Customer Success Manager eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.

**Hur är integreringen aktiverad?**

Håll reda på chatt för [!DNL Marketo Measure] är aktiverat som standard. Om du av någon anledning vill inaktivera den (och inte skapa kontaktpunkter från chatt med drivrutiner som standard) behöver vi ett extra attribut till din [!DNL Marketo Measure] Javascript-implementering, fet nedan:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

För dem som använder [!DNL Google Tag Manager] för att läsa in [!DNL Marketo Measure] Om du vill utesluta dina chattar från att vara berättigande för pekpunkter måste du lägga till följande `<span>` direkt efter [!DNL Marketo Measure] Skript:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Vad gör integreringen?**

Integreringen tillåter nu [!DNL Marketo Measure] för att spåra när en slutanvändare anger sin e-postadress i en chatt med drivrutiner. Därifrån skapar vi kontaktytor utifrån dessa interaktioner med kontaktytan &quot;Webbchatt&quot;. Tack vare den här integreringen kan marknadsförarna förstå hur deras chattinteraktioner fungerar, tillsammans med de kanaler/underkanaler/kampanjer som får människor att interagera med chattarna.

**Vad händer om jag spårar Drift via kampanjsynkroniseringsregler?**

Om det finns några regler för kampanjsynkronisering för att skapa kontaktytor för chattinteraktioner med drivrutiner måste du se till att du inte längre lägger till dessa specifika slutanvändare i motsvarande CRM-kampanj. Annars skapar vi en CRM Campaign-kontaktyta och en digital kontaktyta för en enda interaktion med drift-chatt när funktionsbiten är aktiverad.

**Vad händer om jag spårar drivrutiner via CRM-kampanjer?**

Om det finns CRM-kampanjer på plats för att skapa kontaktytor för interaktion med drift-chatt måste slutdatumet för kontaktytan anges för dessa specifika kampanjer (slutdatumet för slutdatumet för kontaktytan ska vara det datum då funktionen för Web Chat-integrering aktiveras).

**Vad händer om jag spårar Drift via aktiviteter?**

Om det finns aktivitetsregler för att skapa kontaktytor för interaktion med drift-chatt måste ytterligare en logik läggas till i reglerna. Du måste lägga till logik med fältet Aktivitet skapad den för att förhindra att duplicering av kontaktpunkter skapas (IE CrmTask.CreatedDate är mindre än det datum då funktionsbiten aktiverades). Se skärmbilden nedan.

![](assets/activity-rule-drift.png)
