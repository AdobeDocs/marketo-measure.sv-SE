---
description: Exkluderar [!DNL Marketo Measure] från specifik Forms - [!DNL Marketo Measure]
title: Exkluderar [!DNL Marketo Measure] från specifika Forms
exl-id: ce39a3b2-2ac6-4385-b6d1-3c36b51c03fa
feature: Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Exkluderar [!DNL Marketo Measure] från specifik Forms {#excluding-marketo-measure-from-specific-forms}

Som standard kopplas [!DNL Marketo Measure] till alla formulär på din webbplats. Alla inskickade formulär bör dock inte nödvändigtvis spåras eller inkluderas i en attribueringsmodell. Det beror på att inte alla formulärfyllningar anses vara&quot;bra&quot;. Ett exempel på detta är en sida/ett formulär för att avbryta prenumerationen. Dessutom spåras vanligtvis inte inloggningsformulär eftersom det skulle resultera i en utspädning av attribueringsmodellen.

## Så här lägger du till [!DNL Marketo Measure]-exkluderingskod:  {#how-to-add-marketo-measure-exclude-code}

Om du vill förhindra att [!DNL Marketo Measure] spårar specifika formulär lägger du bara till [!DNL Bizible-Exclude] som en klass i formuläret. Koden är följande:

`<form id="myForm" action="/Home/TestPage" method="POST" class="Bizible-Exclude">`
