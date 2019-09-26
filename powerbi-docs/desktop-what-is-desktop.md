---
title: Was ist Power BI Desktop?
description: Hier erfahren Sie, was Power BI Desktop ist und wie Sie mit der Verwendung beginnen.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 575d66ad6bb10a4e7faa90f5f658e86115402400
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71141971"
---
# <a name="what-is-power-bi-desktop"></a>Was ist Power BI Desktop?

**Power BI Desktop** ist eine kostenlose Anwendung, die Sie auf Ihrem lokalen Computer installieren können und die es Ihnen ermöglicht, eine Verbindung mit Ihren Daten herzustellen und diese zu transformieren und zu visualisieren. Mit **Power BI Desktop** können Sie eine Verbindung mit mehreren verschiedenen Datenquellen herstellen und diese in ein Datenmodell kombinieren (dies wird oft als Modellierung bezeichnet). Mit einem solchen Datenmodell können Sie Visuals und Sammlungen mit Visuals erstellen, die Sie als für andere Benutzer in Ihrer Organisation als Berichte freigeben können. Die meisten Benutzer, die an Business Intelligence-Projekten arbeiten, verwenden **Power BI Desktop** zum Erstellen von Berichten und nutzen dann den **Power BI-Dienst**, um ihre Berichte für andere Personen freizugeben.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Im Folgenden finden Sie die häufigsten Verwendungsmöglichkeiten für **Power BI Desktop**:

* Verbinden mit Daten
* Transformieren und Bereinigen von Daten zum Erstellen eines Datenmodells
* Erstellen von Visuals wie Diagrammen oder Graphen, die visuelle Darstellungen der Daten bieten
* Erstellen von Berichten, bei denen es sich um Sammlungen von Visuals handelt, auf einer oder mehreren Berichtsseiten
* Freigeben von Berichten für andere Personen über den **Power BI-Dienst**

Personen, die für solche Aufgaben zuständig sind, werden häufig als *Datenanalysten* (bzw. einfach *Analysten*) oder als Business Intelligence-Experten (oder *Berichtersteller*) bezeichnet. Allerdings arbeiten auch viele Menschen, die sich selbst nicht als Analysten oder Berichtersteller betrachten, mit **Power BI Desktop**, um überzeugende Berichts zu erstellen oder Daten aus verschiedenen Quellen abzurufen und Datenmodelle zu erstellen, die sie für Kollegen und Organisationen freigeben können.

Es gibt drei Ansichten in Power BI Desktop, die entlang der linken Seite des Zeichenbereichs angezeigt werden. Die Ansichten, die in der Reihenfolge der Darstellung beschrieben werden, sind die folgenden:
* **Berichtsansicht**: Hier erstellen Sie Berichte und visuelle Elemente, und hier wenden Sie den größten Teil ihrer Erstellungszeit auf.
* **Datenansicht**: Hier werden die Tabellen, Measures und sonstigen Daten angezeigt, die in dem mit dem Bericht verknüpften Datenmodell verwendet werden, und hier werden die Daten für die optimale Nutzung im Modell des Berichts transformiert.
* **Modellansicht**: In dieser Ansicht können Sie die Beziehungen zwischen den Tabellen in Ihrem Datenmodell anzeigen und verwalten.

Die folgende Abbildung zeigt die drei Ansichten, wie sie links neben der Zeichenfläche angezeigt werden:

![verschiedene Ansichten](media/desktop-what-is-desktop/what-is-desktop-07.png)


Mit **Power BI Desktop** können Sie komplexe visuell aufbereitete Berichte erstellen und dabei Daten aus mehreren Quellen in einem Bericht zusammenstellen, den Sie dann für andere Personen in Ihrer Organisation freigeben. 

## <a name="connect-to-data"></a>Verbinden mit Daten
Der erste Schritt bei der Verwendung von **Power BI Desktop** besteht darin, eine Verbindung mit Daten herzustellen. Es gibt viele verschiedene Datenquelle, mit denen Sie über **Power BI Desktop** eine Verbindung herstellen können. Um eine solche Verbindung mit Daten herzustellen, wählen Sie das Menüband **Start** aus, und klicken Sie auf **Daten abrufen > Mehr**. Die folgende Abbildung zeigt das Fenster **Daten abrufen** mit den vielen Kategorien, mit denen Power BI Desktop eine Verbindung herstellen kann.

