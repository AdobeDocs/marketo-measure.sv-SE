---
description: '[!DNL Marketo Measure] Ultimat dataintegritetskrav - [!DNL Marketo Measure] - Produktdokumentation'
title: '''[!DNL Marketo Measure] Ultimate Data Integrity Required'
feature: Integration, Tracking, Attribution
exl-id: 8ad001d0-e9fe-46f5-b808-d6203a55a229
source-git-commit: 034c4639e6054118052524c457995f4caf7a4bf2
workflow-type: tm+mt
source-wordcount: '1465'
ht-degree: 7%

---

# [!DNL Marketo Measure] Ultimat dataintegritetskrav {#marketo-measure-ultimate-data-integrity-requirement}

[!DNL Marketo Measure] validerar inkommande AEP-datauppsättningar för att säkerställa att data är tillräckliga och konsekventa för ändamålet med attribueringen. Om dataintegritetskravet inte uppfylls kommer datauppsättningen att refuseras av [!DNL Marketo Measure] system. Det här dokumentet innehåller information om dataintegritetskravet, frågeexempel för datainspektion och rekommenderar en lösning för obligatoriska fält med ett null-värde.

## Enhetsobjekt {#entity-object}

<table style="table-layout:auto">
  <tr>
    <th>XDM-klass</th>
    <th>XDM-fältgrupp</th>
    <th>XDM-sökväg</th>
    <th>XDM-typ</th>
    <th>Datakällfält</th>
    <th>Obligatoriskt?</th>
    <th>Anteckningar</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Konto</strong> (Konto för Salesforce, Company och/eller Named Account för Marketo)</td>
    </tr>
    <tr>
      <td rowspan="6">XDM Business Account</td>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>Exempel: - 123</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>XDM Business Account Details</td>
      <td>accountName</td>
      <td>string</td>
      <td>Namn</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Campaign</strong> (Campaign for Salesforce, Program for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="8">XDM Business Campaign</td>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>Exempel: - 55555</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignName</td>
      <td>string</td>
      <td>Namn</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>campaignType</td>
      <td>string</td>
      <td>CampaignType</td>
      <td>Nej</td>
      <td>För kanalmappning</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Information om XDM Business Campaign</td>
      <td>channelName</td>
      <td>string</td>
      <td>ChannelName</td>
      <td>Nej</td>
      <td>För kanalmappning</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignStartDate</td>
      <td>date-time</td>
      <td>StartDate</td>
      <td>Nej</td>
      <td>För kampanjkostnad</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignEndDate</td>
      <td>date-time</td>
      <td>EndDate</td>
      <td>Nej</td>
      <td>För kampanjkostnad</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.amount</td>
      <td>tal</td>
      <td>Kostnad</td>
      <td>Nej</td>
      <td>För kampanjkostnad</td>
    </tr>
    <tr>
      <td></td>
      <td>actualCost.currencyCode</td>
      <td>
        <p>string</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Nej</td>
      <td>För kampanjkostnad</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Kampanjmedlem</strong> (Campaign Member for Salesforce, Program Memberships for Marketo)</td>
    </tr>
    <tr>
      <td rowspan="14">XDM Business Campaign-medlemmar</td>
      <td></td>
      <td>campaignMemberKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 987654321@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>Exempel: - 987654321</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignMemberKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Lead-ID eller kontakt-ID</td>
      <td>Ja</td>
      <td>
        <p>Till exempel - 333, beroende på datakälltabellen, är detta antingen lead-ID eller kontakt-ID.</p>
        <p>Sekundär nyckel till lead eller kontakt</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceID</td>
      <td>string</td>
      <td>Kampanj-ID</td>
      <td>Ja</td>
      <td>
        <p>T.ex. - 55555.</p>
        <p>Främmande nyckel till kampanj</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">Information om XDM Business Campaign-medlem</td>
      <td>b2b.personType</td>
      <td>string</td>
      <td>Lead eller Kontakt</td>
      <td>Ja</td>
      <td>Beroende på tabellen för datakälla ska detta anges till antingen Lead eller Kontakt. Vi rekommenderar att du ställer in det på "Kontakt" för de flesta fall</td>
    </tr>
    <tr>
      <td></td>
      <td>memberStatus</td>
      <td>string</td>
      <td>Status</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>hasResponded</td>
      <td>boolesk</td>
      <td>hasResponded</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>firstRespondedDate</td>
      <td>date-time</td>
      <td>FirstRespondedDate</td>
      <td>Nej</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Person</strong> (Kontakt eller lead för Salesforce, Personer för Marketo)</td>
    </tr>
    <tr>
      <td>Individuell XDM-profil</td>
      <td rowspan="11">Information om XDM Business Person</td>
      <td>b2b.personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>t.ex. - 333, beroende på datakälltabellen, är detta antingen lead-ID eller kontakt-ID</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>workEmail.address</td>
      <td>
        <p>string</p>
        <p>e-post</p>
      </td>
      <td>E-post</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personStatus</td>
      <td>string</td>
      <td>Status</td>
      <td>Ja för endast lead-personType</td>
      <td>Endast obligatoriskt om b2b.personType är Lead</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.isConverted</td>
      <td>boolesk</td>
      <td>IsConverted</td>
      <td>Ja för endast lead-personType</td>
      <td>Endast obligatoriskt om b2b.personType är Lead</td>
    </tr>
    <tr>
      <td></td>
      <td>b2b.personType</td>
      <td>string</td>
      <td>Lead eller Kontakt</td>
      <td>Ja</td>
      <td>Beroende på tabellen för datakälla ska detta anges till antingen Lead eller Kontakt. Vi rekommenderar att du ställer in det på "Kontakt" för de flesta fall</td>
    </tr>
    <tr>
      <td></td>
      <td>extendedWorkDetails.jobTitle</td>
      <td>string</td>
      <td></td>
      <td>Nej</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="4">XDM Business Person Components</td>
      <td>personComponents.sourceAccountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Nej</td>
      <td>
        <p>Exempel: 123@999-abc-888.Marketo.</p>
        <p>Uppsättningen med sourceAccountKey-fält är bara"obligatorisk" för sanna kontaktposter, som definieras som personposter som är länkade till konto. Om den saknas kommer datauppsättningen inte att refuseras, men attribueringsresultaten kommer att vara avstängda.</p>
        <p>personComponents är en array, men Marketo Measure tar bara det första elementet personComponents[0]</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceID</td>
      <td>string</td>
      <td>Konto-ID</td>
      <td>Nej</td>
      <td>
        <p>Exempel: - 123.</p>
        <p>Sekundär nyckel till konto</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Nej</td>
      <td>t.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personComponents.sourceAccountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Nej</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td colspan="7"><strong>Möjligheter</strong> (Möjligheter för Salesforce, möjligheter för Marketo)</td>
    </tr>
    <tr>
      <td rowspan="13">XDM - affärsmöjlighet</td>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>Exempel: - 77777</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 123@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceID</td>
      <td>string</td>
      <td>Konto-ID</td>
      <td>Ja</td>
      <td>
        <p>Exempel: - 123.</p>
        <p>Sekundär nyckel till konto</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>accountKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>OpportunityName</td>
      <td>string</td>
      <td>Namn</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityStage</td>
      <td>string</td>
      <td>Scen</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityType</td>
      <td>string</td>
      <td></td>
      <td>Nej</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Information om affärsmöjligheter i XDM</td>
      <td>isWon</td>
      <td>boolesk</td>
      <td>IsWon</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isClosed</td>
      <td>boolesk</td>
      <td>ÄrStängd</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>expectedCloseDate</td>
      <td>datum</td>
      <td>CloseDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.amount</td>
      <td>tal</td>
      <td>Belopp</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityAmount.currencyCode</td>
      <td>
        <p>string</p>
        <p>^[A-Z]{3}$</p>
      </td>
      <td>CurrencyIsoCode</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Roll för säljprojektskontakt (behövs bara om du planerar att använda säljprojektskontaktrollen som inköpsgrupp för attribuering)</strong></td>
    </tr>
    <tr>
      <td rowspan="16">XDM - affärsmöjlighet, personrelation</td>
      <td></td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Kontakt-ID</td>
      <td>Ja</td>
      <td>
        <p>t.ex. - 333.</p>
        <p>Sekundär nyckel att kontakta</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>isPrimary</td>
      <td>boolesk</td>
      <td>ÄrPrimär</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 77777@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceID</td>
      <td>string</td>
      <td>ID för affärsmöjlighet</td>
      <td>Ja</td>
      <td>
        <p>till exempel - 77777.</p>
        <p>Främmande nyckel till affärsmöjlighet</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 222222@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceID</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>t.ex. - 22222</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td>opportunityPersonKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>personRole</td>
      <td>string</td>
      <td>Roll</td>
      <td>Nej</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td colspan="7"><strong>Konverteringshastighet (behövs bara om du använder flera valutor; endast en konverteringskursdatauppsättning kan aktiveras för Marketo Measure)</strong></td>
    </tr>
    <tr>
      <td rowspan="7">Konvertering</td>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 8888@0x012345.Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceId</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>till exempel - 8888</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: 0x012345</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.externalKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel - Salesforce</td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.createdDate</td>
      <td>date-time</td>
      <td>SkapadDatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>extSourceSystemAudit.lastUpdatedDate</td>
      <td>date-time</td>
      <td>ModifiedDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>isDeleted</td>
      <td>boolesk</td>
      <td></td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td rowspan="5">Valutakonverteringsinformation</td>
      <td>conversionRate</td>
      <td>tal</td>
      <td>ConversionRate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>endDate</td>
      <td>datum</td>
      <td>NästaStartdatum</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>startDate</td>
      <td>datum</td>
      <td>StartDate</td>
      <td>Ja</td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td>sourceISOCode</td>
      <td>string</td>
      <td>ISOCode</td>
      <td>Ja</td>
      <td>Exempel: EUR</td>
    </tr>
    <tr>
      <td></td>
      <td>targetISOCode</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Standardvalutakoden i Marketo Measure, t.ex. USD</td>
    </tr>
  </tbody>
</table>

## ExperienceEvent {#experienceevent}

<table style="table-layout:auto">
  <tr>
    <th>XDM-klass</th>
    <th>XDM-fältgrupp</th>
    <th>XDM-sökväg</th>
    <th>XDM-typ</th>
    <th>Datakällfält</th>
    <th>Obligatoriskt?</th>
    <th>Anteckningar</th>
  </tr>
  <tbody>
    <tr>
      <td colspan="7"><strong>Aktivitet</strong></td>
    </tr>
    <tr>
      <td rowspan="3">XDM ExperienceEvent</td>
      <td></td>
      <td>_id</td>
      <td>string</td>
      <td>ID</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td></td>
      <td>eventType</td>
      <td>string</td>
      <td>ActivityType</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td></td>
      <td>tidsstämpel</td>
      <td>date-time</td>
      <td>Aktivitetsdatum</td>
      <td>Ja</td>
      <td>Ja</td>
    </tr>
    <tr>
      <td></td>
      <td>Identifierare för person</td>
      <td>personKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: - 333@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceID</td>
      <td>string</td>
      <td>Lead-ID eller kontakt-ID</td>
      <td>Ja</td>
      <td>
        <p>Till exempel - 333, beroende på datakälltabellen, är detta antingen lead-ID eller kontakt-ID.</p>
        <p>Sekundär nyckel till lead eller kontakt</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceInstanceID</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>personKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Lägg till i kampanj</td>
      <td>leadOperation.addToCampaign.campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja endast för leadOperation.addToCampaign-typen</td>
      <td>Exempel: - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceId</td>
      <td>string</td>
      <td>Kampanj-ID</td>
      <td>Ja endast för leadOperation.addToCampaign-typen</td>
      <td>
        <p>T.ex. - 55555.</p>
        <p>Främmande nyckel till kampanj</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Ja endast för leadOperation.addToCampaign-typen</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.addToCampaign.campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja endast för leadOperation.addToCampaign-typen</td>
      <td>Exempel: Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td>Status i kampanjförloppet har ändrats</td>
      <td>leadOperation.campaignProgression.campaignKey.sourceKey</td>
      <td>string</td>
      <td></td>
      <td>Ja för endast leadOperation.campaignProgression-typen</td>
      <td>Exempel: - 55555@999-abc-888.Marketo</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceId</td>
      <td>string</td>
      <td>Kampanj-ID</td>
      <td>Ja för endast leadOperation.campaignProgression-typen</td>
      <td>
        <p>T.ex. - 55555.</p>
        <p>Främmande nyckel till kampanj</p>
      </td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceInstanceId</td>
      <td>string</td>
      <td></td>
      <td>Ja för endast leadOperation.campaignProgression-typen</td>
      <td>T.ex. - 999-abc-888</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>leadOperation.campaignProgression.campaignKey.sourceType</td>
      <td>string</td>
      <td></td>
      <td>Ja för endast leadOperation.campaignProgression-typen</td>
      <td>Exempel: Marketo</td>
    </tr>
  </tbody>
</table>

## ExperienceEvent-typ som stöds {#experienceevent-type-supported}

<table style="table-layout:auto">
  <tr>
    <th>Händelsetyp</th>
    <th>XDM-händelsetyp</th>
    <th>Beskrivning</th>
  </tr>
  <tbody>
    <tr>
      <td>Nytt lead</td>
      <td>leadOperation.newLead</td>
      <td>Använd för att registrera framtagning och detaljer för ett nytt marknadsföringslead</td>
    </tr>
    <tr>
      <td>Konvertera lead</td>
      <td>leadOperation.convertLead</td>
      <td>Används när ett marknadsföringslead konverteras till en säljkvalificerad kontakt som tilldelas en försäljningsanvändare</td>
    </tr>
    <tr>
      <td>Intressant stund</td>
      <td>leadOperation.interestingMoment</td>
      <td>Används för att spåra värdefulla aktiviteter av potentiella kunder</td>
    </tr>
    <tr>
      <td>Fyll i formulär</td>
      <td>web.formFilledOut</td>
      <td>Används för att samla in information när en person fyller i ett formulär på en webbsida</td>
    </tr>
    <tr>
      <td>Avbeställ e-post</td>
      <td>directMarketing.emailUnsubscribed</td>
      <td>Används för att samla in information när en person avbeställer en e-postprenumeration</td>
    </tr>
    <tr>
      <td>Öppna e-post</td>
      <td>directMarketing.emailOpened</td>
      <td>Används för att samla in information när en person öppnar ett marknadsföringsmejl</td>
    </tr>
    <tr>
      <td>Klicka på E-post</td>
      <td>directMarketing.emailClicked</td>
      <td>Används för att samla in information när en person klickar på en länk i ett marknadsföringsmeddelande</td>
    </tr>
    <tr>
      <td>Ändra status i progression</td>
      <td>leadOperation.statusInCampaignProgressionChanged</td>
      <td>Används för att samla in information när en leads status i en kampanj ändras</td>
    </tr>
    <tr>
      <td>Lägg till i engagemangsprogram (lägg till i struktur)</td>
      <td>leadOperation.addToCampaign</td>
      <td>Används för att lägga till en person till den specifika kampanjen.</td>
    </tr>
  </tbody>
</table>

Använd händelsetypen Intressant stund för händelsetyper som inte stöds i tabellen ovan. Lägg till ett anpassat fält för att ange undertypen&quot;Intressant stund&quot;.

## Frågeexempel för datainspektion {#query-examples-for-data-inspection}

Nedan följer en lista med frågeexempel för att inspektera inkapslade datauppsättningar i AEP-sjön. Om du vill använda dem mot dina datauppsättningar ersätter du tabellnamnet i frågeexemplen nedan med det faktiska datatabellnamnet.

Vi förväntar oss att alla räkningar ska vara 0.

För fältet personType förväntar vi oss att det bara finns värden för Lead eller Contact och att det inte finns något null-värde.

För alla kontaktpersonsposter finns det en sekundärnyckel för kontot.

För Lead-personposter finns ingen extern kontonyckel och är inte obligatorisk. Om du väljer att importera &quot;Lead&quot;-personposter som &quot;Contact&quot;-personposter (vilket rekommenderas), behövs ingen sekundärnyckel för kontot för sådana personposter.

### XDM Business Account {#xdm-business-account}

```
select 'account source id', count(*) from salesforce_account where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_account where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_account where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_account where accountKey.sourceKey is null
union all
select 'account name', count(*) from salesforce_account where accountName is null
union all
select 'created date', count(*) from salesforce_account where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_account where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Campaign {#xdm-business-campaign}

```
select 'campaign source id', count(*) from salesforce_campaign where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign where campaignKey.sourceKey is null
union all
select 'campaign name', count(*) from salesforce_campaign where campaignName is null
union all
select 'created date', count(*) from salesforce_campaign where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Campaign-medlem {#xdm-business-campaign-member}

```
select 'campaign member source id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceId is null
union all
select 'campaign member source type', count(*) from salesforce_campaign_member where campaignMemberKey.sourceType is null
union all
select 'campaign member source instance id', count(*) from salesforce_campaign_member where campaignMemberKey.sourceInstanceId is null
union all
select 'campaign member source key', count(*) from salesforce_campaign_member where campaignMemberKey.sourceKey is null
union all
select 'campaign source id', count(*) from salesforce_campaign_member where campaignKey.sourceId is null
union all
select 'campaign source type', count(*) from salesforce_campaign_member where campaignKey.sourceType is null
union all
select 'campaign source instance id', count(*) from salesforce_campaign_member where campaignKey.sourceInstanceId is null
union all
select 'campaign source key', count(*) from salesforce_campaign_member where campaignKey.sourceKey is null
union all
select 'person source id', count(*) from salesforce_campaign_member where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_campaign_member where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_campaign_member where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_campaign_member where personKey.sourceKey is null
union all
select distinct 'person type', b2b.personType from salesforce_campaign_member
union all
select 'member status', count(*) from salesforce_campaign_member where memberStatus is null
union all
select 'has responded', count(*) from salesforce_campaign_member where hasResponded is null
union all
select 'created date', count(*) from salesforce_campaign_member where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_campaign_member where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM Business Person {#xdm-business-person}

```
select 'person source id', count(*) from marketo_person where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_person where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_person where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_person where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from marketo_person where workEmail.address is null
union all
select 'Lead - person status', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from marketo_person where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from marketo_person
union all
select 'created date', count(*) from marketo_person where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from marketo_person where extSourceSystemAudit.lastUpdatedDate is null;
```

```
select 'person source id', count(*) from salesforce_contact where b2b.personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_contact where b2b.personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_contact where b2b.personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_contact where b2b.personKey.sourceKey is null
union all
select 'email', count(*) from salesforce_contact where workEmail.address is null
union all
select 'Lead - person status', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.personStatus is null
union all
select 'Lead - is converted', count(*) from salesforce_contact where b2b.personType = 'Lead' and b2b.isConverted is null
union all
select distinct 'person type', b2b.personType from salesforce_contact
union all
select 'account source id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_contact where b2b.personType = 'Contact' and personComponents[0].sourceAccountKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM - affärsmöjlighet {#xdm-business-opportunity}

```
select 'opportunity source id', count(*) from salesforce_opportunity where opportunityKey.sourceId is null
union all
select 'opportunity source type', count(*) from salesforce_opportunity where opportunityKey.sourceType is null
union all
select 'opportunity source instance id', count(*) from salesforce_opportunity where opportunityKey.sourceInstanceId is null
union all
select 'opportunity source key', count(*) from salesforce_opportunity where opportunityKey.sourceKey is null
union all
select 'account source id', count(*) from salesforce_opportunity where accountKey.sourceId is null
union all
select 'account source type', count(*) from salesforce_opportunity where accountKey.sourceType is null
union all
select 'account source instance id', count(*) from salesforce_opportunity where accountKey.sourceInstanceId is null
union all
select 'account source key', count(*) from salesforce_opportunity where accountKey.sourceKey is null
union all
select 'opportunity name', count(*) from salesforce_opportunity where opportunityName is null
union all
select 'opportunity stage', count(*) from salesforce_opportunity where opportunityStage is null
union all
select 'is won', count(*) from salesforce_opportunity where isWon is null
union all
select 'is closed', count(*) from salesforce_opportunity where isClosed is null
union all
select 'expected close date', count(*) from salesforce_opportunity where expectedCloseDate is null
union all
select 'opportunity amount', count(*) from salesforce_opportunity where opportunityAmount.amount is null
union all
select 'currency code', count(*) from salesforce_opportunity where opportunityAmount.currencyCode is null
union all
select 'created date', count(*) from salesforce_opportunity where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_opportunity where extSourceSystemAudit.lastUpdatedDate is null;
```

### XDM ExperienceEvent {#xdm-experienceevent}

```
select 'id', count(*) from marketo_activity where _id is null
union all
select 'event type', count(*) from marketo_activity where eventType is null
union all
select 'timestamp', count(*) from marketo_activity where timestamp is null
union all
select 'person source id', count(*) from marketo_activity where personKey.sourceId is null
union all
select 'person source type', count(*) from marketo_activity where personKey.sourceType is null
union all
select 'person source instance id', count(*) from marketo_activity where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from marketo_activity where personKey.sourceKey is null
union all
select 'addToCampaign campaign id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceId is null
union all
select 'addToCampaign campaign type', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceType is null
union all
select 'addToCampaign campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceInstanceId is null
union all
select 'addToCampaign campaign key', count(*) from marketo_activity where eventType = 'leadOperation.addToCampaign' and leadOperation.addToCampaign.campaignKey.sourceKey is null
union all
select 'statusInCampaignProgressionChanged campaign id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceId is null
union all
select 'statusInCampaignProgressionChanged campaign type', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceType is null
union all
select 'statusInCampaignProgressionChanged campaign instance id', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceInstanceId is null
union all
select 'statusInCampaignProgressionChanged campaign key', count(*) from marketo_activity where eventType = 'leadOperation.campaignProgression.campaignKey.sourceKey' and leadOperation.campaignProgression.campaignKey.sourceKey is null;
```

```
select 'id', count(*) from salesforce_task where _id is null
union all
select 'event type', count(*) from salesforce_task where eventType is null
union all
select 'timestamp', count(*) from salesforce_task where timestamp is null
union all
select 'person source id', count(*) from salesforce_task where personKey.sourceId is null
union all
select 'person source type', count(*) from salesforce_task where personKey.sourceType is null
union all
select 'person source instance id', count(*) from salesforce_task where personKey.sourceInstanceId is null
union all
select 'person source key', count(*) from salesforce_task where personKey.sourceKey is null;
```

### Konvertering {#conversion}

```
select 'conversion rate', count(*) from currency_conversion_rate where conversionRate is null
union all
select 'end date', count(*) from currency_conversion_rate where endDate is null
union all
select 'start date', count(*) from currency_conversion_rate where startDate is null
union all
select 'source ISO Code', count(*) from currency_conversion_rate where sourceISOCode is null
union all
select 'target ISO Code', count(*) from currency_conversion_rate where targetISOCode is null
union all
select 'source id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceId is null
union all
select 'source type', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceType is null
union all
select 'source instance id', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceInstanceId is null
union all
select 'source key', count(*) from currency_conversion_rate where extSourceSystemAudit.externalKey.sourceKey is null
union all
select 'created date', count(*) from salesforce_contact where extSourceSystemAudit.createdDate is null
union all
select 'last updated date', count(*) from salesforce_contact where extSourceSystemAudit.lastUpdatedDate is null;
```

## Rekommenderad lösning för obligatoriska fält med ett NULL-värde {#recommended-solution-for-required-fields-with-a-null-value}

Vi rekommenderar att du använder ett beräknat fält i fältmappning för att ange ett icke-NULL-värde som standardvärde för fältet. Följande är två exempel:

* Om affärsmöjlighetsnamnet för vissa affärsmöjlighetsposter är null skapar och använder du följande beräknade fält i fältmappning
   * `iif(name != null && name != "", name, "Unknown")`

* Om leadOperation.campaignProgression.campaignID för vissa upplevelsehändelseposter är null skapar och använder du följande beräknade fält i fältmappning
   * `iif(leadOperation.campaignProgression.campaignID != null && leadOperation.campaignProgression.campaignID != "" , to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", leadOperation.campaignProgression.campaignID, "sourceKey", concat(leadOperation.campaignProgression.campaignID,"@123-abc-321.Marketo")), iif(eventType == "leadOperation.statusInCampaignProgressionChanged", to_object("sourceType", "Marketo", "sourceInstanceID", "123-abc-321", "sourceID", "Unknown", "sourceKey", "Unknown@123-abc-321.Marketo"), null))`
