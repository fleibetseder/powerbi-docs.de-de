---
title: Tabellenvisualisierungen in Power BI-Berichten und -Dashboards
description: Tutorial zum Arbeiten mit Tabellenvisualisierungen in Power BI-Berichten und -Dashboards, einschließlich Erläuterungen zum Ändern der Spaltenbreite.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 65410dc15600307ba11a2c48db1689be5a458383
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193077"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tabellen in Power BI-Berichten und -Dashboards

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Eine Tabelle ist ein Raster, das zusammengehörende Daten in einer logischen Folge von Zeilen und Spalten enthält. Zudem können auch Kopfzeilen und eine Zeile für Summen enthalten sein. Tabellen empfehlen sich insbesondere für quantitative Vergleiche, bei denen Sie viele Werte einer einzigen Kategorie betrachten. In dieser Tabelle werden beispielsweise fünf verschiedene Measures für die **Kategorie** angezeigt.

![Screenshot einer Tabelle, die fünf verschiedene Measures für die Kategorie anzeigt.](media/power-bi-visualization-tables/power-bi-table-grid3.png)

Erstellen Sie Tabellen in Berichten, und heben Sie Elemente in der Tabelle mit anderen Visuals auf der gleichen Berichtsseite übergreifend hervor. Sie können Zeilen, Spalten und sogar einzelne Zellen für die Kreuzhervorhebung auswählen. Sie können auch einzelne und mehrere ausgewählte Zellen kopieren und in andere Anwendungen einfügen.

## <a name="when-to-use-a-table"></a>Verwenden von Tabellen

Tabellen sind für folgende Zwecke gut geeignet:

* Anzeigen und Vergleichen detaillierter Daten und genauer Werte (anstelle von visuellen Darstellungen).

* Auflisten von Daten in einem Tabellenformat.

* Anzeigen numerischer Daten nach Kategorien.

## <a name="prerequisite"></a>Voraussetzung

Dieses Tutorial verwendet die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Wählen Sie im oberen linken Bereich der Menüleiste die Option **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.


## <a name="create-a-table"></a>Erstellen einer Tabelle

Sie erstellen die am Anfang des Artikels abgebildete Tabelle, um Umsatzwerte nach Artikelkategorien anzuzeigen.


1. Wählen Sie im Bereich **Felder** **Element** > **Kategorie** aus.

    Power BI erstellt automatisch eine Tabelle, in der alle Kategorien aufgelistet werden.

    ![Ergebnis: „Kategorie“ hinzugefügt](media/power-bi-visualization-tables/power-bi-table1.png)

1. Wählen Sie **Verkäufe > Durchschnittlicher Einzelpreis** und **Verkäufe > Verkäufe im letzten Jahr** aus.

1. Wählen Sie dann **Verkäufe > Verkäufe in diesem Jahr** aus, und wählen Sie alle drei Optionen aus: **Wert**, **Ziel** und **Status**.

1. Suchen Sie im Bereich **Visualisierung** den Bereich **Werte**, und wählen Sie die Werte aus, bis die Reihenfolge der Diagrammspalten der in der ersten Abbildung auf dieser Seite entspricht. Ziehen Sie bei Bedarf die Werte in den Wertbereich. Ihre **Werte** sehen nun wie folgt aus:

    ![Werte](media/power-bi-visualization-tables/power-bi-table2.png)


## <a name="format-the-table"></a>Formatieren der Tabelle

Es gibt viele Möglichkeiten, eine Tabelle zu formatieren. Nur wenige werden hier behandelt. Eine hervorragende Möglichkeit, die weiteren Formatierungsoptionen kennenzulernen ist, den Bereich **Format** zu öffnen (Farbrollensymbol ![Farbrolle](media/power-bi-visualization-tables/power-bi-format.png)) und ihn genauer zu betrachten.

