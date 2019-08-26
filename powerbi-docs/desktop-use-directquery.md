---
title: Verwenden von DirectQuery in Power BI Desktop
description: Verwenden von DirectQuery („Liveverbindung“) in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/19/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6664924a10b89e057765d70499208aede2d7fdad
ms.sourcegitcommit: 4a3afe761d2f4a5bd897fafb36b53961739e8466
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69654783"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Verwenden von DirectQuery in Power BI Desktop
Wenn Sie mit **Power BI Desktop** eine Verbindung zu Ihrer Datenquelle herstellen, ist es immer möglich, eine Kopie der Daten in **Power BI Desktop** zu importieren. Für einige Datenquellen steht ein alternativer Ansatz zur Verfügung: das Herstellen einer direkten Verbindung zur Datenquelle mit **DirectQuery**.

## <a name="supported-data-sources"></a>Unterstützte Datenquellen
Eine vollständige Auflistung der Datenquellen, die **DirectQuery** unterstützen, finden Sie unter [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md).

## <a name="how-to-connect-using-directquery"></a>Herstellen einer Verbindung mithilfe von DirectQuery
Wenn Sie **Daten abrufen** verwenden, um eine Verbindung mit einer Datenquelle herzustellen, die von **DirectQuery** unterstützt wird, können Sie im Verbindungsfenster auswählen, wie Sie die Verbindung herstellen möchten.  

![](media/desktop-use-directquery/directquery_2a.png)

**Importieren** und **DirectQuery** weisen folgende Unterschiede auf:

**Importieren:** Die ausgewählten Tabellen und Spalten werden in **Power BI Desktop** importiert. Beim Erstellen oder Interagieren mit einer Visualisierung verwendet **Power BI Desktop** die importierten Daten. Um Änderungen anzuzeigen, die seit dem ersten Import oder der letzten Aktualisierung an den zugrunde liegenden Daten vorgenommen wurden, müssen Sie die Daten aktualisieren. Dabei wird das vollständige Dataset erneut importiert.

**DirectQuery:** Es werden keine Daten in **Power BI Desktop** importiert oder kopiert. Bei relationalen Quellen werden die ausgewählten Tabellen und Spalten in der Liste **Felder** angezeigt. Bei mehrdimensionalen Datenquellen wie SAP Business Warehouse werden die Dimensionen und Measures für den ausgewählten Cube in der Liste **Felder** angezeigt. Beim Erstellen oder Interagieren mit einer Visualisierung fragt **Power BI Desktop** die zugrunde liegende Datenquelle ab. Das bedeutet, dass Ihnen immer aktuelle Daten angezeigt werden.

Bei Verwendung von **DirectQuery** sind viele Datenmodelle und Datentransformationen verfügbar, jedoch mit einigen Einschränkungen. Beim Erstellen oder Interagieren mit einer Visualisierung muss die zugrunde liegende Datenquelle abgefragt werden. Die zum Aktualisieren der Visualisierung erforderliche Zeit ist abhängig von der Leistung der zugrunde liegenden Datenquelle. Wenn die erforderlichen Daten für die Anforderung kürzlich abgefragt wurden, verwendet Power BI Desktop diese Daten, damit weniger Zeit zum Anzeigen der Visualisierung benötigt wird. Durch Auswählen von **Aktualisieren** im Menüband auf der Registerkarte **Start** wird sichergestellt, dass alle Visualisierungen mit aktuellen Daten aktualisiert werden.

Im Artikel [Power BI und DirectQuery](desktop-directquery-about.md) wird **DirectQuery** im Detail beschrieben. Weitere Informationen über die Vorteile und Einschränkungen sowie wichtige Überlegungen zur Verwendung von **DirectQuery** finden Sie außerdem in den folgenden Abschnitten.

## <a name="benefits-of-using-directquery"></a>Vorteile der Verwendung von DirectQuery
Einige Vorteile sprechen für die Verwendung von **DirectQuery**:

* Mithilfe von **DirectQuery** können Visualisierungen sehr großer Datasets erstellt werden, bei denen es andernfalls nicht möglich wäre, sämtliche Daten mit Vorabaggregation zu importieren.
* Änderungen an den zugrunde liegenden Daten können eine Aktualisierung der Daten erforderlich machen, und bei einigen Berichten kann das Erfordernis, aktuelle Daten zu zeigen, sehr umfangreiche Datenübertragungen mit sich bringen, was das erneute Importieren von Daten praktisch ausschließt. Im Gegensatz dazu verwenden **DirectQuery** -Berichte immer aktuelle Daten.
* Die Einschränkung auf 1 GB für Datasets gilt *nicht* für **DirectQuery**.

