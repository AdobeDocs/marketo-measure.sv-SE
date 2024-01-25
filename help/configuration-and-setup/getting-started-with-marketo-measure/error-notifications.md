---
description: Felmeddelanden - [!DNL Marketo Measure] - Produktdokumentation
title: Felmeddelanden
hide: true
hidefromtoc: true
feature: Fundamentals
source-git-commit: b4fadc6519761975736ce7a0e4f99a30c589c9af
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Felmeddelanden {#error-notifications}

Nedan visas en lista med fel som du kan få via meddelanden i appen eller e-post. Om du får något av dessa felsökningar följer du de aktuella felsökningsstegen. Om de här stegen inte löser problemet kan du kontakta [Marketo Support](https://nation.marketo.com/t5/support/ct-p/Support).

<table>
  <tbody>
    <tr>
      <th style="width:31%">Felkod</th>
      <th style="width:23%">Exempel på meddelanden</th>
      <th style="width:23%">Beskrivning</th>
      <th style="width:23%">Felsökningssteg</th>
    </tr>
    <tr>
      <td>API_DISABLED</td>
      <td>Ett fel uppstod vid CRM-import: API_DISABLED: API-anrop har inaktiverats för den här användaren</td>
      <td>API-behörigheten har inaktiverats för Marketo Measure-användaren.</td>
      <td>Läs följande Salesforce-dokumentation om <a href="https://help.salesforce.com/s/articleView?id=sf.branded_apps_commun_api_permset.htm&amp;type=5">aktivera API-åtkomst</a>.</td>
    </tr>
    <tr>
      <td>API_LIMIT_EXCEEDED</td>
      <td>Ett fel uppstod vid CRM-export : PI_LIMIT_EXCEEDED</td>
      <td>CRM:s API-gräns har överskridits (24 timmar).</td>
      <td>Se följande dokumentation för CRM för att få hjälp med att justera API-kreditallokeringar:</p>
          <ul>
            <li><a href="https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/service-protection-monitoring">Dynamics</a>
            </li>
            <li><a href="https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm">Salesforce</a>
            </li>
          </ul>
          <p>Du kan även justera de CRM-krediter som Marketo Measure använder genom att följa stegen nedan:</p>
          <ul>
            <li>Navigera till <b>Inställningar</b> &gt; <b>CRM</b> &gt; <b>Allmänt</b></li>
            <li>Uppdatera gränsen för Daily CRM API<br/>
              <ul>
                <li><b>Obs! Standardvärdet är 100 000</b></li>
              </ul>
            </li>
          </ul>
          <p>
           <img src="assets/error-notifications-1.png">
          </p>
      </td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Ett fel uppstod vid Adobe Analytics-export: INVALID_ADOBE_ANALYTICS_CONFIGURATION : Fel: Överföring tillåts inte. Bekräfta datakällans schema innan överföring. Datakällans ID:1234</td>
      <td>Adobe Analytics-integreringen är inte korrekt konfigurerad.</td>
      <td>Se följande hjälpartiklar för att säkerställa korrekt konfiguration:
        <ul>
          <li>
            <a href="/help/marketo-measure-and-adobe/marketo-measure-integrations-with-adobe-analytics.md">Marketo Measure-integrering med Adobe Analytics</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/core-services/interface/services/customer-attributes/t-crs-usecase.html">Skapa en kundattributskälla och överför datafilen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INVALID_CURRENCY_ISO_CODE</td>
      <td>Ett fel uppstod vid annonsimporten: INVALID_CURRENCY_ISO_CODE: Currency XXX stöds inte av Marketo Measure.
      <p>
      Ett fel uppstod vid annonsimport: INVALID_CURRENCY_ISO_CODE : Currency XXX på Konto för 1234 stöds inte av Marketo Measure.</td>
      <td>En valuta som inte stöds påträffades.</td>
      <td>I källsystemet som anges i meddelandet (Ad, Crm, Marketo) ser du till att den valuta som är associerad med posten har en giltig valuta som stöds. De valutor som stöds härleds från ISO-valutastandarder.</td>
    </tr>
    <tr>
      <td>MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>Ett fel uppstod vid CRM-export: MISSING_CONVERTED_LEAD_PERMISSION</td>
      <td>Marketo Measure saknar behörigheten Visa/redigera konverterade leads</td>
      <td>Mer information om hur du aktiverar den här behörigheten i CRM finns i följande Experience League-dokument<br/>
          <a href="/help/marketo-measure-salesforce-reporting/additional-functionality/enabling-the-permission-to-edit-converted-leads.md">Aktivera behörighet att redigera konverterade leads</a></td>
    </tr>
    <tr>
      <td>MISSING_FIELD_READ_PERMISSION</td>
      <td>Ett fel uppstod vid CRM-import: MISSING_FIELD_READ_PERMISSION : Enhetstyp 'Event': INVALID_FIELD:<br/>
    SystemModstamp,IsDeleted,WhoId,bizible2_Bizible_Touchpoint_Date__c</td>
      <td>Marketo Measure saknar läsbehörighet för ett obligatoriskt fält.</td>
      <td>Läs följande hjälpartiklar för mer information om vilka behörigheter Marketo Measure kräver:
        <ul>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>MISSING_ISREPLICATEABLE_PERMISSION</td>
      <td>Ett fel uppstod vid CRM-import: Saknad_ISREPLICATEABLE_PERMISSION: Vi saknar IsReplicable-behörighet för Campaign</td>
      <td>Den här behörigheten krävs för Salesforce-objekt för att vi ska kunna synkronisera dina Marketo Measure- och Salesforce-objekt.</td>
      <td>Kontakta Salesforce-support om du behöver hjälp med att ange replikeringsbar behörighet för objekt.</td>
    </tr>
    <tr>
      <td>MISSING_OBJECT_READ_PERMISSION</td>
      <td>Ett fel uppstod vid CRM-import: MISSING_OBJECT_READ_PERMISSION : Enhetstyp Campaign': CRM-felkod: MISSING_PERMISSION</td>
      <td>Marketo Measure saknar läsbehörighet för ett obligatoriskt objekt.</td>
      <td rowspan="2">Läs följande hjälpartiklar för mer information om vilka behörigheter Marketo Measure kräver:
          <ul>
            <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/marketo-measure-dynamics-schema.md">Dynamics</a>
            </li>
            <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Salesforce</a>
            </li>
          </ul>
      </td>
    </tr>
    <tr>
      <td>MISSING_OBJECT_WRITE_PERMISSION</td>
      <td>Ett fel uppstod vid CRM-export: MISSING_OBJECT_WRITE_PERMISSION : Enhetstypen 'bizible2_Bizible_Attribution_Touchpoint': CRM-felkod: MISSING_PERMISSION</td>
      <td>Marketo Measure saknar skrivbehörighet till ett obligatoriskt objekt.</td>
    </tr>
    <tr>
      <td>NULL_EMPTY_CURRENCY_ISO_CODE</td>
      <td>
        <p>
          Ett fel uppstod vid CRM-import: NULL_EMPTY_CURRENCY_ISO_CODE: ISO-valutakod är NULL eller tom när MultiCurrency är aktiverat för RecordId 1234
      </td>
      <td>Valutan måste vara en ISO-valutakod som stöds.</td>
      <td>I källsystemet som anges i meddelandet (Ad, Crm, Marketo) ser du till att den valuta som är associerad med posten har en giltig valuta som stöds. De valutor som stöds härleds från ISO-valutastandarder.</td>
    </tr>
    <tr>
      <td>OPERATION_TOO_LARGE</td>
      <td>Ett fel uppstod vid CRM-import: OPERATION_TOO_LARGE: Vi kräver behörigheten Visa alla data för att kunna fråga efter aktiviteter.</td>
      <td>CRM-inställningarna tillåter inte Marketo Measure att fråga en stor mängd data</td>
      <td>Bevilja Marketo Measure 'Visa alla data'-behörigheter för det angivna objektet.
      <p>
      Mer information om behörigheten Visa alla data <a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">finns här</a>.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Ett fel uppstod vid CRM-import: UNSUPPORTED_CRM_PACKAGE_VERSION : Uppdatera CRM-paketet</td>
      <td>Det aktuella paketet som identifierats stöds inte längre.</td>
      <td>Uppgradera ditt paket till den senaste versionen:
        <ul>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/best-practices-for-marketo-measure-crm-package.md">Bästa praxis</a>
          </li>
          <li><a href="/help/marketo-measure-and-dynamics/getting-started-with-marketo-measure-and-dynamics/microsoft-dynamics-crm-installation-guide.md">Dynamics</a>
          </li>
          <li><a href="/help/configuration-and-setup/marketo-measure-and-salesforce/marketo-measure-salesforce-package-installation-and-set-up.md">Salesforce</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
