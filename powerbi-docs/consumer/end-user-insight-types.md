---
title: Von Power BI unterstützte Einblicke
description: Schnelle Einblicke und „Einblicke anzeigen“ in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 216c58644ee13cc6015878fc31d83e47e5673398
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "61064283"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Von Power BI unterstützte Einblicke
## <a name="how-does-insights-work"></a>Wie funktionieren Einblicke?
Power BI durchsucht schnell verschiedene Teilmengen des Datasets unter Verwendung eines hoch entwickelten Algorithmus, um potenziell interessante Einblicke zu gewinnen. Power BI untersucht in einer festgelegten Zeit möglichst große Mengen des Datasets.

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

Wenn Sie ein Dataset besitzen, können Sie es [für Einblicke optimieren](../service-insights-optimize.md).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