## <a name="limitations-of-directquery"></a>Einschränkungen für DirectQuery
Derzeit bestehen einige Einschränkungen bei der Verwendung von **DirectQuery**:

* Alle Tabellen müssen aus einer einzelnen Datenbank kommen, es sei denn, es werden [zusammengesetzte Modelle](desktop-composite-models.md) verwendet.

* Wenn die Abfrage im **Abfrage-Editor** übermäßig komplex ist, tritt ein Fehler auf. Um den Fehler zu beheben, müssen Sie wie folgt vorgehen: Löschen Sie den fraglichen Schritt im **Abfrage-Editor**, oder *importieren* Sie die Daten, statt **DirectQuery** zu verwenden. Bei mehrdimensionalen Datenquellen wie SAP Business Warehouse ist kein **Abfrage-Editor** vorhanden.

* Zeitintelligenzfunktionen sind in **DirectQuery** nicht verfügbar. Beispielsweise wird die spezifische Behandlung von Datumsspalten (Jahr, Quartal, Monat, Tag usw.) im **DirectQuery**-Modus nicht unterstützt.

* Um sicherzustellen, dass Abfragen, die an die zugrundeliegende Datenquelle gesendet werden, eine akzeptable Leistung aufweisen, werden für Measures standardmäßig DAX-Einschränkungen angewendet.

* Bei Verwendung von **DirectQuery** können maximal 1 Million Zeilen mit Daten zurückgegeben werden. Dies betrifft nicht Aggregationen oder Berechnungen, die zum Erstellen des mit **DirectQuery** zurückgegebenen Datasets verwendet wurden, sondern nur die zurückgegebenen Zeilen. Sie können beispielsweise 10 Millionen Zeilen mit der Abfrage aggregieren, die für die Datenquelle ausgeführt wird, und die Ergebnisse dieser Aggregation mithilfe von **DirectQuery** präzise an Power BI zurückgeben, solange weniger als 1 Million Zeilen mit Daten an Power BI zurückgegeben werden. Wenn mehr als 1 Million Zeilen von **DirectQuery** zurückgegeben werden, gibt Power BI einen Fehler aus.

## <a name="important-considerations-when-using-directquery"></a>Wichtige Überlegungen bei der Verwendung von DirectQuery
Die folgenden drei Punkte sollten Sie bei der Verwendung von **DirectQuery** berücksichtigen:

* **Leistung und Auslastung** – Alle **DirectQuery**-Anforderungen werden an die Quelldatenbank gesendet. Daher hängt die erforderliche Zeitspanne für die Aktualisierung eines visuellen Elements davon ab, wie lange diese Back-End-Quelle für die Rückgabe der Ergebnisse der Abfrage (bzw. Abfragen) benötigt. Die empfohlene Reaktionszeit (mit der Rückgabe der angeforderten Daten) für die Verwendung von **DirectQuery** für visuelle Elemente beträgt fünf Sekunden oder weniger. Die empfohlene maximale Reaktionszeit für Ergebnisse beträgt 30 Sekunden. Eine längere Zeitspanne stellt eine inakzeptable Beeinträchtigung der Benutzerfreundlichkeit des Berichts dar. Sobald ein Bericht im Power BI-Dienst veröffentlicht wurde, tritt außerdem für jede Abfrage, die länger als einige Minuten dauert, ein Timeout auf, und der Benutzer erhält einen Fehler.
  
  Auch sollte die Auslastung der Quelldatenbank basierend auf der Anzahl der Power BI-Benutzer berücksichtigt werden, die den veröffentlichten Bericht verwenden werden. Die Verwendung von *Sicherheit auf Zeilenebene* (Row Level Security, RLS) kann ebenfalls erhebliche Auswirkungen haben. Eine Nicht-RLS-Dashboardkachel, die von mehreren Benutzern gemeinsam verwendet wird, führt zu einer einzelnen Datenbankabfrage, doch die Verwendung von RLS für eine Dashboardkachel bedeutet in der Regel, dass für die Aktualisierung einer Kachel eine Abfrage *pro Benutzer* erforderlich ist. Hierdurch wird die Auslastung der Quelldatenbank deutlich erhöht und die Leistung möglicherweise beeinträchtigt.
  
  Power BI erstellt Abfragen, die so effizient wie möglich sind. In bestimmten Situationen jedoch ist die generierte Abfrage möglicherweise nicht effizient genug, um Aktualisierungsfehler zu verhindern. Ein Beispiel für eine solche Situation ist eine generierte Abfrage, die eine übermäßig große Anzahl von Zeilen aus der Back-End-Datenquelle abruft. In diesem Fall tritt der folgende Fehler auf:
  
      The resultset of a query to external data source has exceeded
  
  Diese Situation kann bei einem einfachen Diagramm auftreten, das eine sehr hohe Kardinalitätsspalte enthält und für das die Aggregationsoption auf *Nicht zusammenfassen* festgelegt ist. Das visuelle Element darf nur Spalten mit einer Kardinalität unter 1 Million enthalten, oder es müssen entsprechenden Filter angewendet werden.
