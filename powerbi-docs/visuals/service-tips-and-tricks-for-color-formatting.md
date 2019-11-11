---
title: Tipps und Tricks zur Farbformatierung in Power BI
description: Tipps und Tricks zur Farbformatierung in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3865647a056e28735894e40f71045305518642c6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880638"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tipps und Tricks zur Farbformatierung in Power BI
Power BI bietet viele unterschiedliche Methoden zum Anpassen der Dashboards und Berichte. In diesem Artikel erhalten Sie Tipps, wie Sie Ihre Power BI-Visualisierungen ansprechender, interessanter und personalisierter gestalten können.

Nachfolgend finden Sie einige Tipps. Haben Sie weitere tolle Tipps? Sehr gut! Wenn Sie sie uns zukommen lassen, nehmen wir sie möglicherweise in diese Liste auf.

* Farbe eines einzelnen Datenpunkts ändern
* Farben eines Diagramms nach einem numerischen Wert vergeben
* Farbe der Datenpunkte nach einem numerischen Wert vergeben
* Farben in der Farbskala anpassen
* Abweichende Farbskalen verwenden
* Änderungen in Power BI rückgängig machen

Um Änderungen vorzunehmen, müssen Sie einen Bericht bearbeiten. Öffnen Sie den Bericht, und wählen Sie im oberen Menübereich **Bericht bearbeiten** aus, wie im folgenden Bild gezeigt.

![Position des Menüs „Bearbeiten“](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-report.png)

Wenn die Bereiche **Filter** und **Visualisierungen** auf der rechten Seite des Berichtszeichenbereichs angezeigt werden, können Sie den Bericht anpassen. Wenn der Bereich nicht angezeigt wird, klicken Sie auf den Pfeil in der oberen rechten Ecke, um ihn zu öffnen.

![Berichtszeichenbereich in der Bearbeitungsansicht](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

## <a name="change-the-color-of-a-single-data-point"></a>Farbe eines einzelnen Datenpunkts ändern
Unter Umständen möchten Sie einen bestimmten Datenpunkt markieren. Möglicherweise handelt es sich dabei um die Verkaufszahlen für ein neu eingeführtes Produkt oder bessere Qualitätsergebnisse nach der Einführung eines neuen Programms. Mit Power BI können Sie einen bestimmten Datenpunkt hervorheben, indem Sie seine Farbe ändern.

In der folgenden Visualisierung werden verkaufte Einheiten nach Produktsegment angeordnet. 

![Ändern der Datenfarben in Grau](media/service-tips-and-tricks-for-color-formatting/power-bi-data.png)

Stellen Sie sich vor, dass Sie das Segment **Convenience** farblich hervorheben möchten, um zu zeigen, wie gut dieses brandneue Segment abschneidet. Gehen Sie wie folgt vor:

Erweitern Sie den Abschnitt **Datenfarben**, und aktivieren Sie den Schieberegler für **Alles einblenden**. Die Farben für jedes Datenelement in der Visualisierung werden angezeigt. Wenn Sie auf die Datenpunkte zeigen, wird der Bildlauf aktiviert, sodass Sie alle Datenpunkte ändern können.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show.png)

Legen Sie **Convenience** auf Orange fest. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Sobald die Auswahl getroffen wurde, wird der Datenpunkt **Convenience** in einem ansprechenden Orange hervorgehoben.

Auch wenn Sie Visualisierungstypen ändern und später zurückkehren, speichert Power BI Ihre Auswahl und markiert **Convenience** in Orange.

Sie können die Farbe eines Datenpunkts für einzelne, mehrere oder alle Datenelemente in der Visualisierung ändern. Vielleicht möchten Sie Ihr Visual an Ihre Unternehmensfarben anpassen. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Farben bieten Ihnen viele Gestaltungsmöglichkeiten. Im nächsten Abschnitt prüfen wir Farbverläufe.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>Farben eines Diagramms nach einem numerischen Wert vergeben
Diagramme lassen sich mit dynamischen Farbeinstellungen nach dem numerischen Wert eines Felds ansprechend gestalten. Dadurch können Sie einen anderen als für die Größe eines Balkens verwendeten Wert anzeigen und die beiden Werte in einer einzelnen Grafik anzeigen. Sie können damit auch Datenpunkte markieren, die über (oder unter) einem bestimmten Wert liegen, z. B. Bereiche mit geringer Rentabilität.

Die folgenden Abschnitte zeigen die verschiedene Methoden, Farben auf Grundlage eines numerischen Werts anzupassen.

## <a name="base-the-color-of-data-points-on-a-value"></a>Farbe von Datenpunkten nach einem numerischen Wert vergeben
Öffnen Sie den Bereich „Formatierung“, und wählen Sie die Option **Bedingte Formatierung** aus, um die auf einem Wert basierende Farbe zu ändern.  

