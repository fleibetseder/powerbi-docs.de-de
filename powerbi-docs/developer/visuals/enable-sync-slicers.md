---
title: Synchronisierung von Slicern
description: Hinzufügen der Funktion „Slicer synchronisieren“ für Power BI-Visuals
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425020"
---
# <a name="sync-slicers"></a>Slicer synchronisieren

Zur Unterstützung von [Slicer synchronisieren](https://docs.microsoft.com/power-bi/desktop-slicers) muss für das benutzerdefinierte Slicervisual API 1.13 oder höher verwendet werden.

Die zweite wichtige Voraussetzung besteht darin, dass die Option in `capabilities.json` aktiviert sein muss (siehe Beispiel unten).

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Nachdem Sie die Änderungen in `capabilities.json` vorgenommen haben, wird der Bereich „Slicer synchronisieren“ mit Optionen eingeblendet, wenn Sie auf das benutzerdefinierte Slicervisual klicken.

> [!NOTE]
> Wenn der Slicer mehr als ein Feld (Kategorie oder Measure) aufweist, wird die Funktion deaktiviert, da mehrere Felder von „Slicer synchronisieren“ nicht unterstützt werden.

![Bereich „Slicer synchronisieren“](./media/sync-slicers-panel.png)

Im Bereich sehen Sie, dass die Sichtbarkeit und Filterung des Slicers auf mehrere Berichtsseiten angewendet werden können.
