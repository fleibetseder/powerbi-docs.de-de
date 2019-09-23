---
title: DAX-Grundlagen in Power BI Desktop
description: DAX-Grundlagen in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 64957fa71249c551b4f69b619a12baf03fae6b06
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513718"
---
# <a name="dax-basics-in-power-bi-desktop"></a>DAX-Grundlagen in Power BI Desktop
Dieser Artikel ist für Benutzer gedacht, die noch nicht mit Power BI Desktop gearbeitet haben. Er soll Ihnen kurz eine einfache Einführung in die Verwendung von DAX (Data Analysis Expressions) zum Lösen einer Reihe einfacher Berechnungen und Datenanalyseprobleme geben. Wir gehen einige Konzeptinformationen, eine Reihe von Aufgaben, die Sie ausführen können, und ein paar Quizfragen zum Prüfen des Gelernten durch. Nach dem Durcharbeiten dieses Artikels sollten Sie über ein gutes Verständnis der wichtigsten Konzepte in DAX verfügen.

## <a name="what-is-dax"></a>Was ist DAX?
DAX ist eine Sammlung von Funktionen, Operatoren und Konstanten, die in einer Formel oder einem Ausdruck verwendet werden können, um einen oder mehrere Werte zu berechnen oder zurückzugeben. Einfacher ausgedrückt hilft Ihnen DAX, neue Informationen aus Daten zu erstellen, die sich bereits in Ihrem Modell befinden.

## <a name="why-is-dax-so-important"></a>Warum ist DAX so wichtig?
Es ist recht einfach, eine neue Power BI Desktop-Datei zu erstellen und einige Daten in sie zu importieren. Sie können sogar ohne die Verwendung von DAX-Formeln Berichte erstellen, die wertvolle Einblicke geben. Was aber, wenn Sie das prozentuale Wachstum über alle Produktkategorien und für unterschiedliche Datumsbereiche analysieren müssen? Oder Sie müssen das jährliche Wachstum im Vergleich mit den Markttrends berechnen? DAX-Formeln geben Ihnen diese und noch viele andere wichtige Möglichkeiten. Das Wissen, wie Sie effektive DAX-Formeln erstellen, hilft Ihnen, Ihre Daten optimal zu nutzen. Wenn Sie die Informationen erhalten, die Sie benötigen, können Sie mit der Lösung echter Geschäftsprobleme beginnen, die sich auf Ihr Geschäftsergebnis auswirken. Das ist die Power in Power BI, und DAX hilft Ihnen, sie freizusetzen.

## <a name="prerequisites"></a>Voraussetzungen
Vielleicht kennen Sie sich schon mit dem Erstellen von Formeln in Microsoft Excel aus. Dieses Wissen hilft Ihnen, DAX zu verstehen, aber selbst wenn Sie keine Erfahrung mit Excel-Formeln haben, helfen Ihnen die hier beschriebenen Konzepte beim Einstieg in DAX-Formeln und beim Lösen von realen BI-Problemen nahezu aus dem Stand.

Wir legen den Schwerpunkt auf das Verstehen der DAX-Formeln, die in Berechnungen verwendet werden, genauer gesagt in Measures und berechneten Spalten. Sie sollten sich bereits mit Power BI Desktop, dem Importieren von Daten, dem Hinzufügen von Feldern zu Berichten und ebenso mit den grundlegenden Konzepten von [Measures](desktop-measures.md) und [Berechneten Spalten](desktop-calculated-columns.md) auskennen.

**Beispielarbeitsmappe**

Die beste Möglichkeit, DAX zu lernen, besteht im Erstellen einiger einfacher Formeln, ihrer Verwendung mit ein paar echten Daten und im Beobachten der Ergebnisse. Für die Beispiele und Aufgaben in diesem Artikel wird die Contoso Sales for Power BI Desktop Preview-Datei verwendet. Dies ist die gleiche Beispieldatei, die im [Tutorial: Erstellen eigener Measures in Power BI Desktop](desktop-tutorial-create-measures.md) verwendet wird. Die Beispieldatei, die Sie herunterladen können, finden Sie [hier](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip).

## <a name="lets-begin"></a>Fangen wir an!
Den Bezugsrahmen für unser Verständnis von DAX bilden drei grundlegende Konzepte: *Syntax*, *Funktionen* und *Kontext*. Natürlich gibt es andere wichtige Konzepte in DAX, aber das Verständnis dieser drei Konzepte bietet die beste Grundlage für die Entwicklung Ihrer DAX-Fertigkeiten.

