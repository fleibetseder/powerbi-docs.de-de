---
title: Ändern der Sortierung eines Diagramms in einem Bericht
description: Ändern der Sortierung eines Diagramms in einem Power BI-Bericht
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852388"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändern der Sortierung eines Diagramms in einem Power BI-Bericht

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Im Power BI-Dienst können Sie das Erscheinungsbild eines Visuals ändern, indem Sie es nach verschiedenen Datenfeldern sortieren. Indem Sie die Sortierung eines Visuals ändern, können Sie die Informationen hervorheben, die Sie vermitteln möchten, und sicherstellen, dass das Visual den gewünschten Trend (oder den gewünschten zentralen Aspekt) widerspiegelt.

Ob Sie numerische Daten (z.B. Umsatzzahlen) oder Text (z.B. Ländernamen) verwenden – die Visualisierungen lassen sich wunschgemäß sortieren und optisch aufbereiten. Power BI bietet große Flexibilität beim Sortieren sowie Schnellmenüs. Wählen Sie für ein beliebiges Visual **Weitere Aktionen** (...) und anschließend das Feld aus, nach dem Sie sortieren möchten.

![Balkendiagramm mit alphabetischer Sortierung an der X-Achse](media/end-user-change-sort/power-bi-more-actions.png)

In einem Power BI-Bericht können Sie die meisten Visualisierungen alphabetisch nach den Namen der Kategorien im Diagramm oder nach den numerischen Werten jeder Kategorie sortieren. In diesem Diagramm wird z.B. alphabetisch nach der Kategorie **Geschäftsname** sortiert.

![Balkendiagramm mit alphabetischer Sortierung an der X-Achse](media/end-user-change-sort/pbi-chartsortcategory.png)

Sie können ganz einfach statt nach einer Kategorie (Geschäftsname) nach einem Wert (Umsatz pro Quadratfuß) sortieren.

1. Wählen Sie die **Weitere Aktionen** (...) und anschließend **Sortieren nach > Sales Per Sq Ft** (Verkäufe pro Quadratmeter) aus.
2. Wählen Sie erforderlichenfalls noch einmal **Weitere Aktionen** (...) und dann **Absteigend sortieren** aus. Das Feld, das zum Sortieren verwendet wird, ist fett dargestellt und weist eine gelbe Leiste auf.

   ![Video: Auswählen von „Sortieren nach“ und dann „Aufsteigend sortieren“, „Absteigend sortieren“](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nicht alle Visuals können sortiert werden. Beispielsweise können die folgenden Visuals nicht sortiert werden: Treemaps, Karten, Flächenkartogramme, Punktdiagramme, Tachometerdiagramme, Kartendiagramme, Wasserfalldiagramme.

## <a name="saving-changes-you-make-to-sort-order"></a>Speichern der Änderungen an der Sortierreihenfolge
Power BI-Berichte behalten die von Ihnen vorgenommenen Änderungen am Filter, Slicer, der Sortierung und anderen Datenansichten, bei. Wenn Sie also den Bericht verlassen und später zurückkehren, sind Ihre Änderungen gespeichert.  Wenn Sie Ihre Änderungen auf die Einstellungen des Berichts-Designers zurücksetzen möchten, wählen Sie aus der oberen Menüleiste **Auf Standardwert zurücksetzen** aus. 

![Sortierung beibehalten](media/end-user-change-sort/power-bi-reset.png)

Ist die Schaltfläche **Auf Standardwert zurücksetzen** jedoch ausgegraut, bedeutet das, dass der Berichts-Designer die Option zum Speichern (Beibehalten) der Änderungen deaktiviert hat.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortieren mithilfe anderer Kriterien
Zuweilen möchten Sie Ihre Visualisierung anhand eines anderen Felds (das nicht im Visual enthalten ist) oder anderer Kriterien sortieren,  beispielsweise nach Monat (anstatt in alphabetischer Reihenfolge) oder nach ganzen Zahlen anstatt nach Ziffer (z. B. 0, 1, 9, 20 und nicht 0, 1, 20, 9).  Der Entwerfer des Berichts ist imstande, das Dataset zu aktualisieren, um diese Art Sortierung zu ermöglichen. Kontaktinformationen für den Entwerfer können Sie erfahren, indem Sie den Namen des Berichts in der Kopfleiste auswählen.

![Dropdownfeld mit Kontaktinformationen](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu [Visualisierungen in Power BI-Berichten](end-user-visualizations.md).

[Power BI – Grundkonzepte](end-user-basic-concepts.md)
