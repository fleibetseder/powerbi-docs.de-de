---
title: Bereitstellen und Verwalten von Power BI Premium Kapazitäten
description: Machen Sie sich mit den möglichen Power BI Premium vertraut, und erfahren Sie, wie Sie skalierbare Lösungen entwerfen, bereitstellen, überwachen und beheben.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: eecbc43f26cebc12884ae6c5143a815f6e310ce5
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432367"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Bereitstellen und Verwalten von Power BI Premium Kapazitäten

**Zusammenfassung:** Power BI Premium bietet eine konsistente Leistung, Unterstützung für große Datenvolumes und die Flexibilität einer einheitlichen Self-Service-und Enterprise-BI-Plattform für alle Personen in Ihrer Organisation. Dieses technische Whitepaper der Ebene 300 wurde speziell für Power BI-Administratoren und Inhaltsautoren und-Herausgeber geschrieben. Es soll Ihnen helfen, das Potenzial von Power BI Premium zu verstehen und zu erläutern, wie Sie skalierbare Lösungen entwerfen, bereitstellen, überwachen und beheben können.

**Autor:** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (Data Platform MVP und unabhängiger BI-Experte mit bitweisen Lösungen)

**Technische Reviewer:** Adam Saxton, akshai spiechandani, bhavik Händler, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Olivier matrat, Swati Gupta

**Gilt für:** Power BI-Dienst, Power BI Premium und Azure-Power BI Embedded Kapazität

> [!NOTE]
> Sie können dieses Whitepaper speichern oder ausdrucken, indem Sie in Ihrem Browser erst auf **Drucken** und dann auf **Als PDF speichern** klicken.

## <a name="introducing-power-bi"></a>Einführung in Power BI

Power BI ist ein Business Analytics-Dienst, der für die Bereitstellung von Erkenntnissen konzipiert ist, die schnelle, fundierte Entscheidungen ermöglichen Seit seiner Veröffentlichung in 2015 ist es schnell ein beliebter Dienst, der zum Bereitstellung von Lösungen für die kleinsten Organisationen der größten Unternehmen genutzt wird.

