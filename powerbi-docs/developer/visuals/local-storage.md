---
title: API für lokalen Speicher in Power BI-Visuals
description: In diesem Artikel wird beschrieben, wie Sie die Power BI-Visuals-API verwenden, um Zugriff auf den lokalen Browserspeicher zu erhalten.
author: uve
ms.author: v-grniki
ms.reviewer: KesemSharabi
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 85517fcd7ec773f947135614c94c0c4e4638ea48
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539323"
---
# <a name="local-storage-api"></a>API für lokalen Speicher

Die API für lokalen Speicher ist eine API, die ein Visual nutzen kann, um beim Host das Speichern oder Laden von Daten aus dem Gerätespeicher anzufordern. Sie ist dahingehend isoliert, dass der Speicherzugriff zwischen verschiedenen Visualtypen getrennt wird.

## <a name="sample"></a>Beispiel

Wenn das benutzerdefinierte Visual bei jedem Aufruf der Aktualisierungsmethode einen Zähler erhöhen soll, der Zählerwert aber gleichzeitig beibehalten und nicht bei jedem Visualstart zurückgesetzt werden soll:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Bekannte Einschränkungen und Probleme

Die API für lokalen Speicher ist standardmäßig nicht für benutzerdefinierte Visuals aktiviert. Wenn Sie die API für Ihr benutzerdefiniertes Visual aktivieren möchten, senden Sie eine Anfrage an das Supportteam für benutzerdefinierte Power BI-Visuals: `pbicvsupport@microsoft.com`.  
**Bitte beachten Sie, dass Ihr Visual in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) verfügbar und [zertifiziert](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/) sein sollte.**