### <a name="syntax"></a>Syntax
Bevor Sie eigene Formeln erstellen, werfen wir einen Blick auf die DAX-Formelsyntax. Zur Syntax gehören die verschiedenen Elemente, aus denen eine Formel besteht, oder, einfacher, wie sich die Formel zusammensetzt. Betrachten wir als Beispiel eine einfache DAX-Formel für ein Measure.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Diese Formel beinhaltet die folgenden Syntaxelemente:

**A.** Den Measurenamen **Total Sales** (Gesamtumsatz).

**B.** Der Gleichheitszeichenoperator ( **=** ) kennzeichnet den Anfang der Formel. Bei der Berechnung gibt er ein Ergebnis zurück.

**C.** Die DAX-Funktion **SUM** addiert alle Zahlen in der Spalte **Sales[SalesAmount]** . Im weiteren Verlauf erfahren Sie mehr über Funktionen.

**D.** Klammern **()** umschließen einen Ausdruck, der ein oder mehrere Argumente enthält. Für alle Funktionen ist mindestens ein Argument erforderlich. Ein Argument übergibt einen Wert an eine Funktion.

**E.** Die referenzierte Tabelle **Sales** (Umsätze).

**F.** Die referenzierte Spalte **[SalesAmount]** in der Tabelle „Sales“. Dank dieses Arguments weiß die Funktion SUM, für welche Spalte sie eine SUMME aggregieren soll.

Bei dem Versuch, eine DAX-Formel zu verstehen, ist es oft hilfreich, jedes der Elemente in eine Sprache aufzuschlüsseln, die Sie im Alltag verwenden. Beispielsweise können Sie diese Formel wie folgt lesen:

> *Für das Measure mit dem Namen „Total Sales“ (Gesamtumsatz) berechne (=) die SUMME der Werte in der Spalte „[SalesAmount]“ (Umsatzbetrag) in der Tabelle „Sales“ (Umsätze).*
> 
> 

Wenn es zu einem Bericht hinzugefügt wird, berechnet dieses Measure Werte, indem es die Umsatzbeträge für jedes der anderen Felder, die wir aufnehmen, addiert und zurückgibt, z. B. Mobiltelefone in den USA.

Sie denken jetzt vielleicht: „Macht dieses Measure nicht etwas, was ich einfach durch Hinzufügen des Felds ‚SalesAmount‘ (Umsatzbetrag) zum Bericht erreichen kann?“ Ja, stimmt. Es gibt aber einen guten Grund, ein eigenes Measure zum Addieren von Werten aus dem Feld „SalesAmount“ zu verwenden: Wir können es als Argument in anderen Formeln verwenden. Das mag jetzt ein bisschen verwirrend erscheinen, aber in dem Maß, wie Ihre Fähigkeiten im Umgang mit DAX-Formeln zunehmen, macht dieses Wissen Ihre Formeln und Modelle effizienter. Und Sie finden das Measure „Total Sales“ (Gesamtumsatz) im weiteren Verlauf in anderen Formeln.

