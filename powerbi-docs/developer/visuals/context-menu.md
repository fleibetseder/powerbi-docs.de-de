---
title: Funktionen und Eigenschaften von Power BI-Visuals
description: In diesem Artikel werden die Funktionen und Eigenschaften von Power BI-Visuals beschrieben.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819190"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Hinzufügen eines Kontextmenüs zu einem Power BI-Visual

Sie können `selectionManager.showContextMenu()` mit `selectionId`-Parametern und einer Position (`{x:, y:}`-Objekt) verwenden, damit Power BI ein Kontextmenü für Ihr Visual anzeigt.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` wurde mit der Visuals-API 2.2.0 eingeführt.

Kontextmenüs werden in der Regel als Rechtsklickereignis (oder Ereignis für langes Drücken bei Touch-Geräten). Im folgenden BarChart-Beispiel wurde ein Kontextmenü hinzugefügt:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
