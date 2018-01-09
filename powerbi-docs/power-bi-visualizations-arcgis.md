---
title: "Interagieren mit einer ArcGIS-Karte, die für Sie freigegeben wurde"
description: 'Verwenden einer ArcGis-Karte in der Leseansicht '
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: power bi, service, desktop, mobile
featuredvideoid: 
qualityfocus: monitoring
qualitydate: 06/23/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: 511f01494410215451d9f77ff637c7cfce8e89b3
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2017
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Interagieren mit ArcGIS-Karten in Power BI
Dieses Thema ist für Personen verfasst, die ArcGIS-Karten im Power BI-Dienst, in Power BI Desktop oder in einer mobilen Power BI-App *nutzen*. Sobald ein Ersteller eine ArcGIS-Karte für Sie freigegeben hat, gibt es viele Möglichkeiten für die Interaktion mit dieser Karte.  Weitere Informationen zum Erstellen einer ArcGIS-Karte finden Sie im [Tutorial zu ArcGIS Maps von ESRI](power-bi-visualization-arcgis.md).

Die Kombination von ArcGIS Maps und Power BI bietet völlig neue Möglichkeiten der Kartendarstellung, die über die Darstellung von Punkten auf einer Karte weit hinausgeht. Die verfügbaren Optionen für Basiskarten, Standorttypen, Designs, Symbolstile und Referenzebenen ermöglichen das Erstellen von beeindruckenden, aussagekräftigen Kartenvisualisierungen. Die Kombination von autoritativen Datenebenen (z.B. Volkszählungsdaten) auf einer Karte mit räumlicher Analyse vermittelt ein tieferes Verständnis der Daten in der Visualisierung.

> [!TIP]
> GIS steht für „Geographic Information Science“.
> 
> 

Das hier verwendete Beispiel ist die im [Tutorial zu ArcGIS Maps von ESRI](power-bi-visualization-arcgis.md) erstellte ArcGIS-Karte. In dieser wird der Vorjahresumsatz nach Ort ausgewertet. Es wird eine Basiskarte verwendet, die Größe wird durch Blasensymbole dargestellt, und für das mittlere Haushaltseinkommen wird eine Referenzebene verwendet. Die Karte enthält 3 Stecknadeln und einen Fahrzeitradius (in Violett).

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Besuchen Sie die [Seite von ESRI für Power BI](https://www.esri.com/powerbi), auf der Sie viele Beispiele und Kommentare von Kunden finden. Und besuchen Sie dann die [Seite für erste Schritte mit ArcGIS Maps für Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm) (in englischer Sprache) von ESRI.
> 
> 

<br/>

## <a name="user-consent"></a>Zustimmung des Benutzers
Wenn eine ArcGIS-Karte zum ersten Mal von einem Kollegen für Sie freigegeben wird, wird in Power BI eine Eingabeaufforderung angezeigt. ArcGIS Maps für Power BI wird von [ESRI](https://www.esri.com) bereitgestellt, und die Verwendung von ArcGIS Maps für Power BI unterliegt den Nutzungsbedingungen und der Datenschutzrichtlinie von Esri. Power BI-Benutzer, die Visuals von ArcGIS Maps für Power BI verwenden möchten, müssen die Informationen im Zustimmungsdialogfeld akzeptieren.

## <a name="selection-tools"></a>Auswahltools
ArcGIS-Karten für Power BI stellt drei Auswahlmodi bereit. Es können maximal 250 Datenpunkte gleichzeitig ausgewählt werden.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Wählt einzelne Datenpunkte aus.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) Zeichnet ein Rechteck auf der Karte und wählt die darin enthaltenen Datenpunkte aus. Mit STRG können Sie mehrere rechteckige Bereiche auswählen.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) Ermöglicht die Verwendung von Begrenzungen oder Polygonen in den Referenzebenen zum Auswählen von enthaltenen Datenpunkten.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Interagieren mit einer ArcGIS-Karte
Die für Sie verfügbaren Funktionen hängen davon ab, ob Sie der *Ersteller* (die Person, von der die Karte erstellt wurde) oder der *Nutzer* (jemand hat eine ArcGIS-Karte für Sie freigegeben) sind. Wenn Sie als Nutzer mit einer ArcGIS-Karte interagieren (auch als [Leseansicht](service-interact-with-a-report-in-reading-view.md) bezeichnet), sind die folgenden Aktionen für Sie verfügbar.

