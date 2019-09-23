---
title: Strukturieren und Kombinieren von Daten aus mehreren Quellen
description: In diesem Tutorial erfahren Sie, wie Sie Daten in Power BI Desktop strukturieren und kombinieren.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 2835dd34ce5ba2d7bc6be8659b87eb1f550fdc28
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514591"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>Tutorial: Strukturieren und Kombinieren von Daten in Power BI Desktop

Mit **Power BI Desktop** können Sie Verbindungen zu vielen unterschiedlichen Arten von Datenquellen herstellen und anschließend die Daten nach Ihren Anforderungen strukturieren. So können Sie visuelle Berichte erstellen und mit anderen Benutzern gemeinsam nutzen. Das *Strukturieren* von Daten ist mit einem Transformieren der Daten gleichzusetzen. So müssen beispielsweise Spalten oder Tabellen umbenannt, Text in Zahlen umgewandelt, Zeilen entfernt oder die erste Zeile als Überschrift festgelegt werden. Als *Kombinieren* von Daten werden das Verbinden von mehreren Datenquellen, das auf die Anforderungen ausgerichtete Strukturieren der Daten und schließlich das Konsolidieren in eine praktische Abfrage bezeichnet.

In diesem Tutorial erhalten Sie Informationen zu den folgenden Vorgängen:

* Strukturieren von Daten mit dem **Abfrage-Editor**
* Herstellen einer Verbindung mit einer Datenquelle
* Herstellen einer Verbindung mit einer anderen Datenquelle
* Kombinieren dieser Datenquellen und Erstellen eines Datenmodells zur Verwendung in Berichten

Dieses Tutorial veranschaulicht, wie Sie eine Abfrage mit Power BI Desktop strukturieren, und erläutert einige der dabei am häufigsten auszuführenden Aufgaben. Die hier verwendete Abfrage (und auch der gesamte Erstellungsvorgang) ist im Handbuch [Erste Schritte mit Power BI-Desktop](desktop-getting-started.md) ausführlicher beschrieben.

Es ist wichtig zu wissen, dass im **Abfrage-Editor** von Power BI Desktop neben den im Menüband verfügbaren Optionen häufig Kontextmenüs (Rechtsklick) zum Einsatz kommen. Die meisten Optionen, die im Menüband **Transformieren** zur Auswahl stehen, können auch über Klicken auf ein Element (z. B. eine Spalte) mit der rechten Maustaste und Auswählen aus dem Kontextmenü aufgerufen werden.

## <a name="shape-data"></a>Strukturieren von Daten
Wenn Sie im Abfrage-Editor Daten strukturieren, geben Sie schrittweise Anweisungen vor (die der Abfrage-Editor dann für Sie ausführt), um die Daten beim Laden und Darstellen im Abfrage-Editor anzupassen. Die ursprüngliche Datenquelle wird davon nicht berührt. Angepasst bzw. *strukturiert* wird nur diese spezifische Ansicht der Daten.

Die Schritte, die Sie angeben (z. B. Umbenennen einer Tabelle, Transformieren eines Datentyps oder Löschen von Spalten), werden vom Abfrage-Editor aufgezeichnet und bei jeder Verbindung zu dieser Datenquelle ausgeführt, sodass die Daten stets in der gewünschten Art "strukturiert" sind. Dieser Vorgang erfolgt jedes Mal, wenn Sie den Abfrage-Editor in Power BI Desktop verwenden, aber auch jedes Mal, wenn jemand auf die freigegebene Abfrage zugreift, z. B. im **Power BI**-Dienst. Diese Schritte werden der Reihe nach im Bereich **Abfrageeinstellungen** unter **Angewendete Schritte** aufgezeichnet.

Die folgende Abbildung zeigt den Bereich **Abfrageeinstellungen** für eine strukturierte Abfrage. In den nächsten Abschnitten werden die Schritte im Einzelnen erläutert.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

