---
title: Ändern der Sortierung eines Diagramms in einem Bericht
description: Ändern der Sortierung eines Diagramms in einem Power BI-Bericht
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302747"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Ändern der Sortierung eines Diagramms in einem Power BI-Bericht
In einem Power BI-Bericht können Sie die meisten Visualisierungen alphabetisch nach den Namen der Kategorien im Diagramm oder nach den numerischen Werten jeder Kategorie sortieren. In diesem Diagramm wird z.B. nach der Kategorie **Geschäftsname** sortiert.

![Balkendiagramm mit alphabetischer Sortierung an der X-Achse](media/end-user-change-sort/pbi_chartsortcategory.png)

Sie können ganz einfach statt nach einer Kategorie (Geschäftsname) nach einem Wert (Umsatz pro Quadratfuß) sortieren.

1. Wählen Sie die Auslassungspunkte (...) aus und anschließend **Sortieren nach > Sales Per Sq Ft** (Verkäufe pro Quadratmeter).
2. Wählen Sie bei Bedarf erneut die Auslassungspunkte und anschließend **Absteigend sortieren**.

   ![Video: Auswählen von „Sortieren nach“ und dann „Aufsteigend sortieren“, „Absteigend sortieren“](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Nicht alle Visuals können sortiert werden. Beispielsweise können die folgenden Visuals nicht sortiert werden: Treemaps, Karten, Flächenkartogramme, Punktdiagramme, Tachometerdiagramme, Kartendiagramme, Wasserfalldiagramme.

## <a name="saving-changes-you-make-to-sort-order"></a>Speichern der Änderungen an der Sortierreihenfolge
Power BI-Berichte behalten die von Ihnen vorgenommenen Änderungen am Filter, Slicer, der Sortierung und anderen Datenansichten, bei. Wenn Sie also den Bericht verlassen und später zurückkehren, sind Ihre Änderungen gespeichert.  Wenn Sie Ihre Änderungen auf die Einstellungen des Berichts-Designers zurücksetzen möchten, wählen Sie aus der oberen Menüleiste **Auf Standardwert zurücksetzen** aus. 

![Sortierung beibehalten](media/end-user-change-sort/power-bi-reset.png)

Ist die Schaltfläche **Auf Standardwert zurücksetzen** jedoch ausgegraut, bedeutet das, dass der Berichts-Designer die Option zum Speichern (Beibehalten) der Änderungen deaktiviert hat.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sortieren mithilfe anderer Kriterien
Zuweilen möchten Sie Ihre Visualisierung anhand eines anderen Felds oder anderer Kriterien sortieren,  beispielsweise nach Monat (anstatt in alphabetischer Reihenfolge) oder nach ganzen Zahlen anstatt nach Ziffer (z. B. 0, 1, 9, 20 und nicht 0, 1, 20, 9).  

In einigen Fällen können Sie möglicherweise das visuelle Element so sortieren, wie Sie möchten, z.B. nach Monat.  Wenn dies jedoch nicht möglich ist, kann die Ursache sein, dass das dem Bericht zugrunde liegende Dataset optimiert werden muss. Bitten Sie den Berichts-Designer, das Dataset zu aktualisieren.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu [Visualisierungen in Power BI-Berichten](end-user-visualizations.md).

[Power BI – Grundkonzepte](end-user-basic-concepts.md)