Gehen wir noch ein paar weitere Dinge in dieser Formel durch. Insbesondere haben wir eine Funktion [SUM](https://msdn.microsoft.com/library/ee634387.aspx) eingeführt. Funktionen sind vorbereitete Formeln, die das Ausführen komplexer Berechnungen und Manipulationen mit Zahlen, Datumswerten, Uhrzeiten, Text und mehr erleichtern. Sie erfahren später mehr über Funktionen.

Sie sehen außerdem, dass der Spalte „[SalesAmount]“ der Name der Tabelle („Sales“) voransteht, in die die Spalte gehört. Dies wird als ein vollqualifizierter Spaltenname bezeichnet, insofern als er den Spaltennamen mit vorangestelltem Tabellennamen enthält. Wenn auf Spalten in der gleichen Tabelle verwiesen wird, muss der Tabellenname nicht in die Formel aufgenommen werden. Dadurch können lange Formeln, die auf viele verschiedene Spalten verweisen, kürzer und leichter lesbar werden. Allerdings empfiehlt es sich, den Tabellennamen in Ihre Measureformeln mit aufzunehmen, selbst innerhalb derselben Tabelle.

> [!NOTE]
> Wenn ein Tabellenname Leerzeichen, reservierte Schlüsselwörter oder unzulässige Zeichen enthält, müssen Sie den Tabellennamen in einfache Anführungszeichen einschließen. Sie müssen Tabellennamen auch in Anführungszeichen einschließen, wenn der Name Zeichen außerhalb des alphanumerischen ANSI-Zeichenbereichs enthält, unabhängig davon, ob diese Zeichen in Ihrem Gebietsschema unterstützt werden oder nicht.
> 
> 

Es ist wichtig, dass ihre Formeln die richtige Syntax aufweisen. In den meisten Fällen wird ein Syntaxfehler zurückgegeben, wenn die Syntax fehlerhaft ist. In anderen Fällen ist vielleicht die Syntax richtig, aber die zurückgegebenen Werte entsprechen ganz und gar nicht Ihren Erwartungen. Der DAX-Editor in Power BI Desktop beinhaltet ein Vorschlagsfeature, das zum Erstellen syntaktisch korrekter Formeln dient, indem es Ihnen hilft, die richtigen Elemente auszuwählen.

Erstellen wir eine einfache Formel. Diese Aufgabe vertieft Ihr Verständnis für die Formelsyntax und dafür, wie die Vorschlagsfunktion in der Bearbeitungsleiste Ihnen helfen kann.

### <a name="task-create-a-measure-formula"></a>Aufgabe: Erstellen einer Measureformel
Um diese Aufgabe auszuführen, müssen Sie die Contoso Sales Power BI Desktop-Beispieldatei öffnen.
    
1. Klicken Sie in der Berichtsansicht in der Feldliste mit der rechten Maustaste auf die Tabelle **Sales**, und klicken Sie dann auf **Neues Measure**.
    
2. Ersetzen Sie in der Bearbeitungsleiste **Measure**, indem Sie einen neuen Measurenamen eingeben: **Previous Quarter Sales** (Umsätze des Vorquartals).
    
3. Geben Sie nach dem Gleichheitszeichen die ersten paar Buchstaben **CAL** ein, und doppelklicken Sie dann die zu verwendende Funktion. In dieser Formel sollten Sie die **CALCULATE**-Funktion verwenden.

   Sie verwenden die Funktion CALCULATE, um die zu addierenden Beträge mithilfe eines Arguments, das wir der Funktion CALCULATE übergeben, zu filtern. Dies wird als Verschachteln von Funktionen bezeichnet. Die Funktion CALCULATE weist mindestens zwei Argumente auf. Das erste ist der auszuwertende Ausdruck und das zweite ein Filter.
   
4. Geben Sie nach der öffnenden Klammer **(** der **CALCULATE**-Funktion **SUM** gefolgt von einer weiteren öffnenden Klammer ein **(** . Nun müssen Sie ein Argument an die SUM-Funktion übergeben.

5. Beginnen Sie mit der Eingabe von **Sal**, und wählen Sie dann **Sales[SalesAmount]** aus. Fügen Sie dann eine schließende Klammer **)** ein. Dies ist das erste Ausdrucksargument für unsere CALCULATE-Funktion.
    
6. Geben Sie ein Komma ( **,** ) gefolgt von einem Leerzeichen ein, um den ersten Filter anzugeben, und geben Sie dann **PREVIOUSQUARTER** ein. Dies ist der Filter.
    
   Sie verwenden die PREVIOUSQUARTER-Zeitintelligenzfunktion, um die SUM-Ergebnisse nach dem vorherigen Quartal zu filtern.
    
7. Geben Sie nach der öffnenden Klammer **(** für die PREVIOUSQUARTER-Funktion **Calendar[DateKey]** ein.
    
   Die Funktion PREVIOUSQUARTER hat ein Argument, eine Spalte, die einen zusammenhängenden Bereich von Datumswerten enthält. In diesem Fall ist dies die DateKey-Spalte in der Calendar-Tabelle.
    
8. Achten Sie darauf, dass beide an die Funktion PREVIOUSQUARTER und an die Funktion CALCULATE übergebenen Argumente mit zwei schließenden Klammern **))** geschlossen werden.
    
   Die Formel sollte nun wie folgt aussehen:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
9. Klicken Sie auf das Häkchen ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) in der Bearbeitungsleiste, oder drücken Sie die EINGABETASTE, um die Formel zu überprüfen und sie zum Modell hinzuzufügen.

