---
title: Rendern von Ereignissen
description: Power BI kann von Power BI-Visuals benachrichtigt werden, dass sie für den Export in PowerPoint/eine PDF-Datei bereit sind.
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425089"
---
# <a name="event-service"></a>Ereignisdienst

Die neue API umfasst drei Methoden („started“, „finished“ oder „failed“), die während des Renderings aufgerufen werden müssen.

Beim Start des Renderings wird vom Code des benutzerdefinierten Visuals die renderingStarted-Methode aufgerufen, um anzugeben, dass der Renderingvorgang gestartet wurde.

Wenn das Rendering erfolgreich abgeschlossen wurde, wird im Code des benutzerdefinierten Visuals sofort die `renderingFinished`-Methode aufgerufen, um die Listener (hauptsächlich für **„In PDF exportieren“ und „Nach PowerPoint exportieren“** ) zu benachrichtigen, dass das Image des Visuals bereit ist.

Ein Problem während des Renderingvorgangs kann verhindern, das dass benutzerdefinierte Visual erfolgreich abgeschlossen wird. Im Code des benutzerdefinierten Visuals muss die `renderingFailed`-Methode aufgerufen werden, durch die der Listener benachrichtigt wird, dass der Renderingvorgang noch nicht abgeschlossen wurde. Diese Methode stellt zusätzlich eine optionale Zeichenfolge zur Erläuterung der Fehlerursache bereit.

## <a name="usage"></a>Syntax

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Einfaches Beispiel: Das Visual weist beim Rendern keine Animationen auf.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-with-animation"></a>Beispiel: Das Visual weist Animationen auf.

Wenn das Visual Animationen oder asynchrone Funktionen für das Rendering aufweist, muss nach der Animation oder innerhalb der asynchronen Funktion die `renderingFinished`-Methode aufgerufen werden.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Rendern von Ereignissen für die Zertifizierung von Visuals

Eine Anforderung für die Zertifizierung von Visuals besteht darin, dass das Visual das Rendern von Ereignissen unterstützen muss. Weitere Informationen zu [Zertifizierungsanforderungen](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
