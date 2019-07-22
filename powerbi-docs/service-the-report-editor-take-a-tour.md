---
title: Einführung in den Berichts-Editor
description: Der Berichts-Editor im Power BI-Dienst und der Berichts-Editor in Power BI Desktop sind sich sehr ähnlich.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/07/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 37337d7b544bcad5c1f357b00eb73d7af6c6da7d
ms.sourcegitcommit: dc0258bb4f647ff646c6fff2aaffa29b413aa2df
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342223"
---
# <a name="tour-the-report-editor-in-power-bi"></a>Einführung in den Berichts-Editor in Power BI

Der *Berichts-Editor* im Power BI-Dienst und der Berichts-Editor in Power BI Desktop sind sich sehr ähnlich. Normalerweise beginnen Sie mit dem Erstellen von Berichten in Power BI Desktop. Anschließend veröffentlichen Sie sie im Power BI-Dienst, wo Sie sie weiter bearbeiten können. Der Power BI-Dienst ist auch der Ort, wo Sie die Dashboards auf der Grundlage Ihrer Berichte bearbeiten.

Nach dem Erstellen verteilen Sie Ihre Dashboards und Berichte an die Endbenutzer Ihrer Berichte. Abhängig von der Art der Freigabe sind Ihre Endbenutzer möglicherweise imstande, mit den Berichten in der Leseansicht im Power BI-Dienst zu interagieren, können sie allerdings nicht bearbeiten. Erfahren Sie mehr darüber, [welche Möglichkeiten Endbenutzer von Berichten im Power BI-Dienst haben](consumer/end-user-reading-view.md). 

Im folgenden Video wird der Berichts-Editor in Power BI Desktop gezeigt. Dieser Artikel zeigt den Berichts-Editor in Power BI-Dienst. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Im Power BI-Dienst ist der Berichts-Editor nur in der Bearbeitungsansicht verfügbar. Wenn Sie einen Bericht in der Bearbeitungsansicht öffnen möchten, müssen Sie Besitzer oder Ersteller des Berichts oder Mitwirkender im App-Arbeitsbereich sein, in dem der Bericht enthalten ist.

Der Berichts-Editor von Power BI besteht aus drei Abschnitten:  

1. den Bereichen **Felder**, **Visualisierungen** und **Filter**
2. den oberen Navigationsleisten    
3. dem Zeichenbereich für den Bericht     

![Die Abschnitte des Berichts-Editors](media/service-the-report-editor-take-a-tour/power-bi-report-canvas.png)

## <a name="1-the-report-editor-panes"></a>1. Die Bereiche des Berichts-Editors
![Power BI-Berichts-Editor](media/service-the-report-editor-take-a-tour/power-bi-report-panes.png)

Wenn Sie erstmalig einen Bericht öffnen, sind drei Bereiche sichtbar: Visualisierungen, Filter und Felder. Die Bereiche auf der linken Seite (Visualisierungen und Filter) steuern das Aussehen Ihrer Visualisierungen: Typ, Farben, Filter, Format.  Im Bereich auf der rechten Seite (Felder) werden die zugrunde liegenden Daten verwaltet, die in den Visualisierungen verwendet werden. 

Der im Berichts-Editor angezeigte Inhalt variiert je nach ausgewählten Optionen, die Sie im Berichtszeichenbereich vornehmen.  Wenn Sie z. B. ein einzelnes Visual auswählen:

