---
description: Bästa praxis för användning av ett anpassat intäktsbelopp - [!DNL Marketo Measure]
title: Bästa metoder för att använda ett anpassat intäktsbelopp
exl-id: 553bd75a-512a-4733-a24b-8112eb420afc
feature: Custom Revenue Amount
source-git-commit: 915e9c5a968ffd9de713b4308cadb91768613fc5
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Bästa metoder för att använda ett anpassat intäktsbelopp {#best-practices-for-utilizing-a-custom-revenue-amount}

## Översikt {#overview}

Kärnfunktionerna i [!DNL Marketo Measure] är möjligheten att tillföra intäktskrediter till marknadsföringskontaktytor under hela kundresan. Nyckeln till korrekt intäktsattribuering är möjligheten att [!DNL Marketo Measure] för att hänvisa till rätt intäktsbelopp för ett säljprojekt, som i sin tur fördelas över alla kontaktytor för marknadsföring via de olika attribueringsmodellerna.

Om inget annat anges under implementeringen kan du [!DNL Marketo Measure] -instansen ställs in på att referera till standardbeloppet för affärsmöjlighet (SFDC-standard) för intäktsattribuering. För många [!DNL Marketo Measure] konton, detta fält återspeglar inte det korrekta intäktsbeloppet för affärsmöjligheter. I dessa fall [!DNL Marketo Measure] erbjuder möjlighet att ställa in ett Custom Revenue Amount för [!DNL Marketo Measure] referera till och distribuera via attribueringsslutpunkterna (BAT).

## Bästa praxis {#best-practice}

När du ställer in ett Custom Revenue Amount (Anpassat intäktsbelopp) bör du tänka på följande för att säkerställa att [!DNL Marketo Measure] attribueringsdata är korrekta och konsekventa!

Tänk på följande:

* Välj det intäktsfält som är korrekt och som används för alla affärsmöjligheter
   * ARR- eller Total Contract-värde rekommenderas
* Använd inte ett formelfält
* Om du använder ett Custom Revenue Amount (Anpassat intäktsbelopp) för valutakonverteringar visas [!UICONTROL Marketo Measure Multiple Currencies] i stället är det den metod du föredrar.
   * The [!DNL Marketo Measure] Funktionen Flera valutor refererar till de konverteringsgrader som fastställts i [!DNL Salesforce] för att på bästa sätt säkerställa justeringen mellan valutakonverteringar. Detta gör att du kan fortsätta använda standardvärdet för Belopp (SFDC-standard) eller något annat anpassat beloppsfält som relaterar till [!DNL Salesforce] konverteringsgrader.
* Om du uppdaterar fältet Belopp vill du ha [!DNL Marketo Measure] som referens kan du använda datainläsaren för att uppdatera tidigare affärsmöjligheter för att säkerställa att dina intäktsdata är konsekventa och att rätt fält fylls i via arbetsflödet

## Bästa praxis för underhåll {#best-practice-for-maintenance}

Om du granskar intäktsbeloppet årligen ser du till att dina attribueringsdata är korrekta och anpassade till resten av organisationens intäktsrapportering.

Om du använder ett anpassat intäktsbelopp kontrollerar du dina intäktsinställningar enligt följande.

* I [!DNL Marketo Measure] konto, gå till[!UICONTROL Opportunities]&#39;-sektion under CRM
* Identifiera [!UICONTROL Custom Opportunity Amount] Field, here your [!UICONTROL custom revenue amount API] ska anges
* Bekräfta att detta fortfarande är rätt fält
* Du kan även [!DNL Salesforce] Administratören bekräftar att arbetsflödet för anpassade intäktsbelopp i [!DNL Salesforce] körs fortfarande

Förutom en årlig översyn kan vissa organisatoriska förändringar signalera att du behöver granska intäktsbeloppet...

* Omsättning i marknadsföringsteamet
* Ändringar i fältet Anpassad intäkt
* Organisationen har ändrat hur intäkter rapporteras

>[!MORELIKETHIS]
>
>* [Använda fältet Anpassat intäktsbelopp](/help/advanced-marketo-measure-features/custom-revenue-amount/using-a-custom-revenue-amount-field.md)
>* [Uppdatera fält för anpassat belopp med datainläsaren](/help/advanced-marketo-measure-features/custom-revenue-amount/using-data-loader-to-update-marketo-measure-custom-amount-field.md)
>* [Översikt över flera valutor](/help/advanced-marketo-measure-features/multi-currency/overview.md)
>* [Inställningar för flera valutor](/help/advanced-marketo-measure-features/multi-currency/settings.md)
