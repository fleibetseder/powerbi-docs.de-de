---
title: "Kartenvisualisierungen (auch als Kacheln für große Zahlen bezeichnet)"
description: Erstellen von Kartenvisualisierungen in Power BI
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/24/2017
ms.author: mihart
ms.openlocfilehash: 1136aae9af4481a1d55ca3d11ed300242aab187b
ms.sourcegitcommit: 74fbbca81a056dda19b3647ae058005aba5296f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2018
---
# <a name="card-visualizations"></a>Kartenvisualisierungen
Manchmal ist eine einzelne Zahl das Wichtigste, das Sie in Ihrem Power BI-Dashboard oder Bericht nachverfolgen möchten, wie z.B. der Gesamtumsatz, der Marktanteil im Jahresverlauf oder die Gesamtverkaufschancen. Eine solche Visualisierung wird als *Karte* bezeichnet. Wie fast alle nativen Power BI-Visualisierungen können Karten im Berichts-Editor oder in Q&A erstellt werden.

![Kartenvisualisierung](media/power-bi-visualization-card/pbi_opptuntiescard.png)

## <a name="create-a-card-using-the-report-editor"></a>Erstellen einer Karte im Berichts-Editor
In dieser Anleitung wird das Analysebeispiel für den Einzelhandel verwendet. Wenn Sie diese Schritte selbst ausführen möchten, [laden Sie das Beispiel für den Power BI-Dienst („app.powerbi.com“) oder Power BI Desktop herunter](sample-datasets.md).   

1. Beginnen Sie mit einer [leeren Berichtsseite](power-bi-report-add-page.md), und wählen Sie das Feld **Store** \> **Open store count** aus. Wenn Sie den Power BI-Dienst verwenden, müssen Sie den Bericht in der [Bearbeitungsansicht](service-interact-with-a-report-in-editing-view.md) öffnen.

    Power BI erstellt ein Säulendiagramm mit dieser einen Zahl.

   ![](media/power-bi-visualization-card/pbi_rptnumbertilechart.png)
2. Wählen Sie im Bereich „Visualisierungen“ das Kartensymbol aus.

   ![](media/power-bi-visualization-card/pbi_changechartcard.png)
6. Zeigen Sie auf die Karte, und wählen Sie das Anheftsymbol ![](media/power-bi-visualization-card/pbi_pintile.png) aus, um die Visualisierung dem Dashboard hinzuzufügen.

   ![](media/power-bi-visualization-card/power-bi-pin-icon.png)
7. Heften Sie die Kachel an ein vorhandenes oder neues Dashboard an.

   * Vorhandenes Dashboard: Wählen Sie den Namen des Dashboards aus der Dropdownliste aus.
   * Neues Dashboard: Geben Sie den Namen des neuen Dashboards ein.
8. Wählen Sie **Anheften**aus.

   Eine Erfolgsmeldung (in der Nähe der oberen rechten Ecke) weist Sie darauf hin, dass die Visualisierung als Kachel zu Ihrem Dashboard hinzugefügt wurde.

   ![](media/power-bi-visualization-card/power-bi-pin-success-message.png)
9. Wählen Sie **Zum Dashboard wechseln** aus. Hier können Sie die angeheftete Visualisierung [bearbeiten und verschieben](service-dashboard-edit-tile.md).


## <a name="create-a-card-from-the-qa-question-box"></a>Erstellen einer Karte aus dem Q&A-Fragefeld
Das Q&A-Fragefeld bietet die einfachste Möglichkeit, eine Karte zu erstellen. Das Q&A-Fragefeld ist im Power BI-Dienst („app.powerbi.com“) in Dashboards und Berichten verfügbar. Die folgenden Schritte beschreiben das Erstellen einer Karte aus einem Dashboard im Power BI-Dienst. Wenn Sie in Power BI Desktop eine Karte mit Q&A erstellen möchten, [folgen Sie diesen Anweisungen](https://powerbi.microsoft.com/en-us/blog/power-bi-desktop-december-feature-summary/#QandA) für die Q&A-Vorschau von Desktop-Berichten.

1. Erstellen Sie ein [Dashboard](service-dashboards.md) und [rufen Sie Daten ab](service-get-data.md). Hier wird das [Beispiel zur Opportunityanalyse](sample-opportunity-analysis.md) verwendet.

1. Geben Sie oben auf Ihrem Dashboard im Fragefeld ein, was Sie über Ihre Daten wissen möchten. 

   ![](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

>**TIPP**: Wählen Sie in einem Bericht im Power BI-Dienst in der [Bearbeitungsansicht](service-reading-view-and-editing-view.md) in der oberen Menüleiste **Frage stellen** aus. Suchen Sie in einem Power BI Desktop-Bericht eine freie Stelle, und doppelklicken Sie, um ein Fragefeld anzuzeigen.

3. Geben Sie z. B. „Anzahl Verkaufschancen“ in das Fragefeld ein.

   ![](media/power-bi-visualization-card/power-bi-q-and-a.png)

   Im Fragefeld werden Vorschläge und Formulierungsalternativen angezeigt. Schließlich sehen Sie hier die Gesamtanzahl.  
4. Wählen Sie das Anheftsymbol ![](media/power-bi-visualization-card/pbi_pintile.png) rechts oben aus, um die Karte zum Dashboard hinzuzufügen.

   ![](media/power-bi-visualization-card/power-bi-pin.png)
5. Heften Sie die Karte als Kachel an ein vorhandenes oder neues Dashboard an.

   * Vorhandenes Dashboard: Wählen Sie den Namen des Dashboards aus der Dropdownliste aus. Sie können nur die Dashboards innerhalb des aktuellen Arbeitsbereichs auswählen.
   * Neues Dashboard: Geben Sie den Namen des neuen Dashboards ein. Dieses wird anschließend dem aktuellen Arbeitsbereich hinzugefügt.
6. Wählen Sie **Anheften**aus.

   Eine Erfolgsmeldung (in der Nähe der oberen rechten Ecke) weist Sie darauf hin, dass die Visualisierung als Kachel zu Ihrem Dashboard hinzugefügt wurde.  

   ![](media/power-bi-visualization-card/power-bi-success.png)
7. Wählen Sie **Zum Dashboard wechseln**, um die neue Kachel anzuzeigen. Dort können Sie es u.a. [umbenennen, die Größe ändern, einen Link hinzufügen und die Kachel auf dem Dashboard verschieben](service-dashboard-edit-tile.md).

   ![](media/power-bi-visualization-card/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
- Wenn kein Fragefeld angezeigt wird, wenden Sie sich an den System- oder Mandantenadministrator.    
- Wenn Sie die Desktop-Version verwenden und beim Klicken an eine leere Stelle im Bericht Q&A nicht geöffnet wird, müssen Sie diese Funktion möglicherweise aktivieren.  Wählen Sie **Datei > Optionen und Einstellungen > Optionen > Vorschaufeatures > Q&A** aus, und starten Sie Power BI Desktop neu.


## <a name="next-steps"></a>Nächste Schritte
[Dashboardkacheln in Power BI](service-dashboard-tiles.md)

[Dashboards in Power BI](service-dashboards.md)

[Power BI – Grundkonzepte](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)