Wir verwenden wieder die Daten zu den bevorzugten Wohnorten für Pensionäre aus dem Handbuch [Erste Schritte mit Power BI Desktop](desktop-getting-started.md), die wir über die Verbindung mit einer Webdatenquelle gefunden haben. Wir werden die Daten so strukturieren, dass sie unseren Anforderungen entsprechen.

Fügen Sie zunächst eine benutzerdefinierte Spalte hinzu, um den Rang basierend auf allen Daten als gleichwertige Faktoren zu berechnen, und diese mit der vorhandenen Spalte _Rang_ zu vergleichen.  Im Folgenden ist das Menüband **Spalte hinzufügen** mit einem auf die Schaltfläche **Benutzerdefinierte Spalte** zeigenden Pfeil abgebildet, mit der Sie eine benutzerdefinierte Spalte hinzufügen können.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

Geben Sie im Dialogfeld **Benutzerdefinierte Spalte** unter **Neuer Spaltenname** einen Wert für _Neuer Rang_ und unter **Benutzerdefinierte Spaltenformel** Folgendes ein:

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

Vergewissern Sie sich, dass die Statusmeldung _Es wurden keine Syntaxfehler erkannt._ angezeigt wird, und klicken Sie auf **OK**.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

Um die Konsistenz der Spaltendaten sicherzustellen, transformieren Sie die neuen Spaltenwerte in ganze Zahlen. Klicken Sie einfach mit der rechten Maustaste auf die Spaltenüberschrift, und wählen Sie **Typ ändern \> Ganze Zahl** aus, um die Werte zu ändern. 

Wenn Sie mehr als eine Spalte auswählen müssen, wählen Sie zuerst eine Spalte aus, halten Sie die **UMSCHALTTASTE** gedrückt, und wählen Sie dann weitere angrenzende Spalten aus. Klicken Sie anschließend mit der rechten Maustaste auf eine Spaltenüberschrift, um alle ausgewählten Spalten zu ändern. Sie können auch die **STRG-TASTE** verwenden, um nicht angrenzende Spalten auszuwählen.

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

Sie können über das Menüband **Transformieren** Spaltendatentypen auch *transformieren* . Die Abbildung zeigt das Menüband **Transformieren**. Der Pfeil weist auf die Schaltfläche **Datentyp**, mit der Sie den aktuellen Datentyp in einen anderen Typ transformieren können.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Im Bereich **Abfrageeinstellungen** sehen Sie, dass unter **Angewendete Schritte** alle Schritte zum Strukturieren der Daten aufgeführt sind. Wenn Sie einen Schritt aus dem Strukturierungsprozess entfernen möchten, wählen Sie einfach das **X** links neben dem jeweiligen Schritt aus. In der folgenden Abbildung werden unter **Angewendete Schritte** die bisher ausgeführten Schritte aufgelistet: Herstellen einer Verbindung zur Website (**Quelle**), Auswahl der Tabelle (**Navigation**) und die automatische Konvertierung von textbasierten Zahlenspalten von *Text* in *Ganze Zahl* (**Geänderter Typ**) durch den Abfrage-Editor beim Laden der Tabelle. Die letzten beiden Schritte spiegeln unsere vorherigen Aktionen mit **Hinzugefügte benutzerdefinierte Spalte** und **Typ1 geändert** wider. 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

Bevor wir mit dieser Abfrage arbeiten können, müssen wir ein paar Änderungen vornehmen, um die Daten nach unseren Anforderungen zu ordnen:

* *Anpassen der Rangfolgen durch Entfernen einer Spalte*: Wir sind zu dem Schluss gekommen, dass **Lebenshaltungskosten** kein Faktor in unseren Ergebnissen ist. Nachdem diese Spalte entfernt wurde, waren wir mit dem Problem konfrontiert, dass die Daten nicht geändert wurden. Dieses Problem kann mit Power BI Desktop jedoch mühelos behoben werden, was ein interessantes Feature des Bereichs **Angewendete Schritte** in der Abfrage veranschaulicht.
* *Beheben einiger Fehler*: Da wir eine Spalte entfernt haben, müssen wir unsere Berechnungen in der Spalte **Neuer Rang** erneut anpassen. Hierbei muss eine Formel geändert werden.
* *Sortieren von Daten*: Wir sortieren Daten basierend auf den Spalten **Neuer Rang** und **Rang**. 
* *Ersetzen von Daten*: Wir zeigen, wie ein bestimmter Wert ersetzt wird und dabei ein Schritt unter **Angewendete Schritte** einzufügen ist.
* *Ändern des Tabellennamens*: **Table 0** ist kein sinnvoller Deskriptor, kann aber sehr einfach geändert werden.

