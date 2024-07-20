---
description: Bästa tillvägagångssätt för att använda ett anpassat intäktsbelopp - [!DNL Marketo Measure]
title: Bästa metoder för att använda ett anpassat intäktsbelopp
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Bästa metoder för att använda ett anpassat intäktsbelopp {#best-practices-for-utilizing-a-custom-revenue-amount}

## Översikt {#overview}

Kärnfunktionen i [!DNL Marketo Measure] är möjligheten att tilldela intäktskrediter till marknadsföringskontaktytor under köparens resa. Nyckeln till korrekt intäktsattribuering är möjligheten för [!DNL Marketo Measure] att referera till rätt intäktsbelopp för ett säljprojekt, som i sin tur fördelas över alla kontaktytor för marknadsföring via de olika attribueringsmodellerna.

Om inget annat anges under implementeringen kommer instansen [!DNL Marketo Measure] att anges som referens för standardbeloppet för affärsmöjlighet (SFDC-standard) för intäktsattribuering. För många [!DNL Marketo Measure]-konton återspeglar dock det här fältet inte det korrekta intäktsbeloppet för affärsmöjligheter. I de här instanserna erbjuder [!DNL Marketo Measure] möjligheten att ställa in ett anpassat intäktsbelopp för [!DNL Marketo Measure] att referera till och distribuera över attributets slutpunkter (BAT).

## Bästa praxis {#best-practice}

När du konfigurerar ett anpassat intäktsbelopp bör du tänka på följande bästa praxis för att se till att dina [!DNL Marketo Measure]-attribueringsdata är korrekta och konsekventa!

Tänk på följande:

* Välj det intäktsfält som är korrekt och som används för alla affärsmöjligheter
   * ARR- eller Total Contract-värde rekommenderas
* Använd inte ett formelfält
* Om du använder ett anpassat intäktsbelopp för valutakonverteringar är funktionen [!UICONTROL Marketo Measure Multiple Currencies] att föredra i stället.
   * Funktionen [!DNL Marketo Measure] Flera valutor refererar till de konverteringsgrader som upprättats i [!DNL Salesforce] för att optimera justeringen mellan valutakonverteringar. Detta gör att du kan fortsätta använda standardvärdet för Belopp (SFDC-standard) eller något annat anpassat beloppsfält som relaterar till konverteringsgraden [!DNL Salesforce].
* Om du uppdaterar det beloppsfält som du vill att [!DNL Marketo Measure] ska referera till använder du Datainläsaren för att uppdatera tidigare affärsmöjligheter för att säkerställa att dina intäktsdata är konsekventa och att rätt fält fylls i via arbetsflödet

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar intäktsbeloppet årligen ser du till att dina attribueringsdata är korrekta och anpassade till resten av organisationens intäktsrapportering.

Om du använder ett anpassat intäktsbelopp kontrollerar du dina intäktsinställningar enligt följande.

* Gå till avsnittet [!UICONTROL Opportunities] i ditt [!DNL Marketo Measure]-konto under CRM
* Identifiera fältet [!UICONTROL Custom Opportunity Amount], här ska fältet [!UICONTROL custom revenue amount API] listas
* Bekräfta att detta fortfarande är rätt fält
* Be även din [!DNL Salesforce]-administratör bekräfta att arbetsflödet för anpassade intäktsbelopp i [!DNL Salesforce] fortfarande körs

Förutom en årlig översyn kan vissa organisatoriska förändringar signalera att du behöver granska intäktsbeloppet...

* Omsättning i marknadsföringsteamet
* Ändringar i fältet Anpassad intäkt
* Organisationen har ändrat hur intäkter rapporteras

>[!MORELIKETHIS]
>
>* [Använda ett fält för anpassade intäktsbelopp](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Använder datainläsaren för att uppdatera fält för anpassat belopp](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Översikt över flervaluta](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Inställningar för flera valutor](/help/advanced-marketo-measure-features/multi-currency/settings.md)