![Auswählen der Option „Bedingte Formatierung“ durch Klicken auf die drei vertikalen Punkte](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting.png)

Verwenden Sie im Bereich „Standardfarben“ die Dropdownlisten, um die Felder zu identifizieren, die für die bedingte Formatierung verwendet werden. In diesem Beispiel wird das Feld **Sales fact** > **Total Units** ausgewählt und hellblau für **Niedrigster Wert** bzw. dunkelblau für **Höchster Wert** verwendet. 

![Einstellungen für die bedingte Formatierung von Datenfarben](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![Säulendiagramm, für das die Standardfarben verwendet werden](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

Sie können die Farbe des Visuals mithilfe eines Felds formatieren, das nicht Teil des Visuals ist. In der folgenden Abbildung wird **%Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) verwendet. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


Sie sehen, dass zwar mehr Einheiten aus den Bereichen **Productivity** (Produktivität) und **Extreme** verkauft wurden (die Säulen sind höher), **Moderation** aber dennoch einen höheren Wert für **%Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) aufweist (die Säule zeigt eine stärkere Farbsättigung).

## <a name="customize-the-colors-used-in-the-color-scale"></a>Farben in der Farbskala individuell anpassen
Sie können auch ändern, wie die Werte diesen Farben zugeordnet werden. In der folgenden Abbildung werden für **Minimal** und **Maximal** die Farben Orange und Grün festgelegt.

Achten Sie im ersten Bild darauf, wie die Balken im Diagramm den Farbverlauf in der Farbverlaufsleiste widerspiegeln. Der höchste Wert ist Grün, ist der niedrigste ist Orange, und jeder Balken dazwischen wird mit einer Farbe zwischen Grün und Orange gekennzeichnet.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Lassen Sie uns überprüfen, was passiert, wenn wir in den Feldern **Minimum** und **Maximum** numerische Werte angeben. Legen Sie **Minimum** auf 3.500 und **Maximum** auf 6.000 fest.

Werden diese Werte festgelegt, wird der Farbverlauf nicht mehr auf die Werte im Diagramm angewendet, die unter dem **Minimum** oder über dem **Maximum** liegen. Alle Balken mit Werten oberhalb des **Maximums** werden grün, alle Balken mit Werten unterhalb des **Minimums** rot markiert.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

## <a name="use-diverging-color-scales"></a>Abweichende Farbskalen verwenden
Manchmal verfügen Ihre Daten über natürlich abweichende Skalen. Beispielsweise liegt bei einem Temperaturbereich die natürliche Mitte am Gefrierpunkt, und eine Rentabilitätsbewertung hat einen natürlichen Mittelpunkt (Null).

Wählen Sie die Option **Abweichend** aus, um abweichende Farbskalen zu verwenden. Wenn **Abweichend** aktiviert ist, wird wie im Folgenden dargestellt eine zusätzliche Farbauswahl namens **Mitte** angezeigt.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging2.png)

Wenn der Schieberegler **Abweichend** aktiviert ist, können Sie die Farben für **Minimal**, **Maximal** und **Mitte** separat auswählen. In der folgenden Abbildung wird die **Mitte** für **% Market Share SPLY YTD** (% Marktanteil im gleichen Vorjahreszeitraum seit Jahresbeginn) auf „0,2“ festgelegt, sodass Balken mit Werten über 0,2 in einem Grünton und Balken mit Werten unter 0,2 in einem Rotton angezeigt werden.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="how-to-undo-in-power-bi"></a>Änderungen in Power BI rückgängig machen
Wie viele andere Microsoft-Dienste und Software bietet Power BI eine einfache Möglichkeit, den letzten Befehl rückgängig zu machen. Nehmen wir an, Sie ändern die Farbe eines Datenpunkts oder eine Reihe von Datenpunkten, und die Farbe gefällt Ihnen nicht, wenn sie in der Visualisierung angezeigt wird. Sie wissen nicht genau, wie die Farbe zuvor festgelegt war, aber Sie möchten wieder diese Farbe angezeigt bekommen.

Sie können Ihre letzte Aktion bzw. die letzten paar Aktionen ganz einfach **rückgängig machen**:

- Geben Sie STRG + Z ein.

## <a name="feedback"></a>Feedback
Haben Sie einen Tipp, von dem Sie berichten möchten? Bitte lassen Sie ihn uns zukommen –möglicherweise nehmen wir ihn in diese Liste auf.

>[!NOTE]
>Die Farb- und Achseneinstellungen sowie die zugehörigen Anpassungen, die bei Auswahl des Symbols **Format** verfügbar sind, stehen auch in Power BI Desktop zur Verfügung.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Farbeinstellungen und Achseneigenschaften](service-getting-started-with-color-formatting-and-axis-properties.md)

