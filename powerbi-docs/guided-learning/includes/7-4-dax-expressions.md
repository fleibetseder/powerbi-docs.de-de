---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799868"
---
Die Verwendung von **Variablen** ist ein äußerst wichtiger Teil eines DAX-Ausdrucks.

![](media/7-4-dax-expressions/dax-variables_1.png)

Sie können eine Variable überall in einem DAX-Ausdruck definieren. Verwenden Sie dabei die folgenden Syntax:

    VARNAME = RETURNEDVALUE

Bei Variablen kann es sich um einen beliebigen Datentyp handeln, u.a. ganze Tabellen.

Beachten Sie, dass Power BI bei jedem Verweis auf die Variable in Ihrem DAX-Ausdruck den Wert entsprechend der Definition neu berechnen muss. Es wird daher empfohlen, Variablen in einer Funktion nicht zu wiederholen.

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

