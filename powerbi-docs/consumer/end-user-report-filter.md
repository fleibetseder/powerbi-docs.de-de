---
title: Überblick über den Berichtsbereich „Filter“
description: Hinzufügen eines Filters zu einem Bericht im Power BI-Dienst für Nutzer
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532784"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Überblick über den Berichtsbereich „Filter“

Dieser Artikel befasst sich mit dem Berichtsbereich **Filter** im Power BI-Dienst. Sie können Filter verwenden, um neue Erkenntnisse zu Ihren Daten zu gewinnen.

Es gibt viele verschiedene Wege, Daten in Power BI zu filtern. Weitere Informationen zu Filtern finden Sie unter [Filters and highlighting in Power BI reports (Filter und Hervorhebungen in Power BI-Berichten)](../power-bi-reports-filters-and-highlighting.md).

![Screenshot: Bericht im Browser mit einem Pfeil, der auf die Option „Filter“ zeigt](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Arbeiten mit dem Bereich „Filter“ in Berichten

Wenn ein Kollege einen Bericht mit Ihnen teilt, suchen Sie immer nach dem Bereich **Filter**. Manchmal befindet er sich zugeklappt am rechten Rand des Berichts. Klicken Sie darauf, um ihn aufzuklappen.

![Screenshot: Bericht mit erweitertem Bereich „Filter“](media/end-user-report-filter/power-bi-filter-pane.png)

Der Bereich **Filter** enthält Filter, die der *Berichts-Designer* zum Bericht hinzugefügt hat. *Berichtsnutzer* wie Sie können mit den vorhandenen Filtern interagieren und ihre Änderungen speichern, aber keine neuen Filter zum Bericht hinzufügen. Auf dem obigen Screenshot hat der Designer beispielsweise zwei Filter auf Seitenebene hinzugefügt: **Segment** und **Year** (Jahr). Sie können mit diesen Filtern interagieren und sie ändern, Sie können jedoch keinen dritten Filter auf Seitenebene hinzufügen.

Berichte behalten alle Änderungen bei, die Sie im Bereich **Filter** vornehmen. Der Dienst überträgt diese Änderungen auch in die mobile Version des Berichts.

Sie können den Bereich **Filter** auf die Standardwerte des Designers zurücksetzen, indem Sie auf ![Screenshot: Option „Auf Standardwert zurücksetzen“](media/end-user-report-filter/power-bi-reset.png) in der oberen Menüleiste klicken.

## <a name="view-all-the-filters-for-a-report-page"></a>Anzeigen aller Filter einer Berichtsseite

Der Bereich **Filter** zeigt alle Filter an, die der Designer zum Bericht hinzugefügt hat. Im Bereich **Filter** können Sie außerdem Informationen zu den Filtern anzeigen und mit ihnen interagieren. Sie können Ihre Änderungen speichern oder **Auf Standardwert zurücksetzen** verwenden, um die ursprünglichen Filtereinstellungen wiederherzustellen.

Wenn Sie Änderungen speichern möchten, können Sie auch ein persönliches Lesezeichen erstellen.  Weitere Informationen finden Sie unter [What are bookmarks? (Was sind Lesezeichen?)](end-user-bookmarks.md).

Im Bereich **Filter** werden mehrere Arten von Berichtsfiltern angezeigt und verwaltet. Diese können auf ein Visual, eine Berichtsseite oder auf den gesamten Bericht angewendet werden.

In diesem Beispiel wurde ein Visual mit zwei Filtern ausgewählt. Außerdem wurden Filter auf die Berichtsseite angewendet, die unter **Filter für diese Seite** aufgeführt werden. Darüber hinaus wurde auf den gesamten Bericht der Filter **Date** (Datum) angewendet.

![Screenshot: Bericht mit einem Visual und den zugehörigen Filtern hervorgehoben](media/end-user-report-filter/power-bi-all-filters2.png)

Neben einigen der Filter steht **(All)** (Alle). **(All)** (alle) bedeutet, dass alle Werte im Filter enthalten sind. Im obigen Screenshot wird mit **Segment (All)** angegeben, dass diese Berichtsseite Daten zu allen Produktsegmenten enthält. Wenn Sie den Filter auf Seitenebene **Region is West** (Region ist Westen) auswählen, enthält die Berichtsseite nur die Daten für die Region „Westen“.

Jeder, der den Bericht aufruft, kann auch mit den Filtern interagieren.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Ausschließliches Anzeigen der auf ein Visual angewendeten Filter

Sie können sich die Filter eines spezifischen Visuals genauer ansehen, indem Sie auf das Visual zeigen, um das Filtersymbol aufzudecken ![Screenshot: Filtersymbol](media/end-user-report-filter/power-bi-filter-icon.png). Klicken Sie auf das Filtersymbol, um ein Popupfenster mit allen Filtern, Datenschnitten usw. zu öffnen, die auf das Visual angewendet wurden. Die Filter im Popupfenster sind die gleichen, die auch im Bereich **Filter** aufgeführt werden.

![Screenshot: Liste der Filter mit Pfeilen, die auf die gleichen Filter im Filterbereich zeigen.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Die folgenden Filter können in dieser Ansicht angezeigt werden:

- Basisfilter

- Datenschnitte

- Übergreifende Hervorhebung

- Kreuzfilterung

- Erweiterte Filter

- Top N-Filter

- Relative Datenfilter

- Synchronisierungsslicer

- Einschluss-/Ausschlussfilter

- Per URL übergebene Filter

Im folgenden Beispiel:

1. können Sie sehen, dass Kreuzfilter auf das Säulendiagramm angewendet wurden.

1. gibt **Included** (Enthalten) an, dass die Kreuzfilterung für **Segment** gilt und dass drei enthalten sind.

1. wurde ein Datenschnitt für **Quarter** (Quartal) angewendet.

1. ist **Region** ein Filter, der auf die Berichtsseite angewendet wurde, und

1. **isVanArsdel** und **Year** (Jahr) sind Filter, die auf das Visual angewendet wurden.

![Screenshot: Bericht und Filter mit der Liste der Filter gemäß der obigen Liste nummeriert](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Suche in einem Filter

Manchmal kann ein Filter eine lange Liste von Werten aufweisen. Verwenden Sie das Suchfeld, um den gewünschten Wert zu finden und auszuwählen.

![Screenshot: Suchen in einem Filter](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Anzeigen von Filterdetails

Sehen Sie sich die verfügbaren Werte und Zahlen an, um einen Filter zu verstehen.  Sie können die Details zu einem Filter anzeigen, indem Sie auf den Pfeil neben dem Namen eines Filters klicken.
  
![Screenshot: Filter mit ausgewählter Region „West“ (Westen)](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Ändern der Filterauswahl

Eine Möglichkeit zum Ermitteln von Erkenntnissen zu Daten besteht darin, mit Filtern zu interagieren. Sie können die Filterauswahl mithilfe des Dropdownpfeils neben dem Feldnamen ändern.  Je nach Filter und Datentyp, der von Power BI gefiltert wird, reichen Ihre Optionen von der einfacher Auswahl aus einer Liste bis zum Identifizieren von Datumsbereichen oder Zahlen. Im folgenden erweiterten Filter wurde der Filter **Total Units YTD** (Gesamtanzahl der Einheiten seit Jahresbeginn) für das Kacheldiagramm auf den Bereich von 2.000 bis 3.000 beschränkt. Beachten Sie, dass Prirum aufgrund dieser Änderung aus dem Kacheldiagramm entfernt wurde.
  
![Screenshot: Bericht und Filter mit hervorgehobenen Filtereinstellungen](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Halten Sie die STRG-TASTE gedrückt, um mehrere Filterwerte gleichzeitig auszuwählen. Die meisten Filter unterstützen die Auswahl mehrerer Werte.

### <a name="reset-filter-to-default"></a>Zurücksetzen des Filters auf die Standardwerte

Wenn Sie all Ihre Änderungen an den Filtern zurücksetzen möchten, klicken Sie in der oberen Menüleiste auf **Auf Standardwert zurücksetzen**.  Dadurch werden die Filter wieder in den ursprünglichen Zustand versetzt, den der Berichts-Designer festgelegt hat.

![Screenshot: Option „Auf Standardwert zurücksetzen“.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Löschen eines Filters

Wenn Sie nur einen Filter auf **(All)** (alle) festlegen möchten, können Sie die Filter löschen, indem Sie auf das Radierersymbol ![Screenshot: Radierersymbol](media/end-user-report-filter/power-bi-eraser-icon.png) neben dem Filternamen klicken.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie und wieso Sie [Kreuzfilterung und Kreuzhervorhebung für Visuals auf einer Berichtsseite ausführen](end-user-interactions.md).