Sie haben‘s geschafft! Sie haben gerade mithilfe von DAX ein Measure erstellt, und noch dazu kein einfaches. Was diese Formel tut – sie berechnet die Gesamtumsätze für das Vorquartal, abhängig von den in einem Bericht angewendeten Filtern. Wenn wir z. B. „SalesAmount“ (Umsatzbetrag) und unser neues Measure „Previous Quarter Sales“ in ein Diagramm einsetzen und dann „Year“ (Jahr) und „QuarterOfYear“ („QuartalImJahr“) als Datenschnitte hinzufügen, kommt etwas in dieser Art heraus:

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Sie wurden gerade mit einigen wichtigen Aspekten von DAX-Formeln bekannt gemacht. Erstens enthielt diese Formel zwei Funktionen. Beachten Sie, dass [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) eine Zeitintelligenzfunktion ist, die als Argument verschachtelt ist, das an die Filterfunktion [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx) übergeben wird. DAX-Formeln können bis zu 64 geschachtelte Funktionen enthalten. Es ist unwahrscheinlich, dass eine Formel jemals so viele verschachtelte Funktionen enthalten sollte. Eine solche Formel wäre tatsächlich sehr schwer zu erstellen und zu debuggen, und wahrscheinlich wäre sie auch nicht sehr schnell.

In dieser Formel haben Sie außerdem Filter verwendet. Filter grenzen den zu berechnenden Bereich ein. In diesem Fall haben Sie einen Filter als Argument ausgewählt, der tatsächlich das Ergebnis einer weiteren Funktion ist. Sie erfahren später noch mehr über Filter.

Schließlich haben Sie die Funktion CALCULATE verwendet. Dies ist eine der leistungsstärksten Funktionen in DAX. Beim Erstellen von Modellen und komplexeren Formeln werden Sie diese Funktion wahrscheinlich viele Male verwenden. Die Erörterung der Funktion CALCULATE würde den Rahmen dieses Artikels sprengen, Sie sollten ihr mit wachsendem Wissen über DAX aber besondere Aufmerksamkeit schenken.

### <a name="syntax-quickquiz"></a>Syntax-Kursquiz
1. Wozu dient diese Schaltfläche auf der Bearbeitungsleiste?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Was umgibt immer einen Spaltennamen in einer DAX-Formel?

Die Antworten finden Sie am Ende dieses Artikels.

### <a name="functions"></a>Funktionen
Funktionen sind vordefinierte Formeln, die Berechnungen ausführen, indem sie bestimmte Werte, die Argumente genannt werden, in einer bestimmten Reihenfolge oder Struktur verwenden. Als Argumente können andere Funktionen, eine andere Formel, ein Ausdruck, Spaltenverweise, Zahlen, Text, logische Werte wie WAHR oder FALSCH oder Konstanten dienen.

