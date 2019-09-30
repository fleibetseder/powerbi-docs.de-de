---
title: Automatisiertes Machine Learning in Power BI (Vorschauversion)
description: Erfahren Sie, wie Sie automatisiertes maschinelles Lernen (AutoML) in Power BI nutzen
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236448"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Automatisiertes Machine Learning in Power BI (Vorschauversion)

Automatisiertes maschinelles Lernen (AutoML) für Dataflows ermöglicht Geschäftsanalysten direkt in Power BI, Machine Learning-Modellen zu trainieren, zu prüfen und aufzurufen. Dazu gehört eine einfache Umgebung zur Erstellung eines neuen ML-Modells, in dem Analysten ihre Dataflows verwenden können, um die Eingabedaten zum Trainieren des Modells festzulegen. Der Dienst extrahiert automatisch die wichtigsten Features, wählt einen geeigneten Algorithmus aus, optimiert das ML-Modell und prüft es. Nach dem Trainieren eines Modells erstellt Power BI automatisch einen Bericht, der die Ergebnisse der Prüfung enthält und Analysten die Leistung und Ergebnisse erklärt. Das Modell kann anschließend für alle neuen oder aktualisierten Daten im Dataflow aufgerufen werden.

![Bildschirm zum maschinellen Lernen](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automatisiertes maschinelles Lernen ist nur für Datenflows verfügbar, die in Power BI Premium und Embedded gehostet werden. In dieser Vorschauversion ermöglicht Ihnen AutoML das Trainieren von Machine Learning-Modellen für die Modelle „Binäre Vorhersage“, „Klassifizierung“ und „Regression“.

## <a name="working-with-automl"></a>Arbeiten mit AutoML

[Power BI-Dataflows](service-dataflows-overview.md) lassen eine Self-Service-Datenaufbereitung durch Big Data-Analysen zu. AutoML ermöglicht Ihnen das Profitieren von Ihrer Anstrengungen zur Datenaufbereitung für das Erstellen von Machine Learning-Modellen direkt in Power BI.

AutoML in Power BI ermöglicht Datenanalysten den Einsatz von Dataflows, um Machine Learning Modelle in vereinfachter Weise zu erstellen, wobei nur Power BI-Fertigkeiten genutzt werden. Der größte Teil der Data Science hinter der Erstellung der ML-Modelle wird von Power BI automatisiert, und zwar mithilfe Vorkehrungen, die sicherstellen, dass das produzierte Modell eine gute Qualität aufweist. Außerdem erhalten Sie transparent einen vollständigen Einblick in den Prozess, der zur Erstellung Ihres ML-Modells verwendet wird.

AutoML unterstützt für Dataflows das Erstellen von Modellen der Typen **Binäre Vorhersage**, **Klassifizierung** und **Regression**. Dies sind beaufsichtigte Machine Learning-Modelltypen, was bedeutet, dass sie aus den bekannten Ergebnissen früherer Beobachtungen lernen, um die Ergebnisse anderer Beobachtungen vorherzusagen. Das Eingabedataset zum Trainieren eines AutoML-Modells besteht aus einer Reihe von Datensätzen, die mit den bekannten Ergebnissen **beschriftet**  sind.

AutoML in Power BI integriert [automatisiertes ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) aus [Azure Machine Learning Service](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml), um Ihre ML-Modelle zu erstellen. Sie benötigen jedoch kein Azure-Abonnement, um AutoML in Power BI zu nutzen. Der Prozess des Trainings und Hostings der ML-Modelle wird vollständig vom Power BI-Dienst verwaltet.

Nachdem ein ML-Modell trainiert wurde, erstellt AutoML automatisch einen Power BI-Bericht, der die wahrscheinliche Leistung Ihres ML-Modells erklärt. AutoML legt den Schwerpunkt auf Erklärbarkeit, indem es die wichtigsten Einflussfaktoren unter Ihren Eingaben hervorhebt, die die von Ihrem Modell gelieferten Vorhersagen beeinflussen. Der Bericht enthält auch Schlüsselmetriken für das Modell, die vom ML-Modelltyp abhängen.

Andere Seiten des generierten Berichts zeigen eine statistische Zusammenfassung zum Modell und die Trainingsdetails. Die statistische Zusammenfassung ist von Interesse für Benutzer, die die üblichen Data Science Performance-Measures für das Modell einsehen möchten. In den Trainingsdetails sind alle Iterationen mit den zugehörigen Modellierungsparametern zusammengefasst, die zur Erstellung Ihres Modells erfolgt sind. Außerdem wird beschrieben, wie die einzelnen Eingaben zur Erstellung des ML-Modells verwendet wurden.

Danach können Sie Ihr ML-Modell auf Ihre Daten anwenden, um es zu bewerten. Bei Aktualisierung des Dataflows werden die Vorhersagen aus Ihrem ML-Modell automatisch auf Ihre Daten angewendet. Power BI bietet auch eine individualisierte Erklärung für jeden spezifischen Vorhersagewert, den das ML-Modell liefert.

## <a name="creating-a-machine-learning-model"></a>Erstellen eines Machine Learning-Modells

In diesem Abschnitt wird das Erstellen eines AutoML-Lernmodells beschrieben. 

### <a name="data-prep-for-creating-an-ml-model"></a>Datenaufbereitung zum Erstellen eines ML-Modells

Um ein Machine Learning-Modell in Power BI zu erstellen, müssen Sie zunächst einen Dataflow für die Daten mit den historischen Ergebnisinformationen erstellen, der zum Trainieren des ML-Modells verwendet wird. Ausführliche Informationen zum Konfigurieren des Dataflows finden Sie unter [Self-Service-Datenaufbereitung in Power BI](service-dataflows-overview.md).

In der aktuellen Version verwendet Power BI zum Trainieren des ML-Modells nur Daten aus einer einzigen Entität. Wenn Ihre historischen Daten sich aus mehreren Entitäten zusammensetzen, müssen Sie die Daten manuell zu einer einzigen Dataflow-Entität verknüpfen. Sie sollten auch berechnete Spalten für Geschäftsmetriken hinzufügen, die starke Prädiktoren für das Ergebnis sein können, das Sie vorherzusagen versuchen.

In AutoML gelten für das Trainieren eines Machine Learning-Modells bestimmte Anforderungen. Diese Anforderungen werden in den folgenden Abschnitten basierend auf den jeweiligen Modelltypen beschrieben.

### <a name="configuring-the-ml-model-inputs"></a>Konfigurieren der Eingaben in das ML-Modell

Um ein AutoML-Modell zu erstellen, klicken Sie in der Spalte **Aktionen** der Dataflow-Entität mit den historischen Daten auf das ML-Symbol und wählen **Machine Learning-Modell hinzufügen** aus.

![Machine Learning-Modell hinzufügen](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Es wird eine vereinfachte Umgebung gestartet, die aus einem Assistenten besteht, der Sie durch die Erstellung des ML-Modells begleitet. Der Assistent umfasst die folgenden einfachen Schritte.

1. Wählen Sie die Entität mit den historischen Ergebnisdaten und das Feld aus, für das Sie eine Vorhersage wünschen.
2. Wählen Sie einen Modelltyp basierend auf dem Typ der gewünschten Vorhersage.
3. Wählen Sie die Eingaben aus, die das Modell als Prognosesignale verwenden soll.
4. Benennen Sie Ihr Modell, und speichern Sie die Konfiguration.

Im Feld mit historischen Ergebnissen wird das Beschriftungsattribut für das Training des ML-Modells bestimmt (siehe folgende Abbildung).

![Historische Ergebnisdaten auswählen](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Wenn Sie das Feld mit historischen Ergebnissen angeben, analysiert AutoML die Beschriftungsdaten, um die Typen von ML-Modellen zu ermitteln, die für diese Daten trainiert werden können. Weiterhin schlägt AutoML den wahrscheinlichsten ML-Modelltyp vor, der trainiert werden kann. 

> [!NOTE]
> Einige Modelltypen werden möglicherweise nicht für die von Ihnen ausgewählten Daten unterstützt.

AutoML analysiert auch alle Felder in der ausgewählten Entität, um die Eingaben vorzuschlagen, die für das Training des ML-Modells verwendet werden können. Dieser Prozess ist approximativ und basiert auf statistischen Analysen, weshalb Sie die verwendeten Eingaben überprüfen müssen. Alle Eingaben, die vom Feld mit historischen Ergebnissen (oder Beschriftungsfeld) abhängig sind, dürfen nicht zum Trainieren des ML-Modells verwendet werden, da sie dessen Leistung beeinträchtigen.

![Eingabefelder anpassen](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

Im letzten Schritt können Sie das Modell benennen und seine Einstellungen speichern.

In dieser Phase werden Sie aufgefordert, den Dataflow zu aktualisieren, wodurch der Trainingsprozess für das ML-Modell gestartet wird.

### <a name="ml-model-training"></a>ML-Modelltraining

Das Training von AutoML-Modellen ist Teil der Aktualisierung des Dataflows. AutoML bereitet zunächst Ihre Daten auf das Training auf.

AutoML unter teilt die von Ihnen bereitgestellten historischen Daten in ein Trainings- und ein Testdataset. Der Testdataset besteht aus zurückgehaltenen Daten, die zum Prüfen der Modellleistung nach dem Training verwendet werden. Diese werden als **Trainings- und Test**entitäten im Dataflow realisiert. AutoML verwendet zur Modellprüfung die Kreuzvalidierung.

Anschließend wird jedes Eingabefeld analysiert und die Anrechnung angewendet, bei der fehlende Werte durch Ersatzwerte ausgetauscht werden. AutoML arbeitet mit verschiedenen Anrechnungsstrategien. Anschließend werden alle erforderlichen Samplings und Normalisierungen auf Ihre Daten angewendet.

AutoML wendet mehrere Transformationen an, wobei jedes ausgewählte Eingabefeld basierend auf seinem Datentyp und seinen statistischen Eigenschaften ausgewählt wird. AutoML verwendet diese Transformationen zum Extrahieren von Features, die zum Trainieren Ihres ML-Modells verwendet werden.

Der Trainingsprozess für AutoML-Modelle besteht aus bis zu 50 Iterationen mit unterschiedlichen Modellierungsalgorithmen und Hyperparametereinstellungen, um das Modell mit der besten Leistung zu finden. Die Leistung der einzelnen Modelle wird mittels Prüfung mit dem zurückgehaltenen Testdataset bewertet. Während dieses Trainingsschritts erstellt AutoML verschiedene Pipelines für Training und Prüfung dieser Iterationen. Der Prozess der Bewertung der Leistung der Modelle kann je nach Größe Ihres Datasets und der verfügbaren dedizierten Kapazitätsressourcen eine Weile dauern, und zwar von einigen Minuten bis zu mehreren Stunden.

In einigen Fällen verwendet das endgültige generierte Modell möglicherweise Ensemble-Lernmethoden, bei denen mehrere Modelle verwendet werden, um eine bessere Vorhersageleistung zu erzielen.

### <a name="automl-model-explainability"></a>Erklärbarkeit des AutoML-Modells

Nachdem dem Trainieren des Modells analysiert AutoML die Beziehung zwischen Eingabefeatures und Modellausgabe. Es bewertet für jedes Eingabefeature Größe und Richtung der Änderung der Modellausgabe für das zurückgehaltene Testdataset. Dies wird als *Featurepriorität* bezeichnet.

![Featurepriorität](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML-Modellbericht

AutoML generiert einen Power BI-Bericht, der die Leistung des Modells während der Prüfung sowie die globale Featurepriorität aufzeigt. Der Bericht fasst die Ergebnisse der Anwendung des ML-Modells auf die zurückgehaltenen Testdaten zusammen und vergleicht die Vorhersagen mit den bekannten Ergebniswerten.

Sie können den Bericht zum Modell überprüfen, um seine Leistung zu verstehen. Sie können auch prüfen, ob die wichtigsten Einflussfaktoren des Modells mit den geschäftlichen Erkenntnissen zu den bekannten Ergebnissen übereinstimmen.

Die Diagramme und Measures, die zum Beschreiben der Modellleistung im Bericht verwendet werden, hängen vom Modelltyp ab. Diese Leistungsdiagramme und -measures werden in den folgenden Abschnitten beschrieben.

Auf weiteren Seiten des Berichts werden ggf. statistische Measures des Modells aus Data Science-Perspektive beschrieben. Der Bericht **Binäre Vorhersage** enthält beispielsweise ein Diagramm der Verstärkung und die Grenzwertoptimierungskurve für das Modell.

Die Berichte enthalten auch die Seite **Trainingsdetails** mit einer Beschreibung, wie das Modell trainiert wurde, und ein Diagramm, das die Modellleistung bei jedem der Iterationsläufe beschreibt.

![Details zum Training](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

In einem weiteren Abschnitt auf dieser Seite wird beschrieben, wie die Anrechnungsmethode zum Auffüllen fehlender Werte für die Eingabefelder verwendet wird, sowie wie jedes Eingabefeld transformiert wurde, um die im Modell verwendeten Features zu extrahieren. Der Abschnitt enthält auch die Parameter, die vom endgültigen Modell verwendet werden.

![Weitere Informationen zum Modell](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Wenn das produzierte Modell Ensemble-Lernmethoden verwendet, enthält die Seite **Trainingsdetails** auch einen Abschnitt, der die Gewichtung jedes Teilmodells im Ensemble sowie dessen Parameter beschreibt.

![Gewichtung im Ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Anwenden des AutoML-Modells

Falls Sie mit der Leistung des erstellten ML-Modells zufrieden sind, können Sie es auf neue oder aktualisierte Daten anwenden, wenn Ihr Dataflow aktualisiert wird. Dies können Sie im Modellbericht tun, indem Sie rechts oben auf die Schaltfläche **Anwenden** klicken.

Um das ML-Modell anzuwenden, müssen Sie den Namen der Entität, auf die es angewendet werden soll, und ein Präfix für die Spalten angeben, die bei der Modellausgabe dieser Entität hinzugefügt werden sollen. Das Standardpräfix für die Spaltennamen ist der Modellname. Die Funktion *Anwenden* kann zusätzliche, für den Modelltyp spezifische Parameter einschließen.

Durch das Anwenden des ML-Modells wird eine neue Dataflow-Entität mit dem Suffix **enriched <model_name>** (<Modellname> erweitert) erstellt. Wenn Sie beispielsweise das Modell _PurchaseIntent_ auf die Entität _OnlineShoppers_ anwenden, wird bei der Ausgabe **OnlineShoppers enriched PurchaseIntent** (durch OnlineShoppers erweitertes PurchaseIntent) erzeugt.

Derzeit kann die Ausgabeentität nicht verwendet werden, um eine Vorschau der ML-Modellergebnisse im Power Query-Editor anzuzeigen. In den Ausgabespalten wird immer NULL als Ergebnis angezeigt. Um die Ergebnisse anzuzeigen, wird beim Anwenden des Modells eine zweite Ausgabeentität mit dem Suffix **enriched <model_name> Preview** (<Modellname> erweitert: Vorschau) erstellt.

Sie müssen den Dataflow aktualisieren, um im Abfrage-Editor eine Vorschau der Ergebnisse anzuzeigen.

![Abfrage-Editor](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Bei Anwenden des Modells hält AutoML Ihre Vorhersagen immer auf dem neuesten Stand, wenn der Dataflow aktualisiert wird.

AutoML enthält auch eine individualisierte Erklärung jeder Zeile, die in der Ausgabeentität bewertet wird.

Um die Erkenntnisse und Vorhersagen aus dem ML-Modell in einem Power BI-Bericht zu verwenden, können Sie sich in Power BI Desktop über den Connector **Dataflows** mit der Ausgabeentität verbinden.

## <a name="binary-prediction-models"></a>Modelle zur binären Vorhersage

Modelle zur binären Vorhersage, auch bekannt als **binäre Klassifizierungsmodelle**, werden verwendet, um ein Dataset in zwei Gruppen aufzuteilen. Sie dienen zum Vorhersagen von Ereignissen mit binärem Ausgang, wie z. B. ob eine Verkaufschance in einen Abschluss konvertiert wird, ob ein Kunde abwandert, ob eine Rechnung pünktlich bezahlt wird, ob eine Transaktion betrügerisch ist usw.

Da das Ergebnis binär ist, erwartet Power BI, dass die Beschriftung eines Modells einer binären Vorhersage boolesch ist, wobei bekannte Ergebnisse mit **wahr** oder **falsch** beschriftet werden. Bei einem Modell zur Konvertierung von Verkaufschancen werden beispielsweise gewonnene Verkaufschancen mit „Wahr“, verlorene mit „Falsch“ und offene Verkaufschancen mit NULL beschriftet.

Die Ausgabe eines Modells zur binären Vorhersage ist eine Wahrscheinlichkeitsbewertung, die die Wahrscheinlichkeit angibt, dass das Ergebnis, das der Beschriftung „Wahr“ entspricht, erzielt wird.

### <a name="training-a-binary-prediction-model"></a>Trainieren eines Modells zur binären Vorhersage

Um ein Modell zur binären Vorhersage zu erstellen, muss die Eingabeentität, die Ihre Trainingsdaten enthält, ein boolesches Feld als Feld mit historischen Ergebnissen aufweisen, um die bisherigen bekannten Ergebnisse zu identifizieren.

Voraussetzungen:

* Ein boolesches Feld muss als Feld mit historischen Ergebnissen verwendet werden.
* Für jede Klasse von Ergebnissen sind mindestens 50 Zeilen mit historischen Daten erforderlich.

Wenn die bisherigen Ergebnisse im Allgemeinen durch Felder eines anderen Datentyps identifiziert werden, können Sie eine berechnete Spalte hinzufügen, um diese mithilfe von Power Query in ein boolesches Format umzuwandeln.

Der Erstellungsprozess des Modells zur binären Vorhersage folgt den gleichen Schritten wie bei anderen AutoML-Modellen, die im Abschnitt **Konfigurieren der Eingaben in das ML-Modell** weiter oben beschrieben sind.

### <a name="binary-prediction-model-report"></a>Bericht zum Modell zur binären Vorhersage

Das Modell zur binären Vorhersage produziert als Ausgabe eine Wahrscheinlichkeit, dass ein Datensatz das Ergebnis erreicht, das durch den booleschen Beschriftungswert als „Wahr“ definiert ist. Der Bericht enthält einen Datenschnitt für den Wahrscheinlichkeitsschwellenwert, der beeinflusst, wie die Werte über und unter dem Wahrscheinlichkeitsschwellenwert interpretiert werden.

Im Bericht wird die Leistung des Modells als *Richtige Positive*, *Falsche Positive*, *Richtige Negative* und *Falsche Negative* beschrieben. „Richtige Positive“ und „Richtige Negative“ sind für die beiden Klassen in den Ergebnisdaten richtig vorhergesagte Ergebnisse. „Falsche Positive“ sind Ergebnisse, die den tatsächlichen booleschen Beschriftungswert „Falsch“ hatten, aber als „Wahr“ vorhergesagt wurden. Umgekehrt sind „Falsche Negative“ Ergebnisse, bei denen der tatsächliche boolesche Beschriftungswert „Wahr“ war, die aber als „Falsch“ vorhergesagt wurden.

Measures, z. B. Genauigkeit und Abruf, beschreiben die Auswirkung des Wahrscheinlichkeitsschwellenwerts auf die vorhergesagten Ergebnisse. Sie können den Datenschnitt für den Wahrscheinlichkeitsschwellenwert verwenden, um einen Schwellenwert auszuwählen, der einen ausgewogenen Kompromiss zwischen Genauigkeit und Abruf erreicht.

![Vorschau der Genauigkeit](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

Die Seite **Accuracy Report** (Genauigkeitsbericht) des Modellberichts enthält das Diagramm für *kumulative Verstärkungen* und die Grenzwertoptimierungskurve für das Modell. Dabei handelt es sich um statistische Measures der Modellleistung. Die Berichte enthalten Beschreibungen der gezeigten Diagramme.

![Bildschirm mit dem Bericht zur Genauigkeit](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Anwenden eines Modells zur binären Vorhersage

Um ein Modell zur binären Vorhersage anwenden zu können, müssen Sie die Entität mit den Daten angeben, auf die Sie die Vorhersagen aus dem ML-Modell anwenden möchten. Weitere Parameter sind das Präfix für den Namen der Ausgabespalte und der Wahrscheinlichkeitsschwellenwert für die Klassifizierung des vorhergesagten Ergebnisses.

![Vorhersageeingaben](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Wenn ein Modell zur binären Vorhersage angewendet wird, fügt es der erweiterten Ausgabeentität drei Ausgabespalten hinzu. Dabei handelt es sich um **PredictionScore** (Vorhersagebewertung), **PredictionOutcome** (Vorhersageergebnis) und **PredictionExplanation** (Vorhersageerklärung). Die Spaltennamen in der Entität haben das bei der Anwendung des Modells angegebene Präfix.

Die Spalte **PredictionOutcome** enthält die vorhergesagte Ergebnisbeschriftung. Datensätze mit Wahrscheinlichkeiten über dem Schwellenwert werden als wahrscheinlich für das Erreichen des Ergebnisses prognostiziert. Datensätze unter dem Schwellenwert werden dagegen als unwahrscheinlich für das Erreichen des Ergebnisses eingestuft.

Die Spalte **PredictionExplanation** enthält eine Erklärung des spezifischen Einflusses, den die Eingabefeatures auf **PredictionScore** hatten. Dies ist eine Sammlung von Gewichtungen der Eingabefeatures für die Vorhersage im JSON-Format.

## <a name="classification-models"></a>Klassifizierungsmodelle

Klassifizierungsmodelle werden verwendet, um ein Dataset in mehrere Gruppen oder Klassen aufzuteilen.  Diese Modelle werden verwendet, um Ereignisse vorherzusagen, die eines von mehreren möglichen Ergebnissen haben können. Dazu gehört beispielsweise, ob ein Kunde wahrscheinlich einen sehr hohen, hohen, mittleren oder niedrigen Ertragswert hat, ob das Ausfallrisiko hoch, mittel, niedrig oder sehr niedrig ist usw.

Die Ausgabe eines Klassifizierungsmodells ist eine Wahrscheinlichkeitsbewertung, die die Wahrscheinlichkeit angibt, dass ein Datensatz die Kriterien einer bestimmten Klasse erfüllt.

### <a name="training-a-classification-model"></a>Trainieren eines Klassifizierungsmodells

Die Eingabeentität mit Ihren Trainingsdaten für ein Klassifizierungsmodell muss als Feld mit dem historischen Ergebnis ein Zeichenfolgen- oder numerisches Feld aufweisen, das die bisherigen bekannten Ergebnisse identifiziert.

Voraussetzungen:

* Für jede Klasse von Ergebnissen sind mindestens 50 Zeilen mit historischen Daten erforderlich.

Der Erstellungsprozess des Klassifizierungsmodells besteht aus den gleichen Schritten wie bei anderen AutoML-Modellen, die im Abschnitt **Konfigurieren der Eingaben in das ML-Modell** weiter oben beschrieben sind.

### <a name="classification-model-report"></a>Bericht zum Klassifizierungsmodell

Der Bericht zum Klassifizierungsmodell wird erstellt, indem das ML-Modell auf die zurückgehaltenen Testdaten angewendet und die vorhergesagte Klasse für einen Datensatz mit der tatsächlich bekannten Klasse verglichen wird.

Der Musterbericht enthält ein Diagramm, das die Aufschlüsselung der richtig und falsch klassifizierten Datensätze für jede bekannte Klasse enthält.

![Modellbericht](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Eine weitere klassenspezifische Recherche ermöglicht eine Analyse, wie die Vorhersagen für eine bekannte Klasse verteilt sind. Dazu gehören auch die anderen Klassen, in denen Datensätze dieser bekannten Klasse wahrscheinlich falsch klassifiziert werden.

![Analysebericht](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

Die Modellerklärung im Bericht enthält auch die wichtigsten Prädiktoren für jede Klasse.

Der Bericht zum Klassifizierungsmodell enthält auch eine Seite mit Trainingsdetails ähnlich den Seiten bei anderen Modelltypen, wie im Abschnitt **AutoML-Modellbericht** weiter oben in diesem Artikel beschrieben.

### <a name="applying-a-classification-model"></a>Anwenden eines Klassifizierungsmodells

Um ein ML-Modell zur Klassifizierung anzuwenden, müssen Sie die Entität mit den Eingangsdaten und das Präfix für den Namen der Ausgabespalte angeben.

Wenn ein Klassifizierungsmodell angewendet wird, fügt es der erweiterten Ausgabeentität drei Ausgabespalten hinzu. Dabei handelt es sich um **PredictionScore** (Vorhersagebewertung), **PredictionClass** (Vorhersageklasse) und **PredictionExplanation** (Vorhersageerklärung). Die Spaltennamen in der Entität haben das bei der Anwendung des Modells angegebene Präfix.

Die Spalte **PredictionClass** enthält die wahrscheinlichste vorhergesagte Klasse für den Datensatz. Die Spalte **PredictionScore** enthält die Liste der Wahrscheinlichkeitsbewertungen für den Datensatz für jede mögliche Klasse.

Die Spalte **PredictionExplanation** enthält eine Erklärung des spezifischen Einflusses, den die Eingabefeatures auf **PredictionScore** hatten. Dies ist eine Sammlung von Gewichtungen der Eingabefeatures für die Vorhersage im JSON-Format.

## <a name="regression-models"></a>Regressionsmodelle

Regressionsmodelle dienen zum Vorhersagen eines Werts, wie z. B. der wahrscheinlich zu erzielende Erlös aus einem Verkaufsabschluss, der Kundenertragswert, der Betrag einer Debitorenrechnung, der wahrscheinlich bezahlt wird, das Datum, an dem eine Rechnung ggf. bezahlt wird usw.

Die Ausgabe eines Regressionsmodells ist der vorhergesagte Wert.

### <a name="training-a-regression-model"></a>Trainieren eines Regressionsmodells

Die Eingabeentität, die Ihre Trainingsdaten für ein Regressionsmodell enthält, muss als Feld mit dem historischen Ergebnis ein numerisches Feld aufweisen, das die bisherigen bekannten Ergebniswerte identifiziert.

Voraussetzungen:

* Für ein Regressionsmodell sind mindestens 100 Zeilen mit historischen Daten erforderlich.

Der Erstellungsprozess des Regressionsmodells befolgt die gleichen Schritten wie bei anderen AutoML-Modellen, die im Abschnitt **Konfigurieren der Eingaben in das ML-Modell** weiter oben beschrieben sind.

### <a name="regression-model-report"></a>Bericht zum Regressionsmodell

Wie bei den anderen AutoML-Modellberichten basiert der Bericht zur Regression auf den Ergebnissen der Anwendung des Modells auf die zurückgehaltenen Testdaten.

Der Modellbericht enthält ein Diagramm, das die vorhergesagten Werte mit dem Istwert vergleicht. In diesem Diagramm gibt die Entfernung von der Diagonalen den Fehler in der Vorhersage an.

Das Restfehlerdiagramm zeigt die Verteilung des Prozentsatzes des durchschnittlichen Fehlers für verschiedene Werte im zurückgehaltenen Testdataset. Die horizontale Achse stellt den Mittelwert des Istwertes für die Gruppe dar, wobei die Größe der Blase die Frequenz oder Anzahl der Werte in diesem Bereich anzeigt. Die vertikale Achse ist der durchschnittliche Restfehler.

![Restfehlerdiagramm](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Der Bericht zum Regressionsmodell enthält auch eine Seite mit Trainingsdetails ähnlich wie in den Berichten zu anderen Modelltypen, wie im Abschnitt **AutoML-Modellbericht** weiter oben in diesem Artikel beschrieben.

### <a name="applying-a-regression-model"></a>Anwenden eines Regressionsmodells

Um ein ML-Modell zur Regression anzuwenden, müssen Sie die Entität mit den Eingabedaten und das Präfix für den Namen der Ausgabespalte angeben.

![Anwenden einer Regression](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Wenn ein Regressionsmodell angewendet wird, fügt es der erweiterten Ausgabeentität zwei Ausgabespalten hinzu. Dabei handelt es sich **PredictionValue** (Vorhersagewert) und **PredictionExplanation** (Vorhersageerklärung). Die Spaltennamen in der Entität haben das bei der Anwendung des Modells angegebene Präfix.

Die Spalte **PredictionValue** enthält den basierend auf den Eingabefeldern vorhergesagten Wert für den Datensatz. Die Spalte **PredictionExplanation** enthält eine Erklärung des spezifischen Einflusses, den die Eingabefelder auf **PredictionValue** hatten. Dies ist eine Sammlung von Gewichtungen der Eingabefeatures im JSON-Format.

## <a name="next-steps"></a>Nächste Schritte

Dieser Artikel enthält eine Übersicht über automatisiertes maschinelles Lernen für Dataflows im Power BI-Dienst. Die folgenden Artikel können ebenfalls hilfreich sein.

* [Tutorial: Erstellen eines Machine Learning-Modells in Power BI (Vorschauversion)](service-tutorial-build-machine-learning-model.md)
* [Tutorial: Verwenden von Cognitive Services in Power BI](service-tutorial-use-cognitive-services.md)
* [Tutorial: Aufrufen eines Machine Learning Studio-Modells in Power BI (Vorschau)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services in Power BI (Vorschau)](service-cognitive-services.md)
* [Azure Machine Learning-Integration in Power BI (Vorschau)](service-machine-learning-integration.md)

Weitere Informationen zu Dataflows finden Sie in den folgenden Artikeln:
* [Erstellen und Verwenden von Dataflows in Power BI](service-dataflows-create-use.md)
* [Using computed entities on Power BI Premium (Verwenden berechneter Entitäten in Power BI Premium)](service-dataflows-computed-entities-premium.md)
* [Using dataflows with on-premises data sources (Verwenden von Datenflüssen mit lokalen Datenquellen)](service-dataflows-on-premises-gateways.md)
* [Developer resources for Power BI dataflows (Entwicklerressourcen für Power BI-Datenflüsse)](service-dataflows-developer-resources.md)
* [Dataflows und Integration in Azure Data Lake (Vorschauversion)](service-dataflows-azure-data-lake-integration.md)


