---
title: Einstieg in das Formatieren von Berichtsvisualisierungen
description: Einstieg in die Formatierungsoptionen für Berichtsvisualisierungen
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/14/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b42d83b4cea6f5f5e8908244b2b298dc3f327468
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540620"
---
# <a name="getting-started-with-the-formatting-pane"></a>Einstieg in den Formatierungsbereich
Wenn Sie über die nötigen Berechtigungen zum Bearbeiten von Berichten verfügen, stehen Ihnen zahlreiche Formatierungsoptionen zur Verfügung. In **Power BI**-Berichten können Sie die Farbe von Datenreihen und Datenpunkten und sogar den Hintergrund von Visualisierungen ändern. Sie können ändern, wie die x- und die y-Achse dargestellt werden. Sie können sogar die Schriftarteigenschaften von Visualisierungen, Formen und Titeln formatieren, und haben somit die vollständige Kontrolle über die Darstellung Ihrer Berichte.

Öffnen Sie zunächst einen Bericht in Power BI Desktop oder im Power BI-Dienst. Beide Dienste bieten beinahe identische Formatierungsoptionen. Wenn Sie einen Bericht im Power BI-Dienst öffnen, achten Sie darauf, in der Menüleiste **Bericht bearbeiten** auszuwählen.  

![Menüleiste mit der Option „Bearbeiten“](media/service-getting-started-with-color-formatting-and-axis-properties/power-bi-edit.png)

Wenn Sie eine Visualisierung ausgewählt haben und einen Bericht bearbeiten, wird der Bereich **Visualisierungen** angezeigt, in dem Sie Visualisierungen hinzufügen oder ändern können. Direkt unter den verfügbaren Visualisierungen werden drei Symbole angezeigt: **Felder** (zwei Kästchen), **Format** (eine Farbwalze) und **Analyse** (eine Lupe). In der folgenden Abbildung ist das Symbol **Felder** ausgewählt, was durch den einen gelben Balken unterhalb des Symbols erkennbar ist.

![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_2a.png)

Wenn Sie **Format**auswählen, zeigt der Bereich unterhalb des Symbols die verfügbaren Farb- und Achseneinstellungen der ausgewählten Visualisierung an.  

![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_3a.png)

Verschiedene Elemente der einzelnen Visualisierung können angepasst werden:

* Legende
* X-Achse
* Y-Achse
* Datenfarben
* Datenbeschriftungen
* Formen
* Zeichnungsfläche
* Titel
* Hintergrund
* Seitenverhältnis fixieren
* Rahmen

> [!NOTE]
>  
> Nicht bei jedem Visualisierungstyp werden all diese Elemente angezeigt. Die ausgewählte Visualisierung wirkt sich darauf aus, welche Anpassungen verfügbar sind. So wird Ihnen beispielsweise bei einem Kreisdiagramm keine X-Achse angezeigt, da Kreisdiagramme über keine X-Achsen verfügen.

Beachten Sie außerdem, dass **Filter** anstelle der Symbole angezeigt werden, wenn keine Visualisierung ausgewählt wurde. Dadurch können Sie die Filter auf alle Visualisierungen auf der Seite anwenden.

Im Folgenden finden Sie ein Beispiel zu Farben und eines zum Ändern der Achseneigenschaften. Diese Beispiele zeigen Ihnen, wie Farben, Achsen und Beschriftungen angepasst werden.

## <a name="working-with-colors"></a>Arbeiten mit Farben

Zum Anpassen von Farben in einem Diagramm sind die folgenden Schritte auszuführen.

1. Wählen Sie im Berichtszeichenbereich **Säulendiagramm (gruppiert)** aus.
2. Wählen Sie danach das Symbol **Format** aus, um die verfügbaren Anpassungsmöglichkeiten anzuzeigen.
3. Danach wählen Sie den kleinen Pfeil nach unten aus, der links von **Datenfarben** angezeigt wird. Dadurch sehen Sie, wie die Datenfarben mit den für die ausgewählte Visualisierung spezifischen Optionen angepasst werden können.
4. **Datenfarben** wird nach unten erweitert und zeigt die verfügbaren Anpassungen an.  
   ![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_4a.png)

Hier können Sie verschiedene Änderungen vornehmen. Mit dem Pfeil nach unten neben der Farbe ist es möglich, die verfügbaren Datenreihen zu ändern. In diesem Beispiel wählen wir Gelb für **Lebenshaltungskosten**, Orange für **Wetter** und Grün für **Gesellschaftliches Wohlbefinden**. Der folgende Bildschirm zeigt den letzten Schritt an, das Ändern der **Lebenshaltungskosten**.  

![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_5a.png)

Die Änderungen werden in der folgenden Abbildung dargestellt. Das Diagramm ist nun sehr farbenfroh. Beim Arbeiten mit Farben sind die folgenden Elemente sehr hilfreich. Die Zahlen in der folgenden Auflistung werden auf dem Bildschirm unten ebenfalls angezeigt. So sehen Sie, wo Sie auf diese Elemente zugreifen oder diese ändern.

1. Die Farben gefallen Ihnen nicht? Kein Problem: Über **Auf Standardwert zurücksetzen** wird Ihre Auswahl wieder auf die Standardeinstellungen zurückgesetzt. Dabei können Sie eine Farbe oder die gesamte Visualisierung zurücksetzen.
2. Möchten Sie eine Farbe auswählen, die Sie in der Palette nicht finden? Wählen Sie einfach **Benutzerdefinierte Farbe**aus, und Ihnen wird ein Farbspektrum angezeigt.  
   ![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_6a.png)

Gefällt Ihnen die zuletzt vorgenommene Änderung nicht? Mit **STRG + Z** machen Sie die letzte Änderung wie gewohnt rückgängig.

## <a name="changing-axis-properties"></a>Ändern der Achseneigenschaften

Häufig soll auch die X-Achse oder die Y-Achse geändert werden. Ähnlich wie bei den Farbeinstellungen können Sie auch die Achseneigenschaften ändern, indem Sie links neben der zu ändernden Achse den Pfeil nach unten auswählen, wie in der folgenden Abbildung dargestellt.  
![](media/service-getting-started-with-color-formatting-and-axis-properties/gettingstartedcolor_7a.png)

Wählen Sie zum Reduzieren der Optionen für die **X-Achsen** den Pfeil nach oben aus, der neben der **X-Achse**angezeigt wird.

Die Beschriftungen der X-Achse werden mithilfe des Optionsfelds neben der **X-Achse** komplett ausgeblendet. Das Optionsfeld neben **Titel**legt fest, ob Achsentitel ein- oder ausgeblendet werden.  

Auf Ihre Power BI-Berichte und Dashboards können Sie die verschiedensten Farben und viele weitere Anpassungsmöglichkeiten anwenden.

> [!NOTE]
>  
> Die Farb- und Achseneinstellungen sowie die zugehörigen Anpassungen, die bei Auswahl des Symbols **Format** verfügbar sind, stehen auch in Power BI Desktop zur Verfügung.

## <a name="setting-color-from-text-values"></a>Festlegen von Farben mithilfe von Textwerten

Ab dem **Power BI Desktop**-Update vom August 2018 können Sie für ein angegebenes Berichtselement Farben nach Textwert oder Hexadezimalcode festlegen. Weitere Informationen finden Sie unter [Bedingte Formatierung in Tabellen](../desktop-conditional-table-formatting.md).


## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie im folgenden Artikel:  

* [Tipps und Tricks zur Farbformatierung in Power BI](service-tips-and-tricks-for-color-formatting.md)  
* [Bedingte Formatierung in Tabellen](../desktop-conditional-table-formatting.md)

