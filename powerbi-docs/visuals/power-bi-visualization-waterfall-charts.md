---
title: Wasserfalldiagramme in Power BI
description: Wasserfalldiagramme in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409000"
---
# <a name="waterfall-charts-in-power-bi"></a>Wasserfalldiagramme in Power BI

Wasserfalldiagramme zeigen eine laufende Summe an, während Power BI Werte hinzugefügt oder entfernt. Sie sind nützlich, um zu verdeutlichen, wie ein anfänglicher Wert (z.B. das Nettoeinkommen) durch eine Reihe von positiven und negativen Änderungen beeinflusst wird.

Die Säulen sind farbkodiert, damit Sie Zu- und Abnahmen der Werte schnell erkennen können. Die Säulen für den Anfangs- und den Endwert [gehen häufig von der horizontalen Achse aus](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "gehen häufig von der horizontalen Achse aus"), während die Zwischenwerte unverankerte Säulen sind. Aufgrund dieses Aussehens werden Wasserfalldiagramme auch als „Brückendiagramme“ bezeichnet.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Einsatz von Wasserfalldiagrammen

Wasserfalldiagramme sind gut für folgende Zwecke geeignet:

* Bei Änderungen der Zahlen im Laufe der Zeit, für eine Serie oder über verschiedene Kategorien hinweg.

* Zum Überwachen der wichtigsten Änderungen am Gesamtwert.

* Zum Anzeigen des jährlichen Gewinns Ihres Unternehmens mithilfe einer Darstellung verschiedener Umsatzquellen und letztendlich des Gesamtgewinns (oder -verlusts).

* Zum Illustrieren der Mitarbeiterzahl Ihres Unternehmens zu Jahresbeginn und -ende.

* Zum Visualisieren Ihrer Einnahmen und Ausgaben pro Monat und des laufenden Kontostands für Ihr Konto.

## <a name="prerequisites"></a>Voraussetzungen

* Der Power BI-Dienst oder Power BI Desktop

* Bericht zum Analysebeispiel für den Einzelhandel

## <a name="get-the-retail-analysis-sample-report"></a>Abrufen des Berichts zum Analysebeispiel für den Einzelhandel

In dieser Anleitung wird das Analysebeispiel für den Einzelhandel verwendet. Zum Erstellen einer Visualisierung benötigen Sie Bearbeitungsberechtigungen für das Dataset und den Bericht. Erfreulicherweise können die Power BI-Beispiele alle bearbeitet werden. Wenn jemand einen Bericht für Sie freigegeben hat, können Sie keine Visualisierungen in Berichten erstellen. Öffnen Sie zum besseren Verständnis den [Bericht zum Analysebeispiel für den Einzelhandel](../sample-datasets.md).

Nach dem Abrufen des Datasets für das **Analysebeispiel für den Einzelhandel** können Sie beginnen.

## <a name="create-a-waterfall-chart"></a>Erstellen eines Wasserfalldiagramms

Sie erstellen ein Wasserfalldiagramm, mit dem Abweichungen beim Umsatz (geschätzter Umsatz im Vergleich zu tatsächlichen Verkaufszahlen) nach Monat dargestellt werden.

1. Wählen Sie in **Mein Arbeitsbereich** die Option **Datasets** > **Bericht erstellen** aus.

    ![Screenshot von „Datasets > Bericht erstellen“.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. Wählen Sie im Bereich **Felder** die Option **Verkäufe** > **Gesamtabweichung Verkäufe** aus.

   ![Screenshot der Auswahl von „Verkäufe > Gesamtabweichung Verkäufe“ und des resultierenden visuellen Elements.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Wählen Sie das Wasserfallsymbol ![Screenshot des Wasserfallsymbols](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) aus, um das Diagramm in ein Treemap-Diagramm umzuwandeln.

    Wenn sich **Gesamtabweichung Verkäufe** nicht im Bereich der **Y-Achse** befindet, ziehen Sie es dorthin.

    ![Visualisierungsvorlagen](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Wählen Sie **Zeit** > **FiscalMonth** aus, um den Wert dem Bereich **Kategorie** hinzuzufügen.

    ![Wasserfalldiagramm](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Stellen Sie sicher, dass Power BI das Wasserfalldiagramm chronologisch sortiert hat. Wählen Sie in der rechten oberen Ecke des Diagramms die Auslassungspunkte (...) aus.

    Überprüfen Sie, ob sich links von den Optionen **Aufsteigend sortieren** und **FiscalMonth** ein gelber Indikator befindet.

    ![Auswählen von „Sortieren nach > FiscalMonth“](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    Sie können auch die Werte auf der X-Achse betrachten und sehen dann, dass sie in der Reihenfolge von **Jan** bis **Aug** sortiert sind.

    Analysieren Sie die Informationen genauer, um zu ermitteln, was von Monat zu Monat am stärksten zu den Änderungen beiträgt.

1. Ziehen Sie **Store** > **Gebiet** in den Bucket **Aufschlüsselung**.

    ![Zeigt Store im Bucket „Aufschlüsselung“ an](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Standardmäßig fügt Power BI die wichtigsten fünf Faktoren für die Steigerungen oder Verringerungen pro Monat hinzu.

    ![Zeigt Store im Bucket „Aufschlüsselung“ an](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Sie interessieren sich aber nur für die ersten beiden Faktoren.

1. Wählen Sie im Bereich **Format** **Aufschlüsselung** aus, und legen Sie für **Max. Aufschlüsselungen** **2** fest.

    ![„Format > Aufschlüsselung“](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    Ein kurzer Blick zeigt, dass die Gebiete „Ohio“ und „Pennsylvania“ im Wasserfalldiagramm den größten Anteil an positiven wie negativen Änderungen haben.

    ![Wasserfalldiagramm](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    Dies ist ein bemerkenswertes Ergebnis. Haben Ohio und Pennsylvania so starken Einfluss, weil der Umsatz in diesen beiden Gebieten sehr viel höher als in den anderen Gebieten ist? Das können Sie nachprüfen.

1. Erstellen Sie eine Karte, mit der der Umsatz dieses Jahres nach Umsatzwert und der des letzten Jahres nach Gebiet analysiert wird.

    ![Kartenausschnitt für Pennsylvania und Ohio](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    Die Karte unterstützt unsere Theorie. Sie zeigt, dass diese beiden Gebiete im letzten Jahr (Blasengröße) und in diesem Jahr (Blasenschattierung) die höchsten Umsätze erzielt haben.

## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern

Informationen zur Verwendung des Bereichs **Filter** finden Sie unter [Hinzufügen eines Filters zu einem Bericht in der Bearbeitungsansicht](../power-bi-report-add-filter.md).

Das Markieren einer Säule in einem Wasserfalldiagramm ermöglicht ein Kreuzfiltern anderer Visualisierungen auf der Berichtsseite und umgekehrt. Die Säule mit dem **Gesamtwert** löst jedoch keine Markierung aus und reagiert nicht auf Kreuzfiltern.

## <a name="next-steps"></a>Nächste Schritte

* [Ändern der Interaktion von Visualisierungen in einem Power BI-Bericht](../service-reports-visual-interactions.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
