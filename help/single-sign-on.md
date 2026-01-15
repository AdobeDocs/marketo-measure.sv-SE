---
description: Riktlinjer för enkel inloggning för Marketo Measure-användare
title: Enkel inloggning
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '1376'
ht-degree: 0%

---

# Enkel inloggning {#single-sign-on}

SAML (Security assertion markup language) för enkel inloggning (single sign-on) gör det möjligt för användare att autentisera via ett företags identitetsleverantör när de loggar in i appen [!DNL Marketo Measure]. Med enkel inloggning kan en användare autentisera en gång utan att behöva autentisera separata appar. SAML är en nödvändighet för företagskunder eftersom inte alla användare har ett [!DNL Salesforce]- eller [!DNL Google]-konto inom organisationen. För att skala har [!DNL Marketo Measure] utvecklat en SAML-lösning som kan stödja företag-identitetsleverantörer.

>[!CAUTION]
>
>I den här artikeln beskrivs enkel inloggning (SSO) och avancerad CRM-användarhantering. Om ditt konto har etablerats **efter 2010-09-10** kan du ignorera den här artikeln eftersom enkel inloggning och Identity Management kommer att konfigureras i [Adobe Admin Console för din [!DNL Marketo Measure] integrering](/help/implementation-guide.md).

>[!NOTE]
>
>Det är sannolikt att företag använder olika identitetsleverantörer (till exempel Ping Identity, Okta). De termer som används i följande konfigurationsinstruktioner och i användargränssnittet kanske inte matchar de som används av din identitetsleverantör.

## Krav {#requirements}

* Användare med AccountAdmin-behörighet i appen [!DNL Marketo Measure]
* Användare med administrativ åtkomst till kundens identitetsleverantör

## Komma igång {#getting-started}

Navigera till Inställningar > Säkerhet > Autentisering i programmet [!DNL Marketo Measure] för att komma igång. Växla sedan inloggningstypen till Anpassad enkel inloggning för att se konfigurationsalternativen. Ändringarna börjar inte gälla förrän du testar autentiseringen och klickar på knappen **[!UICONTROL Save]** längst ned på sidan.

