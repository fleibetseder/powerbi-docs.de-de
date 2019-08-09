---
title: Analysebereich
description: Erstellen dynamischer Bezugslinien in Power BI-Visuals
author: Guy-Moses
ms.author: guymos
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b3b50f8dbcf40a3923e86422e24f8ed020894445
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425526"
---
# <a name="analytics-pane-in-power-bi-visuals"></a>Analysebereich in Power BI-Visuals

Der **Analysebereich** wurde im November 2018 für [native Visuals eingeführt](https://docs.microsoft.com/power-bi/desktop-analytics-pane).
Für benutzerdefinierte, mit API 2.5.0 erstellte Visuals können Eigenschaften im **Analysebereich** dargestellt und verwaltet werden.

![Analysebereich](./media/visualization-pane-analytics-tab.png)

Die Vorgehensweise ähnelt dem [Verwalten von Eigenschaften im Formatbereich](https://docs.microsoft.com/power-bi/developer/custom-visual-develop-tutorial-format-options), da ein Objekt in der Datei „capabilities.json“ des Visuals definiert wird. 

Es gibt folgende Unterschiede:

1. Fügen Sie unter der Definition von `object` ein `objectCategory`-Feld mit dem Wert 2 hinzu.

    > [!NOTE]
    > `objectCategory` ist ein optionales Feld, das mit API 2.5.0 eingeführt wurde. Damit wird der Aspekt des Visuals definiert, der durch das Objekt gesteuert wird (1 = Formatierung, 2 = Analytics). „Formatierung“ wird für Erscheinungsbild, Farben, Achsen, Beschriftungen usw. und „Analytics“ für Vorhersagen, Trendlinien, Bezugslinien, Formen usw. verwendet.
    >
    > Wenn `objectCategory` nicht festgelegt ist, wird der Standardwert „Formatierung“ verwendet.

2. Das Objekt muss die beiden folgenden Eigenschaften aufweisen:
    1. `show` mit dem Typ „bool“ und dem Standardwert „false“.
    2. `displayName` mit dem Typ „text“. Der von Ihnen ausgewählte Standardwert wird zum ursprünglichen Anzeigenamen der Instanz.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Alle anderen Eigenschaften können auf dieselbe Weise wie für Format-Objekte definiert werden. Die Objektenumeration erfolgt auf exakt die gleiche Weise wie im **Formatbereich**.

***Bekannte Einschränkungen und Probleme***

  1. Bisher gibt es keine Unterstützung für mehrere Instanzen. Objekte können keinen anderen [Selektor](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) als statisch haben (d. h. Selektor: NULL), und benutzerdefinierte Visuals können nicht mehrere benutzerdefinierte Instanzen einer Karte aufweisen.
  2. Eigenschaften des Typs `integer` werden nicht korrekt angezeigt. Verwenden Sie als Problemumgehung den Typ `numeric`.

> [!NOTE]
> Verwenden Sie den Analysebereich nur für Objekte, durch die neue Informationen hinzugefügt bzw. die dargestellten Informationen in einem neuen Blickwickel betrachtet werden. Durch dynamische Bezugslinien werden beispielsweise wichtige Trends veranschaulicht.
> Alle Optionen, die das Erscheinungsbild des Visuals bestimmen (d. h. Formatierungen), sollten im Formatierungsbereich verbleiben.
