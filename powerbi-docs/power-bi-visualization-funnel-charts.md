---
title: Trichterdiagramme (Tutorial)
description: 'Tutorial: Trichterdiagramme in Power BI'
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: maTzOJSRB3g
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/27/2017
ms.author: mihart
ms.openlocfilehash: 231bf7febb19583414d976cc612d06c2caa1e246
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2017
---
# <a name="funnel-charts-tutorial"></a>Trichterdiagramme (Tutorial)
Mit einem Trichterdiagramm kann ein linearer Prozess mit aufeinanderfolgenden und miteinander verbundenen Phasen visuell dargestellt werden. Ein Beispiel ist etwa ein Trichterdiagramm für den Verkauf, das die von den Kunden durchlaufenen Phasen nachverfolgt: Lead \> Qualifizierter Lead \> Potenzieller Kunde \> Vertrag \> Abschluss.  Die Form des Trichterdiagramms zeigt auf einen Blick den Zustand des nachverfolgten Prozesses an.

Jede Phase des Diagramms stellt einen prozentualen Anteil am Gesamtwert dar. Daher hat ein Trichterdiagramm in den meisten Fällen die Form eines Trichters, wobei die erste Phase am größten und jede nachfolgende Phase etwas kleiner ist.  Ein birnenförmiges Diagramm ist hilfreich, um ein Problem im Prozess zu identifizieren.  In der Regel ist jedoch die erste Phase (die „Trichteröffnung“) am größten.

![](media/power-bi-visualization-funnel-charts/funnelplain.png)

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

<iframe width="560" height="315" src="https://www.youtube.com/embed/maTzOJSRB3g" frameborder="0" allowfullscreen></iframe>


Erstellen Sie jetzt ein eigenes Trichterdiagramm, das die Anzahl der Verkaufschancen in jeder der Verkaufsphasen anzeigt.

In dieser Anleitung wird das Beispiel zur Opportunityanalyse verwendet. Gehen Sie wie folgt vor: [Laden Sie das Beispiel herunter](sample-datasets.md), melden Sie sich bei Power BI an, und wählen Sie **Daten abrufen \> Beispiele \> Beispiel zur Nachverfolgung von Verkaufschancen \> Verbinden**.

1. Beginnen Sie auf einer [leeren Berichtsseite](power-bi-report-add-page.md) in der [Bearbeitungsansicht](service-interact-with-a-report-in-editing-view.md), und wählen Sie **SalesStage** \> **Vertriebsphase** aus.  
   
    ![](media/power-bi-visualization-funnel-charts/funnelselectfield_new.png)
2. [Wandeln Sie das Diagramm](power-bi-report-change-visualization-type.md) in ein Trichterdiagramm um. Beachten Sie, dass sich **Vertriebsphase** im Bereich der **Gruppe** befindet. 
3. Wählen Sie im Bereich **Felder** die Option **Fakt** \> **Anzahl an Verkaufschancen** aus.
   
    ![](media/power-bi-visualization-funnel-charts/funnelfinal_new.png)
4. Wenn Sie mit dem Mauszeiger auf einen Balken zeigen, werden zahlreiche Informationen angezeigt.
   
   * Name der Phase
   * Anzahl aktueller Verkaufschancen in dieser Phase
   * Gesamte Konversionsrate (% der Leads) 
   * Änderungen zwischen den einzelnen Phasen in Prozent (in diesem Fall zwischen Angebots- und Lösungsphase)
     
     ![](media/power-bi-visualization-funnel-charts/funnelhover_new.png)
5. [Fügen Sie den Trichter als Dashboardkachel hinzu](service-dashboard-tiles.md). 
6. [Speichern Sie den Bericht](service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern
Informationen zur Verwendung des Filterbereichs finden Sie unter [Hinzufügen eines Filters zu einem Bericht in Power BI](power-bi-report-add-filter.md).

Durch Markieren eines Balkens in einem Trichterdiagramm werden Kreuzfilter zu anderen Visualisierungen auf der Berichtsseite aktiviert und umgekehrt. Fügen Sie hierfür der Berichtsseite, die das Trichterdiagramm enthält, einige weitere visuelle Elemente hinzu.

1. Wählen Sie im Trichterdiagramm den Balken **Angebot** aus. Dadurch erfolgt eine Kreuzhervorhebung der anderen Visualisierungen auf der Seite. Mit STRG können Sie mehrere Elemente auswählen.
   
   ![](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Informationen zum Festlegen der Einstellungen für die Kreuzhervorhebung und Kreuzfilterung von visuellen Elementen finden Sie unter [Interaktionen mit Visualisierungen in einem Power BI-Bericht](service-reports-visual-interactions.md).

## <a name="create-a-funnel-chart-in-qa"></a>Erstellen eines Trichterdiagramms in Q&A
Markieren Sie das Dashboard mit mindestens einer Visualisierung, die vom Dataset „Nachverfolgung von Verkaufschancen“ angeheftet wurde.  Wenn Sie in Q&A eine Frage eingeben, sucht Power BI in allen dem ausgewählten Dashboard zugeordneten Datasets (d. h. mit Kacheln, die dem Dashboard angeheftet sind) nach Antworten. Weitere Informationen finden Sie unter [Power BI – Grundkonzepte](service-basic-concepts.md).

1. Markieren Sie das Dashboard mit mindestens einer Kachel, die vom Dataset „Nachverfolgung von Verkaufschancen“ angeheftet wurde.
2. Geben Sie Ihre Frage in das Fragenfeld von Q&A ein.
   
   ![](media/power-bi-visualization-funnel-charts/funnelfromqna_new.png)
   
   Fügen Sie „als Trichter“ hinzu, um den bevorzugten Visualisierungstyp anzugeben.

## <a name="next-steps"></a>Nächste Schritte
[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

[Anheften einer Visualisierung an ein Dashboard](service-dashboard-pin-tile-from-report.md)

[Power BI – Grundkonzepte](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
