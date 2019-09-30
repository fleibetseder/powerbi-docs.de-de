---
title: Interaktionen zwischen Visuals in einem Bericht
description: Dokumentation für Power BI-Endbenutzer, die erklärt, wie visuelle Elemente auf einer Berichtsseite interagieren.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: b95df5c32d9058e4480d7af5e226a971ba581144
ms.sourcegitcommit: 02042995df12cc4e4b97eb8a369e62364eb5af36
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256294"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Gegenseitige Kreuzfilterung von Visuals in einem Power BI-Bericht
Eines der herausragenden Features von Power BI ist die Art, auf die alle visuellen Elemente auf einer Berichtsseite miteinander verbunden sind. Wenn Sie in einem der visuellen Elemente einen Datenpunkt auswählen, ändern sich alle anderen visuellen Elemente auf der Seite, die diese Daten enthalten, auf Grundlage dieser Auswahl. 

![Video von interagierenden visuellen Elementen](media/end-user-interactions/interactions.gif)

Standardmäßig führt die Auswahl eines Datenpunkts in einer Visualisierung auf einer Berichtseite zu Kreuzfilterung und -hervorhebung sowie zu Drillvorgängen der anderen Visualisierungen auf der Seite. 

Dadurch lässt sich erkennen, wie die einzelnen Werte in Ihren Daten zusammenhängen. Wenn Sie beispielsweise den Abschnitt „Moderation“ des Ringdiagramms auswählen, wird der Beitrag dieses Abschnitts zu jeder Spalte des Diagramms „Total Units by Month“ hervorgehoben und das Liniendiagramm auf der rechten Seite entsprechend gefiltert.

![Darstellung von interagierenden Visuals](media/end-user-interactions/power-bi-interactions.png)

Siehe [Informationen zum Filtern und Hervorheben](../power-bi-reports-filters-and-highlighting.md). 

Wie visuelle Elemente auf einer Seite genau miteinander interagieren, wird vom *Designer* des Berichts festgelegt. Designer können visuelle Interaktionen aktivieren und deaktivieren sowie das Standardverhalten von Kreuzfilterung und -hervorhebung sowie Drillvorgängen ändern. 
  
> [!NOTE]
> Die Begriffe *Kreuzfilterung* und *Kreuzhervorhebung* werden verwendet, um das hier beschriebene Verhalten davon zu unterscheiden, was geschieht, wenn Sie den Bereich **Filter** zum Filtern und Hervorheben von Visualisierungen verwenden.  

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
- Verfügt der Bericht über eine Visualisierung, die [Drilling](../power-bi-visualization-drill-down.md) unterstützt, hat das Drilling einer Visualisierung standardmäßig keinen Einfluss auf die anderen Visualisierungen auf der Berichtseite.     
- Interagiert Visual A mit Visual B, werden die Filter auf Visualebene von Visual A auch auf Visual B angewendet.

## <a name="next-steps"></a>Nächste Schritte
[Verwenden von Berichtsfiltern](../power-bi-how-to-report-filter.md)
