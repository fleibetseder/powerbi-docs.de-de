---
title: Ringdiagramme in Power BI
description: Ringdiagramme in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d90ef12e1971ddc81928746f338ba927a48d5b23
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195153"
---
# <a name="doughnut-charts-in-power-bi"></a>Ringdiagramme in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Ein Ringdiagramm ähnelt einem Kreisdiagramm insofern, als dass es die Beziehung von Teilen zu einem Ganzen zeigt. Der einzige Unterschied ist, dass die Mitte leer und Platz für eine Beschriftung oder ein Symbol bleibt.

## <a name="prerequisite"></a>Voraussetzung

Dieses Tutorial verwendet die [PBIX-Datei mit einem Analysebeispiel für den Einzelhandel](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Wählen Sie im oberen linken Bereich der Menüleiste die Option **Datei** > **Öffnen** aus.
   
2. Suchen Sie Ihre Kopie der **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel**.

1. Öffnen Sie die **PBIX-Datei mit einem Analysebeispiel für den Einzelhandel** in der Berichtsansicht ![Screenshot des Berichtsansichtssymbols.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Auswählen ![Screenshot der gelben Registerkarte.,](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) um eine neue Seite hinzuzufügen.


## <a name="create-a-doughnut-chart"></a>Erstellen eines Ringdiagramms

1. Beginnen Sie auf einer leeren Berichtsseite, und wählen Sie im Bereich „Felder“ die Option **Sales** \> **Last Year Sales**.  
   
3. Wählen Sie im Bereich „Visualisierungen“ das Symbol für ein Ringdiagramm ![Symbol für Ringdiagramm](media/power-bi-visualization-doughnut-charts/power-bi-icon.png) aus, um das Balkendiagramm in ein Ringdiagramm zu konvertieren. Wenn sich die Kategorie **Verkäufe im letzten Jahr** nicht im Bereich **Werte** befindet, ziehen Sie diese dorthin.
     
   ![Bereich „Visualisierung“ mit ausgewähltem Ringdiagramm](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-chart.png)

4. Wählen Sie **Element** \> **Kategorie** aus, um die Kategorie dem Bereich **Legende** hinzuzufügen. 
     
    ![Ringdiagramm neben Bereich „Felder“](media/power-bi-visualization-doughnut-charts/power-bi-doughnut-done.png)

5. Optional können Sie [die Textgröße und -farbe des Diagramms anpassen](power-bi-visualization-customize-title-background-and-legend.md). 

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
* Die Summe der Ringdiagrammwerte muss insgesamt 100 % betragen.
* Zu viele Kategorien erschweren das Lesen und Interpretieren der Werte.
* Ringdiagramme werden am besten zum Vergleichen eines bestimmten Bereichs gegenüber dem Ganzen verwendet, anstatt einzelne Abschnitte miteinander zu vergleichen. 

## <a name="next-steps"></a>Nächste Schritte
[Trichterdiagramme in Power BI](power-bi-visualization-funnel-charts.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)


