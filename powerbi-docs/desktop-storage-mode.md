---
title: Verwenden des Speichermodus in Power BI Desktop
description: Mit dem Speichermodus können Sie steuern, ob Daten für Berichte in Power BI Desktop im In-Memory-Cache zwischengespeichert werden sollen.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: bf69b2e4c25597eba980137e5ef8b2feb2f4d103
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327715"
---
# <a name="storage-mode-in-power-bi-desktop"></a>Speichermodus in Power BI Desktop

In Power BI Desktop können Sie den *Speichermodus* von Tabellen festlegen. Mit dem *Speichermodus* können Sie steuern, ob Power BI Desktop Tabellendaten im Arbeitsspeicher für Berichte zwischenspeichert. 

![Speichermodus in Power BI Desktop](media/desktop-storage-mode/storage-mode-01.png)

Das Festlegen des Speichermodus bietet viele Vorteile. Sie können den Speichermodus für jede Tabelle in Ihrem Modell einzeln festlegen. Durch diese Aktion entsteht ein einzelnes Dataset, das folgende Vorteile bietet:

* **Abfrageleistung**: Bei der Interaktion der Benutzer mit Visuals in Power BI-Berichten werden DAX-Abfragen (Data Analysis Expressions) an das Dataset gesendet. Durch die Zwischenspeicherung von Daten im Speicher (mit ordnungsgemäßer Angabe des Speichermodus) können die Abfrageleistung und die Interaktivität Ihrer Berichte erhöht werden.

* **Große Datasets**: Tabellen, die nicht zwischengespeichert werden, belegen keinen Speicher für die Zwischenspeicherung. Sie können interaktive Analysen für große Datasets aktivieren, bei denen eine vollständige Zwischenspeicherung im Speicher zu umfangreich oder zu kostspielig wäre. Sie können die Tabellen auswählen, bei denen eine Zwischenspeicherung sinnvoll ist, und solche, bei denen dies nicht der Fall ist.

* **Optimierung der Datenaktualisierung**: Tabellen, die nicht zwischengespeichert werden, müssen nicht aktualisiert werden. Sie können die Aktualisierungszeiten verkürzen, indem Sie nur die Zwischenspeicherung der Daten veranlassen, die erforderlich sind, um Ihre Vereinbarungen zum Servicelevel und Ihre geschäftlichen Anforderungen zu erfüllen.

* **Anforderungen hinsichtlich einer Ausführung nahezu in Echtzeit**: Bei Tabellen, die nahezu in Echtzeit ausführbar sein sollen, ist ein Verzicht auf eine Zwischenspeicherung möglicherweise sinnvoll, um Datenlatenzen zu verringern.

* **Rückschreiben**: Durch das Rückschreiben können Geschäftsbenutzer mögliche Szenarios durch die Änderung von Zellenwerten untersuchen. Benutzerdefinierte Anwendungen können Änderungen an der Datenquelle anwenden. Tabellen, die nicht zwischengespeichert, können Änderungen sofort darstellen, wodurch eine sofortige Analyse der Auswirkungen möglich ist.

Die Einstellung „Speichermodus“ in Power BI Desktop ist eines von drei in Beziehung stehenden Features:

* **Zusammengesetzte Modelle**: Hierbei kann ein Bericht mindestens zwei Datenverbindungen beinhalten, einschließlich DirectQuery- oder Importverbindungen in beliebiger Kombination. Weitere Informationen finden Sie unter [Verwenden zusammengesetzter Modelle in Power BI Desktop](desktop-composite-models.md).

* **m:n-Beziehungen**: Mithilfe *zusammengesetzter Modelle* können Sie *m:n-Beziehungen* zwischen Tabellen einrichten. Durch *m:n-Beziehungen* entfallen die Anforderungen für eindeutige Werte in Tabellen. Zudem sind vorherige Problemumgehungen hinfällig, wie z.B. die Einführung neuer Tabellen zum Einrichten von Beziehungen. Weitere Informationen finden Sie unter [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md).

* **Speichermodus**: Sie können nun angeben, welche Visuals eine Abfrage in Back-End-Datenquellen erfordern. Visuals, für die keine Abfrage nötig ist, werden importiert, auch wenn diese auf DirectQuery basieren. Mit diesem Feature kann die Leistung verbessert und die Auslastung des Back-Ends verringert werden. Zuvor initiierten sogar einfache Visuals wie Slicer Abfragen, die an Back-End-Quellen gesendet wurden. Im vorliegenden Artikel wird der Speichermodus ausführlich erläutert.

