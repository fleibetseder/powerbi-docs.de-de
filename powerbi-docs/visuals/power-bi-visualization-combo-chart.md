---
title: Kombinationsdiagramm in Power BI
description: In diesem Tutorial zu Kombinationsdiagrammen wird erläutert, wann sie verwendet werden sollten und wie sie im Power BI-Dienst und in Power BI Desktop erstellt werden.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/23/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e4b7b4b336b376f6ccec0bc0fe56de107ab8bd09
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67124265"
---
# <a name="combo-chart-in-power-bi"></a>Kombinationsdiagramm in Power BI

Ein Kombinationsdiagramm in Power BI ist eine einzelne Visualisierung, die ein Liniendiagramm und ein Säulendiagramm kombiniert. Die Kombination von zwei Diagrammen in einem ermöglicht einen schnelleren Vergleich von Daten.

Kombinationsdiagramme können ein oder zwei y-Achsen haben.

## <a name="when-to-use-a-combo-chart"></a>Einsatz von Kombinationsdiagrammen

Kombinationsdiagramme sind gut für folgende Zwecke geeignet:

* Bei einem Liniendiagramm und ein Säulendiagramm mit der gleichen X-Achse.

* Zum Vergleichen mehrerer Measures mit verschiedenen Wertebereichen.

* Zum Verdeutlichen der Zusammenhänge zweier Measures in einer Visualisierung.

* Zum Prüfen, ob ein Measure das durch ein anderes Measure vorgegebene Ziel erfüllt.

* Zur Platzersparnis im Zeichenbereich.

## <a name="prerequisites"></a>Voraussetzungen

Kombinationsdiagramme sind im Power BI-Dienst und in Power BI Desktop verfügbar. In diesem Tutorial wird zum Erstellen eines Kombinationsdiagramms der Power BI-Dienst verwendet. Stellen Sie sicher, dass Sie über die Benutzeranmeldeinformationen für die Anmeldung bei Power BI verfügen.

In diesem Video sehen Sie, wie ein Kombinationsdiagramm anhand des Beispiels für Vertrieb und Marketing erstellt wird.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

## <a name="create-a-basic-single-axis-combo-chart"></a>Erstellen eines einfachen Kombinationsdiagramms mit einer Achse

Um die Schritte durchzuführen, öffnen Sie den Power BI-Dienst, und stellen Sie eine Verbindung mit dem **Analysebeispiel für Einzelhandel** her. Melden Sie sich zum Erstellen eines Kombinationsdiagramms beim Power BI-Dienst an, und wählen Sie **Daten abrufen** > **Beispiele** > **Analysebeispiel für Einzelhandel** > **Verbinden** aus. Das Dashboard **Analysebeispiel für Einzelhandel** wird angezeigt.

1. Wählen Sie im Dashboard „Analysebeispiel für Einzelhandel“ die Kachel **Läden gesamt** aus, um den Bericht **Übersicht über Ladenverkäufe** zu öffnen.

1. Wählen Sie **Bericht bearbeiten** , um den Bericht in der Bearbeitungsansicht zu öffnen.

1. Wählen Sie am unteren Rand der Seite **+** aus, um eine neue Berichtsseite hinzuzufügen.

1. Erstellen Sie ein Säulendiagramm, das den Absatz des laufenden Jahres und den Bruttogewinn pro Monat anzeigt.

    1. Wählen Sie im Bereich „Felder“ die Option **Verkäufe** \> **Verkäufe in diesem Jahr**  >  **Wert**.

    1. Ziehen Sie **Vertrieb** \>**Bruttogewinn in diesem Jahr** in den Bereich **Wert**.

    1. Wählen Sie **Zeit** \> **Geschäftsmonat** aus, um den Wert dem Bereich **Achse** hinzuzufügen.

        ![Screenshot des neu erstellten Säulendiagramms.](media/power-bi-visualization-combo-chart/combotutorial1new.png)

1. Wählen Sie die Auslassungspunkte in der rechten oberen Ecke der Visualisierung und dann **Sortieren nach > FiscalMonth** aus. Wenn Sie die Sortierreihenfolge ändern möchten, klicken Sie erst erneut auf die Auslassungspunkte und anschließend auf **Aufsteigend sortieren** oder **Absteigend sortieren**.

1. Konvertieren Sie das Säulendiagramm in ein Kombinationsdiagramm. Es gibt zwei Kombinationsdiagramme: **Linien- und gestapeltes Säulendiagramm** und **Linien- und gruppiertes Säulendiagramm**. Wenn Sie das Säulendiagramm ausgewählt haben, wählen Sie im Bereich **Visualisierungen** die Option **Linien- und gruppiertes Säulendiagramm** aus.

    ![Screenshot des Bereichs „Visualisierungen“ mit hervorgehobener Option „Linien- und gruppiertes Säulendiagramm“.](media/power-bi-visualization-combo-chart/converttocombo_new2.png)

