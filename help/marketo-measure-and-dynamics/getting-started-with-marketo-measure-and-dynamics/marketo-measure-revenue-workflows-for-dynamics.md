---
unique-page-id: 37356132
description: "[!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics - [!DNL Marketo Measure] - Produktdokumentation"
title: "[!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics"
exl-id: 0e64201a-bc65-4a6d-9192-09c14c810c4a
source-git-commit: 54337a0a65b79d80ebeae6531f5e92f4f48721a7
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# [!DNL Marketo Measure] Intäktsarbetsflöden för Dynamics {#marketo-measure-revenue-workflows-for-dynamics}

## Del 1: Uppskattad intäkt kontra faktisk intäkt {#part-estimated-revenue-vs-actual-revenue}

[!DNL Marketo Measure] pekar på ett standardintäktsfält utanför rutan (Faktisk intäkt) men Dynamics har två standardintäktsfält: Faktisk omsättning och beräknad omsättning. Om du vill att pipeline-intäkter ska vara tillgängliga i Discover Dashboard behövs ett anpassat fält och ett arbetsflöde för att hämta korrekt belopp från antingen fältet för beräknad intäkt eller Faktisk intäkt beroende på om affärsmöjligheten är öppen eller stängd (Won).

Steg 1: Skapa fält för anpassat affärsmöjlighetsbelopp i Dynamics

>[!NOTE]
>
>Alla Dynamics-intäktsfält har ett basfält och ett vanligt fält. Ignorera basfältet.

Steg 2: Skapa ett arbetsflöde som uppdaterar både det anpassade fältet för affärsmöjlighetsbelopp som skapats i steg 1 och [!DNL Marketo Measure] Fältet Affärsmöjlighet.

>[!NOTE]
>
>Vi kan inte peka på [!DNL Marketo Measure] Affärsmöjlighetens belopp (bizible2_bizible_Opportunity_amount) i fältet Discover with Dynamics accounts. Dynamics-kunder måste skapa ett anpassat fält för affärsmöjlighetsbelopp för [!DNL Marketo Measure] till Discover. När det är klart måste kunden skapa ett arbetsflöde som uppdaterar **båda** den [!DNL Marketo Measure] Affärsmöjlighet (bizible2_bizible_Opportunity_amount) **och** det anpassade fältet för affärsmöjlighetsbelopp. The [!DNL Marketo Measure] Fältet Affärsmöjlighet levereras med paketet, men ett anpassat fält måste skapas.

Instruktioner för arbetsflöde:

**ARBETSFLÖDE nr 1**: Möjligheter - Uppdatera [!DNL Marketo Measure] Fält för affärsmöjlighet och anpassat fält = Uppskattad intäkt

Det här arbetsflödet körs på öppna affärsmöjligheter varje gång en beräknad intäkt ändras och uppdaterar [!DNL Marketo Measure] Fältet Affärsmöjlighet och ditt anpassade fält är lika med fältet för beräknad intäkt. Arbetsflödet ska vara inställt på att köras i realtid, men kan även köras på begäran för att uppdatera öppna affärsmöjligheter.

Ange [!DNL Marketo Measure] kontaktpunkt med namnet på det anpassade fältet för affärsmöjlighetsbelopp. De kommer att uppdatera [!DNL Marketo Measure] Inställningar för appmöjlighet som ska innehålla namnet på fältet för det anpassade affärsmöjlighetsbeloppet. Detta visar vilket fält som ska användas vid rapportering.

**ARBETSFLÖDE nr 2**: Möjligheter - Uppdatera [!DNL Marketo Measure] Fält för affärsmöjlighetsbelopp och anpassat fält = Faktisk intäkt

Det här arbetsflödet körs i realtid. Det initieras när en användare stänger ett säljprojekt och uppdaterar [!DNL Marketo Measure] Fältet Affärsmöjlighet och ditt anpassade fält med den faktiska intäkten tillagd i stängningsformuläret för affärsmöjlighet innan affärsmöjligheten låses som stängd.

