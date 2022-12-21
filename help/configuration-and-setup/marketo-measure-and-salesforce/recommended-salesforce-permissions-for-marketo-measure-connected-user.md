---
unique-page-id: 18874696
description: Rekommenderas [!DNL Salesforce] Behörigheter för [!DNL Marketo Measure] Ansluten användare - [!DNL Marketo Measure] - Produktdokumentation
title: Rekommenderas [!DNL Salesforce] Behörigheter för [!DNL Marketo Measure] Ansluten användare
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Rekommenderas [!DNL Salesforce] Behörigheter för [!DNL Marketo Measure] Ansluten användare {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] skickar och tar emot data via en ansluten [!DNL Salesforce] användare inom [!DNL Marketo Measure] app.

För att skicka data till kontaktytan [!DNL Salesforce] -instans måste den anslutna användaren ha åtkomst till [!DNL Marketo Measure] anpassade objekt (t.ex. Buyer Touchpoint och Buyer Attribution Touchpoint) samt standard [!DNL Salesforce] objekt som leads och kontakter (se [[!DNL Marketo Measure] i Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Administratörsanvändarlicenser kan fungera som den anslutna användaren eftersom de ofta har de nödvändiga databehörigheterna som standard. Ditt team kanske föredrar att använda en integreringsanvändare eller en dedikerad [!DNL Salesforce] användarlicens för att spåra effekten av [!DNL Marketo Measure] på din instans.

Vi rekommenderar följande behörigheter för att säkerställa att [!DNL Marketo Measure] data flödar korrekt:

* [!DNL Marketo Measure] Administratörsbehörighet för dedikerad användare

Den hanterade behörighetsgruppen ger en SFDC-administratör möjlighet att skapa, läsa, skriva, ta bort poster från [!DNL Marketo Measure] objekt.

* Visa och redigera behörighetsgrupp för konverterade leads

Detta gör att [!DNL Marketo Measure] för att dekorera leads efter att de har konverterats till kontakter. Om den här behörighetsgruppen inte är aktiverad kan det finnas stora luckor i dataspårningen. Mer information finns i [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/articleView?id=leads_view_edit_converted.htm&amp;type=5).

* [!DNL Salesforce] Marknadsföringsanvändarkryssruta

The [!UICONTROL Marketing User] Med kryssrutan kan användaren skapa kampanjer och använda guiden för kampanjimport. Om det här alternativet inte är markerat kan användaren bara visa kampanjer och avancerade kampanjinställningar, redigera kampanjhistoriken för en enskild lead eller kontakt och köra kampanjrapporter. [!DNL Marketo Measure] måste kunna läsa och skriva till kampanjobjektet.

**Ytterligare felsökning**

If [!DNL Marketo Measure] har fortfarande problem med att läsa eller skriva data. Det kan vara bra att undersöka följande:

* Åtkomst till [!DNL Salesforce] Köer

Om den dedikerade användaren inte har åtkomst till leads i köer kan den inte ändra leads med [!DNL Marketo Measure] data. Du kan uppnå detta genom att ha en roll i hierarkin som tillåter åtkomst till köer eller individuell behörighet för användare.

* Fältnivåsäkerhet och tillgänglighet

Fältnivåsäkerhet och fälttillgänglighet är relaterade men har vissa viktiga skillnader. Fältnivåsäkerhet definierar fältsynlighet för en viss profil medan Fälttillgänglighet avgör om ett fält kan redigeras baserat på fältnivåsäkerhet och sidlayoutskonfiguration. Använda [!DNL Marketo Measure] paketets behörighetsgrupper du kommer att få de nödvändiga säkerhetsinställningarna för fältobjekt. I vissa fall måste den anslutna användaren ha [!DNL Marketo Measure] fält på sidlayouten. [!DNL Marketo Measure] -fält i layouten tillåter [!DNL Marketo Measure] data att mappa till [!DNL Salesforce]. Detta beror på din [!DNL Salesforce] miljö.

Alla organisationer [!DNL Salesforce] har individuella behov, men vi förser dig med våra krav för att balansera [!DNL Marketo Measure] med era säkerhetsprotokoll. Tveka inte att nå ut till [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target=&quot;_blank&quot;}.