|  |  |
| --- | --- |
| ![Bereiche des Berichts-Editors](media/service-the-report-editor-take-a-tour/power-bi-panes.png) |<ul><li>wird am Anfang des Bereichs „Visualisierung“ der Typ des verwendeten visuellen Elements angegeben; in diesem Beispiel ein gruppiertes Säulendiagramm.<br><br></li> <li>werden am Ende des Bereichs „Visualisierung“ (möglicherweise müssen Sie nach unten scrollen) die vom visuellen Element verwendeten Felder angezeigt. In diesem Diagramm werden „FiscalMonth“, „DistrictManager“ und „Total Sales Variance“ verwendet. <br><br></li><li>werden im Bereich „Filter“ (möglicherweise müssen Sie nach unten scrollen) alle Filter angezeigt, die angewendet wurden. <br><br></li><li>werden im Bereich „Felder“ die verfügbaren Tabellen und, wenn Sie den Namen einer Tabelle erweitern, die Felder aufgelistet, die diese Tabelle bilden. An gelber Schrift können Sie erkennen, dass mindestens ein Feld aus dieser Tabelle in der Visualisierung verwendet wird.<br><br></li><li>![Farbrollensymbol](media/service-the-report-editor-take-a-tour/power-bi-paint-roller-icon.png) Klicken Sie auf das Farbrollensymbol, um den Formatierungsbereich der ausgewählten Visualisierung anzuzeigen.<br><br></li><li>![Lupensymbol](media/service-the-report-editor-take-a-tour/power-bi-magnifying-icon.png) Wählen Sie das Lupensymbol aus, um den Analysebereich anzuzeigen.</ul> |

## <a name="the-visualizations-pane"></a>Der Bereich „Visualisierungen“
![Oben im Bereich „Visualisierungen“](media/service-the-report-editor-take-a-tour/selectviz.png)

Hier wählen Sie den Typ der Visualisierung aus. Die kleinen Bilder werden als *Vorlagen* bezeichnet. In der Abbildung oben wurde ein gestapeltes Balkendiagramm ausgewählt. Wenn Sie am Anfang keinen Visualisierungstyp auswählen, sondern eine Visualisierung durch Auswählen von Feldern erstellen, wählt Power BI den Visualisierungstyp aus. Sie können die Auswahl von Power BI übernehmen oder den Typ ändern, indem Sie eine andere Vorlage auswählen. Wechseln Sie den Visualisierungstyp beliebig oft, bis Sie den Typ gefunden haben, mit dem Ihre Daten am besten dargestellt werden.

### <a name="manage-the-fields-in-your-visual"></a>Steuern der Felder in Ihrem Visual
![Mitte des Bereichs „Visualisierungen“](media/service-the-report-editor-take-a-tour/power-bi-field-list.png)

Die in diesem Bereich angezeigten Buckets (auch als *Bereiche* bezeichnet) variieren je nach Typ der ausgewählten Visualisierung.  Wenn Sie z. B. ein Balkendiagramm ausgewählt haben, werden Buckets für Folgendes angezeigt: Werte, Achse und Legende. Wenn Sie ein Feld auswählen oder in den Zeichenbereich ziehen, fügt Power BI dieses Feld zu einem der Buckets hinzu.  Sie können die Felder aus der Liste „Felder“ auch direkt in die Buckets ziehen.  Einige Buckets sind auf bestimmte Datentypen beschränkt.  **Werte** akzeptiert beispielsweise keine nicht numerischen Felder. Wenn Sie also das Feld **Mitarbeitername** in das Bucket **Werte** ziehen, ändert sich das Feld für Power BI in **Anzahl von Mitarbeitername**.

### <a name="remove-a-field"></a>Entfernen von Feldern
Um ein Feld aus der Visualisierung zu entfernen, klicken Sie auf das **X** rechts neben dem Feldnamen.

![„StoreType“ aus der Legende entfernen](media/service-the-report-editor-take-a-tour/deletefield.png)

Weitere Informationen finden Sie unter [Hinzufügen von Visualisierungen zu einem Power BI-Bericht](visuals/power-bi-report-add-visualizations-i.md).

### <a name="format-your-visuals"></a>Formatieren von visuellen Elementen
Wählen Sie das Farbrollen-Symbol aus, um den Formatierungsbereich anzuzeigen. Die verfügbaren Optionen hängen vom ausgewählten Visualisierungstyp ab.

![Bereich „Formatierung“ im Berichts-Editor](media/service-the-report-editor-take-a-tour/power-bi-formatting.png)

Ihnen stehen nahezu unbegrenzt viele Formatierungsmöglichkeiten zur Verfügung.  Wenn Sie mehr Informationen benötigen, untersuchen Sie den Bereich selbst weiter oder lesen Sie die folgenden Artikel:

