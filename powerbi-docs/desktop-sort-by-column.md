---
title: Sortieren nach Spalten in Power BI Desktop
description: Sortieren nach Spalten in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 53fc561e2f8dcb4869eff6e6fd172c8a3663840d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514013"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Sortieren nach Spalten in Power BI Desktop
In **Power BI Desktop** und im **Power BI-Dienst** können Sie das Erscheinungsbild eines Visuals ändern, indem Sie es nach verschiedenen Datenfeldern sortieren. Indem Sie die Sortierung eines Visuals ändern, können Sie die Informationen hervorheben, die Sie vermitteln möchten, und sicherstellen, dass das Visual den gewünschten Trend (oder den gewünschten zentralen Aspekt) widerspiegelt.

Ob Sie numerische Daten (z.B. Umsatzzahlen) oder Text (z.B. Ländernamen) verwenden – die Visualisierungen lassen sich wunschgemäß sortieren und optisch aufbereiten.  **Power BI** bietet große Flexibilität beim Sortieren sowie Schnellmenüs. Wählen Sie in einem Visual das Menü mit den Auslassungszeichen (...) und dann das Feld aus, nach dem sortiert werden soll, wie in der folgenden Abbildung dargestellt.

![Menü „Mehr Optionen“](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="more-depth-and-an-example"></a>Ausführliches Beispiel
Sehen wir uns ein ausführliches Beispiel an und wie es in **Power BI Desktop** funktioniert.

In der folgenden Visualisierung sind die Kosten, die Verkaufsmenge sowie der Rabattbetrag für den jeweiligen Herstellernamen aufgeführt. Hier sehen Sie die Visualisierung vor dem weiteren Sortieren.

![Erste Visualisierung](media/desktop-sort-by-column/sortbycolumn_1.png)

Das visuelle Element ist derzeit nach **SalesQuantity** sortiert – dies wird durch Farbvergleich der absteigenden Balken mit der Legende ersichtlich. Es gibt jedoch eine bessere Möglichkeit zum Festlegen der aktuellen Sortierspalte: das Menü mit den Auslassungszeichen („...“) oben rechts im Visual. Nach Auswahl der Auslassungspunkte wird Folgendes angezeigt:

![Menü „Mehr Optionen“](media/desktop-sort-by-column/sortbycolumn_2.png)

* Das aktuelle Sortierfeld ist **SalesQuantity**, was durch den Fettdruck und die gelbe Leiste von **Sort By SalesQuantity** angegeben wird. 

* Die derzeitige Sortierrichtung ist von klein nach groß, was von dem kleinen Symbol **A/Z** (A nach Z) und einem Pfeil nach unten angegeben wird.

In den nächsten beiden Abschnitten betrachten wir das Sortierfeld und die -richtung unabhängig voneinander.

## <a name="selecting-which-column-to-use-for-sorting"></a>Auswählen der Sortierspalte
Möglicherweise haben Sie schon die gelbe Leiste neben **Sort By SalesQuantity** im Menü **Weitere Optionen** gesehen, die angibt, dass das Visual nach **SalesQuantity** sortiert ist. Das Sortieren nach einer anderen Spalte ist einfach – klicken Sie dazu auf die Auslassungszeichen, um das Menü unter Auslassungspunkten aufzurufen, und wählen Sie dann eine andere Spalte aus.

In der folgenden Abbildung wurde die Spalte *DiscountAmount* als Sortierspalte ausgewählt. Diese Spalte entspricht einer Linie im visuellen Element und keinem Balken. Nachstehend finden Sie die Darstellung nach Auswahl von **Sortieren nach DiscountAmount**.

![Sortieren nach DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

Beachten Sie, wie sich das visuelle Element geändert hat. Die Werte werden nun vom höchsten DiscountAmount-Wert im Visual „Fabrikam Inc.“ nach unten zum Hersteller „Northwind Traders“ sortiert, der über den niedrigsten Wert verfügt. 

Aber was geschieht, wenn wir statt in absteigender Reihenfolge aufsteigend sortieren möchten? Im nächsten Abschnitt wird gezeigt, wie einfach das ist.

## <a name="selecting-the-sort-order---smallest-to-largest-largest-to-smallest"></a>Auswählen der Sortierreihenfolge – vom kleinsten zum größten und umgekehrt
Ein genauerer Blick auf das Menü **Optionen** in der vorherigen Abbildung zeigt im Symbol neben **Sortieren nach DiscountAmount** den Schriftzug **Z/A** (Z nach A). Dies hat folgende Bedeutung:

![Nach Größe sortieren (absteigend)](media/desktop-sort-by-column/sortbycolumn_4.png)

Wenn **Z/A** angezeigt wird, zeigt dies eine Sortierreihenfolge im visuellen Element an, bei der zunächst der größte Wert und dann nacheinander die Werte bis hin zum kleinsten Wert berücksichtigt werden. Sie möchten dies ändern? Kein Problem – tippen oder klicken Sie hierzu einfach auf das Symbol **Z/A**. Damit ändern Sie die Sortierreihenfolge in **A/Z**, und im visuellen Element (in Bezug auf die ausgewählte Spalte) werden zunächst der kleinste Wert und dann die Werte bis hin zum größten Wert berücksichtigt.

Die Abbildung zeigt wieder dasselbe Visual, dieses Mal jedoch nach Tippen auf das Symbol **Z/A** im Menüelement **Sortieren nach DiscountAmount** zum Ändern der Sortierreihenfolge. Beachten Sie, dass Northwind Traders nun der erste aufgeführte Hersteller ist und Fabrikam Inc. der letzte – also das genaue Gegenteil wie zuvor.

![Nach Größe sortieren (aufsteigend)](media/desktop-sort-by-column/sortbycolumn_5.png)

Die Darstellung lässt sich nach jeder im visuellen Element enthaltenen Spalte sortieren – beispielsweise könnte „SalesQuantity“ als Sortierspalte ausgewählt werden mit **Sortieren nach SalesQuantity**, um die Hersteller mit den meisten Verkäufen anzuzeigen. Die anderen Spalten werden dennoch im Visual berücksichtigt, wie auch immer sie für den betreffenden Hersteller gelten. Hier sehen Sie das visuelle Element mit den genannten Einstellungen.

![Sortieren nach SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Sortieren mit der Schaltfläche „Nach Spalte sortieren“
Es gibt eine weitere Möglichkeit zum Sortieren von Daten. Sie können auf die Schaltfläche **Nach Spalte sortieren** im Menüband **Modellierung** klicken.

![Sortieren nach Spalte (Schaltfläche)](media/desktop-sort-by-column/sortbycolumn_8.png)

Bei diesem Verfahren zum Sortieren müssen Sie eine Spalte im Bereich **Felder** auswählen und anschließend auf die Schaltfläche **Nach Spalte sortieren** klicken, um auszuwählen, wie (d.h. nach welcher Spalte) die Visualisierung sortiert werden soll. Sie müssen die Spalte (Feld) im Bereich **Felder** auswählen, nach der sortiert werden soll, um die Schaltfläche **Nach Spalte sortieren** zu aktivieren – andernfalls ist die Schaltfläche inaktiv.

Ein typisches Beispiel: Sie verfügen über Daten für die einzelnen Monate des Jahres, und diese sollen chronologisch sortiert werden. In den folgenden Schritten wird die Vorgehensweise erläutert.

1. Zunächst stellen Sie Folgendes fest: Wenn die Visualisierung, jedoch keine Spalte im Bereich **Felder** ausgewählt ist, ist die Schaltfläche **Nach Spalte sortieren** inaktiv (abgeblendet dargestellt).
   
   ![Inaktive „Nach Spalte sortieren“-Schaltfläche](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Wenn Sie im Bereich **Felder** die Spalte auswählen, nach der sortiert werden soll, wird die Schaltfläche **Nach Spalte sortieren** aktiviert.
   
   ![Aktive „Nach Spalte sortieren“-Schaltfläche](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Nun können Sie bei ausgewähltem Visual die Spalte *MonthOfYear* anstelle der Standardspalte (*MonthName*) auswählen, und das Visual wird in der gewünschten Reihenfolge sortiert: nach dem Monat des Jahres.
   
   ![Nach Spalte sortieren (Menü)](media/desktop-sort-by-column/sortbycolumn_11.png)

Und das ist auch schon alles. Denken Sie daran, dass Sie im Bereich **Felder** eine Spalte auswählen müssen, damit die Schaltfläche **Nach Spalte sortieren** aktiviert wird.

## <a name="getting-back-to-default-column-for-sorting"></a>Wiederherstellen der Standardsortierspalte
Sie können nach einer beliebigen gewünschten Spalte sortieren, aber in bestimmten Situationen soll das visuelle Element anschließend wieder anhand der Standardsortierspalte dargestellt werden. Kein Problem. Öffnen Sie bei einem Visual mit ausgewählter Sortierspalte (die durch einen gelben Balken im Menü mit den Auslassungspunkten gekennzeichnet ist) einfach das Menü **Weitere Optionen**, und wählen Sie die Spalte erneut aus, damit für die Visualisierung wieder die Standardsortierspalte verwendet wird.

Hier ist z. B. das vorherige Diagramm:

![Erste Visualisierung](media/desktop-sort-by-column/sortbycolumn_6.png)

Wenn im Menü erneut **SalesQuantity** ausgewählt wird, wird für das Visual wieder das Standardverhalten angewendet. Somit erfolgt eine alphabetische Sortierung nach **Manufacturer**, wie in der folgenden Abbildung gezeigt.

![Standardsortierspalte](media/desktop-sort-by-column/sortbycolumn_7.png)

Durch die vielen Optionen beim Sortieren der visuellen Elemente wird das Erstellen eines wunschgemäßen Diagramms oder Bilds vereinfacht.

