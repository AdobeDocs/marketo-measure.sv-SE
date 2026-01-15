---
description: Riktlinjer för domänhantering för Marketo Measure-användare
title: Domänhantering
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
feature: Integration, Tracking
hidefromtoc: true
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Domänhantering {#domain-management}

För IMS-aktiverade klientorganisationer som kör [!DNL Marketo Measure] i Experience Cloud-gränssnittet innehåller [!DNL Marketo Measure] ett gränssnitt som gör att användare kan hantera sina egna domänlistor. [!DNL Marketo Measure]-användare måste först verifiera alla domäner som de vill spåra i [Adobe Admin Console](https://adminconsole.adobe.com/). När domäner har verifierats i Admin Console kan användare hantera om [!DNL Marketo Measure] använder dessa domäner för att spåra webbplatstrafiken.

## Lägga till domäner i Admin Console {#adding-domains-in-admin-console}

IMS-användare med åtkomst till Adobe Admin Console kan lägga till och validera domäner som de äger. Domänvalidering innebär att en DNS-post läggs till för varje domän och att Admin Console sedan kan verifiera posten.

![IMS-användare med åtkomst till Adobe Admin Console kan lägga till och](assets/domain-management-4.png)

Instruktioner om hur du lägger till domäner finns i [Admin Console-dokumentationen](https://helpx.adobe.com/se/enterprise/using/add-domains-directories.html). När en domän har lagts till måste den vara [länkad till en katalog](https://helpx.adobe.com/se/enterprise/using/add-domains-directories.html#link-domains-to-directoies).

## Hantera domäner i [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

När en domän har lagts till i Admin Console synkroniserar [!DNL Marketo Measure] den här posten regelbundet till databasen. Den här synkroniseringen sker varje natt, och dessutom varje gång en användare besöker sidan **[!UICONTROL Domains]** i användargränssnittet i [!DNL Marketo Measure]. Som standard är alla poster som [!DNL Marketo Measure] importerar inaktiverade och klientorganisationen måste aktivera varje domän manuellt.

![När en domän har lagts till i Admin Console, Marketo Measure](assets/domain-management-2.png)

På sidan **[!UICONTROL Integration]** > **[!UICONTROL Domains]** ser användaren alla domäner som de har registrerat i Admin Console, tillsammans med deras status. Varje domän kan aktiveras eller inaktiveras. Om en domän är aktiverad samlar [!DNL Marketo Measure]-spårning in trafik som kan ses på den domänen. Om en domän är inaktiverad ignorerar [!DNL Marketo Measure] all trafik som kommer från den domänen och skapar inte kontaktytor eller andra data. [!DNL Marketo Measure] bekräftar inaktiveringen av en domän och varnar för eventuella ändringar:

![På sidan Integreringsdomäner ser användaren alla domäner](assets/domain-management-3.png)

Effekten av att växla en domän är omedelbar, och ändringarna är inte retroaktiva. I framtiden kommer [!DNL Marketo Measure] att rensa data från inaktiverade domäner efter en angiven period.

## Status {#statuses}

Admin Console-status kategoriseras enligt följande:

* **VALIDERAD**: Den här domänen har verifierats i Admin Console
* **UNVERIFIED**: Den här domänen har inte verifierats fullständigt i Admin Console och kan inte spåras i [!DNL Marketo Measure]
* **OGILTIG**: Den här domänen kan ha upphört att gälla eller tagits bort från Admin Console. Spårningsdata i [!DNL Marketo Measure] har flaggats för borttagning
* **ÄLDRE**: Den här domänen skapades i [!DNL Marketo Measure] och finns inte i Admin Console

Spårningsstatus kan vara följande:

* **AKTIVT**: [!DNL Marketo Measure] tar emot data från den här domänen
* **INAKTIVERAD**: Den här domänen är tillgänglig för spårning, men är inaktiverad
* **OTILLGÄNGLIG**: Den här domänen är inte tillgänglig för spårning eftersom den inte har verifierats

När du hovrar över ett enskilt statusobjekt utlöses ett verktygstips som ytterligare förklarar statusen.

## Vanliga frågor och svar {#faq}

**Vad händer när en domän tas bort i Admin Console?**

När en domän tas bort i Admin Console markeras domänen som borttagen av [!DNL Marketo Measure]. [!DNL Marketo Measure] stoppar omedelbart spårningen av trafik på den här domänen, men tar inte bort tidigare insamlade data.

**Varför kan jag inte aktivera en domän?**

Det finns flera orsaker till varför en domän inte tillåts att väljas på den här sidan. Om domänen inte har verifierats i Admin Console är den inte tillgänglig i [!DNL Marketo Measure]. Om domänen ägs av en annan Adobe-organisation än den aktuella [!DNL Marketo Measure]-innehavaren kanske den inte kan väljas.

**Hur tar jag bort en domän från den här listan?**

Om en domän har inaktiverat &quot;aktiverad&quot;-växeln, ignorerar [!DNL Marketo Measure] den och tas bort från [!DNL Marketo Measure]. Om du vill ta bort en domän permanent från [!DNL Marketo Measure] måste du inaktivera den i [!DNL Marketo Measure] och sedan ta bort den från Admin Console.