DAX enthält die folgenden Kategorien von Funktionen: [Datum und Uhrzeit](https://msdn.microsoft.com/library/ee634786.aspx), [Zeitintelligenz](https://msdn.microsoft.com/library/ee634763.aspx), [Information](https://msdn.microsoft.com/library/ee634552.aspx), [Logisch](https://msdn.microsoft.com/library/ee634365.aspx), [Mathematisch](https://msdn.microsoft.com/library/ee634241.aspx), [Statistisch](https://msdn.microsoft.com/library/ee634822.aspx), [Text](https://msdn.microsoft.com/library/ee634938.aspx), [Über-/Untergeordnet](https://msdn.microsoft.com/library/mt150102.aspx) sowie [sonstige](https://msdn.microsoft.com/library/mt150101.aspx) Funktionen. Wenn Sie mit Funktionen in Excel-Formeln vertraut sind, werden Ihnen viele der Funktionen in DAX ähnlich vorkommen; Sie sind jedoch in diesen Punkten einzigartig:

* Eine DAX-Funktion verweist immer auf eine gesamte Spalte oder eine Tabelle. Wenn Sie nur bestimmte Werte aus einer Tabelle oder Spalte verwenden möchten, können Sie der Formel Filter hinzufügen.
* Wenn Sie Berechnungen zeilenweise anpassen müssen, bietet DAX Funktionen, bei denen Sie den Wert der aktuellen Zeile oder einen damit zusammenhängenden Wert als eine Art Argument verwenden können, um Berechnungen durchzuführen, die sich je nach Kontext unterscheiden. Sie erfahren später noch mehr über Kontext.
* DAX beinhaltet zahlreiche Funktionen, die eine Tabelle anstelle eines Werts zurückgeben. Die Tabelle wird nicht angezeigt, wird aber verwendet, um die Eingabe für andere Funktionen bereitzustellen. Beispielsweise können Sie eine Tabelle abrufen und dann die diskreten Werte darin zählen oder dynamische Summen über gefilterte Tabellen oder Spalten berechnen.
* DAX beinhaltet eine Vielzahl von Zeitintelligenzfunktionen. Mit diesen Funktionen können Sie Datumsbereiche definieren oder auswählen und dynamische Berechnungen auf ihrer Grundlage durchführen. Beispielsweise können Sie Summen über parallele Zeiträume vergleichen.
* Excel verfügt über eine sehr beliebte Funktion, SVERWEIS. DAX-Funktionen nehmen keine Zelle oder einen Zellbereich als Verweis an, wie SVERWEIS in Excel. DAX-Funktionen nehmen eine Spalte oder eine Tabelle als Verweis an. Bedenken Sie, dass Sie in Power BI Desktop mit einem relationalen Datenmodell arbeiten. Das Nachschlagen von Werten in einer anderen Tabelle ist wirklich recht einfach, und in den meisten Fällen müssen Sie dafür gar keine Formel erstellen.
  
  Wie Sie sehen können, können Funktionen in DAX Ihnen beim Erstellen sehr leistungfähiger Formeln helfen. Wir haben wirklich gerade eben nur die Grundlagen von Funktionen berührt. Mit wachsenden DAX-Fertigkeiten erstellen Sie Formeln, die viele verschiedene Funktionen verwenden. Eine der besten Quellen für Details zu jeder der DAX-Funktionen ist die [DAX-Funktionsreferenz](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>Funktionen-Kurzquiz
1. Worauf verweist eine Funktion in jedem Fall?
2. Kann eine Formel mehr als eine Funktion enthalten?
3. Welche Kategorie von Funktionen würden Sie verwenden, um zwei Textzeichenfolgen zu einer Zeichenfolge zu verketten?

Die Antworten finden Sie am Ende dieses Artikels.

### <a name="context"></a>Kontext
Kontext ist eins der wichtigsten Konzepte für das Verständnis von DAX. Es gibt zwei Arten von Kontext in DAX; Zeilenkontext und Filterkontext. Wir betrachten zuerst den Zeilenkontext.

**Zeilenkontext**

Den Zeilenkontext kann man sich am einfachsten als die aktuelle Zeile vorstellen. Er gilt immer, wenn eine Funktion eine Formel aufweist, die Filter anwendet, um eine einzelne Zeile in der Tabelle zu identifizieren. Die Funktion wendet inhärent einen Zeilenkontext für jede einzelne Zeile der Tabelle an, die sie filtert. Diese Art Zeilenkontext betrifft meistens Measures.

**Filterkontext**

Filterkontext ist ein bisschen schwieriger zu verstehen als Zeilenkontext. Sie können sich einen Filterkontext am einfachsten so vorstellen: Ein oder mehrere Filter werden in einer Berechnung angewendet, die ein Ergebnis oder einen Wert bestimmt.

Filterkontext ersetzt Zeilenkontext nicht, er gilt vielmehr zusätzlich zum Zeilenkontext. Um beispielsweise die in eine Berechnung aufzunehmenden Werte weiter einzugrenzen, können Sie einen Filterkontext anwenden, der nicht nur den Zeilenkontext, sondern auch einen bestimmten Wert (Filter) in diesem Zeilenkontext angibt.

Ein Filterkontext lässt sich in Ihren Berichten leicht erkennen. Wenn Sie z. B. einer Visualisierung „TotalCost“ (Gesamtkosten) hinzufügen und dann „Year“ und „Region“, definieren Sie einen Filterkontext, der eine Teilmenge der Daten auf der Basis eines bestimmten Jahrs und einer bestimmten Region auswählt.

Warum ist der Filterkontext so wichtig für DAX? Zwar kann ein Filterkontext am einfachsten durch Hinzufügen von Feldern zu einer Visualisierung angewendet werden, er kann jedoch auch in einer DAX-Formel durch Definieren eines Filters mithilfe von Funktionen wie ALL, RELATED, FILTER, CALCULATE, durch Beziehungen und andere Measures und Spalten angewendet werden. Sehen wir uns als Beispiel die folgende Formel in einem Measure mit dem Namen „Store Sales“ (Ladenumsätze) an:

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Um diese Formel besser zu verstehen, können wir sie aufgliedern, wie andere Formeln auch.

Diese Formel beinhaltet die folgenden Syntaxelemente:

**A.** Den Measurenamen **Store Sales**.

**B.** Der Gleichheitszeichenoperator ( **=** ) kennzeichnet den Anfang der Formel.

**C.** Die Funktion **CALCULATE** wertet einen Ausdruck als Argument in einem Kontext aus, der durch die angegebenen Filter verändert wird.

**D.** Klammern **()** umschließen einen Ausdruck, der ein oder mehrere Argumente enthält.

**E.** Ein Measure **[Total Sales]** in derselben Tabelle wie ein Ausdruck. Das Measure „Total Sales“ hat die Formel: =SUM(Sales[SalesAmount]).

**F.** Ein Komma ( **,** ) trennt das erste Ausdrucksargument vom Filterargument.

**G.** Die vollqualifizierte referenzierte Spalte **Channel[ChannelName]** . Dies ist unser Zeilenkontext. Jede Zeile in dieser Spalte bezeichnet einen Kanal: „Store“, „Online“ usw.

**H.** Der Einzelwert **Store** als Filter. Dies ist unser Filterkontext.

Diese Formel stellt sicher, dass nur Umsatzwerte, die durch das Measure „Total Sales“ definiert sind, nur für die Zeilen in der Spalte „Channel[ChannelName]“, die den Wert „Store“ als Filter aufweisen, berechnet werden.

Sie können sich sicher vorstellen, dass die Möglichkeit, Filterkontexte innerhalb einer Formel zu definieren, ungeheuer leistungsfähige Möglichkeiten bietet. Die Möglichkeit, in einer zugeordneten Tabelle nur auf einen bestimmten Wert zu verweisen, ist dafür nur ein Beispiel. Machen Sie sich keine Gedanken, wenn Sie Kontext nicht auf Anhieb voll und ganz verstehen. Wenn Sie eigene Formeln erstellen, werden Sie Kontext und dessen Bedeutung in DAX besser verstehen.

### <a name="context-quickquiz"></a>Kontext-Kurzquiz
1. Welche zwei Arten von Kontext gibt es?
2. Was ist Filterkontext?
3. Was ist Zeilenkontext?

Die Antworten finden Sie am Ende dieses Artikels.

## <a name="summary"></a>Zusammenfassung
Jetzt, da Sie über ein grundlegendes Verständnis der wichtigsten Konzepte in DAX verfügen, können Sie beginnen, auf eigene Faust DAX-Formeln für Measures zu erstellen. DAX ist ein bisschen schwierig zu lernen, Ihnen stehen aber viele Ressourcen zur Verfügung. Nach dem Lesen dieses Artikels und ein paar Experimenten mit eigenen Formeln können Sie mehr über andere DAX-Konzepte und -Formeln lernen, die Ihnen beim Lösen Ihrer Geschäftsprobleme helfen können. Ihnen stehen viele DAX-Ressourcen zur Verfügung. Am wichtigsten ist die [DAX-Referenz (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx).

DAX ist schon seit mehreren Jahren in anderen Microsoft BI-Tools anzutreffen, wie Power Pivot und tabellarischen Modellen von Analysis Services, daher stehen gute Informationen in großer Menge zur Verfügung. Sie finden weitere Informationen in Büchern, Whitepapers und Blogs sowohl von Microsoft als auch von führenden BI-Experten. Das [DAX Resource Center Wiki auf TechNet](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) ist ebenfalls ein hervorragender Ausgangspunkt.

### <a name="quickquiz-answers"></a>Kurzquiz-Antworten
Syntax:

1. Überprüft das Measure und gibt es in das Modell ein.
2. Eckige Klammern [].

Funktionen:

1. Eine Tabelle und eine Spalte.
2. Ja. Eine Formel kann bis zu 64 verschachtelte Funktionen aufweisen.
3. [Textfunktionen](https://msdn.microsoft.com/library/ee634938.aspx).

Kontext:

1. Zeilenkontext und Filterkontext.
2. Ein oder mehrere Filter in einer Berechnung, die einen einzelnen Wert bestimmt.
3. Die aktuelle Zeile.