* **Sicherheit** – Alle Benutzer, die einen veröffentlichten Bericht verwenden, stellen die Verbindung mit der Back-End-Datenquelle mit den Anmeldeinformationen her, die nach der Veröffentlichung im Power BI-Dienst eingegeben wurden. Dies ist dieselbe Ausgangssituation wie bei importierten Daten: Für alle Benutzer werden dieselben Daten angezeigt, unabhängig von den in der Back-End-Datenquelle definierten Sicherheitsregeln. Kunden, die mit DirectQuery-Quellen benutzerspezifische Sicherheit implementieren möchten, sollten RLS verwenden. [Erfahren Sie mehr zu RLS](service-admin-rls.md).
* **Unterstützte Funktionen** – Nicht alle Funktionen in **Power BI Desktop** werden im **DirectQuery**-Modus unterstützt, oder es gelten bestimmte Einschränkungen. Darüber hinaus sind einige Funktionen des Power BI-Diensts (z. B. *Schnelleinblicke*) nicht für Datasets verfügbar, die **DirectQuery** verwenden. Daher sollten die Einschränkungen dieser Funktionen bei der Verwendung von **DirectQuery** berücksichtigt werden, wenn bestimmt wird, ob **DirectQuery** verwendet werden soll.   

## <a name="publish-to-the-power-bi-service"></a>Veröffentlichen im Power BI-Dienst
Mit **DirectQuery** erstellte Berichte können im Power BI-Dienst veröffentlicht werden.

Wenn die Datenquelle kein **lokales Datengateway** benötigt (**Azure SQL-Datenbank**, **Azure SQL Data Warehouse** oder **Redshift**), müssen Anmeldeinformationen bereitgestellt werden, bevor der veröffentlichte Bericht im Power BI-Dienst angezeigt wird.

Sie können Anmeldeinformationen angeben, indem Sie in Power BI das Zahnradsymbol **Einstellungen** und anschließend **Einstellungen**auswählen.

![](media/desktop-use-directquery/directquery_3.png)

Power BI zeigt das Fenster **Einstellungen** an. Wählen Sie dort die Registerkarte **Datasets** und anschließend das Dataset aus, das **DirectQuery** verwendet. Wählen Sie dann **Anmeldeinformationen bearbeiten** aus.

![](media/desktop-use-directquery/directquery_4.png)

Wenn Sie vor der Angabe von Anmeldeinformationen versuchen, einen veröffentlichten Bericht zu öffnen oder ein Dataset zu untersuchen, das bzw. der mit einer **DirectQuery**-Verbindung zu einer solchen Datenquelle erstellt wurde, führt dies zu einem Fehler.

Bei anderen Datenquellen als **Azure SQL-Datenbank**, **Azure SQL Data Warehouse** und **Redshift**, die DirectQuery verwenden, muss ein **lokales Datengateway** installiert sein und die Datenquelle registriert werden, um eine Datenverbindung herstellen zu können. Lesen Sie zu diesem Thema den [Artikel zum lokalen Datengateway](http://go.microsoft.com/fwlink/p/?LinkID=627094).

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu **DirectQuery** finden Sie sich den folgenden Ressourcen:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
* [Lokales Datengateway](service-gateway-onprem.md)

