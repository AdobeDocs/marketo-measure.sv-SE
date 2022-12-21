---
unique-page-id: 18874761
description: Enkel inloggning - [!DNL Marketo Measure] - Produktdokumentation
title: Enkel inloggning
exl-id: a328e9cb-8352-4693-8a44-533e08f1a29c
source-git-commit: 09ffdbb0b1baeed870a3145268997e63a3707c97
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 0%

---

# Enkel inloggning {#single-sign-on}

SAML (Security assertion markup language) för enkel inloggning (single sign-on) gör det möjligt för användare att autentisera via ett företags identitetsleverantör när de loggar in på [!DNL Marketo Measure] app. Med enkel inloggning kan användaren bara autentisera en gång utan att behöva autentisera separata appar. SAML är en nödvändighet för företagskunder eftersom inte alla användare har [!DNL Salesforce] eller [!DNL Google] inom organisationen. För att kunna skala [!DNL Marketo Measure] har utvecklat en SAML-lösning som kan stödja leverantörer av företagsidentiteter.

>[!CAUTION]
>
>I den här artikeln beskrivs enkel inloggning (SSO) och avancerad CRM-användarhantering. Om ditt konto har etablerats **efter den 10 september 2020**, ignorera den här artikeln eftersom enkel inloggning och Identity Management kommer att konfigureras i [Adobe Admin Console för [!DNL Marketo Measure] integration](/help/configuration-and-setup/getting-started-with-marketo-measure/marketo-measure-quick-start.md).

>[!NOTE]
>
>Det är sannolikt att företag använder olika identitetsleverantörer (t.ex. Ping Identity, Okta). De termer som används i följande konfigurationsinstruktioner och i användargränssnittet kanske inte matchar de som används av din identitetsleverantör.

## Krav {#requirements}

* Användare med AccountAdmin-behörighet i [!DNL Marketo Measure] App
* Användare med administrativ åtkomst till kundens identitetsleverantör

## Komma igång {#getting-started}

Navigera till Inställningar > Säkerhet > Autentisering på sidan [!DNL Marketo Measure] program. Växla sedan inloggningstypen till Anpassad enkel inloggning för att se konfigurationsalternativen. Ändringarna börjar inte gälla förrän du testar autentiseringen och klickar på **[!UICONTROL Save]** längst ned på sidan.

![](assets/single-sign-on-1.png)

## Process {#process}

[!DNL Marketo Measure] För enkel inloggning krävs att du konfigurerar dina autentiseringsinställningar i en serie steg som är viktiga att följa så att du inte riskerar att bli låst från din [!DNL Marketo Measure] konto.

