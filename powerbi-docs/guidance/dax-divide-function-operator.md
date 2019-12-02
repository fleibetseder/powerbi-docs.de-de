---
title: 'DAX: Vergleich zwischen der DIVIDE-Funktion und dem Divisionsoperator (/)'
description: Leitfaden zur Verwendung der DAX-Funktion DIVIDE
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 91acaa3a2252250e2a10674bae0e9be81f142696
ms.sourcegitcommit: f1f57c5bc6ea3057007ed8636ede50188ed90ce1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74410939"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Vergleich zwischen der DIVIDE-Funktion und dem Divisionsoperator (/)

Beim Schreiben eines DAX-Ausdrucks zum Teilen eines Zählers durch einen Nenner können Sie als Datenmodellierer die [DIVIDE](/dax/divide-function-dax)-Funktion oder den Divisionsoperator („/“ – Schrägstrich) verwenden.

Wenn Sie die DIVIDE-Funktion verwenden, müssen Sie den Zähler und den Nenner in Ausdrücken übergeben. Optional können Sie einen Wert übergeben, der ein _alternatives Ergebnis_ darstellt.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

Die DIVIDE-Funktion wurde so konzipiert, dass Fälle mit Division durch 0 (null) automatisch behandelt werden. Wenn kein alternatives Ergebnis übergeben wird, und der Nenner 0 (null) oder BLANK (leer) ist, gibt die Funktion BLANK (leer) zurück. Wenn ein alternatives Ergebnis übergeben wird, wird dieses anstelle von BLANK zurückgegeben.

Die DIVIDE-Funktion ist praktisch, da Ihr Ausdruck den Nennerwert nicht testen muss. Die Funktion ist außerdem besser für das Testen des Nennerwerts geeignet als die [IF](/dax/if-function-dax)-Funktion. Der Leistungsgewinn ist wichtig, da das Überprüfen der Division durch Null (0) ressourcenintensiv ist. Darüber hinaus ergibt die Verwendung von DIVIDE in einen präziseren und schöneren Ausdruck.

## <a name="example"></a>Beispiel

Der folgende Measureausdruck erzeugt eine sichere Division, erfordert jedoch vier DAX-Funktionen.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Dieser Measureausdruck erzielt dasselbe Ergebnis, ist aber effizienter und schöner.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Empfehlungen

Es wird empfohlen, dass Sie die DIVIDE-Funktion verwenden, wenn es sich beim Nenner um einen Ausdruck handelt, der 0 (null) oder BLANK zurückgeben _kann_.

Wenn es sich beim Nenner um einen konstanten Wert handelt, wird empfohlen, dass Sie den Divisionsoperator verwenden. In diesem Fall ist die Division garantiert erfolgreich, und Ihr Ausdruck erzielt eine bessere Leistung, da unnötige Tests vermieden werden.

Überlegen Sie sorgfältig, ob die DIVIDE-Funktion einen alternativen Wert zurückgeben sollte. Für Measures ist es in der Regel besser, wenn sie BLANK zurückgeben. Der Vorteil einer Rückgabe von BLANK ist, dass Berichtsvisuals Gruppierungen standardmäßig löschen, wenn Zusammenfassungen leer sind. Dadurch kann das Visual die Aufmerksamkeit auf Gruppierungen lenken, die Daten enthalten. Bei Bedarf können Sie das Visual so konfigurieren, dass alle Gruppen (die Werte oder BLANK zurückgeben) im Filterkontext angezeigt werden, indem Sie die Option „Elemente ohne Daten anzeigen“ aktivieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu diesem Artikel finden Sie in den folgenden Ressourcen:

- [DAX-Referenz (Data Analysis Expressions)](/dax/)
- Haben Sie Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
