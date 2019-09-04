---
title: 'Übergeben eines Berichtsparameters in einer URL für einen paginierten Bericht: Power BI-Berichts-Generator'
description: In diesem Thema wird beschrieben, wie Sie Berichtsparameter an einen Bericht übergeben, indem Sie diese in die URL eines paginierten Berichts einschließen.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: add2f82594d83d1e1f177bfad5045c2e0a34ba84
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70189367"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Übergeben eines Berichtsparameters in einer URL für einen paginierten Bericht in Power BI 

Sie können Berichtsparameter an einen Bericht übergeben, indem Sie diese in die URL eines paginierten Berichts einschließen. Alle Abfrageparameter können über entsprechende Berichtsparameter verfügen. Daher übergeben Sie einen Abfrageparameter an einen Bericht, indem Sie den entsprechenden Berichtsparameter übergeben. Sie müssen den Parameternamen mit dem Präfix `rp:` versehen, damit Power BI ihn in der URL erkennen kann. 

Bei den Berichtsparametern wird die Groß-/Kleinschreibung beachtet, und es werden die folgenden Sonderzeichen verwendet: 

- Ein Leerzeichen im Parameterteil der URL wird durch ein Pluszeichen (+) ersetzt.  Beispiel: 

    ```rp:Holiday=Christmas+Day```

- Ein Semikolon in einem beliebigen Teil der Zeichenfolge wird durch die Zeichen `%3A` ersetzt.

Browser sollten automatisch die richtige URL-Codierung durchführen. Sie müssen keines der Zeichen manuell codieren. 

Verwenden Sie die folgende Syntax, um einen Berichtsparameter innerhalb einer URL festzulegen: 

```
rp:parameter=value
```

Wenn Sie z. B. die beiden Parameter „Salesperson“ und „State“ angeben möchten, die Sie in einem Bericht in Ihrem Arbeitsbereich definiert haben, verwenden Sie folgende URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Wenn Sie dieselben zwei Parameter angeben möchten, die Sie in einem Bericht in einer App definiert haben, verwenden Sie die folgende URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Verwenden Sie die folgende Syntax, um einen NULL-Wert für einen Parameter zu übergeben: 

```
parameter:isnull=true
```

Beispiel:

```
rp:SalesOrderNumber:isnull=true
```

Verwenden Sie 0 für FALSE und 1 für TRUE, um einen booleschen Wert zu übergeben. Schließen Sie das Dezimaltrennzeichen des Servergebietsschemas ein, um einen Gleitkommawert zu übergeben.

> [!NOTE]
> Wenn Ihr Bericht einen Berichtsparameter enthält, der über einen Standardwert verfügt, und der Wert der  **Prompt**-Eigenschaft  **FALSE** ist (d. h., die **Prompt User**-Eigenschaft wird im Berichts-Manager nicht ausgewählt), können Sie für diesen Berichtsparameter keinen Wert innerhalb einer URL übergeben. Dadurch können Administratoren verhindern, dass Endbenutzer die Werte bestimmter Berichtsparameter hinzufügen oder ändern.

## <a name="additional-examples"></a>Zusätzliche Beispiele 

Das folgende URL-Beispiel enthält einen mehrwertigen Parameter „Salesperson“. Das Format für einen mehrwertigen Parameter sieht vor, den Parameternamen für jeden Wert zu wiederholen. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

Im folgenden URL-Beispiel wird ein einzelner Parameter von SellStartDate mit dem Wert „7/1/2005“ für einen Berichtsserver im einheitlichen Modus übergeben.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Nächste Schritte

- [URL-Parameter in paginierten Berichten in Power BI](report-builder-url-parameters.md)
- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)