> [!NOTE]
> Zum Anzeigen des aktuellen Speichermodus wählen Sie die Ansicht **Modell** aus, wählen die gewünschte Tabelle aus und zeigen dann im Abschnitt **Erweitert** des Bereichs **Eigenschaften** den Wert des **Speichermodus** an.

## <a name="use-the-storage-mode-property"></a>Verwenden der Speichermoduseigenschaft

Der Speichermodus ist eine Eigenschaft, die Sie für jede Tabelle in Ihrem Modell festlegen können. Wählen Sie in der Ansicht **Modell** die Tabelle aus, deren Eigenschaften Sie anzeigen oder festlegen möchten, wählen Sie dann den Bereich **Eigenschaften**, und erweitern Sie dann den Abschnitt **Erweitert**. Erweitern Sie anschließend das Dropdownmenü **Speichermodus**, um den Speichermodus festzulegen oder seine aktuelle Einstellung anzuzeigen.

![Die Option „Eigenschaften“ im Kontextmenü](media/desktop-storage-mode/storage-mode-02.png)


Es gibt drei Werte für den Speichermodus:

* **Import**: Wenn der Wert auf **Import** festgelegt ist, werden importierte Tabellen zwischengespeichert. Abfragen, die an das Power BI-Dataset gesendet werden, die Daten aus Import-Tabellen zurückgeben, können nur von zwischengespeicherten Daten ausgeführt werden.

* **DirectQuery**: Bei dieser Einstellung werden keine DirectQuery-Tabellen zwischengespeichert. Abfragen, die Sie an das Power BI-Dataset (z.B. DAX-Abfragen) senden, und die Daten von DirectQuery-Tabellen zurückgeben, können nur durch Ausführung von bedarfsgesteuerten Abfragen an die Datenquelle ausgeführt werden. Abfragen, die Sie an die Datenquelle senden, verwenden die Abfragesprache dieser Datenquelle (z.B. SQL).

* **Dual**: Dual-Tabellen können entweder zwischengespeichert oder nicht zwischengespeichert werden, abhängig vom Kontext der an das Power BI-Dataset gesendeten Abfrage. In einigen Fällen werden Abfragen über zwischengespeicherte Daten ausgeführt. In anderen Fällen werden Abfragen durch das Ausführen einer bedarfsgesteuerten Abfrage an die Datenquelle ausgeführt.

Das Ändern einer Tabelle in **Import** kann *nicht rückgängig gemacht werden*. Diese Eigenschaft kann nicht in „DirectQuery“ oder „Dual“ zurück geändert werden.

> [!NOTE]
> Sie können den Speichermodus *Dual* in Power BI Desktop und im Power BI-Dienst verwenden.


## <a name="constraints-on-directquery-and-dual-tables"></a>Einschränkungen für DirectQuery- und Dual-Tabellen

