---
unique-page-id: 18874592
description: Samtalsuppföljningsintegrering - [!DNL Marketo Measure] - Produktdokumentation
title: Samtalsspårningsintegrering
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# Samtalsspårningsintegrering {#call-tracking-integration}

Vår integrering med [!DNL CallTrackingMetrics] är avsett att sammanfoga en webbsession med ett telefonsamtal. Ett telefonsamtal behandlas som en formuläröverföring till [!DNL Marketo Measure]. Det är ett erkännande till en webbsession som annars bara skulle ha betraktats som ett webbbesök eftersom det inte fanns någon faktisk formulärinlämning.

## Anropsspårning förklaras {#call-tracking-explained}

&quot;Anropsspårning&quot; är i allmänhet en produkt från företag som [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca], eller [!DNL CallRail], för att nämna några. Unika telefonnummer visas för användarna baserat på de olika marknadsföringskanaler eller kampanjer de kommer från. På så sätt kan marknadsförarna se hur dessa kanaler eller kampanjer fungerar.

![](assets/1.png)

## Före och efter {#before-and-after}

Ta en titt på flödesdiagrammet nedan för att se hur [!DNL Marketo Measure] används för att hantera telefonsamtal utan integrering med CallTrackingMetrics. Telefonsamtalet som ägde rum spårades inte, så det betraktades som en webbsession och ingen kontaktyta skapades för det. Det var inte förrän vid nästa besök där användaren fyllde i ett formulär som en kontaktyta slutligen fylldes i.

Med integreringen ser du att webbsessionen faktiskt var knuten till ett telefonsamtal. Nästa formulärfyllning blir en PostLC-kontakt och spåras fortfarande som en del av resan.

![](assets/2.png)

## Så här fungerar det {#how-it-works}

CallTrackingMetrics måste göra lite utvecklingsarbete för att detta ska fungera. Med det javascript som de placerar på din webbplats kan CallTrackingMetrics hämta _biz_uid från [!DNL Marketo Measure] cookie. Detta &quot;[!DNL BizibleId]&quot; lagras sedan av CallTrackingMetrics.

När en besökare kommer till er webbplats och ringer ett telefonsamtal är det CallTrackingMetrics uppgift att överföra dessa data till [!DNL Salesforce]  Vanligtvis är [!DNL Salesforce Task] skapas som fyller i data som telefonnummer, ämne, typ och nu [!DNL BizibleId]

The [!DNL BizibleId] är ett fält som installeras med version 6.7+ av [!DNL Marketo Measure] Marknadsattribueringspaket.

Nedan visas ett exempel på en Task-post med [!DNL BizibleId] populerad.

![](assets/3.png)

När [!DNL Marketo Measure] söker efter en uppgiftspost med en känd [!DNL BizibleId] värdet är ifyllt, [!DNL Marketo Measure] kan mappa användaren till en webbsession med samma [!DNL BizibleId] och attribuera sessionen till ett telefonsamtal i stället för ett webbbesök.

## Touchpoint {#the-touchpoint}

När [!DNL Marketo Measure] kan importera/hämta uppgiften, bearbetar vi den detaljen tillsammans med webbsessionen. I de flesta fall kan den sammanfogas med en hänvisare eller annons. I exemplet nedan hittade en besökare verksamheten via en betald Google-annons och gjorde ett telefonsamtal.

The [!UICONTROL Touchpoint] Typen&quot;Call&quot; hämtas från aktiviteten från skärmbilden ovan, som även fylls i av CallTrackingMetrics när uppgiften skapas.

![](assets/4.png)

## Rapportering {#reporting}

Touchpoint-typvärden som [!DNL Marketo Measure] Vanligtvis är push-meddelanden Web Visit, Web Form eller Web Chat, men när det gäller CallTrackingMetrics-kontaktytan är det Phone Call som kontakttyp. Detta hjälper marknadsförarna att se vilka kanaler som utnyttjar de flesta telefonsamtal och generera intäkter för organisationen.

![](assets/5.png)

## Vanliga frågor {#faq}

**Varför besöker jag min kontakttyp via webben?**

Touchpoint-typen fylls i från fältet Task.Type. Om fältet Task.Type är tomt [!DNL Marketo Measure] anger automatiskt Touchpoint Type som Web Visit. När fältet Task.Type har fyllts i [!DNL Marketo Measure] läser det värdet och fyller i Touchpoint-typen därefter.

**Vilka andra fält fyller Touchpoint i från telefonsamtalet?**

Både Touchpoint Type och Medium innehåller data som hämtas från Task.Type. Alla andra datapunkter hämtas från webbspårning och javascript-data.

**Varför är det här telefonsamtalet inte knutet till en webbsession?**

Kontrollera först att det finns en [!DNL BizibleId] populerad. Om det inte finns något värde kan vi inte skapa en kontaktyta för den. Detta måste eskaleras med CallTrackingMetrics.

Om det finns ett värde bör du tänka på att alla webbsessioner bara ska vara 30 minuter. Om du klickade på en Google Ad kl. 12.17 (början av sessionen på webbplatsen), men telefonsamtalet inte ägde rum förrän 17.05, sammanfogas inte webbsessionen och telefonsamtalet. I stället för [!DNL Marketo Measure] skapar en separat [!DNL Salesforce Task] kontaktyta för att spåra telefonsamtalet, men har inga webbsessionsdata.

![](assets/6.png)

## Partnerskap {#partnerships}

[!DNL Marketo Measure] för närvarande har en officiell partner för samtalsspårning som har gått igenom den&quot;officiella&quot; integreringsprocessen med oss, som inkluderade sammarknadsföring och produktutbildning. Den här partnern är CallTrackingMetrics.
