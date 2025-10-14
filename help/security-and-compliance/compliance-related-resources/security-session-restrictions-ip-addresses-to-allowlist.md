---
unique-page-id: 18874706
description: Begränsningar för säkerhetssession - IP-adresser att Tillåtslista till - Marketo Measure - Produktdokumentation
title: Begränsningar för säkerhetssession - IP-adresser som ska Tillåtslista
exl-id: aaf5190f-893c-4872-8d03-93f516e70a59
feature: Tracking
source-git-commit: 8ac315e7c4110d14811e77ef0586bd663ea1f8ab
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 0%

---

# Begränsningar för säkerhetssession: IP-adresser som ska Tillåtslista {#security-session-restrictions-ip-addresses-to-allowlist}

Om det finns [säkerhetsinställningar för sessioner](https://help.salesforce.com/articleView?id=admin_sessions.htm&type=0){target="_blank"} som förhindrar att specifika IP-adresser skickar/hämtar data till din [!DNL Salesforce]-instans behöver vi följande IP-intervall tillåtslista så att [!DNL Marketo Measure] kan skicka data till [!DNL Salesforce]:

* 52.162.84.192 - 52.162.84.207
* 23.100.229.112 - 23.100.229.127
* 20.186.163.0 - 20.186.163.15

Om du vill lägga till [!DNL Marketo Measure] IP-adresser i de betrodda IP-intervallen i Salesforce klickar du på **[!UICONTROL Setup]** > **[!UICONTROL Administration Setup]** > **[!UICONTROL Security Controls]** > **[!UICONTROL Network Access]** > **[!UICONTROL New]**.

![](assets/1.png)
