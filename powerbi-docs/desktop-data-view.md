---
title: Datenansicht in Power BI Desktop
description: Datenansicht in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 8e1babaa39a1f52a06c69dcb9aac2441ca02452b
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761270"
---
# <a name="work-with-data-view-in-power-bi-desktop"></a>Arbeiten mit der Datenansicht in Power BI Desktop
Mit der **Datenansicht** können Sie Daten im **Power BI Desktop-Modell** überprüfen, untersuchen und verstehen. Sie unterscheidet sich von der Anzeige von Tabellen, Spalten und Daten im **Abfrage-Editor**. Mit der Datenansicht sehen Sie die Daten, *nachdem* sie in das Modell geladen wurden.

Wenn Sie Ihre Daten modellieren, möchten Sie möglicherweise sehen, was tatsächlich in einer Tabelle oder Spalte vorhanden ist, ohne eine Visualisierung im Berichtszeichenbereich zu erstellen, und zwar häufig bis auf Zeilenebene. Dies ist besonders nützlich, wenn Sie Measures und berechnete Spalten erstellen oder einen Datentyp oder die Datenkategorie identifizieren müssen.

Sehen Sie sich nun einige der Elemente in der **Datenansicht** näher an.

![Datensicht in Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Symbol für die Datenansicht:** Mit einem Klick auf dieses Symbol gelangen Sie zur Datenansicht zurück.

2. **Datenraster:** Zeigt die ausgewählte Tabelle und alle darin enthaltenen Spalten und Zeilen an. Spalten, die aus der **Berichtsansicht** ausgeblendet sind, sind ausgegraut. Sie können mit der rechten Maustaste auf eine Spalte klicken, um Optionen anzuzeigen.

3. **Menüband „Modellierung“:** Hier können Sie Beziehungen verwalten, Berechnungen erstellen und den Datentyp, das Format und die Datenkategorie für eine Spalte ändern.

4. **Bearbeitungsleiste:** Hier geben Sie DAX-Formeln für Measures und berechnete Spalten ein.

5. **Suche:** Hier können Sie nach einer Tabelle oder Spalte im Modell suchen.

6. **Liste „Felder“:** Hier können Sie eine Tabelle oder Spalte auswählen, die im Datenraster angezeigt werden soll.

## <a name="filtering-in-data-view"></a>Filtern in der Datensicht

Sie können Daten in **Datenansicht** auch filtern und sortieren. In jeder Spalte wird ein Symbol angezeigt, das die Sortierreihenfolge angibt (falls angewendet).

![Sortieren und Filtern in der Datensicht in Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Sie können einzelne Werte filtern oder erweiterte Filter auf Grundlage der Daten in der Spalte verwenden. 

> [!NOTE]
> Wenn ein Power BI-Modell mit einer Kultur erstellt wurde, die nicht der aktuellen Benutzeroberfläche entspricht (z. B. wurde das Modell auf Englisch (USA) erstellt und wird auf Spanisch angezeigt), wird das Suchfeld in der Benutzeroberfläche „Datenansicht“ nur für Textfelder angezeigt.
