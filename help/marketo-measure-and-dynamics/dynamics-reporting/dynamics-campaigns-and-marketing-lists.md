---
unique-page-id: 18874610
description: Dynamics-kampanjer och marknadsföringslistor - [!DNL Marketo Measure] - Produktdokumentation
title: Dynamics-kampanjer och marknadsföringslistor
exl-id: 7b3d4032-5edf-489d-b86b-1e2a5755b258
feature: Microsoft Dynamics
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Dynamics-kampanjer och marknadsföringslistor {#dynamics-campaigns-and-marketing-lists}

>[!NOTE]
>
>Instruktioner som anger &quot;[!DNL Marketo Measure]&quot; i vår dokumentation, men ändå se &quot;Bizible&quot; i CRM. Vi arbetar för att få den uppdaterade versionen och omprofileringen kommer snart att återspeglas i CRM.

## Kampanjer {#campaigns}

Dynamics Campaigns är bra för att spåra offlinemarknadsföringsaktiviteter och inkludera dem i flerkanalsresan. Kampanjer måste relatera till leads eller kontakter och kan antingen samlas i kampanjen via antingen Campaign Responses eller Marketing Lists.

## Kampanjsvar {#campaign-responses}

När leads eller kontakter läggs till direkt i en kampanj anges de som en svarspost för kampanj.

![](assets/1.png)

## Aktivera kontaktpunkter {#enable-touchpoints}

Om du vill inkludera dessa poster i kontaktytan finns det ett fåtal alternativ för vilka typer av kampanjsvar som ska synkroniseras. På Campaign-posten ska det finnas ett anpassat fält från den installerade lösningen med etiketten &quot;[!UICONTROL Enable Buyer Touchpoints].&quot; Om du inte ser detta måste fältet läggas till via Formulärredigeraren.

![](assets/2.png)

Du kan välja att ta med alla poster som har ett kampanjsvar i Campaign, eller bara de som har svaret&quot;Intresserad&quot;, eller som standard, kan du inte inkludera kampanjsvaren alls. Du kan antingen lämna fältet tomt eller välja att exkludera det explicit.

[!DNL Marketo Measure] stöder inte anpassade svarsvärden.

![](assets/3.png)

Det här är lagersvarsvärdena för Campaign-svaret:

![](assets/4.png)

Beroende på vad du har valt är dessa poster nu berättigade till kontaktytor i lead-, kontakt- eller säljprojektsresan. Om de kvalificerar sig visas en kontaktyta för Dynamics Campaign på resan.

En orsak till att ett kampanjsvar kanske inte visas är att en beröringsaktivitet för First Touch och/eller Lead Creation redan har registrerats för Lead/Contact och funktionen PostLC är inaktiverad eller har nått maximalt antal kontaktytor.

## Kontaktpunktsdatum {#touchpoint-date}

Slutpunktsdatumet för en kampanj är vanligtvis det datum då kampanjsvaret lades till i kampanjen. Den kan åsidosättas om det anpassade fältet från den installerade lösningen med etiketten&quot;Buyer Touchpoint Date&quot; (Köparens slutpunktsdatum) fylls i. Om du inte ser detta måste fältet läggas till via Formulärredigeraren.

Ett vanligt exempel som används i det här fältet är för händelser där en lista med badge-sökningar från en händelse läggs till i CRM-dagarna efter att händelsen inträffade, så att användaren faktiskt kan ändra Buyer Touchpoint-datumet tillbaka till när händelsen inträffade.

![](assets/5.png)

## Marknadsföringslistor {#marketing-lists}

Marknadsföringslistor är ett annat sätt att inkludera leads eller kontakter i en marknadsföringsresa. Marknadsföringslistor är unika för en grupp leads eller kontakter, vilket innebär att användaren måste välja om deras lista är en uppsättning leads eller en uppsättning kontakter.

[!DNL Marketo Measure] stöder endast statiska marknadsföringslistor. Vi stöder inte dynamiska marknadsföringslistor eftersom vår bearbetning kräver att vi kontrollerar en posts ändrade datum, men eftersom en dynamisk lista ofta ändras finns det inget ändrat datum för [!DNL Marketo Measure] att kontrollera mot. Detta kräver en konstant nedladdning av hela datauppsättningen under hela dagen.

![](assets/6.png)

Skärmbilden ovan är en marknadsföringslista för leads. Marknadsföringslistor är kopplade till kampanjer och kan associeras med flera kampanjer. Såvida ni inte bara skapar en marknadsföringslista för en kampanj, [!DNL Marketo Measure] rekommenderar inte att kunder använder marknadsföringslistor för att spåra sina kampanjer. Det är osannolikt att samma exakta lista över leads/kontakter skulle vara berättigad till kontaktytor i flera kampanjer.

## Aktivera kontaktpunkter {#enable-touchpoints-1}

Om du vill aktivera en marknadsföringslista för kontaktytor finns det en separat inställning för kampanjposten med etiketten &quot;[!UICONTROL Sync Marketing Lists],&quot; som är en enkel ja/nej-switch. Om du inte ser detta måste fältet läggas till via Formulärredigeraren. På Campaign-posten kan ni se vilka marknadsföringslistor som är relaterade till Campaign så att ni vet hur många listor ni aktiverar.

![](assets/7.png)

## Kontaktpunktsdatum {#touchpoint-date-1}

Slutpunktsdatumet för en marknadsföringslista är vanligtvis det datum då ListMember skapades, så det datum då lead eller kontakt lades till i marknadsföringslistan. Den kan åsidosättas om det anpassade fältet från den installerade lösningen med etiketten&quot;Buyer Touchpoint Date&quot; (Köparens slutpunktsdatum) fylls i. Om du inte ser detta måste fältet läggas till via Formulärredigeraren.

![](assets/8.png)

## Kanalmappning {#channel-mapping}

Dynamics-kampanjer är paketerade i dina anpassade marknadsföringskanaler med hjälp av fältet Campaign-typ. Dessa kan ändras på menyn Dynamics-anpassningar.

Värdena på menyn Campaign-typ hämtas till [!DNL Marketo Measure] Program. **[!UICONTROL My Account]** > **[!UICONTROL Settings]** > **[!UICONTROL Offline Channels]**.

För varje Campaign-typ kan den mappas till en Channel- och Subchannel-kombination så att varje kontaktyta som härleds från Campaign har rätt mappad kanal och subkanal.

![](assets/9.png)

![](assets/10.png)

## Kampanjsynkroniseringsdatum {#campaign-sync-date}

Detta är inte tillgängligt för Dynamics-kunder

## Vanliga frågor {#faq}

**Kan vi aktivera kontaktytor på marknadsföringslistor eller endast kampanjer i Dynamics?**

Du kan aktivera en marknadsföringslista men den måste vara relaterad till en kampanj eftersom alternativet att synkronisera en marknadsföringslista finns i Campaign.

**Kan vi använda kampanjsvar OCH marknadsföringslistor i en kampanj?**

Ja.
