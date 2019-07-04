---
title: Punkt-, Blasen- und Punktplotdiagramme in Power BI
description: Punktdiagramme, Punktplotdiagramme und Blasendiagramme in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8222194359077cb0d88286a33d1c9b2a05f6bd80
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390734"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Punktdiagramme, Punktplotdiagramme und Blasendiagramme in Power BI

Ein Punktdiagramm weist immer zwei Wertachsen auf, sodass ein Satz von numerischen Daten entlang einer horizontalen Achse und ein anderer Satz von numerischen Werten entlang einer vertikalen Achse angezeigt wird. Das Diagramm zeigt Schnittpunkte von x- und y-Zahlenwerten an, wobei diese Werte in jeweils einem einzelnen Punkt kombiniert werden. Power BI kann diese Datenpunkte gleichmäßig oder ungleichmäßig auf der horizontalen Achse verteilen. Es hängt von den Daten ab, die das Diagramm darstellt.

In diesem Video sehen Sie, wie Will ein Punktdiagramm erstellt. Mit den unten beschriebenen Schritten können Sie dann selbst ein solches Diagramm erstellen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

Sie können die Anzahl der Datenpunkte auf maximal 10.000 festlegen.  

## <a name="when-to-use-a-scatter-chart-bubble-chart-or-a-dot-plot-chart"></a>Wann sollte ein Punktdiagramm, Blasendiagramm oder Punktplotdiagramm verwendet werden?

### <a name="scatter-and-bubble-charts"></a>Punkt- und Blasendiagramme

Ein Punktdiagramm zeigt die Beziehung zwischen zwei numerischen Werten an. In einem Blasendiagramm werden Datenpunkte durch Blasen ersetzt. Hierbei repräsentiert die *Größe* der Blase eine zusätzliche dritte Datendimension.

