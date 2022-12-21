---
unique-page-id: 18874706
description: Begränsningar för säkerhetssession - IP-adresser att Tillåtslista - Marketo-mått - Produktdokumentation
title: Begränsningar för säkerhetssession - IP-adresser som ska Tillåtslista
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
source-git-commit: b9d9e3110e87be0d6311c17b0ef76dfad8735a00
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 3%

---

# Begränsningar för säkerhetssession: IP-adresser att Tillåtslista {#security-session-restrictions-ip-addresses-to-allowlist}

Om det finns [Säkerhetsinställningar för session](https://help.salesforce.com/articleView?id=admin_sessions.htm&amp;type=0){target=&quot;_blank&quot;} på plats, vilket förhindrar att specifika IP-adresser skickar/hämtar data till din [!DNL Salesforce] Vi behöver till exempel följande IP-intervall tillåtslista för att tillåta [!DNL Marketo Measure] att skicka data till [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Lägg till [!DNL Marketo Measure] IP-adresser till de betrodda IP-intervallen i Salesforce klickar du **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