![Abrufen von Daten in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

Wenn Sie einen Datentyp auswählen, werden Sie aufgefordert, Informationen einzugeben, wie z.B. URL und Anmeldeinformationen, die erforderlich sind, damit Power BI Desktop in Ihrem Namen eine Verbindung mit der Datenquelle herstellen kann.

![Herstellen einer Verbindung mit einer SQL Server-Datenbank in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

Sobald Sie eine Verbindung mit mindestens einer Datenquelle hergestellt haben, können Sie die Daten so transformieren, dass sie für Sie von Nutzen sind.

## <a name="transform-and-clean-data-create-a-model"></a>Transformieren und Bereinigen von Daten und Erstellen eines Modells

In Power BI Desktop können Sie Daten mit dem integrierten **Abfrage-Editor** bereinigen und transformieren. Mit dem Abfrage-Editor können Sie Änderungen an Ihren Daten vornehmen. Sie können z.B. einen Datentyp ändern, Spalten entfernen oder Daten aus mehreren Quellen kombinieren. Sie können sich den Vorgang in etwa wie das Formen einer Lehmskulptur vorstellen: Sie beginnen mit einem großen Block Lehm (bzw. Daten), nehmen dann an einigen Stellen Material weg und fügen an anderen Stellen welches hinzu, bis die Form bzw. Struktur der Daten Ihren Wünschen entspricht. 

![Abfrage-Editor in Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Jeder Schritt, den Sie zum Transformieren der Daten durchführen (z.B. Umbenennen einer Tabelle, Transformieren eines Datentyps oder Löschen von Spalten), wird vom **Abfrage-Editor** aufgezeichnet. Jedes Mal, wenn diese Abfrage eine Verbindung mit der Datenquelle herstellt, werden diese Schritte ausgeführt, sodass die Daten stets in der gewünschten Art strukturiert sind.

Die folgende Abbildung zeigt den Bereich **Abfrageeinstellungen** für eine Abfrage, die strukturiert und in ein Modell umgewandelt wurde.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Sobald Ihre Daten in der von Ihnen gewünschten Form vorliegen, können Sie Visuals erstellen. 

## <a name="create-visuals"></a>Erstellen von visuellen Elementen 

Sobald Sie über ein Datenmodell verfügen, können Sie *Felder* auf die Berichtscanvas ziehen, um *Visuals* zu erstellen. Ein *Visual* ist eine grafische Darstellung der Daten in Ihrem Modell. Das folgende Visual zeigt ein einfaches Säulendiagramm. 

![Ein Visual in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

In Power BI Desktop stehen viele verschiedene Arten von Visuals zur Auswahl bereit. Um ein Visual zu erstellen oder zu ändern, wählen Sie einfach im Bereich **Visualisierungen** das Symbol des Visuals aus. Wenn Sie auf der Berichtscanvas ein Visual ausgewählt haben, ändert sich dieses in den von Ihnen ausgewählten Typ. Wenn kein Visual ausgewählt ist, wird basierend auf Ihrer Auswahl ein neues Visual erstellt.

![Der Bereich „Visualisierungen“ in Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>Erstellen von Berichten

Vermutlich werden Sie häufig eine Sammlung von Visuals erstellen, die verschiedene Aspekte der Daten zeigen, mit denen Sie Ihr Modell in Power BI Desktop erstellt haben. Eine Sammlung von Visuals in einer einzigen Power BI Desktop-Datei wird als *Bericht* bezeichnet. Ein Bericht kann eine oder mehrere Seiten umfassen, ebenso wie eine Excel-Datei aus einem oder mehreren Arbeitsblättern bestehen kann. In der folgenden Abbildung sehen Sie die erste Seite eines Power BI Desktop-Berichts mit der Bezeichnung „Overview“ (der Name wird auf der Registerkarte im unteren Bereich des Bilds angezeigt). Dieser Bericht umfasst zehn Seiten.

![Power BI Desktop-Bericht mit zehn Seiten](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Freigeben von Berichten

Sobald ein Bericht für andere Personen freigegeben werden kann, **veröffentlichen** Sie den Bericht im **Power BI-Dienst** und stellen ihn so für alle Benutzer in Ihrer Organisation zur Verfügung, die eine Power BI-Lizenz besitzen. Um einen Power BI Desktop-Bericht zu veröffentlichen, klicken Sie auf dem Menüband **Start** in Power BI Desktop auf die Schaltfläche **Veröffentlichen**.

![Veröffentlichen eines Berichts aus Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

Sobald Sie auf**Veröffentlichen** geklickt haben, stellt Power BI Desktop über Ihr Power BI-Konto eine Verbindung mit dem **Power BI-Dienst** her und fordert Sie dann auf, auszuwählen, an welcher Stelle im Power BI-Dienst Sie Ihren Bericht freigeben möchten: in Ihrem Arbeitsbereich, einem Teamarbeitsbereich oder einem anderen Bereich im Power BI-Dienst. Sie müssen über eine Power BI-Lizenz verfügen, um Berichte im Power BI-Dienst freizugeben.


## <a name="next-steps"></a>Nächste Schritte

Um mit **Power BI Desktop** zu beginnen, müssen Sie die Anwendung zuerst herunterladen und installieren. Es gibt zwei Möglichkeiten, **Power BI Desktop** zu erhalten:

* [Herunterladen von Power BI Desktop aus dem Web](desktop-get-the-desktop.md)
* [Abrufen von Power BI Desktop aus dem Windows Store](http://aka.ms/pbidesktopstore)
