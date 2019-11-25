---
title: Migration zu powerbi-visuals-tools 3.x
description: Erste Schritte mit der neuen Version von powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061820"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migrieren zum neuen powerbi-visuals-tools 3.x.x

Ab Version 3 verwenden die Power BI-Visualtools zum Erstellen benutzerdefinierter Visuals Webpack.
Die neue Version bietet Entwicklern neue Möglichkeiten für die Erstellung von Visuals:

* TypeScript v3.x.x als Standardeinstellung. Ab TypeScript 1.5 wurde die Nomenklatur geändert. [Erfahren Sie mehr über die TypeScript-Module](https://www.typescriptlang.org/docs/handbook/modules.html).

* Unterstützung für ES6-Module. Die Verwendung von [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries) ist nicht mehr erforderlich, verwenden Sie stattdessen ES6-Importe.

* Neue Versionen von [D3v5](https://d3js.org/) und andere ES6-modulbasierte Bibliotheken werden unterstützt.

* Kleinere Paketgröße. Webpack nutzt das [Tree Shaking](https://webpack.js.org/guides/tree-shaking/), um nicht verwendeten Code zu entfernen. Es reduziert den JS-Code und sorgt so für eine bessere Leistung beim Laden von Visuals.

* Verbesserte API-Leistung.

* Die Bibliothek „globalize.js“ wurde in „formatting-utils“ [integriert](migrate-to-new-tools.md#remove-globalizejs-library).

* Die Tools verwenden [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer), um die Codebasis des Visuals anzuzeigen.

Alle Migrationsschritte für die neue Version der Power BI-Visualtools werden unten beschrieben.

## <a name="backward-compatibility"></a>Abwärtskompatibilität

Die neuen Tools bieten Abwärtskompatibilität mit der alten Visualcodebasis, möglicherweise sind aber einige zusätzliche Änderungen erforderlich, um externe Bibliotheken zu laden.

Bibliotheken, die Modulsysteme unterstützen, werden als Webpack-Module importiert. Alle anderen Bibliotheken und Visualquellcode werden in einem Modul zusammengefasst.

In früheren Versionen der Power BI-Visualtools verwendete globale Variablen wie JQuery und Lodash sind jetzt veraltet. Wenn sich daher der alte Visualcode auf globale Variablen stützt, funktioniert das Visual möglicherweise nicht mehr.

In der Vorgängerversion der Power BI-Visualtools musste unter dem `powerbi.extensibility.visual`-Modul eine Visualklasse definiert werden.

## <a name="how-to-install-powerbi-visuals-tools"></a>Installieren von powerbi-visuals-tools

Das neue Toolset kann durch Ausführung des folgenden Befehls installiert werden:

```cmd
npm install -g powerbi-visuals-tools
```

Beispiel für das sampleBarChart-Visual und entsprechende [Änderungen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) in `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Installieren der Power BI-API für benutzerdefinierte Visuals

Die neue Version von powerbi-visual-tools enthält nicht alle API-Versionen. Der Entwickler muss stattdessen eine bestimmte Version des [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api)-Pakets installieren. Die Version des Pakets entspricht der API-Version für benutzerdefinierte Power BI-Visuals und stellt alle Typdefinitionen für die Power BI-API für benutzerdefinierte Visuals bereit.

Fügen Sie `powerbi-visuals-api` in die Abhängigkeiten des Projekts ein, indem Sie den Befehl `npm install --save-dev powerbi-visuals-api` ausführen.
Außerdem müssen Sie den Link zu alten API-Typdefinitionen entfernen, weil Typen aus `powerbi-visuals-api` automatisch von Webpack eingeschlossen werden. Entsprechende Änderungen sind in [dieser](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) Zeile von `package.json` enthalten.

## <a name="update-tsconfigjson"></a>Aktualisieren von „`tsconfig.json`“

Um externe Module zu verwenden, müssen Sie von der `out`-Option zu `outDir` wechseln.
`"outDir": "./.tmp/build/",` stattdessen `"out": "./.tmp/build/visual.js",`.

Dies ist erforderlich, weil TypeScript-Dateien separat in JavaScript-Dateien kompiliert werden. Deshalb müssen Sie nicht länger eine Datei „visual.js“ als Ausgabe angeben.

Sie können außerdem die `target`-Option in `ES6` ändern, wenn Sie modernes JavaScript als Ausgabe verwenden möchten. [Dies ist optional](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Aktualisieren von Hilfsprogrammen für benutzerdefinierte Visuals

Wenn Sie eines der Hilfsprogramme in [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) verwenden, sollten Sie diese ebenfalls auf die neueste Version aktualisieren.

Führen Sie den Befehl `npm install powerbi-visuals-utils-<UTILNAME> --save` (Beispiel: `npm install powerbi-visuals-utils-dataviewutils --save`) aus, um die neue Version mit externen Modulen von TypeScript abzurufen.

Ein Beispiel finden Sie im MekkoChart-[Repository](https://github.com/Microsoft/powerbi-visuals-mekkochart).
Dieses Visual verwendet alle Hilfsprogramme.

## <a name="remove-globalizejs-library"></a>Entfernen der Bibliothek „globalize.js“

In der neuen Version von [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) ist „globalize.js“ standardmäßig enthalten.
Sie müssen diese Bibliothek nicht manuell zum Projekt hinzufügen.
Alle erforderlichen Lokalisierungen werden dem endgültigen Paket automatisch hinzugefügt.

## <a name="fix-loading-external-libraries"></a>Korrigieren des Ladevorgangs für externe Bibliotheken

Schließen Sie eine neue JS-Datei nach Bibliotheken im `externalJS`-Array von `pbiviz.json` ein. Beispiel:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importieren Sie die Bibliotheken in der Quelle. Beispiel für `lodash-es`:

```JS
import * as _ from "lodash-es";
```

Hierbei ist `_` die globale Variable für die `lodash`-Bibliothek.

## <a name="changes-in-the-visuals-sources"></a>Änderungen in den Visualquellen

Die wichtigste Änderung besteht darin, interne Module in externe Module umzuwandeln, da Sie keine externen Module innerhalb interner Module verwenden können.

Diese Änderungen beschreiben Modifikationen, die im Beispielliniendiagramm angewendet wurden.

Detaillierte Beschreibungen der Änderungen finden Sie unten:

1. Entfernung aller Moduldefinitionen aus jeder Datei des [Quellcodes](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Import von API-Definitionen für benutzerdefinierte Power BI-Visuals](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2)

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Import](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) erforderlicher Schnittstellen oder Klassen aus einem internen `powerbi`-Modul

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

4. [Import](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) der D3.js-Bibliothek

    ```typescript
    import * as d3 from "d3";
    ```

    (oder nur Import der erforderlichen d3-Bibliotheksmodule)

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Import](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) von Hilfsprogrammen, Klassen, Schnittstellen, die im Visualprojekt der Hauptquelldatei definiert sind

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Import von CSS-Stilen

Die neue Toolversion ermöglicht es Entwicklern, CSS-LESS-Stile direkt in den TypeScript-Code zu importieren.

Daher wird der zuvor verwendete [Stilabschnitt](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) durch einen Compiler ignoriert.

Öffnen Sie zur Verwendung Ihres Stylesheets die TS-Hauptdatei, und fügen Sie die folgende Zeile ein.  

```typescript
import "./../style/visual.less";
```  

Ihre CSS-LESS-Stile werden automatisch kompiliert.  

### <a name="externaljs-section-in-pbivizjson"></a>externalJS-Abschnitt in „pbiviz.json“

Eine `externalJS`-Liste zum Laden in das Visualbundle wird von den Tools [nicht benötigt](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20). Webpack schließt alle importierten Bibliotheken ein.

**Der Abschnitt „externalJS“ in der Datei „pbivi.json“ muss leer sein.**

Rufen Sie die typischen Befehle `npm run package` zum Erstellen des Visualpakets oder `npm run start` zum Starten des Entwicklungsserver auf.

## <a name="updating-d3js-library-to-version-5"></a>Aktualisieren der D3.js-Bibliothek auf Version 5

Mit den neuen Tools können Sie die neue Version der D3.js-Bibliothek verwenden.

Rufen Sie Befehle zum Aktualisieren von D3 in Ihrem Visualprojekt auf.

`npm install --save d3@5` zum Installieren der neuen D3.js-Bibliothek

`npm install --save-dev @types/d3@5` zum Installieren der neuen Typdefinitionen für die D3.js-Bibliothek

Es gibt verschiedene Breaking Changes, deshalb müssen Sie Ihren Code zur Verwendung der neuen D3.js-Bibliothek ändern.

1. Die Schnittstelle `d3.Selection<T>` [wurde geändert](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

2. Es ist nicht möglich, mehrere Attribute durch einen einzigen Aufruf der `attr`-Methode anzuwenden. Sie [müssen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) jedes Attribut in einem separaten Aufruf der `attr`-Methode übergeben. [Ähnliches](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) gilt auch für die `style`-Methode.

3. In D3.js v4 wurde die neue merge-Methode eingeführt. Diese Methode wird üblicherweise verwendet, um die Eingabe- und Aktualisierungsauswahl nach einem Datenjoin zusammenzuführen. [Rufen Sie die merge-Methode auf](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272), um d3 ordnungsgemäß zu verwenden.

[Erfahren Sie mehr](https://github.com/d3/d3/blob/master/CHANGES.md) über die Änderungen in der D3.js-Bibliothek.

## <a name="babel"></a>Babel

Ab Version 3.1 verwenden die Tools Babel, um neuen, modernen JS-Code in herkömmlichen ES5-Code zu kompilieren und so eine Vielzahl von Browsern zu unterstützen.

Diese Option ist standardmäßig aktiviert, aber Sie müssen das [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill)-Paket manuell importieren.

Führen Sie zur Paketinstallation diesen Befehl aus:

`npm install --save @babel/polyfill`

Importieren Sie das Paket am Startpunkt des Visualcodes (üblicherweise die zugehörige Datei „src/visual.ts“):

`import "@babel/polyfill";`

Weitere Informationen zu Babel finden Sie in der [Dokumentation](https://babeljs.io/docs/en/).

Führen Sie abschließend [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) aus, um die Codebasis des Visuals anzuzeigen.  

![Statistik zum Visualcode](./media/webpack-stats.png)
