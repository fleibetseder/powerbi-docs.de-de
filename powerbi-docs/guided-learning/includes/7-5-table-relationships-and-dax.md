---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273396"
---
Power BI ermöglicht es Ihnen, Beziehungen zwischen mehreren Tabellen zu erstellen, einschließlich Tabellen, die aus völlig anderen Datenquellen stammen. Sie können diese Beziehungen für jedes beliebige Datenmodell in der Ansicht **Beziehungen** von Power BI Desktop anzeigen.

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>Relationale DAX-Funktionen
DAX verfügt über **relationale Funktionen**, die die Interaktion mit Tabellen ermöglichen, die bestehende Beziehungen besitzen.

Sie können den Wert einer Spalte zurückgeben, oder Sie können alle Zeilen in einer Beziehung mit DAX-Funktionen zurückgeben.

Die **RELATED**-Funktion berücksichtigt z.B. Beziehungen und gibt den Wert einer Spalte zurück, während **RELATEDTABLE**E Beziehungen berücksichtigt und eine gesamte Tabelle zurückgibt, die herausgefiltert wurde und nur verwandte Zeilen besitzt.

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

Die **RELATED**-Funktion kann für *n:1-Beziehungen* verwendet werden, während **RELATEDTABLE** für *1: n-Beziehungen* vorgesehen ist.

Mit relationalen Funktionen können Sie Ausdrücke mit Werten in verschiedenen Tabellen erstellen. DAX gibt mit diesen Funktionen ein Ergebnis zurück, unabhängig davon, wie weit die Beziehung verkettet ist.

> Videoinhalt zur Verfügung gestellt von [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