Um die Spalte **Lebenshaltungskosten** zu entfernen, wählen Sie zuerst die Spalte und dann im Menüband die Registerkarte **Start** aus. Klicken Sie anschließend auf **Spalten entfernen**, wie in der folgenden Abbildung gezeigt.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

Beachten Sie, dass die Werte _Neuer Rang_ nicht geändert wurden. Dies liegt an der Reihenfolge der Schritte. Der Abfrage-Editor zeichnet die Schritte zwar nacheinander, aber unabhängig voneinander auf. Daher können Sie unter **Angewendete Schritte** die Schritte in der Reihenfolge nach oben oder unten verschieben. Klicken Sie einfach mit der rechten Maustaste auf einen beliebigen Schritt, und der Abfrage-Editor stellt ein Kontextmenü mit folgenden Optionen bereit: **Umbenennen**, **Löschen**, **Bis zum Ende** **löschen** (entfernt den aktuellen Schritt und auch alle nachfolgenden Schritte), **Nach oben** und **Nach unten**. Fahren Sie fort, und verschieben Sie den letzten Schritt _Entfernte Spalten_ an die Stelle direkt über den Schritt _Hinzugefügte benutzerdefinierte Spalte_.

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

Wählen Sie als Nächstes den Schritt _Hinzugefügte benutzerdefinierte Spalte_ aus. Beachten Sie, dass bei den Daten nun ein _Fehler_ angezeigt wird, den wir beheben müssen. 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

Es gibt verschiedene Möglichkeiten, weitere Informationen zu den einzelnen Fehlern zu erhalten. Sie können entweder die Zelle auswählen (ohne auf das Wort **Fehler**zu klicken) oder direkt auf das Wort **Fehler** klicken. Wenn Sie die Zelle *ohne* Klicken auf das Wort **Fehler**auswählen, zeigt der Abfrage-Editor die Fehlerinformationen unten im Fenster an.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

Wenn Sie direkt auf das Wort *Fehler* klicken, erstellt die Abfrage im Bereich **Abfrageeinstellungen** unter **Angewendete Schritte** einen weiteren Schritt und zeigt die Informationen zu dem Fehler an. Diesen Weg möchten wir jedoch nicht gehen. Klicken Sie daher auf **Abbrechen**.

Wählen Sie zur Behebung des Fehlers die Spalte _Neuer Rang_ aus, und zeigen Sie dann die Datenbearbeitungsleiste der Spalte an, indem Sie das Menüband **Ansicht** öffnen und das Kontrollkästchen **Bearbeitungsleiste** aktivieren. 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

Nun können Sie den Parameter _Lebenshaltungskosten_ entfernen und den Divisor durch Ändern der Formel in folgenden Wert verringern: 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

Aktivieren Sie das Kontrollkästchen „Bearbeitungsleiste“, oder drücken Sie die **EINGABETASTE**. Die Daten sollten daraufhin durch geänderte Werte ersetzt werden und der Schritt **Hinzugefügte benutzerdefinierte Spalte** sollte nun *ohne Fehler*  durchgeführt werden.

> [!NOTE]
> Sie können auch die Option **Fehler entfernen** (im Menüband oder Kontextmenü) verwenden, mit der fehlerhafte Zeilen entfernt werden. In diesem Fall würden damit alle Zeilen aus den Daten entfernt. Das möchten wir aber nicht, sondern wir möchten alle Daten in der Tabelle beibehalten.