![Om du vill komma igång går du till sidan för säkerhetsautentisering av inställningar i &#x200B;](assets/compliance-resources-1.png)

## Process {#process}

[!DNL Marketo Measure] enkel inloggning kräver att autentiseringsinställningarna konfigureras i en serie steg så att du inte riskerar att bli utlåst från ditt [!DNL Marketo Measure]-konto.

Konfigurera programmet [!DNL Marketo Measure] i din identitetsleverantör. Se extern dokumentation som listas nedan för genomgångar.

    a. När du uppmanas att ange URL:en för enkel inloggning eller mottagarens URL eller mål-URL använder du [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b. Använd [https://BizibleLPM](https://biziblelpm/)
 när du uppmanas att ange målgruppsbegränsnings-URL eller en programdefinierad unik identifierare.
Växla till anpassad enkel inloggning i programmet [!DNL Marketo Measure]

    a. När faktureringsgruppen har aktiverats för ditt konto kan du nu navigera till [!UICONTROL Settings] >>[!UICONTROL Security] >> [!UICONTROL Authentication]
    
    b. Som standard anges din inloggningstyp till &quot;CRM-användare&quot;.
    
    c. Växla inloggningstypen till Anpassad enkel inloggning för att starta konfigurationsprocessen.

Fyll i anslutningsinställningarna för din identitetsleverantörskonfiguration

    a. Din identitetsleverantör kan ge ett IdP-metadatadatadokument (XML) som tar bort de konfigurationsfält som krävs. Läs antingen in innehållet i XML-dokumentet eller fyll i de tre fälten nedan från utdata som erhållits under konfigurationsprocessen för identitetsleverantören. **Du behöver inte fylla i båda.**
    
    i. IdP-URL: Den URL som  [!DNL Marketo Measure] måste peka på för att dina användare ska kunna autentiseras i  [!DNL Marketo Measure] programmet. Kallas ibland &quot;Omdirigerings-URL&quot;.
    ii. IdP-utfärdare: En unik identifierare för identitetsprovidern. Kallas ibland &quot;extern nyckel&quot;.
    iii. IdP-certifikat: En offentlig nyckel som tillåter [!DNL Marketo Measure] att verifiera och validera signaturen för alla identitetsleverantörssvar.

Ange utgångsdatum för token för dina användare på några minuter.

    a. [!DNL Marketo Measure] tillåter ett heltal mellan 1 och 1 440 minuter. När en användares sessionstid har överskridits loggas användaren ut när han/hon navigerar till en ny sida.

Ange och mappa inställningarna för användarattributet till respektive förnamn, efternamn och e-postadress.

    a. Genom att ange SAML-attributen kan  [!DNL Marketo Measure]  identifiera dina användare genom den information som skickas.
    
    i. E-postattribut: Ange det attributnamn som identitetsleverantören använder för användarens e-postadress.
    ii. Förnamnsattribut: Ange det attributnamn som identitetsleverantören använder för användarens förnamn.
    iii. Efternamnsattribut: Ange det attributnamn som identitetsleverantören använder för användarens efternamn.
    
    b. Tips! Om du testar din SAML-konfiguration nu kommer vi att analysera attributen E-post, Förnamn och Efternamn som du kan använda för det här avsnittet.

![b. Tips! Om du testar din SAML-konfiguration nu tolkas &#x200B;](assets/discover-control-1.png)

Konfigurera och mappa dina användarrollsinställningar till respektive roller eller grupper som klassificerats från din IdP.

    a. Kunderna kan tilldela  [!DNL Marketo Measure] användarroller baserat på grupper som definierats i deras identitetsleverantör. Genom att ange dina SAML-attribut kan  [!DNL Marketo Measure] mappa din användares roller och grupper till  [!DNL Marketo Measure] användarbehörigheter. Vi rekommenderar att du konfigurerar de här rollerna så att din [!DNL Marketo Measure] administratör har behörighet att uppdatera ditt konto.
    
    b. Om inga roller eller grupper mappas är standardinställningen att alla anställda i identitetsleverantören har standardanvändaråtkomst.
    
    i. [!DNL Marketo Measure] Standardanvändare: Ange roll- eller gruppvärdet (från din SSO-leverantör) för användare som ska ha skrivskyddad åtkomst till  [!DNL Marketo Measure] programmet.
    ii. [!DNL Marketo Measure] Kontoadministratörsanvändare: Ange roll- eller gruppvärdet (från din SSO-leverantör) för användare som ska ha administrativ åtkomst till  [!DNL Marketo Measure] programmet. Detta innebär att rollen har åtkomst till att ändra konfigurationer och inställningar som är relaterade till ditt konto.
    iii. Du måste ha ett attribut i din IdP med det exakta namnet &quot;groups&quot; som innehåller de värden du angett i attributen &quot;Bizible Standard User&quot; eller &quot;Bizible Account Admin User&quot;.
    
    c. Om flera roller eller grupper ska mappas till en roll anger du varje värde avgränsat med kommatecken.

![c. Om flera roller eller grupper ska mappas till en roll &#x200B;](assets/discover-control-2.png)

Testa konfigurationen för enkel inloggning

    a. Innan du kan trycka på Spara måste du klicka på knappen [!UICONTROL Test SAML Authentication] för att bekräfta att inställningarna har konfigurerats korrekt.
    
    b. Om ett felmeddelande visas följer du meddelandet och försöker igen.

![b. Om ett felmeddelande visas följer du meddelandet och försöker &#x200B;](assets/discover-control-3.png)

Spara dina inställningar och instruera dina kollegor att använda [!UICONTROL Single Sign On] med din nya anpassade inloggnings-URL.

    a. Viktigt! När du har sparat dina nya autentiseringsinställningar kan det hända att sessionen avslutas när du navigerar till en ny sida eftersom du har inaktiverat inloggning av CRM-användare och aktiverat Anpassad enkel inloggning.

![a. Viktigt: När du har sparat dina nya autentiseringsinställningar är det möjligt](assets/discover-control-3.png)

Prova!

    a. Använd din nya anpassade inloggnings-URL och försök logga in på  [!DNL Marketo Measure] programmet igen med din identitetsleverantörs autentiseringsuppgifter.
    
    b. Formatet kommer att se ut som &quot;https://apps.adobe.com/business/[accountName]&grave;
    
    c. Grattis! Du har konfigurerat enkel inloggning i  [!DNL Marketo Measure] programmet för ditt konto!

![c. Grattis! Du har konfigurerat enkel inloggning i &#x200B;](assets/discover-control-3.png)

>[!NOTE]
>
>När du har konfigurerat enkel inloggning behöver du inte längre lägga till användare i programmet [!DNL Marketo Measure]. Etablering av användare bör hanteras direkt i identitetsleverantören.

## CRM-användare (Avancerad inställning) {#crm-users-advanced-setup}

Som standard kan alla konton komma åt programmet [!DNL Marketo Measure] med hjälp av sina CRM-autentiseringsuppgifter. Ibland måste kontoägare begränsa åtkomsten till vissa roller och inte öppna den för alla användare med en aktiv CRM-licens. Med den avancerade konfigurationen kan du mappa dina CRM-roller och CRM-grupper till [!DNL Marketo Measure] användarbehörigheter.

Om inga roller eller grupper mappas är standardinställningen att alla aktiva licenser i CRM har standardanvändaråtkomst.

* [!DNL Marketo Measure] Standardanvändare: Ange roll- eller gruppvärdet för användare som ska ha skrivskyddad åtkomst till programmet [!DNL Marketo Measure].
* [!DNL Marketo Measure]-kontoadministratörsanvändare: Ange rollen eller gruppvärdet för användare som ska ha administrativ åtkomst till programmet [!DNL Marketo Measure]. Detta innebär att rollen har åtkomst till att ändra konfigurationer och inställningar som är relaterade till ditt konto.

Om flera roller eller grupper ska mappas till en roll anger du varje värde avgränsat med kommatecken.

**Salesforce-roller**

Använd namnet på varje roll för [!DNL Salesforce]-roller. Alla roller finns på menyn [!UICONTROL Setup] >[!UICONTROL Manage Users] >[!UICONTROL Roles].

![För Salesforce-roller använder du namnet på varje roll. Alla roller](assets/discover-control-3.png)

**Dynamics-roller**

Använd namnet på varje säkerhetsroll för [!DNL Dynamics]-roller. Alla säkerhetsroller finns på menyn [!UICONTROL Settings] >[!UICONTROL Security] >[!UICONTROL Security Roles].

![Använd namnet på varje säkerhetsroll för Dynamics-roller. Alla](assets/discover-control-3.png)

![Använd namnet på varje säkerhetsroll för Dynamics-roller. Alla](assets/discover-control-3.png)

**Google-användare**

När Anpassad enkel inloggning har konfigurerats uppdateras sidan [!UICONTROL Users] så att endast externa användare som har lagts till med Google-inloggningar visas. Eftersom alla användare med åtkomst definieras via SSO-konfigurationen, visas ytterligare externa användare här.

![När anpassad enkel inloggning har konfigurerats är sidan Användare &#x200B;](assets/discover-control-3.png)

Endast giltiga [!DNL Google]-konton kan läggas till och måste ha en användarroll definierad.

## Externa länkar {#external-links}

* [Okta](https://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Ping-identitet](https://docs.pingidentity.com:443/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](https://onelogin.service-now.com/support?id=kb_article&sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