* Experimentieren Sie mit der Formatierung des Tabellenrasters. Hier fügen Sie ein blaues vertikales Raster hinzu sowie Abstand zwischen den Zeilen und vergrößern Kontur und Text.

    ![Karte „Raster“](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![Tabelle mit Ergebnissen](media/power-bi-visualization-tables/power-bi-table-grid3.png)

* Ändern Sie bei den Spaltenüberschriften die Hintergrundfarbe, fügen Sie eine Kontur hinzu und setzen Sie die Schriftgröße herauf.

    ![Karte „Spaltenüberschriften“](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![Headerformate in Tabelle](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Sie können sogar einzelne Spalten und Spaltenheader formatieren. Erweitern Sie dazu zunächst die **Feldformatierung**, und wählen Sie die zu formatierende Spalte aus der Dropdownliste aus. Je nach Spaltenwerten können Sie über die **Feldformatierung** u.a. Folgendes festlegen: Anzeigeeinheiten, Schriftfarbe, Anzahl der Dezimalstellen, Hintergrund, Ausrichtung und mehr. Wenn Sie die Einstellungen angepasst haben, können Sie diese auch auf die Header und die Ergebniszeile anwenden.

    ![Feldformatierung für „Verkäufe in diesem Jahr“](media/power-bi-visualization-tables/power-bi-field-formatting.png)

    ![Feldformatierung für „Verkäufe in diesem Jahr“ in der Tabelle](media/power-bi-visualization-tables/power-bi-field-formatting-1.png)

* Unten sehen Sie die fertige Tabelle nach einigen weiteren Formatierungen.

    ![Tabelle mit allen bereits vorgenommenen Formatierungen](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Bedingte Formatierung

*Bedingte Formatierung* ist eine Art der Formatierung. Power BI wendet bedingte Formatierung auf Felder im Bereich **Werte** des Bereichs **Visualisierungen** an.

Mit der bedingten Formatierung für Tabellen können Sie benutzerdefinierte Hintergrundfarben für Zellen und Schriftfarben auf Grundlage von Zellwerten angeben, u.a. mit Verlaufsfarben.

1. Wählen Sie im Bereich **Visualisierungen** das Symbol **Felder** ![Feldersymbol](media/power-bi-visualization-tables/power-bi-fields-icon.png) aus.

1. Wählen Sie im Bereich **Werte** neben dem Wert, den Sie formatieren möchten, den nach unten gerichteten Pfeil aus (oder klicken Sie mit der rechten Maustaste in das Feld).

    > [!NOTE]
    > Sie können die bedingte Formatierung nur für Felder im Bereich **Werte** des Bereichs **Felder** verwalten.

    ![Pfad zu Skalen für die Hintergrundfarbe](media/power-bi-visualization-tables/power-bi-conditional-formatting-background.png)

1. Wählen Sie **Hintergrundfarbe** aus.

1. Im angezeigten Dialogfeld können Sie die Farbe sowie die Werte für **Minimum** und **Maximum** konfigurieren. Wenn Sie die Option **Abweichend** aktivieren, können Sie auch einen optionalen Wert für **Zentriert** konfigurieren.

    ![Anzeige „Skalen für die Hintergrundfarbe“](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Lassen Sie uns jetzt einige benutzerdefinierte Formatierungen auf die Werte für den durchschnittlichen Einzelpreis anwenden. Wählen Sie **Abweichend** aus, fügen Sie Farben hinzu, und wählen Sie **OK** aus.

    ![Tabelle mit abweichenden Farbskalen](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
1. Fügen Sie der Tabelle ein neues Feld mit positiven und negativen Werten hinzu. Wählen Sie **Verkäufe > Gesamtabweichung Verkäufe** aus.

    ![Neues Feld auf der rechten Seite](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)

1. Fügen Sie eine bedingte Formatierung für Datenbalken hinzu, indem Sie den Dropdownpfeil neben **Gesamtabweichung Verkäufe** und dann **Bedingte Formatierung > Datenbalken** auswählen.

    ![Pfad zum Auswählen von Datenbalken](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars.png)

1. Legen Sie im daraufhin angezeigten Dialogfeld Farben für **Positiver Balken** und **Negativer Balken** fest, aktivieren Sie die Option **Nur Balken anzeigen**, und nehmen Sie ggf. weitere Änderungen vor.

    ![Kontrollkästchen „Show bar only“ (Nur Balken anzeigen)](media/power-bi-visualization-tables/power-bi-data-bars.png)

1. Wählen Sie **OK**aus.

    Datenbalken ersetzen die numerischen Werte in der Tabelle und sind so leichter zu erkennen.

    ![Dieselbe Tabelle, aber mit Balken in der letzten Spalte](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)

Wenn Sie eine bedingte Formatierung aus einer Visualisierung entfernen möchten, klicken Sie einfach mit der rechten Maustaste erneut auf das Feld, und wählen Sie **Bedingte Formatierung entfernen** aus.

> [!TIP]
> Die bedingte Formatierung ist auch über den Bereich **Format** verfügbar. Wählen Sie den zu formatierenden Wert aus, und legen Sie dann **Farbskalen** oder **Datenbalken** auf **Ein** fest, um die Standardeinstellungen zu übernehmen. Wenn Sie die Einstellungen anpassen möchten, wählen Sie **Erweiterte Steuerelemente** aus.

## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Kopieren von Werten aus Power BI-Tabellen zum Verwenden in anderen Anwendungen

Womöglich enthält Ihre Matrix oder Tabelle Inhalte, die Sie in anderen Anwendungen wie Dynamics CRM oder Excel oder sogar in anderen Power BI-Berichten verwenden möchten. Wenn Sie in Power BI mit der rechten Maustaste in eine Zelle klicken, können sie in die Daten in einer einzelnen Zelle oder einer Zellenauswahl in Ihre Zwischenablage kopieren und in die andere Anwendung einfügen.

So kopieren Sie den Wert einer einzelnen Zelle:

1. Wählen Sie die Zelle aus, die Sie kopieren möchten.

1. Klicken Sie mit der rechten Maustaste in die Zelle.

1. Wählen Sie **Kopieren** > **Wert kopieren** aus.

    ![Kopieroptionen](media/power-bi-visualization-tables/power-bi-copy-value.png)

    Der unformatierte Zellenwert befindet sich in der Zwischenablage und lässt sich in eine andere Anwendung einfügen.

So kopieren Sie mehrere Zellen:

1. Markieren Sie einen Zellbereich, oder verwenden Sie die **STRG-TASTE**, um eine oder mehrere Zellen auszuwählen.

1. Klicken Sie mit der rechten Maustaste in eine der Zellen, die Sie ausgewählt haben.

1. Wählen Sie **Kopieren** > **Auswahl kopieren** aus.

    ![Kopieroptionen](media/power-bi-visualization-tables/power-bi-copy-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Anpassen der Spaltenbreite in einer Tabelle

Gelegentlich wird in Power BI eine Spaltenüberschrift in einem Bericht oder in einem Dashboard abgeschnitten. Zeigen Sie zum Anzeigen des gesamten Spaltennamens mit dem Mauszeiger auf den Bereich rechts neben der Überschrift, um die Doppelpfeile einzublenden, wählen Sie sie aus, und ziehen Sie sie.

![Video: Nahaufnahme zum Ändern der Größe von Spalten](media/power-bi-visualization-tables/resizetable.gif)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

Wenn Sie die Spaltenformatierung anwenden, können Sie nur eine Ausrichtungsoption pro Spalte auswählen: **Auto**, **Links**, **Zentriert**, **Rechts**. Normalerweise enthält eine Spalte den gesamten Text oder alle Zahlen und keine Mischung daraus. In Fällen, in denen eine Spalte jeweils Zahlen und Text enthält, wird durch die Auswahl von **Auto** der Text links ausgerichtet, und die Zahlen werden rechts ausgerichtet. Dieses Verhalten unterstützt Sprachen, bei denen von links nach rechts gelesen wird.

## <a name="next-steps"></a>Nächste Schritte

* [Treemaps in Power BI](power-bi-visualization-treemaps.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