Nun müssen wir die Daten basierend auf der Spalte **Neuer Rang** sortieren. Wählen Sie zuerst den zuletzt angewendeten Schritt **Typ1 geändert** aus, um die neuesten Daten abzurufen. Wählen Sie anschließend die Dropdownliste neben der Spaltenüberschrift **Neuer Rang** und dann **Aufsteigend sortieren** aus.

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

Beachten Sie, dass die Daten nun nach **Neuer Rang** sortiert sind.  Wenn Sie sich jedoch die Spalte **Rang** ansehen, wird Ihnen auffallen, dass die Daten in Fällen, in denen der Wert **Neuer Rang** gleichwertig ist, nicht ordnungsgemäß sortiert wurden. Wählen Sie zur Behebung dieses Problems die Spalte **Neuer Rang** aus, und ändern Sie die Formel in der **Bearbeitungsleiste** in den folgenden Wert:

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

Aktivieren Sie das Kontrollkästchen „Bearbeitungsleiste“, oder drücken Sie die **EINGABETASTE**. Die Zeilen sollten nun gemäß den beiden Spalten _Neuer Rang_ und _Rang_ sortiert werden.

Außerdem können Sie unter **Angewendete Schritte** einen beliebigen Schritt in der Liste auswählen und die Strukturierung der Daten an diesem Punkt der Reihenfolge fortsetzen. Der Abfrage-Editor fügt unter **Angewendete Schritte**nach dem aktuell ausgewählten Schritt automatisch einen neuen Schritt ein. Probieren wir es aus.

Wählen Sie vor Hinzufügen der benutzerdefinierten Spalte zunächst den jeweiligen Schritt unter **Angewendete Schritte** aus, d.h. den Schritt _Entfernte Spalten_. An dieser Stelle wird der Wert der Rangfolge _Wetter_ in Arizona ersetzt. Klicken Sie mit der rechten Maustaste auf die Zelle, die die Rangfolge _Wetter_ von Arizona enthält, und wählen Sie *Werte ersetzen...* im angezeigten Kontextmenü aus. Achten Sie darauf, welcher Schritt unter **Angewendete Schritte** aktuell ausgewählt ist (der Schritt vor dem Schritt _Hinzugefügte benutzerdefinierte Spalte_).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

Da wir einen Schritt einfügen, warnt uns der Abfrage-Editor vor möglichen Konsequenzen - die nachfolgenden Schritte könnten u.U. beeinträchtigt und die Abfrage unbrauchbar werden. Wir müssen sorgfältig und mit Bedacht vorgehen! Da dies ein Tutorial ist und wir ein wirklich nützliches Feature der Abfrage zum Erstellen, Löschen, Einfügen und Neuordnen von Schritten veranschaulichen möchten, fahren wir fort und wählen **Einfügen** aus.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Ändern Sie den Wert in _51_. Die Daten für Arizona werden daraufhin ersetzt. Wenn Sie einen neuen angewendeten Schritt erstellen, benennt ihn der Abfrage-Editor nach der jeweiligen Aktion, in diesem Fall **Ersetzter Wert**. Wenn die Abfrage mehrere Schritte gleichen Namens enthält, versieht der Abfrage-Editor unter **Angewendete Schritte** jeden Folgeschritt zur Unterscheidung mit einer Nummer in der entsprechenden Reihenfolge.

Wählen Sie nun den letzten Schritt _Sortierte Zeilen_ unter **Angewendete Schritte** aus, und berücksichtigen Sie den Umstand, dass die Daten bezüglich der neuen Rangfolge von Arizona geändert wurden.  Dies ist darauf zurückzuführen, dass wir den Schritt _Ersetzter Wert_ an der richtigen Stelle eingefügt haben, nämlich vor dem Schritt _Hinzugefügte benutzerdefinierte Spalte_.

Zugegeben, das war jetzt ein bisschen kompliziert, aber ein gutes Beispiel für die leistungsfähigen und vielseitigen Abfragefunktionen.

