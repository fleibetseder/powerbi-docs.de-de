---
title: Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop
description: Erfahren Sie, wie Sie einen Drillthrough von einem Bericht zu einem anderen in Power BI Desktop durchführen.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6424180dde3dac0d6d2b66c8a9303810b6aa0dc6
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100099"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Verwenden der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop

Mit der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop können Sie kontextbezogen von einem Bericht zu einem anderen Bericht wechseln. Dies trifft zu, solange sich die Berichte im Power BI-Dienst im gleichen Arbeitsbereich oder der gleichen App befinden. Verwenden Sie die berichtsübergreifende Drillthroughfunktion zum Verbinden von zwei oder mehr Berichten mit verwandten Inhalten, und um den Filterkontext zusammen mit der berichtsübergreifenden Verbindung zu übergeben. In diesem Artikel erfahren Sie, wie Sie einen berichtsübergreifenden Drillthrough für Power BI-Berichte einrichten und welche Erfahrungen Benutzer mit der Verwendung des berichtsübergreifenden Drillthroughs machen.

![Screenshot der Drillthroughoption von Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Sie müssen die folgenden Definitionen verstehen, bevor wir mit dem Einrichten und Verwenden eines berichtsübergreifenden Drillthroughs beginnen:

* **Quellvisual:** Das Visual, das die Drillthroughaktion über das Visualkontextmenü aufruft.
* **Quellbericht:** Der Bericht, der das Quellvisual für den berichtsübergreifenden Drillthrough enthält.
* **Zielseite:** Die Seite, auf die ein Benutzer nach Initiieren einer Drillthroughaktion gelangt.
* **Zielbericht:** Der Bericht, der die Zielseite für den berichtsübergreifenden Drillthrough enthält.


> [!NOTE]
> Mit der berichtsübergreifenden Drillthroughfunktion in Power BI Desktop können Sie kontextbezogen von einem Bericht zu einem anderen Bericht wechseln. Dies trifft zu, solange sich die Berichte im Power BI-Dienst im gleichen Arbeitsbereich oder der gleichen App befinden. Dies betrifft nicht den Zugriff auf einzeln freigegebene Berichte in *Mein Arbeitsbereich* ([Für mich freigegebene Berichte](service-share-dashboards.md#share-a-dashboard-or-report)); stattdessen müssen Sie auf den Bericht in dem Arbeitsbereich zugreifen, in dem er ursprünglich freigegeben wurde.


## <a name="enable-cross-report-drillthrough"></a>Aktivieren des berichtsübergreifenden Drillthroughs

Um einen Bericht als Ziel eines berichtsübergreifenden Drillthroughs zu aktivieren, müssen Sie die Funktion für diesen Bericht im Fenster **Optionen** aktivieren. Wechseln Sie zu **Datei** > **Optionen und Einstellungen** > **Optionen**, und navigieren Sie dann zu **Berichtseinstellungen** in der Nähe des unteren Seitenrandes links.

Aktivieren Sie das Kontrollkästchen **Erlauben Sie, dass Visuals in diesem Bericht Drillthroughziele aus anderen Berichten verwenden**, wie in der folgenden Abbildung dargestellt.

![Screenshot des Fensters „Optionen“ mit hervorgehobenen „Berichtseinstellungen“](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Berichtsübergreifender Drillthrough ist jetzt aktiviert.

## <a name="set-up-cross-report-drillthrough"></a>Einrichten des berichtsübergreifenden Drillthroughs

Das Einrichten des berichtsübergreifenden Drillthroughs ähnelt dem Einrichten eines Drillthroughs innerhalb eines Berichts. Der Drillthrough wird auf der Zielseite aktiviert, sodass andere Visuals für den Drillthrough auf die aktivierte Seite zugreifen können. Die Schritte zum Erstellen eines Drillthroughs innerhalb eines einzelnen Berichts finden Sie unter [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md).

Um den Setupvorgang zu starten, müssen Sie zuerst folgende Schritte ausführen:

* Richten Sie eine Drillthroughzielseite ein, auf die andere Berichte im Arbeitsbereich oder in der App zugreifen können.
* Ermöglichen Sie, dass ein Bericht Drillthroughseiten erkennen kann, die sich außerhalb des Berichts befinden.

Im Abschnitt **Felder** des Bereichs **Visualisierungen** finden Sie Drillthroughoptionen, wie in der folgenden Abbildung dargestellt.

![Screenshot des Bereichs „Visualisierungen“ mit hervorgehobenen Drillthroughoptionen](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Der erste Schritt beim Aktivieren des Drillthroughs für eine Seite besteht darin, die Datenmodelle für Quell- und Zielberichte zu validieren. Stellen Sie Folgendes sicher: 

* Felder, die Sie übergeben möchten, sind in beiden Datenmodellen vorhanden.
* Die Namen der Felder und die Namen der Tabellen, zu denen sie gehören, sind identisch (die Zeichenfolgen müssen ebenfalls unter Berücksichtigung der Groß-/Kleinschreibung übereinstimmen).

Wenn Sie z. B. einen Filter für das Feld *Land* innerhalb der Tabelle *Geografie* übergeben möchten, müssen beide Modelle über eine Tabelle *Geografie* verfügen, die ein Feld *Land* enthält. Andernfalls müssen Sie den Feld- oder Tabellennamen im zugrunde liegenden Modell aktualisieren. Das einfache Aktualisieren des Anzeigennamens der Felder funktioniert für berichtsübergreifende Drillthroughs nicht ordnungsgemäß. (Beachten Sie, dass die Schemas in den einzelnen Berichten nicht identisch sein müssen.)

Zum Einstieg in das Setup müssen Sie die Zielseite vorbereiten. Wechseln Sie in Power BI Desktop zu der Seite, und stellen Sie sicher, dass der Drillthrougschalter **Berichtsübergreifend** auf **Ein** festgelegt ist. 

![Screenshot: Schalter „Berichtsübergreifend“ auf „Ein“ festgelegt](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Ziehen Sie als nächstes die Felder, die Sie als Drillthroughziel verwenden möchten, in den Zeichenbereich. Wählen Sie aus, ob das Feld als Kategorie oder zusammengefasst wie ein Measure verwendet werden soll. An diesem Punkt können Sie auswählen, ob Sie den Schalter **Alle Filter beibehalten** für das Visual deaktivieren möchten. Wenn Sie keine anderen angewendeten Filter vom Quellvisual an das Zieldrillthroughvisual übergeben möchten, wählen Sie **Aus** aus.

> [!NOTE]
> Wenn Sie die Seite nur für den berichtsübergreifenden Drillthrough verwenden, sollten Sie die Schaltfläche **Zurück** löschen, die automatisch hinzugefügt wird. Die Schaltfläche **Zurück** funktioniert nur für die Navigation innerhalb eines einzelnen Berichts. 

Nachdem Sie das Visual konfiguriert haben, stellen Sie sicher, dass Sie den Bericht speichern, wenn Sie sich im Power BI-Dienst befinden, oder speichern und veröffentlichen Sie den Bericht, wenn Sie Power BI Desktop verwenden.

Im vorherigen Abschnitt wurde das Aktivieren eines berichtsübergreifenden Drillthroughs für Power BI Desktop beschrieben (im Fenster **Optionen**). Wenn Sie den Power BI-Dienst zum Erstellen eines berichtsübergreifenden Drillthroughziels verwenden, müssen Sie Folgendes tun, um den berichtsübergreifenden Drillthrough zu aktivieren: 

1. Wählen Sie den Arbeitsbereich aus, in dem sich Zielbericht und Quellbericht befinden.
2. Wählen Sie **Berichte** aus.
3. Wählen Sie das **Einstellungen**-Symbol für den Quellbericht aus.
4. Stellen Sie sicher, dass der Schalter für den berichtsübergreifenden Drillthrough auf **Ein** gesetzt ist.
5. Speichern Sie den Bericht.

Fertig! Der Bericht ist für die berichtsübergreifende Drillthroughfunktion bereit. 

Im nächsten Abschnitt betrachten wir die Benutzeroberfläche aus der Perspektive des Benutzers.

## <a name="cross-report-drillthrough-experience"></a>Benutzeroberfläche für berichtsübergreifenden Drillthrough

Wenn Sie die Benutzeroberfläche für den berichtsübergreifenden Drillthrough für einen Bericht konfigurieren, können Sie die Funktion einsatzbereit machen.

Wählen Sie den Quellbericht im Power BI-Dienst aus, und wählen Sie dann eine Visualisierung aus, die das Feld bzw. die Felder so verwendet, wie Sie es beim Einrichten der Zielseite angegeben haben. Klicken Sie dann mit der rechten Maustaste auf einen Datenpunkt, um das Visualkontextmenü zu öffnen, und wählen Sie **Drillthrough** aus.

![Screenshot des Quellberichts im Power BI-Dienst, wobei „Drillthrough“ hervorgehoben ist](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Dann sehen Sie die Ergebnisse auf der Zielseite des berichtsübergreifenden Drillthroughs, so wie Sie sie beim Erstellen des Ziels eingerichtet haben. Die Ergebnisse werden den Drillthrougheinstellungen gemäß gefiltert.

> [!IMPORTANT]
> Power BI speichert Ziele des berichtsübergreifenden Drillthroughs zwischen. Wenn Sie Änderungen vornehmen, achten Sie darauf, dass Sie Ihren Browser aktualisieren, wenn nicht die erwarteten Drillthroughziele angezeigt werden. 

Berichtsübergreifende Ziele werden wie folgt formatiert: 

`Target Page Name [Target Report Name]`

Nachdem Sie die Zielseite ausgewählt haben, für die Sie einen Drillthrough durchführen möchten, wird Power BI zu dieser Seite weitergeleitet. Der Filterkontext wird auf der Grundlage der Einstellungen der Zielseite übergeben. 

Der Filterkontext aus dem Quellvisual kann Folgendes umfassen: 

* Filter auf Berichts-, Seiten- und Visualebene, die sich auf das Quellvisual auswirken. 
* Kreuzfilterung und übergreifende Hervorhebung, die sich auf das Quellvisual auswirken. 
* Slicer auf der Seite und Synchronisierungsslicer.
* URL-Parameter.

Wenn Sie zu dem Zielbericht für den Drillthrough gelangen, wendet Power BI nur Filter für Felder an, für die genaue Zeichenfolgenübereinstimmungen für Feldname und Tabellenname gefunden werden. Power BI wendet keine Kurzfilter aus dem Zielbericht an. Es wird jedoch Ihr standardmäßiges persönliches Lesezeichen angewendet, sofern vorhanden. Wenn Ihr standardmäßiges persönliches Lesezeichen z. B. einen Filter auf Berichtsebene für *Country = US* enthält, wendet Power BI diesen Filter an, bevor der Filterkontext aus dem Quellvisual angewendet wird. 

Für den berichtsübergreifenden Drillthrough übergibt Power BI den Filterkontext an alle Standardseiten des Zielberichts. Power BI übergibt den Filterkontext nicht für QuickInfo-Seiten, da QuickInfo-Seiten auf Basis des Quellvisuals gefiltert werden, das die QuickInfo aufruft.

Wenn Sie nach der berichtsübergreifenden Drillthroughaktion zum Quellbericht zurückkehren möchten, verwenden Sie die Schaltfläche **Zurück** des Browsers. 

## <a name="next-steps"></a>Nächste Schritte

Folgende Artikel könnten Sie ebenfalls interessieren:

* [Verwenden von Slicern in Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Verwenden der Drillthroughfunktion in Power BI Desktop](desktop-drillthrough.md)

