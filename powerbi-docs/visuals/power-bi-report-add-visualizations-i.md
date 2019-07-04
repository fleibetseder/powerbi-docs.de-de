---
title: Teil 1 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
description: Teil 1 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299184"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Teil 1 – Hinzufügen von Visualisierungen zu einem Power BI-Bericht

Dieser Artikel enthält eine kurze Einführung in das Erstellen einer Visualisierung in einem Bericht. Er gilt sowohl für den Power BI-Dienst als auch für Power BI Desktop. Komplexere Inhalte [finden Sie in Teil 2](power-bi-report-add-visualizations-ii.md) dieser Serie. Sehen Sie, wie Amanda verschiedene Methoden zum Erstellen, Bearbeiten und Formatieren von Visuals im Berichtszeichenbereich demonstriert. Versuchen Sie es dann selbst, indem Sie das [Beispiel für Vertrieb und Marketing](../sample-datasets.md) verwenden, um einen eigenen Bericht zu erstellen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Öffnen eines Berichts und Hinzufügen einer neuen Seite

1. Öffnen Sie einen Bericht in der [Bearbeitungsansicht](../service-interact-with-a-report-in-editing-view.md).

    In diesem Lernprogramm wird das [Beispiel für Vertrieb und Marketing](../sample-datasets.md) genutzt.

1. Wenn der **Felderbereich** nicht sichtbar ist, wählen Sie das Pfeilsymbol aus, um ihn zu öffnen.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Fügen Sie dem Bericht eine leere Seite hinzu.

## <a name="add-visualizations-to-the-report"></a>Hinzufügen von Visualisierungen zum Bericht

1. Erstellen Sie eine Visualisierung durch Auswahl eines Felds aus dem Bereich **Felder** .

    Beginnen Sie mit einem numerischen Feld wie **SalesFact** > **Sales $** . Power BI erstellt ein Säulendiagramm mit einer einzelnen Spalte.

    ![Screenshot eines Säulendiagramms mit einer einzelnen Spalte.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Beginnen Sie alternativ mit einem Kategoriefeld, z.B. **Name** oder **Produkt**. Power BI erstellt eine Tabelle und fügt das Feld dem Bereich **Werte** hinzu.

    ![GIF-Animation, die zeigt, wie eine Person „Produkt“ und dann „Kategorie“ auswählt, um eine Tabelle zu erstellen.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Beginnen Sie alternativ mit einem geografischen Feld wie **Geo** > **City** (Stadt). Power BI und Bing Maps erstellen eine Kartenvisualisierung.

    ![Screenshot einer Kartenvisualisierung.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Erstellen Sie eine Visualisierung, und ändern Sie deren Typ. Wählen Sie **Product** (Produkt) > **Category** (Kategorie) und dann **Product** > **Count of Product** (Produktanzahl) aus, um beide dem Bereich **Values** (Werte) hinzuzufügen.

   ![Screenshot des Bereichs „Felder“, wobei „Werte“ hervorgehoben ist.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Ändern Sie die Visualisierung in einem Säulendiagramm, indem Sie das Symbol **Gestapeltes Säulendiagramm** auswählen.

   ![Screenshot des Bereichs „Visualisierungen“ mit hervorgehobener Option „Gestapeltes Säulendiagramm“.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Wenn Sie Visualisierungen in Ihrem Bericht erstellen, können Sie sie [an Ihr Dashboard anheften](../service-dashboard-pin-tile-from-report.md). Um die Visualisierung anzuheften, wählen Sie das Anheftsymbol ![Screenshot des Anheftsymbols](media/power-bi-report-add-visualizations-i/pinnooutline.png) aus.

   ![Screenshot einer Säulendiagrammvisualisierung mit hervorgehobenem Anheftsymbol.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Nächste Schritte

 Fahren Sie fort mit:

* [Teil 2: Hinzufügen von Visualisierungen zu einem Power BI-Bericht](power-bi-report-add-visualizations-ii.md)

* [Mit den Visualisierungen](../consumer/end-user-reading-view.md) im Bericht interagieren

* [Weiter Aktionen mit Visualisierungen ausführen](power-bi-report-visualizations.md)

* [Den Bericht speichern](../service-report-save.md)
