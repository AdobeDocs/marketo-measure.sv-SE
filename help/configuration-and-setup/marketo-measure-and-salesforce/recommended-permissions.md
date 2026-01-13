---
description: Rekommenderad [!DNL Salesforce] behörighet för [!DNL Marketo Measure] Ansluten användare - [!DNL Marketo Measure]
title: Rekommenderad [!DNL Salesforce] behörighet för [!DNL Marketo Measure] ansluten användare
exl-id: b74aa28b-4a7b-42d1-8df0-d1ae0ff1f338
feature: Salesforce
source-git-commit: c6090ce0c3ac60cd68b1057c369ce0b3b20aeeee
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Rekommenderade [!DNL Salesforce] behörigheter för [!DNL Marketo Measure]-anslutna användare {#recommended-salesforce-permissions-for-marketo-measure-connected-user}

[!DNL Marketo Measure] skickar och tar emot data via en ansluten [!DNL Salesforce]-användare i [!DNL Marketo Measure]-appen.

Om du vill skicka kontaktpunktsdata till [!DNL Salesforce]-instansen måste den anslutna användaren ha tillgång till [!DNL Marketo Measure] anpassade objekt (dvs. Buyer Touchpoint och Buyer Attribution Touchpoint) samt [!DNL Salesforce] standardobjekt som leads och kontakter. Se [[!DNL Marketo Measure] i Salesforce](/help/configuration-and-setup/marketo-measure-and-salesforce/how-marketo-measure-and-salesforce-interact.md).

[!DNL Salesforce] Administratörsanvändarlicenser kan fungera som den anslutna användaren eftersom de ofta har nödvändiga databehörigheter som standard. Ditt team kanske föredrar att använda en integreringsanvändare eller en dedikerad [!DNL Salesforce]-användarlicens för att spåra [!DNL Marketo Measure] effekt på din instans.

Vi rekommenderar följande behörigheter för att säkerställa att [!DNL Marketo Measure]-data flödar korrekt:

* [!DNL Marketo Measure] Administratörsbehörighetsuppsättning för dedikerad användare

Den hanterade behörighetsgruppen ger en SFDC-administratör möjlighet att skapa, läsa, skriva och ta bort poster från [!DNL Marketo Measure]-objekt.

* Visa och redigera behörighetsgrupp för konverterade leads

Detta gör att [!DNL Marketo Measure] kan dekorera leads efter att de har konverterats till kontakter. Om den här behörighetsgruppen inte är aktiverad kan det finnas stora luckor i dataspårningen. Mer information finns i [[!DNL Salesforce Trailblazer] community](https://help.salesforce.com/s/articleView?language=en_US&id=leads_view_edit_converted.htm&type=5).

* Kryssrutan [!DNL Salesforce] för marknadsföringsanvändare

Med kryssrutan [!UICONTROL Marketing User] kan användaren skapa kampanjer och använda guiden för kampanjimport. Om det här alternativet inte väljs kan användaren bara visa kampanjer och avancerade kampanjinställningar, redigera kampanjhistoriken för en enskild lead eller kontakt och köra kampanjrapporter. [!DNL Marketo Measure] måste kunna läsa och skriva till kampanjobjektet.

**Ytterligare felsökning**

Om [!DNL Marketo Measure] fortfarande har problem med att läsa eller skriva data kan det vara bra att undersöka följande:

* Åtkomst till [!DNL Salesforce] köer

Om den dedikerade användaren inte har åtkomst till leads i köer kan den inte ändra leads med [!DNL Marketo Measure]-data. Du kan uppnå detta genom att ha en roll i hierarkin som tillåter åtkomst till köer eller individuell behörighet för användare.

* Fältnivåsäkerhet och tillgänglighet

Fältnivåsäkerhet och fälttillgänglighet är relaterade men har vissa viktiga skillnader. Fältnivåsäkerhet definierar fältsynlighet för en viss profil medan Fälttillgänglighet avgör om ett fält är redigerbart baserat på fältnivåsäkerhet och sidlayoutskonfiguration. Med hjälp av behörighetsuppsättningarna för paketet [!DNL Marketo Measure] får du de nödvändiga säkerhetsinställningarna för fältobjekt. Ibland måste den anslutna användaren ha [!DNL Marketo Measure]-fälten på sidlayouterna för att kunna ha rätt fälttillgänglighet. [!DNL Marketo Measure] fält i layouten tillåter att [!DNL Marketo Measure]-data mappas till [!DNL Salesforce]. Detta beror på just din [!DNL Salesforce]-miljö.

Varje organisations [!DNL Salesforce] har individuella behov, men vi tillhandahåller våra krav för att balansera [!DNL Marketo Measure]-åtkomstbehoven med dina säkerhetsprotokoll. Tveka inte att nå ut till [[!DNL Marketo Support]](https://nation.marketo.com/t5/support/ct-p/Support){target="_blank"}.
