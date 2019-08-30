---
title: Konfigurieren von Workloads in Power BI Premium
description: Hier erfahren Sie, wie Sie Workloads in einer Power BI Premium-Kapazität konfigurieren.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985692"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Konfigurieren von Workloads in einer Premium-Kapazität

In diesem Artikel erfahren Sie, wie Sie Workloads für Power BI Premium-Kapazitäten aktivieren und konfigurieren. Kapazitäten unterstützen standardmäßig nur die Workload für die Ausführung von Power BI-Abfragen. Sie können auch zusätzliche Workloads für **[KI (Cognitive Services)](service-cognitive-services.md)** , **[Dataflows](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** und **[Paginierte Berichte](paginated-reports-save-to-power-bi-service.md)** aktivieren und konfigurieren.

## <a name="default-memory-settings"></a>Standardeinstellungen für den Arbeitsspeicher

Abfrageworkloads sind für Ressourcen optimiert und durch Ressourcen beschränkt, die durch Ihre Premium-Kapazitäts-SKU bestimmt werden. Premium-Kapazitäten unterstützen auch zusätzliche Workloads, die Ihre Kapazitätsressourcen nutzen können. Arbeitsspeicher-Standardwerte für diese Workloads basieren auf den Kapazitätsknoten, die für Ihre SKU zur Verfügung stehen. Die Einstellungen für maximalen Arbeitsspeicher sind nicht kumulativ. Für KI und Dataflows wird Arbeitsspeicher dynamisch bis zum angegebenen Maximalwert zugeordnet. Für paginierte Berichte ist die Zuordnung dagegen statisch.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office-SKUs für Software-as-a-Service-Szenarios (SaaS)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| KI | N/V | N/V | 20 % Standard; mindestens 20 % | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 % |
| Dataflows | N/V |20% Standard; mindestens 12%  | 20 % Standard, mindestens 5 %  | 20% Standard; mindestens 3% | 20 % Standard, mindestens 2 %  |
| Paginierte Berichte | N/V |N/V | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 % | 20 % Standard, mindestens 2,5 % |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Azure-SKUs für Plattform-as-a-Service-Szenarios (PaaS)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| KI | N/V                      | 20 % Standard; mindestens 100 %                     | 20 % Standard; mindestens 50 %                     | 20 % Standard; mindestens 20 % | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 % |
| Dataflows         | 40% Standard; mindestens 40% | 24% Standard; mindestens 24% | 20% Standard; mindestens 12% | 20 % Standard, mindestens 5 %  | 20% Standard; mindestens 3% | 20 % Standard, mindestens 2 %   |
| Paginierte Berichte | N/V                      | N/V                      | N/V                     | 20 % Standard, mindestens 10 % | 20 % Standard, mindestens 5 % | 20 % Standard, mindestens 2,5 % |
| | | | | | |

## <a name="workload-settings"></a>Workloadeinstellungen

### <a name="ai-preview"></a>KI (Vorschauversion)

Mit der KI-Workload können Sie Cognitive Services und automatisiertes maschinelles Lernen in Power BI verwenden. Verwenden Sie die folgenden Einstellungen, um das Workloadverhalten zu steuern.

| Einstellungsname | Beschreibung |
|---------------------------------|----------------------------------------|
| **Max. Arbeitsspeicher (%)** | Der Prozentsatz des maximal verfügbaren Arbeitsspeichers, der von KI-Prozessen in einer Kapazität verwendet werden kann. |
| **Verwendung über Power BI Desktop zulassen** | Diese Einstellung ist für die zukünftige Verwendung reserviert und wird nicht auf allen Mandanten angezeigt. |
| **Erstellung von Machine Learning-Modellen zulassen** | Diese Einstellung gibt an, ob Business Analysts Machine Learning-Modelle direkt in Power BI trainieren, überprüfen und aufrufen können. Weitere Informationen finden Sie unter [Automatisiertes Machine Learning in Power BI (Vorschau)](service-machine-learning-automated.md). |
| **Parallelismus für KI-Anforderungen aktivieren** | Diese Einstellung gibt an, ob KI-Anforderungen parallel ausgeführt werden können. |
|  |  |

### <a name="datasets"></a>Datasets

Die Datasetworkload ist standardmäßig aktiviert und kann nicht deaktiviert werden. Verwenden Sie die folgenden Einstellungen, um das Workloadverhalten zu steuern.

| Einstellungsname | Beschreibung |
|---------------------------------|----------------------------------------|
| **Max. Arbeitsspeicher (%)** | Der Prozentsatz des maximal verfügbaren Arbeitsspeichers, der von Datasets in einer Kapazität verwendet werden kann. |
| **XMLA-Endpunkt** | Mit dieser Einstellung wird festgelegt, dass Verbindungen von Clientanwendungen die Sicherheitsgruppenmitgliedschaft berücksichtigen, die auf den Ebenen des Arbeitsbereichs und der Apps festgelegt wird. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Datasets und Clientanwendungen und Tools](service-premium-connect-tools.md). |
| **Max Intermediate Row Set Count** (Maximale Anzahl von Zwischenrowsets) | Die maximale Anzahl von Zwischenzeilen, die von DirectQuery zurückgegeben werden. Der Standardwert ist 1.000.000, und der zulässige Bereich liegt zwischen 100.000 und 2.147.483.647. Verwenden Sie diese Einstellung, um die Auswirkungen ressourcenintensiver oder schlecht konzipierter Berichte einzuschränken. |
| **Maximale Größe für Offlinedataset (GB)** | Die maximale Größe des Offlinedatasets im Arbeitsspeicher. Dies ist die komprimierte Größe auf dem Datenträger. Der Standardwert wird durch die SKU festgelegt, und der zulässige Bereich liegt zwischen 0,1 und 10 GB. Mit dieser Einstellung hindern Sie Ersteller von Berichten daran, ein großes Dataset zu veröffentlichen, das sich negativ auf die Kapazität auswirken könnte. |
| **Max Result Row Set Count** (Maximale Anzahl von Ergebnisrowsets) | Die maximale Anzahl von Zeilen, die in einer DAX-Abfrage zurückgegeben werden. Der Standardwert ist -1 (keine Grenze), und der zulässige Bereich liegt zwischen 100000 und 2147483647. Verwenden Sie diese Einstellung, um die Auswirkungen ressourcenintensiver oder schlecht konzipierter Berichte einzuschränken. |
| **Query Memory Limit (%)** (Arbeitsspeicherlimit für Abfragen (%)) | Der Prozentsatz des maximal verfügbaren Arbeitsspeichers, der für temporäre Ergebnisse in einer Abfrage oder einem DAX-Measure verwendet werden kann. Verwenden Sie diese Einstellung, um die Auswirkungen ressourcenintensiver oder schlecht konzipierter Berichte einzuschränken. |
| **Query Timeout (seconds)** (Abfragetimeout (Sekunden)) | Die maximale Zeitspanne bis zum Timeout einer Abfrage. Der Standardwert lautet 3.600 Sekunden (1 Stunde). Bei einem Wert von 0 (null) tritt kein Timeout für Abfragen auf. Mit dieser Einstellung erhalten Sie mehr Kontrolle über zeitintensive Abfragen. |
|  |  |  |

