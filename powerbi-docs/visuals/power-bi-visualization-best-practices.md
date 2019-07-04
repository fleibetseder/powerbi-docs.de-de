---
title: Bewährte Entwurfsmethoden für Berichte und Visualisierungen
description: Ein Artikel über bewährte Methoden für das Entwerfen von Berichten in Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7d716c79146a0d53d261dba514aacb8787ca2fa3
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299728"
---
# <a name="best-design-practices-for-reports-and-visuals"></a>Bewährte Entwurfsmethoden für Berichte und Visualisierungen

Dieser Artikel beschreibt bewährte Methoden für das Entwerfen von Berichten in Power BI. Entwurfsgrundlagen und -verfahren werden beschrieben, die Sie für Ihre Berichte sowie für die Seiten und einzelnen visuellen Elemente der Berichte verwenden können. Viele dieser bewährten Methoden gelten auch für das Entwerfen von Dashboards.

> [!NOTE]
> Die Empfehlungen in diesem Artikel sollen als Richtlinien dienen, die Sie anwenden können, wann und wo dies sinnvoll ist. Für jedes unten beschriebene Verfahren gibt es häufig auch Gründe für das „Brechen der Regeln“.

Wir hoffen, dass dieser Artikel eine gute Ausgangsbasis für Sie darstellt, indem Sie das Gelernte auf Ihre eigenen Berichte und Visualisierungen anwenden, und dass Sie sich mit Beiträgen an der [Microsoft Power BI-Community](http://community.powerbi.com/) beteiligen. BI-Berichtsentwurf und Visualisierung sind derzeit ein aktuelles Thema. Es gibt viele Vordenker, Blogger und Websites, die den Entwurf von BI-Berichten in allen Dimensionen behandeln. Wir haben ein paar am Ende dieses Artikels aufgeführt.

> *Wir werden mit Informationen überhäuft. Es sind nicht zu viele Informationen, aber wir wissen nicht, wie wir sie bewältigen sollen.*
-- Stephen Few

## <a name="a-look-at-the-landscape-and-terminology"></a>Betrachtung der Designlandschaft und Terminologie

In Power BI kann ein Bericht eine oder mehrere Seiten enthalten. Alle Seiten zusammen werden zusammen als Bericht bezeichnet. Die grundlegenden Elemente des Berichts sind visuelle Elemente (auch Visualisierungen genannt), separate Abbildungen und Textfelder. Von den einzelnen Datenpunkten über die Berichtselemente bis zur Berichtsseite selbst gibt es viele verschiedene Formatierungsoptionen.

Wir beginnen mit der Phase der Berichtsplanung, fahren dann mit den Grundlagen des Berichtsentwurfs und den Grundlagen für den Entwurf von visuellen Elementen fort und beschreiben abschließend die bewährten Methoden für bestimmte Arten von visuellen Elementen.

Ausführliche Anleitungen und Hilfeinformationen zum Erstellen und Verwenden von Power BI-Berichten finden Sie unter [Power BI erlernen](https://powerbi.microsoft.com/learning/).

## <a name="before-you-build-your-first-visualization-focus-on-requirements"></a>Vor der Erstellung der ersten Visualisierung: Konzentration auf die Anforderungen

Die Erstellung eines Berichts beginnt vor dem Erstellen des ersten visuellen Elements. Ein guter Bericht setzt Planung voraus. Sie sollten wissen, mit welchen Daten Sie arbeiten müssen, und eine Liste mit den Anforderungen für den Bericht erstellen. Stellen Sie sich diese Fragen:

* Wie sieht die geschäftliche Anforderung aus?

* Wie werden die Leser diese Daten verwenden?

* Wer wird diese Daten verwenden?

* Welche Entscheidungen möchte der Leser anhand dieses Berichts treffen können?

Die Antworten auf diese Fragen stellen die Grundlage Ihres Entwurfs dar. Mit jedem Bericht wird eine „Geschichte“ erzählt. Stellen Sie sicher, dass die Geschichte an der geschäftlichen Anforderung ausgerichtet ist. Es kann verlockend sein, visuelle Elemente hinzuzufügen, mit denen eindrucksvolle Erkenntnisse veranschaulicht werden. Wenn diese Erkenntnisse aber nicht zur geschäftlichen Anforderung passen, ist der Bericht nicht hilfreich. Sie könnten Ihre Benutzer mit diesen visuellen Elementen tatsächlich ablenken. Sie könnten auch feststellen, dass Sie die zum Treffen dieser Entscheidung notwendigen Informationen diesen Daten nicht entnehmen können. Können mit diesem Bericht messen, was Sie messen möchten?

Sie können Berichte zum Überwachen, Aufdecken, Nachverfolgen, Vorhersagen, Messen, Verwalten, Testen usw. verwenden. Die geschäftliche Anforderung ist z.B. ein Verkaufsbericht, der Leistung misst. Sie könnten einen Bericht entwerfen, der Folgendes leistet: Ermitteln des aktuellen Umsatzes, Vergleichen mit vorherigem Umsatz, Vergleichen mit Wettbewerbern und Nutzen von KPIs zum Auslösen von Warnungen. Es kann beispielsweise sein, dass Leser die ausführlichen Verkaufszahlen anzeigen können, um sich über Geschäftsschließungen oder Lieferkettenprobleme zu informieren, die sich ggf. auf den Umsatz auswirken. Eine weitere Drilldownoption kann darin bestehen, den Umsatz nach Geschäft, Region, Produkt, Jahreszeit usw. anzuzeigen.

Machen Sie sich klar, für welche Kunden der Bericht bestimmt ist. Entwerfen Sie einen Bericht, in dem vertraute Terminologie verwendet wird, und der Daten mit dem Detail- bzw. Komplexitätsgrad enthält, der für den Wissensstand der Kunden geeignet ist. Haben Sie mehrere Typen von Kunden? Eine Größe passt nicht immer allen. Entwerfen Sie separate Berichtsseiten, die auf der Erfahrung basieren. Achten Sie darauf, jede Seite eindeutig zu bezeichnen, damit sie für Kunden selbsterklärend ist. Eine andere Möglichkeit ist die Verwendung von Datenschnitten (Slicern), damit Kunden die Seite je nach Bedarf anpassen können. Beziehen Sie Kunden in die Planungsphase ein, und vermeiden Sie es zu glauben, dass Sie bereits wissen, was benötigt wird. Wenn Sie diesen Fehler machen, bereiten Sie sich darauf vor, von vorne anzufangen und den Vorgang zu wiederholen.

Nachdem Sie die geschäftliche Anforderung, die Kunden und die einzubeziehenden Metriken ermittelt haben, umfasst der nächste Schritt das Auswählen der richtigen visuellen Elemente zum Erzählen der Geschichte. Finden Sie heraus, wie Sie diese visuellen Elemente in möglichst effektiver Weise präsentieren. Wir beginnen mit einigen Grundlagen des Berichtsentwurfs.

## <a name="principles-of-report-design"></a>Grundlagen des Berichtsentwurfs

Der Platz auf einer Berichtsseite ist begrenzt, und eine der schwierigsten Aufgaben besteht darin, alle gewünschten Elemente unterzubringen – und dies trotzdem auf leicht verständliche Weise. Unterschätzen Sie auch nicht den Wert eines optisch ansprechenden Berichts. Es geht darum, das Gleichgewicht zwischen einem ansprechenden und einem nützlichen Bericht zu finden.

Als Nächstes geht es um die Punkte Layout, Klarheit und Ästhetik.

### <a name="layout-of-the-report-canvas"></a>Layout des Zeichenbereichs des Berichts

Der Platz im Zeichenbereich (Canvas) des Berichts ist begrenzt. Unterteilen Sie den Bericht in mehrere Seiten, falls nicht alle Elemente auf eine Berichtsseite passen. Sie können eine Berichtsseite einer bestimmten Zielgruppe anpassen (z.B. HR, IT, Vertrieb, SLT). Wenn Sie möchten, passen Sie sie einer bestimmten Geschäftsanforderung an:

* „Welchen Einfluss haben Defekte auf unsere Downtime?“

* „Welchen Einfluss hat unsere Marketingkampagne auf die Stimmungslage?“

Eine fortschreitende Geschichte kann der bessere Ansatz sein. Vielleicht bietet die erste Seite eine Übersicht oder einen „Aufhänger“, der die Aufmerksamkeit erregt, die zweite Seite setzt die Datengeschichte fort, die dritte Seite vertieft die Geschichte usw. Wenn der gesamte Bericht auf eine Seite passt: umso besser. Falls nicht, ist es ratsam, separate Berichtsseiten zu erstellen, auf denen der Inhalt in logische Blöcke unterteilt ist. Denken Sie auch daran, für die Seiten aussagekräftige und hilfreiche Namen zu verwenden.

Stellen Sie sich dies wie die Einrichtung einer Kunstausstellung vor. Sie würden nicht 50 Kunstobjekte in einem kleinen Raum anordnen, Stühle aufstellen und jede Wand in einer anderen Farbe streichen. Als Kurator würden Sie nur Teile mit gemeinsamer Thematik auswählen. Sie würden sie im Raum verteilen und darauf achten, dass die Besucher viel Bewegungsspielraum haben und zum Nachdenken angeregt werden. Sie können sogar Informationskarten platzieren, die beschreiben, was sie sehen. Dass die meisten modernen Galerien weiße bzw. einfarbige Wände haben, hat einen guten Grund!

In diesem Artikel beginnen wir mit einem Beispiel für einen Bericht, für den viele Arbeitsschritte erforderlich sind, um ein gutes Ergebnis zu erhalten. Wenn wir nach und nach die bewährten Methoden und Entwurfsgrundlagen anwenden, verbessert sich die Qualität des Berichts.

![Diese wenig ansprechende Berichtsseite muss umfassend bearbeitet werden.](media/power-bi-visualization-best-practices/power-bi-example1newa.png)

**Abbildung 1: Für diese wenig ansprechende Berichtsseite ist eine umfangreiche Bearbeitung erforderlich.**

Das obige Beispiel weist viele platzbezogene Entwurfsprobleme (Layoutprobleme) auf, die im Folgenden beschrieben werden:

* Ausrichtung, Reihenfolge und Abstände

* Fehlerhafte Nutzung des Platzes und der Sortierung

* Unübersichtlichkeit

### <a name="alignment-order-and-proximity"></a>Ausrichtung, Reihenfolge und Abstände

Das Layout von Berichtselementen hat eine Auswirkung auf das Verständnis und leitet den Leser durch die Berichtsseite. Durch die Art und Weise der Anordnung und Positionierung von Elementen wird eine Geschichte erzählt. Die Aussage kann beispielsweise „Hier beginnen und dann hier fortfahren“ oder „Diese drei Elemente gehören zusammen“ lauten.

* In vielen Kulturen lesen Benutzer von links nach rechts und von oben nach unten. Ordnen Sie das wichtigste Element oben links im Bericht an. Platzieren Sie die restlichen visuellen Elemente so, dass sich eine logische Navigation und ein logisches Verständnis der Informationen ergibt.

* Ordnen Sie Elemente, bei denen der Leser eine Wahl treffen muss, links von den Visualisierungen an, auf die sich die Wahl auswirkt, z.B. bei Datenschnitten.

* Platzieren Sie zusammengehörige Elemente nah beieinander. Geringe Abstände betonen die Beziehung der Elemente.

* Eine weitere Möglichkeit zum Vermitteln von Beziehungen ist das Einfügen eines Rahmens oder farbigen Hintergrunds für eine Gruppe von Elementen. Sie können auch eine Trennlinie einfügen, um die bessere Unterscheidung zwischen unterschiedlichen Abschnitten eines Berichts zu ermöglichen.

* Verwenden Sie Leerraum, um die einzelnen Abschnitte der Berichtsseite visuell abzutrennen.

* Füllen Sie die Berichtsseite aus. Falls Ihnen zu viel Leerraum zur Verfügung steht, ist es oft ratsam, die Visualisierungen größer oder den Zeichenbereich kleiner zu machen.

* Wählen Sie die Größe der Berichtselemente mit Bedacht. Lassen Sie nicht zu, dass die Größe einer Visualisierung automatisch durch die Menge des verfügbaren Platzes vorgegeben wird.

* Machen Sie wichtige Elemente größer als andere, oder fügen Sie visuelle Elemente ein, z.B. einen Pfeil, um die Aufmerksamkeit auf etwas zu lenken.

* Richten Sie die Elemente auf der Berichtsseite entweder symmetrisch oder absichtlich asymmetrisch aus.

Wir gehen nun näher auf die Ausrichtung ein.

#### <a name="alignment"></a>Ausrichtung

Ausrichtung bedeutet nicht, dass die verschiedenen Komponenten dieselbe Größe aufweisen müssen. Sie bedeutet nicht, dass Sie in jeder Zeile des Berichts die gleiche Anzahl von Komponenten unterbringen müssen. Ausrichtung bedeutet lediglich, dass die Seite eine Struktur hat, die die leichte Navigation und Lesbarkeit fördert.

Im aktualisierten Bericht sehen wir, dass wir die Berichtskomponenten am linken und rechten Rand ausgerichtet haben. Wir haben auch jede Berichtszeile horizontal und vertikal ausgerichtet. Unsere Datenschnitte sind links von den visuellen Elementen angeordnet, auf die sie sich auswirken.

![Unser Beispiel für einen wenig ansprechenden Bericht mit Layoutverbesserungen.](media/power-bi-visualization-best-practices/power-bi-example2new.png)

**Abbildung 2: Unser Beispiel für einen wenig ansprechenden Bericht mit Layoutverbesserungen**

Power BI enthält Tools, die Sie beim Ausrichten der visuellen Elemente unterstützen. Wenn Sie in Power BI Desktop mehrere visuelle Elemente markiert haben, können Sie im Menüband auf der Registerkarte **Visuelle Elemente** die Optionen **Ausrichten** und **Verteilen** verwenden, um die Position von visuellen Elementen anzugleichen.

![Ausrichten von visuellen Elementen in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization.png)

**Abbildung 3a: Ausrichten von visuellen Elementen in Power BI Desktop**

![Ausrichten von visuellen Elementen in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-visualization-pbi-service.png)

**Abbildung 3b: Ausrichten von visuellen Elementen im Power BI-Dienst**

Im Power BI-Dienst und in Power BI Desktop haben Sie auch die genaue Kontrolle über die Größe und Position von visuellen Elementen. Dieses Steuerelement finden Sie auf der Registerkarte **Allgemein** im Bereich **Format** für alle visuellen Elemente:

![Festlegen der genauen Position für Ihre visuellen Elemente.](media/power-bi-visualization-best-practices/power-bi-align-vizs.png)

**Abbildung 4: Festlegen der genauen Position für Ihr Visual**

Auf der Berichtsseite in unserem Beispiel (Abbildung 2) richtet Power BI die beiden Karten und den großen Rahmen an der **X-Position** bei 200 aus.

#### <a name="fit-to-the-space"></a>Anpassen an den vorhandenen Platz

Nutzen Sie den vorhandenen Platz so gut wie möglich. Wenn Sie wissen, wie Personen den Bericht betrachten und anzeigen, entwerfen sie ihn dementsprechend. Reduzieren Sie den leeren Platz, um den Zeichenbereich auszufüllen. Versuchen Sie möglichst zu vermeiden, dass für einzelne visuelle Elemente Scrollleisten eingeblendet werden. Füllen Sie den Platz aus, ohne dass die einzelnen visuellen Elemente zu stark eingeengt sind.

##### <a name="adjust-the-page-size"></a>Anpassen der Seitengröße

Wenn Sie die Seitengröße verringern, erscheinen einzelne Elemente relativ zur gesamten Seite größer. Löschen Sie die Auswahl aller visuellen Elemente auf der Seite, und verwenden Sie im Bereich **Format** die Registerkarte **Seitengröße**.

Hier ist eine Berichtsseite dargestellt, für die einmal das Format **4:3** und dann das Format **16:9** gewählt wurde. Achten Sie darauf, dass 16:9 für das Layout deutlich besser geeignet ist. Es ist sogar so viel Platz vorhanden, dass die Scrollleiste für das zweite visuelle Element entfernt werden kann.

![Der Bericht mit einem Seitenverhältnis von 4:3.](media/power-bi-visualization-best-practices/power-bi-page-view-before.png)

**Abbildung 5a: Bericht mit einem Seitenverhältnis von 4:3**

![Der Bericht mit einem Seitenverhältnis von 16:9.](media/power-bi-visualization-best-practices/power-bi-page-view-after.png)

**Abbildung 5b: Der Bericht mit einem Seitenverhältnis von 16:9**

Wird Ihr Bericht in 4:3, 16:9 oder einem anderen Seitenverhältnis angezeigt? Auf kleinen oder großen Bildschirmen? Wird Ihr Bericht in allen möglichen Bildschirmformaten und -größen angezeigt? Berücksichtigen Sie dies beim Entwerfen.

Unsere Berichtsseite im Beispiel ist etwas überladen. Wenn kein visuelles Element ausgewählt ist:

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Erweitern Sie **Seitengröße**.

1. Wählen Sie für **Typ** die Option **Benutzerdefiniert** aus.

1. Ändern Sie **Höhe** in **900**.

    ![Vergrößern der Seitenhöhe.](media/power-bi-visualization-best-practices/power-bi-page-size.png)

**Abbildung 6: Vergrößern der Seitenhöhe**

#### <a name="reduce-clutter"></a>Verringern der Unübersichtlichkeit

Eine unübersichtliche Berichtsseite ist nur schwer schnell zu erfassen und kann so überwältigend wirken, dass die Leser gleich aufgeben. Entfernen Sie alle Berichtselemente, die nicht benötigt werden. Fügen Sie keine Features hinzu, die nicht dem Verständnis oder der Navigation dienen. Ihre Berichtsseite sollte die Informationen so eindeutig, schnell und zusammenhängend wie möglich vermitteln.

Edward Tufte bezeichnet dies in seinem Buch *The Visual Display of Quantitative Information* (Die visuelle Darstellung von quantitativen Informationen) als „data to ink ratio“ (Verhältnis von Daten zu „Tinte“). Dies bedeutet im Wesentlichen, dass alle unnötigen Elemente entfernt werden sollten.

Je mehr Sie die Unordnung beseitigen, desto größer wird der Leerraum auf Ihrer Berichtsseite. Sie erhalten mehr Platz für die Anwendung der Best Practices, die wir im Abschnitt [Ausrichtung, Reihenfolge und Abstände](#alignment-order-and-proximity) erörtert haben.

Unser Beispiel sieht schon besser aus. Wir haben die Unübersichtlichkeit beseitigt und Elemente durch die Verwendung passender Formen gruppiert. Das Hintergrundbild ist nicht mehr vorhanden, der überflüssige Pfeil und das Textfeld wurden entfernt, ein visuelles Element wurde auf eine andere Seite des Berichts verschoben usw. Außerdem haben wir die Seite verlängert, um mehr freie Fläche zu erhalten.

![Verbesserte Übersichtlichkeit des wenig ansprechenden Berichts.](media/power-bi-visualization-best-practices/power-bi-example3newer.png)

**Abbildung 7: Verbesserte Übersichtlichkeit des wenig ansprechenden Berichts**

### <a name="tell-a-story-at-a-glance"></a>Eine ganze Geschichte auf einen Blick

Der ultimative Test ist: Eine Person ohne Vorkenntnisse muss den Bericht schnell verstehen können, ohne dass sie eine Erklärung erhält. Leser können auf den ersten Blick erkennen, um was es auf der Seite und in den einzelnen Diagrammen und Tabellen geht.

Wenn Leser den Bericht anzeigen, sollten ihre Augen sich auf das Element konzentrieren, auf das sie zuerst schauen sollen. Ihren Augen bewegen sich von links nach rechts und von oben nach unten. Ändern Sie dieses Verhalten, indem Sie visuelle Anhaltspunkte wie Textfeldbeschriftungen, Formen, Rahmen und verschiedene Größen und Farben einsetzen.

#### <a name="text-boxes"></a>Textfelder

In einigen Fällen reichen die Titel der Visualisierungen nicht aus, um die Geschichte zu erzählen. Fügen Sie Textfelder hinzu, um mit den Benutzern zu kommunizieren, die Ihre Berichte anzeigen. Beschreiben Sie mit Textfeldern eine Berichtsseite, eine Gruppe von visuellen Elementen oder ein einzelnes visuelles Element. Sie erläutern Ergebnisse oder definieren ein visuelles Element, Komponenten in visuellen Elementen oder Beziehungen zwischen visuellen Elementen besser. Mithilfe von Textfeldern können Sie die Aufmerksamkeit anhand von verschiedenen Kriterien auf bestimmte Dinge lenken.

Wählen Sie im Power BI-Dienst oben in der Menüleiste die Option **Textfeld**. (In Power BI Desktop: Wählen Sie im Menüband im Bereich **Einfügen** die Option **Textfeld**.)

![Hinzufügen eines Textfelds im Power BI-Dienst.](media/power-bi-visualization-best-practices/power-bi-text-boxes.png)

**Abbildung 8: Hinzufügen eines Textfelds im Power BI-Dienst**

Geben Sie Text in das leere Feld ein. Legen Sie dann mit den Steuerelementen Schriftart, Größe, Ausrichtung und Sonstiges fest. Verwenden Sie die Ziehpunkte, um die Größe des Felds zu ändern.

![Formatieren des Textfelds.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Abbildung 9: Formatieren des Textfelds**

Übertreiben Sie es aber nicht. Zu viel Text in einem Bericht lenkt von den visuellen Elementen ab. Falls sich herausstellt, dass sehr viel Text erforderlich ist, um Ihre Berichtsseite verständlich zu machen, sollten Sie neu anfangen. Ist es möglich, ein anderes visuelles Element zu wählen, das mehr Aussagekraft hat? Können Sie die nativen Titel des Visuals verbessern, um die Verständlichkeit zu fördern?

#### <a name="text"></a>Text

Erstellen Sie eine Stilvorgabe für Text, und wenden Sie diese Regeln auf allen Seiten des Berichts an. Wählen Sie nur ein paar Schriftarten, Textgrößen und Farben. Wenden Sie diese Stilvorgabe auf Textelemente an. Wenden Sie sie auch auf die Schriftarten an, die Sie in den Visualisierungen auswählen. Weitere Informationen finden Sie im Abschnitt [Titel und Beschriftungen in Visualisierungen](#titles-and-labels-that-are-part-of-the-visualizations). Legen Sie Regeln für die Verwendung von Fettdruck, Kursivschrift, größeren Schriftgraden, bestimmten Farben usw. fest. Versuchen Sie, Text in Großbuchstaben oder Unterstreichungen zu vermeiden.

#### <a name="shapes"></a>Formen

Auch Formen können zu einer besseren Navigation und zum Verständnis beitragen. Verwenden Sie Formen, um zusammengehörige Informationen zu gruppieren und wichtige Daten hervorzuheben, und setzen Sie Pfeile ein, um die Augen beim Lesen zu leiten. Formen dienen als Hilfe für Leser, damit sie wissen, wo sie beginnen sollen und wie der Bericht zu interpretieren ist. In der Designsprache wird dies häufig als *Kontrast* bezeichnet.

![Formen im Power BI-Dienst.](media/power-bi-visualization-best-practices/shapes.png)

**Abbildung 10a: Formen im Power BI-Dienst**

![Formen in Power BI Desktop.](media/power-bi-visualization-best-practices/power-bi-desktop-shapes2new.png)

**Abbildung 10b: Formen in Power BI Desktop**

Wie sieht unsere Beispielseite jetzt aus? Abbildung 11 zeigt eine aufgeräumtere und übersichtlichere Seite mit einheitlicher Nutzung von Schriftarten, Schriftgrößen und Farben. Der Seitentitel in der Ecke oben links informiert den Leser darüber, um was es auf der Seite geht.

![Berichtsbeispiel mit angewendeten Texthinweisen und hinzugefügtem Titel.](media/power-bi-visualization-best-practices/power-bi-example4new.png)

**Abbildung 11: Berichtsbeispiel mit angewendeten Texthinweisen und hinzugefügtem Titel**

Im Beispiel haben wir oben links einen Titel für die Berichtsseite eingefügt, also an der Stelle, auf die Leser zuerst schauen. Der Schriftgrad ist 28, und die Schriftart ist Segoe Bold, damit der Text gegenüber den anderen Seitenelementen hervorgehoben ist. Unsere Textstilvorgabe legt fest, dass keine Hintergründe verwendet werden, schwarze Titel, Legenden und Beschriftungen. Wir haben das nach Möglichkeit auf alle visuellen Elemente der Seite angewendet (die Achsen und Bezeichnungen des Kombinationsdiagramms sind nicht editierbar). Außerdem wurden diese Elemente gemäß der Spezifikationen der Stilvorgabe konfiguriert:

* Karten: **Kategoriebeschriftung** festgelegt auf **Aus**, **Titel** festgelegt auf **Ein**, 12 Punkt, schwarz und zentriert.

* Titel von visuellen Elementen: Wenn auf **Ein** gesetzt, auf 12 Punkt und linksbündig festgelegt.

* Slicer: **Kopfzeile** auf **Aus** und **Titel** auf **Ein** festgelegt. Behalten Sie für **Elemente** > **Text** die Einstellung „Grau“ und „10 Punkt“ bei.

* Punkt- und Säulendiagramme: Schwarze Schrift für X- und Y-Achsen und Titel von X- und Y-Achsen, falls zutreffend.

#### <a name="color"></a>Farbe

Verwenden Sie Farben, um die Einheitlichkeit sicherzustellen. Auf diesen Punkt gehen wir später unter [Grundlagen des Entwurfs von visuellen Elementen](#principles-of-visual-design) näher ein. Wir reden hier über die sorgfältige Auswahl Ihrer Farbe. Die Farbe soll die Fähigkeit des Lesers, Ihren Bericht schnell zu verstehen, nicht beeinträchtigen. Zu viele grelle Farben können störend wirken. Dieser Abschnitt enthält eher Informationen dazu, was Sie in Bezug auf Farbe nicht tun sollten.

#### <a name="backgrounds"></a>Hintergründe

Wählen Sie beim Festlegen von Hintergründen für Berichtsseiten keine Farben, die den Bericht verdüstern, die nicht zu den anderen Farben auf der Seite passen oder deren Anblick wehtut. Beachten Sie auch, dass einige Farben mit bestimmten Bedeutungen behaftet sind. In den USA wird die Farbe Rot in einem Bericht normalerweise für etwas Negatives verwendet.

![Festlegen des Hintergrunds für den Bericht.](media/power-bi-visualization-best-practices/power-bi-page-background.png)

**Abbildung 12: Festlegen des Hintergrunds für den Bericht**

Die Aufgabe besteht nicht darin, ein Kunstwerk zu erstellen, sondern einen funktionellen Bericht. Wählen Sie eine Farbe, mit der die Lesbarkeit und Hervorhebung der Berichtselemente verbessert wird. Eine Studie über die Verwendung von Farbe und Visualisierungen innerhalb von Webseiten ergab, dass ein höherer Kontrast zwischen den Farben das Verständnis erleichtert. Zwei Whitepapers behandeln dieses Thema:

* [The effect of text and background color on visual search of Web pages](https://www.sciencedirect.com/science/article/pii/S0141938202000410) (Die Auswirkung von Text- und Hintergrundfarbe auf das visuelle Durchsuchen von Webseiten)

* [Determining Users’ Perception of Web Page Visual Complexity and Aesthetic Characteristics](https://www.researchgate.net/publication/301362579_Determining_Users'_Perception_of_Web_Page_Visual_Complexity_and_Aesthetic_Characteristics) (Bestimmung der Wahrnehmung der visuellen Komplexität und ästhetischen Merkmale einer Webseite durch Benutzer)

Wir haben einige bewährte Methoden für den Einsatz von Farben auf unseren Beispielbericht angewendet (siehe Abbildungen 20 und 21). Der wichtigste Punkt ist, dass wir die Hintergrundfarbe in Schwarz geändert haben. Gelb war zu grell und eine Belastung für die Augen. Außerdem lief der gelbe Teil der Balken im Diagramm **Count of athlete name by year and class** in den gelben Hintergrund. Bei Verwendung eines schwarzen (oder weißen) Hintergrunds ist der Kontrast am größten, und die Aufmerksamkeit wird auf die visuellen Elemente geleitet.

Wir haben die folgenden zusätzlichen Schritte ausgeführt, um den Beispielbericht zu verbessern:

#### <a name="page-title"></a>Seitentitel

Als wir den Hintergrund auf die Farbe Schwarz festgelegt haben, war der Titel nicht mehr zu sehen, weil im Textfeld nur schwarze Schrift zulässig ist. Fügen Sie stattdessen einen Textfeldtitel ein, um dieses Problem zu beheben:

1. Wählen Sie das Textfeld aus, und löschen Sie den Text.

1. Wählen Sie auf der Registerkarte **Visualisierungen** den **Titel** aus, und setzen Sie ihn auf **Ein**.

1. Wählen Sie den Pfeil aus, um die Optionen für den **Titel** zu erweitern.

1. Geben Sie **Summer Olympic Games** in das Feld **Titeltext** ein.

1. Wählen Sie für **Schriftfarbe** die Farbe „Weiß“ aus.

    ![Hinzufügen eines Seitentitels.](media/power-bi-visualization-best-practices/power-bi-text-box-title.png)

    **Abbildung 13: Hinzufügen eines Seitentitels**

#### <a name="cards"></a>Karten

Für die visuellen Kartenelemente:

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Legen Sie für **Hintergrund** die Option **Ein** fest.

1. Wählen Sie die Farbe Weiß mit einer **Transparenz** von **0%** aus.

    ![Karten-Hintergrundfarben.](media/power-bi-visualization-best-practices/power-bi-card-background.png)

1. Wählen Sie dann für **Titel** die Option **Ein** aus.

1. Wählen Sie für **Schriftfarbe** „Weiß“ und für **Hintergrundfarbe** „Schwarz“ aus.

    ![Kartentitelfarben.](media/power-bi-visualization-best-practices/power-bi-card-title.png)

#### <a name="slicers"></a>Datenschnitte

Bis zu diesem Punkt wiesen die beiden Datenschnitte eine unterschiedliche Formatierung auf. Das ist nicht sinnvoll. Für beide Datenschnitte: 

1. Ändern Sie die Hintergrundfarbe in „Aquamarin“.

    ![Ändern Sie die Hintergrundfarbe der Datenschnitte.](media/power-bi-visualization-best-practices/power-bi-slicer-background.png)

    **Abbildung 14: Ändern der Hintergrundfarbe für den Slicer**

    Die Farbe Aquamarin ist eine gute Wahl, da sie in der Farbpalette der Seite enthalten ist. Sie ist im Flächenkartogramm, in der Strukturkarte und im Säulendiagramm zu sehen.

1. Fügen Sie einen dünnen weißen Rahmen hinzu.

    ![Hinzufügen eines Rahmens für den Datenschnitt.](media/power-bi-visualization-best-practices/power-bi-slicer-outline.png)

    **Abbildung 15: Hinzufügen eines Rahmens für den Slicer**

1. Die graue Farbe ist auf dem Aquamarin-Hintergrund nicht gut zu sehen. Ändern Sie die Farbe für **Elemente** daher in Weiß.

    ![Ändern der Schriftfarbe des Datenschnitts.](media/power-bi-visualization-best-practices/power-bi-slicer-items.png)

    **Abbildung 16: Ändern der Schriftfarbe des Slicers**

1. Ändern Sie abschließend unter **Titel** die Option **Schriftfarbe** in „Weiß“, und legen Sie für **Hintergrundfarbe** „Schwarz“ fest.

    ![Formatieren des Titels für den Datenschnitt.](media/power-bi-visualization-best-practices/power-bi-card-formatting.png)

    **Abbildung 17: Formatieren des Titels für den Slicer**

#### <a name="rectangle-shape"></a>Rechteckige Form

Auch das Rechteck ist auf dem schwarzen Hintergrund nicht mehr sichtbar. So beheben Sie dieses Problem:

1. Wählen Sie die Form aus.

1. Setzen Sie im Bereich **Form formatieren** den Schieberegler für **Hintergrund** auf **Ein**.

    ![Formatieren der Form](media/power-bi-visualization-best-practices/power-bi-shape-format.png)

    **Abbildung 18: Formatieren der Form**

#### <a name="column-charts-bubble-chart-filled-map-and-treemap"></a>Säulendiagramme, Blasendiagramm, Flächenkartogramm und Strukturkarte

Fügen Sie den restlichen visuellen Elementen auf der Berichtsseite einen weißen Hintergrund hinzu. Im Bereich **Format**:

1. Erweitern Sie die Option **Hintergrund**.

1. Legen Sie die **Farbe** „Weiß“ fest.

1. Setzen Sie die **Transparenz** auf 0.

    ![Hinzufügen eines weißen Hintergrunds für die restlichen Visualisierungen.](media/power-bi-visualization-best-practices/power-bi-background.png)

    **Abbildung 19: Hinzufügen eines weißen Hintergrunds für die restlichen Visualisierungen**

So sieht der Bericht aus, nachdem Sie ihn neu formatiert haben:

![Berichtsbeispiel mit Anwendung von bewährten Methoden für Farbe (schwarzer Hintergrund).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Abbildung 20: Berichtsbeispiel mit Anwendung von bewährten Methoden für Farbe (schwarzer Hintergrund)**

![Berichtsbeispiel mit Anwendung von bewährten Methoden für Farbe (weißer Hintergrund)](media/power-bi-visualization-best-practices/power-bi-example5b.png)

**Abbildung 21: Berichtsbeispiel mit Anwendung von bewährten Methoden für Farbe (weißer Hintergrund)**

### <a name="aesthetics"></a>Ästhetik

Viele Aspekte der Ästhetik haben wir oben bereits genannt: Ausrichtung, Farbe, Schriftart und Übersichtlichkeit. Ein paar weitere Best Practices für die Berichtsgestaltung sind es wert, diskutiert zu werden. Sie betreffen das Gesamtbild des Berichts.

Denken Sie daran, dass die Aufgabe des Berichts darin besteht, eine geschäftliche Anforderung zu erfüllen, und nicht darin, besonders hübsch auszusehen. Ein gewisses Maß an gutem Design ist erforderlich. Dies gilt vor allem für den ersten Eindruck. Nashville-Berater Tony Bodoh meint: „Die Gefühlsregung tritt eine halbe Sekunde vor der logischen Erkenntnis ein.“ Leser reagieren auf Ihre Berichtsseite zuerst auf emotionaler Ebene. Dann nehmen sie sich die Zeit, tiefer einzusteigen. Wenn die Seite unorganisiert, verwirrend und unprofessionell aussieht, kann es gut sein, dass die Leser die Bedeutung der Geschichte gar nicht erst erkennen.

Der Blogger und TechTarget-Branchenanalyst Wayne Eckerson hat hierzu eine schöne Analogie. Das Entwerfen eines Berichts ist wie das Einrichten eines Zimmers. Im Laufe der Zeit kaufen Sie eine Vase, ein Sofa, einen Beistelltisch und ein Gemälde. Diese Elemente liegen Ihnen alle am Herzen. Auch wenn jedes einzelne Stück sinnvoll ist, kann es trotzdem sein, dass sie nicht zusammenpassen oder um die Aufmerksamkeit des Betrachters konkurrieren.

Konzentrieren Sie sich auf Folgendes:

* Erstellen Sie ein einheitliches Design oder Erscheinungsbild für den Bericht zur Anwendung auf alle Berichtsseiten.

* Verwenden Sie eigenständige Bilder und andere Grafiken zur Unterstützung der Geschichte – und nicht als Ablenkung.

* Wenden Sie alle bewährten Methoden an, die in diesem Artikel bisher beschrieben wurden.

## <a name="principles-of-visual-design"></a>Grundlagen des Entwurfs von visuellen Elementen

Wir haben die Grundlagen des Berichtsentwurfs beschrieben und das Organisieren der Berichtselemente mit der Zielsetzung, den Bericht schnell und leicht verständlich zu machen. Nun geht es um die Entwurfsgrundlagen für die eigentlichen visuellen Elemente. Im nächsten Abschnitt werden die einzelnen visuellen Elemente dann näher beschrieben und die bewährten Methoden für einige häufig verwendete Elemente erläutert.

Wir lassen unser Beispiel für die Berichtsseite beiseite und sehen uns andere Beispiele an. Nachdem wir die Grundlagen des Entwurfs von visuellen Elementen abgehandelt haben, kehren wir zur Berichtsseite aus dem Beispiel zurück und wenden das Gelernte an. Wir bieten Schrittanleitungen.

### <a name="planning--choose-the-right-visual"></a>Planung – Auswählen des richtigen visuellen Elements

Ebenso wichtig wie das Planen des Berichts vor dem Beginn der Erstellung ist das Planen der einzelnen visuellen Elemente. Fragen Sie sich: „Welche Geschichte versuche ich mit diesem visuellen Element zu erzählen“, und finden Sie dann heraus, welche Art von visuellem Element die Geschichte am besten erzählt. Sie können den Fortschritt eines Verkaufszyklus zwar in Form eines Balkendiagramms ausdrücken, aber wäre ein Wasserfalldiagramm oder Trichterdiagramm nicht viel besser geeignet? Hilfe bei diesem Prozess finden Sie im letzten Abschnitt dieses Artikels, [Arten von visuellen Elementen und bewährte Methoden](#visual-types-and-best-practices). Es werden bewährte Methoden für einige gängigere Arten von visuellen Elementen beschrieben. Wundern Sie sich nicht, wenn sich das zuerst ausgewählte visuelle Element nicht als beste Option herausstellt. Probieren Sie mehr als eine Art von visuellem Element aus, um herauszufinden, womit die Aussage am besten vermittelt wird.

Machen Sie sich mit dem Unterschied zwischen quantitativen Daten und Kategoriedaten vertraut, und ermitteln Sie, welche Arten von visuellen Elementen für welche Arten von Daten am besten funktionieren. Quantitative Daten werden häufig als Kennzahlen bezeichnet und sind meist numerischer Art. Kategoriedaten werden häufig als Dimensionen bezeichnet und können klassifiziert werden. Im Abschnitt [Wählen der richtigen Measures](#choose-the-right-measure) wird dies ausführlicher beschrieben.

Widerstehen Sie der Versuchung, ausgefallene oder komplexere visuelle Elemente mit dem Ziel zu verwenden, den Bericht eindrucksvoller erscheinen zu lassen. Ihr Ziel sollte darin bestehen, die einfachste Option zum Vermitteln Ihrer Geschichte zu finden. Mit horizontalen Balkendiagrammen und einfachen Liniendiagrammen lassen sich Informationen schnell vermitteln. Sie sind Lesern vertraut und können meist leicht interpretiert werden. Ein weiterer Vorteil ist, dass der größte Teil Ihrer Zielgruppe von links nach rechts und von oben nach unten liest und deshalb schnell diese beiden Diagrammtypen erfassen und diese Informationen verstehen kann.

Muss für Ihre visuellen Elemente ein Bildlauf durchgeführt werden, um die Geschichte zu erzählen? Vermeiden Sie Bildläufe nach Möglichkeit. Versuchen Sie, Filter anzuwenden und Hierarchien/Drilldowns zu verwenden. Wenn diese Elemente die Scrollleiste nicht entfernen, sollten Sie eine andere Art von visuellem Element wählen. Wenn Sie das Scrollen nicht vermeiden können, tolerieren Ihre Leser das horizontale Scrollen besser als das vertikale Scrollen.

Auch wenn Sie das beste visuelle Element für die Geschichte wählen, kann es sein, dass Sie für die Vermittlung trotzdem weitere Hilfsmittel benötigen. An diesem Punkt kommen Beschriftungen, Titel, Menüs, Farben und verschiedene Größen ins Spiel. Diese Entwurfselemente werden später im Abschnitt [Entwurfselemente](#design-elements) beschrieben.

### <a name="choose-the-right-measure"></a>Wählen der richtigen Measures

Ist die Geschichte, die mit dem visuellen Element erzählt wird, interessant genug? Hat sie Aussagekraft? Erstellen Sie visuelle Elemente nicht nur um ihrer reinen Erstellung wegen. Sie sind vielleicht der Meinung, dass mit den Daten eine interessante Geschichte erzählt wird, aber es kann auch sein, dass dies nicht der Fall ist. Scheuen Sie sich nicht, neu anzufangen und nach einer interessanteren Geschichte zu suchen. Es kann auch sein, dass die Geschichte steht, aber andere Measures erforderlich sind.

Angenommen, Sie möchten den Erfolg Ihrer Vertriebsleiter messen. Welches Measure würden Sie für diese Aufgabe verwenden? Würden Sie sich den Gesamtumsatz oder -gewinn, die Steigerungsrate des letzten Jahres oder die Leistung anhand einer Zielvorgabe ansehen? Vertriebsmitarbeiterin Sally hat möglicherweise den höchsten Umsatz. Wenn Sie den Gesamtumsatz pro Vertriebsmitarbeiter in einem Balkendiagramm darstellen würden, wäre Sally unter ihren Kolleginnen und Kollegen der Star. Wenn Sally aber auch hohe Vertriebskosten (Reisekosten, Lieferkosten, Fertigungskosten usw.) verursacht hat, ist die Aussagekraft nicht ausreichend, wenn allein der Umsatz betrachtet wird.

#### <a name="reflect-reality-dont-distort-reality"></a>Realität widerspiegeln – nicht verzerren

Es ist möglich, ein visuelles Element zu erstellen, mit dem die Wahrheit verzerrt wird. Es gibt eine Website, auf der Datenspezialisten ihrer Meinung nach schlechte visuelle Elemente vorstellen. In den meisten Kommentaren wird bemängelt, dass ein Unternehmen das jeweilige fehlerhafte visuelle Element erstellt und veröffentlicht hat. Ein schlechtes visuelles Element vermittelt die Botschaft, das Unternehmen sei nicht vertrauenswürdig.

Erstellen Sie also visuelle Elemente, mit denen die Realität nicht absichtlich verzerrt wird und die nicht manipuliert wurden, um einer Geschichte die gewünschte Richtung zu geben. Beispiel:

![Diagramm mit Verzerrung der Realität.](media/power-bi-visualization-best-practices/corp-success-distorted.png)

**Abbildung 22: Diagramm mit Verzerrung der Realität**

In diesem Beispiel wird der Eindruck erweckt, dass zwischen den vier Unternehmen ein großer Unterschied bestünde und CorpB deutlich erfolgreicher als die anderen drei Unternehmen sei. Beachten Sie, dass die X-Achse nicht bei Null (0) beginnt und die Unterschiede zwischen den Unternehmen sich innerhalb des Fehlerquotenbereichs bewegen. Unten sind die gleichen Daten in einem Diagramm dargestellt, bei dem die X-Achse bei Null (0) beginnt.

![Realistisches Diagramm.](media/power-bi-visualization-best-practices/corp-success.png)

**Abbildung 23: Realistisches Diagramm**

Leser erwarten, dass die X-Achse bei Null (0) beginnt, und setzen es häufig als gegeben voraus. Wenn Sie nicht bei Null (0) beginnen möchten, tun Sie es auf eine Weise, die die Ergebnisse nicht verzerrt. Erwägen Sie, einen visuellen Hinweis oder ein Textfeld hinzuzufügen, um auf die Abweichung von der Norm hinzuweisen.

### <a name="design-elements"></a>Entwurfselemente

Nachdem Sie einen Typ und ein Measure ausgewählt und das visuelle Element erstellt haben, ist es an der Zeit, die Darstellung zu optimieren, um eine maximale Effektivität zu erzielen. In diesem Abschnitt wird Folgendes beschrieben:

* Layout, Abstände und Größen

* Textelemente: Beschriftungen, Anmerkungen, Menüs, Titel

* Sortierung

* Visuelle Interaktion

* Farbe

#### <a name="tweaking-visuals-for-best-use-of-space"></a>Optimieren von visuellen Elementen zur bestmöglichen Nutzung des Platzes

Wenn Sie mehrere Diagramme in einem Bericht unterbringen möchten, kann es hilfreich sein, das Verhältnis von Daten zu „Tinte“ zu erhöhen, um den Fokus auf die Geschichte zu legen. Wie bereits erwähnt, prägte Edward Tufte den Begriff vom „Verhältnis von Daten zu ‚Tinte‘“. Das Ziel besteht darin, so viele Hinweis- und Designelemente wie möglich aus einem Diagramm zu entfernen, ohne die Interpretation der Daten durch den Leser zu beeinträchtigen.

Die erste unten angegebene Gruppe von Diagrammen enthält redundante Achsenbeschriftungen: **Jan 2014**, **Apr 2014** usw. In den Titeln wird **by Date** wiederholt. Für die Titel jedes Diagramms ist außerdem eigener Platz in horizontaler Richtung erforderlich. Indem wir die Diagrammtitel entfernen und einzelne Achsenbeschriftungen aktivieren, beseitigen wir einige Hinweis- und Designelemente und erzielen so eine bessere Nutzung des vorhandenen Platzes. Wir können die Achsenbeschriftungen für die oberen beiden Diagramme entfernen, um die Zahl der Hinweis- und Designelemente weiter zu reduzieren und einen größeren Teil des Platzes für Daten zu nutzen.

Falls Sie bestimmte Zeiträume besonders hervorheben möchten, können Sie Linien oder Rechtecke hinter allen Diagrammen einzeichnen. Diese dienen als Anhaltspunkte für die Augen, um Vergleiche zu vereinfachen.

![Vorher.](media/power-bi-visualization-best-practices/power-bi-multiples-before.png)

**Abbildung 24: Vorher**

![Nachher.](media/power-bi-visualization-best-practices/power-bi-multiples-after.png)

**Abbildung 25: Nachher**

**So aktivieren bzw. deaktivieren Sie Achsentitel**

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Erweitern Sie die Optionen für die **X-Achse** oder **Y-Achse**.

1. Setzen Sie den Schieberegler für **Titel** auf „Ein“ oder „Aus“.

    ![Aktivieren und Deaktivieren von Achsentiteln.](media/power-bi-visualization-best-practices/power-bi-axis-titles.png)

    **Abbildung 26: Aktivieren und Deaktivieren von Achsentiteln**

##### <a name="to-turn-axis-labels-on-and-off"></a>So aktivieren bzw. deaktivieren Sie Achsenbeschriftungen

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Neben den Optionen **X-Achse** und **Y-Achse** befinden sich jeweils Schieberegler.

1. Verschieben Sie den Schieberegler, um die Achsenbeschriftungen zu aktivieren bzw. zu deaktivieren.

    ![Aktivieren und Deaktivieren von Achsenbeschriftungen.](media/power-bi-visualization-best-practices/power-bi-axis-labels.png)

    **Abbildung 27: Aktivieren und Deaktivieren von Achsenbeschriftungen**

    > [!TIP]
    > Ein Fall, in dem Sie die Beschriftungen der Y-Achse deaktivieren können, ist die Nutzung von aktivierten **Datenbeschriftungen**.

##### <a name="to-remove-visual-titles"></a>So entfernen Sie Titel von visuellen Elementen

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Setzen Sie den Schieberegler für **Titel** auf **Aus**.

    ![Entfernen von Titeln von visuellen Elementen.](media/power-bi-visualization-best-practices/power-bi-title-off.png)

    **Abbildung 28: Entfernen von Titeln von Visuals**

Berücksichtigen Sie, wie Ihre Leser den Bericht anzeigen werden. Stellen Sie sicher, dass Ihre visuellen Elemente und Texte groß genug und dunkel genug sind, um gelesen werden zu können. Falls die Seite ein überproportional großes visuelles Element enthält, gehen die Leser unter Umständen davon aus, dass es sich um das wichtigste Element handelt. Lassen Sie zwischen den visuellen Elementen genügend Platz, damit der Bericht nicht überladen und verwirrend aussieht. Richten Sie die visuellen Elemente so aus, dass die Augen der Leser richtig geleitet werden.

##### <a name="to-resize-a-visual"></a>So ändern Sie die Größe eines visuellen Elements

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Verschieben Sie einen der Ziehpunkte, um die Größe anzupassen.

    ![Ändern Sie die Größe eines visuellen Elements.](media/power-bi-visualization-best-practices/power-bi-drag-handles.png)

    **Abbildung 29: Ändern der Größe eines Visuals**

##### <a name="to-move-a-visual"></a>So verschieben Sie ein visuelles Element

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Wählen Sie das visuelle Element aus, und halten Sie das Ziehelement oben in der Mitte des visuellen Elements.

1. Ziehen Sie das visuelle Element an die neue Position.

    ![Verschieben eines visuellen Elements.](media/power-bi-visualization-best-practices/power-bi-move.png)

    **Abbildung 30: Verschieben eines Visuals**

#### <a name="titles-and-labels-that-are-part-of-the-visualizations"></a>Titel und Beschriftungen in Visualisierungen

Achten Sie darauf, dass Titel und Beschriftungen gut lesbar und selbsterklärend sind. Der Text von Titeln und Beschriftungen muss eine optimale Größe und eine auffällige Farbe haben. Erinnern Sie sich an unsere Stilvorgabe (siehe Abschnitt [Text](#text) weiter oben im Artikel)? Begrenzen Sie die Anzahl unterschiedlicher Farben und Größen. Wenn zu viele verschiedene Schriftgrößen und Farben verwendet werden, sieht die Seite überladen und verwirrend aus. Erwägen Sie, die gleiche Schriftfarbe und -größe für die Titel aller visuellen Elemente auf einer Berichtsseite zu verwenden. Wählen Sie außerdem für alle Titel einer Berichtsseite die gleiche Ausrichtung.

**Der Bereich „Format“**

Wählen Sie für alle unten aufgeführten Formatänderungen jeweils das ![Farbrollen-Symbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

![Öffnen des Bereichs „Format“.](media/power-bi-visualization-best-practices/power-bi-paintbrush.png)

**Abbildung 31: Öffnen des Bereichs „Format“**

Wählen Sie anschließend das anzupassende visuelle Element aus, und vergewissern Sie sich, dass **Ein** festgelegt ist. Beispiele für visuelle Elemente: **X-Achse**, **Y-Achse**, **Titel**, **Datenbeschriftungen** und **Legende**. Im Beispiel unten wird das Element **Titel** verwendet.

![Formatieren des Titels eines visuellen Elements.](media/power-bi-visualization-best-practices/power-bi-title-formatting.png)

**Abbildung 32: Formatieren des Titels eines Visuals**

##### <a name="set-the-text-size"></a>Festlegen der Textgröße

Sie können die Textgröße für Titel und Datenbeschriftungen anpassen, aber nicht für X- oder Y-Achsen oder Legenden. Experimentieren Sie speziell für Datenbeschriftungen mit den **Anzeigeeinheiten** und der Anzahl der **Dezimalstellen**. Schließlich werden Sie den optimalen Detaillierungsgrad für die Anzeige von Informationen in Ihrem Bericht finden.

##### <a name="set-the-text-alignment"></a>Festlegen der Textausrichtung

Sie können für die Titelausrichtung links, rechts oder zentriert wählen. Entscheiden Sie sich für eine Option, und wenden Sie diese Einstellung für alle visuellen Elemente auf der Seite an.

##### <a name="set-the-text-position"></a>Festlegen der Textposition

Sie können die Textposition für einige Y-Achsen und für die Legende anpassen. Gehen Sie für die anderen Y-Achsen und Legenden der Seite genauso vor, nachdem Sie sich für eine Option entschieden haben.

##### <a name="set-the-title-and-label-length"></a>Festlegen der Länge für Titel und Beschriftungen

Passen Sie die Länge der Titel, Achsentitel, Datenbeschriftungen und Legenden an. Wenn Sie sich für die Anzeige dieser Elemente entscheiden, wird durch das Anpassen der Länge (und der Textgröße) sichergestellt, dass Power BI die Werte nicht abschneidet:

* Für **Titel** und **Legende** lautet die Einstellung **Titeltext**. Geben Sie den eigentlichen Titel an, der für das visuelle Element angezeigt wird.

* Für **X-Achse** und **Y-Achse** lautet die Einstellung **Stil**, und Sie treffen Ihre Wahl in einer Dropdownliste.

* Für **Datenbeschriftungen** lauten die Einstellungen **Anzeige** und **Dezimal**. Verwenden Sie die Dropdownliste **Anzeige**, um die Maßeinheiten auszuwählen: **Millionen**, **Tausende**, **Keine**, **Auto** usw. Verwenden Sie das Feld **Dezimal**, um anzugeben, wie viele Dezimalstellen von Power BI angezeigt werden sollen.

##### <a name="set-the-text-color"></a>Festlegen der Textfarbe

Sie können die Textfarbe für Titel, Achsen und Datenbeschriftungen anpassen.

#### <a name="titles-and-labels-that-arent-part-of-the-visualizations"></a>Titel und Beschriftungen außerhalb von Visualisierungen

Weiter oben in diesem Artikel wurde das Einfügen von Textfeldern auf Berichtsseiten beschrieben. In einigen Fällen reichen die Titel der Visualisierungen nicht aus, um die Geschichte zu erzählen. Fügen Sie Textfelder hinzu, um den Lesern Ihrer Berichte zusätzliche Informationen zu vermitteln.

Damit die Berichtsseite nicht zu verwirrend oder voll aussieht, ist es ratsam, bei der Verwendung von Schriftarten, Schriftgrößen, Farben und der Ausrichtung einheitlich vorzugehen. Wählen Sie das Textfeld aus, dessen Text Sie ändern möchten, um das Menü für die Formatierung zu öffnen.

![Formatieren der Schriftart in einem Textfeld.](media/power-bi-visualization-best-practices/power-bi-text-box-edit.png)

**Abbildung 33: Formatieren der Schriftart in einem Textfeld**

#### <a name="sorting"></a>Sortierung

Eine einfache Möglichkeit zur Förderung des Verständnisses ist das Sortieren der visuellen Elemente. Wenn Sie Balkendiagramme beispielsweise anhand des Werts der Balken in absteigender oder aufsteigender Reihenfolge sortieren, können Sie signifikante inkrementelle Informationen schnell anzeigen, ohne dass mehr Platz verbraucht wird.

So sortieren Sie ein Diagramm:

1. Wählen Sie in der rechten oberen Ecke des Diagramms die Auslassungspunkte aus.

1. Wählen Sie **Sortieren** aus.

1. Wählen Sie das Feld aus, nach dem sortiert werden soll, und die Richtung.

Weitere Informationen finden Sie unter [Ändern der Sortierung eines Diagramms in einem Power BI-Bericht](../consumer/end-user-change-sort.md).

#### <a name="chart-interaction-and-interplay"></a>Interaktion und Zusammenwirken von Diagrammen

Eine der interessantesten Funktionen von Power BI ist die Möglichkeit zum Ändern der Art und Weise, wie Diagramme interagieren. Standardmäßig funktionieren Hervorhebungen diagrammübergreifend: Wenn Sie einen Datenpunkt auswählen, werden die dazugehörigen Daten in anderen Diagrammen hervorgehoben und die nicht relevanten Daten abgeblendet. Sie können dieses Verhalten überschreiben, um ein Diagramm als echten Filter zu verwenden. So sparen Sie Platz auf der Seite. Wählen Sie im Power BI-Dienst **Visualinteraktionen** in der Menüleiste aus, um die Änderung vorzunehmen.

![Visualinteraktionen.](media/power-bi-visualization-best-practices/power-bi-visual-interactions.png)

**Abbildung 34: Visualinteraktionen**

Entscheiden Sie dann für jedes visuelle Element auf der Seite, ob das ausgewählte visuelle Element für die Filterung oder Hervorhebung verwendet werden oder ob keine Aktion durchgeführt werden soll. Sie können nicht alle visuellen Elemente hervorheben. Für visuelle Elemente, die Sie nicht hervorheben können, ist das Steuerelement für die Hervorhebung nicht verfügbar. Weitere Informationen finden Sie unter [Interaktionen mit Visualisierungen in einem Power BI-Bericht](../consumer/end-user-interactions.md).

> [!TIP]
> Für Leser, für die Power BI neu ist, ist die Möglichkeit zum Auswählen und Interagieren mit Berichten unter Umständen nicht gleich erkennbar. Fügen Sie Textfelder ein, damit verdeutlicht wird, was ausgewählt werden kann, um weitere Erkenntnisse zu gewinnen.

#### <a name="the-use-of-color-in-visuals"></a>Verwendung von Farbe in visuellen Elementen

Weiter oben in diesem Artikel ging es um die Bedeutung eines Plans für den Einsatz von Farbe in einem Bericht. Einige Punkte werden hier wiederholt, aber im Wesentlichen geht es darum, wie Sie Farbe in den einzelnen visuellen Elementen einsetzen können. Es gelten auch wieder die gleichen Grundprinzipien: Nutzen Sie Farbe, um den Bericht konsistent zu machen, die Aufmerksamkeit auf wichtige Daten zu lenken und die Verständlichkeit des visuellen Elements für Leser zu fördern. Die Verwendung von zu vielen unterschiedlichen Farben kann störend sein. Sie erschwert Ihren Lesern die Orientierung. Vermeiden Sie es, die Verständlichkeit auf Kosten des hübschen Designs zu reduzieren. Fügen Sie nur Farbe hinzu, wenn dies der Verständlichkeit dient.

> [!TIP]
> Stellen Sie sicher, dass Sie genau wissen, wie Ihre Zielgruppe aussieht und welche Regeln in Bezug auf Farben gelten. In den USA steht Grün normalerweise für „positiv“ und Rot für „negativ“.

In den folgenden Abschnitten werden diese Themen behandelt:

* Farben für Daten

* Farben für Datenbeschriftungen

* Farben für Kategoriewerte

* Farben für Zahlenwerte

##### <a name="use-colors-to-highlight-interesting-data"></a>Verwenden von Farben zum Hervorheben von interessanten Daten

Die einfachste Möglichkeit zur Verwendung von Farben besteht darin, die Farbe von einem oder mehreren Datenpunkten zu ändern, um die Aufmerksamkeit darauf zu lenken. In diesem Beispiel ändert sich die Farbe an dem Punkt, an dem sich der Jahresrhythmus für die Olympischen Sommer- und Winterspiele geändert hat (abwechselnd alle zwei Jahre, anstatt alle vier Jahre).

![Verwenden von Farben zum Erzählen einer Geschichte.](media/power-bi-visualization-best-practices/power-bi-data-color.png)

**Abbildung 35: Verwenden von Farben zum Erzählen einer Geschichte**

Sie können die Farbe von Datenpunkten im Bereich **Format** auf der Registerkarte **Datenfarben** ändern. Stellen Sie sicher, dass **Alle anzeigen** auf **Ein** festgelegt ist, wenn Sie jeden Datenpunkt einzeln anpassen möchten.

![Festlegen von Farben für Datenpunkte.](media/power-bi-visualization-best-practices/power-bi-colors.png)

**Abbildung 36: Festlegen von Farben für Datenpunkte**

> [!NOTE]
> Power BI wendet ein Standarddesign auf die visuellen Elemente des Berichts an. Designer haben die Designfarben so ausgewählt, dass für Abwechslung und Kontrast gesorgt ist. Wählen Sie die Option **Benutzerdefinierte Farbe**, wenn Sie von der Palette mit den Standardfarben abweichen möchten.
>
> ![Auswählen einer benutzerdefinierten Farbe.](media/power-bi-visualization-best-practices/power-bi-custom-color.png)
>
> **Abbildung 37: Auswählen einer benutzerdefinierten Farbe**

In Power BI Desktop können Sie sogar **Ausreißer** oder einen bestimmten Abschnitt einer Linie hervorheben, indem Sie eine zweite Reihe verwenden:

![Verwenden von Desktop zum Darstellen von Ausreißern.](media/power-bi-visualization-best-practices/power-bi-outliers.png)

**Abbildung 38: Verwenden von Power BI Desktop zum Darstellen von Ausreißern**

Hier sind in der Reihe **Ausreißer** nur Werte enthalten, wenn die Durchschnittstemperatur für den Monat August unter 15,5°C (60°F) gefallen ist. Hierfür erstellten wir mit der folgenden Formel per DAX-Berechnung eine Säule:

```
Outliers = if(Editions[Temp]<60, Editions[Temp], BLANK())
```

Unser Beispiel enthält drei Ausreißer: **1952**, **1956** und **2000**.

##### <a name="colors-for-labels-and-titles"></a>Farben für Beschriftungen und Titel

Wenn Sie sich alle verfügbaren Formatierungsoptionen ansehen, erkennen Sie die vielen Möglichkeiten zum Einfügen von Farbe für Titel und Legenden. Sie können beispielsweise die Farbe von Datenbeschriftungen und Achsentiteln ändern. Seien Sie jedoch vorsichtig. Es ist meist ratsam, für alle Titel von visuellen Elementen die gleiche Farbe zu nutzen. Wie bei den anderen Richtlinien in diesem Artikel gibt es immer Situationen und Gründe, die Regeln zu brechen. Wenn Sie sich entscheiden, Regeln zu brechen, tun Sie dies aus einem guten Grund.

##### <a name="colors-for-categorical-values"></a>Farben für Kategoriewerte

Diagramme mit einer Datenreihe enthalten in der Legende normalerweise einen Kategoriewert. Jede Farbe in der unten angegebenen Legende steht für eine andere Kategorie im Bereich „Land/Region“.

![Angewendete Standardfarben.](media/power-bi-visualization-best-practices/power-bi-bubble-color.png)

**Abbildung 39: Angewendete Standardfarben**

Designer haben die von Power BI standardmäßig verwendeten Farben speziell ausgewählt, um eine gute farbliche Trennung zwischen Kategoriewerten zu ermöglichen, damit sie gut unterschieden werden können. Es kann vorkommen, dass Benutzer diese Farben ändern, um sie an das im Unternehmen verwendete Schema anzupassen. Dies kann aber zu Problemen führen.

![Anwendung von Farbe in Form von Farbtönen einer bestimmten Farbe.](media/power-bi-visualization-best-practices/power-bi-bubble-color2.png)

**Abbildung 40: Anwendung von Farbe in Form von Farbtönen einer bestimmten Farbe**

Indem nur ein einzelner Farbton verwendet und die Intensität der Farbe variiert wurde, wurde in diesem visuellen Element eine scheinbare Sortierung für die Kategorien erzielt. Es wird impliziert, dass die dunkleren Blasen auf einer Skala höher oder niedriger als die helleren Blasen angeordnet sind. Für diese Art von Kategoriewerten gilt normalerweise mit Ausnahme der alphabetischen Sortierung keine andere Sortierung.

Wählen Sie zum Ändern der Standardfarben das ![Farbrollen-Symbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen, und wählen Sie **Datenfarben** aus.

##### <a name="colors-for-numerical-values"></a>Farben für Zahlenwerte

Für Felder, die über eine inhärente Reihenfolge und einen Zahlenwert verfügen, können Sie Datenpunkte auch basierend auf dem Wert mit einer Farbe versehen. Das Kolorieren von Datenpunkten kann nützlich sein, um die Verteilung der Werte über die Daten hinweg darzustellen und außerdem Power BI zu ermöglichen, zwei Variablen gemeinsam in einem Diagramm anzuzeigen. In diesem Diagramm wird verdeutlicht, dass China zwar die höchste Zahl von Medaillen errungen hat, aber Japan und Thailand an mehr Olympischen Spielen teilgenommen haben.

![Versehen von Datenpunkten mit Farbe basierend auf dem Wert.](media/power-bi-visualization-best-practices/power-bi-saturation.png)

**Abbildung 41: Versehen von Datenpunkten mit Farbe basierend auf dem Wert**

So erstellen Sie dieses Diagramm:

1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

1. Wählen Sie **Datenfarben** > Option > **Bedingte Formatierung** aus:

    ![Auswählen der bedingten Formatierung.](media/power-bi-visualization-best-practices/power-bi-conditional-formatting.png)

    **Abbildung 42: Auswählen der bedingten Formatierung**

1. Passen Sie diese Farben im Dialogfeld **Standardfarbe – *Datenfarben*** an.

    ![Anpassen der für die Sättigung verwendeten Farben.](media/power-bi-visualization-best-practices/power-bi-color-controls.png)

    **Abbildung 43: Anpassen der für die Sättigung verwendeten Farben**

Sie können Farben auch verwenden, um die Varianz für einen Hauptwert hervorzuheben. Ein Beispiel hierfür sind grüne positive Werte und rote negative Werte. Beachten Sie die kulturellen Unterschiede, wenn Sie positiven oder negativen Werten Farben zuweisen. Nicht in allen Kulturen wird die Farbe Rot für „negativ“ und Grün für „positiv“ verwendet!

![Farbe zum Hervorheben der Varianz für einen Hauptwert.](media/power-bi-visualization-best-practices/power-bi-color.png)

**Abbildung 44: Farbe zum Hervorheben der Varianz für einen Hauptwert**

### <a name="principles-of-visual-design--applied-to-example-report-page"></a>Grundlagen des Entwurfs von visuellen Elementen – Anwendung auf die Berichtsseite aus dem Beispiel

Nun wenden wir die oben beschriebenen Grundlagen für visuelle Element auf unseren Beispielbericht an.

![Beispielbericht (vorher).](media/power-bi-visualization-best-practices/power-bi-example5a.png)

**Abbildung 45: Beispielbericht (vorher)**

![Beispielbericht (nachher).](media/power-bi-visualization-best-practices/power-bi-example6anew.png)

**Abbildung 46: Beispielbericht (nachher)**

#### <a name="what-did-we-do"></a>Was haben wir unternommen?

| Artikel | Beschreibung |
| ---- | ----------- |
| Slicer | Wir haben die Leerstellen aus den Datenschnitten entfernt, indem wir einen Filter auf Seitenebene hinzugefügt und nur **Gold**, **Silber** und **Bronze** ausgewählt haben. <br> Wir haben die Option **Auswahlsteuerelemente** für **Einfachauswahl** und **Alles auswählen** in **Aus** geändert. |
| Blase | Die Legende enthält so viele Elemente, dass nicht alle sichtbar sind. Wir haben die Legende entfernt und stattdessen **Kategoriebeschriftungen** aktiviert. Kunden können den Mauszeiger auf die Blasen bewegen, um die Details anzuzeigen.<br> Wir haben den Titel gekürzt und den Zusatz „by countryregion“ entfernt, weil dies offensichtlich ist. <br> Wir haben die Achsenbeschriftungen jeweils auf **Ein** festgelegt, damit das Diagramm leichter verständlich ist. |
| Flächenkartogramm | Wir haben die **Datenfarben** geändert, um eine bessere Hervorhebung zu erzielen. <br> Wir haben **Abweichend** aktiviert und das **Minimum** auf „Rosa“ und das **Maximum** auf „Rot“ festgelegt.
| Treemap | Wir haben den Filter entfernt, der nur für die USA galt. <br> Legen Sie für die **Datenbeschriftungen** eine Dezimalstelle fest. <br> Für das visuelle Element wurde das Feld **Klasse** verwendet. Dies ist nicht nützlich, da der Wert fast immer 33% für die 3 Medaillen beträgt: Gold, Silber und Bronze. <br> Wir haben ein interessanteres Feld ausgewählt, **Gender**. Aus Designgründen haben wir „Aquatics“ (Wassersport) in Blau und „Athletics“ (Leichtathletik) in Grau geändert.
| Oberes Balkendiagramm | Wir haben den Titel verkürzt, die Datenbeschriftungen entfernt und den Legendentitel deaktiviert. <br> Wir haben die Wortreihenfolge im Titel geändert, um sie an das Diagramm unten anzupassen.
| Unteres Balkendiagramm | Wir haben aufsteigend nach dem Jahr sortiert, damit dies mit dem obigen Diagramm übereinstimmt. <br> Wir haben die Farben geändert, damit sie mit der Klasse übereinstimmen. <br> Der Titel wurde geändert. <br> Wir haben die Legende deaktiviert, um mehr Platz für Daten zu erhalten. <br> Wir haben die Datenbeschriftungen aktiviert. Sie werden im Bericht nicht angezeigt, da das visuelle Element zu klein ist, als dass die Beschriftungen leicht zu lesen wären. Sie werden angezeigt, wenn der Leser das visuelle Element im **Fokusmodus** öffnet. Informationen zum [Fokusmodus](../consumer/end-user-focus.md). <br> **Count of Event (Distinct)** wurde den **QuickInfos** hinzugefügt. Wenn Sie nun die Maus über eine gestapelte Säule bewegen, teilen Ihnen die QuickInfos mit, wie viele Veranstaltungen die Personen in diesem Jahr ausgetragen haben. |
| Visualinteraktionen | Wir haben die Interaktionen für beide Karten deaktiviert, da immer alle Spiele und Sportarten angezeigt werden sollen. |

## <a name="visual-types-and-best-practices"></a>Arten von visuellen Elementen und bewährte Methoden

In Power BI werden viele Arten von visuellen Elementen nativ bereitgestellt. Wenn wir nun noch die Liste benutzerdefinierter visueller Elemente hinzufügen, die über Microsoft und die Power BI-Community verfügbar sind, werden die gesamten Optionen zu zahlreich, um hier dokumentiert zu werden. Wir gehen auf die am häufigsten verwendeten nativen Arten von visuellen Elementen ein.

### <a name="line-charts"></a>Liniendiagramme

![Liniendiagramm.](media/power-bi-visualization-best-practices/power-bi-line-chartb.png)

Liniendiagramme sind eine gute Möglichkeit, um Daten in Abhängigkeit der Zeit darzustellen. Wenn wir uns Daten in Tabellen ansehen, können die Augen sie nicht so schnell erfassen, wie dies bei den Spitzen, Tälern, Zyklen und Mustern dieser Diagrammdarstellung möglich ist. Im Beispiel unten sind die Trends bei der Anzahl von vergebenen Medaillen und der Anzahl von Athleten erkennbar, die diese Medaillen errungen haben.

![Liniendiagramme.](media/power-bi-visualization-best-practices/power-bi-line-chart.png)

**Abbildung 47: Liniendiagramme**

#### <a name="best-practices"></a>Bewährte Methoden

* Beim Ansehen von Liniendiagrammen fällt Benutzern zuerst die Form der Kurve auf. Sie benötigen also eine X-Achse, damit die Kurve aussagekräftig ist, z.B. Zeit- oder Verteilungskategorien. Wenn Sie auf der X-Achse Kategoriefelder wie „Produkt“ oder „Geografische Region“ anordnen, ist das Liniendiagramm uninteressant. Die Form der Kurve würde keine sinnvollen Informationen liefern.

* Wenn Sie mehrere Diagramme über- bzw. untereinander anordnen, um das Vergleichen der Datenreihen zu vereinfachen, sollten Sie die X-Achse ausrichten. Verwenden Sie Filter, um sicherzustellen, dass Power BI den gleichen Wertebereich anzeigt. Stellen Sie bei Datumsbereichen sicher, dass die gleichen Datumsbereiche verwendet werden. Beispiel: 1896 bis 2012 in beiden Diagrammen.

* Nutzen Sie den vorhandenen Platz auf bestmögliche Weise. Gehen Sie wie folgt vor, sofern es für Ihre Daten sinnvoll ist: Legen Sie den **Start**- und **Endpunkt** für die Y-Achse so fest, dass oben und unten im Diagramm keine leeren Flächen entstehen. So kann das visuelle Element leichter den Fokus auf die eigentlichen Datenpunkte legen. So legen Sie **Start**- und **Endpunkt** fest:

  1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

  1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.
  
  1. Erweitern Sie den Bereich für die **Y-Achse**, und legen Sie die Punkte für **Start** und **Ende** fest.
  
      ![Festlegen von Start- und Endpunkt.](media/power-bi-visualization-best-practices/power-bi-start-end.png)
  
      **Abbildung 48: Festlegen von Start- und Endpunkt**

* Ein weiterer Grund dafür, warum **Start**- und **Endpunkt** explizit festgelegt werden sollten, ist die Vergleichsmöglichkeit von zwei oder mehr Diagrammen auf einer Seite anhand des gleichen Felds der Y-Achse. Wenn Sie sich beispielsweise kumulative Veranstaltungszahlen ansehen und die Zahlen für das Vereinigte Königreich von 1 bis 70 und für Australien von 1 bis 12 reichen, werden in den beiden Liniendiagrammen unterschiedliche Y-Achsen angezeigt (Abbildung 49). Dies erschwert einen Vergleich auf den ersten Blick. Legen Sie die Diagramme stattdessen so fest, dass der gleiche Bereich für die Y-Achse verwendet wird (Abbildung 50).
  
  ![Liniendiagramme mit unterschiedlichen Y-Achsen.](media/power-bi-visualization-best-practices/power-bi-line-chart2.png)
  
  **Abbildung 49: Liniendiagramme mit unterschiedlichen Y-Achsen**
  
  ![Liniendiagramme mit gleichen Y-Achsen.](media/power-bi-visualization-best-practices/power-bi-line-chart3.png)
  
  **Abbildung 50: Liniendiagramme mit gleichen Y-Achsen**

Weitere Informationen finden Sie unter:

* [Anpassen der Eigenschaften der X- und Y-Achse](power-bi-visualization-customize-x-axis-and-y-axis.md)

* [Line charts and irregular intervals: An Incompatible Partnership](http://www.perceptualedge.com/articles/visual_business_intelligence/line_graphs_and_irregular_intervals.pdf) (Liniendiagramme und unregelmäßige Intervalle: Eine inkompatible Partnerschaft)

* [Data Visualization 101: Line Charts](http://www.columnfivemedia.com/data-visualization-101-line-charts) (Datenvisualisierung 101: Liniendiagramme)

### <a name="bar-and-column-charts"></a>Balken- und Säulendiagramme

![Balken- und Säulendiagramme.](media/power-bi-visualization-best-practices/power-bi-bar-chart.png)

Wenn Liniendiagramme der Standard für die Darstellung von Daten in Abhängigkeit der Zeit sind, sind Balkendiagramme der Standard für die Darstellung eines bestimmten Werts für unterschiedliche Kategorien. Wenn Sie die Balken anhand des Zahlenwerts sortieren, sind die höchsten Werte und die Verteilung sofort erkennbar. Horizontale Balkendiagramme eignen sich gut für längere Beschriftungen.

![Horizontales Balkendiagramm.](media/power-bi-visualization-best-practices/power-bi-horizontal-scroll.png)

**Abbildung 51: Horizontales Balkendiagramm**

#### <a name="best-practices"></a>Bewährte Methoden

* Nutzen Sie Datenbeschriftungen für Werte. Dies erleichtert Ihnen die Identifizierung von bestimmten Werten. So zeigen Sie Datenbeschriftungen an: 

  1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

  1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.
  
  1. Legen Sie für **Datenbeschriftungen** die Option **Ein** fest.

      ![Aktivieren von Datenbeschriftungen.](media/power-bi-visualization-best-practices/power-bi-data-labels.png)

      **Abbildung 52: Aktivieren von Datenbeschriftungen**

* Das obige Balkendiagramm ist gut geeignet, um ein Measure für einen bestimmten Zeitpunkt mit vielen anderen Measures zu vergleichen. Während im Liniendiagramm der Trend in Abhängigkeit der Zeit verdeutlicht wurde, ist im Balkendiagramm der Trend für eine einzelne Kategorie zu einem bestimmten Zeitpunkt zu sehen. In unserem Balkendiagramm ist sofort erkennbar, dass Spanien eine der weltweit höchsten Arbeitslosenquoten aufweist (24,70%).

* Wenn der zugeordnete Platz für ein Balken- bzw. Säulendiagramm nicht ausreicht, werden in Power BI Scrollleisten eingefügt. Bauen Sie das visuelle Element und den Bericht – sofern dies möglich und sinnvoll ist – so auf, dass Diagramme vollständig zu sehen sind. So können die Leser sich einen Überblick über die gesamte Verteilung verschaffen. Aufgrund der hohen Zahl von Ländern der Welt ist dies in unserem Beispiel leider nicht möglich.

  Eine Möglichkeit zur Begrenzung der einbezogenen Werte ist die Verwendung eines Filters. Fügen Sie beispielsweise einen Filter auf **visueller Ebene** hinzu, damit ein Land nur angezeigt wird, wenn die Arbeitslosenquote über 20% liegt.

* Sie können einen Drilldown (und anschließend einen Drillup) in Balken- und Säulendiagrammen durchführen. Dies ist eine hervorragende Möglichkeit, um mehr Informationen in einem visuellen Element unterzubringen, ohne dass mehr Platz belegt wird. Das folgende Beispiel enthält eine Hierarchie für „Regionen“ > „Länder“. Wenn Sie auf den Balken für eine Region klicken, wird ein Drilldown zu den Ländern durchgeführt, die sich in der Region befinden. Weitere Informationen zum Drillmodus finden Sie unter [Drillmodus in einer Visualisierung in Power BI](../consumer/end-user-drill.md).
  
  ![Drilldown ausführen.](media/power-bi-visualization-best-practices/power-bi-drill.png)
  
  **Abbildung 53: Drilldown ausführen**

Ausführlichere Informationen zu Balken- und Säulendiagrammen finden Sie auf den folgenden Seiten:

* [Data Visualization 101: Bar Charts](http://blog.newscred.com/article/data-visualization-101-bar-charts) (Datenvisualisierung 101: Balkendiagramme)

* [Data Visualization Catalogue: Bar Chart](http://www.datavizcatalogue.com/methods/bar_chart.html#.VYV-hY3bLJw) (Katalog für Datenvisualierungen: Balkendiagramm)

* [Data Visualization Catalogue: Multi-Set Bar Chart](http://www.datavizcatalogue.com/methods/multiset_barchart.html#.VYV_gI3bLJw) (Katalog für Datenvisualierungen: Multiset-Balkendiagramm)

### <a name="stacked-bar-and-column-charts"></a>Gestapelte Balken- und Säulendiagramme

![Gestapelte Diagramme.](media/power-bi-visualization-best-practices/power-bi-stacked.png)

Fügen Sie Ihren Balken- und Säulendiagrammen eine weitere Dimension hinzu, indem Sie verschiedene Kategorien im Balken oder in der Säule stapeln. Mit dem Diagramm werden dann nicht nur Informationen zu einem Haupttrend vermittelt (basierend auf Höhe und Länge), sondern es wird auch der Einfluss der Kategorien auf diesen Trend dargestellt. Im folgenden Diagramm wird die Umsatzsteigerung von Fußball-Spitzenteams auf Beträge von über 6 Milliarden im Jahr 2014 veranschaulicht.

![Gestapeltes Säulendiagramm](media/power-bi-visualization-best-practices/power-bi-deloite.png)

**Abbildung 54: Gestapeltes Säulendiagramm**

Dieses gestapelte Säulendiagramm verdeutlicht, dass sich der **Total Revenue** im Laufe der Zeit erhöht und dass die Werte in den Kategorien **Commercial** und **Broadcasting** stetig zunehmen – und so zur Steigerung des Gesamtumsatzes beitragen. Mit diesem Diagramm können aber nicht ohne Weiteres die Auswirkungen verglichen werden, die die drei Kategorien jeweils aufeinander haben. Beispiel: Wie verhält sich die Steigerung in der Kategorie „Commercial“ zur Steigerung in den Kategorien „Broadcasting“ oder „Match Day“? Eine bessere Wahl für diese Daten oder für ein begleitendes visuelles Element wäre ein Liniendiagramm.

![Konvertieren in ein Liniendiagramm.](media/power-bi-visualization-best-practices/power-bi-deloite2.png)

**Abbildung 55: Konvertieren in ein Liniendiagramm**

In diesem Liniendiagramm ist leicht erkennbar, dass der Umsatzanstieg für „Commercial“ am höchsten war, gefolgt von „Broadcasting“ und „Match Day“.

#### <a name="best-practices"></a>Bewährte Methoden

* Wie bei Balken- und Säulendiagrammen auch, können Sie die horizontale oder vertikale Anzeige wählen. Die horizontale Anzeige ist die bessere Wahl, wenn Sie lange Beschriftungen verwenden, und die vertikale Anzeige hat Vorteile, wenn Sie Zeitreihendaten verwenden.

* Vermeiden Sie die Nutzung von gestapelten Balken- und Säulendiagrammen, wenn Sie Trends und andere Veränderungsmuster in Abhängigkeit der Zeit darstellen möchten. Andere Diagramme, z.B. Liniendiagramme, sind für diese Aufgabe deutlich besser geeignet.

* Sie können das Diagramm auch so einrichten, dass die Verteilung auf dem Gesamtvolumen oder einem Prozentsatz des Gesamtwerts basiert.

* Wie Stephen Few angemerkt hat:

    > *...ist es schwierig, die Segmente eines gestapelten Balkens zu vergleichen. Wenn Sie die Segmente nebeneinander angeordnet haben und alle von der gleichen Grundlinie aus nach oben verlaufen, kann die Höhe leicht verglichen werden. Dies ist aber schwierig, wenn sie gestapelt werden. Außerdem ist zwar relativ leicht erkennbar, wie sich der Umsatz von Monat zu Monat geändert hat, aber es nicht einfach zu sehen, wie sich der Umsatz in anderen Kategorien geändert hat*.

* Diagramme vom Typ „Gestapelt (100 %)“ sind eine gute Wahl, wenn Sie Prozentsätze verwenden, die zusammen den Wert 100 ergeben. Im Beispiel unten ist die Kategorieverteilung nach Team zu sehen. Die Prozentsätze sind relativ und ermöglichen uns, die Muster auf einen Blick zu erkennen. Der Umsatz von Everton stammt hauptsächlich aus der Kategorie „Broadcasting“ (über 70%), während PSG nur 20% seines Umsatzes in dieser Kategorie erzielt. Wenn die horizontale Anzeige gewählt wird, ist mehr Platz für die Namen der Teams vorhanden, und die Auswirkung der Umsatzart ist besser erkennbar.

  ![Horizontales gestapeltes Diagramm.](media/power-bi-visualization-best-practices/power-bi-deloite3.png)

  **Abbildung 56: Horizontales gestapeltes Diagramm**

Weitere Informationen zu gestapelten Diagrammen:

* [Data Visualization Catalogue: Stacked bar graphs](http://www.datavizcatalogue.com/methods/stacked_bar_graph.html#top) (Katalog für Datenvisualisierungen: Gestapelte Balkendiagramme)

* [When are 100% stacked bar graphs useful?](http://www.perceptualedge.com/blog/?p=2239) (Wann sind „Gestapelte Balkendiagramme (100 %)“ sinnvoll?)

### <a name="combo-bar-and-column-charts"></a>Kombinierte Balken- und Säulendiagramme

![Kombinationsdiagramme.](media/power-bi-visualization-best-practices/power-bi-combo.png)

In Power BI können Sie Säulen- und Liniendiagramme zu einem Kombinationsdiagramm kombinieren. Die Optionen sind: 

* Linien- und gestapeltes Säulendiagramm 

* Linien- und gruppiertes Säulendiagramm

Sparen Sie wertvollen Platz im Zeichenbereich, indem Sie zwei separate visuelle Elemente kombinieren.

Die beiden nächsten Screenshots zeigen den Zustand vorher und nachher.

![Zwei separate Diagramme.](media/power-bi-visualization-best-practices/power-bi-spain-line.png)

 **Abbildung 57: Zwei separate Diagramme**

Der erste enthält zwei separate visuelle Elemente: ein Säulendiagramm mit der Bevölkerungszahl in Abhängigkeit der Zeit und ein Liniendiagramm mit dem Bruttoinlandsprodukt (BIP) in Abhängigkeit der Zeit. Diese Diagramme sind ein guter Kandidat für ein Kombinationsdiagramm, weil sie über die gleiche X-Achse (Jahr) und die gleichen Werte (2002 bis 2012) verfügen. Warum kombinieren wir die Diagramme nicht, um die beiden Trends in einem visuellen Element gemeinsam anzuzeigen und zu vergleichen? Die Kombination dieser beiden Diagramme ermöglicht einen schnelleren Vergleich der Daten.

![Einzelnes Kombinationsdiagramm.](media/power-bi-visualization-best-practices/power-bi-spain-combo.png)

 **Abbildung 58: Einzelnes Kombinationsdiagramm**

Die neue Berichtsseite enthält nur noch ein visuelles Element: ein Linien- und gestapeltes Säulendiagramm. Wir hätten auch ein Linien- und gruppiertes Säulendiagramm erstellen können. Es ist jetzt leichter möglich, nach einer Beziehung zwischen den beiden Trends zu suchen. Wir sehen, dass der Trend für die Bevölkerungszahl und das BIP bis 2008 ähnlich verlaufen sind. Ab 2009 flachte die Zunahme der Bevölkerung ab, und das BIP wurde volatiler.

#### <a name="best-practices"></a>Bewährte Methoden

* Kombinationsdiagramme funktionieren am besten, wenn beide visuellen Elemente mindestens eine gleiche Achse aufweisen.

* Achten Sie auf die Achsen! Lässt sich Ihr Kombinationsdiagramm leicht lesen und interpretieren? Werden unterschiedliche Bereiche und Werte verwendet? Wenn der Maßstab der Y-Achse des Säulendiagramms deutlich kleiner als der Maßstab der Y-Achse des Liniendiagramms ist, ist das Kombinationsdiagramm nicht aussagekräftig. Sehen Sie sich die dritte Zeile (Farbe „Aquamarin“) ganz unten an.

   ![Ungeeignetes Liniendiagramm.](media/power-bi-visualization-best-practices/power-bi-dual-line.png)

   **Abbildung 59: Ungeeignetes Liniendiagramm**

  Das Kombinationsdiagramm ist auch nicht aussagekräftig, wenn für das Säulendiagramm und das Liniendiagramm zwei verschiedene Measures verwendet werden, und Sie nicht zwei Achsen erstellen. Beispiel: US-Dollar und Prozent. Binden Sie beide Achsen ein, damit die Leser das Diagramm besser verstehen können, und erwägen Sie auch, Achsenbeschriftungen zu verwenden.

  So erstellen Sie zwei Achsen:

    1. Wählen Sie das visuelle Element aus, um es zu aktivieren.

    1. Wählen Sie das ![Farbrollensymbol für den Bereich „Format“](media/power-bi-visualization-best-practices/power-bi-paint-roller.png) aus, um den Bereich **Format** zu öffnen.

    1. Erweitern Sie die **Y-Achse**, und legen Sie für **Sekundäre anzeigen** die Option **Ein** fest.

          ![Anzeigen der Sekundärachse.](media/power-bi-visualization-best-practices/power-bi-show-secondary-new.png)

          **Abbildung 60: Anzeigen der Sekundärachse**

    1. Legen Sie für **Y-Achse (Spalte)**  > **Titel** die Option **Ein** fest.

    1. Legen Sie für **Y-Achse (Linie)**  > **Titel** die Option **Ein** fest.

  Das fertige Diagramm wird wie folgt aussehen:

  ![Erstellen eines Kombinationsdiagramms als Alternative.](media/power-bi-visualization-best-practices/power-bi-combo-chart.png)

  **Abbildung 61: Erstellen eines Kombinationsdiagramms als Alternative**

* Nutzen Sie die Vorteile von zwei Achsen. Dies ist eine gute Möglichkeit, um mehrere Measures mit verschiedenen Wertebereichen zu vergleichen. So werden die Zusammenhänge zweier Measures in einer Visualisierung verdeutlicht.

Weitere Informationen finden Sie unter:

* [Kombinationsdiagramm in Power BI](power-bi-visualization-combo-chart.md)

* [Dual-Scaled Axes in Graphs: Are They Ever the Best Solution? ](http://www.perceptualedge.com/articles/visual_business_intelligence/dual-scaled_axes.pdf) (Dual skalierte Achsen in Diagrammen: Sind sie immer die beste Lösung?)

### <a name="scatter-chart"></a>Punktdiagramm

![Punktdiagramm](media/power-bi-visualization-best-practices/power-bi-scatter.png)

In einigen Fällen sind viele Variablen vorhanden, die zusammen dargestellt werden sollen. Ein Punktdiagramm kann nützlich sein, um sich einen Gesamtüberblick zu verschaffen. Mit Punktdiagrammen werden Beziehungen zwischen zwei (Punktdiagramm) oder drei (Blasendiagramm) quantitativen Measures dargestellt. Ein Punktdiagramm weist immer zwei Wertachsen auf, sodass ein Satz von numerischen Daten entlang einer horizontalen Achse und ein anderer Satz von numerischen Werten entlang einer vertikalen Achse angezeigt werden. Das Diagramm zeigt Schnittpunkte von x- und y-Zahlenwerten an, wobei diese Werte in jeweils einem einzelnen Punkt kombiniert werden. Power BI kann diese Datenpunkte gleichmäßig oder ungleichmäßig auf der horizontalen Achse verteilen. Dies hängt von den Daten ab.

In einem Blasendiagramm werden die Datenpunkte durch Blasen ersetzt, wobei die Blasengröße eine zusätzliche Datendimension darstellt.

Das unten angegebene Blasendiagramm gilt für Südamerika und enthält einen Vergleich des BIP pro Kopf (Y-Achse), der BIP-Summe (X-Achse) und der Bevölkerung nach Land in Südamerika.

![BIP und Bevölkerung für Südamerika als Blasendiagramm.](media/power-bi-visualization-best-practices/power-bi-bubble.png)

**Abbildung 62: BIP und Bevölkerung für Südamerika als Blasendiagramm**

Die Größe der Blasen steht für die Gesamtbevölkerung eines Lands. Brasilien weist die höchste Bevölkerungszahl (Blasengröße) und den größten Anteil am BIP von Südamerika auf. Dies ist der höchste Wert auf der X-Achse. Beachten Sie aber, dass das BIP pro Kopf für Uruguay, Chile und Argentinien höher als für Brasilien ist. Sie sind weiter oben auf der Y-Achse.

Wenn Sie eine Wiedergabeachse hinzufügen, können Sie so tun, als ob Sie Hans Rosling sind, und die Geschichte erzählen: [From Data to Insight & Impact: Showing Africa's Progress with Power View and PPI by Microsoft](https://www.youtube.com/watch?v=PbaDBJWCeD4) (Von Daten zu Einblicken und Auswirkungen: Anzeige des afrikanischen Fortschritts mit Power View und PPI von Microsoft). Ziehen Sie zum Hinzufügen einer Wiedergabeachse ein datetime-Feld in den Bereich **Wiedergabeachse**.

#### <a name="best-practices"></a>Bewährte Methoden

* Punkt- und Blasendiagramme eignen sich gut zum Erzählen von Geschichten. Für das Untersuchen von Daten sind sie dagegen nicht so nützlich. Stephen Few verweist darauf:

    > *Die Stärke dieses Ansatzes zeigt sich, wenn er verwendet wird, um eine Geschichte zu erzählen. Wenn Hans Rosling kommentiert, was im Diagramm passiert, während sich die Blasen bewegen und ihre Werte ändern, und auf die interessanten Aspekte hinweist, werden die Informationen zum Leben erweckt. Animierte Blasendiagramme sind aber deutlich weniger effektiv, was das Untersuchen und Interpretieren der Daten betrifft, wenn Sie dies allein versuchen. Vermutlich setzt Hans Rosling diese Methode nicht zum Ermitteln der Geschichten ein, sondern nur zum Erzählen, nachdem die Geschichte bereits steht. Wir können nicht auf mehr als eine Blase gleichzeitig achten, während sie sich bewegen. Also müssen wir die Animation immer wieder abspielen und versuchen, die Geschehnisse zu erfassen. Wir können Spuren für ausgewählte Blasen hinzufügen, damit wir den gesamten Weg der Blasen verfolgen können. Aber wenn Sie Spuren für eine höhere Zahl von Blasen aktivieren, wird das Diagramm schnell unübersichtlich. Mit diesen Informationen möchte ich im Wesentlichen darauf hinweisen, dass dies nicht die beste Möglichkeit ist, um diese Informationen zu Untersuchungs- und Analysezwecken anzuzeigen.*

* Fügen Sie Beschriftungen für die X- und Y-Achse ein, damit mehr Informationen zum Vermitteln der Geschichte vorhanden sind. Besonders bei Blasendiagrammen sind viele Komponenten involviert, und Beschriftungen tragen zum besseren Verständnis des visuellen Elements bei.

* Fügen Sie Datenbeschriftungen ein, damit das visuelle Element leichter interpretiert werden kann. Vor allem bei Blasendiagrammen kann es schwierig sein, zwischen ähnlichen Farben zu unterscheiden, wenn die Legende viele Einträge enthält. Im obigen visuellen Element sind die Legendenfarben für Suriname, Kolumbien und Ecuador ähnlich.

* Haben Sie ein Punktdiagramm erstellt, und sehen Sie nur einen Datenpunkt, unter dem alle Werte auf der X- und der Y-Achse zusammengefasst sind? Werden im Diagramm alle Werte auf einer einzelnen horizontalen oder vertikalen Linie zusammengefasst? Gehen Sie wie folgt vor, um die Aggregation zu beheben: Fügen Sie im Bereich **Details** ein Feld hinzu, damit Power BI erkennt, wie die Werte gruppiert werden sollen. Das Feld muss für jeden Punkt, der dargestellt werden soll, eindeutig sein. Hilfe finden Sie unter [Tutorial: Punktdiagramme und Blasendiagramme in Power BI](power-bi-visualization-scatter.md).

### <a name="treemap-charts"></a>Treemap-Diagramm

![Treemap-Diagramme.](media/power-bi-visualization-best-practices/power-bi-treemap.png)

Treemap-Diagramme können nützlich sein, um einen guten Überblick über die relative Größe verschiedener Komponenten zu erhalten, die ein Ganzes bilden – besonders wenn eine Gruppierung nach Kategorien möglich ist. Immer wenn Sie versuchen, einen neuen Geschäftsansatz zu verstehen, kann ein Treemap-Diagramm mit den Hauptkomponenten nützlich sein, um die Gesamtverteilung darzustellen.

Im ersten der unten angegebenen Diagramme sehen Sie sofort, dass „Brazil“ ungefähr die Hälfte des BIP von „South America“ beisteuert. Sie können auch sehen, dass „Columbia“ und „Chile“ ungefähr die gleichen Werte aufweisen.

Nehmen wir an, Sie wünschen einen breiteren Kontext und haben noch eine Vorstellung von dem Einfluss, der von den am stärksten beitragenden Ländern ausgeht. Erstellen Sie visuelle Hierarchien mit Kategorieelementen (Ländern), die in Regionen geschachtelt sind. Das zweite Treemap-Diagramm bietet uns in erster Linie einen Überblick über die relative Größe der Regionen. Dann sehen wir innerhalb jeder Region, welche einzelnen Länder am meisten beitragen. Wir sehen, dass es drei sehr große Regionen gibt: „Europe“, „Asia“ und „North America“. In diesen Regionen können wir einfach die führenden Länder/Regionen sehen.

Die wichtigste Einschränkung eines Treemap-Diagramms ist die Schwierigkeit, die kleineren Rechtecke zu vergleichen. Das Diagramm ist gut geeignet, um sich einen Überblick zu verschaffen. Balken- und Säulendiagramme sind aber meist die bessere Wahl, wenn es um präzise Informationen zur relativen Größe von unterschiedlichen Komponenten geht.

Das erste Treemap-Diagramm gibt einen groben Überblick über die BIP-Größenordnung. Es ist jedoch schwierig, spezifische Unterschiede zwischen den Ländern zu erkennen, insbesondere bei den kleineren, nicht beschrifteten Blättern. Für diese Daten, bei denen Sie eine einzelne Gruppierung vergleichen, ist ein Balken- oder Säulendiagramm wahrscheinlich besser geeignet.

![Vergleich des BIP für „South America“ per Treemap-Diagramm.](media/power-bi-visualization-best-practices/power-bi-treemap3.png)

**Abbildung 63: Vergleich des BIP für „South America“ per Treemap-Diagramm**

Als Nächstes haben wir „Region“ als weitere Datenebene hinzugefügt. Wir sehen den Gesamtbeitrag zum BPI nach Regionen. Außerdem können wir die relative Auswirkung in den Regionen sehen. Beachten Sie Folgendes: Bei Verwendung von nicht summativen Measures (z.B. Durchschnittswerten) stellt die Summe der Details unter Umständen nicht den tatsächlichen Wert auf Aggregatebene dar.

![BIP nach Region und Land als Strukturdiagramm.](media/power-bi-visualization-best-practices/power-bi-treemap2.png)

**Abbildung 64: BIP nach Region und Land als Strukturdiagramm**

Weitere Informationen zu Treemaps:

* [Discovering Business Intelligence Using Treemap Visualizations](http://www.perceptualedge.com/articles/b-eye/treemaps.pdf) (Ermitteln von Business Intelligence mit Treemapvisualisierungen)

* [Data Visualization Catalogue: Treemap](http://www.datavizcatalogue.com/methods/treemap.html#.VYhylI3bL7Y) (Katalog für Datenvisualierungen: Treemap)

### <a name="other-charts"></a>Andere Diagramme

#### <a name="pie-or-donut-charts"></a>Kreis- oder Ringdiagramme

![Kreis- oder Ringdiagramme](media/power-bi-visualization-best-practices/power-bi-donut.png)

Im Allgemeinen reichen Balken-, Säulen- und Liniendiagramme für die meisten Zwecke aus. Es ist bekannt, dass Kreis- und Ringdiagramme von Menschen nur schwer richtig interpretiert werden können. In der Tat können sie die Daten häufig verzerren. Vermeiden Sie es nach Möglichkeit, diese Diagramme zu verwenden. Stephen Few hat einen hervorragenden Artikel zur Geschichte und zu den Gefahren verfasst: [Save the Pies for Dessert](https://www.perceptualedge.com/articles/08-21-07.pdf) (Sparen Sie sich die Torte für das Dessert auf).

Er beschreibt einen Fall, in dem Kreisdiagramme nützlich sein können: beim Vergleichen der Beziehungen von Teilen zum Ganzen. Es ist kaum besser als ein 100-prozentiges gestapeltes Balkendiagramm.

Einen weiteren interessanten Artikel (und eine Animation) zu Kreisdiagrammen finden Sie auf der [Darkhorse Analytics-Website](http://www.darkhorseanalytics.com/blog/salvaging-the-pie).

#### <a name="radial-gauges--kpis"></a>Radiale Messgeräte und KPIs

![Radiale Messgeräte und KPIs.](media/power-bi-visualization-best-practices/power-bi-gauge.png)

Radiale Messgeräte scheinen gute visuelle Elemente zu sein, um die Leistung gegenüber einem Zielwert anzuzeigen, und sind in Dashboards für Führungskräfte beliebt. Sie haben allerdings zwei entscheidende Nachteile. Wie bei Kreisdiagrammen auch, ist es nicht einfach, den Winkel des schattierten Bereichs gegenüber dem vollständigen 180-Grad-Bogen oder der Ziellinie zu interpretieren. Außerdem wird viel Platz verbraucht, um eine einzelne Metrik anzuzeigen.

Eine gute Alternative ist ein einfaches visuelles KPI-Element:

![Ein einfaches visuelles KPI-Element.](media/power-bi-visualization-best-practices/power-bi-kpi.png)

Mit KPIs werden der Wert, der Status, der Zielwert und die Abweichung vom Zielwert und Trend gemeinsam in einem Bereich angezeigt. Die grüne Farbe ändert sich in Rot, wenn die Daten das Ziel nicht erreichen, oder ggf. in Gelb, wenn die Daten ein Zwischenziel erreichen. Das KPI-Element kann viel einfacher als das Messgerät gelesen und interpretiert werden.

Weitere Informationen finden Sie unter:

* [Radialmessgerät-Diagramme in Power BI](power-bi-visualization-radial-gauge-charts.md)

* [KPI-Visualisierung](power-bi-visualization-kpi.md)

## <a name="conclusion"></a>Fazit

Sie können diese bewährten Methoden jetzt in der Praxis testen. Bleiben Sie mit uns in Kontakt. Wir würden uns freuen, wenn Sie uns über Ihre bewährten Methoden informieren würden. Sind Sie anderer Meinung, oder haben Sie einen guten Grund, die Regeln zu brechen? Auch an diesen Erfahrungen sind wir interessiert.

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

### <a name="book-recommendations"></a>Buchempfehlungen

Es sind viele gute Bücher erhältlich, mit denen Teams ihre Kenntnisse über Entwurfstechniken für visuelle Elemente auffrischen können. Ein wichtiges Buch ist *Information Dashboard Design* (Entwurf eines Informationsdashboards) von Stephen Few. In zwei anderen Büchern geht er näher ins Detail: *Show Me the Numbers* (Zeigen Sie mir die Zahlen) und *Now You See It* (Jetzt erkennen Sie es). Stephen Few und andere haben sich von Edward R. Tufte inspirieren lassen, dessen Buch *The Visual Display of Quantitative Information* als Klassiker in diesem Bereich angesehen wird. Weitere Bücher von Edward R. Tufte sind *Visual Explanations*, *Envisioning Information* und *Beautiful Evidence*. Das neue Buch von Andy Kirk, *Data Visualization: A Handbook for Data Driven Design* ist eine weitere hervorragende Option. Weitere empfehlenswerte Autoren sind: Lachlan James, William McKnight und Boris Evelson (Forrester), Darkhorse Analytics.
