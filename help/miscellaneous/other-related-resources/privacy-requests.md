---
description: Sekretessförfrågningar - [!DNL Marketo Measure] - Produktdokumentation
title: Sekretessförfrågningar
exl-id: 883e475f-9868-412a-b505-230556f38484
feature: APIs, Tracking
source-git-commit: a2a7657e8377fd5c556d38f6eb815e39d2b8d15e
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Sekretessförfrågningar {#privacy-requests}

I det här dokumentet finns en översikt över hur du hanterar enskilda sekretessförfrågningar som du kan skicka till [!DNL Marketo Measure] via [!DNL Privacy Service] Användargränssnittet och **[!DNL Privacy Service]API**.

Du kan skicka enskilda förfrågningar för att få åtkomst till och ta bort konsumentdata från [!DNL Marketo Measure] på två sätt:

* Via [[!DNL Privacy Service] UI](https://experienceleague.adobe.com/docs/experience-platform/privacy/ui/overview.html){target="_blank"}.
* Via **[!DNL Privacy Service]API**. Läs dokumentationen [här](https://experienceleague.adobe.com/docs/experience-platform/privacy/api/overview.html){target="_blank"} and the API reference [here](https://developer.adobe.com/experience-platform-apis/references/privacy-service/){target="_blank"}.

The [Privacy Service](https://experienceleague.adobe.com/docs/experience-platform/privacy/home.html){target="_blank"} har stöd för två typer av begäranden: dataåtkomst och borttagning av data.

Låt oss se hur du kan skapa förfrågningar om åtkomst och borttagning.

## Nödvändig konfiguration för att skicka begäranden för Marketo Measure {#required-setup-to-send-requests-for-marketo-measure}

För att göra förfrågningar om åtkomst- och borttagningsdata för [!DNL Marketo Measure]måste du:

1. Identifiera följande:

   a. IMS-organisations-ID

   b. E-postadress till den person du vill agera på

   Ett IMS-organisations-ID är en 24 tecken lång alfanumerisk sträng som läggs till med @AdobeOrg. Om ditt marknadsföringsteam eller den interna systemadministratören i Adobe inte känner till din organisations IMS-organisation kan du kontakta Adobe kundtjänst på gdprsupport@adobe.com. Du behöver IMS-organisations-ID för att kunna skicka begäranden till sekretess-API:t.

1. I [!DNL Privacy Service]kan du skicka in begäranden om åtkomst och borttagning till [!DNL Marketo Measure]och kontrollera status för befintliga förfrågningar.

## Obligatoriska fältvärden i [!DNL Marketo Measure] JSON-begäranden {#required-field-values-in-marketo-measure-json-requests}

&quot;companyContext&quot;:

* &quot;namespace&quot;: **imsOrgID**
* värde: `<Your IMS Org ID Value>`

användare:

* &quot;action&quot;: antingen [!UICONTROL access] eller ta bort
* &quot;användar-ID&quot;:
   * &quot;namespace&quot;: email
   * &quot;type&quot;: standard
   * värde: `<Data Subject's Email Address>`

include:

* **marketoMeasurement** (som är den Adobe-produkt som är tillämplig på ansökan)

reglering:

* **gdpr**, **ccpa**, **pdpa**, **lgpd_bra**, eller **nzpa_nzl** (som är den sekretessregel som gäller för begäran)

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
