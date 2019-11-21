---
title: 'Tutorial: Facebook-Analysen mit Power BI Desktop'
description: 'Tutorial: Facebook-Analysen mit Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 96811a2cfd7d08a210c4efd177e989abce16d25d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876270"
---
# <a name="tutorial-facebook-analytics-using-power-bi-desktop"></a>Tutorial: Facebook-Analysen mit Power BI Desktop

In diesem Tutorial erfahren Sie, wie Sie Daten aus Facebook importieren und in Power BI Desktop verwenden. Sie verbinden und importieren Daten von der Power BI-Facebook-Seite, wenden Transformationen auf die importierten Daten an und verwenden die Daten in Berichtsvisualisierungen.

> [!WARNING]
> Aufgrund von Berechtigungseinschränkungen der Facebook-App funktionieren die in diesem Artikel beschriebenen Connectorfunktionen zurzeit nicht ordnungsgemäß. Wir arbeiten mit Facebook zusammen, um diese Funktionalität so bald wie möglich wiederherzustellen.


## <a name="connect-to-a-facebook-page"></a>Herstellen der Verbindung mit einer Facebook-Seite

In diesem Tutorial werden Daten von der [Microsoft Power BI-Facebook-Seite](https://www.facebook.com/microsoftbi) ( *https://www.facebook.com/microsoftbi* ) verwendet. Um sich mit dieser Seite zu verbinden und Daten zu importieren, benötigen Sie keine besonderen Anmeldeinformationen, sondern lediglich ein persönliches Facebook-Konto.

1. Öffnen Sie Power BI Desktop, und wählen Sie im Dialogfeld **Erste Schritte** oder auf der Registerkarte des Menübands **Start** die Option **Daten abrufen**. Wählen Sie dann **Daten abrufen** und anschließend **Mehr...** .
   
2. Wählen Sie im Dialogfeld **Daten abrufen** aus der Gruppe **Onlinedienste** die Option **Facebook** aus, und wählen Sie dann **Verbinden**.
   
   ![Daten abrufen](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Ein Dialogfeld wird angezeigt, das Sie vor den Risiken bei Verwendung eines Drittanbieterdiensts warnt.
   
   ![Warnung vor Drittanbieterdienst](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Wählen Sie **Weiter** aus. Das Dialogfeld **Facebook** wird angezeigt.
   
4. Geben Sie im Dialogfeld den Seitennamen **microsoftbi** in das Textfeld **Benutzername** ein, oder kopieren Sie diesen hinein, und wählen Sie dann aus der Dropdownliste **Verbindung** die Option **Beiträge** aus. Klicken Sie dann auf **OK**.
   
   ![Verbinden](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Wenn Sie zur Eingabe von Anmeldeinformationen aufgefordert werden, melden Sie sich mit Ihrem Facebook-Konto an, um Power BI den Zugriff über Ihr Konto zu gewähren.
   
   ![Anmeldeinformationen](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Nach dem Herstellen der Verbindung mit der Power BI-Facebook-Seite sehen Sie eine Vorschau der Daten auf der Seite **Beiträge**. 
   
   ![Datenvorschau](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>Strukturieren und Transformieren der importierten Daten

Sie wollen anzeigen, welche Beiträge im Laufe der Zeit die meisten Kommentare haben. In der Vorschau der **Beiträge** stellen Sie jedoch fest, dass die Daten von **created_time** schwer zu lesen und zu verstehen sind, und es überhaupt keine Kommentare gibt. Sie müssen die Daten zunächst strukturieren und bereinigen, damit Sie diese optimal nutzen können. Mit dem **Power Query-Editor** von Power BI Desktop können Sie die Daten vor oder nach dem Import in Power BI Desktop bearbeiten. 

### <a name="split-the-datetime-column"></a>Unterteilen der Spalte für Datum/Uhrzeit

Unterteilen Sie zunächst die Werte für Datum und Uhrzeit in der Spalte **created_time** für eine bessere Lesbarkeit. 

1. Wählen Sie in der Facebook-Datenvorschau **Bearbeiten** aus. 
   
   ![Datenvorschau – Bearbeiten](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   Der **Power Query-Editor** von Power BI Desktop wird in einem neuen Fenster geöffnet und zeigt die Datenvorschau von der Power BI-Facebook-Seite an. 
   
   ![Power Query-Editor](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Wählen Sie die Spalte **created_time** aus. Beachten Sie, dass es sich aktuell um einen Textdatentyp handelt, der durch ein **ABC**-Symbol in der Spaltenüberschrift gekennzeichnet ist. Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift, und wählen Sie in der Dropdownliste **Spalte teilen > Nach Trennzeichen** aus, oder wählen Sie im Menüband auf der Registerkarte „Start“ unter **Transformieren** die Option **Spalte teilen > Nach Trennzeichen** aus.  
   
   ![Spalte nach Trennzeichen teilen](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Wählen Sie im Dialogfeld **Spalte nach Trennzeichen teilen** im der Dropdownliste die Option **Benutzerdefiniert** aus, geben Sie im Eingabefeld das Zeichen **T** ein (welches den Anfang des Uhrzeitteils in den Werten „created_time“ angibt), und wählen Sie dann **OK**. 
   
   ![Dialogfeld „Spalte nach Trennzeichen teilen“](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   Die Spalte wird in zwei Spalten unterteilt, die die Zeichenfolgen vor und nach dem **T**-Trennzeichen enthalten und **created_time.1** bzw. **created_time.2** benannt sind. Beachten Sie, dass Power BI die Datentypen **Datum** für die erste Spalte und **Uhrzeit** für die zweite Spalte automatisch erkannt und geändert hat. Die Datums- und Zeitwerte wurden so formatiert, dass sie besser lesbar sind.
   
4. Benennen Sie die Spalten um, indem Sie auf jede Spaltenüberschrift doppelklicken oder jede Spalte markieren und dann im Menüband in der Registerkarte **Transformation** in der Gruppe **Jede Spalte** die Option **Umbenennen** auswählen und die neuen Spaltenüberschriften **created_date** bzw. **created_time** eingeben.
   
   ![Neue Datums- und Uhrzeitspalten](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>Erweitern der geschachtelten Spalte

Jetzt, da die Datums- und Zeitdaten so sind, wie Sie sie haben möchten, können Sie die Kommentardaten anzeigen, indem Sie eine geschachtelte Spalte erweitern. 

1. Markieren Sie die Spalte **object_link**, und wählen Sie dann das ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), um das Dialogfeld **Erweitern/Aggregieren** zu öffnen. Wählen Sie **Verbindungen**, und wählen Sie dann **OK**. 
   
   ![Erweitern von „object_link“](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   Die Spaltenüberschriften werden in **object_link.connections** geändert.
2. Wählen Sie erneut oben in der Spalte **object_link.connections** das ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), wählen Sie **Kommentare**, und wählen Sie dann **OK**. Die Spaltenüberschriften werden in **object_link.connections.comments** geändert.
   
3. Wählen Sie oben in der Spalte **object_link.connections.comments** das ![Erweiterungssymbol](media/desktop-tutorial-facebook-analytics/14.png), und wählen Sie diesmal im Dialogfeld **Aggregieren** anstelle von „Erweitern“. Wählen Sie **# Anzahl von ID**, und wählen Sie dann **OK**. 
   
   ![Aggregieren von Kommentaren](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   In der Spalte wird nun die Anzahl von Kommentaren für jede Nachricht angezeigt. 
   
4. Benennen Sie die Spalte **Anzahl von object_link.connections.comments.id** in **Anzahl von Kommentaren** um.
   
5. Wählen Sie den Abwärtspfeil neben der Überschrift **Anzahl von Kommentaren**, und wählen Sie **Absteigend sortieren**, um die Beiträge von den meisten bis zu den wenigsten Kommentaren zu sortieren. 
   
   ![Kommentare pro Nachricht](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Überprüfen der Abfrageschritte

Während Sie Daten im **Power Query-Editor** strukturiert und transformiert haben, wurde jeder Schritt auf der rechten Seite des Power Query-Editor-Fensters im Bereich **Abfrageeinstellungen** im Abschnitt **Angewendete Schritte** aufgezeichnet. Sie können durch die angewandten Schritte zurückgehen, um genau zu sehen, welche Änderungen Sie vorgenommen haben, und sie bei Bedarf bearbeiten, löschen oder neu anordnen (obwohl dies riskant sein kann, da das Ändern vorhergehender Schritte spätere Schritte beeinträchtigen kann). 

Nach dem Anwenden der bisherigen Datentransformationen sollte der Abschnitt „Angewendete Schritte“ wie folgt aussehen:
   
   ![Angewendete Schritte](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >Den angewendeten Schritten liegen Formeln zugrunde, die in der **Power Query-Sprache**, auch bekannt als **M**-Sprache, geschrieben sind. Zum Anzeigen und Bearbeiten der Formeln wählen Sie in der Registerkarte „Start“ des Menübands in die Gruppe **Abfrage** die Option **Erweiterter Editor**. 

### <a name="import-the-transformed-data"></a>Importieren der transformierten Daten

Wenn Sie mit den Daten zufrieden sind, wählen Sie in der Registerkarte „Start“ des Menübands **Schließen und übernehmen** > **Schließen und übernehmen**, um sie in Power BI Desktop zu importieren. 
   
   ![Schließen und übernehmen](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   Es wird ein Dialogfeld angezeigt, in dem Sie den Status des Ladevorgangs der Daten in das Datenmodell von Power BI Desktop verfolgen können. 
   
   ![Die Daten werden geladen.](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   Sobald die Daten geladen sind, erscheinen sie in der Berichtsansicht in der Liste „Felder“ als neue Abfrage.
   
   ![Neue Abfrage](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>Verwenden der Daten in Berichtvisualisierungen 

Nachdem Sie die Daten von der Facebook-Seite importiert haben, können Sie mithilfe von Visualisierungen schnell und einfach Einblicke in Ihre Daten erhalten. Die Erstellung einer Visualisierung ist denkbar einfach: Wählen Sie ein Feld aus, oder ziehen Sie es aus der Liste **Felder** in den Berichtszeichenbereich.

### <a name="create-a-bar-chart"></a>Erstellen eines Balkendiagramms

1. Wählen Sie in der Power BI Desktop-Berichtsansicht in der Liste „Felder“ die Option **Nachricht**, oder ziehen Sie sie in den Zeichenbereich. Eine Tabelle mit allen Beitragsnachrichten wird im Zeichenbereich angezeigt. 
   
   ![Neue Abfrage](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. Wählen Sie bei ausgewählter Tabelle aus der Liste „Felder“ die Option **Anzahl von Kommentaren**, oder ziehen Sie sie in die Tabelle. 
   
3. Wählen Sie im Bereich „Visualisierungen“ das Symbol **Gestapeltes Balkendiagramm** aus. Die Tabelle wird in ein Balkendiagramm geändert, das die Anzahl von Kommentaren pro Beitrag zeigt. 
   
   ![Balkendiagramm](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Wählen Sie die Auslassungspunkte (...) für **Weitere Optionen** in der oberen rechten Ecke der Visualisierung aus, und wählen Sie dann **Nach Anzahl von Kommentaren sortieren**, um die Tabelle nach absteigender Anzahl von Kommentaren zu sortieren. 
   
   ![Nach Anzahl von Kommentaren sortieren](media/desktop-tutorial-facebook-analytics/barchart2.png)
   
5. Beachten Sie, dass die meisten Kommentare mit **leeren** Nachrichten verbunden waren (diese Beiträge können Geschichten, Links, Videos oder andere Inhalte ohne Text gewesen sein). Um die Zeile „Leer“ herauszufiltern, wählen Sie am unteren Rand des Bereichs „Visualisierungen“ unter **Filter**die Option **Nachricht (alle)** , wählen Sie **Alle auswählen**, und wählen Sie dann **Leer**, um die Auswahl aufzuheben. Die Filtereinträge zeigen nun **Nachricht ist nicht (Leer)** an, und die Zeile „Leer“ wird im Diagramm nicht mehr angezeigt. 
   
   ![Leere herausfiltern](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>Formatieren der Tabelle

Die Visualisierung wird interessanter, allerdings können Sie nicht viel vom Beitragstext im Diagramm sehen. So zeigen Sie mehr vom Beitragstext an

1. Vergrößern Sie das Diagramm über die Handles der Diagrammvisualisierung soweit wie möglich. 
   
2. Wählen Sie bei ausgewähltem Diagramm im Bereich „Visualisierung“ das **Formatierungssymbol** (Farbroller).
   
3. Wählen Sie den Abwärtspfeil neben **Y-Achse**, und ziehen Sie den Schieberegler ganz nach rechts neben **Maximalgröße** (50 %). 
4. Verringern Sie zudem die **Textgröße** auf **10**, damit mehr Text hinein passt.
   
   ![Formatierungsänderungen](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   Im Diagramm sind nun die meisten Beitragsinhalte zu sehen. 
   
   ![Anzeigen weiterer Beiträge](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
Die X-Achse (Anzahl von Kommentaren) des Diagramms zeigt keine genauen Werte an und sieht am unteren Ende des Diagramms verloren aus. Verwenden Sie stattdessen Datenbeschriftungen. 

1. Wählen Sie das Formatierungssymbol, und stellen Sie dann den Schieberegler neben **X-Achse** auf **Aus**. 
   
2. Stellen Sie den Schieberegler neben **Datenbeschriftungen** auf **Ein**. Jetzt wird im Diagramm die genaue Anzahl von Kommentaren für jeden Beitrag angezeigt.
   
   ![Anwenden von Datenbeschriftungen](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Bearbeiten des Datentyps

Das Diagramm sieht nun schon viel besser aus, die Datenbeschriftungen haben jedoch noch alle eine Nachkommastelle ( **,0**). Dies ist störend und irreführend, da die **Anzahl von Beiträgen** eine ganze Zahl sein muss. Daher müssen Sie den Datentyp für die Spalte **Anzahl von Beiträgen** in „Ganzzahl“ ändern.

1. Klicken Sie zum Ändern des Datentyps mit der rechten Maustaste in der Liste „Felder“ auf **Abfrage1**, oder zeigen Sie darauf, und wählen Sie die Auslassungszeichen (...) für **Weitere Optionen** und dann **Abfrage bearbeiten** aus. Sie können auch in der Registerkarte „Start“ des Menübands im Bereich **Externe Daten** die Option **Abfragen bearbeiten** wählen und dann in der Dropdownliste erneut **Abfragen bearbeiten** wählen. Der **Power Query-Editor** von Power BI Desktop wird in einem separaten Fenster geöffnet.
   
   ![Bearbeiten einer Abfrage über die Liste „Felder“](media/desktop-tutorial-facebook-analytics/editquery1.png)     ![Bearbeiten von Abfragen über das Menüband](media/desktop-tutorial-facebook-analytics/t_fb_editquery.png)
   
2. Wählen Sie im Power Query-Editor die Spalte **Anzahl von Kommentaren**, und ändern Sie den Datentyp in **Ganze Zahl**, indem Sie eine der folgenden Vorgehensweisen wählen: 
   - Wählen Sie das Symbol **1.2** neben der Spaltenüberschrift **Anzahl von Kommentaren** und anschließend in der Dropdownliste **Ganze Zahl** aus.
   - Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift und wählen **Typ ändern > Ganze Zahl** aus.
   - Wählen Sie die Option **Datentyp: Dezimalzahl** auf der Registerkarte „Start“ in der Gruppe **Transformieren** oder die Option **Ganze Zahl** auf der Registerkarte **Transformieren** in der Gruppe **Beliebige Spalte**.
   
   Das Symbol in der Spaltenüberschrift wird in **123** geändert und weist so auf den Datentyp „Ganze Zahl“ hin.
   
   ![Ändern des Datentyps](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. Wählen Sie **Schließen und übernehmen** oder nur **Übernehmen**, um die Änderungen zu übernehmen, während das Power Query-Editor-Fenster geöffnet bleibt. Sobald die Änderungen geladen sind, werden die Datenbeschriftungen im Diagramm als ganze Zahlen angezeigt. 
   
   ![Diagramm mit ganzen Zahlen](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Erstellen eines Datenschnitts

Sie möchten die Anzahl von Kommentaren zu Beiträgen im Zeitverlauf visualisieren. Sie können eine Datenschnittvisualisierung erstellen, um die Diagrammdaten für verschiedene Zeitabschnitte zu filtern. 

1. Klicken Sie auf eine leere Stelle im Zeichenbereich, und wählen Sie dann im Bereich „Visualisierungen“ das **Datenschnittsymbol**. Es wird eine leere Datenschnittvisualisierung angezeigt. 
   
   ![Auswählen des Datenschnittsymbols](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Wählen Sie aus der Liste „Felder“ das Feld **created_date**, oder ziehen Sie es in den neuen Datenschnitt. Der Datenschnitt wird basierend auf dem Datumsdatentyp des Felds in einen Datumsschieberegler geändert.
   
   ![Datenschnitt mit Datumsschieberegler](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. Verschieben Sie die Schieberegler-Ziehpunkte, um einen anderen Datumsbereich zu wählen, und sehen Sie, wie die Diagrammdaten entsprechend gefiltert werden. Sie können auch die Datumsfelder im Datenschnitt verwenden, um bestimmte Daten einzugeben, oder Sie wählen die Daten im Popupkalender aus.
    
   ![Datenschnitt](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>Formatieren der Visualisierungen

Sie entscheiden sich, dem Diagramm einen aussagekräftigeren und attraktiveren Titel zu geben. 

1. Wählen Sie bei ausgewähltem Diagramm das Symbol **Format**, und wählen Sie den Dropdownpfeil, um **Titel** zu erweitern.
2. Ändern Sie **Titeltext** in **Kommentare pro Beitrag**. 
3. Wählen Sie den Dropdownpfeil neben **Schriftfarbe**, und wählen Sie eine grüne Farbe, passend zu den grünen Balken der Visualisierung.
4. Erhöhen Sie die **Textgröße** auf **10**, und ändern Sie die **Schriftfamilie** in **Segoe (Fett)** .

![Formatieren des Diagrammtitels](media/desktop-tutorial-facebook-analytics/formatting1.png)

Experimentieren Sie mit anderen Formatierungsoptionen und Einstellungen, um das Aussehen Ihrer Visualisierungen zu ändern. 

![Visualisierungen](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>Erstellen weiterer Visualisierungen

Wie Sie sehen können, ist das Anpassen von Visualisierungen in Berichten wirklich einfach, um so Ihre Daten in der gewünschten Weise zu präsentieren. Verwenden Sie zum Beispiel die importierten Facebook-Daten, um dieses Liniendiagramm mit der Anzahl von Kommentaren im Zeitverlauf zu erstellen.

![Liniendiagramm](media/desktop-tutorial-facebook-analytics/moreviz.png)

Power BI Desktop bietet ein nahtloses End-to-End-Erlebnis, das vom Abrufen der Daten aus einer Vielzahl von Datenquellen über die Strukturierung der Daten für Analysezwecke bis zur Visualisierung dieser Daten auf umfassende und interaktive Weise reicht. Nachdem Ihr Bericht fertig ist, können Sie ihn [in Power BI-Dienst hochladen](desktop-upload-desktop-files.md) und auf seiner Grundlage Dashboards erstellen, die Sie für andere Power BI-Benutzer freigeben können.

## <a name="next-steps"></a>Nächste Schritte
* [Weitere Tutorials zu Power BI Desktop lesen](https://go.microsoft.com/fwlink/?LinkID=521937)
* [Videos zu Power BI Desktop ansehen](https://go.microsoft.com/fwlink/?LinkID=519322)
* [Power BI-Forum besuchen](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Power BI-Blog lesen](https://go.microsoft.com/fwlink/?LinkID=519327)

