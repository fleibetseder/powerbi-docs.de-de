---
title: 'Tutorial: Erstellen eines Machine Learning-Modells in Power BI (Vorschauversion)'
description: In diesem Tutorial erstellen Sie ein Machine Learning-Modell in Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406746"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Erstellen eines Machine Learning-Modells in Power BI (Vorschauversion)

In diesem Tutorialartikel verwenden Sie **Automatisiertes maschinelles Lernen** zum Erstellen und Anwenden eines binären Vorhersagemodells in Power BI. Das Tutorial enthält Anleitungen zum Erstellen eines Power BI-Dataflows und zum Verwenden der im Dataflow definierten Entitäten, um ein Machine Learning-Modell direkt in Power BI zu trainieren und zu überprüfen. Wir verwenden dieses Modell dann zur Bewertung, um Vorhersagen zu generieren.

Zunächst erstellen Sie ein Machine Learning-Modell für die binäre Vorhersage der Kaufabsichten von Onlinekunden auf Basis eines Satzes ihrer Onlinesitzungsattribute. Für diese Übung wird ein Benchmark-Machine Learning-Dataset verwendet. Sobald ein Modell trainiert ist, generiert Power BI automatisch einen Überprüfungsbericht, in dem die Modellergebnisse erläutert werden. Sie können dann den Überprüfungsbericht auswerten und das Modell zur Bewertung auf die Daten anwenden.

Dieses Tutorial umfasst folgende Schritte:

> [!div class="checklist"]
> * Erstellen eines Dataflows mit den Eingabedaten
> * Erstellen und Trainieren eines Machine Learning-Modells
> * Auswerten des Modellüberprüfungsberichts
> * Anwenden des Modells auf eine Dataflowentität
> * Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

## <a name="create-a-dataflow-with-the-input-data"></a>Erstellen eines Dataflows mit den Eingabedaten

Der erste Teil dieses Tutorials besteht darin, einen Dataflow mit Eingabedaten zu erstellen. Dieser Vorgang erfordert einige Schritte, wie in den folgenden Abschnitten beschrieben, beginnend mit dem Erfassen der Daten.

### <a name="get-data"></a>Daten abrufen

Der erste Schritt beim Erstellen eines Dataflows besteht darin, dass Sie Ihre Datenquellen bereithalten. In unserem Fall verwenden wir ein Machine Learning-Dataset aus einer Reihe von Onlinesitzungen, wobei es in einigen davon zum Kauf kam. Das Dataset enthält eine Reihe von Attributen zu diesen Sitzungen, die wir zum Trainieren unseres Modells verwenden.

Sie können das Dataset von der UC Irvine-Website herunterladen.  Auch dies steht für den Zweck dieses Tutorials über den folgenden Link zur Verfügung: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Erstellen der Entitäten

Um die Entitäten in Ihrem Dataflow zu erstellen, melden Sie sich beim Power BI-Dienst an, und navigieren Sie zu einem Arbeitsbereich Ihrer dedizierten Kapazität, in dem die KI-Vorschau aktiviert ist.

Wenn Sie noch keinen Arbeitsbereich haben, können Sie einen Arbeitsbereich erstellen, indem Sie im Power BI-Dienst im linken Navigationsmenü **Arbeitsbereiche** und im dann angezeigten Bereich am unteren Rand **App-Arbeitsbereich erstellen** auswählen. Daraufhin wird rechts ein Bereich zur Eingabe der Details des Arbeitsbereichs geöffnet. Geben Sie einen Namen für den Arbeitsbereich ein, und wählen Sie **Erweitert** aus. Bestätigen Sie mithilfe des Optionsfelds „Dedizierte Kapazität“, dass der Arbeitsbereich dedizierte Kapazität verwendet und einer Instanz mit dedizierter Kapazität zugewiesen ist, für die die KI-Vorschau aktiviert ist. Klicken Sie auf **Speichern**.