Sie wird auf zwei Arten verfügbar gemacht: als clouddienst und als lokale Berichterstattungs Lösung mit dem Namen **Power BI-Berichtsserver**. \[[1](#endnote-01)\]

Power BI als clouddienst ist Software-as-a-Service (SaaS) \[[2](#endnote-02)\]. Es stellt eine Reihe von Diensten und Anwendungen dar, die es Organisationen ermöglichen, Lösungen zum Überwachen Ihres Geschäfts zu entwickeln, bereitzustellen, zu verwalten und freizugeben.

Dieses Whitepaper ist nicht in der Absicht, eine umfassende Beschreibung des Power BI-Dienst bereitzustellen. Er konzentriert sich stattdessen auf Themen, die für den Betreff von Power BI Premium relevant sind. Allgemeine Informationen zu Power BI finden Sie in der Dokumentation zu umfassenden [Power BI](service-admin-premium-multi-geo.md). Eine ausführlichere Erläuterung der Power BI-Dienst, die sich auf das erreichen von leistungsstarken Unternehmens Bereitstellungen konzentriert, finden Sie im Whitepaper zur umfassenden [Planung einer Power BI Unternehmens Bereitstellung](https://aka.ms/pbienterprisedeploy) .

Im Rahmen des Themas dieses Whitepaper werden in diesem Abschnitt Kapazitäten, Power BI von Inhaltstypen, Modell Speicher Modi und Lizenzierung vorgestellt und beschrieben. Ein Verständnis dieser Themen ist für die erfolgreiche Bereitstellung und Verwaltung von Power BI Premium von entscheidender Bedeutung.

### <a name="capacities"></a>Funktionen

**Kapazitäten** sind ein Kern Power BI Konzept, das einen Satz von Ressourcen (Speicher, Prozessor und Arbeitsspeicher) darstellt, die zum Hosten und Bereitstellen Power BI Inhalts verwendet werden. Kapazitäten werden entweder gemeinsam genutzte oder sind dediziert. Eine **gemeinsam genutzte Kapazität** wird für andere Microsoft-Kunden freigegeben, während eine **dedizierte Kapazität** vollständig einem einzelnen Kunden zugewiesen wird. Dedizierte Kapazitäten werden im Thema [Premium-Kapazitäten](#premium-capacities) eingeführt.

Bei gemeinsam genutzten Kapazitäten werden Workloads auf Computeressourcen ausgeführt, die gemeinsam mit anderen Kunden genutzt werden. Da die Kapazität Ressourcen gemeinsam nutzen muss, werden Einschränkungen auferlegt, um "Fairplay" zu gewährleisten, z. b. die maximale Modell Größe (1 GB) und die maximale tägliche Aktualisierungshäufigkeit (acht Mal pro Tag).

### <a name="workspaces"></a>Arbeitsbereiche

Power BI Arbeitsbereiche befinden sich innerhalb von Kapazitäten und stellen Sicherheits-, Zusammenarbeits-und Bereitstellungs Container dar. Jeder Power BI-Benutzer verfügt über einen persönlichen Arbeitsbereich, der als **Mein Arbeitsbereich** bezeichnet wird. Zusätzliche Arbeitsbereiche können erstellt werden, um die Zusammenarbeit und Bereitstellung zu ermöglichen. Diese werden als **Arbeitsbereiche**bezeichnet. Arbeitsbereiche, einschließlich persönlicher Arbeitsbereiche, werden standardmäßig in der gemeinsam genutzten Kapazität erstellt.

### <a name="power-bi-content-types"></a>Power BI von Inhaltstypen

Um Power BI Premium Themen einzuführen, ist es wichtig, mit einer umfassenden Erörterung der Power BI Architektur zu beginnen, einschließlich grundlegender Inhaltstypen.

Alle Power BI Inhalt werden innerhalb von Arbeitsbereichen gespeichert und verwaltet, die Container für Power BI Inhalte sind. Jeder Power BI Benutzer verfügt über einen eigenen persönlichen Arbeitsbereich, aber die allgemeine bewährte Vorgehensweise besteht darin, Arbeitsbereiche zu erstellen. Arbeitsbereiche ermöglichen den gemeinsamen Besitz von Inhalten sowie die Möglichkeit, an Inhalten zusammenzuarbeiten. Außerdem haben Sie die Möglichkeit, Inhalte als apps bereitzustellen und an große Zielgruppen zu verteilen.

Der folgende Power BI Inhalt wird in Arbeitsbereichen gespeichert:

- Dataflows
- Datasets
- Arbeitsmappen
- Berichte
- Dashboards

#### <a name="dataflows"></a>Dataflows

Power BI Datenflüsse helfen Organisationen dabei, Daten aus unterschiedlichen Quellen zu vereinheitlichen. Sie können als Daten vorbereitet und bereitgestellt werden, die für die Verwendung in Modellen bereitgestellt werden. Sie können jedoch nicht direkt als Quelle für die Berichterstellung verwendet werden. Sie nutzen die umfangreiche Sammlung von Microsoft-datenconnectors und ermöglichen so die Erfassung von Daten aus lokalen und cloudbasierten Datenquellen.

Dataflows können nur in Arbeitsbereichen erstellt und verwaltet werden, und Sie werden als Entitäten im Common Data Model (CDM) in Azure Data Lake Storage Gen2 gespeichert. In der Regel werden Sie so geplant, dass Sie regelmäßig aktualisiert werden, um aktuelle Daten zu speichern.

Weitere Informationen finden Sie [im Dokument Self-Service-Daten Vorbereitung in Power BI (Vorschau)](service-dataflows-overview.md) .

#### <a name="datasets"></a>Datasets

Power BI Datasets stellen eine Datenquelle dar, die für die Berichterstellung und Visualisierung bereit ist. Es gibt viele Arten von Datasets, die von erstellt werden:

- Herstellen einer Verbindung mit einem vorhandenen Datenmodell, das nicht in einer Power BI Kapazität gehostet wird
- Hochladen einer Power BI Desktop-Datei, die ein Modell enthält
- Hochladen einer Excel-Arbeitsmappe (mit einer oder mehreren Excel-Tabellen und/oder einem arbeitsmappendatenmodell) oder Hochladen einer CSV-Datei (Comma-Separated Value)
- Verwenden des Power BI-Dienst zum Erstellen eines Push-, Streaming-oder Hybrid Streaming-Datasets

Mit Ausnahme der streamingdatasets \[[3](#endnote-03)\]stellt das Dataset ein Datenmodell dar, das die ausgereiften Modellierungs Technologien von Analysis Services nutzt.

Beachten Sie, dass die Terminologien-Datasets und-Modelle in der-Dokumentation manchmal austauschbar sind. Im Allgemeinen wird Sie aus einer Power BI-Dienst Perspektive als **DataSet** bezeichnet, und aus Sicht der Entwicklung wird Sie als **Modell**bezeichnet. Im Zusammenhang mit diesem Whitepaper haben Sie viel zu tun.

##### <a name="externally-hosted-models"></a>Extern gehostete Modelle

Zum Herstellen einer Verbindung mit einem extern gehosteten Modell müssen Sie das [lokale Daten Gateway](service-gateway-onprem.md) installieren, um eine Verbindung mit SQL Server Analysis Services herzustellen, unabhängig davon, ob es sich um eine lokale oder eine VM-gehostete Infrastructure-as-a-Service (IaaS) handelt. Azure Analysis Services erfordert kein Gateway. Dieses Szenario ist häufig sinnvoll, wenn vorhandene Modell Investitionen vorhanden sind, die in der Regel einen Teil des Enterprise Data Warehouse (EDW) bilden. Sie ermöglicht es Power BI, eine **Live Verbindung** (LC) auszuführen, um zu Analysis Services. Dies geschieht durch Erzwingen von Daten Berechtigungen mithilfe der Identität des Power BI Berichts Benutzers. Für SQL Server Analysis Services werden sowohl mehrdimensionale Modelle (Cubes) als auch tabellarische Modelle unterstützt. Wie in der folgenden Abbildung gezeigt, übergibt ein Live Connection-DataSet Abfragen an extern gehostete Modelle.

![Ein Live Connection-DataSet übergibt Abfragen an extern gehostete Modelle.](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Power BI Desktop entwickelte Modelle

Power BI Desktop: eine Client Anwendung, die für die Power BI Entwicklung vorgesehen ist, kann verwendet werden, um ein Modell zu entwickeln, das tatsächlich ein Analysis Services tabellarisches Modell ist. Modelle können durch Importieren von Daten aus Daten Flüssen entwickelt werden, die anschließend in andere Datenquellen integriert werden können. Obwohl die Besonderheiten, wie die Modellierung erreicht werden kann, den Rahmen dieses Whitepaper sprengen, ist es wichtig zu verstehen, dass es drei verschiedene Typen oder Modi gibt, die mithilfe von Power BI Desktop entwickelt werden können. Diese Modi bestimmen, ob Daten in das Modell importiert werden oder ob Sie in der Datenquelle verbleiben. Die drei Modi lauten: Import, directquery und Composite. Eine vollständige Erläuterung der einzelnen Modi finden Sie im Thema [Modell Speicher Modi](#model-storage-modes) .

Extern gehostete Modelle und Modelle, die in Power BI Desktop entwickelt wurden, können Sicherheit auf Zeilenebene (Row-Level Security, RLS) erzwingen, um die Daten einzuschränken, die für einen bestimmten Benutzer abgerufen werden können. Beispielsweise können Benutzer, denen die Sicherheitsgruppe "Salespeople" zugewiesen ist, nur Berichtsdaten für die Verkaufs Regionen anzeigen, denen Sie zugewiesen sind. RLS-Rollen können dynamisch oder statisch sein. **Dynamische Rollen** Filtern nach dem Berichts Benutzer, während **statische Rollen** dieselben Filter für alle Benutzer anwenden, die der Rolle zugewiesen sind.

##### <a name="excel-workbook-models"></a>Excel-arbeitsmappenmodelle

Das Erstellen von Datasets auf der Grundlage von Excel-Arbeitsmappen oder CSV-Dateien führt zur automatischen Erstellung eines Modells. Excel-Tabellen und CSV-Daten werden importiert, um Modell Tabellen zu erstellen, während ein Excel-arbeitsmappendatenmodell zum Erstellen eines Power BI Modells übertragen wird. In allen Fällen werden Datei Daten in ein Modell importiert.

Unterschiede können dann über Power BI Datasets, die Modelle darstellen, vorgenommen werden:

- Sie werden entweder in der Power BI-Dienst gehostet oder extern von Analysis Services
- Sie können importierte Daten speichern oder Pass-Through-Abfrage Anforderungen an zugrunde liegende Datenquellen oder eine Kombination aus beidem ausgeben.

Im folgenden finden Sie eine Zusammenfassung wichtiger Fakten zu Power BI Datasets, die Modelle darstellen:

- SQL Server Analysis Services gehosteten Modellen erfordert ein Gateway zum Ausführen von LC-Abfragen.
- Power BI gehostete Modelle, mit denen Daten importiert werden
  - Muss vollständig in den Arbeitsspeicher geladen werden, damit Sie abgefragt werden können.
  - Aktualisierung erforderlich, um Daten aktuell zu halten, und muss Gateways umfassen, wenn nicht direkt über das Internet auf Quelldaten zugegriffen werden kann
- In Power BI gehosteten Modellen, die den directquery-Speicher Modus (DQ) verwenden, ist eine Verbindung mit den Quelldaten erforderlich. Wenn das Modell abgefragt wird, gibt Power BI Abfragen an die Quelldaten aus, um die aktuellen Daten abzurufen. Dieser Modus muss Gateways umfassen, wenn nicht direkt über das Internet auf Quelldaten zugegriffen werden kann.
- Modelle können RLS-Regeln erzwingen und Filter erzwingen, um den Datenzugriff auf bestimmte Benutzer einzuschränken.

Um Power BI Premium erfolgreich bereitzustellen und zu verwalten, ist es wichtig, zu verstehen, wo Modelle gehostet werden, welchen Speicher Modus, welche Abhängigkeiten von Gateways, die Größe der importierten Daten und den Aktualisierungstyp und die Häufigkeit haben. Diese können alle Power BI Premium Ressourcen erheblich beeinträchtigen. Darüber hinaus kann der Modellentwurf selbst einschließlich der Daten Vorbereitungs Abfragen und-Berechnungen der Mischung der Überlegungen hinzugefügt werden.

Es ist auch wichtig zu verstehen, dass Power BI von gehosteten Import Modellen nach Zeitplan aktualisiert oder bei Bedarf von einem Benutzer im Power BI-Dienst ausgelöst werden können.

Das Entwerfen optimierter Modelle wird weiter unten in diesem technischen Artikel des Themas [Optimierungsmodelle](#optimizing-models) erläutert.

#### <a name="workbooks"></a>Arbeitsmappen

Power BI Arbeitsmappen sind Power BI Inhaltstyp \[[4](#endnote-04)\]. Dabei handelt es sich um Excel-Arbeitsmappen, die in den Power BI-Dienst hochgeladen wurden und nicht mit hochgeladenen Excel-Arbeitsmappen verwechselt werden sollten, die Datasets (Modelle) erstellen. Der Inhaltstyp der Arbeitsmappe stellt eine Verbindung mit einer-Arbeitsmappe dar, die entweder in den Power BI-Dienst hochgeladen oder im cloudspeicher auf onedrive oder SharePoint Online verbleiben kann.

Es ist wichtig zu wissen, dass dieser Inhaltstyp nicht als Datenquelle für die Power BI von Datenvisualisierungen verfügbar ist. Stattdessen kann Sie mithilfe von Excel Online als Arbeitsmappe in der Power BI-Dienst geöffnet werden. Der Hauptzweck dieses Inhaltstyps besteht darin, den Zugriff auf ältere Excel-arbeitsmappenberichte innerhalb des Power BI-Dienst zuzulassen und die Datenvisualisierungen an Power BI Dashboards zu binden.

Weitere Informationen finden Sie im Dokument [Get Data from Excel Arbeitsmappendateien](service-excel-workbook-files.md) .

#### <a name="reports"></a>Berichte

Es gibt zwei Arten von Berichten: Power BI Berichte und paginierte Berichte.

**Power BI Berichte** bieten eine interaktive Oberfläche für die Datenvisualisierung, die nur eine Verbindung mit einem einzelnen Dataset herstellt. Berichte sind häufig darauf ausgelegt, die Benutzer Teilnahme zu fördern, sodass Sie mit einem außergewöhnlichen Funktionsumfang interagieren können, darunter Filterung, Slicing, Kreuz Filterung und Hervorhebung, Drilldown, Drilldown, Drillthrough, Q & eine natürliche Sprachfrage, Fokus, Seitennavigation, Spotbeleuchtung, Anzeige von Lesezeichen usw.

Im Zusammenhang mit diesem Whitepaper ist es wichtig zu verstehen, wie sich die Power BI Architektur, Power BI Berichtsentwurf und Benutzerinteraktionen, auf die Power BI-Dienst Ressourcen auswirken können:

- Zum Laden von und interagieren mit Berichten auf der Grundlage von Import Modellen muss das Modell vollständig in den Arbeitsspeicher geladen werden (unabhängig davon, ob es im Power BI-Dienst gehostet oder extern gehostet wird).
- Jede Berichts Visualisierung gibt eine Abfrage aus, um Daten abzurufen, indem das Modell abgefragt wird.
- Im Allgemeinen umfassen Filter-und slicerinteraktionen das Abfragen des Modells. Wenn Sie z. b. eine slicerauswahl ändern, muss jedes Visual auf der Seite \[[5](#endnote-05) erneut geladen werden\]
- Power BI Berichte gewährleisten nicht, dass aktuelle Daten angezeigt werden. möglicherweise muss der Benutzer den Bericht aktualisieren, um die Berichtsseite und seine visuellen Elemente neu zu laden.
- Benutzer können mit der Q & eine Funktion in natürlicher Sprache zusammenarbeiten, um Fragen zu stellen. Sie können die Power BI Berichtsentwürfe bereitstellen, und das DataSet stellt ein Power BI gehostete Datenimport Modell oder ein LC-DataSet dar, das zum Aktivieren von Q & A konfiguriert ist.

**Paginierte Berichte** , die das Veröffentlichen und Rendering von SQL Server Reporting Services (SSRS)-Berichten ermöglichen (\*. RDL-Format). Wie der Name bereits vermuten lässt, werden paginierte Berichte häufig verwendet, wenn Anforderungen für das Drucken in eine festgelegte Seitengröße erforderlich sind oder wenn Variablen Listen mit Daten vorhanden sind, die vollständig erweitert werden müssen. Beispielsweise eine Rechnung, die für das Rendering mehrerer Seiten (statt eines Bildlaufs innerhalb eines visuellen Elements) und zum Drucken entworfen wurde.

Die beiden unterstützten Berichts Typen bieten die Wahl für Berichts Autoren, sodass Sie den Typ basierend auf den Anforderungen und der vorgesehenen Verwendung auswählen können. Im Allgemeinen sind Power BI Berichte ideal für interaktive Benutzeroberflächen, die es dem Benutzer ermöglichen, Einblicke in Daten zu untersuchen und zu ermitteln, während paginierte Berichte für Parameter gesteuerte Seitenlayouts besser geeignet sind.

Unabhängig vom Berichtstyp ist das erzielen von reaktionsfähigen Berichts Lade-und Datenaktualisierungen (wenn Filter oder Parameter geändert werden) zwingend erforderlich, um eine zuverlässige und leistungsfähige Benutzerfunktion bereitzustellen.

#### <a name="dashboards"></a>Dashboards

Power BI Dashboards sind für die Bereitstellung von Überwachungsumgebungen gedacht und unterscheiden sich konzeptionell stark von Power BI Berichten. Dashboards sind für die Anzeige in einem einzelnen Glasbereich konzipiert, um Werte und Datenvisualisierungen in Kacheln auszudrücken. Im Allgemeinen bieten Dashboards weniger Interaktionen als Power BI Berichte, wobei einige dashboardentwürfe keine Interaktion erwarten. Beispielsweise ein unbeaufsichtigtes Dashboard, das auf einem nicht-Touchscreen in einem Serverraum angezeigt wird. Ein weiterer bedeutender Unterschied besteht darin, dass Dashboards Kacheln darstellen können, die Daten aus mehreren Datasets Quellen, während ein Power BI Bericht immer nur auf einem einzelnen Dataset basieren kann.

Es ist wichtig zu verstehen, dass ein Dashboard so konzipiert ist, dass es schnell geladen wird und die aktuellsten Daten (die Power BI-Dienst) jederzeit ausgedrückt werden. Dies wird erreicht, indem Kachel Abfrageergebnisse zwischengespeichert werden, und dies erfolgt für jedes Dashboard. Tatsächlich muss dies für jeden Benutzer durchzuführen sein, der Zugriff auf ein Dashboard hat, das auf Modellen basiert, die dynamische RLS erzwingen.

Der Power BI-Dienst aktualisiert dashboardabfragecaches sofort nach der Aktualisierung von Power BI gehosteten Import Modellen. Im Fall von LC-und DQ-Modellen hat der Besitzer des Datasets einen gewissen Grad an Kontrolle darüber, wie oft das Power BI-Dienst den Cache aktualisiert, der so häufig als alle 15 Minuten konfiguriert werden kann oder so selten wie einmal pro Woche. Beachten Sie, dass LC-Abfragecache Updates zuerst Modell Metadaten Abfragen, um zu bestimmen, ob eine Modell Aktualisierung seit dem letzten Cache Update stattgefunden hat, und dass der Cache nicht mehr aktualisiert wird, wenn eine Aktualisierung nicht durchgeführt wurde. Diese Überprüfung ist für DQ-Modelle nicht möglich, sodass Cache Aktualisierungen unabhängig davon erfolgen, ob sich die Quelldaten geändert haben.

Dashboard-Abfragecache Updates, die auf DQ-und LC-Modellen basieren, können sich erheblich auf Power BI-Dienst Ressourcen und externe Datenquellen auswirken. Angenommen, ein Dashboard mit 20 Kacheln basiert auf einem Azure Analysis Services Modell, das dynamische RLS erzwingt und jede Stunde aktualisiert wird, und dass dieses Dashboard für 100 Benutzer freigegeben wird. Wenn das DataSet stündlich für die Aktualisierung konfiguriert ist, führt dies zu mindestens 2000 (20 x 100) LC-Abfragen. Dies kann zu einer enormen Belastung der Power BI-Dienst und der externen Datenquellen und auch zu den Grenzwerten für die verfügbaren Ressourcen werden. Kapazitäts Ressourcen und-Grenzwerte werden im Thema [Kapazitäts Knoten](#capacity-nodes) beschrieben.

Benutzer können auf verschiedene Weise mit einem Dashboard interagieren, das Power BI-Dienst Ressourcen erfordert. Sie haben insbesondere folgende Möglichkeiten:

- Löst eine Aktualisierung von dashboardkacheln aus. Dies kann zu einer bedarfsgesteuerten Aktualisierung aller zugehörigen Power BI-gehosteten Datenimport Modelle führen.
- Wenden Sie sich an das Q & eine Funktion in natürlicher Sprache, um Fragen zu stellen. (die Bereitstellung des dashboardentwurfs ermöglicht es, und das DataSet ist ein Power BI gehostetes Datenimport Modell oder ein LC-DataSet, das zum Aktivieren von Q & A
- Verwenden Sie die Quick Insights Funktion, um Power BI Einblicke aus einem zugrunde liegenden DataSet zu erhalten und mit visuellen Elementen zu antworten, in denen Sie angezeigt und beschrieben werden (vorausgesetzt, die Kachel basiert auf einem DataSet, das Power BI-gehosteten Datenimport Modell ist).
- Konfigurieren Sie Warnungen auf dashboardkacheln, die erfordern, dass der Power BI-Dienst Schwellenwerte mit Kachel Werten vergleicht (möglicherweise so oft wie stündlich) und Benutzer benachrichtigt werden, wenn Schwellenwerte überschritten werden (vorausgesetzt, die Kachel zeigt einen einzelnen numerischen Wert an und basiert auf einem DataSet, das Power BI-gehosteten Datenimport Modell ist)

### <a name="model-storage-modes"></a>Modell Speicher Modi

Denken Sie daran, dass Power BI Desktop das Entwickeln eines Modells in einem von drei Modi ermöglicht. Es ist wichtig, die Gründe für die einzelnen Datenmodell-Speicher Modi und mögliche Auswirkungen auf Power BI-Dienst Ressourcen zu verstehen. In diesem Abschnitt werden alle drei Modi vorgestellt. Diese werden weiter unten in diesem Whitepaper des Themas Optimierungsmodelle ausführlich erläutert.

#### <a name="import-mode"></a>Import Modus

Der Import Modus ist der am häufigsten verwendete Modus zum Entwickeln von Modellen aufgrund der extrem schnellen Leistung im Zusammenhang mit in-Memory-Abfragen, der für Modeller verfügbaren Entwurfs Flexibilität und der Unterstützung spezifischer Power BI-Dienst Funktionen (Q & A, Quick Insights , usw.). Dies ist der Standardmodus beim Erstellen einer neuen Power BI Desktop Lösung.

Es ist wichtig zu verstehen, dass importierte Daten immer auf einem Datenträger gespeichert werden und vollständig in den Arbeitsspeicher geladen werden müssen, um abgefragt oder aktualisiert werden zu können. Im Arbeitsspeicher erzielen importmodelle blitzschnelle Abfrageergebnisse. Es ist auch wichtig zu verstehen, dass es kein Konzept für ein Import Modell gibt, das teilweise in den Arbeitsspeicher geladen wird.

Bei der Aktualisierung werden die Daten komprimiert und optimiert und dann von der vertibloq-Speicher-Engine auf einem Datenträger gespeichert. Beim Laden von einem Datenträger in den Arbeitsspeicher ist es möglich, die Zehnfache-Komprimierung anzuzeigen. es ist daher sinnvoll zu erwarten, dass 10 GB Quelldaten auf ungefähr 1 GB komprimiert werden können. Die Speichergröße auf dem Datenträger kann eine Verringerung von 20% erreichen. \[[6](#endnote-06)\]

Die Entwurfs Flexibilität kann auf drei Arten erreicht werden. Daten Modeller können folgende Aktionen ausführen:

- Integrieren von Daten durch Zwischenspeichern von Daten aus mehreren Datenquellen (unabhängig vom Typ und Format der Datenquelle)
- Nutzen Sie beim Erstellen von Daten Vorbereitungs Abfragen den gesamten Satz Power Query Formelsprache (als M bezeichnet).
- Nutzen Sie den gesamten Satz von Data Analysis Expressions (DAX)-Funktionen, wenn Sie das Modell mit Geschäftslogik verbessern, die mit berechneten Spalten, berechneten Tabellen und Measures erzielt wurde.

Wie in der folgenden Abbildung gezeigt, kann ein Import Modelldaten aus einer beliebigen Anzahl unterstützter Datenquellen Typen integrieren.

![Ein Import Modell kann Daten aus einer beliebigen Anzahl unterstützter Datenquellen Typen integrieren.](media/whitepaper-premium-deployment/import-model.png)

Obwohl es überzeugende Vorteile im Zusammenhang mit Import Modellen gibt, gibt es auch Nachteile:

- Das gesamte Modell muss in den Arbeitsspeicher geladen werden, bevor Power BI das Modell Abfragen kann. Dadurch kann der Druck auf verfügbare Ressourcen bei Anwachsen der Anzahl und Größe von Modellen entstehen.
- Modelldaten sind nur so aktuell wie die aktuellste Aktualisierung, weshalb importmodelle aktualisiert werden müssen, vorzugsweise auf der Grundlage eines Zeitplans.
- Bei einer vollständigen Aktualisierung werden alle Daten aus allen Tabellen entfernt und aus der Datenquelle erneut geladen. Dies kann in Bezug auf die Zeit und die Ressourcen für die Power BI-Dienst und die Datenquellen sehr teuer sein. Power BI bietet Unterstützung für die inkrementelle Aktualisierung, die das Abschneiden und erneute Laden ganzer Tabellen vermeiden kann. Dies wird im Thema [optimieren Power BI gehosteter Modelle](#optimizing-power-bi-hosted-models) beschrieben.

Aus Sicht der Power BI-Dienst Ressource ist für importmodelle Folgendes erforderlich:

- Genügend Arbeitsspeicher zum Laden des Modells, wenn es abgefragt oder aktualisiert wird
- Verarbeiten von Ressourcen und zusätzlichen Speicherressourcen zum Aktualisieren von Daten

#### <a name="directquery-mode"></a>Directquery-Modus

Modelle, die im directquery-Modus (DQ) entwickelt wurden, importieren keine Daten. Stattdessen bestehen Sie nur aus Metadaten, die beim Abfragen von systemeigenen Abfragen an die zugrunde liegende Datenquelle ausgegeben werden.

![Ein directquery-Modell gibt Native Abfragen an die zugrunde liegende Datenquelle aus.](media/whitepaper-premium-deployment/direct-query-model.png)

Es gibt zwei Hauptgründe, ein DQ-Modell zu entwickeln. Der erste Grund ist, dass Datenvolumes zu groß sind, auch wenn Daten Reduzierungs Methoden angewendet werden, um Sie in ein Modell zu laden oder praktisch zu aktualisieren. Der zweite Grund ist, wenn Berichte und Dashboards "Near Real-Time"-Daten liefern müssen, die über die möglichen Anforderungen innerhalb geplanter Aktualisierungs Limits hinausgehen (48 mal pro Tag für eine dedizierte Kapazität).

Es gibt mehrere Vorteile, die mit DQ-Modellen verbunden sind:

- Die Größenbeschränkungen für das Importieren von Modellen gelten nicht.
- Für Modelle ist keine Aktualisierung erforderlich.
- Berichts Benutzer sehen die neuesten Daten bei der Interaktion mit Berichts Filtern und Slicern und können den gesamten Bericht aktualisieren, um aktuelle Daten abzurufen.
- Dashboardkacheln, die auf DQ-Modellen basieren, können automatisch so oft wie alle 15 Minuten aktualisiert werden.

Es gibt jedoch zahlreiche Nachteile und Einschränkungen im Zusammenhang mit DQ-Modellen:

- Das Modell muss auf einer einzelnen unterstützten Datenquelle basieren. Daher muss die Datenintegration bereits in der Datenquelle erfolgen. Unterstützte Datenquellen sind relationale und analytische Systeme mit Unterstützung für viele beliebte Datenspeicher \[[7](#endnote-07)\].
- Die Leistung kann langsam sein und sich möglicherweise negativ auf die Power BI-Dienst auswirken (Abfragen können sehr CPU-intensiv sind) und auf der Datenquelle (die möglicherweise nicht für Analyse Abfragen optimiert ist).
- Power Query Abfragen können nicht übermäßig komplex sein und sind auf M-Ausdrücke und-Funktionen beschränkt, die in Native Abfragen, die von der Datenquelle gelesen werden, übertragen werden können.
- DAX-Funktionen sind auf jene beschränkt, die in systemeigene Abfragen, die von der Datenquelle verstanden werden, übertragen werden können. berechnete Tabellen oder integrierte Zeit Intelligenz Funktionen werden nicht unterstützt.
- Standardmäßig können Modell Abfragen, die mehr als 1 Million Zeilen abrufen müssen, nicht ausgeführt werden.
- Berichte und Dashboards mit mehreren visuellen Elementen können inkonsistente Ergebnisse anzeigen, insbesondere wenn die Datenquelle flüchtig ist.
- F & A und Quick Insights werden nicht unterstützt.

Aus Sicht der Power BI-Dienst Ressource ist für DQ-Modelle Folgendes erforderlich:

- Minimaler Arbeitsspeicher zum Laden des Modells (nur Metadaten), wenn es abgefragt wird
- Manchmal bedeutende Prozessorressourcen zum Generieren und Verarbeiten von Abfragen, die an die Datenquelle gesendet werden

Weitere Informationen finden Sie [im Dokument verwenden von directquery in Power BI Desktop](desktop-use-directquery.md) .

#### <a name="composite-mode"></a>Zusammengesetzter Modus

Modelle, die im zusammengesetzten Modus entwickelt wurden, ermöglichen das Konfigurieren des Speicherungs Modus für einzelne Modell Tabellen. Daher wird eine Mischung aus Import-und DQ-Tabellen unterstützt. Sie unterstützt auch berechnete Tabellen (die mit DAX definiert sind) und mehrere DQ-Datenquellen.

Der Tabellen Speicher Modus kann als "Import", "directquery" oder "Dual" konfiguriert werden. Eine als Dual Storage-Modus konfigurierte Tabelle ist sowohl Import als auch directquery. Dies ermöglicht es dem Power BI-Dienst, den effizientesten Modus zu bestimmen, der für eine Abfrage auf Abfrage Basis verwendet werden soll.

![Ein zusammengesetztes Modell ist eine Kombination aus Import-und DQ-Speicher Modi, die auf Tabellenebene konfiguriert sind](media/whitepaper-premium-deployment/composite-model.png)

Zusammengesetzte Modelle sind bestrebt, das Beste aus den Import-und directquery-Modi zu liefern. Bei entsprechender Konfiguration kann eine hohe Abfrageleistung von in-Memory-Modellen mit der Möglichkeit kombiniert werden, Daten aus Datenquellen nahezu in Echtzeit abzurufen.

Daten modelzierer, die zusammengesetzte Modelle entwickeln, konfigurieren wahrscheinlich Dimensions Typen Tabellen im Import-oder Dual-Speicher Modus und Fakten Typen Tabellen im directquery-Modus. Nehmen Sie beispielsweise ein Modell mit einer Tabelle vom Typ "Product Dimension" im Dual-Modus und eine Tabelle "Sales Fact-Type" im directquery-Modus. Die Product-Tabelle kann effizient und schnell aus dem Speicher internen Speicher abgefragt werden, um einen Berichts Slicer zu erzeugen. Die Sales-Tabelle kann dann im directquery-Modus abgefragt werden, der mit der verknüpften Product-Tabelle verknüpft ist. Die zweite Abfrage kann die Generierung einer einzelnen effizienten nativen Abfrage ermöglichen, um die Tabellen "Product" und "Sales" zu verknüpfen und die slicerwerte zu filtern.

Im Allgemeinen können die vor-und Nachteile, die jedem Modell Modus zugeordnet sind, für den Tabellen Speicher Modus in zusammengesetzten Modellen gelten.

Weitere Informationen finden Sie im Dokument verwenden von zusammen [gesetzten Modellen in Power BI Desktop](desktop-composite-models.md) .

### <a name="licensing"></a>Lizenzierung

Power BI verfügt über drei Lizenzen:

- Power BI Free
- Power BI Pro
- Power BI Premium

Mit der **Power BI Free** -Lizenz kann eine Person sich beim Power BI-Dienst anmelden und in Ihrem persönlichen Arbeitsbereich arbeiten, indem Modelle und Berichte veröffentlicht werden. Es ist wichtig zu wissen, dass es nicht möglich ist, Power BI Inhalt mithilfe dieser Lizenzfrei zugeben. Diese Lizenz ist, wie der Name vermuten lässt, kostenlos.

Mit der **Power BI pro** -Lizenz kann eine Person Arbeitsbereiche erstellen und zusammenarbeiten sowie Power BI Inhalt freigeben und verteilen. Sie können auch die Aktualisierung für Ihre Datasets so konfigurieren, dass Daten automatisch aktuell gehalten werden, einschließlich aus lokalen Datenquellen. Darüber hinaus können Sie überwachen und Steuern, wie auf Daten zugegriffen und welche verwendet werden. Diese Lizenz ist erforderlich, um freigegebenen Inhalt von anderen zu empfangen, es sei denn, der Benutzer ist einer Power BI Premium dedizierten Kapazität zugeordnet.

Die **Power BI Premium** -Lizenz ist eine Lizenz auf Mandanten Ebene, die im Abschnitt [Einführung Power BI Premium](#introducing-power-bi-premium) erläutert wird.

Weitere Informationen zur Power BI Lizenzierung finden Sie auf der Seite [Power BI Preise](https://powerbi.microsoft.com/pricing/) .

## <a name="introducing-power-bi-premium"></a>Einführung in Power BI Premium

Power BI Premium bietet eine einheitliche Self-Service-und Enterprise-BI-Plattform mit Skalierbarkeit, zuverlässiger Leistung und vorhersagbaren Kosten. Dies wird in erster Linie durch Bereitstellen dedizierter Ressourcen zum Ausführen der Power BI-Dienst für Ihre Organisation erreicht.

Außerdem bietet Power BI Premium viele Enterprise-Features:

- Kosteneffektive Inhalts Verteilung, die die Freigabe von Power BI Inhalt für unbegrenzte Power BI kostenlose Benutzer, einschließlich externer Benutzer, ermöglicht
- Unterstützung für größere datasetgrößen \[[8](#endnote-08)\]
- Höhere Aktualisierungs Raten von Daten Flüssen und Datasets (bis zu 48-mal pro Tag)
- Inkrementelle Aktualisierung von Daten Flüssen und Datasets
- Verknüpfte Datenfluss Entitäten und parallele Ausführung von Transformationen
- Paginierte Berichte
- Power BI-Berichtsserver für die lokale Berichterstellung
- Möglichkeit zum Einbetten von Inhalten in apps im Namen von App-Benutzern (PAS)

Viele dieser Features können genutzt werden, um effiziente und skalierbare Enterprise-Lösungen bereitzustellen, die im Abschnitt [Optimieren von Premium-Kapazitäten](#optimizing-premium-capacities) beschrieben werden.

### <a name="subscriptions-and-licensing"></a>Abonnements und Lizenzierung

Power BI Premium ist ein Office 365-Abonnement auf Mandantenebene, das in zwei SKU-Familien (Stock Keeping Unit) erhältlich ist:

- **EM** SKUs (EM1-EM3) zum Einbetten, erfordert eine jährliche Verpflichtung, monatlich abgerechnet
- **P** -SKUs (P1-P3) für Einbettungs-und Unternehmens Features, die eine monatliche oder jährliche Verpflichtung erfordern, monatlich abgerechnet werden und eine Lizenz zur Installation von Power BI-Berichtsserver lokal enthalten.

Ein alternativer Ansatz ist das erwerben eines Azure Power BI Embedded-Abonnements, das über eine einzige SKU-Familie verfügt: **eine** SKUs (a1-a6) zum Einbetten und zum Zweck der Kapazitätsprüfung.

Alle SKUs stellen v-Kerne zur Verfügung, um Kapazitäten \[[9](#endnote-09)\]zu erstellen, aber die EM-SKUs sind für kleinere Einbettungen eingeschränkt. Während der Schwerpunkt dieses Whitepaper auf den P-SKUs liegt, ist der Großteil der erörterten Informationen auch für die SKUs von Bedeutung.

Im Gegensatz zu den Premium-Abonnement-SKUs, erfordern Azure-SKUs keine zeitliche Verpflichtung und werden stundenweise abgerechnet. Sie bieten uneingeschränkte Elastizität, die zentrales Hochskalieren, Herunterskalieren, Anhalten, Fortsetzen und Löschen ermöglicht.

Azure-Power BI Embedded ist für dieses Whitepaper größtenteils nicht geeignet, wird aber im Thema Testen von Ansätzen als praktische und wirtschaftliche Option zum Testen und Messen von Workloads behandelt.

Weitere Informationen zu den Azure-SKUs finden Sie in der [Dokumentation zu Azure Power BI Embedded](/azure/power-bi-embedded/).

Power BI-Premium-Abonnements werden von Administratoren im Microsoft 365 Admin Center gekauft. Insbesondere können nur globale Administratoren von Office 365 oder Abrechnungs Administratoren SKUs erwerben.

Nach dem Erwerb erhält der Mandant eine entsprechende Anzahl von v-Kernen, die Kapazitäten zugewiesen werden. Dies wird als **v-Core-Pooling**bezeichnet. Beispielsweise erhält der Mandant durch den Erwerb einer P3-SKU 32 V-Kerne.

Weitere Informationen finden Sie im Dokument [How to purchase Power BI Premium](service-admin-premium-purchase.md) .

### <a name="premium-capacities"></a>Premium-Kapazitäten

Im Gegensatz zu einer gemeinsam genutzten Kapazität, bei der Workloads auf Rechenressourcen ausgeführt werden, die mit anderen Kunden gemeinsam genutzt werden, ist eine **Dedizierte Kapazität** für die ausschließliche Verwendung durch eine Organisation vorgesehen Es ist mit dedizierten Rechenressourcen isoliert, die eine zuverlässige und konsistente Leistung für gehostete Inhalte bereitstellen.

Der Schwerpunkt dieses Whitepaper ist die **Premium-Kapazität** , d. h., Sie ist mit einer der EM-oder P-SKUs verknüpft.

#### <a name="capacity-nodes"></a>Kapazitätsknoten

Wie im Thema Abonnements und Lizenzierung beschrieben, gibt es zwei Power BI Premium SKU-Familien: EM und P. Alle Power BI Premium-SKUs sind als Kapazitäts Knoten verfügbar, wobei jede eine Menge von Ressourcen darstellt, die aus Prozessor, Arbeitsspeicher und Speicher bestehen. Zusätzlich zu den Ressourcen sind für jede SKU Betriebsbeschränkungen hinsichtlich der Anzahl von directquery (DQ)-und Live Connection (LC)-Verbindungen pro Sekunde und der Anzahl paralleler Modell Aktualisierungen fest.

Die Verarbeitung erfolgt mithilfe einer festgelegten Anzahl V-Kerne, die zu gleichen Teilen zwischen Back-End und Front-End aufgeteilt werden.

**Back-End-V-Kerne** sind für die Power BI-Kernfunktionalität zuständig, einschließlich Abfrageverarbeitung, Cacheverwaltung, das Ausführen von R-Diensten, die Verarbeitung natürlicher Sprache (Q&A) und das serverseitige Rendern von Berichten und Bildern. Back-End-v-Kernen wird eine festgelegte Menge an Arbeitsspeicher zugewiesen, die zum Hosten von Modellen verwendet wird, die auch als aktive Datasets bezeichnet werden.

Front **-End-v-Kerne** sind für den Webdienst, die Verwaltung von Dashboards und Berichts Dokumenten, die Zugriffsrechte Verwaltung, die Planung, APIs, Uploads und Downloads und in der Regel für alles, was die Benutzererfahrung betrifft, verantwortlich.

Der Speicher wird auf 100 TB pro Kapazitäts Knoten festgelegt.

In der folgenden Tabelle werden die Ressourcen und die Grenzwerte für die einzelnen Premium-SKU (und die gleichwertig formatierte SKU) beschrieben.

| Kapazitätsknoten | Gesamtzahl an V-Kernen | Back-End-V-Kerne | RAM (GB) | Front-End-V-Kerne | DQ/LC (pro Sekunde) | Modell-Aktualisierungsparallelität |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 3 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Kapazitäts Arbeits Auslastungen

Kapazitätsworkloads sind Dienste, die Benutzern zur Verfügung gestellt werden. Standardmäßig unterstützen Premium-und Azure-Kapazitäten nur eine dataseworkloads, die mit der Ausführung Power BI Abfragen verknüpft sind, die nicht deaktiviert werden können.

Zusätzliche Workloads können für paginierte Berichte, Datenflüsse und Ki aktiviert werden. Jede zusätzliche Arbeitsauslastung erfordert die Konfiguration des maximalen Arbeitsspeichers (als Prozentsatz des gesamten verfügbaren Speichers), der von der Arbeitsauslastung verwendet werden kann.

#### <a name="how-capacities-function"></a>Funktionsweise von Kapazitäts Funktionen

Der Power BI-Dienst versucht, Kapazitäts Ressourcen immer optimal zu nutzen, ohne die Grenzwerte für die Kapazität zu überschreiten.

Kapazitäts Vorgänge werden entweder interaktiv oder im Hintergrund klassifiziert. Zu den interaktiven Vorgängen gehören Renderinganforderungen und das Reagieren auf Benutzerinteraktionen (Filtern, Q&A-Abfragen usw.). Im Allgemeinen ist das Importieren von Modell Abfragen Speicherressourcen intensiv, während die Abfrage von LC/DQ-Modellen CPU-intensiv ist. Zu den Hintergrundvorgängen gehören die Aktualisierung von Datenflüssen und Importmodellen sowie das Cachen von Dashboardabfragen.

Es ist wichtig zu verstehen, dass interaktive Vorgänge immer Vorrang vor Hintergrund Vorgängen sind, um eine bestmögliche Benutzererfahrung zu gewährleisten. Wenn nicht ausreichend Ressourcen vorhanden sind, werden Hintergrundvorgänge einer Warteschlange hinzugefügt, um bei freiwerdenden Ressourcen verarbeitet zu werden. Hintergrund Vorgänge, wie z. b. DataSet-Aktualisierungen und Ki-Funktionen, können während des Power BI-Dienst beendet und einer Warteschlange hinzugefügt werden.

Import Modelle müssen vollständig in den Arbeitsspeicher geladen werden, damit Sie abgefragt oder aktualisiert werden können. Der Power BI-Dienst verwaltet die Speicherauslastung mithilfe von ausgereiften Algorithmen, um die maximale Verwendung des verfügbaren Arbeitsspeichers sicherzustellen und das Überschreiten der Kapazität zu erreichen: zwar ist es möglich, dass eine Kapazität viele importmodelle speichert (bis zu 100 TB pro Premium-Kapazität), Wenn der kombinierte Datenträger Speicher den unterstützten Speicher überschreitet (und zusätzlicher Arbeitsspeicher zum Abfragen und aktualisieren erforderlich ist), können Sie nicht alle gleichzeitig in den Arbeitsspeicher geladen werden.

Import Modelle werden aus diesem Grund entsprechend der Verwendung in geladen und aus dem Arbeitsspeicher entfernt. Ein Import Modell wird geladen, wenn es abgefragt wird (interaktiver Vorgang), noch nicht im Arbeitsspeicher oder wenn es aktualisiert werden soll (Hintergrund Vorgang).

Das Entfernen eines Modells aus dem Arbeitsspeicher wird als Entfernungs Vorgang bezeichnet und ist ein **Vorgang, der** Power BI je nach Größe der Modelle schnell ausführen kann. Wenn die Kapazität keinen Engpass beim Arbeitsspeicher erlebt, werden Modelle einfach in den Arbeitsspeicher geladen und verbleiben dort. \[[10](#endnote-10)\] Wenn jedoch nicht genügend Arbeitsspeicher zum Laden eines Modells verfügbar ist, muss der Power BI-Dienst zuerst Arbeitsspeicher freigeben. Dadurch wird Arbeitsspeicher freigegeben, indem Modelle erkannt werden, die durch das Suchen von Modellen, die in den letzten drei Minuten nicht verwendet wurden, \[[11](#endnote-11)\]und deren Überprüfung nicht mehr verwendet werden. Wenn keine inaktiven Modelle zum Entfernen vorhanden sind, versucht der Power BI-Dienst, Modelle zu entfernen, die für Hintergrundoperationen geladen wurden. Dies kann die Entfernung von hintergrundworkloads wie der AI-Arbeitsauslastung einschließen. Eine letzte Möglichkeit ist, nach 30 Sekunden fehlgeschlagener Versuche \[[11](#endnote-11)\], den interaktiven Vorgang fehlschlagen zu lassen. In diesem Fall wird der Berichts Benutzer ordnungsgemäß benachrichtigt, wenn ein Fehler aufgetreten ist. versuchen Sie es in Kürze erneut.

Es ist wichtig zu betonen, dass das Entfernen von Datasets ein normales und erwartetes Verhalten ist. Es zielt darauf ab, die Speicherauslastung durch Laden und Entladen von Modellen zu maximieren, deren kombinierte Größe den verfügbaren Arbeitsspeicher überschreiten kann. Dies ist beabsichtigt und für Benutzer des Berichts vollständig transparent. Hohe Entfernungsraten bedeuten nicht zwangsläufig, dass die Kapazität unzureichend mit Ressourcen ausgestattet ist. Dies kann jedoch zu einem Problem werden, wenn die Reaktionsfähigkeit auf Abfragen oder Aktualisierungen aufgrund hoher Entfernungsraten leidet.

Aktualisierungen von Import Modellen sind immer Arbeitsspeicher intensiv, da Modelle in den Arbeitsspeicher geladen werden müssen und für die Verarbeitung zusätzlicher Arbeitsspeicher erforderlich ist. Eine vollständige Aktualisierung kann ungefähr doppelt so viel Arbeitsspeicher in Anspruch nehmen, wie für das Modell erforderlich ist. Dadurch wird sichergestellt, dass das Modell auch dann abgefragt werden kann, wenn es verarbeitet wird (Abfragen werden an das vorhandene Modell gesendet, bis die Aktualisierung abgeschlossen ist und die neuen Modelldaten verfügbar sind). Beachten Sie, dass die inkrementelle Aktualisierung weniger Arbeitsspeicher erfordert und schneller ausgeführt werden kann. Dadurch kann der Druck auf Kapazitäts Ressourcen erheblich reduziert werden. Aktualisierungen von Modellen können außerdem CPU-intensiv sein, insbesondere solche mit komplexen Power Query-Transformationen oder berechneten Tabellen/Spalten, die komplex sind oder auf umfangreichen Tabelle basieren.

Aktualisierungen-ähnliche Abfragen: erfordern, dass das Modell in den Arbeitsspeicher geladen wird. Bei unzureichendem Arbeitsspeicher versucht der Power BI-Dienst, inaktive Modelle zu entfernen, und wenn das nicht möglich ist (weil alle Modelle aktiv sind), wird der Aktualisierungsauftrag in die Warteschlange eingestellt. Aktualisierungen sind in der Regel sehr CPU-intensiv und sogar mehr als Abfragen. Aus diesem Grund bestehen Kapazitätsgrenzen für die Anzahl der gleichzeitigen Aktualisierungen, die auf das 1,5-fache der Anzahl der V-Kerne im Back-End festgelegt ist (aufgerundet). Bei zu vielen gleichzeitigen Aktualisierungen wird eine geplante Aktualisierung in die Warteschlange eingestellt. Wenn diese Situationen eintreten, benötigt die Aktualisierung mehr Zeit bis zum Abschluss. Beachten Sie, dass bei Bedarf-Aktualisierungen (ausgelöst durch eine Benutzer Anforderung oder einen API-Aufruf) dreimal wiederholt werden \[[11](#endnote-11)\], und dann fehlschlagen, wenn noch nicht genügend Ressourcen verfügbar sind.

## <a name="managing-power-bi-premium"></a>Verwalten von Power BI Premium

Das Verwalten von Power BI Premium umfasst das erwerben von Abonnements sowie das Erstellen, verwalten und Überwachen von Premium-Kapazitäten.

### <a name="creating-and-managing-capacities"></a>Erstellen und Verwalten von Kapazitäten

Auf der Seite " **Kapazitäts Einstellungen** " des **Power BI admin** -Portals wird die Anzahl der erworbenen und verfügbaren v-Kerne angezeigt (d. h., Sie werden einer Kapazität zugewiesen), und es werden Premium-Kapazitäten aufgeführt. Auf der Seite können globale Administratoren von Office 365 oder Power BI-Dienst Administratoren Premium-Kapazitäten von verfügbaren v-Kernen erstellen oder vorhandene Premium-Kapazitäten ändern.

Beim Erstellen einer Premium-Kapazität muss der Administrator Folgendes definieren:

- Kapazitäts Name (innerhalb des Mandanten eindeutig)
- Kapazitäts Administrator (en)
- Kapazitätsumfang
- Region für die Daten Residenz \[[12](#endnote-12)\]

Mindestens ein Kapazitätsadministrator muss zugewiesen werden. Als Kapazitätsadministratoren zugewiesene Benutzer können folgende Aktionen ausführen:

- Arbeitsbereiche der Kapazität zuweisen
- Verwalten von Benutzerberechtigungen zum Hinzufügen von zusätzlichen Kapazitäts Administratoren oder Benutzern mit Zuweisungs Berechtigungen (damit Sie Arbeitsbereiche der Kapazität zuweisen können)
- Verwalten von Arbeits Auslastungen, um die maximale Speicherauslastung für paginierte Berichte und Datenfluss Arbeits Auslastungen zu konfigurieren
- Starten Sie die Kapazität neu, um alle Vorgänge zurückzusetzen, wenn die Systemüberlastung \[[13](#endnote-13)\]

Kapazitäts Administratoren können nicht auf Arbeitsbereichs Inhalte zugreifen (es sei denn, Sie haben explizit zugewiesene Arbeitsbereichs Berechtigungen) und haben keinen Zugriff auf alle Power BI Administrator Bereiche (sofern nicht explizit zugewiesen) wie nutzungsmetriken, Überwachungs Protokolle oder Mandanten Einstellungen. Wichtig: Kapazitätsadministratoren sind auch nicht berechtigt, neue Kapazitäten zu erstellen oder vorhandene Kapazitäten zu skalieren. Außerdem werden Sie pro Kapazität zugewiesen, um sicherzustellen, dass Sie nur Kapazitäten anzeigen und verwalten können, denen Sie zugewiesen sind.

Die Kapazitäts Größe muss in einer verfügbaren Liste mit SKU-Optionen ausgewählt werden, die durch die Anzahl der verfügbaren v-Kerne im Pool eingeschränkt wird. Es ist möglich, mehrere Kapazitäten aus dem Pool zu erstellen, die aus einer oder mehreren erworbenen SKUs stammen können. Beispielsweise könnte eine P3-SKU (32 V-Kerne) zum Erstellen von drei Kapazitäten verwendet werden: eine P2 (16 V-Kerne) und zwei P1 (2 x 8 V-Kerne). Verbesserte Leistung und Skalierbarkeit können durch die Erstellung von kleineren Kapazitäten erreicht werden. dieses Thema wird im Abschnitt [Optimieren von Premium-Kapazitäten](#optimizing-premium-capacities) erläutert. Die folgende Abbildung zeigt ein Beispiel für das Setup für die fiktive Organisation "Unternehmen", bestehend aus fünf Premium-Kapazitäten (3 x P1 und 2 x P3), die jeweils Arbeitsbereiche enthalten, und mehreren Arbeitsbereichen in gemeinsam genutzter Kapazität.

![Ein Beispielsetup für die fiktive Organisation Contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Eine Premium-Kapazität kann einer anderen Region als der Start Region des Power BI Mandanten zugewiesen werden. Dadurch wird die administrative Kontrolle über die Rechenzentren (innerhalb definierter geografischer Regionen) Power BI Inhalts bereitgestellt. \[[12](#endnote-12)\]

Power BI-Dienstadministratoren und globale Office 365-Administratoren können Premium-Kapazitäten ändern. Sie haben insbesondere folgende Möglichkeiten:

- Ändern Sie die Kapazitäts Größe, um Ressourcen zentral hoch-oder Herunterskalieren. Es ist jedoch nicht möglich, ein Downgrade für eine P-SKU auf eine EM-SKU durchzuführen oder umgekehrt.
- Kapazitäts Administratoren hinzufügen oder entfernen
- Hinzufügen oder Entfernen von Benutzern mit Zuweisungs Berechtigungen
- Hinzufügen oder Entfernen zusätzlicher Workloads
- Bereiche ändern

Zuweisungsberechtigungen sind erforderlich, um einer bestimmten Premium-Kapazität einen Arbeitsbereich zuzuweisen. Die Berechtigungen können für die gesamte Organisation, bestimmte Benutzer oder Gruppen gewährt werden.

Premium-Kapazitäten unterstützen standardmäßig Workloads für die Ausführung von Power BI-Abfragen. Außerdem werden drei zusätzliche Workloads unterstützt: **paginierte Berichte**, **Dataflows**und **Ki**. Jede Workload erfordert das Konfigurieren des maximalen Arbeitsspeichers (als Prozentsatz des gesamten verfügbaren Arbeitsspeichers) für die Verwendung durch die Workload. Es ist wichtig zu verstehen, dass sich das Erhöhen der maximalen Speicher Belegungen auf die Anzahl der aktiven Modelle, die gehostet werden können, und den Durchsatz von Aktualisierungen auswirkt.

Der Arbeitsspeicher wird Dataflows dynamisch zugeordnet, ist paginierten Berichten jedoch statisch zugeordnet. Der Grund für die statische Zuordnung des maximalen Arbeitsspeichers ist, dass paginierte Berichte innerhalb eines gesicherten, eigenständigen Raums der Kapazität ausgeführt werden können. Beim Festlegen des Arbeitsspeichers für paginierte Berichte ist Vorsicht geboten, da der verfügbare Arbeitsspeicher für das Laden von Modellen reduziert wird.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Paginierte Berichte | N/V | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 % | 20 % Standard, mindestens 2,5 % |
| Dataflows | 20 % Standard, mindestens 8 %  | 20 % Standard, mindestens 4 %  | 20 % Standard, mindestens 2 % | 20 % Standard, mindestens 1 %  |
| KI | N/V | 20 % Standard; mindestens 20 %  | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 %  |
| | | | | |

Das Löschen einer Premium-Kapazität ist möglich und führt nicht zum Löschen der Arbeitsbereiche und Inhalte. Stattdessen werden alle zugewiesenen Arbeitsbereiche in freigegebene Kapazität verschoben. Wenn die Premium-Kapazität in einer anderen Region erstellt wurde, wird der Arbeitsbereich in die freigegebene Kapazität der Start Region verschoben.

### <a name="assigning-workspaces-to-capacities"></a>Zuweisen von Arbeitsbereichen zu Kapazitäten

Arbeitsbereiche können einer Premium-Kapazität im **Power BI admin**-**Portal** oder-für einen Arbeitsbereich im **Arbeitsbereich** zugewiesen werden.

Kapazitäts Administratoren und globale Administratoren von Office 365 oder Power BI-Dienst Administratoren können Arbeitsbereiche im **Power BI Verwaltungs**  **Portal**Massen zuweisen. Zuweisungen im Massenvorgang können auf Folgendes angewendet werden:

- **Arbeitsbereiche nach Benutzern** : alle Arbeitsbereiche, die sich im Besitz dieser Benutzer befinden, einschließlich persönlicher Arbeitsbereiche, werden der Premium-Kapazität zugewiesen. Dies schließt die erneute Zuweisung von Arbeitsbereichen ein, wenn Sie bereits einer anderen Premium-Kapazität zugewiesen sind. Außerdem werden den Benutzern auch Berechtigungen zur Zuweisung von Arbeitsbereichen zugewiesen.

- **Bestimmte Arbeitsbereiche**
- **Die Arbeitsbereiche der gesamten Organisation** : alle Arbeitsbereiche, einschließlich persönlicher Arbeitsbereiche, werden der Premium-Kapazität zugewiesen. Außerdem werden allen aktuellen und zukünftigen Benutzern Arbeitsbereichs Zuweisungs Berechtigungen zugewiesen. \[[14](#endnote-14)\]

Ein Arbeitsbereich kann einer Premium-Kapazität im Bereich **Arbeitsbereich** hinzugefügt werden, sofern der Benutzer ein Arbeitsbereichsadministrator ist und über Zuweisungsberechtigungen verfügt.

![Verwenden des Bereichs „Arbeitsbereich“ zum Zuweisen eines Arbeitsbereichs zu einer Premium-Kapazität](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Arbeitsbereichsadministratoren können einen Arbeitsbereich aus einer Kapazität entfernen (in gemeinsam genutzte Kapazität), ohne dass eine Zuweisungsberechtigung erforderlich ist. Durch das Entfernen von Arbeitsbereichen aus dedizierten Kapazitäten wird der Arbeitsbereich tatsächlich in gemeinsam genutzte Kapazität verlagert. Beachten Sie, dass das Entfernen eines Arbeitsbereichs aus einer Premium-Kapazität negative Konsequenzen haben kann, sodass beispielsweise gemeinsam genutzte Inhalte nicht mehr für Benutzer mit Power BI Free-Lizenz verfügbar sind, oder das Aussetzen geplanter Aktualisierung, wenn die durch gemeinsam genutzte Kapazitäten unterstützten Ressourcen überschritten werden.

Im Power BI-Dienst ist ein Arbeitsbereich, der einer Premium-Kapazität zugewiesen ist, leicht an dem Diamantsymbol zu erkennen, mit dem der Name des Arbeitsbereichs versehen ist.

![Identifizieren eines Arbeitsbereichs, der einer Premium-Kapazität zugewiesen ist](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Überwachen von Kapazitäten

Durch Überwachen von Premium-Kapazitäten erhalten Administratoren Informationen über die Leistung ihrer Kapazitäten. Kapazitäten können mithilfe der [Power BI Premium kapazitätsmetriken-App](service-admin-premium-monitor-capacity.md) oder des [Power BI admin-Portals](service-admin-premium-monitor-portal.md)überwacht werden.

#### <a name="interpreting-metrics"></a>Interpretieren von Metriken

Metriken sollten überwacht werden, um ein grundlegendes Verständnis von Ressourcenverwendung und Workloadaktivität zu gewinnen. Wenn bei der Kapazität Leistungsschwächen auftreten, müssen Sie wissen, welche Metriken Sie überwachen und welche Konsequenzen Sie ziehen können.

Im Idealfall sollten Abfragen innerhalb einer Sekunde durchgeführt werden, um Berichtsbenutzern Ergebnisse zu liefern, auf deren Basis sie optimal reagieren können, und einen höheren Abfragedurchsatz zu ermöglichen. Es ist in der Regel von geringerer Bedeutung, wenn die Ausführung von Hintergrundprozessen einschließlich Aktualisierungen länger dauert.

Im Allgemeinen können langsame Berichte ein Hinweis auf eine Kapazitätsüberlastung sein. Wenn Berichte nicht geladen werden können, ist dies ein Hinweis auf eine Kapazitätsüberlastung. In beiden Situationen könnte die Ursache auf zahlreiche Faktoren zurückzuführen sein, darunter:

- **Fehler bei Abfragen** weisen sicherlich auf unzureichenden Arbeitsspeicher hin, und dass ein Modell nicht in den Arbeitsspeicher geladen werden konnte. Der Power BI-Dienst versucht 30 Sekunden lang, ein Modell zu laden, bevor ein Fehler gemeldet wird.

- **Übermäßig lange Wartezeiten bei Abfragen** können aus verschiedenen Gründen auftreten:
  - Der Power BI-Dienst zuerst das Modell (en) entfernen und dann das auf die Abfrage abgefragte Modell laden (denken Sie daran, dass höhere Entfernungs Raten für Datasets allein keine Anzeichen für Kapazitäts Belastung sind, es sei denn, es werden lange Abfrage Wartezeiten begleitet, die eine Speicher Überlastung angeben).
  - Ladezeiten von Modellen (insbesondere das warten auf das Laden eines großen Modells in den Speicher)
  - Abfragen mit langer Ausführungszeit
  - Zu viele lc\dq-Verbindungen (überschreiten der Kapazitäts Limits)
  - CPU-Sättigung
  - Komplexe Berichtsentwürfe mit einer übermäßigen Anzahl von visuellen Elementen auf einer Seite (denken Sie daran, dass jede Visualisierung eine Abfrage ist)
- **Lange Abfragezeiten** können darauf hindeuten, dass Modellentwürfe nicht optimiert sind, insbesondere wenn mehrere Datasets in einer Kapazität aktiv sind und nur ein Dataset lange Abfragezeiten erzeugt. Dies deutet darauf hin, dass die Kapazitätsressourcen ausreichen und das fragliche Dataset suboptimal oder einfach langsam ist. Abfragen mit langer Ausführungszeit können problematisch sein, da sie den Zugriff auf Ressourcen blockieren können, die von anderen Prozessen benötigt werden.
- **Lange Aktualisierungs Wartezeiten oder AI-Anrufe** weisen auf unzureichenden Arbeitsspeicher hin, weil viele aktive Modelle Arbeitsspeicher belegen, oder dass eine problematische Aktualisierung andere Aktualisierungen blockiert (überschreitet parallele Aktualisierungs Limits).

Eine ausführlichere Erläuterung der Verwendung der Metriken finden Sie im Abschnitt Optimieren von [Premium-Kapazitäten](#optimizing-premium-capacities) .

## <a name="optimizing-premium-capacities"></a>Optimieren von Premium-Kapazitäten

Wenn Leistungsprobleme bei der Premium-Kapazität auftreten, besteht der erste Ansatz darin, bereits bereitgestellte Lösungen zu optimieren oder zu optimieren, um akzeptable Antwortzeiten wiederherzustellen. Die über schreibende Begründung besteht darin, den Erwerb zusätzlicher Premium-Kapazität zu vermeiden, es sei denn, Sie

Wenn zusätzliche Premium-Kapazität erforderlich ist, gibt es zwei Optionen, die später in diesem Abschnitt erläutert werden:

- Zentrales hochskalieren der Premium-Kapazität
- Hinzufügen neuer Premium-Kapazität

Schließlich wird in diesem Abschnitt der Test Ansatz und die Premium-Kapazitäts Größe abgeschlossen.

### <a name="general-best-practices"></a>Allgemeine bewährte Methoden

Beim Erreichen der optimalen Nutzung und Leistung gibt es einige bewährte Methoden, die im Allgemeinen als allgemeine Empfehlungen angesehen werden können. Dazu gehören:

- Verwenden von Arbeitsbereichen anstelle persönlicher Arbeitsbereiche
- Trennen von geschäftskritischen und Self-Service-BI (ssbi) in unterschiedliche Kapazitäten

  ![Trennen von unternehmenskritischer und Self-Service-BI in verschiedene Kapazitäten](media/whitepaper-premium-deployment/separate-capacities.png)

- Wenn Inhalte nur für Power BI pro Benutzer freigegeben werden, ist es möglicherweise nicht erforderlich, den Inhalt in einer dedizierten Kapazität zu speichern.
- Verwenden Sie dedizierte Kapazitäten, wenn Sie eine bestimmte Aktualisierungszeit erreichen möchten oder wenn bestimmte Features erforderlich sind, z. b. große Datasets oder paginierte Berichte.

### <a name="addressing-common-questions"></a>Umgang mit häufig gestellten Fragen

Die Optimierung von Power BI Premium Bereitstellungen ist ein komplexes Thema, das ein Verständnis der workloadanforderungen, der verfügbaren Ressourcen und ihrer effektiven Verwendung umfasst.

In diesem Thema werden sieben häufige Supportfragen behandelt, die mögliche Probleme und Erläuterungen beschrieben werden, sowie Informationen dazu, wie Sie identifiziert und aufgelöst werden.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Warum ist die Kapazität langsam, und was kann ich tun?

Es gibt viele Ursachen, die zu einer langsamen Premium-Kapazität beitragen können. Diese Frage erfordert weitere Informationen, um zu verstehen, was mit langsam gemeint ist. Werden Berichte langsam geladen? Oder werden Sie gar nicht geladen? Werden visuelle Elemente in Berichten langsam geladen oder aktualisiert, wenn Benutzer mit dem Bericht interagieren? Dauert das Fertigstellen von Aktualisierungen länger als erwartet oder bereits.

Nachdem Sie die Ursache verstanden haben, können Sie mit der Untersuchung beginnen. Die Antworten auf die folgenden sechs Fragen helfen Ihnen bei spezifischeren Problemen.

#### <a name="what-content-is-using-up-my-capacity"></a>Welche Inhalte verbrauchen meine Kapazität?

Mithilfe der App **Power BI Premium-Kapazitätsmetriken** können Sie nach Kapazität filtern und Leistungsmetriken für Arbeitsbereichsinhalte überprüfen. Es ist möglich, die Leistungsmetriken und die Ressourcennutzung in den letzten sieben Tagen für alle in einer Premium-Kapazität gespeicherten Inhalte stündlich zu überprüfen. Dies ist häufig der erste Schritt bei der Problembehandlung eines allgemeinen Problems in Bezug auf die Premium-Kapazitäts Leistung.

Zu überwachende Schlüsselmetriken sind:

- Durchschnittliche CPU-und hohe Auslastung
- Durchschnittlicher Arbeitsspeicher und hohe Auslastung und Arbeitsspeicher Auslastung für bestimmte Datasets, Datenflüsse und paginierte Berichte
- Aktive Datasets geladen in den Arbeitsspeicher
- Durchschnittliche und maximale Abfrage Dauer
- Durchschnittliche Abfrage Wartezeit
- Durchschnittliches DataSet und Datenfluss Aktualisierungszeiten
- Durchschnittliche Ki-Anrufzeiten und Wartezeiten

Außerdem zeigt der aktive Arbeitsspeicher in der APP für die Power BI Premium kapazitätsmetriken die Gesamtmenge des Arbeitsspeichers an, die einem Bericht zugeordnet ist, der nicht entfernt werden kann, da er in den letzten drei Minuten verwendet wird. Ein hoher Anstieg der Aktualisierungswartezeit kann mit einem großen und/oder aktiven Dataset in Zusammenhang stehen.

Im Diagramm "Top 5 by Average Duration" werden die fünf wichtigsten Datasets, paginierten Berichte, Datenflüsse und Ki-Aufrufe hervorgehoben, die Kapazitäts Ressourcen belegen. Der Inhalt in den fünf wichtigsten Listen ist Kandidaten für die Untersuchung und mögliche Optimierung.

#### <a name="why-are-reports-slow"></a>Warum sind Berichte langsam?

In den folgenden Tabellen sind mögliche Probleme und Möglichkeiten aufgeführt, diese zu erkennen und zu behandeln.

##### <a name="insufficient-capacity-resources"></a>Unzureichende Kapazitätsressourcen

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Hoher gesamter aktiver Arbeitsspeicher (das Modell kann nicht entfernt werden, weil es in den letzten drei Minuten verwendet wird)<br><br> Mehrere hohe Spitzen in den Abfrage Wartezeiten<br><br> Mehrere hohe Spitzen in den Aktualisierungs Wartezeiten | Überwachen von arbeitsspeichermetriken \[[18](#endnote-18)\]und Entfernungs Anzahl \[[19](#endnote-19)\] | Verringern der Modell Größe oder konvertieren in den directquery-Modus: Weitere Informationen finden Sie im Thema [Optimieren von Modellen](#optimizing-models) in diesem Abschnitt.<br><br> Zentrales hochskalieren der Kapazität<br><br> Zuweisen des Inhalts zu einer anderen Kapazität |

##### <a name="inefficient-report-designs"></a>Ineffiziente Berichtsentwürfe

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Berichts Seiten enthalten zahlreiche visuelle Elemente (interaktive Filterung kann mindestens eine Abfrage pro Visualisierung auslöst)<br><br> Visuelle Elemente rufen mehr Daten als notwendig ab | Berichtsentwürfe überprüfen<br><br> Überprüfen der Berichts Benutzer, um zu verstehen, wie Sie mit den Berichten interagieren<br><br> Überwachen von datasetabfragemetriken \[\] [20](#endnote-20) | Umgestalten von Berichten mit weniger visuellen Elementen pro Seite |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Das DataSet ist langsam (vor allem, wenn Berichte bereits erfolgreich ausgeführt wurden).

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Zunehmend große Mengen von Import Daten<br><br> Komplexe oder ineffiziente Berechnungs Logik, einschließlich RLS-Rollen<br><br> Modell nicht vollständig optimiert<br><br> (DQ/LC) Gatewaylatenz<br><br> Langsame Antwortzeiten der DQ-Quell Abfrage | Überprüfen von Modell Entwürfen<br><br> Überwachen von Gateway-Leistungsindikatoren | Weitere Informationen finden Sie im Thema [Optimierungsmodelle](#optimizing-models) in diesem Abschnitt. |

##### <a name="high-concurrent-report-usage"></a>Hohe gleichzeitige Berichtsnutzung

| Mögliche Erklärungen | Erkennung | Behebung |
| --- | --- | --- |
| Hohe Abfrage Wartezeiten<br><br> CPU-Sättigung<br><br> DQ/LC-Verbindungs Limits überschritten | Überwachen der CPU-Auslastung \[[21](#endnote-21)\], Abfrage Wartezeiten und DQ/LC-Auslastung \[[22](#endnote-22)\] Metriken + Abfrage Dauer – Wenn die Fluktuation auf Parallelitäts Probleme hindeuten kann | Zentrales hochskalieren der Kapazität oder Zuweisen des Inhalts zu einer anderen Kapazität<br><br> Umgestalten von Berichten mit weniger visuellen Elementen pro Seite |

#### <a name="why-are-reports-not-loading"></a>Warum werden Berichte nicht geladen?

Wenn Berichte nicht geladen werden können, handelt es sich um ein ungünstigste Szenario und ein sicheres Vorzeichen, dass die Kapazität nicht über genügend Arbeitsspeicher verfügt. Dies kann vorkommen, wenn alle geladenen Modelle aktiv abgefragt werden und daher nicht entfernt werden können und Aktualisierungsvorgänge angehalten oder verzögert wurden. Der Power BI-Dienst versucht 30 Sekunden lang, das Dataset zu laden, und der Benutzer wird ordnungsgemäß über den Fehler informiert mit dem Vorschlag, es in Kürze erneut zu versuchen.

Derzeit gibt es keine Metrik, die auf Fehler beim Laden von Berichten überwacht werden kann. Sie können das Potenzial für dieses Problem erkennen, indem Sie den Systemspeicher überwachen, insbesondere die höchste Auslastung und die Zeit der höchsten Auslastung. Viele entfernte Datasets und eine lange durchschnittliche Wartezeit für Datasetaktualisierungen können darauf hindeuten, dass dieses Problem auftritt.

Wenn dies nur sehr selten vorkommt, wird es möglicherweise nicht als vorrangiges Problem betrachtet. Berichtsbenutzer werden darüber informiert, dass der Dienst ausgelastet ist und sie es nach kurzer Zeit noch einmal versuchen sollen. Wenn dies zu häufig vorkommt, kann das Problem durch zentrales Hochskalieren der Premium-Kapazität oder Zuweisen des Inhalts zu einer anderen Kapazität behoben werden.

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Abfragefehler** überwachen, um festzustellen, wann dies geschieht. Sie können auch die Kapazität neu starten und bei Überlastung des Systems alle Vorgänge zurücksetzen.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Warum werden Aktualisierungen nicht nach Zeitplan gestartet?

Startzeiten für geplante Aktualisierungen sind nicht garantiert. Für den Power BI-Dienst haben interaktive Vorgänge immer höhere Priorität als Hintergrundvorgänge. Die Aktualisierung ist ein Hintergrundvorgang, der stattfinden kann, wenn zwei Bedingungen erfüllt sind:

- Es ist genügend Arbeitsspeicher vorhanden.
- Die Anzahl der unterstützten gleichzeitigen Aktualisierungen für die Premium-Kapazität wird nicht überschritten.

Wenn die Bedingungen nicht erfüllt sind, wird die Aktualisierung in die Warteschlange gestellt, bis die Bedingungen günstig sind.

Beachten Sie bei einer vollständigen Aktualisierung, dass mindestens das Doppelte der aktuellen Arbeitsspeichergröße des Datasets erforderlich ist. Ist nicht genügend Arbeitsspeicher verfügbar, kann die Aktualisierung erst beginnen, wenn durch das Entfernen des Modells Arbeitsspeicher freigegeben wird. Dies bedeutet Verzögerungen, bis ein oder mehrere Datasets inaktiv werden und entfernt werden können.

Die unterstützte maximale Anzahl gleichzeitiger Aktualisierungen ist auf das 1,5-fache der Back-End-V-Kerne (aufgerundet) festgelegt.

Eine geplante Aktualisierung schlägt fehl, wenn sie nicht vor dem Beginn der nächsten geplanten Aktualisierung begonnen werden kann. Bei einer bedarfsgesteuerten Aktualisierung, die manuell über die Benutzeroberfläche ausgelöst wird, werden bis zu drei Ausführungsversuche unternommen, bevor sie fehlschlägt.

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Durchschnittliche Aktualisierungswartezeit (Minuten)** überwachen, um die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start des Vorgangs zu ermitteln.

In der Regel hat es keine administrative Priorität, pünktliche Aktualisierungen der Daten zu erwirken, doch stellen Sie sicher, dass genügend Arbeitsspeicher verfügbar ist. Dies kann das Isolieren von Datasets in Kapazitäten mit bekanntermaßen ausreichenden Ressourcen umfassen. Es ist auch möglich, dass Administratoren sich mit DataSet-Besitzern koordinieren, um geplante Daten Aktualisierungszeiten zu verkürzen oder zu reduzieren, um Konflikte zu minimieren. Beachten Sie, dass es nicht möglich ist, dass ein Administrator die Aktualisierungs Warteschlange anzeigen oder datasetzeitpläne abrufen kann.

#### <a name="why-are-refreshes-slow"></a>Warum sind Aktualisierungen langsam?

Aktualisierungen können langsam sein – oder als langsam empfunden werden (wie bei der vorherigen häufig gestellten Frage angesprochen).

Wenn die Aktualisierung tatsächlich langsam ist, kann dies mehrere Ursachen haben:

- Unzureichende CPU (die Aktualisierung kann sehr CPU-intensiv sein)
- Nicht genügend Arbeitsspeicher, was zu einer Aktualisierung führt (die Aktualisierung muss gestartet werden, wenn die Bedingungen für die Empfehlungs Ausführung günstig sind).
- Gründe für nicht Kapazität, einschließlich der Reaktionsfähigkeit von Datenquellen System, Netzwerk Latenz, ungültige Berechtigungen oder gatewaydurchsatz
- Datenvolumen: ein guter Grund für die Konfiguration der inkrementellen Aktualisierung, wie unten erläutert.

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Durchschnittliche Aktualisierungsdauer (Minuten)** überwachen, um einen Benchmark für den Vergleich im zeitlichen Verlauf zu ermitteln, und die Metrik **Durchschnittliche Aktualisierungswartezeit (Minuten)** überwachen, um die durchschnittliche Verzögerung zwischen der geplanten Zeit und dem Start des Vorgangs zu ermitteln.

Die inkrementelle Aktualisierung kann die Dauer der Datenaktualisierung erheblich verkürzen, insbesondere bei großen Modelltabellen. Die inkrementelle Aktualisierung bietet vier Vorteile:

- Aktualisierungen **sind schneller** : nur eine Teilmenge einer Tabelle muss geladen werden, die CPU-und Speicherauslastung wird reduziert, und die Parallelität kann bei der Aktualisierung mehrerer Partitionen höher sein.
- Aktualisierungen **erfolgen nur bei Bedarf** : Richtlinien für die inkrementelle Aktualisierung können so konfiguriert werden, dass Sie nur geladen werden, wenn Daten
- Aktualisierungen **sind zuverlässiger** : kürzere Verbindungen mit flüchtigen Datenquellen Systemen sind weniger anfällig für die Verbindungs Trennung
- **Modelle bleiben bestehen** : Richtlinien für die inkrementelle Aktualisierung können so konfiguriert werden, dass Sie den Verlauf nach einem gleitenden Zeitfenster

Weitere Informationen finden Sie unter [inkrementelle Aktualisierung in Power BI Premium](service-premium-incremental-refresh.md) Dokument.

#### <a name="why-are-data-refreshes-not-completing"></a>Warum werden Datenaktualisierungen nicht abgeschlossen?

Wenn die Datenaktualisierung beginnt, aber nicht abgeschlossen wird, kann dies mehrere Ursachen haben:

- Nicht genügend Arbeitsspeicher, auch wenn nur ein Modell in der Premium-Kapazität vorhanden ist, d. h. die Modell Größe ist sehr groß.
- Gründe für nicht Kapazität, einschließlich Trennung von Datenquellen System, ungültige Berechtigungen oder Gatewayfehler

Kapazitätsadministratoren (und Power BI-Dienstadministratoren) können die Metrik **Aktualisierungsfehler aufgrund von Arbeitsspeichermangel** überwachen.

#### <a name="why-are-ai-calls-failing"></a>Warum treten bei Ki-aufrufen Fehler auf?

Ki-Aufrufe können aus mehreren Gründen fehlschlagen. Der zum Starten der Ki-Arbeitsauslastung erforderliche Mindestarbeitsspeicher beträgt 5 GB, aber dies ist für einige Eingabe Datasets möglicherweise nicht ausreichend. Beispielsweise erfordert das automatisierte Machine Learning-Modell Training mindestens zweimal und manchmal mehrmals die Größe des Eingabe Datasets. Außerdem wird ein AI-Befehl beendet, wenn er länger als zwei Stunden dauert. Bei automatisierten Machine Learning-Modell Trainings aufrufen, die nicht innerhalb von zwei Stunden ausgeführt werden, wird das beste Modell in diesen zwei Stunden zurückgegeben.  Ki-Aufrufe können auch durch interaktive Anforderungen unterbrochen werden, die Vorrang haben.

Administratoren sollten AI-Wartezeiten auf Anzeichen anderer Anforderungen überwachen, die Vorrang haben. Administratoren können auch sicherstellen, dass genügend Arbeitsspeicher für die AI-Arbeitsauslastung in Bezug auf die Größe der Eingabedaten verfügbar ist. Dies kann dazu führen, dass AI-Workloads auf Kapazitäten isoliert werden, die bekanntermaßen über ausreichende Ressourcen verfügen. Es ist auch möglich, dass Administratoren sich mit Datenfluss Besitzern koordinieren, um Datenfluss Aktualisierungszeiten zu verkürzen oder zu reduzieren, um Konflikte zu minimieren. Beachten Sie, dass ein Administrator die AI-Ansichts Warteschlange nicht anzeigen kann.

### <a name="optimizing-models"></a>Optimieren von Modellen

Ein optimaler Modellentwurf ist entscheidend für die Bereitstellung einer effizienten und skalierbaren Lösung. Es geht jedoch über den Rahmen dieses Whitepapers hinaus, um eine umfassende Erörterung zu bieten. Stattdessen werden in diesem Abschnitt wichtige Bereiche genannt, die beim Optimieren von Modellen zu berücksichtigen sind.

#### <a name="optimizing-power-bi-hosted-models"></a>Optimieren von Power BI gehosteten Modellen

Die Optimierung von Modellen, die in einer Premium-Kapazität gehostet werden, kann auf den Datenquellen und Modell Schichten erreicht werden.

Sehen Sie sich die Optimierungsmöglichkeiten für ein Importmodell an:

![Optimierungsmöglichkeiten für ein Importmodell](media/whitepaper-premium-deployment/import-model-optimizations.png)

Auf der Datenquellen Ebene:

- Relationale Datenquellen können optimiert werden, um die schnellste Aktualisierung sicherzustellen, indem Sie Daten vorab integrieren, geeignete Indizes anwenden, Tabellen Partitionen definieren, die sich auf inkrementelle Aktualisierungs Zeiträume ausrichten, und Berechnungen materialisieren (anstelle von berechneten Modell Tabellen und-Spalten) oder Hinzufügen von Berechnungs Logik zu Sichten
- Nicht relationale Datenquellen können in relationale Speicher integriert werden.
- Stellen Sie sicher, dass Gateways über ausreichende Ressourcen verfügen, vorzugsweise auf dedizierten Computern, mit ausreichender Netzwerkbandbreite und in unmittelbarer Nähe der Datenquellen.

Auf Modellebene:

- Mit Power Query-Abfrageentwürfen können komplexe Transformationen minimiert oder entfernt werden, insbesondere solche, bei denen verschiedene Datenquellen zusammengeführt werden (Data Warehouses können dies während ihrer ETL-Phase (Extract-Transform-Load) erreichen). Dadurch wird sichergestellt, dass die entsprechenden Datenschutz Ebenen der Datenquelle festgelegt werden. Dies kann dazu führen, dass Power BI keine vollständigen Ergebnisse laden muss, um ein kombiniertes Ergebnis über Abfragen
- Die Modellstruktur bestimmt die zu ladenden Daten und wirkt sich direkt auf die Modellgröße aus. Es kann so entworfen werden, dass ein Laden nicht benötigter Daten vermieden wird, indem Spalten entfernt, Zeilen (insbesondere Verlaufsdaten) entfernt oder zusammengefasste Daten geladen werden (auf Kosten des Ladens von Detaildaten). Eine drastische Verringerung der Größe kann erreicht werden, indem Sie Spalten mit hoher Kardinalität (insbesondere Textspalten) entfernen, die nicht sehr effizient gespeichert oder komprimiert werden.
- Die Abfrageleistung des Modells kann durch Konfigurieren von Beziehungen mit nur einer Richtung verbessert werden, es sei denn, es gibt einen zwingenden Grund für eine bidirektionale Filterung. Sie sollten auch die crossfilter-Funktion anstelle der bidirektionalen Filterung verwenden.
- Aggregationstabellen können durch das Laden vorab zusammengefasster Daten schnelle Abfrageantworten erzielen, was jedoch zu einem größeren Modell und längeren Aktualisierungszeiten führt. Generell sollten Aggregationstabellen sehr großen Modellen oder Entwürfen mit zusammengesetzten Modellen vorbehalten sein.
- Berechnete Tabellen und Spalten erhöhen die Modellgröße und führen zu längeren Aktualisierungszeiten. Im Allgemeinen kann eine geringere Speichergröße und eine schnellere Aktualisierungszeit erreicht werden, wenn die Daten in der Datenquelle materialisiert oder berechnet werden. Wenn das nicht möglich ist, kann die Verwendung benutzerdefinierter Power Query-Spalten eine verbesserte Speicherkomprimierung bieten.
- Vielleicht besteht die Möglichkeit, DAX-Ausdrücke für Measures und RLS-Regeln zu optimieren, und eventuell die Logik neu zu schreiben, um kostspielige Formeln zu vermeiden.
- Die inkrementelle Aktualisierung kann die Aktualisierungszeit drastisch verkürzen sowie die Arbeitsspeicher- und CPU-Auslastung verringern. Die inkrementelle Aktualisierung kann auch so konfiguriert werden, dass Verlaufsdaten entfernt und somit Modellgrößen gering gehalten werden.
- Ein Modell kann als zwei Modelle umgestaltet werden, wenn unterschiedliche und widersprüchliche Abfragemuster vorhanden sind. Beispielsweise stellen einige Berichte allgemeine Aggregate im gesamten Verlauf dar und können eine Latenz von 24 Stunden tolerieren. Andere Berichte betreffen die aktuellen Daten und benötigen einen präzisen Zugriff auf einzelne Transaktionen. Anstatt ein einzelnes Modell für alle Berichte zu entwerfen, erstellen Sie zwei Modelle, die für die jeweilige Anforderung optimiert sind.

Sehen Sie sich die Optimierungsmöglichkeiten für ein DirectQuery-Modell an. Wenn das Modell Abfrage Anforderungen an die zugrunde liegende Datenquelle ausgibt, ist die Datenquellen Optimierung wichtig für die Bereitstellung von reaktionsfähigen Modell Abfragen.

 ![Optimierungsmöglichkeiten für ein DirectQuery-Modell](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

Auf der Datenquellen Ebene:

- Die Datenquelle kann optimiert werden, um die schnellstmögliche Abfrage zu gewährleisten, indem Sie Daten vorab integrieren (was auf der Modell Ebene nicht möglich ist), geeignete Indizes anwenden, Tabellen Partitionen definieren, zusammengefasste Daten (mit indizierten Sichten) materialisieren und Minimierung der Berechnungs Menge. Die beste Vorgehensweise wird erzielt, wenn Passthrough-Abfragen nur Filter filtern und interne Joins zwischen indizierten Tabellen oder Sichten ausführen müssen.
- Stellen Sie sicher, dass Gateways über ausreichend Ressourcen verfügen, vorzugsweise auf dedizierten Computern mit ausreichender Netzwerkbandbreite und unmittelbarer Nähe der Datenquelle.

Auf Modellebene:

- Power Query Abfrage Entwürfe sollten vorzugsweise keine Transformationen anwenden. versuchen Sie andernfalls, die Transformationen auf einem absoluten Minimal Stand zu halten.
- Die Abfrageleistung des Modells kann durch Konfigurieren von Beziehungen mit nur einer Richtung verbessert werden, es sei denn, es gibt einen zwingenden Grund für eine bidirektionale Filterung. Modell Beziehungen sollten außerdem so konfiguriert werden, dass die referenzielle Integrität erzwungen wird (in diesem Fall), und es werden Datenquellen Abfragen mit effizienteren inneren Joins (anstelle von äußeren Joins) durchgeführt.
- Vermeiden Sie das Erstellen Power Query Abfragen benutzerdefinierter Spalten oder der berechneten Spalte des Modells. materialisieren Sie diese in der Datenquelle, wenn möglich.
- Vielleicht besteht die Möglichkeit, DAX-Ausdrücke für Measures und RLS-Regeln zu optimieren, und eventuell die Logik neu zu schreiben, um kostspielige Formeln zu vermeiden.

Sehen Sie sich die Optimierungsmöglichkeiten für ein zusammengesetztes Modell an. Ein zusammengesetztes Modell ermöglicht eine Mischung aus Import- und DirectQuery-Tabellen.

![Optimierungsmöglichkeiten für ein zusammengesetztes Modell](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- Im Allgemeinen gelten die Optimierungs Themen für Import-und directquery-Modelle für zusammengesetzte Modell Tabellen, die diese Speicher Modi verwenden.
- In der Regel sollten Sie einen ausgeglichenen Entwurf anstreben, indem Sie Tabellen des Dimensionstyps (die Geschäftsentitäten darstellen) als Speichermodus „Dual“ und Tabellen des Faktentyps (häufig große Tabellen, die operative Fakten darstellen) als Speichermodus „DirectQuery“ konfigurieren. Der Dual-Speicher Modus bedeutet, dass sowohl der Import-als auch der directquery-Speicher Modus verwendet werden. Dadurch kann der Power BI-Dienst den effizientesten Speicher Modus ermitteln, der beim Erstellen einer systemeigenen Abfrage für Passthrough verwendet wird.
- Stellen Sie sicher, dass Gateways über ausreichende Ressourcen verfügen, vorzugsweise auf dedizierten Computern, mit ausreichender Netzwerkbandbreite und in unmittelbarer Nähe der Datenquellen.
- Aggregationstabellen, die als Speichermodus „Import“ konfiguriert sind, können drastische Verbesserungen der Abfrageleistung bewirken, wenn sie zur Zusammenfassung von Tabellen des Faktentyps im Speichermodus „DirectQuery“ verwendet werden. In diesem Fall führen Aggregationstabellen zu einem größeren Modell und längeren Aktualisierungszeiten, doch ist dies häufig ein akzeptabler Kompromiss für schnellere Abfragen.

#### <a name="optimizing-externally-hosted-models"></a>Optimieren von extern gehosteten Modellen

Viele Optimierungsmöglichkeiten, die im Thema [optimieren Power BI gehosteter Modelle](#optimizing-power-bi-hosted-models) erläutert werden, gelten auch für Modelle, die mit Azure Analysis Services und SQL Server Analysis Services entwickelt wurden. Eindeutige Ausnahmen sind bestimmte Features, die derzeit nicht unterstützt werden, einschließlich zusammengesetzter Modelle und Aggregationstabellen.

Eine zusätzliche Überlegung bei extern gehosteten Datasets betrifft das Datenbankhosting in Bezug auf den Power BI-Dienst. Bei Azure Analysis Services bedeutet dies, dass die Azure-Ressource in derselben Region wie der Power BI-Mandant (ursprüngliche Region) erstellt wird. Bei SQL Server Analysis Services für IaaS bedeutet dies, dass der virtuelle Computer in derselben Region gehostet wird, und für die lokale Umgebung bedeutet es die Sicherstellung einer effizienten Gatewayeinrichtung.

Außerdem kann es von Interesse sein, dass Azure Analysis Services-Datenbanken und tabellarische SQL Server Analysis Services-Datenbanken es erforderlich machen, dass ihre Modelle vollständig in den Arbeitsspeicher geladen werden und dort die ganze Zeit verbleiben, um Abfragen zu unterstützen. Wie beim Power BI-Dienst muss ausreichend Arbeitsspeicher für die Aktualisierung vorhanden sein, wenn das Modell während der Aktualisierung online bleiben muss. Im Gegensatz zum Power BI-Dienst gibt es kein Konzept, dass Modelle je nach Nutzung automatisch in den Arbeitsspeicher eingebunden und daraus entfernt werden. Power BI Premium bietet daher einen effizienteren Ansatz zur Maximierung von Modellabfragen bei geringerer Arbeitsspeicherauslastung.

### <a name="capacity-planning"></a>Kapazitätsplanung

Die Größe einer Premium-Kapazität bestimmt die verfügbaren Arbeitsspeicher- und Prozessorressourcen sowie die für die Kapazität zutreffenden Grenzwerte. Die Anzahl der Premium-Kapazitäten ist ebenfalls zu berücksichtigen, da das Erstellen mehrerer Premium-Kapazitäten dazu beitragen kann, Workloads voneinander zu isolieren. Der Speicher beträgt 100 TB pro Kapazitätsknoten, und dies ist wahrscheinlich für alle Workloads mehr als ausreichend.

Die Festlegung der Größe und Anzahl von Premium-Kapazitäten kann eine Herausforderung darstellen, insbesondere bei den anfänglichen Kapazitäten, die von Ihnen erstellt werden. Der erste Schritt bei der Dimensionierung der Kapazität besteht darin, die durchschnittliche Workload zu verstehen, die die erwartete tägliche Nutzung darstellt. Es ist wichtig zu wissen, dass nicht alle Arbeits Auslastungen gleich sind. Beispielsweise kann an einem Ende des Spektrums problemlos eine Anzahl von 100 gleichzeitigen Benutzern erreicht werden, die auf eine einzelne Berichtsseite zugreifen, die wiederum ein einzelnes visuelles Element enthält. Doch kann am anderen Ende des Spektrums eine Anzahl von 100 gleichzeitigen Benutzern, die auf 100 verschiedene Berichte mit jeweils 100 visuellen Elementen auf der Berichtsseite zugreifen, ganz andere Anforderungen an die Kapazitätsressourcen stellen.

Kapazitätsadministratoren müssen daher viele Faktoren berücksichtigen, die für Ihre Umgebung, die Inhalte und die erwartete Nutzung spezifisch sind. Das übergeordnete Ziel ist es, die Kapazitätsauslastung zu maximieren und gleichzeitig konsistente Abfragezeiten, akzeptable Wartezeiten und Entfernungsraten bereitzustellen. Dabei sind unter anderem die folgenden Faktoren zu berücksichtigen:

- **Modell Größe und Daten Merkmale** : Import Modelle müssen vollständig in den Arbeitsspeicher geladen werden, um Abfragen oder aktualisieren zu ermöglichen. Für LC/DQ-Datasets kann eine beträchtliche Prozessorzeit und möglicherweise erheblicher Arbeitsspeicher erforderlich sein, um komplexe Measures oder RLS-Regeln auszuwerten. Arbeitsspeicher- und Prozessorgröße sowie der LC/DQ-Abfragedurchsatz werden durch die Kapazitätsgröße eingeschränkt.
- **Gleichzeitige aktive Modelle** : die gleichzeitige Abfrage von unterschiedlichen Import Modellen liefert die beste Reaktionsfähigkeit und Leistung, wenn Sie im Arbeitsspeicher verbleiben. Es muss genügend Arbeitsspeicher zum Hosten aller stark abgefragten Modelle vorhanden sein sowie zusätzlicher Arbeitsspeicher, um deren Aktualisierung zu ermöglichen.
- **Importieren der Modell Aktualisierung** : der Aktualisierungstyp (vollständig oder inkrementell), die Dauer und die Komplexität von Power Query Abfragen und die berechnete Tabellen-/spaltenlogik können sich auf den Arbeitsspeicher und Gleichzeitige Aktualisierungen werden durch die Kapazitätsgröße eingeschränkt (1,5 x Back-End-V-Kerne, aufgerundet).
- **Gleichzeitige Abfragen** : viele gleichzeitige Abfragen können zu nicht reagierenden Berichten führen, wenn Prozessor-oder LC/DQ-Verbindungen das Kapazitäts Limit überschreiten. Dies gilt insbesondere für Berichtsseiten, die viele visuelle Elemente enthalten.
- **Dataflows, paginierte Berichte und Ki-Funktionen** : die Kapazität kann so konfiguriert werden, dass Datenflüsse, paginierte Berichte und Ki-Funktionen unterstützt werden, wobei jeder einen konfigurierbaren maximalen Prozentsatz des Kapazitäts Speichers erfordert. Der Arbeitsspeicher wird dynamisch Daten Flüssen zugeordnet, aber er wird den paginierten Berichten und der AI-Arbeitsauslastung statisch zugeordnet.

Zusätzlich zu diesen Faktoren können Kapazitätsadministratoren das Erstellen mehrerer Kapazitäten in Betracht ziehen. Mehrere Kapazitäten ermöglichen das Isolieren von Workloads und können so konfiguriert werden, dass Workloads mit Priorität garantierte Ressourcen zur Verfügung stehen. Es können beispielsweise zwei Kapazitäten erstellt werden, um unternehmenskritische Workloads von SSBI-Workloads (Self-Service-BI) zu trennen. Die unternehmenskritische Kapazität kann verwendet werden, um große Unternehmensmodelle zu isolieren und ihnen garantierte Ressourcen bereitzustellen, wobei der Erstellungszugriff nur der IT-Abteilung erteilt wird. Die SSBI-Kapazität kann verwendet werden, um eine wachsende Anzahl kleinerer Modelle zu hosten, wobei der Zugriff den Business Analysts gewährt wird. Bei der SSBI-Kapazität kann es gelegentlich zu tolerierbaren Wartezeiten bei der Abfrage oder Aktualisierung kommen.

Im Laufe der Zeit können Kapazitätsadministratoren Arbeitsbereiche kapazitätsübergreifend ausgleichen, indem sie Inhalte zwischen Arbeitsbereichen oder Arbeitsbereiche zwischen Kapazitäten verschieben und Kapazitäten zentral hoch- oder herunterskalieren. Im Allgemeinen können Sie zum Hosten größerer Modelle zentral hochskalieren und für eine höhere Parallelität skalieren.

Durch den Erwerb einer Lizenz werden dem Mandanten V-Kerne bereitgestellt. Bei Erwerb eines **P3**-Abonnements können eine oder bis zu vier Premium-Kapazitäten erstellt werden, d.h. 1 x P3 oder 2 x P2 oder 4 x P1. Außerdem kann vor der Erweiterung einer P2-Kapazität auf eine P3-Kapazität die Aufteilung der V-Kerne in zwei P1-Kapazitäten in Betracht gezogen werden.

### <a name="testing-approaches"></a>Testen von Ansätzen

Nachdem eine Kapazitätsgröße festgelegt wurde, können Tests durchgeführt werden, indem eine kontrollierte Umgebung erstellt wird. Eine praktische und wirtschaftliche Möglichkeit besteht darin, eine Azure-Kapazität (A-SKUs) zu erstellen, wobei darauf zu achten ist, dass eine P1-Kapazität dieselbe Größe wie eine A4-Kapazität und die P2- und P3-Kapazität die gleiche Größe wie die A5- bzw. A6-Kapazität hat. Azure-Kapazitäten können schnell erstellt und auf Stundenbasis abgerechnet werden. So können sie nach Abschluss der Tests einfach gelöscht werden, um anfallende Kosten zu vermeiden.

Der Testinhalt kann zu den Arbeitsbereichen hinzugefügt werden, die in der Azure-Kapazität erstellt wurden, und dann kann ein einzelner Benutzer Berichte ausführen, um eine realistische und repräsentative Workload von Abfragen zu generieren. Wenn Importmodelle vorhanden sind, sollte auch eine Aktualisierung für jedes Modell durchgeführt werden. Überwachungstools können dann zum Überprüfen aller Metriken verwendet werden, um die Ressourcennutzung zu verstehen.

Es ist wichtig, dass die Tests wiederholbar sind: Tests sollten mehrmals ausgeführt werden, und Sie sollten jedes Mal ungefähr dasselbe Ergebnis liefern. Der Durchschnitt dieser Ergebnisse kann verwendet werden, um eine Workload unter echten Produktionsbedingungen zu extrapolieren und abzuschätzen.

Wenn Sie bereits über eine Kapazität und die Berichte verfügen, für die Sie einen Auslastungstest durchführen möchten, verwenden Sie das [PowerShell-Tool zum Generieren einer Auslastung](https://aka.ms/PowerBILoadTestingTool), um schnell einen Auslastungstest zu erzeugen. Mit dem Tool können Sie abschätzen, wie viele Instanzen jedes Berichts ihre Kapazität innerhalb einer Stunde ausführen kann. Sie können das Tool verwenden, um die Fähigkeit der Kapazität zum Rendern einzelner Berichte oder zum parallelen Rendern mehrerer verschiedener Berichte abzuschätzen. Weitere Informationen finden Sie im Video [Microsoft Power BI: Premium-Kapazität](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Zum Generieren eines komplexeren Tests sollten Sie die Entwicklung einer Auslastungstestanwendung in Betracht ziehen, die eine realistische Workload simuliert. Weitere Informationen erhalten Sie im Webinar zum Thema [Testen von Power BI-Anwendungen mit dem Visual Studio-Auslastungstest](https://www.youtube.com/watch?v=UFbCh5TaR4w).

## <a name="exploring-real-world-scenarios"></a>Erkunden realer Szenarios

In diesem Abschnitt werden verschiedene reale Szenarien eingeführt, um häufige Probleme oder Herausforderungen zu beschreiben, Sie zu identifizieren und zu beheben, wie Sie gelöst werden können:

- [Beibehalten von Datasets auf dem neuesten Stand](#keeping-datasets-up-to-date)
- [Identifizieren von Datensätzen mit langsamer Reaktion](#identifying-slow-responding-datasets)
- [Identifizieren von Gründen für sporadisch langsam reagierende Datasets](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Bestimmen, ob genügend Arbeitsspeicher vorhanden ist](#determining-whether-there-is-enough-memory)
- [Bestimmen, ob genügend CPU vorhanden ist](#determining-whether-there-is-enough-cpu)

Die Schritte sowie Diagramm-und Tabellen Beispiele stammen aus der **Power BI Premium Capacity Metrics-App** (app), auf die ein Power BI Administrator zugreifen kann.

### <a name="keeping-datasets-up-to-date"></a>Beibehalten von Datasets auf dem neuesten Stand

In diesem Szenario wurde eine Untersuchung ausgelöst, wenn sich Benutzer darüber beschweren, dass die Berichtsdaten manchmal alt oder "veraltet" waren.

In der APP interagiert der Administrator mit dem visuellen Element **Aktualisieren** und sortiert Datasets nach der **maximalen Wartezeit** in absteigender Reihenfolge. Dadurch können die Datasets, die die längsten Wartezeiten aufweisen, nach Arbeitsbereichs Namen gruppiert angezeigt werden.

![DataSet-Aktualisierungen sortiert nach absteigender maximaler Wartezeit, gruppiert nach Arbeitsbereich](media/whitepaper-premium-deployment/dataset-refreshes.png)

Außerdem bemerken Sie, dass bei der Visualisierung der **stündlichen durchschnittlichen Aktualisierungs Wartezeit** die Wartezeit um jeden Tag konstant um 4 Uhr liegt.

![Spitzenzeiten beim Aktualisieren von warte Vorgängen um 16 Uhr](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Es gibt mehrere mögliche Erklärungen für diese Ergebnisse:

- Es können zu viele Aktualisierungs versuche gleichzeitig stattfinden, die die durch den Kapazitäts Knoten festgelegten Grenzwerte überschreiten (sechs gleichzeitige Aktualisierungen bei P1 mit Standard Speicher Belegung).

- Die zu aktualisierenden Datasets sind möglicherweise zu groß, um in den verfügbaren Arbeitsspeicher zu passen (für die vollständige Aktualisierung ist mindestens 2 x erforderlich).
- Ineffizient Power Query Logik kann zu einer Speicher Auslastungs Spitze während der Aktualisierung des Datasets führen. Bei einer ausgelasteten Kapazität kann dies gelegentlich die physische Grenze erreichen, die Aktualisierung nicht durchgehen und möglicherweise andere Berichts Ansichts Vorgänge für die Kapazität beeinträchtigen.
- Häufig abgefragte Datasets, die im Arbeitsspeicher bleiben müssen, können die Fähigkeit anderer Datasets aufgrund von eingeschränktem verfügbarem Speicher beeinträchtigen.

Um dies zu untersuchen, kann der Power BI-Administrator Folgendes suchen:

- Wenig verfügbarer Speicher zum Zeitpunkt der Datenaktualisierung, wenn der verfügbare Arbeitsspeicher kleiner als das 2-fache der Größe des Datasets ist, das aktualisiert werden soll.
- Datasets, die nicht aktualisiert wurden und vor einer Aktualisierung nicht im Arbeitsspeicher waren, aber mit der Anzeige von interaktivem Datenverkehr während hoher Aktualisierungszeiten begannen. Um zu sehen, welche Datasets zu einem beliebigen Zeitpunkt in den Arbeitsspeicher geladen wurden, kann ein Power BI Administrator den Bereich Datasets der Registerkarte **DataSets** in der App anzeigen und den Kreuz Filter zu einem bestimmten Zeitpunkt durch Klicken auf eine der Balken in der **Anzahl der stündlichen geladenen Datasets**durch klicken. Eine lokale Spitze (in der Abbildung unten dargestellt) gibt eine Stunde an, in der mehrere Datasets in den Arbeitsspeicher geladen wurden, was den Start geplanter Aktualisierungen verzögern kann.
- Vermehrte datasetentfernungen, die ausgeführt werden, wenn Datenaktualisierungen geplant sind. Dies deutet darauf hin, dass eine hohe Arbeitsspeicher Auslastung verursacht wurde, indem zu viele verschiedene interaktive Berichte vor dem Zeitpunkt der Aktualisierung bedient wurden. Die Visualisierung **stündliches DataSet und** die Arbeitsspeicher Nutzung können deutlich zu Spitzen in Entfernungen hindeuten.

Die folgende Abbildung zeigt eine lokale Spitze in geladenen Datasets, die eine interaktive Abfrage für den verzögerten Start von Aktualisierungen vorschlägt. Durch die Auswahl eines Zeitraums im visuellen Element für **stündliche geladene Datasets** wird die Visualisierung der **Größe des Datasets** Kreuz gefiltert.

![Eine lokale Spitze in geladenen Datasets schlägt den verzögerten Start von Aktualisierungen vor.](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

Der Power BI-Administrator kann versuchen, das Problem zu beheben, indem er die folgenden Schritte durchführt, um sicherzustellen, dass ausreichend Arbeitsspeicher für die Datenaktualisierung zur Verfügung steht:

- Kontaktieren von DataSet-Besitzern und Abfragen von Zeitplänen zur Datenaktualisierung
- Reduzieren der Auslastung von Datasetabfragen durch Entfernen unnötiger Dashboards oder dashboardkacheln, insbesondere bei der Durchsetzung der Sicherheit auf Zeilenebene
- Beschleunigung von Datenaktualisierungen durch Optimieren der Power Query Logik, berechnen von berechneten Spalten oder Tabellen, verringern von datasetgrößen oder konfigurieren größerer Datasets zum Durchführen einer inkrementellen Datenaktualisierung

### <a name="identifying-slow-responding-datasets"></a>Identifizieren von Datensätzen mit langsamer Reaktion

In diesem Szenario wurde eine Untersuchung ausgelöst, wenn sich Benutzer darüber beschweren, dass bestimmte Berichte lange Zeit in Anspruch genommen haben.

In der APP kann der Power BI Administrator mithilfe des visuellen Elements " **Abfrage** dauern" die ungünstigsten Datasets ermitteln, indem Datasets nach absteigender **durchschnittlicher Dauer**sortiert werden. Diese Visualisierung zeigt auch datasetabfragezählungen an, sodass Sie sehen können, wie oft die Datasets abgefragt werden.

![Aufdecken der schlechtesten leistungsstarken Datasets](media/whitepaper-premium-deployment/worst-performing-datasets.png)

Der Power BI-Administrator kann auf das visuelle Element für die **Abfrage Dauer Verteilung** verweisen, das für den gefilterten Zeitraum eine Gesamtverteilung der abgesenkten Abfrageleistung (< = 30ms, 0-100 MS usw.) anzeigt. Im Allgemeinen werden Abfragen, die eine Sekunde oder weniger benötigen, von den meisten Benutzern als reaktionsfähig angesehen. Abfragen, die mehr Zeit in Anspruch nehmen, erzeugen eine schlechte Leistung.

Mit der visuellen Visualisierung für die **stündliche Abfrage Dauer** kann der Power BI-Administrator einstündige Zeiträume ermitteln, wenn die Kapazitäts Leistung als unzureichend empfunden werden könnte. Je größer die Balken Segmente, die die Abfrage Dauer über eine Sekunde darstellen, desto größer ist das Risiko, dass Benutzer eine schlechte Leistung erkennen.

Das visuelle Element ist interaktiv, und wenn ein Segment der Leiste ausgewählt ist, wird die entsprechende Tabellen Visualisierung der **Abfrage Dauer** auf der Berichtsseite Kreuz gefiltert und zeigt die Datasets an, die Sie repräsentiert. Mit dieser Kreuz Filterung kann der Power BI Administrator leicht erkennen, welche Datasets langsam reagieren.

Die folgende Abbildung zeigt eine Visualisierung, die nach **stündlichen Distributionen der Abfrage Dauer**gefiltert wird und sich auf die schlechtesten leistungsstarken Datasets in einem einstündigen Bucket konzentriert. 

![Gefilterte, stündliche Abfrage Dauer Verteilungen Visualisierung zeigt die leistungsfähigsten Datasets an](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Sobald das DataSet mit schlechter Leistung in einer bestimmten Zeitspanne von 1 Stunde identifiziert wurde, kann der Power BI Administrator prüfen, ob eine schlechte Leistung durch eine überladene Kapazität verursacht wird, oder aufgrund eines unzureichend entworfenen Datasets oder Berichts. Um dies zu erreichen, können Sie auf die Visualisierung der **Abfrage Wartezeit** verweisen und Datasets nach absteigender durchschnittlicher Abfrage Wartezeit sortieren. Wenn ein großer Prozentsatz an Abfragen wartet, ist wahrscheinlich eine hohe Nachfrage nach dem DataSet die Ursache für die vielen Abfrage Wartezeiten. Wenn die durchschnittliche Abfrage Wartezeit beträchtlich (> 100 ms) ist, ist es möglicherweise sinnvoll, das DataSet und den Bericht zu überprüfen, um festzustellen, ob Optimierungen vorgenommen werden können. Beispielsweise werden möglicherweise weniger visuelle Elemente auf den angegebenen Berichts Seiten oder eine DAX-Ausdrucks Optimierung angezeigt.

![Das visuelle Element für die Abfrage Wartezeit hilft, leistungsstarke Datasets anzuzeigen.](media/whitepaper-premium-deployment/query-wait-times.png)

Es gibt mehrere mögliche Gründe für die Erstellung von Abfrage Wartezeiten in Datasets:

- Ein suboptimaler Modellentwurf, Measure-Ausdrücke oder sogar Berichtsentwurf: alle Umstände, die zu Abfragen mit langer Ausführungszeit beitragen können, die ein hohes Maß an CPU beanspruchen. Dadurch wird erzwungen, dass neue Abfragen gewartet werden, bis die CPU-Threads verfügbar sind, und Sie können einen konvoinffekt (Datenverkehrs Stau) erstellen, der häufig in Spitzenzeiten Die Seite **Abfrage Wartezeiten** ist die wichtigste Ressource, um zu bestimmen, ob Datasets hohe durchschnittliche Abfrage Wartezeit aufweisen.
- Eine große Anzahl gleichzeitiger Kapazitäts Benutzer (Hunderte bis Tausende), die denselben Bericht oder dasselbe Dataset verwenden. Selbst gut entworfene Datasets können über einen Parallelitäts Schwellenwert hinausgehen. Dies wird in der Regel durch ein einzelnes Dataset angegeben, das einen deutlich höheren Wert für die Abfrage Anzahl anzeigt als andere Datasets (d. h. 300 KB für ein DataSet im Vergleich zu < 30K-Abfragen für alle anderen Datasets). Zu einem späteren Zeitpunkt wartet die Abfrage darauf, dass das DataSet gestaffelt wird. Dies wird im visuellen Element für die **Abfrage Dauer** angezeigt.
- Viele unterschiedliche DataSets, die gleichzeitig abgefragt werden, führen zu einer Überlastung als Datasets, die häufig in den Arbeitsspeicher verschoben werden. Dies führt dazu, dass Benutzer beim Laden des Datasets in den Arbeitsspeicher eine langsame Leistung aufweisen. Um dies zu bestätigen, kann der Power BI Administrator auf das **stündliche DataSet-Entfernungs-und Arbeitsspeicher Verbrauch-** Element verweisen, das angibt, dass eine große Anzahl von Datasets, die in den Arbeitsspeicher geladen werden, wiederholt entfernt werden.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identifizieren von Gründen für sporadisch langsam reagierende Datasets

In diesem Szenario wurde eine Untersuchung ausgelöst, wenn Benutzer beschreiben, dass berichtsvisuals manchmal langsam waren oder nicht mehr reaktionsfähig waren, aber zu anderen Zeiten, in denen Sie nicht mehr reagiert haben.

In der App wurde der Abschnitt " **Abfrage Dauer** " verwendet, um das DataSet "-behalte" auf folgende Weise zu finden:

- Im visuellen Element für die **Abfrage Dauer** hat der admin ein Dataset nach DataSet gefiltert (beginnend bei den ersten abgefragten Datasets) und die Kreuz gefilterten Balken im visuellen Element der **stündlichen Abfrage Verteilung** untersucht.
- Wenn ein einzelner einstündiger Balken signifikante Änderungen im Verhältnis zwischen allen Abfrage Dauer Gruppen und anderen einstündigen Balken für das Dataset anzeigt (d.h. die Verhältnisse zwischen den Farben werden drastisch geändert), bedeutet dies, dass dieses DataSet eine sporadische Änderung in Leistungs.
- Der einstündige Balken, der einen unregelmäßigen Anteil von Abfragen mit schlechter Leistung anzeigt, gibt eine Zeitspanne an, bei der das Dataset durch einen Noisy Neighbor-Effekt beeinträchtigt wurde, der durch andere Datasets verursacht wurde.

Die Abbildung unten zeigt eine Stunde am 30. Januar, bei der ein erheblicher Rückschlag in der Leistung eines Datasets aufgetreten ist, was durch die Größe des Bucket "(3, 10S]" Ausführungsdauer angezeigt wird. Wenn Sie auf diese einstündige Leiste klicken, werden alle Datasets, die während dieser Zeit in den Arbeitsspeicher geladen werden, angezeigt

![Balken mit der schlechtesten Leistung durch einen großen Teil](media/whitepaper-premium-deployment/worst-performing-queries.png)

Sobald eine problematische Zeitspanne identifiziert ist (d. h. während des 30. Januar in der obigen Abbildung), kann der Power BI Administrator alle Datasetfilter entfernen und dann nur nach diesem Zeitraum filtern, um zu bestimmen, welche Datasets während dieser Zeit aktiv abgefragt wurden. Das behaltene Dataset für den "noisy Neighbor"-Effekt ist in der Regel entweder das erste abgefragte DataSet oder das DataSet mit der längsten durchschnittlichen Abfrage Dauer.

Eine Lösung für dieses Problem könnte darin bestehen, die problematischen Datasets über verschiedene Arbeitsbereiche auf unterschiedlichen Premium-Kapazitäten zu verteilen, oder auf freigegebene Kapazität, wenn die Größe des Datasets, die Verbrauchsanforderungen und die Daten Aktualisierungs Muster unterstützt werden.

Das Gegenteil könnte auch der Fall sein. Der Power BI-Administrator könnte Zeiten erkennen, in denen sich die Abfrageleistung eines Datasets drastisch verbessert, und dann nach dem Verschwinden suchen. Wenn an diesem Punkt bestimmte Informationen fehlen, kann dies dazu führen, dass Sie auf das verursachmögliche Problem zeigen.

### <a name="determining-whether-there-is-enough-memory"></a>Bestimmen, ob genügend Arbeitsspeicher vorhanden ist

Um zu ermitteln, ob genügend Arbeitsspeicher zur Verfügung steht, um die Arbeits Auslastungen abzuschließen, kann der Power BI Administrator auf der Registerkarte **DataSets** der APP auf den visuellen Wert des **verbrauchten Arbeitsspeichers** verweisen. Der **gesamte** (gesamte) Arbeitsspeicher steht für den Arbeitsspeicher, der von in den Arbeitsspeicher geladenen Datasets beansprucht wird, unabhängig davon, ob diese aktiv abgefragt oder verarbeitet werden. Der **aktive** Arbeitsspeicher stellt den Arbeitsspeicher dar, der von Datasets beansprucht wird, die aktiv verarbeitet werden.

In einer fehlerfreien Kapazität sieht das visuelle Element wie folgt aus und zeigt eine Lücke zwischen allen (Gesamt) und aktivem Speicher an:

![Eine fehlerfreie Kapazität zeigt eine Lücke zwischen allen (Gesamt) und aktivem Arbeitsspeicher.](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

In einer Kapazität mit unzureichendem Arbeitsspeicher zeigt das gleiche visuelle Element deutlich den aktiven Arbeitsspeicher und die gesamte Arbeitsspeicher konvergieren an, was bedeutet, dass es unmöglich ist, zu diesem Zeitpunkt weitere Datasets in den Arbeitsspeicher zu laden. In diesem Fall kann der Power BI Administrator auf **Kapazitäts Neustart** klicken (unter **Erweiterte Optionen** des Bereichs Kapazitäts Einstellungen des Verwaltungs Portals). Durch einen Neustart der Kapazität werden alle Datasets aus dem Arbeitsspeicher geleert, sodass Sie nach Bedarf in den Arbeitsspeicher geladen werden können (durch Abfragen oder die Datenaktualisierung).

![\* * Aktiv * * Arbeitsspeicher konvergieren mit * * alle * * Arbeitsspeicher](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Bestimmen, ob genügend CPU vorhanden ist

Im Allgemeinen sollte die durchschnittliche CPU-Auslastung einer Kapazität unter 80% liegen. Wenn dieser Wert überschritten wird, bedeutet dies, dass die Kapazität der CPU-

Die Auswirkungen der CPU-Sättigung werden durch Vorgänge ausgedrückt, die länger dauern als aufgrund der Kapazität, die viele CPU-Kontextwechsel durchführt, wenn versucht wird, alle Vorgänge zu verarbeiten. In einer Premium-Kapazität mit einer hohen Anzahl gleichzeitiger Abfragen wird dies durch hohe Abfrage Wartezeiten angegeben. Eine Folge hoher Abfrage Wartezeiten ist langsamer als üblich. Der Power BI-Administrator kann leicht erkennen, wann die CPU ausgelastet ist, indem er das visuelle Element für die **stündliche Abfrage Wartezeit** ansieht. Periodische Spitzenwerte der Abfrage Wartezeit zeigen auf eine potenzielle CPU-Sättigung hin.

![Regelmäßig auftretende Spitzen bei den Indikatoren der Abfragewartezeit weisen auf eine potenzielle CPU-Sättigung hin](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Ein ähnliches Muster kann manchmal bei Hintergrund Vorgängen erkannt werden, wenn Sie zur CPU-Sättigung beitragen. Ein Power BI-Administrator kann eine periodische Spitze der Aktualisierungszeiten für ein bestimmtes Dataset suchen, was zu einem bestimmten Zeitpunkt die CPU-Sättigung angeben kann (wahrscheinlich aufgrund anderer fortlaufender Datasetaktualisierungen und/oder interaktiver Abfragen). In diesem Fall kann das verweisen auf die **System** Sicht in der APP nicht notwendigerweise anzeigen, dass die CPU 100% beträgt. In der **System** Ansicht werden stündliche Durchschnittswerte angezeigt, aber die CPU kann für einige Minuten hoher Vorgänge, die als Spitzenwerte in Wartezeiten angezeigt werden, ausgelastet werden.

Es gibt weitere Nuancen, um die Auswirkung der CPU-Sättigung zu erkennen. Obwohl die Anzahl der Abfragen, die warten, wichtig ist, wird die Abfrage Wartezeit immer in gewissem Umfang durchgeführt, ohne dass eine erkennbare Leistungsminderung auftreten kann. Einige Datasets (mit längerer durchschnittlicher Abfragezeit, die die Komplexität oder Größe angeben) sind anfälliger für die Auswirkungen der CPU-Sättigung als andere. Um diese Datasets leicht zu identifizieren, kann der Power BI Administrator nach Änderungen in der Farbkomposition der Balken im visuellen Element für die **stündliche Wartezeit** suchen. Nachdem Sie eine ausreißerleiste entdeckt haben, können Sie nach den Datasets suchen, die während dieser Zeit Abfrage warte Vorgänge enthielten, und sich die durchschnittliche Abfrage Wartezeit im Vergleich zur durchschnittlichen Abfrage Dauer ansehen. Wenn diese beiden Metriken dieselbe Größe haben und die Abfrage Arbeitsauslastung für das DataSet nicht trivial ist, ist es wahrscheinlich, dass das Dataset durch unzureichende CPU beeinträchtigt wird.

Dieser Effekt kann besonders offensichtlich sein, wenn ein Dataset in kurzen Spitzen von Abfragen mit hoher Häufigkeit von mehreren Benutzern (d. h. in einer Trainings Sitzung) genutzt wird, was zu einer CPU-Sättigung bei jedem Burst führt. In diesem Fall können bedeutende Abfrage Wartezeiten für dieses Dataset auftreten und sich auf andere Datasets in der Kapazität auswirken (Noisy Neighbor-Effekt).

In einigen Fällen können Power BI Administratoren anfordern, dass DataSet-Besitzer eine geringere Abfrage Arbeitsauslastung erstellen, indem Sie ein Dashboard erstellen (das in regelmäßigen Abständen eine beliebige datasetaktualisierung für zwischengespeicherte Kacheln abfragt) statt eines Berichts. Dadurch können Spitzen beim Laden des Dashboards vermieden werden. Diese Lösung ist für bestimmte Geschäftsanforderungen möglicherweise nicht immer möglich. es kann jedoch eine effektive Möglichkeit sein, CPU-Sättigung zu vermeiden, ohne Änderungen am DataSet vorzunehmen.

## <a name="conclusion"></a>Fazit

Power BI Premium bietet eine konsistente Leistung, Unterstützung für große Datenvolumes und die Flexibilität einer einheitlichen Self-Service-und Enterprise-BI-Plattform für alle Personen in Ihrer Organisation. Dieses technische Whitepaper der Ebene 300 wurde speziell für Power BI-Administratoren und Inhaltsautoren und-Herausgeber geschrieben. Es soll Ihnen helfen, das Potenzial von Power BI Premium zu verstehen und zu erläutern, wie Sie skalierbare Lösungen entwerfen, bereitstellen, überwachen und beheben können.

Zum Bereitstellen und Verwalten von Power BI Premium Kapazitäten benötigen Administratoren und Modell Entwickler ein sehr gutes Verständnis der Funktionsweise, der Art und Weise, wie Sie verwaltet und überwacht werden können, und der Optimierung von Modellen, damit Sie entsprechend reagieren können. Leistungsprobleme und Engpässe sollten auftreten.

## <a name="end-notes"></a>Notizen beenden

<a name="endnote-01"></a>\[1\] dieses technische Whitepaper befasst sich mit Power BI Premium, das nur vom clouddienst Power BI unterstützt wird. Power BI-Berichtsserver ist nicht im Bereich, es sei denn, es wird angegeben, dass die für die Installation von Power BI-Berichtsserver erforderliche Lizenz in enthalten ist. einige Power BI Premium-SKUs.

<a name="endnote-02"></a>\[2\] als clouddienst Power BI, wenn Sie zum Einbetten von Inhalten im Namen von Anwendungs Benutzern verwendet wird, ist Platform-as-a-Service (PAS). Diese Art der Einbettung kann mit unterschiedlichen beiden Produkten erreicht werden, von denen eine Power BI Premium ist.

<a name="endnote-03"></a>\[3\] Push-, Streaming-und Hybrid Datasets werden nicht in Premium-Kapazitäten gespeichert und sind daher bei der Bereitstellung, Verwaltung und Überwachung von Premium-Kapazitäten nicht zu berücksichtigen.

<a name="endnote-04"></a>\[4\] Excel-Arbeitsmappen als Power BI Inhaltstyp nicht in Premium-Kapazitäten gespeichert und daher bei der Bereitstellung, Verwaltung und Überwachung von Premium-Kapazitäten nicht berücksichtigt.

<a name="endnote-05"></a>\[5\] visuellen Elemente können so konfiguriert werden, dass Slicer-Interaktionen ignoriert werden. Weitere Informationen finden Sie unter Interaktionen mit [Visualisierungen in einem Power BI-Berichts](service-reports-visual-interactions.md) Dokument.

<a name="endnote-06"></a>\[6\] der Unterschied in der Größe festgelegt werden, indem die Power BI Desktop Dateigröße mit dem Task-Manager-Arbeitsspeicher verglichen wird, der für die Datei verwendet.

<a name="endnote-07"></a>\[7\] Unterstützung für Microsoft-Datenquellen enthalten SQL Server, Azure Data Bricks, Azure HDInsight Spark (Beta), Azure SQL-Datenbank und Azure SQL Data Warehouse. Weitere Informationen zu zusätzlichen Quellen finden Sie unter [Datenquellen, die von direkter Abfrage in Power BI Dokument unterstützt](desktop-directquery-data-sources.md) werden.

<a name="endnote-08"></a>\[8\] Power BI Premium unterstützt das Hochladen einer Power BI Desktop Datei (. pbix) bis zu einer Größe von maximal 10 GB. Nach dem Hochladen kann ein DataSet im Ergebnis der Aktualisierung bis zu 12 GB groß werden. Die maximale Uploadgröße variiert je nach SKU. Weitere Informationen finden Sie im Dokument [Power BI Premium-Unterstützung für große Datasets](service-premium-large-datasets.md) .

<a name="endnote-09"></a>\[9\] SKUs mit weniger als vier v-Kernen können nicht in einer dedizierten Infrastruktur ausgeführt werden. Hierzu gehören die SKUs EM1, EM2, a1 und a2.

<a name="endnote-10"></a>\[10\] in seltenen Fällen können Modelle aufgrund von Dienst Vorgängen aus dem Arbeitsspeicher entladen werden.

<a name="endnote-11"></a>\[11\] diese Zeitangaben jederzeit geändert werden können.

<a name="endnote-12"></a>\[12\] dies als mehrere georedunare, derzeit als Vorschau bezeichnet. Der Grund für eine Multi-Geo-Bereitstellung liegt in der Regel eher in der Konformität mit Unternehmens- oder behördlichen Anforderungen als in Leistung und Skalierung. Für das Laden von Berichten und Dashboards sind weiterhin Metadatenanforderungen an die Startregion erforderlich. Weitere Informationen finden Sie im Dokument [Unterstützung für mehrere georedunkte für Power BI Premium (Vorschau)](service-admin-premium-multi-geo.md) .

<a name="endnote-13"></a>\[13\] es möglich ist, dass Benutzer Leistungsprobleme verursachen können, indem Sie die Power BI-Dienst mit Aufträgen über laden, übermäßig komplexe Abfragen schreiben, Zirkel Verweise erstellen usw.

<a name="endnote-14"></a>\[14\] die Option zum Zuweisen der Arbeitsbereiche der gesamten Organisation nicht empfohlen, und ein gezielteres Konzept wird bevorzugt. Im Allgemeinen ist es nicht empfehlenswert, persönliche Arbeitsbereiche für Produktions Inhalte zu verwenden.

<a name="endnote-15"></a>\[15\] es möglich, SKUs in der APP oder im Azure-Portal zu überwachen, jedoch nicht im Power BI Admin-Portal. Zum Überwachen von SKUs tritt bei der Aktualisierung des Berichts ein Fehler auf, wenn die APP nicht der Rolle "Leser" der Ressource hinzugefügt wurde. Weitere Informationen finden Sie im Dokument [überwachen Power BI Premium und Power BI Embedded Kapazitäten](service-admin-premium-monitor-capacity.md) .

<a name="endnote-16"></a>\[16\] Aktualisierungen können warten, wenn nicht genügend CPU oder Arbeitsspeicher verfügbar ist.

<a name="endnote-17"></a>\[17\] die Größe des Datasets im Arbeitsspeicher größer als die Größe auf dem Datenträger um bis zu 20%.

<a name="endnote-18"></a>\[18\] durchschnittliche Speicherauslastung (GB) und höchste Arbeitsspeicher Nutzung (GB)

<a name="endnote-19"></a>\[19\] datasetentfernungen

<a name="endnote-20"></a>\[20\] Datasetabfragen, durchschnittliche Abfrage Dauer von Datasets (MS), Anzahl der datasetwartezeiten und durchschnittliche Wartezeit für Datasets (MS)

<a name="endnote-21"></a>\[21\] CPU-Auslastung mit hoher Auslastung und CPU-Zeit der höchsten Auslastung (in den letzten sieben Tagen)

<a name="endnote-22"></a>\[22\] DQ/LC-hohe Auslastung und DQ/LC-Zeit der höchsten Auslastung (in den letzten sieben Tagen)