Für Dual-Tabellen gelten dieselben funktionellen Einschränkungen wie für DirectQuery-Tabellen. Zu diesen Einschränkungen zählen beschränkte M-Transformationen und eingeschränkte DAX-Funktionen in berechneten Spalten. Weitere Informationen finden Sie unter [Auswirkungen der Verwendung von DirectQuery](desktop-directquery-about.md#implications-of-using-directquery).

## <a name="propagation-of-dual"></a>Weitergabe von Dual
Sehen Sie sich das folgende einfache Modell an, bei dem alle Tabellen von einer einzelnen Quelle stammen, die Import und DirectQuery unterstützt.

![Beispielbeziehungsansicht für den Speichermodus](media/desktop-storage-mode/storage-mode-04.png)

Nehmen wir an, dass es sich bei allen Tabellen in diesem Modell um DirectQuery-Tabellen handelt. Wenn der **Speichermodus** der *SurveyResponse*-Tabelle in „Import“ geändert wird, wird folgendes Warnungsfenster angezeigt:

![Warnungsfenster des Speichermodus](media/desktop-storage-mode/storage-mode-05.png)

Die Dimensionstabellen (*Customer*, *Geography* und *Date*) können auf **Dual** festgelegt werden, um die Anzahl schwacher Beziehungen im Dataset zu verringern und die Leistung zu verbessern. Schwache Beziehungen enthalten normalerweise mindestens eine DirectQuery-Tabelle, bei der die Joinlogik nicht per Push an die Quellsysteme übertragen werden kann. Die Tatsache, dass **Dual**-Tabellen entweder als DirectQuery oder Import fungieren können, hilft dies zu vermeiden.

Die Weitergabelogik ist dafür konzipiert, Modelle mit vielen Tabellen zu unterstützen. Angenommen, Sie haben ein Modell mit 50 Tabellen, und nur bestimmte (transaktionale) Faktentabellen müssen zwischengespeichert werden. Die Logik in Power BI Desktop berechnet die minimale Gruppe von Dimensionstabellen, die auf **Dual** festgelegt werden müssen. Diese Aufgabe müssen Sie also nicht selbst erledigen.

Die Weitergabelogik durchläuft nur eine Seite der **1:n**-Beziehungen.

## <a name="storage-mode-usage-example"></a>Beispiel für die Verwendung des Speichermodus
Lassen Sie uns mit dem Beispiel aus dem vorherigen Abschnitt fortfahren, und stellen Sie sich vor, die folgenden Eigenschafteneinstellungen für den Speichermodus würden angewendet werden:

| Tabelle                   | Speichermodus         |
| ----------------------- |----------------------| 
| *Sales*                 | DirectQuery          | 
| *SurveyResponse*        | Importieren               | 
| *Date*                  | Dual                 | 
| *Customer*              | Dual                 | 
| *Geography*             | Dual                 | 


Das Festlegen dieser Eigenschaften für den Speichermodus führt zu folgenden Verhaltensweisen, sofern die Tabelle *Sales* ein erhebliches Datenvolumen aufweist.
* Power BI Desktop speichert Dimensionstabellen (*Date*, *Customer* und *Geography*) zwischen, sodass die anfänglichen Berichte beim Abrufen der anzuzeigenden Slicerwerte schnell geladen werden sollten.
* Wird die Tabelle *Sales* nicht zwischengespeichert, liefert Power BI Desktop folgende Ergebnisse:
    * Die Datenaktualisierungszeiten werden verbessert, und die Speichernutzung wird reduziert.
    * Berichtsabfragen, die auf der Tabelle *Sales* basieren, werden im DirectQuery-Modus ausgeführt. Diese Abfragen dauern länger, werden jedoch nahezu in Echtzeit ausgeführt, da keine Latenz durch das Zwischenspeichern entsteht.

* Berichtsabfragen, die auf der Tabelle *SurveyResponse* basieren, werden vom In-Memory-Cache zurückgegeben und sollten daher relativ schnell ausgeführt werden.

## <a name="queries-that-hit-or-miss-the-cache"></a>Abfragen, die vom Cache ausgeführt oder nicht vom Cache ausgeführt werden

Indem Sie eine Verbindung zwischen dem **SQL Server Profiler** und dem Diagnoseport für Power BI Desktop herstellen, können Sie durch Ausführung einer Ablaufverfolgung anhand der folgenden Ereignisse sehen, welche Abfragen vom In-Memory-Cache ausgeführt werden und welche nicht:

* Queries Events\Query Begin
* Query Processing\Vertipaq SE Query Begin
* Query Processing\DirectQuery Begin

Überprüfen Sie für jedes *Query Begin*-Ereignis die anderen Ereignisse mit der gleichen *ActivityID*. Wenn es beispielsweise kein *DirectQuery Begin*-Ereignis, aber ein *Vertipaq SE Query Begin*-Ereignis gibt, wurde die Abfrage vom Cache beantwortet.

Abfragen, die auf Tabellen im **Dual**-Modus verweisen, geben wenn möglich Daten aus dem Cache zurück. Andernfalls werden sie auf DirectQuery zurückgesetzt.

Im Anschluss an das vorherige Beispiel verweist die folgende Abfrage nur auf eine Spalte aus der Tabelle *Date*, die sich im **Dual**-Modus befindet. Aus diesem Grund sollte die Abfrage vom Cache ausgeführt werden.

![Skript für die Speichermodusdiagnose](media/desktop-storage-mode/storage-mode-06.png)

Die folgende Abfrage verweist nur auf eine Spalte aus der Tabelle *Sales*, die sich im **DirectQuery**-Modus befindet. Aus diesem Grund sollte diese *nicht* vom Cache ausgeführt werden.

![Skript für die Speichermodusdiagnose](media/desktop-storage-mode/storage-mode-07.png)

Die folgende Abfrage ist interessant, da sie beide Spalten kombiniert. Diese Abfrage wird nicht vom Cache ausgeführt. Möglicherweise erwarten Sie zunächst, dass *CalendarYear*-Werte vom Cache und *SalesAmount*-Werte von der Quelle abgerufen die Ergebnisse anschließend kombiniert werden, dies wäre jedoch weniger effizient als den SUM/GROUP BY-Vorgang an das Quellsystem zu übermitteln. Wenn der Vorgang an die Quelle weitergegeben wird, fällt die Anzahl der zurückgegebenen Zeilen wahrscheinlich weitaus geringer aus. 

![Skript für die Speichermodusdiagnose](media/desktop-storage-mode/storage-mode-08.png)

> [!NOTE]
> Dieses Verhalten unterscheidet sich von [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md), wenn zwischengespeicherte und nicht zwischengespeicherte Tabellen kombiniert werden.

## <a name="caches-should-be-kept-in-sync"></a>Bedeutung der Synchronisierung von Caches

Die im vorherigen Abschnitt angezeigten Abfragen verdeutlichen, dass **Dual**-Tabellen manchmal vom Cache ausgeführt werden und manchmal nicht. Wenn der Cache veraltet ist, können deshalb unterschiedliche Werte zurückgegeben werden. Bei der Abfrageausführung wird nicht versucht, Datenprobleme, zu maskieren, indem z.B. DirectQuery-Ergebnisse entsprechend den zwischengespeicherten Werten gefiltert werden. Sie müssen bestens mit Ihren Datenflüssen vertraut sein und den Entwurf entsprechend darauf ausrichten. Bei Bedarf können Sie auf etablierte Verfahren zum Umgang mit derartigen Fällen an der Quelle zurückgreifen.

Der Speichermodus *Dual* trägt zur Leistungsoptimierung bei. Er sollte nur auf eine Weise verwendet werden, die die Erfüllung geschäftlicher Anforderungen nicht beeinträchtigt. Ziehen Sie bei anderen Verhaltensweisen ggf. die Verwendung der Methoden in Erwägung, die im Artikel [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md) beschrieben werden.

## <a name="data-view"></a>Datenansicht
Ist für mindestens eine Tabelle im Dataset der Speichermodus auf **Import** oder **Dual** festgelegt, wird die Registerkarte **Datenansicht** angezeigt.

![Datensicht in Power BI Desktop](media/desktop-storage-mode/storage-mode-03.png)

Wenn **Dual-** und **Import-Tabellen** in der **Datenansicht** ausgewählt sind, zeigen diese zwischengespeicherte Daten an. DirectQuery-Tabellen zeigen keine Daten an, und es wird eine Meldung angezeigt, die besagt, dass DirectQuery-Tabellen nicht angezeigt werden können.


## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Es gibt einige Einschränkungen für dieses Release des Speichermodus und dessen Korrelation mit zusammengesetzten Modellen.

Die folgenden (mehrdimensionalen) Live Connect-Quellen können nicht mit zusammengesetzten Modellen verwendet werden:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-Datasets
* Azure Analysis Services

Wenn Sie mithilfe von DirectQuery eine Verbindung mit diesen mehrdimensionalen Quellen herstellen, können Sie keine Verbindung mit einer anderen DirectQuery-Quelle herstellen oder diese mit importierten Daten kombinieren.

Die bestehenden Einschränkungen für die Verwendung von DirectQuery gelten nach wie vor, wenn Sie zusammengesetzte Modelle verwenden. Viele dieser Einschränkungen gelten jetzt abhängig vom Speichermodus der Tabelle für eine einzelne Tabelle. Beispielsweise kann eine berechnete Spalte in einer importierten Tabelle auf andere Tabellen verweisen, wohingegen eine berechnete Spalte in einer DirectQuery-Tabelle nach wie vor nur auf Spalten in derselben Tabelle verweisen kann. Es gelten weitere Einschränkungen für das Modell als Ganzes, wenn eine der Tabellen im Modell DirectQuery enthält. Die Features „QuickInsights“ und „Q&A“ sind nicht für Modelle verfügbar, wenn eine der Tabellen den Speichermodus „DirectQuery“ aufweist. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu zusammengesetzten Modellen und DirectQuery finden Sie in den folgenden Artikeln:
* [Verwenden zusammengesetzter Modelle in Power BI Desktop](desktop-composite-models.md)
* [Beziehungen mit einer m:n-Kardinalität in Power BI Desktop](desktop-many-to-many-relationships.md)
* [Verwenden von DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery in Power BI unterstützte Datenquellen](desktop-directquery-data-sources.md)
