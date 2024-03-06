---
description: Domänhantering - [!DNL Marketo Measure]
title: Domänhantering
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Domänhantering {#domain-management}

För IMS-aktiverade klientorganisationer som körs [!DNL Marketo Measure] i Experience Cloud-gränssnittet, [!DNL Marketo Measure] har ett gränssnitt som gör att användare kan hantera sina egna domänlistor. [!DNL Marketo Measure] användare måste först verifiera alla domäner som de vill spåra i [Adobe Admin Console](https://adminconsole.adobe.com/). När domänerna har verifierats i Admin Console kan användarna hantera om [!DNL Marketo Measure] använder dessa domäner för att spåra webbplatstrafik.

## Lägga till domäner i Admin Console {#adding-domains-in-admin-console}

IMS-användare med åtkomst till Adobe Admin Console kan lägga till och validera domäner som de äger. Domänvalidering innebär att en DNS-post läggs till för varje domän och att Admin Console kan verifiera posten.

![](assets/domain-management-1.png)

Instruktioner för hur du lägger till domäner finns i [Admin Console dokumentation](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). När en domän har lagts till måste den [länkad till en katalog](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Hantera domäner i [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

När en domän har lagts till i Admin Console, [!DNL Marketo Measure] synkroniserar posten regelbundet till databasen. Den här synkroniseringen sker varje natt, och även varje gång en användare besöker **[!UICONTROL Domains]** sidan i [!DNL Marketo Measure] Gränssnitt. Som standard alla poster som [!DNL Marketo Measure] importer är inaktiverade och klientorganisationen måste aktivera varje domän manuellt.

![](assets/domain-management-2.png)

På **[!UICONTROL Integration]** > **[!UICONTROL Domains]** visas alla domäner som användaren har registrerat i Admin Console tillsammans med deras status. Varje domän kan aktiveras eller inaktiveras. Om en domän är aktiverad [!DNL Marketo Measure] spårning samlar in trafik som kan ses på den domänen. Om en domän är inaktiverad [!DNL Marketo Measure] ignorerar all trafik som kommer från den domänen och skapar inte kontaktytor eller andra data. [!DNL Marketo Measure] bekräftar inaktiveringen av en domän och varnar för eventuella ändringar:

![](assets/domain-management-3.png)

Effekten av att växla en domän är omedelbar, och ändringarna är inte retroaktiva. I framtiden [!DNL Marketo Measure] rensar data från inaktiverade domäner efter en angiven period.

## Status {#statuses}

Statusen för Admin Console kategoriseras enligt följande:

* **VALIDERAD**: Den här domänen verifieras i Admin Console
* **OBEKRÄFTAD**: Den här domänen har inte verifierats fullständigt i Admin Console och är inte tillgänglig för spårning i [!DNL Marketo Measure]
* **OGILTIG**: Den här domänen kan ha upphört att gälla eller tagits bort från Admin Console. Spåra data i [!DNL Marketo Measure] är flaggad för borttagning
* **ÄLDRE**: Den här domänen skapades i [!DNL Marketo Measure] och finns inte i Admin Console

Spårningsstatus kan vara följande:

* **AKTIV**: [!DNL Marketo Measure] tar emot data från den här domänen
* **INAKTIVERAT**: Den här domänen är tillgänglig för spårning, men är inaktiverad
* **OTILLGÄNGLIG**: Den här domänen är inte tillgänglig för spårning eftersom den inte har verifierats

När du hovrar över ett enskilt statusobjekt utlöses ett verktygstips som ytterligare förklarar statusen.

## Vanliga frågor och svar {#faq}

**Vad händer när en domän tas bort i Admin Console?**

När en domän tas bort i Admin Console, [!DNL Marketo Measure] markerar domänen som borttagen. [!DNL Marketo Measure] avbryter direkt spårning av trafik på den här domänen, men tar inte bort tidigare insamlade data.

**Varför kan jag inte aktivera en domän?**

Det finns flera orsaker till varför en domän inte tillåts att väljas på den här sidan. Om domänen inte valideras i Admin Console är den inte tillgänglig i [!DNL Marketo Measure]. Om domänen ägs av en annan Adobe-organisation än den aktuella [!DNL Marketo Measure] som är innehavare kan det vara otillgängligt för val.

**Hur tar jag bort en domän från den här listan?**

Om en domän har &quot;aktiverad&quot;-växeln inaktiverad, [!DNL Marketo Measure] ignorerar det och det tas bort effektivt från [!DNL Marketo Measure]. Ta bort en domän permanent från [!DNL Marketo Measure]måste du inaktivera det i [!DNL Marketo Measure]och sedan ta bort den från Admin Console.
