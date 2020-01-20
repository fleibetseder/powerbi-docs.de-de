---
title: Migrieren zu Version 3.x von powerbi-visuals-tools
description: Erste Schritte mit der neuen Version von powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1b819aeb0f59df9ee0d48d7c41807abe62efed08
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885129"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrieren zur neuen Version 3.*x* von powerbi-visuals-tools

Ab Version 3 verwenden die Power BI-Visualtools (powerbi-visuals-tools oder `pbiviz`) zum Erstellen von benutzerdefinierten Visuals Webpack.
Die neue Version enthält zahlreiche Verbesserungen für Entwickler bei der Erstellung von Visuals:

- TypeScript 3.*x* wird standardmäßig verwendet. Ab TypeScript 1.5 werden neue Bezeichnungen verwendet. [Erfahren Sie mehr über die TypeScript-Module](https://www.typescriptlang.org/docs/handbook/modules.html).

- ES6-Module (ECMAScript 6) werden unterstützt. Verwenden Sie jetzt ES6-Importe anstelle von [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Neue Versionen von [D3v5](https://d3js.org/) (datengesteuerte Dokumente) und andere auf ES6-Modulen basierende Bibliotheken werden unterstützt.

- Kleinere Paketgröße. Webpack verwendet das sogenannte [Tree Shaking](https://webpack.js.org/guides/tree-shaking/), um nicht verwendeten Code zu entfernen. Dadurch wird JavaScript-Code reduziert und die Leistung beim Laden von Visuals verbessert.

- Verbesserte API-Leistung.

- Die Bibliothek „globalize.js“ wurde in „FormattingUtils“ [integriert](migrate-to-new-tools.md#remove-the- globalizejs-library).

- Die Power BI-Visualtools verwenden [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer), um die Codebasis des Visuals anzuzeigen.

In diesem Artikel werden alle Migrationsschritte für die neue Version der Power BI-Visualtools beschrieben.

## <a name="backward-compatibility"></a>Abwärtskompatibilität

Die neuen Tools speichern Informationen zur Abwärtskompatibilität mit der alten Visualcodebasis. Es sind jedoch möglicherweise einige zusätzliche Änderungen erforderlich, um externe Bibliotheken zu laden.

Bibliotheken, die Modulsysteme unterstützen, werden als Webpack-Module importiert. Alle anderen Bibliotheken und der Quellcode des Visuals werden in einem Modul zusammengefasst.

In früheren Versionen der Power BI-Visualtools verwendete globale Variablen wie JQuery und Lodash sind jetzt veraltet. Visuals, deren Code auf globalen Variablen basiert, funktionieren mit den neuen Tools wahrscheinlich nicht mehr.

In der Vorgängerversion der Power BI-Visualtools musste im `powerbi.extensibility.visual`-Modul eine Visualklasse definiert werden. In der neuen Version der Tools muss stattdessen in der TypeScript-Hauptdatei (.ts) eine Visualklasse definiert werden. Diese Datei heißt in der Regel `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Installieren von powerbi-visuals-tools

Führen Sie den folgenden Befehl aus, um die neuen Tools zu installieren:

```cmd
npm install -g powerbi-visuals-tools
```

Der folgende Code stammt aus der Datei `package.json` im Visualrepository [sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), nachdem das Visualprojekt auf die neuen Tools aktualisiert wurde:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Installieren der API für benutzerdefinierte Power BI-Visuals

Die neue Version von powerbi-visual-tools enthält nicht alle API-Versionen. Sie müssen daher eine bestimmte Version des [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api)-Pakets installieren. Wählen Sie die Paketversion aus, die mit der API-Version Ihrer benutzerdefinierten Power BI-Visuals übereinstimmt. Das Paket stellt alle Typdefinitionen für die API für benutzerdefinierte Power BI-Visuals bereit.

Fügen Sie den Projektabhängigkeiten eines Projekts `powerbi-visuals-api` hinzu, indem Sie den folgenden Befehl ausführen:

```cmd
npm install --save-dev powerbi-visuals-api
```

Entfernen Sie außerdem alle Links zu alten API-Typdefinitionen, da Webpack automatisch Typen von `powerbi-visuals-api` enthält. Die entsprechenden Änderungen befinden sich in den Dateien [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) und [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Aktualisieren der Datei „tsconfig.json“

Ändern Sie die Option `out` in `outDir`, um externe Module zu verwenden. Verwenden Sie beispielsweise `"outDir": "./.tmp/build/",` anstelle von `"out": "./.tmp/build/visual.js",`.

Diese Änderung ist erforderlich, weil TypeScript-Dateien unabhängig voneinander in JavaScript-Dateien kompiliert werden. Daher müssen Sie nicht länger die Datei „visual.js“ als Ausgabe angeben.

Sie können zudem die Option `target` in `ES6` ändern, wenn Sie modernes JavaScript als Ausgabe verwenden möchten. Diese Änderung ist [optional](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Aktualisieren von Hilfsprogrammen für benutzerdefinierte Visuals

Wenn Sie [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils)-Pakete verwenden, aktualisieren Sie diese ebenfalls auf die neueste Version. Führen Sie hierzu den folgenden Befehl aus:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Führen Sie beispielsweise den folgenden Befehl aus, um die neue Version mit externen Modulen von TypeScript abzurufen: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Ein Beispiel für ein Visual, das alle `powerbi-visuals-utils`-Pakete verwendet, finden Sie im [MekkoChart-Repository](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Entfernen der Bibliothek „globalize.js“

Die neue Version von [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) enthält „globalize.js“. Daher müssen Sie diese Bibliothek Ihrem Projekt nicht manuell hinzufügen. Alle erforderlichen Lokalisierungen werden dem endgültigen Paket automatisch hinzugefügt.

## <a name="configure-loading-of-external-libraries"></a>Konfigurieren des Ladevorgangs externer Bibliotheken

Fügen Sie neue JavaScript-Dateien nach den Bibliotheken in das `externalJS`-Array von `pbiviz.json` ein. Beispiel:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importieren Sie die Bibliotheken in Ihren Quellcode. Verwenden Sie beispielsweise für `lodash-es` folgende Anweisung:

```JS
import * as _ from "lodash-es";
```

Im vorherigen Beispiel stellt `_` die globale Variable für die `lodash`-Bibliothek dar.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Vornehmen von Änderungen in den Quellen der Visuals

Die wichtigste Änderung, die Sie vornehmen müssen, ist das Konvertieren interner Module in externe Module. Externe Module können in internen Modulen nicht verwendet werden.

Im Folgenden finden Sie eine ausführliche Beschreibung der Änderungen, die Sie vornehmen müssen. Diese werden im Kontext des Codebeispiels für das benutzerdefinierte Balkendiagramm beschrieben:

1. Entfernen Sie alle Moduldefinitionen aus allen [Quellcodedateien](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importieren Sie die API-Definitionen für benutzerdefinierte Power BI-Visuals](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importieren Sie erforderliche Schnittstellen oder Klassen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) aus dem internen `powerbi`-Modul:

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importieren Sie die Bibliothek „D3.js“](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Sie können auch nur die erforderlichen D3-Bibliotheksmodule importieren:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importieren Sie die im Visualprojekt definierten Hilfsprogramme, Klassen und Schnittstellen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) in die Hauptquelldatei:

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importieren von CSS-Stilen

Mit der neuen Toolversion können Sie `CSS`- und `Less`-Stile direkt in den TypeScript-Code importieren. Der bisher verwendete [Stilabschnitt](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) wird nun vom Compiler ignoriert.

Öffnen Sie zur Verwendung Ihres Stylesheets die TypeScript-Hauptdatei (.ts), und fügen Sie die folgende Zeile hinzu:  

```typescript
import "./../style/visual.less";
```  

Ihre `CSS`- und `Less`-Stile werden automatisch kompiliert.

### <a name="externaljs-section-in-pbivizjson"></a>externalJS-Abschnitt in „pbiviz.json“

Eine [Liste von `externalJS`-Bibliotheken](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20), die in das Visualbundle geladen werden sollen, ist für die Tools nicht erforderlich, da Webpack alle importierten Bibliotheken enthält.

> [!NOTE]
> Lassen Sie in `pbiviz.json` den Abschnitt `externalJS` leer.

Verwenden Sie den typischen Befehl `npm run package` zum Erstellen des Visualpakets oder `npm run start` zum Starten des Entwicklungsservers.

## <a name="update-the-d3js-library-to-version-5"></a>Aktualisieren der Bibliothek „D3.js“ auf Version 5

Mit den neuen Visualtools können Sie nun die neue Version der Bibliothek „D3.js“ verwenden. Führen Sie die folgenden Befehle aus, um D3 in Ihrem Visualprojekt zu aktualisieren:

- `npm install --save d3@5` zum Installieren der neuen D3.js-Bibliothek

- `npm install --save-dev @types/d3@5` zum Installieren der neuen Typdefinitionen für die D3.js-Bibliothek

> [!IMPORTANT]
> In Version 5 von D3 werden einige wichtige Änderungen eingeführt.

Ändern Sie den Code, damit er mit der neuen D3-Version funktioniert:

- Die Schnittstelle `d3.Selection<T>` [wurde geändert](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Es ist nicht möglich, mehrere Attribute durch einen einzigen Aufruf der `attr`-Methode zu verwenden. Stattdessen müssen Sie [jedes Attribut in einem separaten Aufruf](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) an `attr`übergeben. [Rufen Sie auch die `style`-Methode separat auf](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- In Version 4 von „D3.js“ wurde die neue `merge`-Methode eingeführt. Diese Methode wird üblicherweise verwendet, um die Auswahl für `enter` und `update` nach einem JOIN-Vorgang zusammenzuführen. [Rufen Sie die `merge`-Methode](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) auf, um D3 ordnungsgemäß zu verwenden.

Informationen zu Änderungen in der Bibliothek „D3.js“ finden Sie [hier](https://github.com/d3/d3/blob/master/CHANGES.md).

## <a name="install-babel-and-core-js"></a>Installieren von Babel und „core-js“

Ab Version 3.1 verwenden die Visualtools Babel, um modernen JavaScript-Code in herkömmlichen ES5-Code (ECMAScript 5) zu kompilieren und so eine Vielzahl von Browsern zu unterstützen.

Die Option Babel ist standardmäßig aktiviert, doch Sie müssen das [`core-js`](https://www.npmjs.com/package/core-js)-Paket manuell importieren. Führen Sie den folgenden Befehl aus, um das Paket zu installieren:

```cmd
npm install --save core-js
```

Importieren Sie anschließend das Paket an den Startpunkt des Visualcodes. Dabei handelt es sich in der Regel um die Datei „src/visual.ts“.

```JS
import "core-js/stable";
```

Weitere Informationen zu Babel finden Sie in der [Dokumentation](https://babeljs.io/docs/en/).