Konfigurera [!DNL Marketo Measure] Program i din identitetsleverantör. Se extern dokumentation som listas nedan för genomgångar.

    a. När du uppmanas att ange URL för enkel inloggning eller mottagarens URL eller mål-URL använder du [https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest](https://apps.bizible.com/BizibleSAML2/ReceiveSSORequest)
    
    b. När du uppmanas att ange målgruppsbegränsnings-URL eller programdefinierad unik identifierare använder du [https://BizibleLPM](https://biziblelpm/)

Växla till anpassad enkel inloggning i dialogrutan [!DNL Marketo Measure] Program

    a. När faktureringsgruppen har aktiverats för ditt konto kan du nu gå till [!UICONTROL Settings] >>[!UICONTROL Security] >> [!UICONTROL Authentication]
    
    b. Som standard anges din inloggningstyp till &quot;CRM-användare&quot;.
    
    c. Växla inloggningstypen till Anpassad enkel inloggning för att starta konfigurationsprocessen.

Fyll i anslutningsinställningarna för din identitetsleverantörskonfiguration

    a. Din identitetsleverantör kan ge ett IdP-metadatadatadokument (XML) som tar bort de konfigurationsfält som krävs. Läs antingen in innehållet i XML-dokumentet eller fyll i de tre fälten nedan från utdata som erhållits under konfigurationsprocessen för identitetsleverantören. **Du behöver inte fylla i båda.**
    
    i. IdP-URL: Den URL som [!DNL Marketo Measure] måste peka på för att autentisera användarna i [!DNL Marketo Measure] program. Kallas ibland &quot;Omdirigerings-URL&quot;.
    ii. IdP-utfärdare: En unik identifierare för identitetsleverantören. Kallas ibland &quot;extern nyckel&quot;.
    iii. IdP-certifikat: En offentlig nyckel som tillåter [!DNL Marketo Measure] verifiera och validera signaturen för alla identitetsleverantörssvar.

Ange utgångsdatum för token för dina användare på några minuter.

    a. [!DNL Marketo Measure] tillåter ett heltal mellan 1 och 1 440 minuter. När användarens sessionstid har överskridits loggas användaren ut när han/hon navigerar till en ny sida.

Ange och mappa inställningarna för användarattributet till respektive förnamn, efternamn och e-postadress.

    a. Genom att ange SAML-attributen [!DNL Marketo Measure] kommer att kunna känna igen dina användare genom den information som skickas.
    
    i. E-postattribut: Ange det attributnamn som identitetsleverantören använder för användarens e-postadress.
    ii. Förnamnsattribut: Ange det attributnamn som identitetsleverantören använder för användarens förnamn.
    iii. Efternamnsattribut: Ange det attributnamn som identitetsleverantören använder som användarens efternamn.
    
    b. Tips: Om du testar din SAML-konfiguration nu kommer vi att analysera attributen E-post, Förnamn och Efternamn som du kan använda för det här avsnittet.

![](assets/single-sign-on-2.png)

Konfigurera och mappa dina användarrollsinställningar till respektive roller eller grupper som klassificerats från din IdP.

    a. Kunderna kan välja att tilldela [!DNL Marketo Measure] användarroller baserade på grupper definierade i deras identitetsleverantör. Genom att ange dina SAML-attribut [!DNL Marketo Measure] kan mappa din användares roller och grupper till [!DNL Marketo Measure] användarbehörigheter. Vi rekommenderar att du skapar de här rollerna så att [!DNL Marketo Measure] administratören har behörighet att uppdatera ditt konto.
    
    b. Om inga roller eller grupper mappas är standardinställningen att alla anställda i identitetsleverantören har standardanvändaråtkomst.
    
    i. [!DNL Marketo Measure] Standardanvändare: Ange rollen eller gruppvärdet (från din SSO-leverantör) för användare som ska ha skrivskyddad åtkomst till [!DNL Marketo Measure] program.
    ii. [!DNL Marketo Measure] Kontoadministratörsanvändare: Ange rollen eller gruppvärdet (från din SSO-leverantör) för användare som ska ha administrativ åtkomst till [!DNL Marketo Measure] program. Detta innebär att rollen har åtkomst till att ändra konfigurationer och inställningar som är relaterade till ditt konto.
    iii. Du måste ha ett attribut i din IdP med det exakta namnet &quot;groups&quot; som innehåller de värden du angett i attributen &quot;Bizible Standard User&quot; eller &quot;Bizible Account Admin User&quot;.
    
    c. Om flera roller eller grupper ska mappas till en roll anger du varje värde avgränsat med kommatecken.

![](assets/single-sign-on-3.png)

Testa konfigurationen för enkel inloggning

    a. Innan du kan trycka på Spara måste du klicka på [!UICONTROL Test SAML Authentication] för att verifiera att inställningarna är korrekt konfigurerade.
    
    b. Om ett fel uppstår följer du meddelandet och försöker igen.

![](assets/single-sign-on-4.png)

Spara inställningarna och instruera dina kollegor att använda [!UICONTROL Single Sign On] med din nya anpassade inloggnings-URL.

    a. Viktigt: När du har sparat dina nya autentiseringsinställningar kan det hända att sessionen avslutas när du navigerar till en ny sida, eftersom du har inaktiverat inloggning av CRM-användare och aktiverat Anpassad enkel inloggning.

![](assets/single-sign-on-5.png)

Prova!

    a. Använd din nya anpassade inloggnings-URL och försök logga in igen på [!DNL Marketo Measure] Program med din identitetsleverantörs autentiseringsuppgifter.
    
    b. Formatet kommer att se ut som &quot;https://apps.adobe.com/business/[accountName]&quot;
    
    c. Grattis! Du har konfigurerat enkel inloggning i [!DNL Marketo Measure] Ansökan för ditt konto!

![](assets/single-sign-on-6.png)

>[!NOTE]
>
>När du har konfigurerat enkel inloggning behöver du inte längre lägga till användare i [!DNL Marketo Measure] program. Etablering av användare bör hanteras direkt i identitetsleverantören.

## CRM-användare (avancerad inställning) {#crm-users-advanced-setup}

Som standard har alla konton åtkomst till [!DNL Marketo Measure] program som använder sina CRM-autentiseringsuppgifter. Ibland måste kontoägare begränsa åtkomsten till vissa roller och inte öppna den för alla användare med en aktiv CRM-licens. Med den avancerade konfigurationen kan du mappa dina CRM-roller och CRM-grupper till [!DNL Marketo Measure] användarbehörigheter.

Om inga roller eller grupper mappas är standardinställningen att alla aktiva licenser i CRM har standardanvändaråtkomst.

* [!DNL Marketo Measure] Standardanvändare: Ange rollen eller gruppvärdet för användare som ska ha skrivskyddad åtkomst till [!DNL Marketo Measure] program.
* [!DNL Marketo Measure] Kontoadministratörsanvändare: Ange rollen eller gruppvärdet för användare som ska ha administrativ åtkomst till [!DNL Marketo Measure] program. Detta innebär att rollen har åtkomst till att ändra konfigurationer och inställningar som är relaterade till ditt konto.

Om flera roller eller grupper ska mappas till en roll anger du varje värde avgränsat med kommatecken.

**Salesforce-roller**

För [!DNL Salesforce] Roller, använd namnet på varje roll. Alla roller finns under [!UICONTROL Setup] >[!UICONTROL Manage Users] >[!UICONTROL Roles] -menyn.

![](assets/6.png)

**Dynamics-roller**

För [!DNL Dynamics] Roller, använd namnet på varje säkerhetsroll. Alla säkerhetsroller finns under [!UICONTROL Settings] >[!UICONTROL Security] >[!UICONTROL Security Roles] -menyn.

![](assets/7.png)

![](assets/8.png)

**Google-användare**

När en anpassad enkel inloggning har konfigurerats [!UICONTROL Users] sidan uppdateras så att endast externa användare som har lagts till med Google-inloggningar visas. Eftersom alla användare med åtkomst definieras via SSO-konfigurationen, visas ytterligare externa användare här.

![](assets/9.png)

Endast giltig [!DNL Google] konton kan läggas till och måste ha en användarroll definierad.

## Externa länkar {#external-links}

* [Okta](http://developer.okta.com/standards/SAML/setting_up_a_saml_application_in_okta)
* [Ping-identitet](http://docs.pingidentity.com/bundle/p1_enterpriseConfigSsoSaml_cas/page/enableAppWithoutURL.html)
* [OneLogin](http://onelogin.service-now.com/support?id=kb_article&amp;sys_id=b2c91143db109700d5505eea4b9619d5)
* [Active Directory](http://docs.microsoft.com/en-us/azure/active-directory/active-directory-saas-custom-apps)