* [Anpassen von Visualisierungstitel, Hintergrund und Legende](visuals/power-bi-visualization-customize-title-background-and-legend.md)
* [Farbformatierung](visuals/service-getting-started-with-color-formatting-and-axis-properties.md)
* [Anpassen der Eigenschaften der X- und Y-Achse](visuals/power-bi-visualization-customize-x-axis-and-y-axis.md)

### <a name="add-analytics-to-your-visualizations"></a>Hinzufügen von Analysen in Visualisierungen
Wählen Sie das Lupensymbol aus, um den Analysebereich anzuzeigen. Die verfügbaren Optionen hängen vom ausgewählten Visualisierungstyp ab.

![Bereich „Analyse“ im Berichts-Editor](media/service-the-report-editor-take-a-tour/power-bi-analytics.png)    
Mit dem Bereich „Analyse“ im Power BI-Dienst können Sie Visualisierungen dynamische Bezugslinien hinzufügen und wichtige Trends und Erkenntnisse identifizieren. Weitere Informationen finden Sie unter [Analysebereich im Power BI-Dienst](service-analytics-pane.md) oder [Analysebereich in Power BI Desktop](desktop-analytics-pane.md).

- - -
## <a name="the-filters-pane"></a>Bereich „Filter“
Über den Bereich „Filter“ können Sie persistente Filter für Ihre Berichte auf Seiten-, Berichts-, Drillthrough- und visueller Ebene anzeigen, setzen und ändern. Ja, Sie können eine Ad-hoc-Filterung auf Berichtsseiten und in visuellen Elementen durchführen. Hierzu wählen Sie visuelle Elemente aus oder verwenden Werkzeuge wie „Datenschnitt“, aber wenn Sie den Filterbereich verwenden, wird der Zustand der Filter mit dem Bericht gespeichert. 

Der Bereich „Filter“ verfügt über ein weiteres leistungsstarkes Feature: das Filtern mithilfe eines Felds, ***das nicht bereits in einem der Visuals in Ihrem Bericht verwendet wird***. Mit anderen Worten: Bei der Erstellung einer Berichtsseite fügt Power BI automatisch alle Felder hinzu, die Sie in Ihren Visualisierungen für den Filterbereich der visuellen Ebene im Bereich „Filter“ verwenden.  Möglicherweise möchten Sie einen Filter für ein visuelles Element, eine Seite, einen Drillthrough oder einen Bericht mithilfe eines Felds festlegen. Wenn der betreffende Inhalt derzeit nicht in einer Visualisierung verwendet wird, ziehen Sie ihn einfach auf einen der Filterbuckets.   

![Bereich „Filter“](media/service-the-report-editor-take-a-tour/power-bi-formatting-pane.png)

Weitere Informationen finden Sie unter [Hinzufügen von Filtern zu Berichten](power-bi-report-add-filter.md).

Eine neue Filteroberfläche befindet sich zurzeit in der Vorschau. Die neuen Filter bieten Formatierungsoptionen zur Anpassung an die Darstellung des Berichts. Ferner können Sie Filter sperren oder sie vor Ihren Endbenutzern verbergen. 

![Neue Filteroberfläche](media/service-the-report-editor-take-a-tour/power-bi-filter-reading.png)

Erfahren Sie mehr über die [neue Filteroberfläche](power-bi-report-filter.md).

- - -
## <a name="the-fields-pane"></a>Bereich „Felder“
Im Bereich „Felder“ werden die Tabellen und Felder angezeigt, die in den Daten vorhanden sind und zum Erstellen von Visualisierungen verwendet werden können.

