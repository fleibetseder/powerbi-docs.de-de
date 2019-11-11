---
title: Verwenden von berechneten Tabellen in Power BI Desktop
description: Berechnete Tabellen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4da25e0c6ea7115111bc057947183a8b86b5c2f4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878684"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Verwenden von berechneten Tabellen in Power BI Desktop
Mit berechneten Tabellen können Sie dem Modell eine neue Tabelle hinzufügen. Aber anstatt Werte abzufragen und aus einer Datenquelle in die Spalten Ihrer neuen Tabelle zu laden, erstellen Sie eine DAX-Formel, die die Werte der Spalte definiert. In Power BI Desktop werden berechnete Spalten mithilfe der Funktion "Neue Tabelle" in der Berichtsansicht oder der Datenansicht erstellt.

In den meisten Fällen importieren Sie Daten aus einer externen Datenquelle in das Modell. Berechnete Tabellen bieten jedoch gewisse Vorteile. Berechnete Tabellen sind in der Regel am besten geeignet für Zwischenberechnungen und Daten, die als Teil des Modells gespeichert werden sollen, anstatt sie ad hoc oder als Teil einer Abfrage zu berechnen.

Im Gegensatz zu Tabellen, die als Teil einer Abfrage erstellt werden, basieren berechnete Tabellen, die in der Berichtsansicht oder der Datenansicht erstellt werden, auf Daten, die Sie bereits in das Modell geladen haben. Beispielsweise möchten Sie vielleicht zwei Tabellen vereinen oder kreuzen.

Genau so wie normale Tabellen können auch berechnete Tabellen Beziehungen zu anderen Tabellen aufweisen. Die Spalten in der berechneten Tabelle weisen Datentypen sowie Formatierungen auf und können zu einer Datenkategorie gehören. Sie können Ihre Spalten nach Belieben benennen und sie Berichtsvisualisierungen hinzufügen, genau wie andere Felder. Berechnete Tabellen werden neu berechnet, wenn eine der Tabellen, aus denen sie Daten abrufen, in irgendeiner Weise aktualisiert werden.

Berechnete Tabellen verwenden zum Berechnen von Ergebnissen [DAX](https://msdn.microsoft.com/library/gg413422.aspx) (Data Analysis Expressions), eine Formelsprache, die für das Arbeiten mit relationalen Daten, wie sie in Power BI Desktop verwendet werden, konzipiert ist. DAX beinhaltet eine Bibliothek aus über 200 Funktionen, Operatoren und Konstrukten, die eine enorme Flexibilität beim Erstellen von Formeln zum Berechnen von Ergebnissen für so ungefähr jede benötigte Datenanalyse verfügbar macht.

## <a name="lets-look-at-an-example"></a>Betrachten wir dazu ein Beispiel.
Jan, Projektmanager bei Contoso, verfügt über eine Tabelle mit Mitarbeitern im Nordwesten und über eine Tabelle mit Mitarbeitern im Südwesten. Jan möchte die beiden Tabellen zu einer einzelnen Tabelle zusammenfügen.

**Mitarbeiter im Nordwesten**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SouthwestEmployees** (Mitarbeiter im Südwesten)

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Diese beiden Tabellen mithilfe einer berechneten Tabelle zusammenzufügen, ist ziemlich einfach. Jan kann eine berechnete Tabelle in der Berichtsansicht oder in der Datenansicht erstellen. In der Datenansicht ist dies jedoch etwas einfacher, da Jan die neue berechnete Tabelle dann sofort sehen kann.

In der **Datenansicht**auf der Registerkarte **Modellierung** klickt Jan auf **Neue Tabelle**. Eine Bearbeitungsleiste wird angezeigt.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jan gibt die folgende Formel ein:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

Eine neue Tabelle mit dem Namen "Mitarbeiter Westliche Region" wird erstellt.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

Die neue Tabelle von Jan, mit Mitarbeitern der westlichen Region, wird genau wie alle anderen Tabellen in der Liste der Felder angezeigt. Jan kann sogar Beziehungen mit anderen Tabellen erstellen, berechnete Spalten und Maße hinzufügen sowie beliebige Tabellenfelder Berichten hinzufügen, genau wie bei jeder anderen Tabelle auch.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Funktionen für berechnete Tabellen
Berechnete Tabellen können durch einen DAX-Ausdruck definiert werden, der eine Tabelle zurückgibt, einschließlich eines einfachen Verweises auf eine andere Tabelle. Beispiel:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Sie können berechnete Tabellen zusammen mit DAX verwenden, um eine Vielzahl von analytischen Problemen zu lösen. Dies ist nur eine kurze Einführung in berechnete Tabellen. Für den Einstieg zum Arbeiten mit berechneten Tabellen werden hier einige der gängigeren DAX-Tabellenfunktionen aufgeführt, die hilfreich sein könnten:

* DISTINCT
* WERTE
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Siehe die [DAX-Funktionsreferenz](https://msdn.microsoft.com/ee634396.aspx) für diese und andere Tabellen, die DAX-Funktionen zurückgeben.

