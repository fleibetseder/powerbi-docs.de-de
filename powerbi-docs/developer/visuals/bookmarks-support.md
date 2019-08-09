---
title: Lesezeichen
description: Power BI-Visuals unterstützt das Wechseln des Lesezeichenstatus.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425503"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Hinzufügen von Lesezeichenunterstützung für Power BI-Visuals

Über Lesezeichen in Power BI-Berichten lassen sich konfigurierte Ansichten einer Berichtsseite sowie der Auswahl- und Filterzustand des Visuals erfassen. Allerdings sind zusätzliche Aktionen vonseiten benutzerdefinierter Visuals nötig, damit Lesezeichen unterstützt werden und angemessen auf Änderungen reagiert werden kann.

Weitere Informationen zu Lesezeichen erhalten Sie in dieser [Dokumentation](https://docs.microsoft.com/power-bi/desktop-bookmarks).

## <a name="report-bookmarks-support-in-your-visual"></a>Unterstützung von Berichtslesezeichen in Visuals

Wenn Ihr Visual mit anderen Visuals interagiert, Datenpunkte auswählt oder andere Visuals filtert, müssen Sie den Zustand mithilfe der Eigenschaften wiederherstellen.

## <a name="how-to-add-report-bookmarks-support"></a>Hinzufügen von Unterstützung für Berichtslesezeichen

1. Installieren (oder aktualisieren) Sie das erforderliche Hilfsprogramm: `powerbi-visuals-utils-interactivityutils`: https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) (Version 3.0.0 oder höher). Es enthält zusätzliche Klassen für die Bearbeitung der Zustands- oder Filterauswahl. Das Hilfsprogramm wird zudem für filterbezogene Visuals und alle Visuals vorausgesetzt, die `InteractivityService` verwenden.

2. Aktualisieren Sie die Visual-API auf 1.11.0, um `registerOnSelectCallback` in der Instanz von `SelectionManager` zu verwenden. Das Hilfsprogramm wird für nicht filterbezogene Visuals vorausgesetzt, die den normalen `SelectionManager` anstelle von `InteractivityService` verwenden.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Interaktion zwischen benutzerdefinierten Visuals und Power BI im Berichtslesezeichen-Szenario

Sehen wir uns nun das folgende Beispiel an: Ein Benutzer legt mehrere Lesezeichen auf der Berichtsseite an, die jeweils einen anderen Auswahlzustand aufweisen.

Zuerst wählt der Benutzer einen Datenpunkt im Visual aus. Das Visual interagiert mit Power BI und anderen Visuals, indem es die Auswahl an den Host übergibt. Anschließend wählt der Benutzer „Hinzufügen“ in `Bookmark panel` aus, woraufhin Power BI die aktuelle Auswahl für das neue Lesezeichen speichert.

Dieser Vorgang wird wiederholt, wenn der Benutzer die Auswahl verändert und neue Lesezeichen hinzufügt.
Nach der Erstellung kann der Benutzer zwischen den Lesezeichen wechseln.

Wenn Benutzer ein Lesezeichen auswählen, stellt Power BI den gespeicherten Filter- oder Auswahlzustand wieder her und übergibt ihn an die Visuals. Andere Visuals werden hervorgehoben oder gemäß dem Zustand gefiltert, der im Lesezeichen gespeichert ist. Der Power BI-Host führt die erforderlichen Aktionen aus. Das Visual hat die Aufgabe, den neuen Auswahlzustand (z. B. Farbänderung der gerenderten Datenpunkte) korrekt wiederzugeben.

Der neue Auswahlzustand wird dem Visual über die `update`-Methode mitgeteilt. Das `options`-Argument enthält die besondere Eigenschaft `options.jsonFilters`. Die JSONFilter-Eigenschaft kann `Advanced Filter` und `Tuple Filter` enthalten.

Das Visual muss Filterwerte wiederherstellen, um den entsprechenden Zustand des Visuals für das ausgewählte Lesezeichen anzuzeigen.

Alternativ können Sie die vom Aufruf der Rückruffunktion registrierte `registerOnSelectCallback`-Methode namens ISelectionManager verwenden, wenn das Visual nur die Auswahl verwendet.

### <a name="visuals-with-selections"></a>Visuals mit einer Auswahl