|  |  |
| --- | --- |
| ![Bereich „Felder“](media/service-the-report-editor-take-a-tour/reportfields.png) |<ul><li>Ziehen Sie ein Feld auf die Seite, um eine neue Visualisierung zu starten.  Sie können auch ein Feld auf eine vorhandene Visualisierung ziehen, um das Feld zu dieser Visualisierung hinzuzufügen.<br><br></li> <li>Wenn Sie das Kontrollkästchen neben einem Feld aktivieren, fügt Power BI dieses Feld zur aktiven (oder neuen) Visualisierung hinzu. Außerdem legt Power BI fest, in welchem Bucket dieses Feld platziert werden soll.  Soll das Feld beispielsweise als Legende, Achse oder Wert verwendet werden? Power BI trifft eine bestmögliche Annahme, und Sie können das Feld ggf. aus diesem Bucket in einen anderen verschieben. <br><br></li><li>In beiden Fällen wird das jeweils ausgewählte Feld im Berichts-Editor zum Bereich „Visualisierungen“ hinzugefügt.</li></ul> |

**HINWEIS**: Wenn Sie Power BI Desktop verwenden, finden Sie auch Optionen zum Ein- und Ausblenden von Feldern, Hinzufügen von Berechnungen usw.

### <a name="what-do-the-field-icons-mean"></a>Bedeutung der Feldsymbole
**∑ Aggregate** Ein Aggregat ist ein numerischer Wert, mit dem z.B. eine Summe oder ein Mittelwert gebildet wird. Aggregate werden mit den Daten importiert (definiert im Datenmodell, auf dem der Bericht basiert).
Weitere Informationen finden Sie unter [Aggregate in Power BI-Berichten](service-aggregates.md).

![Rechnersymbol](media/service-the-report-editor-take-a-tour/pbi_calculated_icon.png) **Berechnete Measures (auch berechnete Felder genannt)**  
Jedes berechnete Feld verfügt über eine eigene hartcodierte Formel. Die Berechnung kann nicht geändert werden, d. h. eine Summe bleibt eine Summe. Weitere Informationen finden Sie unter [Grundlegendes zu Measures](desktop-measures.md).

![Symbol „Eindeutige Felder“](media/service-the-report-editor-take-a-tour/icon.png) **Eindeutige Felder**  
Felder mit diesem Symbol wurden aus Excel importiert und sind so eingestellt, dass sie alle Werte anzeigen, auch wenn sie Duplikate aufweisen. Ihre Daten können z. B. zwei Datensätze für Personen namens „John Smith“ enthalten, die jeweils eindeutig behandelt werden, d. h. sie werden nicht zusammengefasst.  

**![Symbol „Geografie“](media/service-the-report-editor-take-a-tour/pbi_geo_icon.png) Geografische Felder**  
Mithilfe der Felder für Ortsangaben können Kartenvisualisierungen erstellt werden. 

**![Symbol „Hierarchie“](media/service-the-report-editor-take-a-tour/power-bi-hierarchy-icon.png) Hierarchie**  
Wählen Sie den Pfeil aus, um die Felder anzuzeigen, die die Hierarchie bilden. 

## <a name="2-the-top-navigation-bar"></a>2. Die obere Navigationsleiste
Die in der oberen Navigationsleiste verfügbaren Aktionen sind zahlreich, und es werden kontinuierlich neue Aktionen hinzugefügt. Informationen zu einer bestimmten Aktion finden Sie im Inhaltsverzeichnis oder im Suchfeld der Power BI-Dokumentation.

## <a name="3-the-report-canvas"></a>3. Der Zeichenbereich des Berichts
Im Zeichenbereich des Berichts wird Ihre Arbeit angezeigt. Wenn Sie in den Bereichen „Felder“, „Filter“ und „Visualisierungen“ Visuals erstellen, werden diese im Zeichenbereich des Berichts erstellt und angezeigt. Jede Registerkarte am unteren Rand des Zeichenbereichs entspricht einer Seite im Bericht. Wählen Sie eine Registerkarte aus, um die entsprechende Seite zu öffnen. 

## <a name="next-steps"></a>Nächste Schritte
[Erstellen eines Berichts](service-report-create-new.md)

Weitere Informationen zu Berichten finden im [Power BI-Dienst](service-report-create-new.md), in [Power BI Desktop](desktop-report-view.md) und in den [Power BI Mobile-Apps](consumer/mobile/mobile-apps-view-phone-report.md).

[Grundlegende Konzepte für Power BI-Designer](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

