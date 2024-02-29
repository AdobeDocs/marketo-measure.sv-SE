---
unique-page-id: 27656441
description: Vanliga frågor om integrering av drivrutiner - [!DNL Marketo Measure]
title: Vanliga frågor om integrering av drivrutiner
exl-id: ae5706b1-1f6c-4201-8585-0d7c587746e1
feature: Integration
source-git-commit: 741ab20845de2f3bcde589291d7446a5b4f877d8
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Vanliga frågor om integrering av drivrutiner {#drift-integration-faq}

Som en del av [!DNL Marketo Measure] integration med Drift, här är några av de vanligaste frågorna. Om det finns frågor som inte beskrivs nedan kan du kontakta kontoteamet (din kontoansvarige) på Adobe eller [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.

**Hur är integreringen aktiverad?**

Håll reda på chatt för [!DNL Marketo Measure] är aktiverat som standard. Om du vill inaktivera det (och inte skapa kontaktpunkter från chatt med drivrutiner som standard) lägger du till ytterligare ett attribut i [!DNL Marketo Measure] Javascript-implementering, fet nedan:

`<script type="text/javascript" src="https://cdn.bizible.com/scripts/bizible.js" async="" id="bizible-settings" data-chatEnabled="false"></script>`

För dem som använder [!DNL Google Tag Manager] för att läsa in [!DNL Marketo Measure] Om du vill utesluta dina chattar från att vara Touchpoint-kompatibla lägger du till följande `<span>` direkt efter [!DNL Marketo Measure] Skript:

`<span id="bizible-settings" data-chatEnabled="false"></span>`

**Vad gör integreringen?**

Integreringen tillåter nu [!DNL Marketo Measure] för att spåra när en slutanvändare anger sin e-postadress i en snabbchatt. Därifrån skapar vi kontaktytor utifrån dessa interaktioner med kontaktytan &quot;Webbchatt&quot;. Tack vare den här integreringen kan marknadsförarna förstå hur deras chattinteraktioner fungerar, tillsammans med de kanaler/underkanaler/kampanjer som får människor att interagera med chattarna.

**Vad händer om jag spårar Drift via kampanjsynkroniseringsregler?**

Om det finns några regler för kampanjsynkronisering för att skapa kontaktytor för chattinteraktioner med drivrutiner ska du se till att du inte lägger till dessa specifika slutanvändare i motsvarande CRM-kampanj. När funktionsbiten är aktiverad kan du annars skapa en CRM Campaign-kontaktyta och en digital kontaktyta för en enda Drift-chattinteraktion.

**Vad händer om jag spårar drivrutiner via CRM-kampanjer?**

Om det finns CRM-kampanjer på plats för att skapa kontaktytor för interaktion med drift-chatt måste slutdatumet för kontaktytan anges för dessa specifika kampanjer (slutdatumet för kontaktytan ska vara det datum då funktionen för Web Chat-integrering aktiveras).

**Vad händer om jag spårar Drift via aktiviteter?**

Om det finns aktivitetsregler för att skapa kontaktytor för interaktion med drift-chatt måste ytterligare en logik läggas till i reglerna. Lägg till logik med fältet Aktivitetens skapad den för att förhindra att dubbletter av kontaktytor skapas (IE CrmTask.CreatedDate är mindre än det datum då funktionsbiten aktiverades). Se skärmbilden nedan.

![](assets/activity-rule-drift.png)
