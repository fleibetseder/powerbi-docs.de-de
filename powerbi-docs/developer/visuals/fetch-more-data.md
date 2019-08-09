---
title: Abrufen zusätzlicher Daten
description: Aktivieren des segmentierten Abrufens großer Datasets für Power BI-Visuals
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425066"
---
# <a name="fetch-more-data-from-power-bi"></a>Abrufen größerer Datenmengen von Power BI

Sie können größere Datenmengen laden, indem Sie das harte API-Limit von 30.000 Datenpunkten umgehen. Daten werden in Blöcken geladen. Die Blockgröße und kann entsprechend dem jeweiligen Anwendungsfall konfiguriert werden, um die Leistung zu verbessern.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Aktivieren des segmentierten Abrufens großer Datasets

Definieren Sie für die erforderliche dataViewMapping für den `dataview`-Segmentmodus in „`capabilities.json`“ des Visuals ein dataReductionAlgorithm-Fenster („window“).
Die Fenstergröße wird durch `count` bestimmt. Dadurch wird die Anzahl neuer Datenzeilen begrenzt, die bei jeder Aktualisierung an `dataview` angefügt werden.

Folgendes muss in „capabilities.json“ hinzugefügt werden:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Neue Segmente werden an die vorhandene `dataview` angefügt und dem Visual als `update`-Aufruf zur Verfügung gestellt.

## <a name="usage-in-the-custom-visual"></a>Verwendung im benutzerdefinierten Visual

Wenn Daten vorhanden sind, ist gleichzeitig `dataView.metadata.segment` vorhanden. Ansonsten nicht:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Durch die Überprüfung von `options.operationKind` können Sie auch feststellen, ob es sich um die erste oder eine nachfolgende Aktualisierung handelt.

`VisualDataChangeOperationKind.Create` entspricht dem ersten Segment und `VisualDataChangeOperationKind.Append` nachfolgenden Segmenten.

Eine Beispielimplementierung finden Sie im folgenden Codeausschnitt:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

Die `fetchMoreData`-Methode kann auch über einen UI-Ereignishandler aufgerufen werden.

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI ruft die `update`-Methode des Visuals mit einem neuen Datensegment in Reaktion auf den `this.host.fetchMoreData`-Methodenaufruf auf.

> [!NOTE]
> In Power BI ist die insgesamt abrufbare Datenmenge derzeit auf **100 MB** begrenzt, um Speichereinschränkungen auf dem Client zu vermeiden. Dass dieses Limit erreicht wurde, erkennen Sie daran, dass fetchMoreData() „false“ zurückgibt.*
