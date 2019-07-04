---
title: Radialmessgerät-Diagramme in Power BI
description: Radialmessgerät-Diagramme in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390545"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Radialmessgerät-Diagramme in Power BI

Ein Diagramm für ein radiales Messgerät verfügt über einen Kreisbogen und zeigt einen einzelnen Wert an, mit dem der Fortschritt bei Erreichen eines Ziels oder ein Key Performance Indicator (KPI) gemessen wird. Die Linie (oder *Nadel*) stellt das Ziel oder den Wert dar. Der Fortschritt beim Erreichen des Ziels wird durch die Schattierung dargestellt. Der Wert innerhalb des Bogens stellt den Fortschrittswert dar. Power BI verteilt alle möglichen Werte gleichmäßig auf dem Bogen, vom kleinsten Wert (ganz links) bis zum höchsten Wert (ganz rechts).

![Screenshot des radialen Messgeräts.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

In diesem Beispiel sind Sie ein Autohändler, der die durchschnittlichen Verkäufe seines Vertriebsteams pro Monat verfolgt. Die Nadel stellt ein Verkaufsziel von 140 Autos dar. Der kleinste Wert für die durchschnittlichen Verkäufe ist 0, und der höchste Wert ist auf 200 festgelegt.  Die blaue Schattierung zeigt, dass das Team im aktuellen Monat einen Durchschnitt von ca. 120 Verkäufen erzielt hat. Glücklicherweise ist noch eine Woche Zeit, um das Ziel zu erreichen.

Schauen Sie Will beim Erstellen von Einzelmetrikvisualisierungen wie Messgeräten, Karten und KPIs zu.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Einsatzmöglichkeiten für ein radiales Messgerät

Radiale Messgeräte sind gut für folgende Zwecke geeignet:

* Anzeigen des Fortschritts beim Erreichen eines Ziels.

* Darstellen eines Quantilmeasures, z.B. eines KPI.

* Anzeigen der Integrität eines Measures.

* Anzeigen von Informationen, die Sie schnell überprüfen und verstehen können.

## <a name="prerequisites"></a>Voraussetzungen

* Der Power BI-Dienst oder Power BI Desktop

* Excel-Arbeitsmappe mit Finanzbeispiel: [Laden Sie das Beispiel direkt herunter](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Erstellen eines einfachen radialen Messgeräts

In dieser Anleitung wird der Power BI-Dienst verwendet. Um die Schritte durchzuführen, melden Sie sich bei Power BI an, und öffnen Sie die Excel-Datei mit dem Finanzbeispiel.

### <a name="step-1-open-the-financial-sample-excel-file"></a>Schritt 1: Öffnen der Excel-Datei mit dem Finanzbeispiel

1. Laden Sie die [Excel-Finanzbeispieldatei](../sample-financial-download.md) herunter, falls Sie dies noch nicht getan haben. Merken Sie sich, wo Sie sie gespeichert haben.

1. Wählen Sie innerhalb des Power BI-Diensts die Option **Daten abrufen** > **Dateien** aus.

1. Wählen Sie **Lokale Datei** aus, und navigieren Sie zum Speicherort der Beispieldatei.

1. Wählen Sie **Importieren** aus. Power BI fügt das Finanzbeispiel Ihrem Arbeitsbereich als Dataset hinzu.

1. Wählen Sie in der Inhaltsliste **Datasets** das Symbol **Bericht erstellen** für das **Finanzbeispiel** aus.

    ![Screenshot der Liste „Datasets“ mit einem Pfeil, der auf das Symbol „Bericht erstellen“ für das Finanzbeispiel zeigt.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Schritt 2: Erstellen eines Messgeräts zum Nachverfolgen des Bruttoumsatzes

Als Sie im letzten Abschnitt das Symbol **Bericht erstellen** ausgewählt haben, hat Power BI einen leeren Bericht in der Bearbeitungsansicht erstellt.

1. Wählen Sie im Bereich **Felder** die Option **Bruttoumsatz** aus.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Ändern Sie die Aggregation in **Mittelwert**.

   ![Screenshot des Bereichs „Felder“, wobei „Bruttoumsatz“ und das Aggregat „Durchschnitt“ hervorgehoben sind.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Wählen Sie das Messgerätsymbol aus ![Screenshot des Messgerätsymbols,](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) um das Säulendiagramm in ein Messgerätdiagramm zu konvertieren.

    ![Screenshot des Messgerätdiagramms.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    Je nachdem, wann Sie die **Finanzbeispiel**-Datei herunterladen, werden möglicherweise Zahlen angezeigt, die mit diesen Zahlen nicht übereinstimmen.

    > [!TIP]
    > Power BI erstellt standardmäßig ein Messgerätdiagramm, in dem der aktuelle Wert (hier: **Mittelwert des Bruttoumsatzes**) in der Mitte der Messgerätskala angeordnet ist. Da der **Mittelwert des Bruttoumsatzes** 182.760 US-Dollar beträgt, ist der Startwert (Minimum) auf 0 und der Endwert (Maximum) auf das Doppelte des aktuellen Werts festgelegt.

### <a name="step-3-set-a-target-value"></a>Schritt 3: Festlegen eines Zielwerts

1. Ziehen Sie **COGS** aus dem Bereich **Felder** auf den Bereich **Zielwert**.

1. Ändern Sie die Aggregation in **Mittelwert**.

   Power BI fügt eine Nadel hinzu, um den Zielwert von **145.480 US-Dollar**anzugeben.

   ![Screenshot des Messgerätdiagramms mit hinzugefügtem „Durchschnitt von COGS“.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Sie sehen also, dass wir unser Ziel übererfüllt haben.

   > [!NOTE]
   > Sie können auch manuell einen Zielwert eingeben. Siehe Abschnitt [Verwenden manueller Formatierungsoptionen zum Festlegen der Werte für Minimum, Maximum und Ziel](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Schritt 4: Festlegen eines Maximalwerts

In Schritt 2 verwendete Power BI das Feld **Wert**, um den kleinsten und den höchsten Wert automatisch festzulegen. Was geschieht, wenn Sie einen eigenen Maximalwert festlegen möchten? Angenommen, Sie möchten nicht die Verdopplung des aktuellen Werts als möglichen Maximalwert verwenden, sondern Sie möchten ihn auf den höchsten Bruttoumsatzwert in Ihrem Dataset festlegen.

1. Ziehen Sie **Bruttoumsatz** aus dem Bereich **Felder** in den Bereich **Maximalwert**.

1. Ändern Sie die Aggregation in **Maximum**.

   ![Screenshot des Bereichs „Felder“, wobei „Bruttoumsatz“ und das Aggregat „Maximum“ hervorgehoben sind.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   Das Messgerät wird mit dem neuen Endwert – Bruttoumsatz von 1,21 Millionen – neu gezeichnet.

   ![Screenshot des fertiggestellten Messgerätdiagramms.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Schritt 5: Bericht speichern

1. [Speichern Sie den Bericht](../service-report-save.md).

1. [Fügen Sie das Messgerätdiagramm als Dashboardkachel hinzu](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Verwenden manueller Formatierungsoptionen zum Festlegen der Werte für Minimum, Maximum und Ziel

1. Entfernen Sie **Maximaler Bruttoumsatz** aus dem Bereich **Maximalwert** .

1. Wählen Sie das Farbrollensymbol aus, um den Bereich **Format** zu öffnen.

   ![Screenshot des Messgerätdiagramms und des Bereichs „Format" mit hervorgehobenem Farbrollensymbol.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Erweitern Sie **Messachse**, und geben Sie Werte für **Min** und **Max** ein.

    ![Screenshot der Messgerätachsen-Optionen.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Deaktivieren Sie die Option **COGS** im Bereich **Felder**, um den Zielwert zu entfernen.

    ![Screenshot der deaktivierten COGS-Option.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. Wenn das Feld **Ziel** unter **Messachse**angezeigt wird, geben Sie einen Wert ein.

     ![Screenshot der Messgerätachsen-Optionen mit hervorgehobenem „Ziel“.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Optional können Sie mit der Formatierung des Tachometerdiagramms fortfahren.

Nachdem Sie diese Schritte abgeschlossen haben, haben Sie ein Messgerätdiagramm, das etwa wie folgt aussieht:

![Screenshot des endgültigen Messgerätdiagramms.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Nächster Schritt

* [KPI-Visualisierung](power-bi-visualization-kpi.md)

* [Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)