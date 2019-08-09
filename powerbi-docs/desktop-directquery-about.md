---
title: Verwenden von DirectQuery mit Power BI
description: Verstehen der Verwendung von DirectQuery mit Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/22/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 591a837bb085ba901316e672112b568923995718
ms.sourcegitcommit: 0332efe8f83cb55a9b8ea011db7c99e9b4568118
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2019
ms.locfileid: "68590556"
---
# <a name="using-directquery-in-power-bi"></a>Verwenden von DirectQuery mit Power BI
Sie können eine Verbindung mit allen möglichen verschiedenen Datenquellen herstellen, wenn Sie  **Power BI Desktop** oder den **Power BI-Dienst** verwenden, und es gibt unterschiedliche Möglichkeiten, diese Datenverbindungen herzustellen. Sie können Daten in Power BI *importieren*, was die gängigste Methode ist, um Daten abzurufen. Alternativ können Sie eine Direktverbindung zu Daten im ursprünglichen Quellrepository herstellen, was als **DirectQuery** bekannt ist. Dieser Artikel beschreibt **DirectQuery** und die zugehörigen Funktionen:

* Verschiedene Konnektivitätsoptionen für DirectQuery
* Leitfaden für die Situation, in der Sie DirectQuery dem Import vorziehen sollten
* Nachteile der Verwendung von DirectQuery
* Bewährte Methode für die Verwendung von DirectQuery

Kurz gesagt besteht die bewährte Methode für die Verwendung von Import im Vergleich zu DirectQuery aus Folgendem:

* **Importieren** Sie Dateien in Power BI, wann immer dies möglich ist. Beim Importieren wird die leistungsstarke Abfrage-Engine von Power BI genutzt, und Sie erhalten eine hochgradig interaktive und voll umfassende Einsicht über Ihre Daten.
* Wenn Ihre Ziele nicht durch den Import von Daten erreicht werden können, erwägen Sie, **DirectQuery** zu verwenden. DirectQuery ist womöglich die beste Wahl, wenn sich die Daten z.B. oft ändern und Berichte die neuesten Daten wiedergeben müssen. Die Verwendung von DirectQuery ist jedoch nur möglich, wenn die zugrunde liegende Datenquelle interaktive Abfragen (weniger als 5 Sekunden) für die typische Aggregatabfrage bereitstellen und die generierte Abfragelast verarbeiten kann. Darüber hinaus muss die Liste der Einschränkungen, die die Verwendung von DirectQuery begleitet, sorgfältig geprüft werden.

Die Reihe der Funktionen, die von Power BI für beide Konnektivitätsmodi – Import und DirectQuery – angeboten wird, wird mit der Zeit weiterentwickelt. Dadurch wird mehr Flexibilität beim Verwenden importierter Daten bereitgestellt, damit der Import in mehr Fällen genutzt werden kann. Es werden zudem einige Nachteile der Verwendung von DirectQuery entfernt. Unabhängig von den Verbesserungen wird die Leistung der zugrunde liegenden Datenquelle bei Verwendung von DirectQuery immer ein wichtiger Gesichtspunkt bleiben. Wenn die zugrunde liegende Datenquelle langsam ist, kann DirectQuery für diese Quelle nicht verwendet werden.

