---
unique-page-id: 18874783
description: Exklusive [!DNL Marketo Measure] från specifika Forms - [!DNL Marketo Measure]
title: Exklusive [!DNL Marketo Measure] från specifik Forms
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# Exklusive [!DNL Marketo Measure] från specifik Forms {#excluding-marketo-measure-from-specific-forms}

Som standard [!DNL Marketo Measure] bifogar till alla formulär på webbplatsen. Alla inskickade formulär bör dock inte nödvändigtvis spåras eller inkluderas i en attribueringsmodell. Det beror på att inte alla formulärfyllningar anses vara&quot;bra&quot;. Ett exempel på detta är en sida/ett formulär för att avbryta prenumerationen. Dessutom spåras vanligtvis inte inloggningsformulär eftersom det skulle resultera i en utspädning av attribueringsmodellen.

## Lägga till [!DNL Marketo Measure]-exclude Code:  {#how-to-add-marketo-measure-exclude-code}

För att förhindra [!DNL Marketo Measure] från att spåra specifika formulär, lägg bara till &quot;[!DNL Bizible-Exclude]&quot; som en&quot;klass&quot; i formuläret. Koden är följande:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
