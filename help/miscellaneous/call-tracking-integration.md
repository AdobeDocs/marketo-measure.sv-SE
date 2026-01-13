---
description: Samtalsspårningsintegrering - [!DNL Marketo Measure]
title: Samtalsspårningsintegrering
exl-id: bc35a789-e056-4456-9038-306ed34c2a8e
feature: Tracking, Integration
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Samtalsspårningsintegrering {#call-tracking-integration}

Vår integrering med [!DNL CallTrackingMetrics] är avsedd att sammanfoga en webbsession med ett telefonsamtal. Ett telefonsamtal behandlas som en formulärsändning till [!DNL Marketo Measure]. Det är ett erkännande till en webbsession som annars bara skulle ha betraktats som ett webbbesök eftersom det inte fanns någon faktisk formulärinlämning.

## Anropsspårning förklaras {#call-tracking-explained}

&quot;Anropsspårning&quot; är i allmänhet en produkt från företag som [!DNL CallTrackingMetrics], [!DNL DiaglogTech], [!DNL Invoca] eller [!DNL CallRail], för att nämna några. Unika telefonnummer visas för användarna baserat på de olika marknadsföringskanalerna eller kampanjerna som de kommer från. På så sätt kan marknadsförarna se hur dessa kanaler eller kampanjer fungerar.

![Diagram som visar unika telefonnummer baserade på olika marknadsföringskanaler och kampanjer](assets/1.png)

## Före och efter {#before-and-after}

Titta i flödesdiagrammet nedan för att se hur [!DNL Marketo Measure] används för att hantera telefonsamtal utan integrering med CallTrackingMetrics. Telefonsamtalet som ägde rum spårades inte, så det betraktades som en webbsession och ingen kontaktyta skapades för det. Det var inte förrän vid nästa besök där användaren fyllde i ett formulär som en kontaktyta till slut fylldes i.

Med integreringen ser du att webbsessionen faktiskt var knuten till ett telefonsamtal. Nästa formulärfyllning blir en PostLC-kontakt och spåras fortfarande som en del av resan.

![Före och efter flödesdiagram som jämför telefonsamtalsspårning utan och med CallTrackingMetrics-integrering](assets/2.png)

## Så här fungerar det {#how-it-works}

CallTrackingMetrics måste göra lite utvecklingsarbete för att detta ska fungera. Med den JavaScript som de placerar på din webbplats kan CallTrackingMetrics hämta _biz_uid från [!DNL Marketo Measure]-cookien. [!DNL BizibleId] lagras sedan av CallTrackingMetrics.

När en besökare kommer till din webbplats och ringer ett telefonsamtal är det CallTrackingMetrics uppgift att överföra dessa data till [!DNL Salesforce].  Vanligtvis skapas en [!DNL Salesforce Task] som fyller i data som telefonnummer, ämne, typ och nu [!DNL BizibleId]

[!DNL BizibleId] är ett fält som installeras med version 6.7+ av paketet [!DNL Marketo Measure] Marketing Attribution.

Nedan visas ett exempel på en Task-post med [!DNL BizibleId] ifylld.

![Exempel på Salesforce-uppgiftspost som visar fältet BizibleId ifyllt med värdet ](assets/3.png)

När [!DNL Marketo Measure] hittar en Task-post med ett känt [!DNL BizibleId]-värde ifyllt kan [!DNL Marketo Measure] mappa användaren till en webbsession med samma [!DNL BizibleId] och tilldela sessionen till ett telefonsamtal i stället för ett webbbesök.

## Touchpoint {#the-touchpoint}

När [!DNL Marketo Measure] kan importera/hämta aktiviteten bearbetar vi den informationen tillsammans med webbsessionen. Vanligtvis kan den sammanfogas med en hänvisare eller annons. I exemplet nedan hittade en besökare verksamheten via en betald Google-annons och gjorde ett telefonsamtal.

[!UICONTROL Touchpoint]-typen &quot;Call&quot; hämtas från aktiviteten från skärmbilden ovan, som också fylls i av CallTrackingMetrics när aktiviteten skapas.

![Touchpoint-post som visar Type as Call från sammanfogade webbsessioner och telefonsamtalsdata](assets/4.png)

## Rapportering {#reporting}

Touchpoint-typvärden som [!DNL Marketo Measure] vanligtvis skickar är Web Visit, Web Form eller Web Chat, men i fråga om CallTrackingMetrics-kontaktytor är kontakttypen Phone Call. Detta hjälper marknadsförarna att se vilka kanaler som utnyttjar de flesta telefonsamtal och generera intäkter för organisationen.

![Rapport med kontaktpunktstyper inklusive telefonsamtal för att spåra anropsgenererade intäkter per kanal](assets/5.png)

## Vanliga frågor och svar {#faq}

**Varför besöker jag min kontakttyp via webben?**

Touchpoint-typen fylls i från fältet Task.Type. Om fältet Task.Type är tomt kommer [!DNL Marketo Measure] automatiskt att ange Touchpoint Type som Web Visit. När fältet Task.Type har fyllts i läser [!DNL Marketo Measure] det värdet och fyller i Touchpoint-typen därefter.

**Vilka andra fält fyller kontaktpunkten i från telefonsamtalet?**

Både Touchpoint Type och Medium innehåller data som hämtas från Task.Type. Alla andra datapunkter hämtas från webbspårning och javascript-data.

**Varför är det här telefonsamtalet inte knutet till en webbsession?**

Kontrollera först aktiviteten och se till att det finns en [!DNL BizibleId] ifylld. Om det inte finns något värde kan vi inte skapa en kontaktyta för den. Detta måste eskaleras med CallTrackingMetrics.

Om det finns ett värde bör du tänka på att alla webbsessioner bara ska vara 30 minuter. Om någon av Google-annonserna klickades på :17pm (början av sessionen på webbplatsen), men telefonsamtalet inte ägde rum förrän :05pm, sammanfogas inte webbsessionen och telefonsamtalet. I stället skapar [!DNL Marketo Measure] en separat [!DNL Salesforce Task]-kontaktyta för att spåra telefonsamtalet, men har inga webbsessionsdata.

![Diagram över 30-minuters tidsgräns för webbsessioner mellan annons- och telefonsamtal](assets/6.png)

## Partnerskap {#partnerships}

[!DNL Marketo Measure] har för närvarande en officiell partner för samtalsspårning som har gått igenom den&quot;officiella&quot; integreringsprocessen med oss, som omfattar sammarknadsföring och produktutbildning. Den här partnern är CallTrackingMetrics.