* Wie bei anderen Visualisierungstypen können Sie Elemente [an Dashboards anheften](service-dashboard-pin-tile-from-report.md), [die zugrunde liegenden Daten anzeigen](service-reports-show-data.md) und/oder [exportieren](power-bi-visualization-export-data.md) sowie die Karte im [Fokusmodus](service-focus-mode.md) und [Vollbildmodus](service-fullscreen-mode.md) anzeigen.    
* Erweitern Sie den Bereich **Filter**, um die Karte mithilfe von Filtern zu untersuchen. Wenn Sie den Bericht schließen, werden die angewendeten Filter nicht gespeichert.    
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* Wenn die Karte über eine Referenzebene verfügt, wählen Sie Standorte aus, um Details in einer QuickInfo anzuzeigen. In diesem Beispiel wurde Adams County ausgewählt, und es werden Daten aus der Referenzebene für das mittlere Haushaltseinkommen angezeigt, die der Karte vom Ersteller hinzugefügt wurde.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    In diesem Fall wird auch ein Diagramm angezeigt. Wählen Sie einen Balken im Diagramm aus, um die Daten genauer zu untersuchen. Hier lässt sich erkennen, dass 79 Haushalte in Adams County über ein Einkommen von mindestens 200.000 $ verfügen.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    Wählen Sie den Pfeil aus, um weitere Diagramme anzeigen.
* Zeigen Sie auf Standortsymbole der Basiskarte, um Details in einer QuickInfo anzuzeigen.     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > Möglicherweise müssen Sie zoomen, um einen bestimmten Standort auszuwählen.  Andernfalls werden möglicherweise mehrere QuickInfos gleichzeitig in Power BI angezeigt, wenn sich Standorte überlappen. Wählen Sie die Pfeile aus, um zwischen den QuickInfos zu wechseln.
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* Wenn der Ersteller der ArcGIS-Karte eine Infografikebene hinzugefügt hat, werden in der rechten oberen Ecke der Karte zusätzliche Daten angezeigt.  Hier hat z.B. der Kartenersteller „Children under 14“ (Kinder unter 14) hinzugefügt.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
ArcGIS Maps für Power BI ist in den folgenden Diensten und Anwendungen verfügbar:

<table>
<tr><th>Dienst/App</th><th>Verfügbarkeit</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Ja</td>
</tr>
<tr>
<td>Power BI-Dienst (PowerBI.com)</td>
<td>Ja</td>
</tr>
<tr>
<td>Mobile Apps für Power BI</td>
<td>Ja</td>
</tr>
<tr>
<td>Power BI-Webveröffentlichung</td>
<td>Nein</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Nein</td>
</tr>
<tr>
<td>Einbettung in den Power BI-Dienst (PowerBI.com)</td>
<td>Nein</td>
</tr>
</table>

**Die ArcGIS-Karte wird nicht angezeigt**    
In Diensten und Anwendungen, für die ArcGIS Maps für Power BI nicht verfügbar ist, wird statt der Visualisierung ein leeres Visual mit dem Power BI-Logo angezeigt.

**Auf der Karte werden nicht alle Adressen angezeigt**    
Bei der Geocodierung von Adressen werden nur die ersten 1500 Adressen verarbeitet. Ortsnamen und Länder sind von dieser Geocodierung-Einschränkung auf 1500 Einträge nicht betroffen.

**Fallen Gebühren für die Verwendung von ArcGIS-Karten für Power BI an?**

ArcGIS Maps für Power BI ist für alle Power BI-Benutzer ohne zusätzliche Kosten verfügbar. Dies ist eine von **Esri** bereitgestellte Komponente, die den Nutzungsbedingungen und der Datenschutzrichtlinie von **Esri** unterliegt, wie weiter oben in diesem Artikel beschrieben.

**Ich erhalte eine Fehlermeldung, dass der Cache voll ist**

Dieser Fehler ist bekannt und wird behoben.  Wählen Sie in der Zwischenzeit den in der Fehlermeldung angezeigten Link aus, um Anweisungen zum Leeren des Power BI-Caches zu erhalten.

**Kann ich meine ArcGIS-Karten offline anzeigen?**

Nein. Zum Anzeigen der Karten in Power BI ist eine Netzwerkverbindung erforderlich.

## <a name="next-steps"></a>Nächste Schritte
Hilfe: **ESRI** bietet eine [umfassende Dokumentation](https://go.microsoft.com/fwlink/?LinkID=828772) zu den Funktionen von **ArcGIS Maps für Power BI**.

In der [Power BI-Community finden Sie einen Thread zu **ArcGIS Maps für Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771) mit aktuellen Informationen. Dort können Sie auch Fragen stellen und Probleme melden.

Verbesserungsvorschläge können Sie an die [Ideensammlung für Power BI](https://ideas.powerbi.com) senden.

[Produktseite zu ArcGIS-Karten für Power BI](https://www.esri.com/powerbi)