Zum Schluss möchten wir noch den Namen der Tabelle in einen aussagekräftigeren Namen ändern. Bei der späteren Erstellung von Berichten sind aussagekräftige Tabellennamen besonders wichtig, gerade wenn Sie Verbindungen zu mehreren Datenquellen herstellen und alle im Bereich **Felder** der **Berichtsansicht** aufgelistet sind.

Das Ändern des Tabellennamen ist einfach: Geben Sie im Bereich **Abfrageeinstellungen** unter **Eigenschaften**einfach den neuen Namen der Tabelle ein (siehe Abbildung), und drücken Sie dann die **EINGABETASTE**. Wir nennen diese Tabelle *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

Die Daten sind nun soweit strukturiert, dass sie unseren Anforderungen entsprechen. Jetzt stellen wir eine Verbindung zu einer anderen Datenquelle her und kombinieren die Daten.

## <a name="combine-data"></a>Kombinieren von Daten
Diese Daten von verschiedenen Bundesstaaten sind interessant und nützlich zur Erstellung weiterer Analysen und Abfragen. Es gibt allerdings ein Problem: Bei den meisten Daten wird ein zweistelliges Länderkürzel als Code für den Bundesstaat und nicht dessen voller Name verwendet. Wir müssen die Namen der Bundesstaaten in irgendeiner Weise mit den Kürzeln verknüpfen.

Glücklicherweise gibt es eine andere öffentliche Datenquelle, die genau das bereitstellt. Die Daten müssen jedoch noch entsprechend strukturiert werden, bevor wir sie mit unserer Tabelle mit bevorzugten Wohnorten für Pensionäre verbinden können. Hier befindet sich die Webressource mit den Länderkürzeln:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Wählen Sie im Abfrage-Editor im Menüband auf der Registerkarte **Start** die Optionen **Neue Quelle \> Web** aus. Geben Sie die Adresse ein, und klicken Sie auf **Verbinden**. Im Navigator werden die Ergebnisse von dieser Webseite angezeigt.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

Wählen Sie **Codes und Abkürzungen...** aus, da diese Tabelle die gewünschten Daten enthält. Sie muss aber noch strukturiert werden, damit diese Tabelle nur noch die gewünschten Daten enthält.

> [!TIP]
> Gibt es einen schnelleren oder einfacheren Weg, die nachstehenden Schritte auszuführen? Ja, Sie könnten eine *Beziehung* zwischen den beiden Tabellen erstellen und die Daten basierend auf dieser Beziehung strukturieren. Die folgenden Schritte sind immer noch hilfreich beim Lernen der Arbeit mit Tabellen. Nehmen Sie jedoch zur Kenntnis, dass Beziehungen dabei helfen können, Daten aus mehreren Tabellen schnell zu verwenden.
> 
> 

Befolgen Sie die folgenden Schritte, um diese Daten zu strukturieren:

* Entfernen Sie die oberste Zeile. Diese ist als Folge der Erstellungsweise der Webseitentabelle entstanden und wird nicht gebraucht. Wählen Sie im Menüband auf der Registerkarte **Start** die Optionen **Zeilen verringern \> Zeilen entfernen \> Erste Zeilen entfernen** aus.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Das Fenster **Erste Zeilen entfernen** wird angezeigt, in dem Sie angeben können, wie viele Zeilen Sie entfernen möchten.

>[!NOTE]
>Wenn Power BI die Tabellenüberschriften versehentlich als Zeile in der Datentabelle importiert, können Sie zur Korrektur der Tabelle auf der Registerkarte **Start** oder der Registerkarte **Transformieren** im Menüband **Erste Zeile als Überschrift verwenden** auswählen.

