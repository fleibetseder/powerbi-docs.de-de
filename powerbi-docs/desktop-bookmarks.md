---
title: Verwenden von Lesezeichen in Power BI
description: Mit den Lesezeichen in Power BI Desktop können Sie Ansichten und Einstellungen in Ihren Berichten speichern und Präsentationen erstellen, die eine Geschichte erzählen.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 59d5ccd6a7179ca4c44210854fb66abb5371ac6c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61325937"
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Verwenden von Lesezeichen zum Teilen von Erkenntnissen und zum Erstellen von Präsentationen in Power BI 
Mit den **Lesezeichen** in Power BI können Sie die derzeit konfigurierte Ansicht einer Berichtsseite erfassen, einschließlich der Filterung und des Status von Visuals, und später zur Ansicht in diesem Status zurückkehren, indem Sie einfach das gespeicherte Lesezeichen auswählen. 

Sie können auch eine Sammlung von Lesezeichen erstellen, sie in der gewünschten Reihenfolge anordnen und dann die einzelnen Lesezeichen in einer Präsentation durchlaufen, um eine Reihe von Einsichten hervorzuheben oder die Geschichte, die Sie mit Ihren Visuals und Berichten erzählen möchten, zu präsentieren. 

![Lesezeichen in Power BI](media/desktop-bookmarks/bookmarks_01.png)

Lesezeichen können für viele unterschiedliche Zwecke hinzugefügt werden. Sie können sie zum Nachverfolgen ihrer Fortschritte beim Erstellen von Berichten verwenden (Lesezeichen lassen sich einfach hinzufügen, löschen und umbenennen). Oder Sie können Lesezeichen erstellen, um eine Präsentation wie in PowerPoint zu erzeugen, in der die Lesezeichen nacheinander aufgerufen werden, sodass Ihr Bericht eine Geschichte erzählt. Sie können Lesezeichen nach eigenem Ermessen auch für andere Zwecke nutzen.

