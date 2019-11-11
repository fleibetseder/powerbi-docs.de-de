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
ms.openlocfilehash: c96518bb8de7f323b51a7e1e3f34f9d9bf056c79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875392"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: Vergleich zwischen der DIVIDE-Funktion und dem Divisionsoperator (/)

Dieser Artikel ist an Datenmodellierer gerichtet, die DAX-Ausdrücke definieren.

## <a name="background"></a>Hintergrund

Beim Schreiben eines DAX-Ausdrucks zum Teilen eines Zählers durch einen Nenner können Sie die [DIVIDE](/dax/divide-function-dax)-Funktion oder den Divisionsoperator („/“ – Schrägstrich) verwenden.

Wenn Sie die DIVIDE-Funktion verwenden, müssen Sie den Zähler und den Nenner in Ausdrücken übergeben. Optional können Sie einen Wert übergeben, der ein alternatives Ergebnis darstellt.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

Die DIVIDE-Funktion wurde dazu konzipiert, Fälle mit Division durch 0 (null) automatisch zu behandeln. Wenn kein alternatives Ergebnis übergeben wird, und der Nenner 0 (null) oder BLANK (leer) ist, gibt die Funktion BLANK (leer) zurück. Wenn ein alternatives Ergebnis übergeben wird, wird dieses anstelle von BLANK zurückgegeben.

Die DIVIDE-Funktion ist praktisch, da Ihr Ausdruck den Nennerwert nicht testen muss. Die Funktion ist außerdem besser für das Testen des Nennerwerts geeignet als die [IF](/dax/if-function-dax)-Funktion. Der Leistungsgewinn ist wichtig, da das Überprüfen der Division durch Null (0) ressourcenintensiv ist. Darüber hinaus resultiert die Verwendung von DIVIDE in einem präziseren und schöneren Ausdruck.

## <a name="example"></a>Beispiel

Der folgende Measureausdruck erzeugt eine sichere Division, erfordert jedoch vier DAX-Funktionen.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Dieser Measureausdruck erzielt dasselbe Ergebnis, ist aber effizienter und schöner.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Empfehlungen

Es wird empfohlen, dass Sie die DIVIDE-Funktion verwenden, wenn es sich beim Nenner um einen Ausdruck handelt, der 0 (null) oder BLANK zurückgeben _kann_.

Wenn es sich beim Nenner um einen konstanten Wert handelt, wird empfohlen, dass Sie den Divisionsoperator verwenden. In diesem Fall ist die Division garantiert erfolgreich, und Ihr Ausdruck erzielt eine bessere Leistung, da unnötige Tests vermieden werden.

Sie sollten sich sorgfältig überlegen, ob die DIVIDE-Funktion einen alternativen Wert zurückgeben sollte. Für Measures ist es in der Regel besser, wenn sie BLANK zurückgeben. Das liegt daran, dass Berichtsvisuals Gruppierungen standardmäßig löschen, wenn Zusammenfassungen leer sind. Dadurch kann sich das Visual auf Gruppierungen konzentrieren, die Daten enthalten. Bei Bedarf können Sie das Visual so konfigurieren, dass alle Gruppen (die Werte oder BLANK zurückgeben) im Filterkontext angezeigt werden, indem Sie die Option „Elemente ohne Daten anzeigen“ aktivieren.