Dieser Artikel behandelt DirectQuery mit Power BI und nicht SQL Server Analysis Services. DirectQuery ist auch ein Feature von **SQL Server Analysis Services**, und viele der unten beschriebenen Details gelten auch dafür. Es gibt aber auch wichtige Unterschiede. Informationen zur Verwendung von DirectQuery mit SQL Server Analysis Services finden Sie [im Whitepaper, das DirectQuery in SQL Server Analysis Services 2016 erklärt](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

Dieser Artikel konzentriert sich auf den empfohlenen Workflow für DirectQuery, wo der Bericht in **Power BI Desktop** erstellt wird, es wird aber auch die direkte Verbindung im **Power BI-Dienst** behandelt.

## <a name="power-bi-connectivity-modes"></a>Power BI-Konnektivitätsmodi
Power BI stellt eine Verbindung mit einer Vielzahl unterschiedlicher Datenquellen her, was Folgendes umfasst:

* Online-Dienste (Salesforce, Dynamics 365 und andere)
* Datenbanken (SQL Server, Access, Amazon Redshift, andere)
* Einfache Dateien (Excel, JSON, andere)
* Andere Datenquellen (Spark, Websites, Microsoft Exchange, andere)

Für diese Datenquellen können die Daten in Power BI importiert werden. Es ist auch möglich, eine Verbindung mithilfe von DirectQuery herzustellen. Der exakte Satz der Quellen, der DirectQuery unterstützt, ist im Artikel [Data Sources supported by DirectQuery (Von DirectQuery unterstützte Datenquellen)](desktop-directquery-data-sources.md) aufgeführt. Viele Quellen werden in Zukunft für DirectQuery aktiviert, wobei man sich hauptsächlich auf Quellen konzentriert, von denen man erwarten kann, dass sie eine gute interaktive Abfrageleistung abliefern.

**SQL Server Analysis Services** ist ein Sonderfall. Beim Herstellen einer Verbindung mit SQL Server Analysis Services können Sie auswählen, die Daten zu importieren oder eine *Liveverbindung* zu nutzen.  Die Verwendung einer Liveverbindung ähnelt DirectQuery in dem Punkt, dass keine Daten importiert werden und die zugrunde liegende Datenquelle immer abgefragt wird, um ein visuelles Element zu aktualisieren. Die *Liveverbindung* unterscheidet sich aber in vielen anderen Punkten, deshalb wird eine andere Benennung (*Live* versus *DirectQuery*) verwendet.

Die drei Optionen zum Herstellen einer Verbindung zu Daten – **Importieren**, **DirectQuery** und **Liveverbindung** – werden in den folgenden Abschnitten genauer erklärt.

### <a name="import-connections"></a>Importieren von Verbindungen
Wenn Sie **Abrufen von Daten** in **Power BI Desktop** verwenden, um eine Verbindung zu einer Datenquelle wie SQL Server herzustellen, und Sie **Importieren** auswählen, ist das Verhalten dieser Verbindung wie folgt:

* Während der anfänglichen **Abrufen von Daten**-Erfahrung definiert jeder ausgewählte Satz von Tabellen eine Abfrage, die einen Satz von Daten zurückgibt (diese Abfragen können vor dem Laden der Daten bearbeitet werden, um z.B. Filter hinzuzufügen, die Daten zu aggregieren oder unterschiedliche Tabellen zu verknüpfen).
* Nach dem Laden werden alle durch diese Abfragen definierten Daten in den Power BI-Cache importiert.
* Beim Erstellen eines visuellen Elements in **Power BI Desktop** werden die importierten Daten abgefragt. Der Power BI-Speicher stellt sicher, dass die Abfrage schnell ist, da alle Änderungen am Visual sofort wiedergegeben werden.
* Änderungen an den zugrunde liegenden Daten werden in keinem visuellen Element wiedergegeben. Es ist notwendig, zu *aktualisieren*, wonach die Daten wieder importiert werden.
* Beim Veröffentlichen des Berichts (die PBIX-Datei) im **Power BI-Dienst** wird ein Dataset erstellt und in den Power BI-Dienst hochgeladen.  Die importierten Daten ist in diesem Dataset enthalten. Es ist möglich, eine planmäßige Aktualisierung der Daten einzurichten, z.B. um die Daten jeden Tag neu zu importieren. Abhängig vom Speicherort der ursprünglichen Datenquelle ist es möglicherweise erforderlich, ein lokales Datengateway zu konfigurieren.
* Beim Öffnen eines vorhandenen Berichts im **Power BI-Dienst** oder beim Erstellen eines neuen Berichts werden die importierten Daten erneut abgefragt, wodurch die Interaktivität sichergestellt wird.
* Visuelle Elemente oder die gesamten Berichtsseiten können als Dashboardkacheln angeheftet werden. Die Kacheln werden automatisch aktualisiert, sobald das zugrunde liegende Dataset aktualisiert wird.  

### <a name="directquery-connections"></a>DirectQuery-Verbindungen
Wenn Sie **Daten abrufen** in **Power BI Desktop** verwenden, um eine Verbindung zu einer Datenquelle herzustellen, und **DirectQuery** wählen, so ist das Verhalten dieser Verbindung wie folgt:

* Während der anfänglichen Erfahrung von **Daten abrufen** wird die Quelle ausgewählt. Für relationale Datenquellen bedeutet dies, dass ein Satz von Tabellen ausgewählt wird, und jede Tabelle definiert weiterhin eine Abfrage, die logisch einen Satz von Daten zurückgibt. Für mehrdimensionale Datenquellen wie SAP BW wird nur die Quelle ausgewählt.
* Allerdings werden nach dem Laden tatsächlich keine Daten in den Power BI-Speicher importiert. Stattdessen werden nach der Erstellung eines visuellen Elements in **Power BI Desktop** Abfragen an die zugrunde liegende Datenquelle gesendet, um die erforderlichen Daten abzurufen. Die Zeit, die dann für die Aktualisierung des visuellen Elements benötigt wird, hängt von der Leistung der zugrunde liegenden Datenquelle ab.
* Alle Änderungen an den zugrunde liegenden Daten werden nicht sofort in jedem vorhandenen visuellen Element wiedergegeben werden. Es ist weiterhin erforderlich, eine Aktualisierung durchzuführen, wonach die benötigten Abfragen für jedes visuelle Element erneut gesendet werden, und das visuelle Element dann wie nötig aktualisiert wird.
* Nach dem Veröffentlichen des Berichts im **Power BI-Dienst** ergibt sich erneut ein Dataset im Power BI-Dienst, genau wie beim Import. Allerdings sind in diesem Dataset *keine Daten* enthalten.
* Beim Öffnen eines vorhandenen Bericht oder beim Erstellen eines neuen im **Power BI-Dienst** wird die zugrunde liegende Datenquelle erneut abgefragt, um die benötigten Daten abzurufen. Abhängig vom Speicherort der ursprünglichen Datenquelle ist es möglicherweise erforderlich, ein lokales Datengateway zu konfigurieren. Dieses wird ebenso für den Importmodus benötigt, wenn die Daten aktualisiert werden.
* Visuelle Elemente oder die gesamten Berichtsseiten können als Dashboardkacheln angeheftet werden. Um sicherzustellen, dass das Öffnen eines Dashboards schnell ausgeführt wird, werden die Kacheln nach einem Zeitplan (z.B. einmal pro Stunde) automatisch aktualisiert. Die Häufigkeit dieser Aktualisierung kann gesteuert werden, um widerzuspiegeln, wie oft sich die Daten ändern und wie wichtig es ist, die neuesten Daten zu sehen. Daher geben die Kacheln beim Öffnen eines Dashboards die Daten vom Zeitpunkt der letzten Aktualisierung wider und nicht unbedingt die neuesten Änderungen, die an der zugrunde liegenden Quelle vorgenommen wurden. Ein neues Dashboard kann immer aktualisiert werden, um sicherzustellen, dass es auf dem neuesten Stand ist.    

### <a name="live-connections"></a>Liveverbindungen
Beim Herstellen einer Verbindung mit **SQL Server Analysis Services** (SSAS) besteht die Option zum Importieren von Daten aus oder zum Herstellen einer Liveverbindung zum ausgewählten Datenmodell. Wenn Sie **Importieren** auswählen, definieren Sie eine Abfrage für die externe SSAS-Quelle, und die Daten werden als „normal“ importiert. Wenn Sie **Live verbinden** auswählen, gibt es keine definierte Abfrage, und das gesamte externe Modell wird in der Feldliste angezeigt.

Die im vorherigen Absatz beschriebene Situation gilt auch für das Herstellen einer Verbindung mit den folgenden Quellen, mit dem Unterschied, dass es keine Option zum Importieren der Daten gibt:

* Power BI-Datasets (z.B. beim Herstellen einer Verbindung zu einem Power BI-Dataset, das zuvor erstellt und im Dienst veröffentlicht wurde, und um einen neuen Bericht darüber zu erstellen)
* Common Data Service

Das Verhalten von Berichten via SSAS nach der Veröffentlichung im **Power BI-Dienst** ist den DirectQuery-Berichten in folgenden Punkten ähnlich:

* Beim Öffnen eines vorhandenen Berichts im **Power BI-Dienst** oder beim Schreiben eines neuen Berichts wird die zugrunde liegende SSAS-Quelle abgefragt (wobei womöglich ein lokales Datengateway erforderlich ist).
* Dashboardkacheln werden automatisch nach einem Zeitplan aktualisiert (z.B. einmal pro Stunde oder wie auch immer die Häufigkeit definiert ist)

Es gibt jedoch auch wichtige Unterschiede, z.B. wird für die Liveverbindung die Identität des Benutzers, der den Bericht öffnet, immer an die zugrunde liegende SSAS-Quelle übergeben.

Schieben wir nun diese Vergleiche beiseite und konzentrieren uns im restlichen Artikel nur auf **DirectQuery**.

## <a name="when-is-directquery-useful"></a>Wann ist DirectQuery sinnvoll?
Die folgende Tabelle beschreibt Szenarios, in denen die Verbindung mit DirectQuery besonders nützlich sein kann. Es werden zudem Fälle behandelt, in denen es als vorteilhaft angesehen wird, wenn die Daten in der ursprünglichen Quelle gelassen werden würden. Die Beschreibung umfasst eine Diskussion darüber, ob das angegebene Szenario in Power BI verfügbar ist.

| Einschränkung | Beschreibung |
| --- | --- |
| Daten werden häufig geändert, und es ist eine Berichterstellung erforderlich, die näher an der „Echtzeit“ ist. |Modelle mit importierten Daten können höchstens einmal pro Stunde aktualisiert werden. Wenn sich daher Daten kontinuierlich ändern, und Berichte die neuesten Daten zeigen müssen, dann ist die Verwendung des Imports mit geplanter Aktualisierung womöglich nicht für Bedürfnisse dieser Art geeignet. Beachten Sie außerdem, dass es auch möglich ist, Daten direkt in Power BI zu streamen. Es gibt jedoch Grenzwerte für die unterstützten Datenvolumes. <br/> <br/> Wenn Sie im Gegensatz dazu DirectQuery verwenden, bedeutet dies, dass beim Öffnen oder Aktualisieren eines Berichts oder Dashboards immer die neuesten Daten in der Datenquelle angezeigt werden. Darüber hinaus können die Dashboardkacheln häufiger (alle 15 Minuten) aktualisiert werden. |
| Die Datenmenge ist sehr groß |Wenn die Daten sehr groß sind, dann ist es sicherlich nicht praktikabel, alle zu importieren. DirectQuery erfordert im Gegensatz dazu keinen großen Datentransfer, da die Abfrage direkt durchgeführt wird. <br/> <br/> Jedoch implizieren große Daten auch, dass die Leistung der Abfragen für die zugrunde liegende Quelle zu langsam ist (dies wird später in diesem Artikel unter *Auswirkungen der Verwendung von DirectQuery* behandelt). Es ist nicht immer notwendig, die vollständig detaillierten Daten zu importieren. Stattdessen können die Daten während des Imports vorher aggregiert werden (und der **Abfrage-Editor** vereinfacht dies). Im Extremfall wäre es möglich, genau die aggregierten Daten zu importieren, die für jedes Visual benötigt werden. Obwohl DirectQuery die einfachste Möglichkeit für große Daten ist, sollten Sie immer bedenken, dass das Importieren von Aggregatdaten möglicherweise eine Lösung bieten kann, wenn die zugrunde liegende Quelle zu langsam ist. |
| Sicherheitsregeln werden in der zugrunde liegenden Datenquelle definiert |Wenn die Daten importiert werden, verbindet sich Power BI entweder über die aktuellen Anmeldeinformationen des Benutzers (über Power BI Desktop) oder mit den Anmeldeinformationen, die Teil der Konfigurierung der geplanten Aktualisierung sind (über Power BI), mit der Datenquelle. Wenn solch ein Bericht veröffentlicht und freigegeben wird, müssen Sie deshalb Sorgfalt walten lassen, damit dieser nur mit Benutzern geteilt wird, die dieselben Daten sehen dürfen oder dass Sicherheit auf Zeilenebene als Teil des Dataset definiert ist. <br/> <br/> Da DirectQuery immer die zugrunde liegende Datenquelle abfragt, würde im Idealfall jede Sicherheitsmaßnahme in dieser zugrunde liegenden Quelle zugelassen werden, die angewendet werden soll. Allerdings wird Power BI derzeit immer eine Verbindung mit der zugrunde liegenden Quelle mithilfe der gleichen Anmeldeinformationen herstellen, die auch für den Import verwendet werden würden. <br/> <br/> Bis zu dem Zeitpunkt, da Power BI zulässt, dass die Identität des Berichtsconsumers an die zugrunde liegende Quelle übermittelt wird, bietet DirectQuery also keine Vorteile im Hinblick auf die Datenquellensicherheit. |
| Einschränkungen der Datensouveränität gelten |Einige Organisationen verfügen über Richtlinien zur Datensouveränität, d.h., dass Daten die Organisation nicht verlassen können. Eine Lösung, die auf Import basiert, würde ganz klar Probleme darstellen. Im Gegensatz dazu verbleiben Daten mit DirectQuery in der zugrunde liegenden Quelle. <br/> <br/> Allerdings sollte darauf hingewiesen werden, dass sogar mit DirectQuery einige Caches von Daten auf der visuellen Ebene im Power BI-Dienst (aufgrund einer geplanten Aktualisierung von Kacheln) beibehalten werden. |
| Die zugrunde liegende Datenquelle ist eine OLAP-Quelle und enthält Measures |Wenn die zugrunde liegende Datenquelle *Measures* enthält (z.B. SAP HANA oder SAP Business Warehouse), dann führt das Importieren der Daten zu anderen Problemen. Dies bedeutet, dass sich die importierten Daten auf einer bestimmten Aggregationsebene befinden, so wie von der Abfrage definiert. Ein Beispiel sind die Measures „TotalSales by Class“, „TotalSales by Year“ und „TotalSales by City“. Wenn ein Visual erstellt und nach höher aggregierten Daten gefragt wird (z.B. TotalSales by Year), wird der Aggregatwert weiter aggregiert. Für additive Measures (wie Sum, Min) ist dies kein Problem. Für nicht additive Measures (z.B. Average, DistinctCount) kann dies ein Problem darstellen. <br/> <br/> Um das Abrufen der korrekten Aggregatdaten (die für ein bestimmtes visuelles Element benötigt werden) direkt aus der Quelle zu vereinfachen, wäre es notwendig, Abfrage per visuellem Element zu senden, so wie in DirectQuery. <br/> <br/> Beim Verbindungsaufbau zu SAP Business Warehouse (BW) ermöglicht die Auswahl von DirectQuery diese Behandlung von Measures. Unterstützung für SAP BW wird unter [DirectQuery und SAP BW](desktop-directquery-sap-bw.md) weiter behandelt. <br/> <br/> Allerdings wird die Datenquelle derzeit von DirectQuery via SAP HANA genauso wie eine relationale Quelle behandelt, was sich auch beim Verhalten für den Import widerspiegelt. Dieser Vorgang wird unter [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md) weiter beschrieben. |

Wenn man zusammengefasst die aktuellen Funktionen von DirectQuery in Power BI mit einbezieht, sind die vorteilhaften Szenarios die folgenden:

* Daten werden häufig geändert, und es ist eine Berichterstellung erforderlich, die näher an der „Echtzeit“ ist
* Behandlung von sehr großen Datenmengen, ohne die Notwendigkeit, vorab zu aggregieren
* Einschränkungen der Datensouveränität gelten
* Die Quelle ist eine multidimensionale Quelle mit Measures (z.B. SAP BW).

Die Details in der vorherigen Liste beziehen sich auf die Verwendung von Power BI allein. Es gibt immer die Möglichkeit, stattdessen ein externes Modell von SQL Server Analysis Services (oder Azure Analysis Services) zu verwenden, um Daten zu importieren, und dann Power BI zu verwenden, um eine Verbindung mit diesem Modell herzustellen. Während dieser Ansatz zusätzliche Fähigkeiten erfordern würde, bietet er jedoch größere Flexibilität. Größere Datenvolumen können z.B. importiert werden, und es gibt keine Einschränkung dafür, wie regelmäßig die Daten aktualisiert werden können.

## <a name="implications-of-using-directquery"></a>Auswirkungen der Verwendung von DirectQuery
Die Verwendung von **DirectQuery** hat negative Auswirkungen, die in diesem Abschnitt aufgeführt sind. Einige dieser Einschränkungen unterscheiden sich geringfügig je nach der genauen Quelle, die verwendet wird. Es wird ggf. darauf hingewiesen, und separate Artikel behandeln diese Quellen, die sich wesentlich unterscheiden.  

### <a name="performance-and-load-on-the-underlying-source"></a>Leistung von und Last auf der zugrunde liegenden Quelle
Bei Verwendung von **DirectQuery** hängt die allgemeine Erfahrung sehr von der Leistung der zugrunde liegenden Datenquelle ab. Wenn jedes Visual (z.B. nach Änderung eines Datenschnittwerts) einige Sekunden benötigt (< 5 s), dann wäre dies angemessen, würde aber möglicherweise etwas träge im Vergleich zur sofortigen Antwort wirken, die wir beim Importieren von Daten in Power BI gewohnt sind. Wenn die Langsamkeit der Quelle stattdessen bedeutet, dass einzelne visuelle Elemente mehr Zeit brauchen (etwa zehn Sekunden), wird die Erfahrung extrem unzureichend, sodass auch die Zeitbegrenzung der Abfragen überschritten werden kann.

Zusammen mit der Leistung der zugrunde liegenden Quelle sollte die Last, die darauf platziert wird (die dann oft die Leistung beeinträchtigt) sorgfältig abgewägt werden. Wie weiter unten dargestellt, übermittelt jeder Benutzer, der den freigegebenen Bericht öffnet, und jede Dashboardkachel, die regelmäßig aktualisiert wird, mindestens eine Abfrage pro visuellem Element an die zugrunde liegende Quelle. Dies erfordert, dass die Quelle solch eine Abfragelast verarbeiten kann, während sie gleichzeitig eine akzeptable Leistung beibehält.

### <a name="security-implications-when-combining-data-sources"></a>Auswirkungen auf die Sicherheit, wenn Datenquellen kombiniert werden
In einem DirectQuery-Modell können, so wie beim Importieren von Daten, mehrere Datenquellen verwendet werden, indem mit [zusammengesetzten Modellen](desktop-composite-models.md) gearbeitet wird. Wenn Sie dies tun, müssen Sie verstanden haben, wie Daten zwischen den zugrunde liegenden Datenquellen ausgetauscht werden und welche [Auswirkungen auf die Sicherheit](desktop-composite-models.md#security-implications) daraus resultieren.

### <a name="limited-data-transformations"></a>Begrenzte Datentransformationen
Es bestehen ähnliche Einschränkungen bei Datentransformationen, die innerhalb des **Abfrage-Editors** angewendet werden können. Mit importierten Daten kann eine ausgefeilte Reihe von Transformationen einfach angewendet werden, um die Daten zu bereinigen und neu zu gestalten, bevor diese zum Erstellen von visuellen Elementen verwendet werden (z.B. JSON-Dokumente analysieren oder Daten aus einer Spalte in eine zeilenorientierte Form pivotieren). Diese Transformationen sind in DirectQuery beschränkter. Zunächst können beim Herstellen einer Verbindung zu einer OLAP-Quelle wie SAP Business Warehouse gar keine Transformationen definiert werden, und das gesamte externe „Modell“ wird aus der Quelle übernommen. Für relationale Quellen wie SQL Server ist es noch immer möglich, mehrere Transformationen pro Abfrage zu bestimmen. Diese Transformationen sind jedoch aus Leistungsgründen eingeschränkt. All diese Transformationen müssen auf jede Abfrage für die zugrunde liegende Quelle und nicht nur einmal auf die Datenaktualisierung angewendet werden, damit sie auf die Transformationen beschränkt sind, die halbwegs in eine einzelne native Abfrage übertragen werden können. Wenn Sie eine Transformation verwenden, die zu komplex ist, erhalten Sie einen Fehler, der angibt, dass sie entweder gelöscht oder das Modell in den Importmodus versetzt werden muss.

Zusätzlich wird die Abfrage, die sich aus dem Dialogfeld **Daten abrufen** oder **Abfrage-Editor** ergibt, in einem untergeordneten SELECT-Ausdruck zusammen mit den generierten Abfragen verwendet und versendet, um die erforderlichen Daten für das visuelle Element zu empfangen. Daher muss die im Abfrage-Editor definierte Abfrage in diesem Kontext gültig sein. Das bedeutet insbesondere, dass es weder möglich ist, eine Abfrage mithilfe von allgemeinen Tabellenausdrücken zu verwenden, noch eine Abfrage, die gespeicherte Prozeduren aufruft.

### <a name="modeling-limitations"></a>Modellierungseinschränkungen
Der Begriff *Modellierung* bezeichnet in diesem Kontext den Vorgang zum Verfeinern und Anreichern der Rohdaten im Rahmen der Erstellung von Berichten, in denen sie verwendet werden. Beispiele:

* Definieren von Beziehungen zwischen Tabellen
* Hinzufügen von neuen Berechnungen (berechnete Spalten und Measures)
* Umbenennen und Ausblenden von Spalten und Measures
* Definieren von Hierarchien
* Definieren der Formatierung, Standardzusammenfassung und Sortierreihenfolge für eine Spalte
* Gruppierungs- oder Clusterwerte

Wenn Sie **DirectQuery** verwenden, können viele dieser Modellanreicherungen noch immer vorgenommen werden, und es existiert sicherlich noch immer das Prinzip, dass die Rohdaten angereichert werden, um den späteren Verbrauch zu verbessern. Allerdings sind einige Modellierungsfunktionen bei der Verwendung von DirectQuery überhaupt nicht oder nur eingeschränkt verfügbar. Im Allgemeinen werden Einschränkungen angewendet, um Leistungsprobleme zu vermeiden. Die Einschränkungen, die häufig für DirectQuery-Quellen angewendet werden, sind in der folgenden Liste aufgeführt. Zusätzliche Einschränkungen gelten möglicherweise für einzelne Quellen, so wie am Ende dieses Artikels unter *Datenquellenspezifische Details* beschrieben wird.

* **Keine integrierte Datumshierarchie:** Wenn Sie Daten importieren, erhält standardmäßig auch jede date/datetime-Spalte eine integrierte Datumshierarchie, die standardmäßig verfügbar ist. Wenn Sie z.B. eine Tabelle mit Verkaufsaufträgen importieren, die eine Spalte „OrderDate“ enthält, dann wird es vor der Verwendung von OrderDate in einem visuellen Element möglich sein, die zugehörige Ebene auszuwählen (Jahr, Monat, Tag), die verwendet werden soll. Diese integrierte Datumshierarchie ist nicht verfügbar, wenn Sie den DirectQuery-Modus verwenden. Beachten Sie jedoch, dass die DAX Time Intelligence-Funktionen ganz normal verwendet werden können, wenn eine Datumstabelle in der zugrunde liegenden Quelle verfügbar ist (wie es in vielen Data Warehouses üblich ist).
* **Einschränkungen in berechneten Spalten:** Berechnete Spalten sind darauf beschränkt, dass sie zeilenintern sind. Das bedeutet, dass sie sich nur auf Werte anderer Spalten derselben Tabelle beziehen können, ohne Aggregatfunktionen zu verwenden. Darüber hinaus werden die zugelassenen DAX-Skalarfunktionen (wie etwa LEFT()) auf diejenigen eingeschränkt, die an die darunter liegende Quelle übertragen werden können. Ergebnisse können je nach genauen Funktionen der Quelle variieren. Funktionen, die nicht unterstützt werden, werden nicht in AutoVervollständigen aufgelistet, wenn DAX für eine berechnete Tabelle erstellt wird, und würden bei Benutzung einen Fehler auslösen.
* **Keine Unterstützung für über- und untergeordnete DAX-Funktionen:** Wenn Sie sich im DirectQuery-Modell befinden, ist die Verwendung der DAX PATH()-Funktionsfamilie nicht möglich, die normalerweise die Strukturen der über- und untergeordneten Funktionen behandeln (etwa als Kontenplan oder Mitarbeiterhierarchien).
* **Berechnete Tabellen werden nicht unterstützt:** Die Möglichkeit zum Definieren einer berechneten Tabelle mithilfe eines DAX-Ausdrucks wird im DirectQuery-Modus nicht unterstützt.
* **Das Filtern von Beziehungen ist auf nur eine Richtung beschränkt:** Bei Verwendung von DirectQuery ist es nicht möglich, die Kreuzfilterrichtung in einer Beziehung auf „Beide“ festzulegen. Beispielsweise würde es mit den drei Tabellen nicht möglich sein, ein visuelles Element zu erstellen, das jeden Kunden[Geschlecht] und die Anzahl der Produkte[Kategorie] zeigt, die von jedem Kunden gekauft werden. Die Verwendung des bidirektionalen Filterns ist in [diesem ausführlichen Whitepaper](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) beschrieben (darin sind Beispiele im Kontext von SQL Server Analysis Services dargestellt, jedoch gelten die grundlegenden Punkte auch gleichermaßen für Power BI).
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Erneut wird die Einschränkung aufgrund der Leistungsauswirkungen angewendet. Eine besonders wichtige Anwendung davon ist, wenn die Sicherheit auf Zeilenebene als Teil des Berichts definiert wird. Und es ist ein verbreitetes Muster, eine m:n-Beziehung zwischen den Benutzern und den Entitäten zu besitzen, auf die zugegriffen werden kann. Die Verwendung des bidirektionalen Filterns ist nötig, um dies zu erzwingen. Allerdings sollte bidirektionales Filtern für DirectQuery-Modelle sinnvoll eingesetzt werden, mit sorgfältiger Beachtung jedes schädlichen Einflusses auf die Leistung.  
* **Kein Clustering:** Bei Verwendung von DirectQuery ist es nicht möglich, die Clusteringfunktion zu verwenden, um Gruppen automatisch zu suchen.

### <a name="reporting-limitations"></a>Einschränkungen bei der Berichterstattung
Fast alle Berichtsfunktionen werden für DirectQuery-Modelle unterstützt. Daher ist es möglich, solange die zugrunde liegenden Datenquelle ein geeignetes Maß an Leistung bietet, den gleichen Satz von Visualisierungen zu verwenden. Es gibt jedoch einige wichtigen Einschränkungen in einigen der anderen Funktionen des **Power BI-Diensts**, nachdem ein Bericht veröffentlicht wird, wie in den folgenden Punkten beschrieben:

* **Quick Insights wird nicht unterstützt:** Power BI Quick Insights durchsucht verschiedene Teilmengen des Datasets unter Verwendung eines hoch entwickelten Algorithmus, um möglicherweise interessante Erkenntnisse zu gewinnen. Da sehr leistungsstarke Abfragen vonnöten sind, ist diese Fähigkeit nicht für Datasets mit DirectQuery verfügbar.
* **Q&A wird nicht unterstützt:** Power BI Q&A ermöglicht Ihnen, Ihre Daten mithilfe intuitiver Möglichkeiten der natürlichen Sprache zu untersuchen und die entsprechenden Antworten in Form von Diagrammen und Grafiken zu erhalten. Jedoch wird dies derzeit nicht für Datasets mit DirectQuery unterstützt.
* **Die Verwendung von „In Excel untersuchen“ führt wahrscheinlich zu einer schlechteren Leistung:** Sie können Ihre Daten untersuchen, indem Sie die Funktion „Explore in Excel“ (In Excel untersuchen) verwenden. Dadurch können PivotTables und PivotCharts in Excel erstellt werden. Diese Funktion wird für Datasets mit DirectQuery unterstützt, die Leistung ist aber generell langsamer als beim Erstellen von visuellen Elementen in Power BI. Deshalb ist die Verwendung von Excel für Ihre Szenarios wichtig, darum sollten Sie diesen Punkt bei Ihrer Entscheidung, DirectQuery zu verwenden, bedenken.

### <a name="security"></a>Sicherheit
Wie weiter oben in diesem Artikel erläutert, wird ein Bericht mit **DirectQuery** nach dem Veröffentlichen zum **Power BI-Dienst** immer die gleichen festen Anmeldeinformationen zur Verbindung mit der zugrunde liegenden Datenquelle verwenden. Beachten Sie erneut, dass sich dies speziell auf DirectQuery bezieht und nicht auf Liveverbindungen mit SQL Server Analysis Services, was sich in dieser Hinsicht unterscheidet. Daher ist es sofort nach Veröffentlichung eines DirectQuery-Berichts notwendig, die Anmeldeinformationen des Benutzers zu konfigurieren, die verwendet werden. Bis dies erfolgt ist, würde das Öffnen des Berichts im Power BI-Dienst zu einem Fehler führen.

Sobald die Anmeldeinformationen des Benutzers bereitgestellt werden, werden diese verwendet, *ungeachtet vom Benutzer, der den Bericht öffnet*. In diesem Zusammenhang verhält es sich genauso wie bei importierten Daten: Jeder Benutzer sieht die gleichen Daten, es sei denn, die Sicherheit auf Zeilenebene wurde als Teil des Berichts definiert. Daher muss die gleiche Aufmerksamkeit dem Freigeben des Berichts gelten, falls Sicherheitsregeln in der zugrunde liegenden Quelle definiert sind.

### <a name="behavior-in-the-power-bi-service"></a>Verhalten im Power BI-Dienst
Dieser Abschnitt beschreibt das Verhalten eines **DirectQuery**-Berichts im **Power BI-Dienst** in erster Linie so, dass Sie den Grad an Last verstehen können, der auf der Back-End-Datenquelle platziert wird, die Anzahl der Benutzer, mit denen der Bericht und das Dashboard geteilt werden, die Komplexität des Berichts und ob die Sicherheit auf Zeilenebene im Bericht definiert ist.

#### <a name="reports--opening-interacting-with-editing"></a>Berichte öffnen, mit ihnen interagieren, sie bearbeiten
Wenn ein Bericht geöffnet ist, werden alle visuellen Elemente auf der aktuell sichtbaren Seite aktualisiert. Jedes visuelle Element erfordert in der Regel mindestens eine Abfrage für die zugrunde liegenden Datenquelle. Einige visuelle Elemente benötigen möglicherweise mehrere Abfragen (z.B. wenn darin Aggregatwerte aus zwei unterschiedliche Faktentabellen angezeigt werden oder ein komplexeres Measure oder Gesamtergebnisse eines nicht addititven Measures wie Count Distinct enthalten sind). Wenn Sie auf eine neue Seite wechseln, werden diese visuellen Elemente aktualisiert, was dazu führt, dass in der zugrunde liegenden Quelle eine neue Reihe von Abfragen erstellt wird.

Jedes Eingreifen des Benutzers in den Bericht führt möglicherweise dazu, dass visuelle Elemente aktualisiert werden. Wenn Sie beispielsweise einen anderen Wert auf einem Datenschnitt auswählen, müssen Sie eine neue Reihe von Abfragen senden, um alle betroffenen Visuals zu aktualisieren. Dasselbe gilt für das Klicken auf ein visuelles Element, um andere visuelle Elemente hervorzuheben oder einen Filter zu ändern.  

Ähnlich erfordert auch das Bearbeiten eines neuen Berichts, dass Abfragen für jeden Schritt des Pfads gesendet werden, um das erwünschte Visual zu erstellen.

Einige Ergebnisse werden zwischengespeichert, damit die Aktualisierung eines visuellen Elements unmittelbar erfolgen kann, wenn genau die gleichen Ergebnisse zuvor abgerufen wurden. Solche Caches werden nicht für Benutzer freigegeben, wenn Sicherheit auf Zeilenebene als Teil des Berichts definiert ist.

#### <a name="dashboard-refresh"></a>Dashboardaktualisierung
Einzelne visuelle Elemente oder die gesamte Seiten können als Kacheln an das Dashboard angeheftet werden. Kacheln,die auf **DirectQuery**-Datasets basieren, werden dann automatisch nach einem Zeitplan aktualisiert, was dazu führt, dass Abfragen an die Back-End-Datenquelle gesendet werden. Standardmäßig geschieht dies einmal pro Stunde, kann aber als Teil der Dataset-Einstellungen für den Zeitraum wöchentlich oder alle 15 Minuten konfiguriert werden.

Wenn keine Sicherheit auf Zeilenebene im Modell definiert ist, bedeutet das, dass jede Kachel einmal aktualisiert und die Ergebnisse an alle Benutzer verteilt werden würde. Wenn die Sicherheit auf Zeilenebene definiert ist, tritt möglicherweise ein großer Multiplikatoreffekt in Kraft: Jede Kachel erfordert separate Abfragen pro Benutzer, die an die zugrunde liegende Quelle gesendet werden.  

Daher wäre das Ergebnis für ein Dashboard mit zehn Kacheln, das mit 100 Benutzern geteilt und auf einem Dataset mit **DirectQuery** mit Sicherheit auf Zeilenebene erstellt wird, und so konfiguriert ist, dass es alle 15 Minuten aktualisiert wird, das Senden von mindestens 1.000 Abfragen an die Back-End-Quelle im Zeitraum von 15 Minuten.

Daher muss die Verwendung von Sicherheit auf Zeilenebene und die Konfiguration des Aktualisierungszeitplans sorgfältig überlegt sein.

#### <a name="timeouts"></a>Timeouts
Ein Timeout von vier Minuten wird für einzelne Abfragen für den **Power BI-Dienst** angewendet, und Abfragen, die mehr Zeit benötigen, schlagen fehl. Wie zuvor betont, wird empfohlen, dass DirectQuery für Quellen verwendet wird, die nahezu interaktive Abfrageleistung bieten. Diese Begrenzung soll also vermeiden, dass Probleme bei übermäßig langen Ausführungszeiten auftreten.

### <a name="other-implications"></a>Andere Auswirkungen
Einige allgemeine Auswirkungen der Verwendung von **DirectQuery** sind die folgenden:

* **Wenn sich Daten ändern, ist es notwendig, eine Aktualisierung durchzuführen, damit die neuesten Daten angezeigt werden:** Hinsichtlich der Verwendung von Caches gibt es keine Garantie, dass das Visual immer die neuesten Daten anzeigt. Ein visuelles Element kann möglicherweise die Transaktionen des letzten Tags anzeigen. Da ein Datenschnitt geändert wird, kann ein visuelles Element aktualisiert werden, damit es die Transaktionen der letzten zwei Tage anzeigt, einschließlich einiger der neuesten eingegangenen Transaktionen. Die Umwandlung des Datenschnitts in seinen ursprünglichen Wert würde dazu führen, dass wieder die zuvor abgerufenen zwischengespeicherten Werte angezeigt werden, die die zuvor dargestellten neuesten Transaktionen nicht enthalten würden.
  
  Wenn Sie „Aktualisieren“ auswählen, werden sämtliche Caches geleert, und alle visuellen Elemente auf der Seite werden aktualisiert, damit sie die neuesten Daten anzeigen.
* **Wenn Daten geändert werden, besteht keine Garantie der Konsistenz zwischen Visuals:** Andere Visuals, egal ob auf derselben Seite oder auf verschiedenen Seiten, werden möglicherweise zu unterschiedlichen Zeiten aktualisiert. Wenn also die Daten in der zugrunde liegenden Quelle geändert werden, kann nicht garantiert werden, dass jedes visuelle Elemente die Daten zu exakt demselben Zeitpunkt anzeigt. Wenn tatsächlich davon ausgegangen wird, dass manchmal mehr als eine Abfrage für ein einzelnes visuelles Element benötigt wird (beispielsweise um die Details und Gesamtwerte abzurufen), kann die Konsistenz auch für ein einzelnes visuelles Element nicht garantiert werden. Damit diese gewährleistet werden kann, ist sobald ein visuelles Element aktualisiert wird, der Aktualisierungsaufwand aller visuellen Elemente erforderlich, zusammen mit dem Gebrauch der zahlungspflichtigen Funktionen wie der Momentaufnahme-Isolation in der zugrunde liegenden Quelle.
  
  Dieses Problem kann weitgehend minimiert werden, indem Sie erneut „Aktualisieren“ auswählen, wodurch alle Visuals auf der Seite aktualisiert werden. Beachten Sie auch, dass auch wenn Sie den Importmodus verwenden, ein ähnliches Problem für die Garantie der Konsistenz besteht, wenn Sie Daten aus mehr als einer Tabelle importieren.
* **Die Aktualisierung in Power BI Desktop ist notwendig, um Änderungen bei Metadaten widerzuspiegeln:** Nachdem ein Bericht veröffentlicht wurde, werden die Visuals im Bericht aktualisiert. Wenn das Schema der zugrunde liegenden Datenquelle geändert wurde, werden diese Änderungen nicht automatisch übernommen, um die verfügbaren Felder in der Feldliste zu ändern. Wenn Tabellen oder Spalten also aus der zugrunde liegenden Datenquelle entfernt wurden, kann es dazu kommen, dass die Abfrage bei der Aktualisierung fehlschlägt. Wenn Sie einen Bericht in Power BI Desktop öffnen und „Aktualisieren“ auswählen, werden die Felder im Modell aktualisiert, damit Sie die Änderungen anzeigen.
* **Beschränkung von einer Millionen Zeilen, die auf eine beliebige Abfrage zurückgegeben werden:** Für die Anzahl von Zeilen, die in einer einzelnen Abfrage an die zugrunde liegende Quelle zurückgegeben werden, gibt es eine festgelegte maximale Anzahl von einer Million Zeilen. Dies hat in der Regel keine praktische Auswirkung, und visuelle Elemente werden selbst nicht so viele Punkte anzeigen. Allerdings kann die Begrenzung in Fällen auftreten, in denen Power BI die gesendeten Abfragen nicht vollständig optimiert und Zwischenergebnisse angefragt werden, die diese Begrenzung übersteigen. Sie kann auch während der Erstellung eines visuellen Elements auf dem Pfad zu einem akzeptableren Endzustand auftreten. Beispielsweise würde das Einschließen von „Customer“ und „TotalSalesQuantity“ diese Begrenzung erreichen, falls es mehr als 1 Million Kunden gibt, bis einige Filter angewendet werden.
  
  Der zurückgegebene Fehler wäre „Das Resultset einer Abfrage einer externen Datenquelle hat die maximal zulässige Größe von 1.000.000 Zeilen überschritten“.
* **Ein Wechsel vom Import- in den DirectQuery-Modus ist nicht möglich:**  Auch wenn es möglich ist, ein Modell vom DirectQuery- auf den Importmodus umzustellen, bedeutet dies jedoch, dass dazu alle nötigen Daten importiert werden müssen. Es ist auch nicht möglich, in den anderen Modus zurück zu wechseln (hauptsächlich aufgrund der Funktionen, die nicht im DirectQuery-Modus unterstützt werden). Aufgrund der anderen Verarbeitung externer Measures kann für DirectQuery-Modelle für mehrdimensionale Datenquellen wie SAP BW auch vom DirectQuery- in den Importmodus gewechselt werden.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery im Power BI-Dienst
Alle Quellen werden von **Power BI Desktop** unterstützt. Einige Quellen sind auch direkt im **Power BI-Dienst** verfügbar. Beispielsweise ist es möglich, dass ein Geschäftsbenutzer Power BI zum Herstellen einer Verbindung mit den Daten in Salesforce verwendet und sofort ohne die Verwendung von **Power BI Desktop** ein Dashboard abrufen kann.

Nur zwei der von DirectQuery aktivierten Quellen sind direkt im Dienst verfügbar.

* Spark
* Azure SQL Data Warehouse

Allerdings es wird empfohlen, dass jede Verwendung von **DirectQuery** über diese beiden Quellen innerhalb von **Power BI Desktop** stattfindet. Der Grund ist, dass viele wichtige Einschränkungen gelten, wenn die Verbindung erstmalig im **Power BI-Dienst** erfolgt ist. Das bedeutet, dass obwohl der Startpunkt einfach war (beginnend im Power BI-Dienst), es weiterhin Einschränkungen bei der Verbesserung des daraus folgenden Reports gibt (es ist z.B. nicht möglich, dann Berechnungen durchzuführen, viele analytische Funktionen zu verwenden oder auch nur die Metadaten zu aktualisieren, um Änderungen im zugrunde liegenden Schema anzuzeigen).   

## <a name="guidance-for-using-directquery-successfully"></a>Leitfaden zur erfolgreichen Verwendung von DirectQuery
Wenn Sie **DirectQuery** verwenden möchten, finden Sie in diesem Abschnitt ausführliche Anleitungen, mit deren Hilfe Sie diese Funktion erfolgreich ausführen können. Die Anleitung in diesem Abschnitt wurde auf Basis der Auswirkungen der Verwendung von DirectQuery geschrieben, die in diesem Artikel beschrieben wurden.

### <a name="backend-data-source-performance"></a>Leistung der Back-End-Datenquelle
Stellen Sie sicher, dass einfache Visuals in einer angemessenen Zeit (idealerweise unter 5 Sekunden) aktualisiert werden können, damit die Interaktion so angenehm wie möglich ist. Wenn visuelle Elemente länger als 30 Sekunden brauchen, ist es sehr wahrscheinlich, dass weitere Probleme nach der Veröffentlichung des Berichts auftreten, wodurch die Lösung unausführbar wird.

Wenn Abfragen langsam sind, ist der erste Punkt der Untersuchung die Überprüfung der Abfrage, die an die zugrunde liegende Quelle gesendet wird sowie der Grund, warum die Abfrageleistung überwacht wird. In diesem Artikel wird die breite Palette der bewährten Methoden zur Datenbankoptimierung für die gesamten potenziellen zugrunde liegenden Quellen nicht behandelt, jedoch gilt es für die grundlegenden Datenbankmethoden, die für die meisten Situationen gelten:

* Beziehungen, die auf Integerspalten basieren, werden in der Regel besser ausgeführt, als Joins auf Spalten eines anderen Datentyps.
* Die entsprechenden Indizes sollten erstellt werden, was im Allgemeinen den Gebrauch von Columnstore-Indizes in den Quellen meint, die sie unterstützen (z.B. SQL Server).
* Es sollten alle notwendigen Statistiken in der Quelle aktualisiert werden

### <a name="model-design-guidance"></a>Leitfaden zum Modellentwurf
Wenn Sie das Modell definieren, denken Sie an Folgendes:

* **Vermeiden Sie komplexe Abfragen im Abfrage-Editor.** Die Abfrage, die im Abfrage-Editor definiert ist, wird in eine einzelne SQL-Abfrage übertragen, die dann in jeden untergeordneten SELECT-Ausdruck jeder Abfrage eingeschlossen wird, die an die Tabelle gesendet wird. Wenn diese Abfrage komplex ist, kann es zu Leistungsproblemen bei jeder gesendeten Abfrage kommen. Die aktuelle SQL-Abfrage für eine Reihe von Schritten erhalten Sie, indem Sie den letzten Schritt im Abfrage-Editor und dann *View Native Query* (Native Abfrage anzeigen) aus dem Kontextmenü auswählen.
* **Halten Sie Measures einfach.** Zumindest am Anfang wird empfohlen, Measures auf einfache Aggregate zu beschränken. Wenn die Measures dann zufriedenstellend ausgeführt werden, können komplexere Measures definiert werden. Achten Sie jedoch auf die Leistung jedes Measures.
* **Vermeiden Sie Beziehungen in berechneten Spalten.** Dies ist relevant für die Datenbanken, in denen es erforderlich ist, mehrspaltige Joins auszuführen. Power BI lässt heute nicht zu, dass eine Beziehung auf mehreren Spalten als FS/PS vergeben wird. Die am meisten verwendete Problemumgehung ist, die Spalten mithilfe einer berechneten Spalte zu verknüpfen und dann den Join darauf zu vergeben. Während diese Problemumgehung für importierte Daten logisch ist, führt sie im Fall von **DirectQuery** zu einem Join auf einem Ausdruck, der meist die Verwendung von Indizes verhindert und zu schwacher Leistung führt. Die einzige Problemumgehung ist tatsächlich, die vielen Spalten in eine einzige Spalte in der zugrunde liegenden Datenbank zu materialisieren.
* **Vermeiden Sie Beziehungen zwischen „uniqueidentifier“-Spalten.** Power BI unterstützt nicht nativ einen uniqueidentifier-Datentyp. Somit führt die Definition einer Beziehung zwischen Spalten des Typs uniqueidentifier zu einer Abfrage mit einem Join, der eine Umwandlung zur Folge hat. In diesem Fall führt dies häufig zu schwacher Leistung. Bis dieser Fall speziell optimiert ist, besteht die einzige Umgehung dieses Problems darin, Spalten eines alternativen Typs in der zugrunde liegenden Datenbank zu materialisieren.
* **Blenden Sie die *to*-Spalte für Beziehungen aus.** Die *to*-Spalte für Beziehungen (häufig der Primärschlüssel in der *to*-Tabelle) muss ausgeblendet sein, damit sie nicht in der Feldliste erscheint und so auch nicht in visuellen Elementen verwendet werden kann. Häufig sind die Spalten, auf denen Beziehungen basieren, tatsächlich *Systemspalten* (z.B. Ersatzschlüssel in einem Data Warehouse), und das Ausblenden dieser Spalten ist sowieso eine gute Empfehlung. Wenn die Spalte von Bedeutung ist, führen Sie eine berechnete sichtbare Spalte ein, die über einen einfachen Ausdruck verfügt, wonach sie mit dem Primärschlüssel gleich ist. Beispiel:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  Der Grund hierfür besteht darin, ein Leistungsproblem zu vermeiden, das andernfalls auftreten kann, wenn ein visuelles Element die Primärschlüsselspalte enthält.
* **Überprüfen Sie alle Vorkommen von berechneten Spalten und Änderungen des Datentyps.** Die Verwendung dieser Funktionen ist nicht zwingend schädlich, jedoch führt dies dazu, dass Abfragen an die zugrunde liegende Quelle gesendet werden, die eher Ausdrücke als einfache Verweise auf Spalten enthält, was wiederum auch dazu führen kann, das Indizes nicht verwendet werden.  
* **Vermeiden Sie die Verwendung der bidirektionalen Kreuzfilterung für Beziehungen.** Die Verwendung des bidirektionalen Kreuzfilterns kann zu Abfrageanweisungen führen, die nicht gut funktionieren.
* **Experimentieren Sie mit der Einstellung *Referenzielle Integrität voraussetzen*.** Die Einstellung *Referenzielle Integrität voraussetzen* für Beziehungen lässt zu, dass Abfragen INNER JOIN-Anweisungen und nicht OUTER JOIN-Anweisungen verwenden. Die Abfrageleistung wird somit generell verbessert, obwohl dies nicht von den Eigenheiten der Datenquelle abhängt.
* **Verwenden Sie nicht die relative Datenfilterung im Abfrage-Editor.** Es ist möglich, die relative Datenfilterung im Abfrage-Editor zu definieren. Ein Beispiel dafür ist es, nach Zeilen zu filtern, in denen das Datum im Zeitraum der letzten 14 Tage liegt.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  Dies wird jedoch in einen Filter auf Grundlage des festgelegten Datums übersetzt, an dem die Abfrage geschrieben wurde. Sie können dies in der nativen Abfrage anzeigen.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Das war sicherlich nicht so vorgesehen. Um sicherzustellen, dass der Filter basierend auf dem Datum angewendet wird, an dem der Bericht ausgeführt wird, wenden Sie stattdessen den Filter im Bericht als Berichtsfilter an. Derzeit würde dies funktionieren, indem Sie eine berechnete Tabelle erstellen, die die Anzahl der vergangenen Tage berechnet (mithilfe der DAX DATE()-Funktion), und dann diese berechnete Spalte in einem Filter verwenden.

### <a name="report-design-guidance"></a>Leitfaden zum Berichtsentwurf
Wenn Sie einen Bericht mithilfe einer DirectQuery-Verbindung erstellen, befolgen Sie die folgenden Leitlinien:

* **Überlegungen für das Verwenden von Optionen zur Verringerung von Abfragen:** Power BI stellt Optionen im Bericht bereit, mit denen weniger Abfragen gesendet und bestimmte Interaktionen deaktiviert werden, die bei langer Ausführung der resultierenden Abfragen zu Leistungseinbußen führen würden. Navigieren Sie in **Power BI Desktop** zu **Datei > Optionen und Einstellungen > Optionen**, und klicken Sie auf **Abfrageverringerung**, um auf diese Optionen zuzugreifen. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    Durch die Kontrollkästchen unter **Abfrageverringerung** können Sie die übergreifende Hervorhebung für den gesamten Bericht deaktivieren. Sie können bei Slicer- und Filterauswahlen ebenfalls die Schaltfläche *Übernehmen* anzeigen lassen, durch die Sie viele Slicer und Filter auswählen können, bevor Sie diese anwenden. Dies führt dazu, dass keine Abfragen gesendet werden, bevor Sie auf die Schaltfläche **Anwenden** des Slicers klicken. Ihre Auswahl kann dann zum Filtern der Daten verwendet werden.

    Diese Optionen gelten für Ihren Bericht, während Sie mit **Power BI Desktop** interagieren, und wenn Ihre Benutzer den Bericht im **Power BI-Dienst** verwenden.

* **Wenden Sie zuerst Filter an:** Wenden Sie anwendbare Filter immer zu Beginn der Erstellung eines Visuals an. Wenden Sie z.B. den Filter „Jahr“ zu Beginn an, anstatt sich im TotalSalesAmount und ProductName zu bewegen und dann nach einem bestimmten Jahr zu filtern. Der Grund dafür ist, dass jeder Schritt zur Erstellung eines visuellen Elements eine Abfrage sendet. Obwohl es möglich ist, Änderungen durchzuführen, bevor die erste Abfrage abgeschlossen ist, bleibt jedoch noch viel unnötige Last auf der zugrunde liegenden Quelle liegen. Wenn Filter früh angewendet werden, werden diese zwischenzeitlichen Abfragen generell günstiger. Darüber hinaus kann es dazu führen, dass die Begrenzung von 1 Million Zeilen erreicht wird, wenn die Filter nicht früh angewendet werden.
* **Begrenzen Sie die Anzahl von Visuals auf einer Seite:** Wenn eine Seite geöffnet wird (oder einige Slicer oder Filter auf Seitenebene geändert wurden), werden alle Visuas auf einer Seite aktualisiert. Es gibt auch eine Begrenzung für die Anzahl der Abfragen, die gleichzeitig gesendet werden, denn wenn die Anzahl der visuellen Elemente steigt, werden auch einige visuelle Elemente nacheinander aktualisiert, wodurch viel mehr Zeit für die Aktualisierung der gesamten Seite benötigt wird. Aus diesem Grund wird empfohlen, die Anzahl von visuellen Elementen auf einer Seite zu begrenzen, und stattdessen mehr einfachere Seiten zu haben.
* **Erwägen Sie, die Interaktion zwischen Visuals zu deaktivieren:** Standardmäßig können Visualisierungen auf einer Berichtsseite für die Kreuzfilterung und -hervorhebung der anderen Visualisierungen auf der Seite verwendet werden. Wenn beispielsweise „1999“ auf dem Kreisdiagramm ausgewählt ist, wird das Säulendiagramm übergreifend hervorgehoben, um die Verkäufe nach Kategorie für „1999“ anzuzeigen.                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  Abfragen müssen in DirectQuery wegen des Kreuzfilterns und dem übergreifenden Hervorheben an die zugrunde liegende Quelle übermittelt werden. Die Interaktion sollte daher deaktiviert werden, wenn es ungewöhnlich lange dauert, auf die Auswahl von Benutzern zu reagieren. Diese Interaktion kann entweder für den gesamten Bericht (wie zuvor unter *Optionen zur Verringerung von Abfragen* beschrieben) oder wie [in diesem Artikel](consumer/end-user-interactions.md) beschrieben von Fall zu Fall deaktiviert werden.

Beachten Sie zusätzlich zu der oben aufgeführten Liste mit Vorschlägen, dass jede der nachfolgenden Berichtsfunktionen Leistungsprobleme auslösen kann.

* **Measurefilter:** Visuals, die Measures (oder Aggregate von Spalten) enthalten, können Filter in diesen Measures enthalten. Das visuelle Element unten zeigt z.B. „SalesAmount“ nach Kategorie an, aber nur einschließlich dieser Kategorien mit mehr als 20 Millionen Verkäufen.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Dies führt dazu, dass zwei Abfragen an die zugrunde liegende Datenquelle gesendet werden:
  
  * Die erste Abfrage ruft die Kategorien ab, die die Bedingungen erfüllen (Verkäufe > 20 Mio.).
  * Die zweite Abfrage ruft die notwendigen Daten für das Visual ab, einschließlich der Kategorien, die die Bedingung in der WHERE-Klausel erfüllen.  
  
  Dies funktioniert in der Regel gut, wenn es wie in diesem Beispiel hunderttausende Kategorien gibt. Die Leistung kann beeinträchtigt werden, wenn die Anzahl der Kategorien viel größer ist (tatsächlich schlägt die Abfrage fehl, wenn mehr als eine Million Kategorien die Bedingung erfüllen. Der Grund dafür ist die Begrenzung von einer Million Zeilen, die vorher erwähnt wurde).
* **TopN-Filter:** Erweiterte Filter können so definiert werden, dass sie nur die oberen (oder unteren) n Werte nach einem Measure filtern, um beispielsweise nur die ersten 10 Kategorien im Visual oben einzuschließen. Dies führt erneut zu zwei Abfragen, die an die zugrunde liegende Quelle gesendet werden. Allerdings gibt die erste Abfrage alle Kategorien der zugrunde liegenden Quelle zurück, dann werden die TopN basierend auf den zurückgegebenen Ergebnissen bestimmt. Abhängigkeit von der Kardinalität der beteiligten Spalte kann dies zu Leistungsproblemen führen (oder Abfragefehlern aufgrund des Zeilengrenzwerts von 1 Mio.).
* **Median:** Generell wird jede Aggregation (Sum, Count Distinct usw.) per Push an die zugrunde liegende Quelle übermittelt. Dies gilt allerdings nicht für Median, da dieses Aggregat normalerweise nicht von der zugrunde liegenden Quelle unterstützt wird. In solchen Fällen werden die Detaildaten aus der zugrunde liegenden Quelle abgerufen, und der Median wird aus den zurückgegebenen Ergebnissen berechnet. Dies ist sinnvoll, wenn der Median über eine relativ kleine Anzahl von Ergebnissen berechnet werden soll. Es treten jedoch Leistungsprobleme (oder Abfragefehler aufgrund der Zeilenbegrenzung von 1 Mio.) auf, wenn die Kardinalität groß ist.  Den Median der Bevölkerungszahl eines Landes zu ermitteln, kann sinnvoll sein, nicht jedoch die Ermittlung des Median von Verkaufspreisen
* **Erweiterte Textfilter („enthält“ und ähnlich):** Wenn nach einer Textspalte gefiltert wird, erlaubt das erweiterte Filtern Filter wie „enthält“ und „beginnt mit“ usw. Diese Filter können sicherlich zu Leistungseinbußen bei einigen Datenquellen führen. Insbesondere sollte der Standardfilter „enthält“ nicht verwendet werden, falls nach einer exakten Übereinstimmung gesucht wird („ist“ oder „ist nicht“). Obwohl das Ergebnis möglicherweise identisch ist, kann sich abhängig von den tatsächlichen Daten die Leistung aufgrund der Verwendung von Indizes erheblich unterscheiden.
* **Slicer mit Mehrfachauswahl:** Standardmäßig erlauben Slicer nur eine einzige Auswahl. Das Zulassen einer Mehrfachauswahl in Filtern kann zu Leistungsproblemen führen, da der Benutzer einen Satz von Elementen im Datenschnitt auswählt (z.B. die zehn Produkte, an die der Benutzer interessiert ist) und jede Auswahl dazu führt, dass Abfragen an die Back-End-Quelle gesendet werden. Der Benutzer kann das nächste Element auswählen, bevor die Abfrage abgeschlossen ist, was zu zusätzlicher Last auf der zugrunde liegenden Quelle führen kann.

* **Erwägen Sie, Summen in Visuals zu deaktivieren:** Standardmäßig werden in Tabellen und Matrizen Summen und Teilsummen angezeigt. In vielen Fällen müssen separate Abfragen an die zugrunde liegende Quelle gesendet werden, um die Werte für solche Summen abzurufen. Dies gilt immer, wenn die Aggregation *DistinctCount* verwendet wird oder wenn DirectQuery über SAP BW oder SAP HANA verwendet wird. Solche Summen sollten deaktiviert werden (mithilfe des Bereichs **Format**), wenn sie nicht erforderlich sind. 

### <a name="maximum-number-of-connections-option-for-directquery"></a>Maximale Anzahl von Verbindungsoptionen für DirectQuery

Sie können einstellen, wie viele Verbindungen für jede zugrunde liegende Datenquelle von DirectQuery maximal geöffnet werden können und dabei auch steuern, wie viele Abfragen gleichzeitig an jede Datenquelle gesendet werden. 

Die maximale Anzahl von DirectQuery-Verbindungen, die gleichzeitig geöffnet werden, ist dann eingestellt. Sie können dies für die aktuelle Datei in **Power BI Desktop** ändern, indem Sie zu **Datei > Optionen und Einstellungen** navigieren und anschließend im Abschnitt **Aktuelle Datei** im linken Bereich **DirectQuery** auswählen. 

![Aktivieren der maximalen Anzahl von DirectQuery-Verbindungen](media/desktop-directquery-about/directquery-about_05b.png)

Die Einstellung ist nur aktiviert, wenn mindestens eine DirectQuery-Quelle im aktuellen Bericht vorhanden ist. Der Wert gilt für alle DirectQuery-Quellen sowie für alle neuen DirectQuery-Quellen, die dem gleichen Bericht hinzugefügt werden.

Durch Erhöhen des Werts für die **maximale Anzahl von Verbindungen** wird eine größere Anzahl von Abfragen sichergestellt (entsprechend der angegebenen maximalen Anzahl), die zu der zugrunde liegenden Datenquelle gesendet werden können. Dies ist hilfreich, wenn sich zahlreiche Visuals auf einer einzigen Seite befinden, oder wenn viele Benutzer gleichzeitig auf einen Bericht zugreifen. Sobald die maximale Anzahl von Verbindungen erreicht ist, werden weitere Abfragen in die Warteschlange gestellt, bis eine Verbindung verfügbar wird. Ein Erhöhen dieses Grenzwerts führt zu mehr Last auf der zugrunde liegenden Quelle. Daher ist nicht garantiert, dass durch die Einstellung die Gesamtleistung verbessert wird.

Sobald ein Bericht veröffentlicht ist, hängt die maximale Anzahl von gleichzeitigen Abfragen, die an die zugrunde liegende Datenquelle gesendet werden, auch von festen Grenzwerten ab, die wiederum von der Zielumgebung abhängen, in der der Bericht veröffentlicht wurde. Unterschiedliche Umgebungen (wie Power BI, Power BI Premium oder Power BI-Berichtsserver) können jeweils unterschiedliche Grenzwerte erfordern.

### <a name="diagnosing-performance-issues"></a>Diagnostizieren von Leistungsproblemen
Dieser Abschnitt beschreibt, wie Sie Leistungsprobleme diagnostizieren oder weitere Informationen darüber erhalten können, wie Berichte optimiert werden.

Es wird dringend empfohlen, dass Sie die Diagnose von Leistungsproblemen in **Power BI Desktop** beginnen und nicht im **Power BI-Dienst**. Es ist häufig der Fall, dass Leistungsprobleme einfach auf dem Leistungsgrad der zugrunde liegenden Quelle basieren. Diese können in der isolierteren Umgebung von **Power BI Desktop** einfacher identifiziert und diagnostiziert werden, und bestimmte Komponenten können zunächst entfernt werden (wie das Power BI-Gateway). Nur wenn Leistungsprobleme nicht in Power BI Desktop vorhanden sind, sollte sich die Untersuchung auf die Eigenschaften des Berichts im Power BI-Dienst fokussieren. Die [Leistungsanalyse](desktop-performance-analyzer.md) ist ein nützliches Tool zum Erkennen von Problemen in diesem Prozess.

Es wird auch empfohlen, zu versuchen, zunächst Probleme eines visuellen Elements zu isolieren, anstatt viele visuelle Element auf einer Seite.

Nehmen wir an, dass die Schritte (in den vorherigen Paragrafen dieses Abschnitts) befolgt wurden und wir nun über ein einzelnes visuelles Element auf einer Seite in **Power BI Desktop** verfügen, das noch immer träge ist. Um die Abfragen zu ermitteln, die von Power BI Desktop an die zugrunde liegende Quelle gesendet werden, können Sie die [Leistungsanalyse](desktop-performance-analyzer.md) verwenden. Es ist auch möglich, Ablaufverfolgungen/Diagnoseinformationen anzuzeigen, sofern solche von der zugrunde liegenden Datenquelle ausgegeben wurden. Solche Ablaufverfolgungen können auch nützliche Informationen über die Details über die Ausführung der Abfrage enthalten, und wie diese verbessert werden kann.

Darüber hinaus ist es möglich, die Abfragen, die von Power BI zusammen mit den Ausführungszeiten gesendet wurden, anzuzeigen, auch wenn keine Ablaufverfolgungen vorhanden sind, so wie unten beschrieben.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Bestimmen der Abfragen von Power BI Desktop
Standardmäßig protokolliert **Power BI Desktop** Ereignisse in einer Ablaufverfolgungsdatei mit dem Namen „FlightRecorderCurrent.trc“ während einer gegebenen Sitzung.

Für einige **DirectQuery**-Quellen enthält dieses Protokoll alle Abfragen, die an die zugrunde liegende Datenquelle gesendet wurden (die verbleibenden DirectQuery-Quellen werden bald hinzugefügt). Die Quellen, die Abfragen an das Protokoll senden, lauten wie folgt:

* SQL Server
* Azure SQL-Datenbank
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Sie finden die Ablaufverfolgungsdatei im **AppData**-Ordner für den aktuellen Benutzer:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Hier ist eine einfache Möglichkeit, zu diesem Ordner zu gelangen: Wählen Sie in **Power BI Desktop** die Optionen **Datei > Optionen und Einstellungen > Optionen**, und wählen Sie dann **Diagnose** aus. Das folgende Dialogfeld wird angezeigt:

![](media/desktop-directquery-about/directquery-about_06.png)

Wenn Sie den Link *Ablaufverfolgungsordner öffnen* unter **Diagnoseoptionen** auswählen, wird der folgende Ordner geöffnet:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

Navigieren zum übergeordneten Ordner des Ordners, zeigt den Ordner an, der *AnalysisServicesWorkspaces* enthält, die einen Arbeitsbereich-Unterordner für jede offene Instanz von **Power BI Desktop** enthält. Diese Unterordner werden mit einem Integersuffix bezeichnet, z.B. *AnalysisServicesWorkspace2058279583*.

In diesem Ordner befindet sich ein *\\Data*-Unterordner, der die Ablaufverfolgungsdatei „FlightRecorderCurrent.trc“ für die aktuelle Power BI-Sitzung enthält. Der entsprechende Arbeitsbereichsordner wird gelöscht, wenn die zugehörige Power BI Desktop-Sitzung endet.

Die Ablaufverfolgungsdateien können mithilfe des **SQL Server Profiler**-Tools gelesen werden, das als kostenloser Download im Rahmen des **SQL Server Management Studio** verfügbar ist. Sie erhalten SSMS [hier](https://msdn.microsoft.com/library/mt238290.aspx).

Nachdem Sie **SQL Server Management Studio** heruntergeladen und installiert haben, führen Sie den **SQL Server Profiler** aus.

![](media/desktop-directquery-about/directquery-about_07.png)

Um die Ablaufverfolgungsdatei zu öffnen, gehen Sie folgendermaßen vor:

1. Wählen Sie in **SQL Server Profiler** **Datei > Öffnen > Ablaufverfolgungsdatei** aus.
2. Geben Sie den Pfad zur Ablaufverfolgungsdatei für die aktuell geöffnete Power BI-Sitzung ein, z.B.:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Öffnen von „FlightRecorderCurrent.trc“

Es werden alle Ereignisse aus der aktuellen Sitzung angezeigt. Ein kommentiertes Beispiel ist unten dargestellt, das Gruppen von Ereignissen markiert. Jede Gruppe verfügt über Folgendes:

* Ein Ereignis für den *Abfragebeginn* und das *Ende der Abfrage*, das den Beginn und das Ende einer DAX-Abfrage darstellt, die von der Benutzeroberfläche (z.B. von einem visuellen Element oder durch Auffüllen einer Liste von Werten in der Filterbenutzeroberfläche) generiert wird.
* Ein oder mehrere Paare von Ereignissen für *DirectQuery – Anfang* und *DirectQuery – Ende* stellen eine an die zugrunde liegende Datenquelle gesendete Abfrage als Teil der Auswertung der DAX-Abfrage dar.

Beachten Sie, dass mehrere DAX-Abfragen parallel ausgeführt werden können, damit sich Ereignisse aus verschiedenen Gruppen überlappen können. Der Wert der Aktivitäts-ID kann verwendet werden, um zu bestimmen, welche Ereignisse zur selben Gruppe gehören.

![](media/desktop-directquery-about/directquery-about_08.png)

Andere interessante Spalten sind die folgenden:

* **TextData:** Die Textdetails des Ereignisses. Für „Abfragebeginn/Ende der Abfrage“-Ereignisse ist dies die DAX-Abfrage. Für „DirectQuery – Anfang/Ende“-Ereignisse ist dies die SQL-Abfrage, die an die zugrunde liegende Quelle gesendet wird. Die Daten von TextData werden für das aktuell ausgewählte Ereignis auch im unteren Bereich angezeigt.
* **EndTime:** Der Zeitpunkt, zu dem das Ereignis abgeschlossen wurde.
* **Duration:** Die Dauer in Millisekunden, die zur Ausführung der DAX- oder SQL-Abfrage benötigt wird.
* **Error:** Gibt an, ob ein Fehler aufgetreten ist (in diesem Fall wird das Ergebnis auch rot angezeigt).

In der Abbildung oben wurden einige weniger relevante Spalten verschmälert, damit die relevanten Spalten einfacher gelesen werden können.

Die empfohlene Vorgehensweise zum Aufzeichnen von Ablaufverfolgungsdaten, um ein mögliches Leistungsproblem zu diagnostizieren, lautet wie folgt:

* Öffnen Sie eine einzelne **Power BI Desktop**-Sitzung (zur Vermeidung von Verwechslungen von mehreren Arbeitsbereichsordnern).
* Führen Sie die interessanten Aktionen in **Power BI Desktop** aus. Schließen Sie einige zusätzliche Aktionen mit ein, um sicherzustellen, dass die interessanten Ereignisse in die Ablaufverfolgungsdatei geleert werden.
* Öffnen Sie den **SQL Server Profiler**, und untersuchen Sie die Ablaufverfolgung, so wie vorher beschrieben. Denken Sie daran, dass die Ablaufverfolgungsdatei nach dem Schließen von **Power BI Desktop** gelöscht wird. Darüber hinaus werden zusätzliche Aktionen in Power BI Desktop nicht sofort angezeigt. Die Ablaufverfolgungsdatei muss geschlossen und erneut geöffnet werden, um die neuen Ereignisse anzuzeigen.
* Halten Sie einzelne Sitzungen relativ klein (Aktionen von zehn Sekunden, nicht von hunderten), damit die Ablaufverfolgungsdatei leichter interpretiert werden kann (und weil es eine Einschränkung der Größe der Ablaufverfolgungsdatei gibt und deshalb bei langen Sitzungen die Gefahr besteht, dass frühe Ereignisse gelöscht werden).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Grundlegendes zur Form der Abfrage, die von Power BI Desktop gesendet wird
Die Allgemeine Form von Abfragen, die durch **Power BI Desktop** gesendet werden, verwendet Unterabfragen für alle referenzierten Tabellen, wobei diese Unterabfragen im **Abfrage-Editor** definiert werden. Nehmen wir z.B. an, dass die folgenden TPC-DS-Tabellen in SQL Server vorhanden sind:

![](media/desktop-directquery-about/directquery-about_09.png)

Bedenken Sie die folgende Abfrage:

![](media/desktop-directquery-about/directquery-about_10.png)

Diese Abfrage ergibt folgendes visuelles Element:

![](media/desktop-directquery-about/directquery-about_11.png)

Wenn Sie dieses visuelle Element aktualisieren, ergibt dies eine SQL-Abfrage, die Sie im nächsten Paragraphen sehen können. Wie Sie erkennen können, gibt es drei untergeordnete SELECT-Ausdrücke für Web Sales, Item und Date_dim, die jeweils alle Spalten in der jeweiligen Tabelle zurückgeben, obwohl das visuelle Element tatsächlich nur auf vier Spalten verweist. Diese Abfragen in den untergeordneten SELECT-Ausdrücken (schattiert) sind genau die Ergebnisse der Abfragen, die im **Abfrage-Editor** definiert sind. Die Verwendung untergeordneter SELECT-Ausdrücke beeinträchtigt die Leistung nicht für Datenquellen, die bisher für DirectQuery unterstützt wurden. Datenquellen wie SQL Server optimieren die Verweise auf die anderen Spalten.

Ein Grund, warum Power BI dieses Muster übernimmt, ist, da die verwendete SQL-Abfrage direkt durch den Analyst bereitgestellt werden kann. Sie wird also „wie bereitgestellt“ verwendet, ohne dass versucht wird, sie umzuschreiben.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Nächste Schritte
Dieser Artikel beschreibt Aspekte von **DirectQuery**, die für alle Datenquellen gängig sind. Es gibt bestimmte Details, die spezifisch für einzelne Datenquellen sind. Informationen finden Sie in den folgenden Artikeln, die bestimmte Quellen abdecken:

* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)

Weitere Informationen zu **DirectQuery** finden Sie sich den folgenden Ressourcen:

* [Data Sources supported by DirectQuery (Von DirectQuery unterstützte Datenquellen)](desktop-directquery-data-sources.md)