Wenn Ihre Visuals über die [Auswahl](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) mit anderen Visuals interagieren, können Sie Lesezeichen auf zwei Weisen hinzufügen.

* Sie können die `FilterManager.restoreSelectionIds`-Methode verwenden, falls Sie zuvor noch **kein [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** -Element im Visual verwendet haben.

* Wenn Ihr Visual bereits **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** verwendet, um die Auswahl zu verwalten, müssen Sie die `applySelectionFromFilter`-Methode in einer Instanz von `InteractivityService` verwenden.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>Verwenden von `ISelectionManager.registerOnSelectCallback`

Wenn ein Benutzer auf ein Lesezeichen klickt, ruft Power BI die `callback`-Methode des Visuals mit der entsprechenden Auswahl auf. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Angenommen, das mit der [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74)-Methode erstellte Visual verfügt über einen Datenpunkt.

Dabei sieht `datapoints` wie folgt aus:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

In diesem Fall steht `visualDataPoints` für Ihre Datenpunkte, und das `ids`-Array wird an die `callback`-Funktion übergeben.

An diesem Punkt sollte das Visual das `ISelectionId[]`-Array mit der Auswahl im `visualDataPoints`-Array vergleichen und die entsprechenden Datenpunkte als ausgewählt markieren.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Nach dem Aktualisieren der Datenpunkte wird der aktuelle Auswahlzustand angezeigt, der im `filter`-Objekt gespeichert ist. Wenn die Datenpunkte anschließend gerendert werden, entspricht der Auswahlzustand des benutzerdefinierten Visuals dem Zustand des Lesezeichens.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>Verwenden von `InteractivityService` zur Steuerelementauswahl im Visual

Wenn Ihr Visual `InteractivityService` verwendet, sind keine Aktionen erforderlich, um Lesezeichen in Visuals zu unterstützen.

Der Auswahlzustand des Visuals wird durch das Hilfsprogramm verarbeitet, wenn der Benutzer Lesezeichen auswählt.

### <a name="visuals-with-filter"></a>Visuals mit Filter

Nehmen wir an, dass vom Visual ein Datenfilter nach Datumsbereich erstellt wird. Somit verfügen wir über `startDate` und `endDate` als Start- bzw. Enddatum des Bereichs.
Durch das Visual wird ein erweiterter Filter erstellt und die Hostmethode `applyJsonFilter` aufgerufen, um Daten nach relevanten Bedingungen zu filtern.
`target` ist die Tabelle, die gefiltert wird.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Sobald ein Benutzer auf ein Lesezeichen klickt, empfängt das benutzerdefinierte Visual einen `update`-Aufruf.

Der Objektfilter muss vom benutzerdefinierten Visual überprüft werden:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Wenn das `filter`-Objekt nicht NULL ist, muss das Visual Filterbedingungen vom Objekt wiederherstellen:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Anschließend muss der interne Zustand des Visuals wie Datenpunkte und Visualisierungsobjekte (Linien, Rechtecke usw.) geändert werden, um die aktuellen Bedingungen widerzuspiegeln.

> [!IMPORTANT]
> Im Berichtslesezeichen-Szenario muss `applyJsonFilter` vom Visual nicht aufgerufen werden, um weitere Visuals zu filtern. Dies wird bereits von Power BI erledigt.

Durch das Zeitachsenslicer-Visual wird die Bereichsauswahl gemäß den Datenbereichen geändert.

Weitere Informationen finden Sie im [Zeitachsenslicer-Repository](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df).

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Filterzustand zum Speichern von Visualeigenschaften in Lesezeichen

Durch die `filterState`-Eigenschaft wird eine Eigenschaft zum Bestandteil der Filterung. Das Visual ist in der Lage, verschiedene Werte in Lesezeichen zu speichern.

Um den Eigenschaftswert als Filterzustand zu speichern, muss die Objekteigenschaft in `capabilities.json` als `"filterState": true` gekennzeichnet werden.

Beispiel: Durch `Timeline Slicer` werden `Granularity`-Eigenschaftswerte im Filter gespeichert. Außerdem kann dadurch die aktuelle Granularität geändert werden, sobald ein Benutzer ein Lesezeichen ändert.

Weitere Informationen finden Sie im [Zeitachsenslicer-Repository](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334);
