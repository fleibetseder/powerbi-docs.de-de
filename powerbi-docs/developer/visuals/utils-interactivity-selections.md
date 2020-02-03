---
title: Interaktivitätshilfsprogramme für Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie Auswahlmöglichkeiten in Power BI-Visuals mithilfe von Interaktivitätshilfsprogrammen hinzufügen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818684"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Interaktivitätshilfsprogramme für Microsoft Power BI-Visuals

InteractivityUtils stellt eine Reihe von Funktionen und Klassen dar, die für die Vereinfachung der Implementierung für die übergreifende Auswahl und Kreuzfilterung für benutzerdefinierte Power BI-Visuals zuständig sind.

## <a name="installation"></a>Installation

> [!NOTE]
> Wenn Sie die ältere Version von „powerbi-visuals-tools“ (Versionsnummer kleiner als 3.x.x) weiterhin verwenden, installieren Sie die neue Version der Tools (3.x.x).

> [!IMPORTANT]
> Die neuen Updates der Interaktivitätshilfsprogramme unterstützen nur die neueste Toolversion. [Erfahren Sie mehr zum Aktualisieren des Codes Ihrer Visuals zur Verwendung mit den neuesten Tools.](migrate-to-new-tools.md)

Führen Sie den folgenden Befehl im Verzeichnis mit ihrem aktuellen benutzerdefinierten Visual aus, um das Paket zu installieren.

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Ab Version 3.0 oder später müssen Sie auch ```powerbi-models``` installieren, um Abhängigkeiten aufzulösen.

```bash
npm install powerbi-models --save
```

Wenn Sie Interaktivitätshilfsprogramme verwenden möchten, müssen Sie die erforderliche Komponente in den Quellcode des Visuals importieren.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>Einschließen von CSS-Artefakten in das benutzerdefinierte Visual

Importieren Sie die folgende CSS-Datei in die `your.less`-Datei, um das Paket mit Ihrem benutzerdefinierten Visual zu verwenden:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Dadurch ergibt sich die folgende Dateistruktur:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Importieren Sie die CSS-Datei als LESS-Datei, da Tools für Power BI-Visuals die externen CSS-Regeln umschließen.

## <a name="usage"></a>Verwendung

### <a name="define-interface-for-data-points"></a>Definieren einer Schnittstelle von Datenpunkten

Normalerweise enthalten Datenpunkte Auswahlmöglichkeiten und Werte. Die Schnittstelle erweitert die `SelectableDataPoint`-Schnittstelle. `SelectableDataPoint` enthält bereits Eigenschaften:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

Der erste Schritt beim Verwenden von Interaktivitätshilfsprogrammen ist das Erstellen einer Instanz von Interaktivitätshilfsprogrammen und anschließend das Speichern eines Objekts als Eigenschaft des Visuals.

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

Der zweite Schritt ist das Erweitern der grundlegenden Verhaltensklasse:

> [!NOTE]
> Die BaseBehavior-Klasse wurde in [Version 5.6.x der Interaktivitätshilfsprogramme](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) eingeführt. Wenn Sie die ältere Version verwenden, erstellen Sie die Verhaltensklasse wie im Beispiel unten (die `BaseBehavior`-Klasse ist gleich):

Definieren Sie die Schnittstelle für Optionen der Verhaltensklasse:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Definieren Sie eine Klasse für `visual behavior`. Die Klasse ist dafür verantwortlich, die Mausereignisse `click` und `contextmenu` zu verarbeiten.
Wenn ein Benutzer auf Datenelemente im Visual klickt, wird daraufhin der Auswahlhandler zum Auswählen von Datenpunkten aufgerufen. Wenn der Benutzer auf das Hintergrundelement des Visuals klickt, wird der Handler zum Löschen der Auswahl aufgerufen. Die Klasse verfügt über die folgenden Methoden: `bindClick`, `bindClearCatcher` und `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

Alternativ können Sie die `BaseBehavior`-Klasse erweitern:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Um Klicks auf Elemente zu verarbeiten, rufen Sie die `on`-Methode eines D3-Auswahlobjekts auf (ebenfalls für elementsSelection und clearCatcherSelection):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Fügen Sie ähnliche Handler für das `contextmenu`-Ereignis zum Aufruf der `showContextMenu`-Methode des Auswahl-Managers hinzu:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

Die Interaktivitätshilfsprogramme rufen die `bindEvents`-Methoden auf, um Handlern Funktionen zuzuweisen, und fügen Aufrufe von `bindClick`, `bindClearCatcher` und `bindContextMenu` zur Methode `bindEvents` hinzu:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

Die `renderSelection`-Methode wird zum Aktualisieren des Status von Visuals von Elementen im Diagramm verwendet.

Beispiel für die `renderSelection`-Implementierungsmethode:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

Mit dem letzten Schritt wird eine `visual behavior`-Instanz erstellt und die `bind`-Methode der Instanz von Interaktivitätshilfsprogrammen aufgerufen:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` ist das D3-Auswahlobjekt, das alle auswählbaren Elemente im Visual darstellt.

* `select(this.target)` ist das D3-Auswahlobjekt, das die wichtigsten DOM-Elemente im Visual darstellt.

* `this.categories` sind Datenpunkte mit Elementen, wobei die Schnittstelle `VisualDataPoint` (oder `categories: VisualDataPoint[];`) ist.

* `this.behavior` ist eine neue Instanz von `visual behavior`.

  Folgendes wird im Konstruktor des Visuals erstellt:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Nun kann das Visual die Auswahl verarbeiten.

## <a name="next-steps"></a>Nächste Schritte

* [Verarbeiten von Auswahlmöglichkeiten bei wechselnden Lesezeichen](bookmarks-support.md#visuals-with-selection)

* [Hinzufügen des Kontextmenüs für Datenpunkte von Visuals](context-menu.md)

* [Verwenden des Auswahl-Managers zum Hinzufügen von Auswahlmöglichkeiten für Power BI-Visuals](selection-api.md).