![Screenshot eines Beispielblasendiagramms.](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Punktdiagramme sind in folgenden Fällen gut geeignet:

* Zum Anzeigen von Beziehungen zwischen zwei numerischen Werten.

* Zum Darstellen zweier Gruppen von Zahlen als eine Reihe von X- und Y-Koordinaten.

* Zur Verwendung anstelle eines Liniendiagramms, wenn Sie die Skalierung der horizontalen Achse ändern möchten.

* Zum Darstellen der horizontalen Achse in logarithmischer Skalierung.

* Zum Anzeigen von Arbeitsblattdaten, die Paare oder gruppierte Werte enthalten.

    > [!TIP]
    > In einem Punktdiagramm können Sie die unabhängigen Skalierungen der Achsen anpassen, um weitere Informationen zu den gruppierten Werten anzugeben.

* Um Muster in großen Mengen von Daten aufzuzeigen, z.B. lineare oder nicht lineare Trends, Ansammlungen oder Ausreißer.

* Um große Mengen von Datenpunkten ohne Berücksichtigung der Zeit zu vergleichen.  Je mehr Daten Sie in ein Punktdiagramm aufnehmen, desto bessere Vergleiche können Sie vornehmen.

Zusätzlich zu dem, was Punktdiagramme für Sie tun können, sind Blasendiagramme eine gute Wahl:

* Wenn Ihre Daten drei Datenreihen aufweisen, die jeweils einen Satz von Werten enthalten.

* Zum Präsentieren von Finanzdaten.  Unterschiedliche Blasengrößen sind nützlich zum optischen Hervorheben bestimmter Werte.

* Für die Verwendung mit Quadranten.

### <a name="dot-plot-charts"></a>Punktplotdiagramme

Ein Punktplotdiagramm ähnelt einem Blasen- und einem Punktdiagramm, aber Sie können auch numerische oder Kategoriedaten entlang der X-Achse darstellen.

![Screenshot eines Punktplotdiagramms.](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Sie sind eine hervorragende Wahl, wenn Sie Kategoriedaten entlang der X-Achse einschließen möchten.

## <a name="prerequisites"></a>Voraussetzungen

* Der Power BI-Dienst

* Bericht zum Analysebeispiel für den Einzelhandel

## <a name="create-a-scatter-chart"></a>Erstellen eines Punktdiagramms

Melden Sie sich beim [Power BI-Dienst](https://app.powerbi.com) an, und öffnen Sie den Bericht zum [Analysebeispiel für den Einzelhandel](../sample-datasets.md) in der [Bearbeitungsansicht](../service-interact-with-a-report-in-editing-view.md).

1. Wählen Sie ![Screenshot des gelben Pluszeichens.](media/power-bi-visualization-scatter/power-bi-yellow-plus-icon.png) aus, um eine leere Berichtsseite zu erstellen.

1. Wählen Sie im Bereich **Felder** diese Felder aus:

    * **Umsätze** > **Umsätze pro Quadratmeter**

    * **Umsätze** > **Abweichungen der Gesamtumsätze in Prozent**

    * **Region** > **Region**

    ![Screenshot des gruppierten Säulendiagramms, des Bereichs „Visualisierungen“ und des Bereichs „Felder“, wobei die von Ihnen ausgewählten Felder hervorgehoben sind.](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

1. Wählen Sie im Bereich **Visualisierungen** ![Symbol für das Punktdiagramm.](media/power-bi-visualization-scatter/power-bi-scatter-chart-icon.png) aus, um das gruppierte Säulendiagramm in ein Punktdiagramm zu konvertieren.

   ![Screenshot des gruppierten Säulendiagramms, das zu einem Punktdiagramm wird.](media/power-bi-visualization-scatter/power-bi-scatter-new.png)

1. Ziehen Sie **Region** von **Details** auf **Legende**.

    Power BI zeigt ein Punktdiagramm an, in dem die **Abweichungen des Gesamtumsatzes in Prozent** auf der Y-Achse und der **Umsatz pro Quadratmeter** auf der X-Achse dargestellt werden. Die Farben der Datenpunkte stellen die Regionen dar:

    ![Screenshot des Punktdiagramms.](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Nun fügen wir eine dritte Dimension hinzu.

## <a name="create-a-bubble-chart"></a>Erstellen eines Blasendiagramms

1. Ziehen Sie aus dem Bereich **Felder** die Option **Umsätze** > **Umsätze dieses Jahr** > **Wert** in den Bereich **Größe**. Die Datenpunkte werden zu Werten erweitert, die proportional zu den Umsatzwerten sind.

   ![Screenshot des Punktdiagramms, das durch Hinzufügen von „Umsatzwert“ zum Bereich „Größe“ zu einem Blasendiagramm wird.](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

1. Zeigen Sie auf eine Blase. Die Größe der Blase gibt den Wert von **Umsätze dieses Jahr**an.

    ![Anzeige von QuickInfos](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

1. Wenn Sie die Anzahl der im Blasendiagramm anzuzeigenden Datenpunkte festlegen möchten, erweitern Sie im Abschnitt **Format** des Bereichs **Visualisierungen** **Allgemein**, und passen Sie die **Datenmenge** an.

    ![Screenshot des Bereichs „Visualisierungen“ mit Formatsymbol, Dropdownliste „Allgemein“ und Option „Datenmenge“.](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png)

    Sie können die maximale Datenmenge auf eine beliebige Zahl bis 10.000 festlegen. Sobald Sie höhere Zahlen erreichen, wird empfohlen, zuerst einen Test durchzuführen, um gute Leistung sicherzustellen.

    > [!NOTE]
    > Mehr Datenpunkte können längere Ladezeit bedeuten. Wenn Sie sich dafür entscheiden, Berichte mit Einschränkungen am oberen Ende der Skala zu veröffentlichen, sollten Sie Ihre Berichte im Web und ebenfalls auf Mobilgeräten testen. Sie möchten bestätigen, dass die Leistung des Diagramms den Erwartungen Ihrer Benutzer entspricht.

1. Sie können [u.a. Visualisierungsfarben, Bezeichnungen, Titel, Hintergrund formatieren](service-getting-started-with-color-formatting-and-axis-properties.md).

    Zum [Verbessern der Barrierefreiheit](../desktop-accessibility.md) sollten Sie das Hinzufügen von Markierungsformen zu jeder Linie in Betracht ziehen. Sie können zum Auswählen der Markierungsform **Formen** erweitern und dann **Markierungsform** sowie eine Form auswählen.

    ![Screenshot der Dropdownliste „Formen“, wobei die Optionen für „Markierungsform“ hervorgehoben sind.](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

    Sie können die Markierungsform auch in Raute, Dreieck oder Quadrat ändern. Die Verwendung einer anderen Markierungsform für jede Linie erleichtert den Benutzern des Berichts, die Linien (oder Flächen) voneinander zu unterscheiden.

## <a name="create-a-dot-plot-chart"></a>Erstellen eines Punktplotdiagramms

Um ein Punktplotdiagramm zu erstellen, ersetzen Sie das numerische Feld **X-Achse** durch ein Kategoriefeld.

Entfernen Sie im Bereich **X-Achse** das Feld **Verkäufe pro qm**, und ersetzen Sie es durch **Distrikt** > **Regionalmanager**.

![Screenshot eines neuen Punktplotdiagramms.](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung

### <a name="your-scatter-chart-has-only-one-data-point"></a>Das Punktdiagramm weist nur einen Datenpunkt auf

Weist Ihr Punktdiagramm nur einen Datenpunkt auf, in dem alle Werte auf der X- und der Y-Achse zusammengefasst sind?  Oder werden alle Werte auf einer einzelnen horizontalen oder vertikalen Linie zusammengefasst?

![Screenshot eines Punktdiagramms mit einem Datenpunkt.](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Fügen Sie im Bereich **Details** ein Feld hinzu, sodass Power BI erkennt, wie die Werte gruppiert werden sollen. Das Feld muss für jeden Punkt, der dargestellt werden soll, eindeutig sein. Ein einfaches Zeilennummern- oder ID-Feld reicht.

![Screenshot eines Punktdiagramms, wobei RowNum dem Bereich „Details“ hinzugefügt ist.](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Wenn dies mit Ihren Daten nicht möglich ist, erstellen Sie ein Feld, in dem die X- und Y-Werte für jeden Punkt auf individuelle Weise dargestellt werden:

![Screenshot eines Punktdiagramms, wobei TempTime dem Bereich „Details“ hinzugefügt ist.](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Um ein neues Feld zu erstellen, [fügen Sie mit dem Abfrage-Editor von Power BI Desktop dem Dataset eine Indexspalte hinzu](../desktop-add-custom-column.md). Fügen Sie diese Spalte dann dem Bereich **Details** Ihrer Visualisierung hinzu.

## <a name="next-steps"></a>Nächste Schritte

* [Stichprobenentnahme mit hoher Dichte in Power BI-Punktdiagrammen](desktop-high-density-scatter-charts.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