1. Ziehen Sie aus dem Bereich **Felder** die Option **Vertrieb** > **Verkäufe im letzten Jahr** in den Bereich **Zeilenwerte**.

    ![Screenshot des Bereichs „Zeilenwerte“, nachdem „Verkäufe im letzten Jahr“ hineingezogen wurde.](media/power-bi-visualization-combo-chart/linevaluebucket.png)

    Das Kombinationsdiagramm sollten nun ungefähr so aussehen:

    ![Screenshot des Säulendiagramms mit hinzugefügtem Zeilenwert „Verkäufe im letzten Jahr“.](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Erstellen eines Kombinationsdiagramms mit zwei Achsen

In dieser Aufgabe vergleichen wir Bruttogewinn und Umsätze.

1. Erstellen Sie ein neues Liniendiagramm, das den **Bruttogewinn in Prozent im letzten Jahr** nach **Monaten** nachverfolgt. Klicken Sie auf die Auslassungspunkte, um **Aufsteigend** nach **Monat** zu sortieren.

    ![Screenshot des neuen Liniendiagramms.](media/power-bi-visualization-combo-chart/combo1_new.png)

     Im Januar lag der Prozentsatz des Bruttogewinns bei 35 %, der Höchststand im April lag bei 45 %, im Juli fiel der Wert, und im August erreichte er wieder einen Spitzenwert. Sehen wir ein ähnliches Muster bei den Umsätzen im letzten und in diesem Jahr?

1. Fügen Sie dem Liniendiagramm **Verkäufe in diesem Jahr** > **Wert** und **Verkäufe im letzten Jahr** hinzu. Der **Bruttogewinn % Vorjahr** ist wesentlich kleiner als die **Umsätze**. Diese Werte können nur schwer verglichen werden.

    ![Screenshot des Liniendiagramms nach Hinzufügen von „Wert“ und „Verkäufe im letzten Jahr“.](media/power-bi-visualization-combo-chart/flatline_new.png)

1. Konvertieren Sie das Liniendiagramm zu einem Linien- und gestapelten Säulendiagramm, damit die Visualisierung besser gelesen und interpretiert werden kann.

    ![Screenshot des Bereichs „Visualisierungen“ mit hervorgehobener Option „Linien- und gestapeltes Säulendiagramm“.](media/power-bi-visualization-combo-chart/converttocombo_new.png)

1. Ziehen Sie **Bruttogewinn % Vorjahr** aus **Spaltenwerte** in **Zeilenwerte**. 

    ![Screenshot: „Linien- und gestapeltes Säulendiagramm“](media/power-bi-visualization-combo-chart/power-bi-combochart.png)

    Power BI erstellt zwei Achsen und ermöglicht dem Dienst, die Datasets unterschiedlich zu skalieren. Links werden die Umsätze in US-Dollar und rechts die Prozentzahlen gemessen. Und hier sehen wir die Antwort auf unsere Frage: Ja, es wird ein ähnliches Muster angezeigt.

## <a name="add-titles-to-the-axes"></a>Hinzufügen von Titeln zu den Achsen

1. Wählen Sie das Farbrollensymbol ![Screenshot des Farbrollensymbols](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) zum Öffnen des Formatierungsbereichs.

1. Wählen Sie den Pfeil nach unten aus, um die Optionen für die **Y-Achse** zu erweitern.

1. Wählen Sie für **Y-Achse (Spalte)** diese Optionen aus:

    | Einstellung | Wert |
    | ------- | ----- |
    | Position | Wählen Sie **Links** aus. |
    | Anzeigeeinheiten | Wählen Sie **Millionen** aus. |
    | Titel | Setzen Sie den Schieberegler auf **Ein**. |
    | Format | Wählen Sie **Nur Titel anzeigen** aus. |
    | Sekundäre anzeigen | Setzen Sie den Schieberegler auf **Ein**.  Damit werden Optionen zur Formatierung des Liniendiagrammanteils des Kombinationsdiagramms angezeigt. |

1. Wählen Sie für **Y-Achse (Linie)** diese Optionen aus:

    | Einstellung | Wert |
    | ------- | ----- |
    | Position | Wählen Sie **Rechts** aus. |
    | Titel | Setzen Sie den Schieberegler auf **Ein**. |
    | Format | Wählen Sie **Nur Titel anzeigen** aus. |

    Das Kombinationsdiagramm zeigt nun zwei Achsen mit Titeln an.

    ![Screenshot des Linien- und gestapelten Säulendiagramms mit aktivierten Titeln.](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

1. Optional können Sie die Schriftart, den Schriftgrad und die Farbe des Texts ändern und weitere Formatierungsoptionen festlegen, um die Darstellung und Lesbarkeit des Diagramms zu verbessern.

Jetzt haben Sie folgende Möglichkeiten:

* [Fügen Sie das Kombinationsdiagramm als Dashboardkachel hinzu.](../service-dashboard-tiles.md)

* [Speichern Sie den Bericht](../service-report-save.md).

* [Barrierefreiheit in Power BI Desktop-Berichten](../desktop-accessibility.md)

## <a name="cross-highlighting-and-cross-filtering"></a>Kreuzhervorheben und Kreuzfiltern

Das Markieren einer Säule oder Linie in einem Kombinationsdiagramm ermöglicht das Kreuzhervorheben und Kreuzfiltern anderer Visualisierungen auf der Berichtsseite. Verwenden Sie [Visualinteraktionen](../service-reports-visual-interactions.md), um dieses Standardverhalten zu ändern.

## <a name="next-steps"></a>Nächste Schritte

[Ringdiagramme in Power BI](power-bi-visualization-doughnut-charts.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)