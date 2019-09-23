---
ms.openlocfilehash: 5c2b254f20bd1eba97840a464a1b554cc4fe1238
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273376"
---
Die Verwendung von **Variablen** ist ein äußerst wichtiger Teil eines DAX-Ausdrucks.

![](media/7-4-dax-expressions/dax-variables_1.png)

Sie können eine Variable überall in einem DAX-Ausdruck definieren. Verwenden Sie dabei die folgenden Syntax:

    VARNAME = RETURNEDVALUE

Bei Variablen kann es sich um einen beliebigen Datentyp handeln, u.a. ganze Tabellen.

Beachten Sie, dass Power BI bei jedem Verweis auf die Variable in Ihrem DAX-Ausdruck den Wert entsprechend der Definition neu berechnen muss. Es wird daher empfohlen, Variablen in einer Funktion nicht zu wiederholen.

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

