---
title: Dashboardkacheln im Power BI-Dienst
description: "Alle wichtigen Informationen über Dashboardkacheln in Power BI. Dies schließt Kacheln ein, die über SQL Server Reporting Services (SSRS) erstellt wurden."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 03/15/2016
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/28/2017
ms.author: mihart
ms.openlocfilehash: d1960ea42bee8b00cc6dd095e94ebf6f6303bce8
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2017
---
# <a name="dashboard-tiles-in-power-bi"></a>Dashboardkacheln in Power BI
Dashboards und Dashboardkacheln sind ein Feature des Power BI-Diensts und nicht von Power BI Desktop. Obwohl Dashboardkacheln nicht in Power BI Mobile erstellt oder angeheftet werden können, lassen sie sich dort [anzeigen und freigeben](mobile-tiles-in-the-mobile-apps.md). Außerdem können Sie in Power BI Mobile [mit der iPhone-App Grafiken zu Ihrem Dashboard hinzufügen](mobile-iphone-app-get-started.md).

## <a name="dashboard-tiles"></a>Dashboardkacheln
![](media/service-dashboard-tiles/power-bi-dashboard.png)

Eine Kachel ist eine Momentaufnahme Ihrer Daten, die an das Dashboard geheftet ist. Eine Kachel kann aus einem Bericht, einem Dataset, einem Dashboard, aus dem Q&A-Feld, aus Excel, aus SSRS (SQL Server Reporting Services) und noch mehr erstellt werden.  Der Screenshot zeigt viele verschiedene Kacheln, die an ein Dashboard angeheftet sind.

Über das Anheften hinaus können mithilfe der Option [Kachel hinzufügen](service-dashboard-add-widget.md) eigenständige Kacheln direkt auf dem Dashboard erstellt werden. Eigenständige Kacheln können Textfelder, Bilder, Videos, Streamingdaten und Webinhalte enthalten.

Benötigen Sie Hilfe, um die Grundkomponenten zu verstehen, aus denen Power BI besteht?  Weitere Informationen finden Sie unter [Power BI – Grundkonzepte](service-basic-concepts.md).

> [!NOTE]
> Wenn sich die ursprüngliche Visualisierung ändert, die zum Erstellen der Kachel verwendet wurde, ändert sich die Kachel nicht.  Wenn Sie beispielsweise ein Liniendiagramm aus einem Bericht angeheftet haben und dann das Liniendiagramm in ein Balkendiagramm ändern, wird auf der Dashboardkachel weiterhin ein Liniendiagramm angezeigt. Die Daten werden aktualisiert, der Visualisierungstyp hingegen nicht.
> 
> 

## <a name="pin-a-tile-from"></a>Anheften einer Kachel aus...
Es gibt viele verschiedene Möglichkeiten, eine Kachel zu Ihrem Dashboard hinzuzufügen (anzuheften). Kacheln können angeheftet werden aus:

