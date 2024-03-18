---
description: Felmeddelanden - [!DNL Marketo Measure]
title: Felmeddelanden
feature: Fundamentals
exl-id: ed07eed6-ddeb-4856-a1ac-ea3d571283f6
source-git-commit: 2b13a518d1be768a5c312ea4abdf2039aa22cf08
workflow-type: tm+mt
source-wordcount: '1675'
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
      <td>Läs följande Salesforce-dokumentation om <a href="https://help.salesforce.com/s/articleView?language=en_US&amp;id=sf.branded_apps_commun_api_permset.htm&amp;type=5">aktivera API-åtkomst</a>.</td>
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
      <td>CANNOT_EXECUTE_FLOW_TRIGGER</td>
      <td>Ett fel uppstod vid CRM-export: CANNOT_EXECUTE_FLOW_TRIGGER : Enhetstypen 'Contact' Ge Salesforce-administratören dessa uppgifter.
Gränsen har överskridits Du eller din organisation har överskridit maxgränsen för den här funktionen. Fel-ID: 123456</td>
      <td>Posten kan inte sparas eftersom den inte uppfyller en utlösarflödesregel som har konfigurerats i Salesforce-organisationen.</td>
      <td>Granska den fullständiga informationen i meddelandemeddelandet och granska flödesutlösarna i Salesforce-organisationen.
