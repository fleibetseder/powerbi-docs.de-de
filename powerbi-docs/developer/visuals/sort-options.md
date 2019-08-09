---
title: Sortieren
description: Das standardmäßige Sortierverhalten für das Power BI-Visual
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424514"
---
# <a name="sorting-options"></a>Sortieroptionen

`Sorting` gibt das standardmäßige Sortierverhalten für das Visual an.
Für die Funktion ist einer der unten beschriebenen Parameter erforderlich:

## <a name="default-sorting"></a>Standardsortierung

Die `default`-Option ist die einfachste Form. Sie ermöglicht es, die im DataMappings-Abschnitt dargestellten Daten zu sortieren.
Durch diese Option kann der Benutzer DataMappings sortieren und die Sortierrichtung angeben.

```json
    "sorting": {
        "default": {   }
    }
```

![Sortieroptionen im Kontextmenü](./media/sorting.png)

## <a name="implicit-sorting"></a>Implizite Sortierung

Bei `implicit` wird die Sortierung mit dem `clauses`-Arrayparameter ausgeführt, der die Sortierung für jede Datenrolle beschreibt.
`implicit` bedeutet, dass die Sortierreihenfolge vom Benutzer des Visuals nicht geändert werden kann.
In Power BI werden keine Sortieroptionen im Menü des Visuals angezeigt. Allerdings werden Daten von Power BI gemäß den festgelegten Einstellungen sortiert.

`clauses`-Parameter können mehrere Objekte mit zwei Parametern enthalten:

- `role`: Bestimmt `DataMapping` für die Sortierung.

- `direction`: Bestimmt die Sortierrichtung (1 = aufsteigend, 2 = absteigend).

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Benutzerdefinierte Sortierung

`custom` bedeutet, dass die Sortierung vom Entwickler im Code des Visuals verwaltet wird.
