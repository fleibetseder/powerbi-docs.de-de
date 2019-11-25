---
title: Funktionen und Eigenschaften von Power BI-Visuals
description: In diesem Artikel werden die Funktionen und Eigenschaften von Power BI-Visuals beschrieben.
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061774"
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