## Del 2: Beräknat stängningsdatum kontra faktiskt stängningsdatum {#part-estimated-close-date-vs-actual-close-date}

Inkomstdata för pipeline kommer inte att vara tillgängliga i kontrollpanelen eftersom Dynamics som standard har två stängningsdatumfält: Beräknat stängningsdatum och faktiskt stängningsdatum. [!DNL Marketo Measure] kan bara peka på ett stängningsdatumfält i kontrollpanelen och vi pekar för närvarande på det faktiska stängningsdatumet.

Om öppna affärsmöjligheter inte har några data i fältet Faktiskt stängningsdatum visas inga data i instrumentpanelen för öppna affärsmöjligheter. Det behövs dock ett arbetsflöde baserat på affärsmöjlighetens fas för att stödja båda datumfälten.

1. Skapa anpassat stängningsdatumfält på säljprojektsobjektet (dvs. [!DNL Marketo Measure] Anpassat stängningsdatum).
1. Skapa ett arbetsflöde för att uppdatera [!DNL Marketo Measure] Anpassat stängningsdatum med datumet från antingen det beräknade stängningsdatumet eller det faktiska stängningsdatumet, beroende på om affärsmöjligheten är öppen eller stängd (arbetsflödet ska sparas för att köras i realtid, men måste köras på begäran minst en gång för att uppdatera alla öppna öppningar).
1. Testa arbetsflödet och bekräfta att det fungerar.
1. Kunden måste ange API-namnet för det anpassade stängningsdatumet för att [!DNL Marketo Measure].
1. [!DNL Marketo Measure] för att uppdatera [!DNL Marketo Measure] appinställningar som pekar på [!DNL Marketo Measure] Anpassat stängningsdatumfält på kontrollpanelen.

   När ovanstående steg är slutförda måste vi köra arbetsflöden för att uppdatera både den anpassade [!DNL Marketo Measure] Opp-belopp och [!DNL Marketo Measure] Anpassat fält för stängningsdatum på dina historiska möjligheter för att spegla rätt data. Detta ändrar troligen de ändrade fälten på/av så att du vill fråga ditt team om det ger några problem.

Uppdatera stängda affärsmöjligheter..

1. Isolera affärsmöjligheter som har stängts sedan [!DNL Marketo Measure] startdatum tills arbetsflödet är aktivt. Det här är en grupp historiska möjligheter som du behöver uppdatera via arbetsflöde.
1. Exportera alla poster till Excel.
1. Öppna Excel-fil, aktivera innehåll.
1. Kopiera faktiska stängningsdatumdata till [!DNL Marketo Measure] Anpassat stängningsdatum.
1. Kopiera faktiska intäktsdata till [!DNL Marketo Measure] Anpassat affärsmöjlighetsbelopp **och** [!DNL Marketo Measure] Affärsmöjlighet (det finns två fält).
1. Spara filen.
1. Importera fil. Dynamics identifierar detta som en fil med befintliga poster att uppdatera.
1. Kontrollera om det inte går att importera filen.

>[!NOTE]
>
>Arbetsflödena som beskrivs i det här dokumentet är bara ett sätt att uppdatera fälten så att [!DNL Marketo Measure] kan visa rätt data i Discover. Om du har ett annat sätt att utföra samma uppgift kan du göra det. Det vi behöver av dem är något slags arbetsflöde som ger följande resultat:
>
> * Om Opp = Open, uppdatera anpassat stängningsdatumfält, anpassat snabbbeloppsfält och [!DNL Marketo Measure] popup-beloppsfält till samma beräknade stängningsdatum respektive uppskattad intäkt.
> * Om Opp = Closed Won, uppdatera anpassat stängningsdatumfält, anpassat snabbbeloppsfält och [!DNL Marketo Measure] Växla beloppsfält till samma faktiska stängningsdatum och faktiska intäkt.

