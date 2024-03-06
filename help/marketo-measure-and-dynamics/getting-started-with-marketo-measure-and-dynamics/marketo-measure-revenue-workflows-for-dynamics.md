---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics - [!DNL Marketo Measure]"
title: "[!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
feature: Microsoft Dynamics
source-git-commit: 9e672d0c568ee0b889461bb8ba6fc6333edf31ce
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---

# [!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Del 1: Uppskattad intäkt kontra faktisk intäkt {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pekar på ett standardintäktsfält utanför rutan (Faktisk intäkt) men Dynamics har två standardintäktsfält: Faktisk intäkt och Uppskattad intäkt. Om du vill att pipeline-intäkter ska vara tillgängliga i Discover Dashboard behövs ett anpassat fält och ett arbetsflöde för att hämta korrekt belopp från antingen fältet för beräknad intäkt eller Faktisk intäkt beroende på om affärsmöjligheten är öppen eller stängd (Won).

Steg 1: Skapa fält för anpassat affärsmöjlighetsbelopp i Dynamics

>[!NOTE]
>
>Alla Dynamics-intäktsfält har ett basfält och ett vanligt fält. Ignorera basfältet.

Steg 2: Skapa ett arbetsflöde som uppdaterar både det anpassade fältet för affärsmöjlighetsbelopp som skapats i steg 1 och [!DNL Marketo Measure] Fältet Affärsmöjlighet.

>[!NOTE]
>
>Vi kan inte peka på [!DNL Marketo Measure] Affärsmöjlighetens belopp (bizible2_bizible_Opportunity_amount) i fältet Discover with Dynamics accounts. Dynamics-kunder måste skapa ett anpassat fält för affärsmöjlighetsbelopp för [!DNL Marketo Measure] till Discover. När det är klart måste kunden skapa ett arbetsflöde som uppdateras **båda** den [!DNL Marketo Measure] Affärsmöjlighet (bizible2_bizible_Opportunity_amount) **och** det anpassade fältet för affärsmöjlighetsbelopp. The [!DNL Marketo Measure] Fältet Affärsmöjlighet levereras med paketet, men ett anpassat fält måste skapas.

Instruktioner för arbetsflöde:

**ARBETSFLÖDE nr 1**: Möjligheter - uppdatering [!DNL Marketo Measure] Fält för affärsmöjlighet och anpassat fält = Uppskattad intäkt

Det här arbetsflödet körs på öppna affärsmöjligheter varje gång en beräknad intäkt ändras och uppdaterar [!DNL Marketo Measure] Fältet Affärsmöjlighet och ditt anpassade fält är lika med fältet för beräknad intäkt. Arbetsflödet ska vara inställt på att köras i realtid, men kan även köras på begäran för att uppdatera öppna affärsmöjligheter.

Ange [!DNL Marketo Measure] kontaktpunkt med namnet på det anpassade fältet för affärsmöjlighetsbelopp. De uppdaterar [!DNL Marketo Measure] Inställningar för appmöjlighet som ska innehålla namnet på fältet för det anpassade affärsmöjlighetsbeloppet. Detta anger vilket fält som ska användas vid rapportering.

**ARBETSFLÖDE 2**: Möjligheter - uppdatering [!DNL Marketo Measure] Fält för affärsmöjlighetsbelopp och anpassat fält = Faktisk intäkt

Det här arbetsflödet startar när en användare stänger ett säljprojekt och uppdaterar [!DNL Marketo Measure] Fältet Affärsmöjlighet och ditt anpassade fält med den faktiska intäkten tillagd i stängningsformuläret för affärsmöjlighet innan affärsmöjligheten låses som stängd.

## Del 2: Beräknat stängningsdatum kontra faktiskt stängningsdatum {#part-estimated-close-date-vs-actual-close-date}

Inkomstdata för försäljningsförlopp är inte tillgängliga i instrumentpanelen eftersom Dynamics som standard har två fält för stängningsdatum för lagerställe: Beräknat stängningsdatum och Faktiskt stängningsdatum. [!DNL Marketo Measure] Det går bara att peka på ett stängningsdatumfält på kontrollpanelen och peka på Faktiskt stängningsdatum.

Om öppna affärsmöjligheter saknar data i fältet Faktiskt stängningsdatum finns det inga data i instrumentpanelen för öppna affärsmöjligheter. Det behövs dock ett arbetsflöde baserat på affärsmöjlighetens fas för att stödja båda datumfälten.

1. Skapa anpassat stängningsdatumfält för säljprojektsobjektet ([!DNL Marketo Measure] Anpassat stängningsdatum).
1. Skapa ett arbetsflöde för att uppdatera [!DNL Marketo Measure] Anpassat stängningsdatum med datumet från antingen det beräknade stängningsdatumet eller det faktiska stängningsdatumet, beroende på om affärsmöjligheten är öppen eller stängd (arbetsflödet ska sparas för att köras i realtid, men måste köras på begäran minst en gång för att uppdatera alla öppna öppningar).
1. Testa arbetsflödet och bekräfta att det fungerar.
1. Kunden måste ange API-namnet för det anpassade stängningsdatumet för att [!DNL Marketo Measure].
1. [!DNL Marketo Measure] för att uppdatera [!DNL Marketo Measure] appinställningar som pekar på [!DNL Marketo Measure] Anpassat stängningsdatumfält på kontrollpanelen.

   När du är klar med ovanstående steg kör du arbetsflödena för att uppdatera båda anpassade [!DNL Marketo Measure] Opp-belopp och [!DNL Marketo Measure] Anpassat fält för stängningsdatum på dina historiska möjligheter för att spegla rätt data. Detta ändrar troligen de ändrade fälten på/efter så att du bör kontrollera med ditt team om detta ger några problem.

Så här uppdaterar du stängda affärsmöjligheter..

1. Isolera affärsmöjligheter som har stängts sedan [!DNL Marketo Measure] startdatum tills arbetsflödet är aktivt. Detta är gruppen med historiska möjligheter som du måste uppdatera via arbetsflöde.
1. Exportera alla poster till Excel.
1. Öppna Excel-fil, aktivera innehåll.
1. Kopiera faktiska stängningsdatumdata till [!DNL Marketo Measure] Anpassat stängningsdatum.
1. Kopiera faktiska intäktsdata till [!DNL Marketo Measure] Anpassat affärsmöjlighetsbelopp **och** [!DNL Marketo Measure] Affärsmöjlighet (det finns två fält).
1. Spara filen.
1. Importera fil. Dynamics identifierar detta som en fil med befintliga poster att uppdatera.
1. Kontrollera om det inte går att importera filen.

>[!NOTE]
>
>Arbetsflödena i det här dokumentet är bara ett sätt att uppdatera fälten så att [!DNL Marketo Measure] kan visa rätt data i Discover. Om du har ett annat sätt att utföra samma uppgift kan du göra det. Det vi behöver av dem är något slags arbetsflöde som gör följande:
>
> * Om Opp = Open, uppdatera anpassat stängningsdatumfält, anpassat snabbbeloppsfält och [!DNL Marketo Measure] popup-beloppsfält till samma beräknade stängningsdatum respektive uppskattad intäkt.
> * Om Opp = Closed Won, uppdatera anpassat stängningsdatumfält, anpassat snabbbeloppsfält och [!DNL Marketo Measure] Växla beloppsfält till samma faktiska stängningsdatum och faktiska intäkt.