> [!TIP]
> Informationen zur Verwendung persönlicher Lesezeichen im Power BI-Dienst finden Sie in der [Blogankündigung](https://powerbi.microsoft.com/blog/announcing-personal-bookmarks-in-the-power-bi-service/) des Features „Persönliche Lesezeichen“. 

### <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Aktivieren der Lesezeichenvorschau (Versionen vor März 2018)
Ab der Version von März 2018 sind Lesezeichen in Power BI Desktop allgemein verfügbar. 

Es wird immer empfohlen, auf das neueste Release zu aktualisieren. Wenn Ihre Power BI Desktop-Version älter ist, können Sie jedoch das neue **Lesezeichen**-Feature ab dem im **Oktober 2017** veröffentlichten Release von **Power BI Desktop** nutzen. Für Berichte, die Lesezeichen unterstützen, können Sie dieses Feature auch im **Power BI-Dienst** verwenden. Wenn Sie das Vorschaufeature aktivieren möchten, wählen Sie **Datei > Optionen und Einstellungen > Optionen > Vorschaufeatures** aus, und aktivieren Sie dann das Kontrollkästchen neben **Lesezeichen**. 

![Aktivieren von Lesezeichen im Fenster „Optionen“](media/desktop-bookmarks/bookmarks_02.png)

Zum Aktivieren der Lesezeichenvorschauversion müssen Sie **Power BI Desktop** neu starten, nachdem Sie die Auswahl vorgenommen haben.

## <a name="using-bookmarks"></a>Verwenden von Lesezeichen
Wählen Sie zum Verwenden von Lesezeichen das Menüband **Ansicht** aus, und aktivieren Sie dann das Kontrollkästchen für **Lesezeichenbereich**. 

![Aktivieren des Lesezeichenbereichs im Menüband „Ansicht“, um ihn anzuzeigen.](media/desktop-bookmarks/bookmarks_03.png)

Wenn Sie ein Lesezeichen erstellen, werden die folgenden Elemente mit dem Lesezeichen gespeichert:

* Die aktuelle Seite
* Filter
* Slicer, einschließlich Slicertyp (z.B. Dropdown oder Liste) und Slicerstatus
* Status der Auswahl des Visuals (z.B. Filter mit übergreifender Hervorhebung)
* Sortierreihenfolge
* Drilldownposition
* Sichtbarkeit (eines Objekts, im Bereich **Auswahl** festgelegt)
* Der Fokus- oder **Spotlightmodus** jedes angezeigten Objekts

Konfigurieren Sie eine Berichtsseite so, wie sie im Lesezeichen angezeigt werden soll. Sobald die Berichtsseite und die Visuals wie gewünscht angeordnet sind, wählen Sie im Bereich **Lesezeichen** die Option **Hinzufügen** aus, um ein Lesezeichen hinzufügen. 

![Hinzufügen eines Lesezeichens](media/desktop-bookmarks/bookmarks_04.png)

**Power BI Desktop** erstellt ein Lesezeichen und benennt es mit einem generischen Namen. Lesezeichen können einfach *umbenannt*, *gelöscht* oder *aktualisiert* werden. Wählen Sie dazu die Auslassungspunkte neben dem Namen des Lesezeichens aus, und wählen Sie im daraufhin angezeigten Menü eine Aktion aus.

![Auswählen des Untermenüs für ein Lesezeichen mithilfe der Auslassungspunkte](media/desktop-bookmarks/bookmarks_05.png)

Sobald ein Lesezeichen erstellt wurde, können Sie es anzeigen, indem Sie einfach im Bereich **Lesezeichen** auf das Lesezeichen klicken. 

Sie können auch auswählen, ob jedes Lesezeichen Eigenschaften von *Daten* anwendet, z.B. Filter und Datenschnitte, die *Anzeigeeigenschaften*, z.B. Spotlight und seine Sichtbarkeit, und Seitenänderungen, sodass die Seite angezeigt wird, die sichtbar war, als das Lesezeichen hinzugefügt wurde. Diese Funktionen sind nützlich, wenn Sie Lesezeichen verwenden, um zwischen Berichtsansichten oder Visuals zu wechseln – in diesem Fall möchten Sie die Dateneigenschaften wahrscheinlich deaktivieren, damit Filter nicht zurückgesetzt werden, wenn Benutzer durch Auswählen eines Lesezeichen zwischen Ansichten wechseln. 

Um solche Änderungen vorzunehmen, wählen Sie die Auslassungspunkte neben dem Namen des Lesezeichens aus, wie in der vorherigen Abbildung gezeigt, und dann aktivieren oder deaktivieren Sie das Häkchen neben *Daten*, *Anzeige* und anderen Steuerelementen. 

## <a name="arranging-bookmarks"></a>Anordnen von Lesezeichen
Beim Erstellen von Lesezeichen werden Sie möglicherweise feststellen, dass die Reihenfolge ihrer Erstellung nicht unbedingt die gleiche Reihenfolge ist, in der Sie sie dem Publikum präsentieren möchten. Dies ist kein Problem, da Sie die Reihenfolge der Lesezeichen leicht ändern können.

Ändern Sie einfach im Bereich **Lesezeichen** die Reihenfolge der Lesezeichen per Drag & Drop, wie in der folgenden Abbildung dargestellt. Die gelbe Leiste zwischen Lesezeichen gibt an, wo das gezogene Lesezeichen abgelegt wird.

![Ändern der Lesezeichen-Reihenfolge per Drag & Drop](media/desktop-bookmarks/bookmarks_06.png)

Die Reihenfolge der Lesezeichen kann wichtig werden, wenn Sie das Feature **Ansicht** für Lesezeichen verwenden, wie im nächsten Abschnitt beschrieben.

## <a name="bookmarks-as-a-slide-show"></a>Lesezeichen als Bildschirmpräsentation
Wenn Sie über eine Sammlung von Lesezeichen verfügen, die Sie nacheinander präsentieren möchten, können Sie im Bereich **Lesezeichen** die Option **Ansicht** auswählen, um eine Bildschirmpräsentation zu starten.

Im Modus **Ansicht** sind einige Features zu beachten:

1. Auf der Lesezeichen-Titelleiste am unteren Rand des Zeichenbereichs wird der Name des Lesezeichens angezeigt.
2. Die Lesezeichen-Titelleiste verfügt über Pfeile, mit denen Sie zum nächsten oder vorherigen Lesezeichen wechseln können.
3. Sie können den Modus **Ansicht** beenden, indem Sie im Bereich **Lesezeichen** die Option **Beenden** oder das **X** auf der Lesezeichen-Titelleiste auswählen. 

![Features der Lesezeichen-Titelleiste](media/desktop-bookmarks/bookmarks_07.png)

Im Modus **Ansicht** können Sie den Bereich **Lesezeichen** schließen (durch Klicken auf das „X“ in diesem Bereich), um mehr Platz für die Präsentation zu erhalten. Und im Modus **Ansicht** sind alle Visuals interaktiv und für die übergreifende Hervorhebung verfügbar, so wie bei der Interaktion mit ihnen. 

## <a name="visibility---using-the-selection-pane"></a>Sichtbarkeit – mithilfe des Bereichs „Auswahl“
Zusammen mit der Einführung von Lesezeichen wird auch der neue Bereich **Auswahl** eingeführt. Der Bereich **Auswahl** enthält eine Liste aller Objekte auf der aktuellen Seite und ermöglicht es Ihnen, das Objekt auszuwählen und anzugeben, ob ein bestimmtes Objekt sichtbar ist. 

![Aktivieren des Bereichs „Auswahl“](media/desktop-bookmarks/bookmarks_08.png)

Sie können mit dem Bereich **Auswahl** ein Objekt auswählen. Sie können außerdem die Sichtbarkeit eines Objekts aktivieren/deaktivieren, indem Sie auf das Augensymbol rechts neben dem Visual klicken. 

![Bereich „Auswahl“](media/desktop-bookmarks/bookmarks_09.png)

Beim Hinzufügen eines Lesezeichens wird der Sichtbarkeitsstatus jedes Objekts basierend auf der Einstellung im Bereich **Auswahl** gespeichert. 

Es ist wichtig zu beachten, dass Berichtsseiten weiterhin durch **Datenschnitte** gefiltert werden, auch wenn sie nicht sichtbar sind. Sie können daher viele verschiedene Lesezeichen mit unterschiedlichen Datenschnitteinstellungen erstellen und eine einzelne Berichtsseite in verschiedenen Lesezeichen sehr unterschiedlich darstellen (und jeweils andere Erkenntnisse hervorheben).

## <a name="bookmarks-for-shapes-and-images"></a>Lesezeichen für Formen und Bilder
Sie können auch Formen und Bilder mit Lesezeichen verknüpfen. Wenn Sie dann auf ein Objekt klicken, wird das mit dem Objekt verknüpfte Lesezeichen angezeigt. Dies kann bei der Arbeit mit Schaltflächen besonders hilfreich sein; weitere Informationen finden Sie im Artikel [Verwenden von Schaltflächen in Power BI](desktop-buttons.md). 

Wenn Sie einem Objekt ein Lesezeichen zuweisen möchten, wählen Sie das Objekt aus, und erweitern Sie dann wie in der folgenden Abbildung dargestellt den Abschnitt **Aktion** im Bereich **Form formatieren**.

![Hinzufügen von Lesezeichenlink zu einem Objekt](media/desktop-bookmarks/bookmarks_10.png)

Nachdem Sie den Schieberegler **Aktion** auf **Ein** gestellt haben, können Sie auswählen, ob das Objekt eine Schaltfläche „Zurück“, ein Lesezeichen oder ein Frage- und Antwortbefehl ist. Wenn Sie „Lesezeichen“ wählen, können Sie das Lesezeichen auswählen, mit dem das Objekt verknüpft wird.

Das Hinzufügen von Lesezeichen, die mit Objekten verknüpft sind, bietet Ihnen viele interessante Möglichkeiten. Sie können auf der Berichtsseite ein visuelles Inhaltsverzeichnis erstellen oder unterschiedliche Ansichten (z.B. Visualtypen) der gleichen Informationen erstellen, indem Sie einfach auf ein Objekt klicken.

Im Bearbeitungsmodus können Sie bei gedrückter STRG-TASTE klicken, um dem Link zu folgen. Außerhalb des Bearbeitungsmodus brauchen Sie nur auf das Objekt klicken, um dem Link zu folgen. 

## <a name="bookmark-groups"></a>Lesezeichengruppen

Ab dem Release vom August 2018 von **Power BI Desktop** können Sie Lesezeichengruppen erstellen und verwenden. Eine Lesezeichengruppe ist eine von Ihnen angegebene Sammlung von Lesezeichen, die als Gruppe angezeigt und organisiert werden kann. 

Halten Sie zum Erstellen einer Lesezeichengruppe die STRG-Taste gedrückt, und wählen Sie die Lesezeichen aus, die Sie verwenden möchten. Klicken Sie dann auf die Auslassungspunkte neben den ausgewählten Lesezeichen, und wählen Sie im angezeigten Menü **Gruppe** aus.

![Erstellen einer Lesezeichengruppe](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** nennt die Gruppe automatisch *Gruppe 1*. Sie können die Gruppe allerdings leicht umbenennen, indem Sie auf den Namen doppelklicken.

![Umbenennen einer Lesezeichengruppe](media/desktop-bookmarks/bookmarks_16.png)

Bei jeder beliebigen Lesezeichengruppe wird durch Klicken auf den Namen der Lesezeichengruppe nur die Gruppe von Lesezeichen erweitert oder zugeklappt. Der Gruppenname selbst stellt kein Lesezeichen dar. 

Bei Verwendung des Features **Ansicht** für Lesezeichen gilt Folgendes:

* Wenn Sie unter Lesezeichen **Ansicht** auswählen und sich das ausgewählte Lesezeichen in einer Gruppe befindet, werden in dieser Ansicht nur die Lesezeichen *in dieser Gruppe* angezeigt. 

* Wenn sich das ausgewählte Lesezeichen nicht in einer Gruppe auf der obersten Ebene befindet (wie z.B. der Name einer Lesezeichengruppe), werden alle Lesezeichen, und zwar auch diejenige aller Gruppen, für den gesamten Bericht angezeigt. 

Gehen Sie wie folgt vor, um die Gruppierung von Lesezeichen aufzuheben: Wählen Sie ein beliebiges Lesezeichen in einer Gruppe aus, und klicken Sie zuerst auf die Auslassungspunkte und anschließend auf **Gruppierung aufheben** im angezeigten Menü. 

![Aufheben der Gruppierung einer Lesezeichengruppe](media/desktop-bookmarks/bookmarks_17.png)

Beachten Sie, dass alle Lesezeichen aus der Gruppe entfernt werden (die Gruppe wird gelöscht, die Lesezeichen selbst allerdings nicht), wenn Sie für ein Lesezeichen in einer Gruppe die **Gruppierung aufheben**. Um also ein einzelnes Lesezeichen aus einer Gruppe zu entfernen, müssen Sie für jedes Mitglied dieser Gruppe die **Gruppierung aufheben**, wodurch die Gruppierung entfernt wird. Wählen Sie dann die Elemente aus, die in der neuen Gruppe enthalten sein sollen (STRG-Taste drücken und jedes Lesezeichen anklicken), und klicken erneut auf **Gruppe**. 


## <a name="using-spotlight"></a>Verwenden von Spotlight
**Spotlight** ist ein weiteres Feature, das zusammen mit Lesezeichen veröffentlicht wird. Mit **Spotlight** können Sie die Aufmerksamkeit auf ein bestimmtes Diagramm lenken, z.B. bei der Präsentation der Lesezeichen im Modus **Ansicht**.

Lassen Sie uns **Spotlight** mit dem **Fokusmodus** vergleichen, um die Unterschiede festzustellen.

1. Im **Fokusmodus** können Sie das Symbol **Fokusmodus** auswählen, um den gesamten Zeichenbereich mit einem Visual auszufüllen.
2. Mit **Spotlight** können Sie ein Visual in seiner ursprünglichen Größe hervorheben, indem Sie alle anderen Visuals auf der Seite bis nahezu zur Transparenz verblassen lassen. 

![Vergleichen von Fokusmodus und Spotlight](media/desktop-bookmarks/bookmarks_11.png)

Wenn für das Visual in der vorherigen Abbildung auf das Symbol **Fokus** geklickt wird, sieht die Seite folgendermaßen aus:

![Fokusmodus](media/desktop-bookmarks/bookmarks_12.png)

Wenn hingegen im Menü mit den drei Auslassungspunkten für das Visual **Spotlight** ausgewählt wird, sieht die Seite wie in dieser Abbildung aus:

![Spotlightmodus](media/desktop-bookmarks/bookmarks_13.png)

Wenn beim Hinzufügen eines Lesezeichens einer der beiden Modi ausgewählt wird, wird dieser Modus (Fokus oder Spotlight) im Lesezeichen gespeichert.

## <a name="bookmarks-in-the-power-bi-service"></a>Lesezeichen im Power BI-Dienst
Wenn Sie im **Power BI-Dienst** einen Bericht mit mindestens einem Lesezeichen veröffentlichen, können Sie diese Lesezeichen im **Power BI-Dienst** anzeigen und mit ihnen interagieren. Wenn in einem Bericht Lesezeichen verfügbar sind, können Sie **Ansicht > Auswahlbereich** oder **Ansicht > Lesezeichenbereich** auswählen, um den jeweiligen Bereich anzuzeigen.

![Anzeigen des Lesezeichen- und Auswahlbereichs im Power BI-Dienst](media/desktop-bookmarks/bookmarks_14.png)

Der **Lesezeichenbereich** bietet im **Power BI-Dienst** die gleichen Funktionen wie in **Power BI Desktop**, einschließlich der Möglichkeit, durch Auswahl von **Ansicht** die Lesezeichen wie in einer Bildschirmpräsentation nacheinander anzuzeigen.

Beachten Sie, dass Sie zum Navigieren zwischen den Lesezeichen die graue Lesezeichen-Titelleiste verwenden müssen, und nicht die schwarzen Pfeile (die schwarzen Pfeile dienen der Navigation zwischen Berichtsseiten, nicht zwischen Lesezeichen).

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen
Für dieses Release von **Lesezeichen** gelten einige Einschränkungen und Überlegungen.

* Die meisten benutzerdefinierten Visualisierungen sollten mit Lesezeichen gut funktionieren. Wenn bei einem Lesezeichen Probleme in Zusammenhang mit einem benutzerdefinierten Visual auftreten sollten, bitten Sie den Ersteller des benutzerdefinierten Visuals, dafür zu sorgen, dass sein Visual Lesezeichen unterstützt. 
* Wenn Sie einer Berichtsseite nach dem Erstellen eines Lesezeichens ein Visual hinzufügen, wird das Visual in seinem Standardstatus angezeigt. Dies bedeutet auch, dass beim Anwenden eines Datenschnitts auf einer Seite, auf der Sie zuvor Lesezeichen erstellt haben, das Verhalten des Datenschnitts seinem Standardstatus entspricht.
* Das Verschieben von Visuals nach dem Erstellen des Lesezeichens wird im Lesezeichen wiedergegeben. 


## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Features, die Lesezeichen ähneln oder mit diesen interagieren, finden Sie in den folgenden Artikeln:

* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)
* [Anzeigen einer Dashboardkachel oder eines Berichtsvisuals im Fokusmodus](consumer/end-user-focus.md)