![Arbeitsbereich erstellen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Sobald der Arbeitsbereich erstellt ist, können Sie unten rechts im Begrüßungsbildschirm **Überspringen** auswählen, wie in der folgenden Abbildung gezeigt.

![Überspringen, wenn Sie über einen Arbeitsbereich verfügen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Wählen Sie die Registerkarte **Dataflows (Vorschau)** aus. Wählen Sie die Schaltfläche **Erstellen** oben rechts im Arbeitsbereich und dann die Schaltfläche **Dataflow** aus.

![Erstellen des Dataflows](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Wählen Sie **Neue Entitäten hinzufügen** aus. Damit wird ein **Power Query**-Editor im Browser gestartet.

![Hinzufügen einer neuen Entität](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Wählen Sie **Text-/CSV-Datei** als Datenquelle aus, wie in der folgenden Abbildung dargestellt.

![Ausgewählte Text-/CSV-Datei](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

Fügen Sie im Feld **Mit einer Datenquelle verbinden**, das als Nächstes angezeigt wird, den folgenden Link zur Datei *online_shoppers_intention.csv* in das Feld **Dateipfad oder URL** ein, und wählen Sie dann **Weiter** aus.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Dateipfad](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Der Power Query-Editor zeigt eine Vorschau der Daten aus der CSV-Datei an. Wählen Sie **Tabelle transformieren** im Menübefehlsband und im dann angezeigten Menü **Erste Zeile als Überschriften verwenden** aus. Dadurch wird der Abfrageschritt _Höher gestufte Header_ im Abschnitt **Angewendete Schritte** rechts im Bildschirm hinzugefügt. Sie können die Abfrage mit einen benutzerfreundlicheren Namen umbenennen, indem Sie den Wert im Feld **Name** im rechten Bereich ändern. Beispielsweise könnten Sie den Abfragenamen in _Online Visitor_ (Onlinebesucher) ändern.

![Ändern in einen benutzerfreundlichen Namen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Einige der Attributdatentypen in diesem Dataset sind _numerisch_ oder _boolesch_, obwohl diese möglicherweise von **Power Query** als Zeichenfolgen interpretiert werden. Wählen Sie das Attributtypsymbol am oberen Rand der Spaltenkopfzeilen aus, um die unten aufgeführten Spalten in die folgenden Typen zu ändern:

* **Dezimalzahl:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False:** Weekend; Revenue

![Ändern des Datentyps](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Das von uns trainierte **binäre Vorhersagemodell** erfordert ein boolesches Feld als Bezeichnung, die die Ergebnisse aus den vergangenen Beobachtungen identifiziert. In diesem Dataset gibt das Attribut _Revenue_ (Umsatz) den Kauf an, und dieses Attribut ist bereits als boolescher Wert verfügbar. Darum müssen wir keine berechnete Spalte für die Bezeichnung hinzufügen. In anderen Datasets müssen Sie möglicherweise vorhandene Bezeichnungsattribute in eine boolesche Spalte umwandeln.

Wählen Sie die Schaltfläche **Fertig** aus, um den Power Query-Editor zu schließen. Dadurch wird die Liste der Entitäten mit den von uns hinzugefügten _Online Visitor_-Daten angezeigt. Wählen Sie in der oberen rechten Ecke **Speichern** aus, geben Sie einen Namen für den Dataflow an, und wählen Sie dann im Dialogfeld die Option **Speichern** aus, wie in der folgenden Abbildung gezeigt.

![Speichern des Dataflows](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Aktualisieren des Dataflows

Beim Speichern des Dataflows wird eine Benachrichtigung angezeigt, die das Speichern bestätigt. Wählen Sie **Jetzt aktualisieren** aus, um Daten aus der Quelle im Dataflow zu erfassen.

![Jetzt aktualisieren](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Wählen Sie **Schließen** in der oberen rechten Ecke aus, und warten Sie, bis die Aktualisierung des Dataflows abgeschlossen ist.

Sie können Ihren Dataflow auch mit den **Aktionen**-Befehlen aktualisieren. Der Dataflow zeigt den Zeitstempel an, wenn die Aktualisierung abgeschlossen ist.

![Zeitstempel der Aktualisierung](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Erstellen und Trainieren eines Machine Learning-Modells

Wählen Sie den Dataflow aus, sobald die Aktualisierung abgeschlossen ist. Wählen Sie zum Hinzufügen eines Machine Learning-Modells die Schaltfläche **ML-Modell anwenden** in der Liste **Aktionen** für die Basisentität aus, die die Trainingsdaten und Bezeichnungsinformationen enthält, und wählen Sie dann **Machine Learning-Modell hinzufügen** aus.

![Machine Learning-Modell hinzufügen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Der erste Schritt beim Erstellen unseres Machine Learning-Modells besteht darin, die Verlaufsdaten zu identifizieren, einschließlich des Bezeichnungsfelds, das Sie vorhersagen möchten. Das Modell wird erstellt, indem es aus diesen Daten lernt.

Im Fall des Datasets, das wir verwenden, ist dies das Feld **Revenue**. Wählen Sie **Revenue** als Wert für „Feld für historisches Ergebnis“ aus, und wählen Sie dann **Weiter** aus.

![Auswählen von Verlaufsdaten](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Als Nächstes müssen wir den Typ des zu erstellenden Machine Learning-Modells auswählen. Power BI analysiert die Werte im „Feld für historisches Ergebnis“, das Sie identifiziert haben, und schlägt die Machine Learning-Modelltypen vor, die erstellt werden können, um dieses Feld vorherzusagen.

Da wir in diesem Fall ein binäres Ergebnis vorhersagen, nämlich ob ein Benutzer einen Einkauf durchführt oder nicht, wählen Sie **Binäre Vorhersage** für den Modelltyp und dann „Weiter“ aus.

![Ausgewählte binäre Vorhersage](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Als Nächstes führt Power BI eine vorläufige Überprüfung der Daten durch und schlägt die Eingaben vor, die das Modell verwenden könnte. Sie haben die Möglichkeit, die für das Modell verwendeten Eingabefelder anzupassen. Um in unserem zusammengestellten Dataset alle Felder auszuwählen, aktivieren Sie das Kontrollkästchen neben dem Entitätsnamen. Wählen Sie **Weiter** aus, um die Eingaben zu akzeptieren.

![Auswählen von „Weiter“](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Im letzten Schritt müssen wir einen Namen für unser Modell sowie die benutzerfreundlichen Bezeichnungen für die Ergebnisse angeben, die im automatisch generierten Bericht verwendet werden, der die Ergebnisse der Modellüberprüfung zusammenfasst. Als Nächstes müssen wir das Modell mit _Purchase Intent Prediction_ (Kaufabsichtsvorhersage) benennen und die „true“- und „false“-Bezeichnungen mit _Purchase_ (Kauf) und _No-Purchase_ (Kein Kauf). Klicken Sie auf **Speichern**.

![Speichern des Modells](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Unser Machine Learning-Modell ist jetzt zum Training bereit. Wählen Sie **Jetzt aktualisieren** aus, um das Trainieren des Modells zu starten.

![Jetzt aktualisieren](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Der Trainingsprozess beginnt mit der Stichprobenentnahme und Normalisierung ihrer Verlaufsdaten sowie dem Aufteilen Ihres Datasets in zwei neue Entitäten *Purchase Intent Prediction Training Data* (Trainingsdaten für Kaufabsichtsvorhersage) und *Purchase Intent Prediction Testing Data* (Testdaten für Kaufabsichtsvorhersage).

Abhängig von der Größe des Datasets kann der Trainingsprozess zwischen einigen Minuten und einigen Stunden dauern. An diesem Punkt können Sie das Modell auf der Registerkarte **Machine Learning-Modelle** des Dataflows sehen. Der Status _Bereit_ zeigt an, dass das Modell in eine Warteschlange eingereiht wurde oder gerade trainiert wird.

![Bereit zum Training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Während das Modell trainiert wird, können Sie den Dataflow nicht anzeigen oder bearbeiten. Sie können über den Status des Dataflows feststellen, ob das Modell trainiert und überprüft wird. Dieser wird als laufende Datenaktualisierung auf der Registerkarte **Dataflows** des Arbeitsbereichs angezeigt.

![In Bearbeitung](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Sobald das Modelltraining abgeschlossen ist, wird für den Dataflow eine aktualisierte Aktualisierungszeit angezeigt. Sie können überprüfen, ob das Modell trainiert ist, indem Sie zur Registerkarte **Machine Learning-Modelle** im Dataflow navigieren. Für das von Ihnen erstellte Modell sollte der Status **Trainiert** angezeigt werden, und die Zeitangabe **Zuletzt trainiert** sollte jetzt aktualisiert sein.

![Zuletzt trainiert](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Auswerten des Modellüberprüfungsberichts

Um den Modellüberprüfungsbericht auszuwerten, wählen Sie in den **Machine Learning-Modellen** die Schaltfläche **Leistungsbericht anzeigen und Modell anwenden** in der Spalte **Aktionen** für das Modell aus. In diesem Bericht wird beschrieben, wie das Machine Learning-Modell wahrscheinlich durchgeführt wird.

Wählen Sie auf der Seite **Modellleistung** des Berichts **Wichtigste Einflussfaktoren** aus, um die wichtigsten Vorhersagen für das Modell anzuzeigen. Sie können eine der Vorhersagen auswählen, um zu sehen, wie die Ergebnisverteilung mit dieser Vorhersage verknüpft ist.

![Modellleistung](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Sie können den **Wahrscheinlichkeitsschwellenwert**-Slicer auf der Seite „Modellleistung“ verwenden, um seine Auswirkung auf die Genauigkeit und den Abruf des Modells zu untersuchen.

![Wahrscheinlichkeitsschwellenwert](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Die anderen Seiten des Berichts beschreiben die statistischen Leistungsmetriken für das Modell.

Der Bericht enthält auch eine Seite mit Trainingsdetails, die die verschiedenen ausgeführten Iterationen beschreibt, wie Features aus den Eingaben extrahiert und welche Hyperparameter für das endgültige Modell verwendet wurden.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Anwenden des Modells auf eine Dataflowentität

Wählen Sie oben im Bericht die Schaltfläche **Modell anwenden** aus, um dieses Modell aufzurufen, wenn der Dataflow aktualisiert wird. Im Dialogfeld **Anwenden** können Sie die Zielentität angeben, die die Quelldaten enthält, auf die das Modell angewendet werden soll.

![Modell anwenden](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Nach Aufforderung müssen Sie den Dataflow **Aktualisieren**, um eine Vorschau der Ergebnisse Ihres Modells anzuzeigen.

Durch das Anwenden des Modells wird eine neue Entität erstellt, wobei das Suffix **enriched <Modellname>** (erweitert) der Entität angehängt wird, auf die Sie das Modell angewendet haben. In unserem Fall wird durch das Anwenden des Modells auf die **OnlineShoppers**-Entität eine **OnlineShoppers enriched Purchase Intent Prediction** erstellt, die die vorhergesagte Ausgabe des Modells einschließt.

Wenn Sie ein binäres Vorhersagemodell anwenden, werden drei Spalten mit dem vorhergesagten Ergebnis, der Wahrscheinlichkeitsbewertung und den wichtigsten datensatzspezifischen Einflussfaktoren für die Vorhersage hinzugefügt, wobei jeweils der angegebene Spaltenname vorangestellt wird.

![Drei Ergebnisspalten](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Aufgrund eines bekannten Problems sind die bewerteten Ausgabespalten in der erweiterten Entität nur über Power BI Desktop zugänglich. Um diese im Dienst in der Vorschau anzuzeigen, müssen Sie eine besondere Vorschauentität verwenden.

Sobald die Dataflowaktualisierung abgeschlossen ist, können Sie die **OnlineShoppers enriched Purchase Intent Prediction Preview**-Entität auswählen, um die Ergebnisse anzuzeigen.

![Anzeigen der Ergebnisse](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

Wenn Sie die bewertete Ausgabe Ihres Machine Learning-Modells verwenden möchten, können Sie mit dem Dataflows-Connector eine Verbindung mit Ihrem Dataflow über den Power BI-Desktop herstellen. Mit der **OnlineShoppers enriched Purchase Intent Prediction**-Entität können Sie jetzt die Vorhersagen aus dem Modell in Power BI-Berichte einbinden.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie mithilfe der folgenden Schritte ein binäres Vorhersagemodell in Power BI erstellt und angewendet:

* Erstellen eines Dataflows mit den Eingabedaten
* Erstellen und Trainieren eines Machine Learning-Modells
* Auswerten des Modellüberprüfungsberichts
* Anwenden des Modells auf eine Dataflowentität
* Verwenden der bewerteten Ausgabe des Modells in einem Power BI-Bericht

Weitere Informationen zur Machine Learning-Automatisierung in Power BI finden Sie unter [Automatisiertes Machine Learning in Power BI (Vorschauversion)](service-machine-learning-automated.md).