* Entfernen Sie die letzten 26 Zeilen. Hierbei handelt es sich um Gebiete, die wir nicht brauchen. Wählen Sie im Menüband auf der Registerkarte **Start** die Optionen **Zeilen verringern \> Zeilen entfernen \> Letzte Zeilen entfernen** aus.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Da die Tabelle „RetirementStats“ keine Informationen für Washington, D.C., enthält, müssen wir Washington, D.C., aus der Liste herausfiltern. Wählen Sie den Dropdownpfeil neben der Spalte „Region Status“ aus, und deaktivieren Sie das Kontrollkästchen neben **Federal District**.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Entfernen Sie ein paar überflüssige Spalten. Wir brauchen nur die Zuordnung der Bundesstaaten zu den offiziellen zweistelligen Länderkürzeln. Daher können wir die folgenden Spalten entfernen: **Column1**, **Column3**, **Column4** und dann **Column6** bis **Column11**. Wählen Sie zuerst **Column1** aus, und wählen Sie dann mit gedrückter **STRG**-TASTE die übrigen zu entfernenden Spalten aus (mit STRG können Sie mehrere nicht angrenzende Spalten auswählen). Wählen Sie im Menüband auf der Registerkarte „Start“ die Optionen **Spalten entfernen \> Spalten entfernen** aus.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>An dieser Stelle sei darauf hingewiesen, dass die *Reihenfolge* der im Abfrage-Editor angewendeten Schritte wichtig ist und sich auf die Strukturierung der Daten auswirken kann. Berücksichtigt werden muss auch, wie sich ein Schritt auf einen anderen, nachfolgenden Schritt auswirkt. Wenn Sie also aus "Angewendete Schritte" einen Schritt entfernen, verhalten sich die nachfolgenden Schritte aufgrund des Einflusses der Schrittreihenfolge der Abfrage möglicherweise nicht mehr so, wie es ursprünglich beabsichtigt war.

>[!NOTE]
>Wenn Sie die Breite des Abfrage-Editorfensters verringern, werden einige Elemente des Menübands gestaucht, um den angezeigten Raum optimal zu nutzen. Wenn Sie das Fenster des Abfrage-Editors verbreitern, werden die Elemente des Menübands gedehnt, um die größere Fläche des Menübands zu nutzen.

* Benennen Sie die Spalten und die eigentliche Tabelle um. Wie üblich gibt es mehrere Möglichkeiten, eine Spalte umzubenennen: Wählen Sie zuerst die Spalte und dann im Menüband auf der Registerkarte **Transformieren** die Option **Umbenennen** aus, oder klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü die Option **Umbenennen** aus. In der folgenden Abbildung weisen Pfeile auf diese beiden Optionen; sie brauchen nur eine davon auszuwählen.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Wir benennen die Spalten in *State Name* und *State Code* um. Um die Tabelle umzubenennen, geben Sie im Bereich **Abfrageeinstellungen** den Namen einfach im Feld **Name** ein. Diese Tabelle nennen wir *StateCodes*.

Nachdem wir nun die Tabelle „StateCodes“ wie gewünscht strukturiert haben, können wir die beiden Tabellen bzw. Abfragen kombinieren. Da die Tabellen, die wir jetzt haben, die Ergebnisse der Abfragen sind, die wir auf die Daten angewendet haben, werden sie häufig auch als *Abfragen* bezeichnet.

Zum Kombinieren von Daten gibt zwei bevorzugte Möglichkeiten: *Zusammenführen* und *Anhängen*.

Wenn eine oder mehrere Spalten zu einer anderen Abfrage hinzugefügt werden sollen, werden die Abfragen **zusammengeführt** . Wenn einer vorhandenen Abfrage zusätzliche Datenzeilen hinzugefügt werden sollen, wird die Abfrage **angehangen** .

Im vorliegenden Fall sollen Abfragen zusammengeführt werden. Wählen Sie zunächst im linken Bereich des Abfrage-Editors die Abfrage aus, *mit der* die andere Abfrage zusammengeführt werden soll, in diesem Fall *RetirementStats*. Anschließend wählen Sie im Menüband auf der Registerkarte **Start\> die** Optionen Kombinieren **Abfragen** zusammenführen aus.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Möglicherweise werden Sie aufgefordert, die Sicherheitsstufen festzulegen, um sicherzustellen, dass die Daten kombiniert werden, ohne Daten mit einzuschließen oder zu übertragen, die Sie nicht einschließen oder übertragen möchten.

