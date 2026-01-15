---
description: Arbetsflöden för att justera Dynamics-intäkter och stängningsdatumfält för Marketo Measure-rapportering
title: '[!DNL Marketo Measure] intäktsarbetsflöden för Dynamics'
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: fcd8e276c85669ddf12bd7404fb12d3e99b2642a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# [!DNL Marketo Measure] intäktsarbetsflöden för Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Del 1: Uppskattad intäkt kontra faktisk intäkt {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pekar på ett standardintäktsfält utanför rutan (Faktisk intäkt), men Dynamics har två standardintäktsfält: Faktisk intäkt och Uppskattad intäkt. Om du vill att pipeline-intäkter ska vara tillgängliga i Discover Dashboard behövs ett anpassat fält och ett arbetsflöde för att hämta korrekt belopp från antingen fältet för beräknad intäkt eller Faktisk intäkt beroende på om affärsmöjligheten är öppen eller stängd (Won).

Steg 1: Skapa fält för anpassat affärsmöjlighetsbelopp i Dynamics

>[!NOTE]
>
>Alla Dynamics-intäktsfält har ett basfält och ett vanligt fält. Ignorera basfältet.

Steg 2: Skapa ett arbetsflöde som uppdaterar både det anpassade fältet för affärsmöjlighetsbelopp som skapats i steg 1 och fältet för [!DNL Marketo Measure] säljprojektsbelopp.

>[!NOTE]
>
>Det går inte att peka på fältet [!DNL Marketo Measure] Affärsmöjlighet (bizible2_bizible_Opportunity_amount) i Identifiera med Dynamics-konton. Dynamics-kunder måste skapa ett anpassat fält för affärsmöjlighetsbelopp för [!DNL Marketo Measure] att peka på i Discover. När det är klart måste kunden skapa ett arbetsflöde som uppdaterar **både** och [!DNL Marketo Measure] fältet för det anpassade affärsmöjlighetsbeloppet (bizible2_bizible_Opportunity_amount) **och**. Fältet [!DNL Marketo Measure] för säljprojektsbelopp levereras med paketet, men ett anpassat fält måste skapas.

Instruktioner för arbetsflöde:

**ARBETSFLÖDE nr 1**: Möjlighet - uppdatera [!DNL Marketo Measure] Fält för säljprojektsbelopp och anpassat fält = Uppskattad intäkt

Det här arbetsflödet körs på öppna affärsmöjligheter varje gång en beräknad intäkt ändras och uppdaterar fältet [!DNL Marketo Measure] Affärsmöjlighet och ditt anpassade fält så att det motsvarar fältet Beräknad intäkt. Arbetsflödet ska vara inställt på att köras i realtid, men kan även köras på begäran för att uppdatera öppna affärsmöjligheter.

Ange kontaktpunkten för [!DNL Marketo Measure] med namnet på fältet för anpassat affärsmöjlighetsbelopp. De uppdaterar inställningarna för [!DNL Marketo Measure]-appmöjlighet så att de innehåller namnet på fältet för det anpassade affärsmöjlighetsbeloppet. Detta anger vilket fält som ska användas vid rapportering.

**ARBETSFLÖDE nr 2**: Möjlighet - uppdatera [!DNL Marketo Measure] Fält för säljprojektsbelopp och anpassat fält = Faktisk intäkt

Det här arbetsflödet startar när en användare stänger ett säljprojekt och uppdaterar fältet [!DNL Marketo Measure] för säljprojektsbelopp och ditt anpassade fält med den faktiska intäkten i formuläret för stängning av säljprojekt innan affärsmöjligheten låses som stängd.

## Del 2: Beräknat stängningsdatum kontra faktiskt stängningsdatum {#part-estimated-close-date-vs-actual-close-date}

Inkomstdata för försäljningsförlopp är inte tillgängliga i instrumentpanelen eftersom Dynamics som standard har två fält för stängningsdatum för lagerställe: Beräknat stängningsdatum och Faktiskt stängningsdatum. [!DNL Marketo Measure] kan bara peka på ett stängningsdatumfält i instrumentpanelen och pekar på det faktiska stängningsdatumet.

Om öppna affärsmöjligheter saknar data i fältet Faktiskt stängningsdatum finns det inga data i instrumentpanelen för öppna affärsmöjligheter. Det behövs dock ett arbetsflöde baserat på affärsmöjlighetens fas för att stödja båda datumfälten.

1. Skapa anpassat stängningsdatumfält för säljprojektsobjektet ([!DNL Marketo Measure] anpassat stängningsdatum).
1. Skapa ett arbetsflöde för att uppdatera fältet [!DNL Marketo Measure] Anpassat stängningsdatum med datumet från antingen det beräknade stängningsdatumet eller det faktiska stängningsdatumet, beroende på om affärsmöjligheten är öppen eller stängd (arbetsflödet ska sparas för körning i realtid, men måste köras på begäran minst en gång för att uppdatera alla öppna öppningar).
1. Testa arbetsflödet och bekräfta att det fungerar.
1. Kunden måste ange API-namnet för det anpassade stängningsdatumet till [!DNL Marketo Measure].
1. [!DNL Marketo Measure] om du vill uppdatera appinställningarna för [!DNL Marketo Measure] så att de pekar på fältet [!DNL Marketo Measure] Anpassat stängningsdatum i instrumentpanelen.

   När du har slutfört stegen ovan kör du arbetsflödena för att uppdatera både fältet för anpassat [!DNL Marketo Measure] Opp-belopp och fältet [!DNL Marketo Measure] Anpassat stängningsdatum för dina historiska möjligheter så att rätt data återges. Detta ändrar troligen de ändrade fälten på/efter så att du bör kontrollera med ditt team om detta ger några problem.

Så här uppdaterar du stängda affärsmöjligheter..

1. Isolera affärsmöjligheter som har stängts sedan ditt [!DNL Marketo Measure]-startdatum fram till dess att arbetsflödet är aktivt. Detta är gruppen med historiska möjligheter som du måste uppdatera via arbetsflöde.
1. Exportera alla poster till Excel.
1. Öppna Excel-fil, aktivera innehåll.
1. Kopiera faktiska stängningsdatumdata till [!DNL Marketo Measure] anpassat stängningsdatum.
1. Kopiera faktiska intäktsdata till [!DNL Marketo Measure] belopp för anpassade affärsmöjligheter **och** [!DNL Marketo Measure] Affärsmöjlighet (det finns två fält).
1. Spara filen.
1. Importera fil. Dynamics identifierar detta som en fil med befintliga poster att uppdatera.
1. Kontrollera om det inte går att importera filen.

>[!NOTE]
>
>De arbetsflöden som beskrivs i det här dokumentet är bara ett sätt att uppdatera fälten så att [!DNL Marketo Measure] kan visa rätt data i Identifiera. Om du har ett annat sätt att utföra samma uppgift kan du göra det. Det vi behöver av dem är något slags arbetsflöde som gör följande:
>
> * Om Opp = Open, uppdatera anpassat stängningsdatumfält, anpassat snabbbeloppsfält och [!DNL Marketo Measure] popup-beloppsfält till samma beräknade stängningsdatum respektive beräknade intäkt.
> * Om Opp = Closed Won, uppdatera det anpassade stängningsdatumfältet, det anpassade snabbbeloppsfältet och fältet [!DNL Marketo Measure] popup-belopp till samma faktiska stängningsdatum respektive faktiska omsättning.
