---
title: Trichterdiagramme
description: Trichterdiagramme in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b12b2035d7686667535dfdddba42b4b8ca014d96
ms.sourcegitcommit: 4ae1257c5d7b33aa2fafd91caf8b353a985c6771
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2019
ms.locfileid: "67161123"
---
# <a name="funnel-charts"></a>Trichterdiagramme
Mit einem Trichterdiagramm kann ein linearer Prozess mit aufeinanderfolgenden und miteinander verbundenen Phasen visuell dargestellt werden. Ein Beispiel ist etwa ein Trichterdiagramm für den Verkauf, das die von den Kunden durchlaufenen Phasen nachverfolgt: Lead \> Qualifizierter Lead \> Potenzieller Kunde \> Vertrag \> Abschluss.  Die Form des Trichterdiagramms zeigt auf einen Blick den Zustand des nachverfolgten Prozesses an.

Jede Phase des Diagramms stellt einen prozentualen Anteil am Gesamtwert dar. Daher hat ein Trichterdiagramm in den meisten Fällen die Form eines Trichters, wobei die erste Phase am größten und jede nachfolgende Phase etwas kleiner ist.  Ein birnenförmiges Diagramm ist hilfreich, um ein Problem im Prozess zu identifizieren.  In der Regel ist jedoch die erste Phase (die „Trichteröffnung“) am größten.

![Blauer Beispieltrichter](media/power-bi-visualization-funnel-charts/funnelplain.png)

## <a name="when-to-use-a-funnel-chart"></a>Einsatz von Trichterdiagrammen
Trichterdiagramme sind gut für folgende Zwecke geeignet:

* Bei fortlaufenden Daten über mindestens vier Phasen hinweg
* Bei einer voraussichtlich größeren Anzahl an „Elementen“ in der ersten Phase im Vergleich zur letzten Phase
* Zum Berechnen potenzieller Werte (Umsatz/Verkäufe/Aufträge usw.) nach Phasen
* Zum Berechnen und Nachverfolgen der Konvertierungs- und Kundenbindungsrate
* Zum Erkennen von Engpässen in einem linearen Prozess
* Zum Nachverfolgen des Workflows in Bezug auf den Warenkorb
* Zum Nachverfolgen des Fortschritts und Erfolgs von Click-Through-Werbe-/Marketingkampagnen

## <a name="working-with-funnel-charts"></a>Arbeiten mit Trichterdiagrammen
Trichterdiagramme:

* Können von Berichten und von Q&A angeheftet werden
* Sortierbar
* Vielfachunterstützung
* Hervorheben und Kreuzfiltern durch andere Visualisierungen auf der gleichen Berichtseite möglich
* Verwendung zum Hervorheben und Kreuzfiltern anderer Visualisierungen auf der gleichen Berichtseite möglich

## <a name="create-a-basic-funnel-chart"></a>Erstellen eines einfachen Trichterdiagramms
In diesem Video sehen Sie, wie ein Trichterdiagramm anhand des Beispiels für Vertrieb und Marketing erstellt wird.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Erstellen Sie jetzt ein eigenes Trichterdiagramm, das die Anzahl der Verkaufschancen in jeder der Verkaufsphasen anzeigt.

In dieser Anleitung wird das Beispiel zur Opportunityanalyse verwendet. Wenn Sie diese Schritte selbst ausführen möchten, [laden Sie das Beispiel](../sample-datasets.md) für den Power BI-Dienst („app.powerbi.com“) oder Power BI Desktop herunter.   

1. Beginnen Sie auf einer leeren Berichtsseite, und wählen Sie **SalesStage** \> **Vertriebsphase** aus. Wenn Sie den Power BI-Dienst verwenden, achten Sie darauf, den Bericht in der [Bearbeitungsansicht](../service-interact-with-a-report-in-editing-view.md) zu öffnen.
   
    ![nach Vertriebsphase](media/power-bi-visualization-funnel-charts/funnelselectfield_new.png)
2. [Wandeln Sie das Diagramm](power-bi-report-change-visualization-type.md) in ein Trichterdiagramm um. Beachten Sie, dass sich **Vertriebsphase** im Bereich der **Gruppe** befindet. 
3. Wählen Sie im Bereich **Felder** die Option **Fakt** \> **Anzahl an Verkaufschancen** aus.
   
    ![Erstellen des Trichterdiagramms](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Wenn Sie mit dem Mauszeiger auf einen Balken zeigen, werden zahlreiche Informationen angezeigt.
   
   * Name der Phase
   * Anzahl aktueller Verkaufschancen in dieser Phase
   * Gesamte Konversionsrate (% der Leads) 
   * Änderungen zwischen den einzelnen Phasen in Prozent (in diesem Fall zwischen Angebots- und Lösungsphase)
     
     ![Details für die Angebotsleiste](media/power-bi-visualization-funnel-charts/funnelhover_new.png)
5. [Fügen Sie den Trichter als Dashboardkachel hinzu](../service-dashboard-tiles.md). 
6. [Speichern Sie den Bericht](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern
Informationen zur Verwendung des Filterbereichs finden Sie unter [Hinzufügen eines Filters zu einem Bericht in Power BI](../power-bi-report-add-filter.md).

Durch Markieren eines Balkens in einem Trichterdiagramm werden Kreuzfilter zu anderen Visualisierungen auf der Berichtsseite aktiviert und umgekehrt. Fügen Sie hierfür der Berichtsseite, die das Trichterdiagramm enthält, einige weitere visuelle Elemente hinzu.

1. Wählen Sie im Trichterdiagramm den Balken **Angebot** aus. Dadurch erfolgt eine Kreuzhervorhebung der anderen Visualisierungen auf der Seite. Mit STRG können Sie mehrere Elemente auswählen.
   
   ![Kurzes Video, das visuelle Interaktionen zeigt](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Informationen zum Festlegen der Einstellungen für die Kreuzhervorhebung und Kreuzfilterung von visuellen Elementen finden Sie unter [Interaktionen mit Visualisierungen in einem Power BI-Bericht](../service-reports-visual-interactions.md).

## <a name="create-a-funnel-chart-using-qa"></a>Erstellen eines Trichterdiagramms mithilfe von Q&A
Öffnen Sie das Dashboard für das Beispiel einer Opportunityanalyse oder ein anderes Dashboard, an das eine Visualisierung aus dem Dataset des Beispiels einer Opportunityanalyse angeheftet wurde.  Wenn Sie in Q&A eine Frage eingeben, sucht Power BI in allen dem ausgewählten Dashboard zugeordneten Datasets (d. h. mit Kacheln, die dem Dashboard angeheftet sind) nach Antworten. Weitere Informationen finden Sie unter [Power BI – Grundkonzepte](../service-basic-concepts.md).

1. Geben Sie im Dashboard des Beispiels einer Opportunityanalyse Ihre Frage im Q&A-Fragefeld ein.
   
   ![Fragefeld und Trichter](media/power-bi-visualization-funnel-charts/power-bi-qna.png)
   
2. Fügen Sie „als Trichter“ hinzu, um den bevorzugten Visualisierungstyp anzugeben.

## <a name="next-steps"></a>Nächste Schritte

[Messanzeigen in Power BI](power-bi-visualization-radial-gauge-charts.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
