---
title: Objekt und Eigenschaften
description: Anpassbare Eigenschaften von Power BI-Visuals
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424606"
---
# <a name="object-and-properties"></a>Objekt und Eigenschaften

Objekte beschreiben anpassbare Eigenschaften, die dem Visual zugeordnet sind.
Jedes Objekt kann über mehrere Eigenschaften verfügen, und jeder Eigenschaft ist ein Typ zugeordnet.
Mit Typen wird die Eigenschaft näher bestimmt. Weitere Informationen zu Typen finden Sie unten.

`myCustomObject` ist der interne Name, mit dem auf das Objekt in `dataView` und `enumerateObjectInstances` verwiesen wird.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Anzeigename

`displayName` ist der Name, der im Eigenschaftenbereich angezeigt wird.

## <a name="properties"></a>Eigenschaften

`properties` ist eine Zuordnung von Eigenschaften, die vom Entwickler definiert wurden.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` ist eine spezielle Eigenschaft, die einen Schalter zum Ein-/Ausschalten des Objekts aktiviert.

Beispiel:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Eigenschaftentypen

Es gibt zwei Arten von Eigenschaftentypen: `ValueTypeDescriptor` und `StructuralTypeDescriptor`

#### <a name="value-type-descriptor"></a>ValueTypeDescriptor

`ValueTypeDescriptor` ist meist ein primitiver Typ, der normalerweise als statisches Objekt verwendet wird.
Im Folgenden einige allgemeine `ValueTypeDescriptor`s

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>StructuralTypeDescriptor

`StructuralTypeDescriptor` wird größtenteils für datengebundene Objekte verwendet.
Der häufigste allgemeine `StructuralTypeDescriptor` ist „Fill“.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Gradient-Eigenschaft

Die Gradient-Eigenschaft kann nicht als Standardeigenschaft festgelegt werden. Stattdessen müssen Sie eine Regel für die Ersetzung der Farbauswahleigenschaft (Fülltyp) festlegen.
Betrachten Sie folgendes Beispiel:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Beachten Sie die `"fill"`-Eigenschaft und die `"fillRule"`-Eigenschaft. Die erste entspricht der Farbauswahl und die zweite der Ersetzungsregel für den Farbverlauf, der die Fill-Eigenschaft `visually` ersetzt, wenn die Bedingungen der Regel erfüllt werden.

Die Verknüpfung zwischen der Fill-Eigenschaft und der Ersetzungsregel wird im Abschnitt `"rule"`->`"output"` der `"fillRule"`-Eigenschaft festgelegt.

`"Rule"`->`"InputRole"` legt fest, durch welche Datenrolle die Regel (Bedingung) ausgelöst wird. Wenn in diesem Beispiel die `"Gradient"`-Datenrolle die Daten enthält, wird die Regel auf die `"fill"`-Eigenschaft angewendet.

Im Folgenden sehen Sie ein Beispiel für die Datenrolle, die die Füllregel auslöst (`the last item`).

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>`enumerateObjectInstances`-Methode

Um Objekte effizient zu verwenden, benötigen Sie in Ihrem benutzerdefinierten Visual eine Funktion namens `enumerateObjectInstances`. Diese Funktion füllt den Eigenschaftenbereich mit Objekten auf und bestimmt auch, wo Objekte in dataView gebunden werden sollen.  

Ein typisches Beispiel sieht folgendermaßen aus:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Eigenschaften

Die Eigenschaften in `enumerateObjectInstances` entsprechen den in Ihren Funktionen definierten Eigenschaften. Ein Beispiel finden Sie unten auf der Seite.

### <a name="objects-selector"></a>Objektselektor

Der Selektor in `enumerateObjectInstances` bestimmt, wo die einzelnen Objekte in dataView gebunden werden. Es gibt vier verschiedene Optionen.

#### <a name="static"></a>static

Dieses Objekt wird an Metadaten gebunden: `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>columns

Dieses Objekt wird an Spalten mit entsprechendem `QueryName` gebunden.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Dieses Objekt wird an das Element gebunden, für das wir `selectionID` erstellt haben. In diesem Beispiel gehen wir davon aus, dass wir `selectionID`s für einige dataPoints erstellt haben und diese durchlaufen.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>ScopeIdentity

Dieses Objekt wird am Schnittpunkt von Gruppen an bestimmte Werte gebunden. Beispiel: Ich verfüge über die Kategorien `["Jan", "Feb", "March", ...]` und die Reihe `["Small", "Medium", "Large"]` und möchte an den Schnittpunkt von Werten, die `Large` und `Feb` entsprechen, ein Objekt binden. Dazu könnte ich für beide Spalten `DataViewScopeIdentity` abrufen, in die `identities`-Variable einfügen und für „selector“ die folgende Syntax verwenden.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht eine objectEnumeration für ein customColor-Objekt mit einer `fill`-Eigenschaft. Wir möchten dieses Objekt statisch an `dataViews[index].metadata.objects` binden.

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