* [Power BI Q&A](service-dashboard-pin-tile-from-q-and-a.md)
* [einem Bericht](service-dashboard-pin-tile-from-report.md)
* [einem anderen Dashboard](service-pin-tile-to-another-dashboard.md)
* [einer Excel-Arbeitsmappe auf OneDrive for Business](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher für Excel](publisher-for-excel.md)
* [Schnelle Einblicke](service-insights.md)
* [SSRS](https://msdn.microsoft.com/library/mt604784.aspx)

Eigenständige Kacheln für Bilder, Textfelder, Videos, Streamingdaten und Webinhalte können mit [Kachel hinzufügen](service-dashboard-add-widget.md) direkt auf dem Dashboard erstellt werden.

  ![](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Interagieren mit Kacheln in einem Dashboard
### <a name="move-and-resize-a-tile"></a>Verschieben und Ändern der Größe einer Kachel
Wählen Sie eine Kachel aus, und [verschieben Sie sie auf dem Dashboard](service-dashboard-edit-tile.md). Zeigen Sie auf eine Kachel, und wählen Sie den Ziehpunkt ![](media/service-dashboard-tiles/resize-handle.jpg) aus, um ihre Größe zu ändern.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Zeigen Sie auf eine Kachel, um Aussehen und Verhalten zu ändern.
1. Zeigen Sie auf die Kachel, um die Auslassungspunkte anzuzeigen.
   
    ![](media/service-dashboard-tiles/ellipses_new.png)
2. Wählen Sie die Auslassungspunkte (...) aus, um das Aktionsmenü zu öffnen.
   
    ![](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    Hier können Sie Folgendes tun:
   
   * [Den Bericht öffnen, mit dem diese Kachel erstellt wurde ](service-reports.md) ![](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Das Arbeitsblatt öffnen, mit dem diese Kachel erstellt wurde ](service-reports.md) ![](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
     * [Im Fokusmodus anzeigen ](service-focus-mode.md) ![](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Die auf der Kachel verwendeten Daten exportieren](power-bi-visualization-export-data.md) ![](media/service-dashboard-tiles/export-icon.png)
     * [Titel und Untertitel bearbeiten, Links hinzufügen und den Zeitpunkt der letzten Aktualisierung anzeigen](service-dashboard-edit-tile.md) ![](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Einblicke ausführen ](service-insights.md) ![](media/service-dashboard-tiles/power-bi-insights.png)
     * [Anheften der Kachel an ein anderes Dashboard](service-pin-tile-to-another-dashboard.md)
       ![](media/service-dashboard-tiles/pin-icon.jpg)
   * [Entfernen der Kachel](service-dashboard-edit-tile.md)
     ![](media/service-dashboard-tiles/trash-icon.png)
3. Wählen Sie zum Schließen des Aktionsmenüs eine leere Fläche im Zeichenbereich aus.

### <a name="select-click-a-tile"></a>Auswählen einer Kachel
Wenn Sie eine Kachel auswählen, hängt das anschließenden Vorgehen davon ab, wie die Kachel erstellt wurde und ob sie über einen [benutzerdefinierten Link](service-dashboard-edit-tile.md) verfügt. Wenn sie einen benutzerdefinierten Link aufweist, bringt Sie das Auswählen der Kachel zum Ziel dieses Links. Andernfalls gelangen Sie nach Auswählen der Kachel zu dem Bericht, der Excel Online-Arbeitsmappe, dem lokalen SSRS-Bericht oder der Q&A-Frage, der/die zum Erstellen der Kachel verwendet wurde.

> [!NOTE]
> Eine Ausnahme sind Videokacheln, die direkt auf dem Dashboard mit **Kachel hinzufügen** erstellt wurden. Bei Auswählen einer Videokachel (die auf diese Weise erstellt wurde) wird das Video direkt auf dem Dashboard wiedergegeben.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
* Wenn der Bericht, der zum Erstellen der Visualisierung verwendet wurde, nicht gespeichert wurde, löst das Auswählen der Kachel keine Aktion aus.
* Wenn die Kachel anhand einer Arbeitsmappe in Excel Online erstellt wurde und Sie nicht mindestens Leseberechtigungen für diese Arbeitsmappe haben, wird durch Auswählen der Kachel die Arbeitsmappe nicht in Excel Online geöffnet.
* Wenn für Kacheln, die mit **Kacheln hinzufügen** direkt auf dem Dashboard erstellt wurden, ein benutzerdefinierter Link festgelegt wurde, wird die betreffende URL durch Auswählen des Titels, des Untertitels oder der Kachel geöffnet.  Standardmäßig erfolgt bei Auswahl einer dieser Kacheln direkt auf dem Dashboard für ein Bild, einen Webcode oder ein Textfeld keine Aktion.
* Wenn Sie über keine Berechtigungen zum Bericht in SSRS verfügen, führt die Auswahl einer über SSRS erstellten Kachel zur Anzeige einer Fehlerseite. Auf dieser werden Sie darauf hingewiesen, dass Sie keinen Zugriff haben (rsAccessDenied).
* Wenn Sie keinen Zugriff auf das Netzwerk mit SSRS haben, führt die Auswahl einer über SSRS erstellten Kachel zur Anzeige einer Fehlerseite. Auf dieser werden Sie darauf hingewiesen, dass der Server nicht gefunden wurde (HTTP 404). Ihr Gerät muss Netzwerkzugriff auf den Berichtsserver besitzen, um den Bericht anzeigen zu können.
* Wenn sich die ursprüngliche Visualisierung ändert, die zum Erstellen der Kachel verwendet wurde, ändert sich die Kachel nicht.  Wenn Sie beispielsweise ein Liniendiagramm aus einem Bericht angeheftet haben und dann das Liniendiagramm in ein Balkendiagramm ändern, wird auf der Dashboardkachel weiterhin ein Liniendiagramm angezeigt. Die Daten werden aktualisiert, der Visualisierungstyp hingegen nicht.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer großen numerischen Kachel aus einem Bericht](power-bi-visualization-big-number-report.md)

[Erstellen einer großen numerischen Kachel anhand von Q&A](power-bi-visualization-big-number.md)

[Dashboards in Power BI](service-dashboards.md)  

[Datenaktualisierung](refresh-data.md)

[Power BI – Grundkonzepte](service-basic-concepts.md)

[Exportieren einer Kachel nach PowerPoint](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Anheften von Reporting Services-Elementen an Power BI-Dashboards](https://msdn.microsoft.com/library/mt604784.aspx)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
