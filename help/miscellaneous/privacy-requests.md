---
description: Sekretessförfrågningar - [!DNL Marketo Measure]
title: Sekretessförfrågningar
exl-id: 883e475f-9868-412a-b505-230556f38484
feature: APIs, Tracking
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---


# Sekretessförfrågningar {#privacy-requests}

Det här dokumentet innehåller en översikt över hur du hanterar enskilda datasekretessbegäranden som du kan skicka till [!DNL Marketo Measure] via [!DNL Privacy Service]-gränssnittet och **[!DNL Privacy Service]-API:t**.

Du kan skicka enskilda förfrågningar för att få åtkomst till och ta bort konsumentdata från [!DNL Marketo Measure] på två sätt:

* Via [[!DNL Privacy Service] gränssnittet](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html?lang=sv-SE){target="_blank"}.
* Via **[!DNL Privacy Service]API**. Se dokumentationen [här](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html?lang=sv-SE){target="_blank"} och API-referensen [här](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

[Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html?lang=sv-SE){target="_blank"} har stöd för två typer av förfrågningar: dataåtkomst och borttagning av data.

Låt oss se hur du kan skapa förfrågningar om åtkomst och borttagning.

## Nödvändig inställning för att skicka begäranden för Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

Om du vill begära åtkomst- och borttagningsdata för [!DNL Marketo Measure] måste du:

1. Identifiera följande:

   a. IMS-organisations-ID

   b. E-postadress till den person du vill agera på

   Ett IMS-organisations-ID är en 24 tecken lång alfanumerisk sträng som läggs till med @AdobeOrg. Om marknadsföringsteamet eller den interna systemadministratören i Adobe inte känner till din organisations IMS-organisation kan du kontakta Adobe kundtjänst på gdprsupport@adobe.com. Du behöver IMS-organisations-ID för att kunna skicka begäranden till sekretess-API:t.

1. I [!DNL Privacy Service] kan du skicka begäranden om åtkomst och borttagning till [!DNL Marketo Measure] och kontrollera status för befintliga begäranden.

## Obligatoriska fältvärden i [!DNL Marketo Measure] JSON-begäranden {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContext&quot;:

* &quot;namespace&quot;: **imsOrgID**
* &quot;value&quot;: `<Your IMS Org ID Value>`

användare:

* &quot;action&quot;: antingen [!UICONTROL access] eller delete
* &quot;användar-ID&quot;:
   * &quot;namespace&quot;: email
   * &quot;type&quot;: standard
   * &quot;value&quot;: `<Data Subject's Email Address>`

include:

* **marketoMeasurement** (som är den Adobe-produkt som gäller för begäran)

reglering:

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra** eller **nzpa_nzl** (som är den sekretessregel som gäller för begäran)

## Exempel ett: GDPR-borttagningsbegäran {#gdpr-delete-request}

JSON-begäran

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "delete"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "gdpr",
}
```

JSON-svar

```text
{
  "requestId": "16331241037112570RX-245",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "997b01e3-9568-402c-904b-b4e60a437875",
      "customer": {
        "user": {
          "action": [
            "delete"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```

## Exempel två: CCPA-åtkomstbegäran {#ccpa-access-request}

JSON-begäran

```text
{
  "companyContexts": [
    {
      "namespace": "imsOrgID",
      "value": "1231659F56A68A8B7F000101@AdobeOrg"
    }
  ],
  "users": [
    {
      "action": [
        "access"
      ],
      "userIDs": [
        {
          "namespace": "email",
          "type": "standard",
          "value": "john.doe@adobe.com"
        }
      ]
    }
  ],
  "include": [
    "marketoMeasure"
  ],
  "regulation": "ccpa",
}
```

JSON-svar

```text
{
  "requestId": "16329573462631890RX-207",
  "totalRecords": 1,
  "jobs": [
    {
      "jobId": "3115e42d-011b-47ab-a2b0-ed4356af4d3e",
      "customer": {
        "user": {
          "action": [
            "access"
          ],
          "userIDs": [
            {
              "namespace": "email",
              "value": "john.doe@adobe.com",
              "type": "standard",
              "namespaceId": 6,
              "isDeletedClientSide": false
            }
          ]
        }
      }
    }
  ]
}
```