Salesforce-dokumentation om flödesutlösare <a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">finns här</a>.
      </td>
    </tr>
    <tr>
      <td>CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY</td>
      <td>Ett fel uppstod vid CRM-export: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Entitetstyp 'Lead': CRM-felkod: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, CRM-felmeddelande: System.LimitException: Apex CPU-tidsgräns överskreds, RecordId: 0123456
      <p>
      Ett fel uppstod vid CRM-export: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY : Entitetstyp 'Konto': CRM-felkod: CANNOT_INSERT_UPDATE_ACTIVATE_ENTITY, CRM-felmeddelande: entitetstypen kan inte uppdateras: Konto, RecordId: 0123456</td>
      <td>Utlösare förhindrar uppdatering eller infogning av ett objekt.
      <p>
      ELLER
      <p>
      Behörigheter saknas för objektet.</td>
      <td>Granska utlösarkod som gör att infogningen/uppdateringen misslyckas. Mer information om utlösare finns i följande Salesforce-dokumentation:
        <ul>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.code_manage_triggers.htm&amp;type=5">Apex-utlösare</a>
          </li>
          <li><a href="https://admin.salesforce.com/blog/2023/what-is-a-record-triggered-flow#:~:text=A%20record%2Dtriggered%20flow%20allows,is%20created%20and%2For%20updated">Flödesutlösare</a>
          </li>
        </ul>
        <p>
        Ge alla nödvändiga behörigheter till <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Marketo Measure</a>.
      </td>
    </tr>
    <tr>
      <td>DUPLICATES_DETECTED</td>
      <td>Ett fel uppstod vid CRM-export: DUPLICATES_DETECTED : Enhetstyp 'Contact': CRM-felkod: DUPLICATES_DETECTED, CRM-felmeddelande: Du skapar en dubblettpost. Vi rekommenderar att du använder en befintlig post i stället., RecordId: 0123456</td>
      <td>Posten som importeras till Salesforce-organisationen finns redan.</td>
      <td>
        <ul>
          <li><a href="https://help.salesforce.com/s/articleView?id=000390009&amp;type=1">Inaktivera inställningen Duplicera regel</a> för att tillåta dubbletter.
          </li>
          <li>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>DUPLICATE_VALUE</td>
      <td>Ett fel uppstod vid CRM-export: DUPLICATE_VALUE : Enhetstyp Lead: CRM-felkod: DUPLICATE_VALUE, CRM-felmeddelande: dubblettvärde hittades: Email_Unique__c-dubblettvärde i post med ID: 123, RecordId: 456</td>
      <td>Fältet som importeras till Salesforce-organisationen tillåter inte dubblettvärden.</td>
      <td>
        <ul>
          <li>Avmarkera <a href="https://help.salesforce.com/s/articleView?id=000390009&amp;type=1">"Unik kryssruta"</a> i Salesforce.
          </li>
          <li>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>ENTITY_IS_LOCKED</td>
      <td>Det uppstod ett fel vid CRM-export: ENTITY_IS_LOCKED : Enhetstyp 'Konto': CRM-felkod: ENTITY_IS_LOCKED, CRM-felmeddelande: Den här posten är låst. Kontakta din administratör om du behöver redigera den. RecordId: 0123456</td>
      <td>När en post är i en godkännandeprocess och en användare som inte är den aktuella godkännaren eller systemadministratören försöker redigera posten.</td>
      <td>
        <ul>
          <li>Lös den väntande godkännandeprocessen för den posten i Salesforce-organisationen.</li>
          <li>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>FIELD_FILTER_VALIDATION_EXCEPTION</td>
      <td>Ett fel uppstod vid CRM-export: FIELD_FILTER_VALIDATION_EXCEPTION : Enhetstyp Lead: CRM-felkod: FIELD_FILTER_VALIDATION_EXCEPTION, fält: User_C, CRM-felmeddelande: Värdet finns inte eller matchar inte filtervillkoren. Välj en användare med rollen"Account Executive, Inside Sales"; RecordId: 0123456</td>
      <td>Den ändrade posten uppfyller inte längre uppslagsfiltren som har definierats för objektet.</td>
      <td>Sök efter filter för det objekt som Marketo Measure försöker ändra. Se <a href="https://help.salesforce.com/s/articleView?id=000384756&amp;type=1">den här Salesforce-artikeln</a> om du vill lära dig hur du söker efter filter för ett objekt.</td>
    </tr>
    <tr>
      <td>FIELD_INTEGRITY_EXCEPTION</td>
      <td>Ett fel uppstod vid CRM-export: FIELD_INTEGRITY_EXCEPTION : Enhetstypen Lead: CRM-felkod: FIELD_INTEGRITY_EXCEPTION, fält: Land, CRM-felmeddelande: Det finns ett problem med det här landet, även om det kan se korrekt ut. Välj ett land/territorium i listan över giltiga länder.: Land, post-ID: 0123456</td>
      <td>Postens förväntade typ matchar inte.</td>
      <td>Det vanligaste fallet med detta är inte att följa namngivningsstandarder för delstat/land som angetts i Salesforce-organisationen eftersom fälten Delstat/Land har standardiserats så att endast vissa plocklistevärden accepteras. Du kan åtgärda problemet genom att:
        <ul>
          <li>Uppdatera posten så att den följer organisationens godkända värden för det fältet. Kontakta SFDC-administratören för att få en lista över godkända värden.</li>
          <li><a href="https://help.salesforce.com/s/articleView?id=sf.admin_state_country_picklist_enable.htm&amp;type=5">Inaktivera plocklistorna Delstat/Land</a>.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>INACTIVE_OWNER_OR_USER</td>
      <td>Ett fel uppstod vid CRM-export: INACTIVE_OWNER_OR_USER : Enhetstyp 'Contact': CRM-felkod: INACTIVE_OWNER_OR_USER, CRM-felmeddelande: åtgärden utfördes med den inaktiva användaren [1234] som ägare av kontakten, RecordId: 0123456</td>
      <td>Marketo Measure saknar behörigheten Uppdatera poster med inaktiva ägare.</td>
      <td>Bevilja Marketo Measure<a href="https://help.salesforce.com/s/articleView?id=000386699&amp;type=1">Uppdatera poster med inaktiva ägare</a>" behörighet.</td>
    </tr>
    <tr>
      <td>INSUFFICIENT_ACCESS_OR_READONLY</td>
      <td>Ett fel uppstod vid CRM-export: INSUFFICIENT_ACCESS_OR_READONLY : Enhetstyp 'Konto': CRM-felkod: INSUFFICIENT_ACCESS_OR_READONLY, CRM-felmeddelande: Otillräcklig behörighet för objekt-ID: [123], RecordId: 456</td>
      <td>Marketo Measure saknar behörighet för ett objekt eller fält, eller så är objektet skrivskyddat.</td>
      <td>Se följande <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">Experience League-artikel</a> för vägledning om vilka behörigheter Marketo Measure kräver.</td>
    </tr>
    <tr>
      <td>INVALID_ADOBE_ANALYTICS_CONFIGURATION</td>
      <td>Ett fel uppstod vid Adobe Analytics-export: INVALID_ADOBE_ANALYTICS_CONFIGURATION : Fel: Överföring tillåts inte. Bekräfta datakällans schema före överföring. Datakällans ID:1234</td>
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
      <td>MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS</td>
      <td>Ett fel uppstod vid CRM-export: MISSING_BIZIBLE_CUSTOM_FIELDS_PERMISSIONS : Enhetstyp 'Campaign': CRM-felkod: INVALID_FIELD_FOR_INSERT_UPDATE, fält: bizible2__UniqueId__c, CRM-felmeddelande: Det går inte att skapa/uppdatera fält: bizible2__Unique Id__c. Kontrollera säkerhetsinställningarna för det här fältet och verifiera att det är skrivskyddat för din profil eller behörighetsgrupp.</td>
      <td>Marketo Measure saknar behörigheter för bizible-fält.</td>
      <td>Vi kräver läs- och skrivbehörighet för alla fält som har prefixet "bizible2__". En fullständig lista över dessa fält finns <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">i den här artikeln</a>.</td>
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
      <td>MISSING_RECORD_OBJECT_PERMISSIONS</td>
      <td>Ett fel uppstod vid CRM-export: MISSING_RECORD_OBJECT_PERMISSIONS : Entitetstypen 'bizible2_Bizible_Touchpoint__c': CRM-felkod: INSUFFICIENT_ACCESS_ON_CROSS_REFERENCE_ENTITY, Fält: Konto, CRM-felmeddelande: Otillräckliga åtkomsträttigheter för korsreferens-ID: 01 23456</td>
      <td>Marketo Measure saknar behörigheter.</td>
      <td>Det finns flera orsaker till det här felet som är specifika för Salesforce-organisationen. Nedan beskrivs några vanliga felsökningssteg som kan lösa problemet:
        <ul>
          <li>Granska alla behörigheter som krävs för varje <a href="/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md">objekt och fält</a>.</li>
          <li>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.</li>
          <li>Bevilja Marketo Measure "<a href="https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/users_profiles_view_all_mod_all.htm">Ändra alla</a>" behörigheter.</li>
        </ul>
      </td>
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
      <td>RECORD_NONCOMPLIANT_WITH_VALIDATION_Rules</td>
      <td>Ett fel uppstod vid CRM-export: RECORD_NONCOMPLIANT_WITH_VALIDATION_Rules : Enhetstyp Lead: CRM-felkod: FIELD_CUSTOM_VALIDATION_EXCEPTION, fält: Lead_Status_Reason__c, CRM-felmeddelande: Du måste välja Lead-statusorsak, RecordId: 0123 456</td>
      <td>Posten som uppdateras uppfyller inte en valideringsregel som angetts i Salesforce-organisationen.</td>
      <td>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
      <p>
      Uppdatera dina <a href="https://help.salesforce.com/s/articleView?id=sf.fields_about_field_validation.htm&amp;type=5">verifieringsregler</a>.</td>
    </tr>
    <tr>
      <td>RESTRICT_PICKLIST_VALUES_ENABLED</td>
      <td>Ett fel uppstod vid CRM-export: RESTRICT_PICKLIST_VALUES_ENABLED : Entitetstyp 'Campaign': CRM-felkod: INVALID_OR_NULL_FOR_RESTRICTED_PICKLIST, Fält: Areas_of_Interest__c, CRM-felmeddelande: felaktigt värde för begränsat listfält: Okänt</td>
      <td>När 'Begränsa plocklistan till de värden som definieras i värdeuppsättningen' är aktiverat i plocklistefältets inställning, eller så är det värde som infogas i fältet inte tillgängligt i objektets posttyp.</td>
      <td>Inaktivera inställningen för begränsad lista i Salesforce-organisationen.
          <p>
          Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
      </td>
    </tr>
    <tr>
      <td>REQUIRED_FIELD_MISSING</td>
      <td>Ett fel uppstod vid CRM-export: MISSING_REQUIRED_FIELD : Enhetstyp Lead: CRM-felkod: REQUIRED_FIELD_MISSING, fält: Product_Type__c, CRM-felmeddelande: Obligatoriska fält saknas: [Product_Type__c], RecordId: 0123456</td>
      <td>När en valideringsregel anger kräver fält på objekt.</td>
      <td>Uteslut den dedikerade Marketo Measure-användaren från <a href="https://trailhead.salesforce.com/content/learn/modules/validation-rules/bypass-your-validation-rules">anpassade valideringsregler</a>.
      </td>
    </tr>
    <tr>
      <td>UNKNOWN_EXCEPTION</td>
      <td>Det uppstod ett fel vid Crm-export: UNKNOWN_EXCEPTION : Enhetstypen 'Contact': CRM-felkod: UNKNOWN_EXCEPTION, CRM-felmeddelande: portalanvändare kan inte äga partnerkonton, RecordId: 0123456</td>
      <td>Ett ohanterat undantag inträffade i Salesforce.</td>
      <td>Om problemet kvarstår kan du skicka ett ärende till Salesforce och kopiera de numeriska värdena i felmeddelandet.</td>
    </tr>
    <tr>
      <td>UNSUPPORTED_CRM_PACKAGE_VERSION</td>
      <td>Ett fel uppstod vid CRM-import: UNSUPPORTED_CRM_PACKAGE_VERSION : Uppdatera crm-paketet</td>
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
