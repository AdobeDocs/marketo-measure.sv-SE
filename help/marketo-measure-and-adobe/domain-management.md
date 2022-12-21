---
description: Domänhantering - [!DNL Marketo Measure] - Produktdokumentation
title: Domänhantering
exl-id: 4db287a0-0267-463c-a359-266b41f15c59
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Domänhantering {#domain-management}

För IMS-aktiverade klientorganisationer som körs [!DNL Marketo Measure] i det enhetliga skalet, [!DNL Marketo Measure] har ett gränssnitt som gör att användare kan hantera sina egna domänlistor. [!DNL Marketo Measure] användare måste först verifiera alla domäner de vill spåra i [Adobe Admin Console](https://adminconsole.adobe.com/). När domänerna har verifierats i Admin Console kan användarna hantera om [!DNL Marketo Measure] använder dessa domäner för att spåra webbplatstrafik.

## Lägga till domäner i Admin Console {#adding-domains-in-admin-console}

IMS-användare med åtkomst till Adobe Admin Console kan lägga till och validera domäner som de äger. Domänvalidering innebär att en DNS-post läggs till för varje domän och att Admin Console sedan kan verifiera posten.

![](assets/domain-management-1.png)

Instruktioner för hur du lägger till domäner finns i [Admin Console dokumentation](https://helpx.adobe.com/enterprise/using/set-up-identity.html#setup-domains). När en domän har lagts till måste den [länkad till en katalog](https://helpx.adobe.com/enterprise/using/set-up-identity.html#link-domains-to-directories).

## Hantera domäner i [!DNL Marketo Measure] {#managing-domains-in-marketo-measure}

När en domän har lagts till i Admin Console, [!DNL Marketo Measure] kommer att synkronisera den här posten med vår databas regelbundet. Den här synkroniseringen sker varje natt, och även varje gång en användare besöker **[!UICONTROL Domains]** sidan i [!DNL Marketo Measure] Gränssnitt. Som standard alla poster som [!DNL Marketo Measure] importer inaktiveras och klientorganisationen måste manuellt aktivera varje domän.

![](assets/domain-management-2.png)

På **[!UICONTROL Integration]** > **[!UICONTROL Domains]** visas alla domäner som användaren har registrerat i Admin Console tillsammans med deras status. Varje domän kan aktiveras eller inaktiveras. Om en domän är aktiverad [!DNL Marketo Measure] spårning samlar in trafik som kan ses på den domänen. Om en domän är inaktiverad [!DNL Marketo Measure] kommer att ignorera all trafik som kommer från den domänen och inte skapa kontaktytor eller andra data. [!DNL Marketo Measure] bekräftar även inaktiveringen av en domän och varnar för förvrängningarna:

![](assets/domain-management-3.png)

Effekten av att växla en domän är omedelbar och ändringarna är inte retroaktiva. I framtiden [!DNL Marketo Measure] rensar data från inaktiverade domäner efter en angiven tidsperiod.

## Status {#statuses}

Statusen för Admin Console kategoriseras enligt följande:

* **VALIDERAD**: Den här domänen verifieras i Admin Console
* **OBEKRÄFTAD**: Den här domänen har inte verifierats fullständigt i Admin Console och är inte tillgänglig för spårning i [!DNL Marketo Measure]
* **OGILTIG**: Den här domänen kan ha upphört att gälla eller tagits bort från Admin Console. Spåra data i [!DNL Marketo Measure] är flaggad för borttagning
* **ÄLDRE**: Den här domänen skapades i [!DNL Marketo Measure] och finns inte i Admin Console

Spårningsstatus kan vara följande:

* **AKTIV**: [!DNL Marketo Measure] tar för närvarande emot data från den här domänen
* **INAKTIVERAT**: Den här domänen är tillgänglig för spårning, men är för närvarande inaktiverad
* **OTILLGÄNGLIG**: Domänen är inte tillgänglig för spårning eftersom den inte har verifierats

Om du hovrar över ett enskilt statusobjekt utlöses ett verktygstips som ytterligare förklarar statusen.

## Vanliga frågor {#faq}

**Vad händer när en domän tas bort i Admin Console?**

När en domän tas bort i Admin Console [!DNL Marketo Measure] markerar domänen som borttagen. [!DNL Marketo Measure] kommer omedelbart att sluta spåra trafik på den här domänen, men kommer inte att ta bort tidigare insamlade data.

**Varför kan jag inte aktivera en domän?**

Det finns flera orsaker till varför en domän inte kan väljas på den här sidan. Om domänen inte valideras i Admin Console är den inte tillgänglig i [!DNL Marketo Measure]. Om domänen ägs av en annan Adobe-organisation än den aktuella [!DNL Marketo Measure] som är innehavare kan det vara otillgängligt för markering.

**Hur tar jag bort en domän från den här listan?**

Om en domän har &quot;aktiverad&quot;-växeln inaktiverad, [!DNL Marketo Measure] ignorerar det och tas bort effektivt från [!DNL Marketo Measure]. Ta bort en domän permanent från [!DNL Marketo Measure]måste du inaktivera det i [!DNL Marketo Measure]och därefter ta bort det från Admin Console.
