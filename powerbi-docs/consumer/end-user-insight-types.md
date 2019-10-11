---
title: Von Power BI unterstützte Einblicke
description: Schnelle Einblicke und „Einblicke anzeigen“ in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/2/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 507d49ba6cdb894667bf66f8f35c5c325b9ff25e
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943923"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Von Power BI unterstützte Einblicke

Der Power BI-Dienst kann in Ihren Dashboards und Berichten automatisch nach Erkenntnissen suchen.

## <a name="how-does-insights-work"></a>Wie funktionieren Einblicke?
Power BI durchsucht schnell verschiedene Teilmengen Ihres Datasets. Während der Suche nutzt Power BI mehrere hoch entwickelte Algorithmen, um potenziell interessante Erkenntnisse zu ermitteln. Power BI untersucht in einer festgelegten Zeit möglichst große Mengen des Datasets.

Sie können Einblicke für ein Dataset oder eine Dashboard-Kachel ausführen.   

## <a name="what-types-of-insights-can-we-find"></a>Nach welchen Typen von Informationen kann gesucht werden?
Im Folgenden finden Sie einige der verwendeten Algorithmen:

## <a name="category-outliers-topbottom"></a>Kategorieausreißer (oben/unten)
Hebt die Fälle hervor, in denen für eine Messung im Modell ein oder zwei Elemente einer Dimension wesentlich größere Werte als andere Elemente der Dimension haben.  

![Beispiel für Kategorieausreißer](./media/end-user-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>Änderungspunkte in einer Zeitreihe
Hebt hervor, wenn es signifikante Trendänderungen in einer Zeitreihe von Daten gibt.

![Beispiel für Änderungspunkte im Laufe der Zeit](./media/end-user-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>Korrelation
Erkennt Fälle, in denen mehrere Messungen eine Korrelation zwischen diesen Messungen zeigen, wenn diese an einer Dimension im Dataset dargestellt werden.

![Beispiel für Korrelation](./media/end-user-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>Geringe Abweichung
Erkennt Fälle, in denen Datenpunkte nicht stark vom Mittelwert abweichen.

![Beispiel für geringe Abweichung](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>Mehrheit (Hauptfaktoren)
Sucht nach Fällen, in denen eine Mehrheit eines Gesamtwerts beim Aufschlüsseln in eine andere Dimension einem einzelnen Faktor zugeordnet werden kann.  

![Beispiel für Hauptfaktoren](./media/end-user-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>Allgemeine Trends in Zeitreihen
Entdeckt Trends nach oben oder unten in Zeitreihendaten.

![Beispiel für allgemeine Trends im Laufe der Zeit](./media/end-user-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>Saisonabhängigkeit in Zeitreihen
Sucht periodische Muster in Zeitreihendaten, z. B. wöchentliche, monatliche oder jährliche Saisonabhängigkeit.

![Beispiel für Saisonabhängigkeit](./media/end-user-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>Stetiger Anteil
Hebt Fälle hervor, in denen eine Beziehung von übergeordneten und untergeordneten Elementen zwischen dem Anteil eines untergeordneten Werts in Bezug auf den Gesamtwert des übergeordneten Elements für eine kontinuierliche Variable vorhanden ist.

![Beispiel für stetigen Anteil](./media/end-user-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>Zeitreihenausreißer
Erkennt in Daten auf einer Zeitreihe, wenn bestimmte Datums- oder Zeitangaben mit sich deutlich von den übrigen Daten unterscheidenden Werten vorliegen.

![Beispiel für Ausreißer im Laufe der Zeit](./media/end-user-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>Nächste Schritte
[Power BI-Einblicke](end-user-insights.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

