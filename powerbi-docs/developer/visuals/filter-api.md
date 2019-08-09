---
title: Filter-API für Visuals
description: So können Power BI-Visuals andere Visuals filtern
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425043"
---
# <a name="power-bi-visual-filters-api"></a>Filter-API für Power BI-Visuals

Das Filtervisual ermöglicht das Filtern von Daten. Der Hauptunterschied zu Auswahlen besteht darin, dass andere Visuals in beliebiger Weise gefiltert werden, obwohl für ein anderes Visual supportsHighlight festgelegt wurde.

Um die Filterung des Visuals zu ermöglichen, muss in dessen `general`-Abschnitt von „capabilities.json“ das `filter`-Objekt enthalten sein.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Filter-API-Schnittstellen sind im [`powerbi-models`](https://www.npmjs.com/package/powerbi-models)-Paket verfügbar. Das Paket enthält auch Klassen zum Erstellen von Filterinstanzen.

```cmd
npm install powerbi-models --save
```

Bei Verwendung von Tools mit älteren Versionen (vor 3.x.x) muss `powerbi-models` in das Visualpaket eingefügt werden. [Kurzanleitung zum Einfügen des Pakets](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

Alle Filter erweitern die `IFilter`-Schnittstelle.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target`: ist eine Tabellenspalte in der Datenquelle.

## <a name="basic-filter-api"></a>Allgemeine Filter-API

Im Folgenden die allgemeine Filterschnittstelle:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` ist eine Enumeration mit den Werten „In“, „NotIn“ und „All“.

`values` sind Werte für eine Bedingung.

Beispiel für einen allgemeinen Filter:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Mit dem Filter sollen alle Zeilen zurückgegeben werden, bei denen `col1` dem Wert 1, 2 oder 3 entspricht.

Im Folgenden die Entsprechung in SQL:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Zum Erstellen eines Filters können Sie die BasicFilter-Klasse in `powerbi-models` verwenden.

Wenn Sie Tools mit einer älteren Version verwenden, sollten Sie mit `window['powerbi-models']` im window-Objekt eine models-Instanz abrufen:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Das Visual ruft den Filter mit der applyJsonFilter()-Methode für die IVisualHost-Hostschnittstelle auf, die im Konstruktor des Visuals angegeben ist.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>Erweiterte Filter-API

Die [erweiterte Filter-API](https://github.com/Microsoft/powerbi-models) unterstützt die komplexe Datenpunktauswahl über mehrere Visuals hinweg bzw. die Abfragefilterung auf der Grundlage mehrerer Kriterien (z. B. „LessThan“, „Contains“, „Is“, „IsBlank“ usw.).

Der Filter wurde in der Visuals-API 1.7.0 eingeführt.

Die erweiterte Filter-API erfordert ebenfalls `target` mit dem `table`-Namen und `column`-Namen. Die Operatoren für die erweiterte Filter-API lauten jedoch `"And" | "Or"`. 

Außerdem nutzt der Filter Bedingungen anstelle von Werten für „interface“:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Die Bedingungsoperatoren für den `operator`-Parameter sind `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`.

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

Im Folgenden die Entsprechung in SQL:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Den gesamten Beispielcode für die Verwendung der erweiterten Filter-API finden Sie im [`Sampleslicer visual`-Repository](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>Tupelfilter-API (Filter für mehrere Spalten)

Die Tupelfilter-API wurde in der Visuals-API 2.3.0 eingeführt.

Die Tupelfilter-API ist mit dem allgemeinen Filter vergleichbar, ermöglicht aber die Definition von Bedingungen für mehrere Spalten und Tabellen.

Und ein Filter verfügt über eine Schnittstelle: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` ist ein Array von Spalten mit Tabellennamen:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  Der Filter kann auf Spalten aus unterschiedlichen Tabellen angewendet werden.

`$schema` entspricht „http://powerbi.com/product/schema#tuple“.

`filterType` entspricht `FilterType.Tuple`.

`operator` lässt nur die Verwendung des `"In"`-Operators zu.

`values` ist ein Array von Werttupeln, bei dem jedes Tupel eine zulässige Kombination der Zielspaltenwerte darstellt. 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Vollständiges Beispiel:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**Die Reihenfolge der Spaltennamen und -werte der Bedingung wird berücksichtigt.**

Im Folgenden die Entsprechung in SQL:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>Wiederherstellen eines JSON-Filters aus DataView

Ab API 2.2 können **JSON-Filter** aus **VisualUpdateOptions** wiederhergestellt werden.

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

Wenn der Benutzer zwischen Textmarken wechselt und das Visual das entsprechende `filter`-Objekt erhält, ruft Power BI die `update`-Methode des Visuals auf.
[Weitere Informationen zur Unterstützung von Textmarken](bookmarks-support.md)

### <a name="sample-json-filter"></a>Beispiel für einen JSON-Filter

![Screenshot: JSON-Filter](./media/json-filter.png)

### <a name="clear-json-filter"></a>Löschen eines JSON-Filters

Die Filter-API akzeptiert den Filterwert `null` als Zurücksetzungs- oder Löschbefehl.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