Im Fenster **Zusammenführen** werden Sie aufgefordert, die Tabelle auszuwählen, die mit der ausgewählten Tabelle zusammengeführt werden soll. Anschließend müssen Sie die Spalten angeben, die für die Zusammenführung verwendet werden sollen. Wählen Sie „State“ in der Tabelle (Abfrage) *RetirementStats* und dann die Abfrage *StateCodes* aus. (Das ist in diesem Fall recht einfach, da es nur eine andere Abfrage gibt. Wenn Sie Verbindungen zu vielen Datenquellen herstellen, stehen hier viele Abfragen zur Auswahl.) Wenn Sie die übereinstimmenden Spalten – **State** aus *RetirementStats* und **State Name** aus *StateCodes* – richtig auswählen, sieht das Fenster **Zusammenführen** wie folgt aus, und die Schaltfläche **OK** ist aktiviert.

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

Am Ende der Abfrage wird eine neue Spalte namens **NewColumn** erstellt, die den Inhalt der Tabelle (Abfrage) enthält, die mit der vorhandenen Abfrage zusammengeführt wurde. Alle Spalten der zusammengeführten Abfrage werden auf die neue Spalte **NewColumn** reduziert. Sie können jedoch die Tabelle **erweitern** und die gewünschten Spalten einbeziehen.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Um die zusammengeführte Tabelle zu erweitern und auszuwählen, welche Spalten einbezogen werden sollen, klicken Sie auf das Erweiterungssymbol (![Erweitern](media/desktop-shape-and-combine-data/icon.png)). Das Fenster **Erweitern** wird geöffnet.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

In unserem Fall benötigen wir nur die Spalte **State Code**. Daher wählen Sie nur diese Spalte aus und klicken dann auf **OK**. Deaktivieren Sie das Kontrollkästchen „Ursprünglichen Spaltennamen als Präfix verwenden“, da wir den ursprünglichen Spaltennamen nicht benötigen. Wenn das Kontrollkästchen aktiviert bleibt, erhält die zusammengeführte Spalte den Namen **NewColumn.State Code** (zusammengesetzt aus dem ursprünglichen Spaltennamen bzw. **NewColumn**, einem Punkt und dem Namen der in die Abfrage eingefügten Spalte).

>[!NOTE]
>Möchten Sie ein wenig mit dem Einfügen der Tabelle **NewColumn** experimentieren? Sie können ein wenig ausprobieren. Wenn Ihnen die Ergebnisse nicht gefallen, löschen Sie diesen Schritt einfach in der Liste **Angewendete Schritte** im Bereich **Abfrageeinstellungen**. Ihre Abfrage wird dann wieder in den Zustand vor Anwenden des Schritts **Erweitern** versetzt. Auf diese Weise können Sie beliebig oft und solange experimentieren, bis die Erweiterung Ihren Vorstellungen entspricht.

Wir haben jetzt eine einzelne Abfrage (Tabelle), in der zwei entsprechend den Anforderungen strukturierte Datenquellen miteinander kombiniert sind. Diese Abfrage kann als Grundlage für viele weitere interessante Datenverbindungen dienen, z. B. für Statistiken zu Wohnkosten, demografischen Daten oder Beschäftigungsmöglichkeiten in den einzelnen Bundesstaaten.

Um die Änderungen zu übernehmen und den Abfrage-Editor zu schließen, wählen Sie auf der Registerkarte **Start** des Menübands die Option **Schließen und Anwenden** aus. Das transformierte Dataset wird in Power BI Desktop angezeigt und kann zum Erstellen von Berichten verwendet werden.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Nächste Schritte
Mit Power BI Desktop können Sie viele Aufgaben ausführen. Weitere Informationen zu den Funktionen und Möglichkeiten finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Übersicht zu Abfragen mit Power BI Desktop](desktop-query-overview.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Verbinden mit Daten in Power BI Desktop](desktop-connect-to-data.md)
* [Allgemeine Abfrageaufgaben in Power BI Desktop](desktop-common-query-tasks.md)   