### <a name="dataflows"></a>Dataflows

Mit der Dataflow-Workload können Sie die Self-Service-Datenaufbereitung von Dataflows nutzen, um Daten zu erfassen, zu transformieren, zu integrieren und zu erweitern. Verwenden Sie die folgenden Einstellungen, um das Workloadverhalten zu steuern.

| Einstellungsname | Beschreibung |
|---------------------------------|----------------------------------------|
| **Max. Arbeitsspeicher (%)** | Der Prozentsatz des maximal verfügbaren Arbeitsspeichers, der von Dataflows in einer Kapazität verwendet werden kann. |
| **Erweiterte Dataflowcomputing-Engine (Vorschau)** | Aktivieren Sie diese Option, um eine bis zu 20-fach schnellere Berechnung von berechneten Entitäten bei der Arbeit mit umfangreichen Datenmengen zu erzielen. **Damit die neue Engine aktiviert wird, müssen Sie die Kapazität neu starten.** Weitere Informationen finden Sie unter [Erweiterte Dataflowcomputing-Engine](#enhanced-dataflows-compute-engine). |
| **Containergröße** | Die maximale Größe des Containers, der für jede Entität im Dataflow verwendet wird. Der Standardwert ist 700 MB. Weitere Informationen finden Sie unter [Containergröße](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Erweiterte Dataflowcomputing-Engine

Unterteilen Sie die Erfassung von Daten in separate Dataflows, und integrieren Sie Transformationslogik in berechnete Entitäten in verschiedenen Dataflows, um von der neuen Compute-Engine zu profitieren. Dieser Ansatz wird empfohlen, weil die Compute-Engine mit Dataflows arbeitet, die auf einen vorhandenen Dataflow verweisen. Dies funktioniert für Dataflows für die Erfassung von Daten nicht. Indem Sie den Anweisungen folgen, stellen Sie sicher, dass die neue Compute-Engine die Transformationsschritte verarbeitet, z. B. Joins und Merges, um optimale Leistung zu erzielen.

#### <a name="container-size"></a>Containergröße

Beim Aktualisieren eines Dataflows erzeugt die Workload für Dataflows einen Container für jede Entität im Dataflow. Die Größe des Containerspeichers wird durch den Wert der Einstellung „Containergröße“ festgelegt. Der Standardwert für alle SKUs ist 700 MB. Sie sollten diese Einstellung in den folgenden Situationen ändern:

- Die Aktualisierung der Dataflows dauert zu lange oder schlägt bei einem Timeout fehl.
- Dataflowentitäten enthalten Berechnungsschritte wie Joins.  

Es wird empfohlen, die App [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) zu verwenden, um die Leistung der Workload für Dataflows zu analysieren.

In einigen Fällen führt das Erhöhen der Containergröße möglicherweise nicht zu einer Verbesserung der Leistung. Wenn z. B. der Dataflow Daten aus einer Quelle ausschließlich abruft, ohne wesentliche Berechnungen durchzuführen, hat eine Anpassung der Containergröße vermutlich keine positiven Auswirkungen. Die Erhöhung der Containergröße kann hilfreich sein, wenn die Workload für Dataflows mehr Speicher für Entitätsaktualisierungen belegen kann. Dadurch kann die Aktualisierungszeit für Entitäten verkürzt werden, für die rechenintensive Vorgänge ausgeführt werden.

Der Wert für „Containergröße“ darf die maximale Größe des Arbeitsspeichers für die Workload der Dataflows nicht überschreiten. Eine P1-Kapazität verfügt beispielsweise über 25 GB Arbeitsspeicher. Wenn für die Einstellung „Max. Arbeitsspeicher“ ein Wert von 20 % für die Workload der Dataflows festgelegt ist, kann der Wert von „Containergröße“ 5000 MB nicht überschreiten. In keinem Fall kann der Wert von „Containergröße“ den von „Max. Arbeitsspeicher“ überschreiten, und zwar auch dann nicht, wenn Sie einen höheren Wert festlegen.

### <a name="paginated-reports"></a>Paginierte Berichte

Die Workload für paginierte Berichte ermöglicht Ihnen die Ausführung paginierter Berichte basierend auf dem Standardformat von SQL Server Reporting Services im Power BI-Dienst. Verwenden Sie die folgende Einstellung, um das Workloadverhalten zu steuern.

| Einstellungsname | Beschreibung |
|---------------------------------|----------------------------------------|
| **Max. Arbeitsspeicher (%)** | Der Prozentsatz des maximal verfügbaren Arbeitsspeichers, der von paginierten Berichten in einer Kapazität verwendet werden kann. |
|  |  |

Mit paginierten Berichten kann benutzerdefinierter Code beim Rendern eines Berichts ausgeführt werden. Das ist beispielsweise sinnvoll, wenn sich die Textfarbe auf Grundlage der Inhalte dynamisch ändert, wodurch zusätzlicher Arbeitsspeicher belegt werden kann. Power BI Premium führt paginierte Berichte in einem Bereich innerhalb der Kapazität aus. Der festgelegte Wert für „Max. Arbeitsspeicher“ wird *unabhängig* davon verwendet, ob die Workload aktiv ist. Wenn Sie für die Einstellung „Max. Arbeitsspeicher“ einen Wert festlegen, der sich von der Standardeinstellung unterscheidet, müssen Sie einen ausreichend niedrigen Wert festlegen, damit dieser sich nicht negativ auf die anderen Workloads auswirkt.

Teilweise kann es vorkommen, dass die Workload für paginierte Berichte nicht verfügbar ist. In diesem Fall zeigt die Workload einen Fehlerstatus im Verwaltungsportal an, und den Benutzern werden Timeouts beim Rendern von Berichten angezeigt. Deaktivieren Sie die Workload, und aktivieren Sie sie dann erneut, um dieses Problem zu beheben.

## <a name="configure-workloads"></a>Konfigurieren von Workloads

Maximieren Sie die Kapazität der verfügbaren Ressourcen, indem Sie Workloads nur dann ermöglichen, wenn sie verwendet werden. Ändern Sie Arbeitsspeichereinstellungen und andere Einstellungen nur dann, wenn Sie Standardeinstellungen festgelegt haben, die Ihre Anforderungen an Kapazitätsressourcen nicht erfüllen.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>So konfigurieren Sie Workloads im Power BI-Verwaltungsportal

1. Wählen Sie unter **Kapazitätseinstellungen** > **PREMIUM-KAPAZITÄTEN** eine Kapazität aus.

1. Erweitern Sie unter **Weitere Optionen** **Workloads**.

1. Aktivieren Sie mindestens eine Workload, und legen Sie einen Wert für **Max. Arbeitsspeicher** und die anderen Einstellungen fest.

1. Klicken Sie auf **Übernehmen**.

### <a name="rest-api"></a>REST-API

Workloads können mithilfe der REST-APIs vom Typ [Capacities](https://docs.microsoft.com/rest/api/power-bi/capacities) aktiviert und einer Kapazität zugewiesen werden.

## <a name="monitoring-workloads"></a>Überwachung von Workloads

Die [Power BI Premium-Kapazitätsmetriken-App](service-admin-premium-monitor-capacity.md) bietet Metriken für Datasets, Dataflows und paginierte Berichte zur Überwachung von Workloads, die für Ihre Kapazitäten aktiviert sind. 

## <a name="next-steps"></a>Nächste Schritte

[Optimieren von Power BI Premium-Kapazitäten](service-premium-capacity-optimize.md)     
[Self-Service-Datenaufbereitung in Power BI (Vorschau)](service-dataflows-overview.md)   
[Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)   

Weitere Fragen? [Fragen an die Power BI-Community](http://community.powerbi.com/)