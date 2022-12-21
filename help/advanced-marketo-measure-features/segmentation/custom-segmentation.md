---
unique-page-id: 18874604
description: Anpassad segmentering - [!DNL Marketo Measure] - Produktdokumentation
title: Anpassad segmentering
exl-id: c20a2add-250e-45ff-97a6-1b1c03351b6a
source-git-commit: b59c79236d3e324e8c8b07c5a6d68bd8176fc8a9
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Anpassad segmentering {#custom-segmentation}

Segment ger möjlighet att filtrera data i [!DNL Marketo Measure] Instrumentpanel för avkastning på investering för att ytterligare detaljgranska en specifik datauppsättning. Ett segment kan till exempel definieras efter geografiskt område eller ett klassificeringssystem.

**Varför anpassad segmentering?**

Med funktionen för anpassad segmentering kan du filtrera Touchpoints efter en kategori och upp till fem segment. Beroende på vilket objekt ditt ROI-tankstreck pekar på (Lead eller Kontakt) kan du skapa segment baserat på fälten som finns i lead-/kontaktobjektet. Du kan också skapa segment baserat på de fält som finns i objektet säljprojekt.

**När är funktionen för anpassad segmentering användbar?**

Anpassad segmentering kan användas för att visa data för en viss posttyp. När du har mappat filterlogiken ska du kunna se i [!DNL Marketo Measure] Instrumentpanelens vy för efterfrågevattenfall - samma data som du skulle se i din CRM.

**Hur konfigurerar jag det?**

Steg 1 - Bestäm vilken information du vill se.

Innan du använder den här funktionen bör du ta reda på vilken kontaktpunktsinformation du vill filtrera efter. Kom ihåg att använda de exakta värdena i CRM för dina posttyper. Konfigurationen filtrerar kontaktytorna uppifrån och ned i marknadsföringstratten.

Steg 2 - Logga in och hitta segmentfunktionen.

* Gå till [experience.adobe.com/marketo-measure](https://experience.adobe.com/marketo-measure){target=&quot;_blank&quot;} och logga in
* Under [!UICONTROL My Account] flik, välja [!UICONTROL Settings]
* Välj [!UICONTROL Segments] från alternativen på sidlisten till vänster, under [!UICONTROL Reporting] section

Steg 3 - Förstå komponenterna.

* Använd den här teckenförklaringen för att förstå de olika ikoner som finns på den här sidan

![](assets/1.png)

Steg 4 - Lägg till filterregler.

* Ange först kategorinamnet. Affärstyp är ett exempel. Klicka på bockmarkeringen när du är klar. Du måste ange ett kategorinamn innan du kan lägga till segment
* Klicka på plustecknet för att lägga till ett segment
* Ange ett segmentnamn. Du kan till exempel ha ett segment för Nytt företag, Partners, Förnyelse eller Merförsäljning

![](assets/2.png)

* Klicka på plusikonen för att visa regelinmatningsfälten. Alternativen i listrutan Fält hämtar fält direkt från CRM

![](assets/3.png)

>[!NOTE]
>
>Formelfält kan inte användas i reglerna och visas inte i plocklistan. Eftersom formler beräknas i bakgrunden och inte ändrar en post, [!DNL Marketo Measure] kan inte identifiera om en post passar en regel eller inte.

* Alternativet Värde är inte en listruta och värdet måste anges manuellt. Kontrollera värdena i Salesforce-organisationen
* Upprepa den här processen för segmentreglerna för affärsmöjligheter
* Kategorin Annan är ett standardsegment som fångar alla odefinierade kontaktpunkter. Du kan ändra standardsegmentets namn
* Klicka på papperskorgsikonen om du vill ta bort en hel kategori eller en enskild regel i en kategori. Du kan också klicka på pennikonen för att redigera kategorin eller regeln
* Du kommer att märka att du har en Spara-knapp och en Spara och bearbetningsknapp. Använd knappen Spara för att spara ditt arbete och dina ändringar över tid. Använd BARA knappen Spara och bearbeta när du har kontrollerat att:

   * Mappningen är korrekt
   * Du har lagt till alla segment som du vill spåra inom en kategori
   * Knappen Spara och bearbeta utlöses [!DNL Marketo Measure] för att synkronisera alla dina kontaktytor och använda den nya information du har lagt till. Den här processen tar 7 dagar och reglerna kan inte ändras under den här perioden

**_Ytterligare information:_**

Om inga regler har ställts in för både Leads/Kontakter och Affärsmöjligheter visas bara en del av dina data. Om du inte konfigurerar säljprojektsreglerna kan du bara se lead-/kontaktdata utan tillhörande säljprojekt. Detsamma gäller om du inte ställer in regler för Leads/Kontakter. Du kan bara se Möjligheter utan associerade Leads/Kontakter.

När du är klar klickar du på [!UICONTROL Save] dubbelkontrollera först allt och klicka sedan på [!UICONTROL Save and Process]. Kom ihåg att du inte kan redigera inställningarna på sju dagar när du sparar och bearbetar som [!DNL Marketo Measure] formaterar om data under tiden.

**Hur sparar jag de genererade rapporterna?**

Du kan inte spara de genererade rapporterna direkt i användargränssnittet. Men [!DNL Marketo Measure] sparar segmentnamnen i URL-adressen så att du kan spara en post med varje rapport genom att bokmärka sidan.
