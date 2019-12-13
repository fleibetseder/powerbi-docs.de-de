---
title: Power BI-Visualkonzepte
description: In diesem Artikel wird beschrieben, wie Visuals in Power BI integriert werden.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700844"
---
# <a name="power-bi-visual-concept"></a>Power BI-Visualkonzepte

In diesem Artikel wird erläutert, wie ein Benutzer und ein Visual mit Power BI interagieren und wie ein Benutzer mit Power BI-Visuals interagiert. Im Diagramm sehen Sie, wie Aktionen des Benutzers bzw. Power BI direkt Einfluss auf das Visual nehmen (z. B. wenn der Benutzer Lesezeichen hinzufügen).

![Power BI-Visual](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>Aktualisieren des Visuals durch Power BI

Das Visual verfügt über die `update`-Methode, die normalerweise die Hauptlogik des Visuals enthält und für das Rendern von Diagrammen bzw. Visualisieren der Daten verantwortlich ist.

Weitere Updates werden über die `update`-Methode abgerufen.

### <a name="user-interacts-with-visual-through-power-bi"></a>Der Benutzer interagiert über Power BI mit Visuals.

* Der Benutzer öffnet den Bereich für Visualeigenschaften.

    Power BI ruft die unterstützten Objekte und Eigenschaften des `capabilities.json`-Visuals ab und die `enumerateObjectInstances`-Methode des Visuals auf, um die tatsächlichen Werte der Eigenschaften zu erhalten.

    Das Visual muss tatsächliche Werte von Eigenschaften zurückgeben.

    Weitere Informationen finden Sie im Artikel zu den [Funktionen von Visuals](capabilities.md).

* [Der Benutzer ändert die Eigenschaft des Visuals im Bereich „Format“.](../../visuals/power-bi-visualization-customize-title-background-and-legend.md)

    Nachdem der Wert einer Eigenschaft geändert wurde, ruft Power BI die `update`-Methode des Visuals auf und übergibt das `options`-Objekt mit den neuen Werten an die Aktualisierungsmethode.

    Weitere Informationen finden Sie im Artikel zu [Objekten und Eigenschaften von Visuals](objects-properties.md).

* Der Benutzer ändert die Größe des Visual.

    Wenn ein Benutzer die Größe des Visuals ändert, ruft Power BI die `update`-Methode mit einem neuen `option`-Objekt auf. Optionen schachteln das `viewport`-Objekt mit neuer Breite und Höhe des Visuals.

* Der Benutzer wendet einen Filter auf Berichts-, Seiten- oder Visualebene an.

    Power BI filtert die Daten gemäß den Filterbedingungen und ruft die `update`-Methode des Visuals auf, um dem Visual neue Daten zu übergeben.

    Das Visual erhält ein neues Update von `options` mit neuen Daten in einem der geschachtelten Objekte. Dies hängt von der Konfiguration der Zuordnung für die Datenansicht des Visuals ab.

    Weitere Informationen finden Sie im Artikel zu [Zuordnungen für die Datenansicht](dataview-mappings.md).

* Der Benutzer wählt den Datenpunkt in einem anderen Visual des Berichts aus.

    Power BI filtert die ausgewählten Datenpunkte oder hebt diese hervor und ruft die `update`-Methode des Visuals auf.

    Das Visual ruft neue gefilterte Daten oder dieselben Daten mit einem Array von Hervorhebungen ab.

    Weitere Informationen finden Sie im Artikel zum [Hervorheben von Daten in Visuals](highlight.md).

* Der Benutzer wählt im Bereich „Lesezeichen“ des Berichts Lesezeichen aus.

    Hier sind zwei Aktionen möglich:

    1. Power BI ruft die von der `registerOnSelectionCallback`-Methode registrierte Funktion auf, und die Rückruffunktion ruft Arrays von Auswahlmöglichkeiten für das Lesezeichen ab.

    2. Power BI ruft die `update`-Methode mit dem entsprechenden Filterobjekt innerhalb von `options` auf.

    In beiden Fällen muss das Visual den Visualisierungszustand gemäß der empfangenen Auswahl oder dem Filterobjekt ändern.

    Weitere Informationen zu Lesezeichen finden Sie im Artikel zum [Arbeiten mit Lesezeichen](filter-api.md).

    Weitere Informationen zu Filtern finden Sie im Artikel zum [Filtern von Daten in anderen Visuals mit Power BI](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>Direktes Interagieren des Benutzers mit dem Visual

* Der Benutzer zeigt mit dem Mauszeiger auf ein Datenelement.

    Das Visual kann über die API für Power BI-QuickInfos zusätzliche Informationen zum Datenpunkt anzeigen.
    Der Benutzer navigiert mit dem Mauszeiger zu einem Visualelement. Das Visual kann Daten für das QuickInfo-Element verarbeiten und anzeigen.

    Das Visual kann die standardmäßige QuickInfo oder QuickInfos der Berichtsseite anzeigen.

    Weitere Informationen finden Sie in der Anleitung zum [Hinzufügen von QuickInfos](add-tooltips.md).

* Der Benutzer ändert die Visualeigenschaften (z. B. erweitert der Benutzer die Struktur und das Visual speichert den Zustand in den Eigenschaften).

    Das Visual kann mithilfe der Power BI-API Eigenschaftswerte speichern. Dies ist beispielsweise der Fall, wenn der Benutzer mit dem Visual interagiert. Das Visual muss dann die Eigenschaftswerte speichern oder aktualisieren. Das Visual kann hierfür die `presistProperties`-Methode aufrufen.

* Der Benutzer klickt auf einen URL-Link.

    Standardmäßig kann die URL nicht vom Visual geöffnet werden. Das Visual muss die `launchURL`-Methode aufrufen und die URL als Parameter übergeben, um die URL in der neuen Registerkarte zu öffnen.

    Weitere Informationen finden Sie im Artikel zum [Starten der URL-API](launch-url.md).

* Der Benutzer wendet Filter auf das Visual an.

    Das Visual ruft `applyJSONFilter` auf und übergibt die Filterbedingungen an den Filter zum Filtern von Daten in einem anderen Visual.

    Das Visual kann verschiedene Filtertypen verwenden (z. B. „Einfaches Filtern“, „Erweiterte Filterung“ oder „Tupel“).

    Weitere Informationen zu Filtern finden Sie im Artikel zum [Filtern von Daten in anderen Visuals mit Power BI](filter-api.md).

* Der Benutzer klickt auf Elemente im Visual.

    Weitere Informationen zum Auswählen finden Sie unter [Interaktion zwischen Visuals](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>Interaktion des Visuals mit Power BI

* Das Visual fordert mehr Daten von Power BI an.

    Das Visual kann Daten nacheinander verarbeiten. Die API-Methode „FetchMoreData“ fordert das nächste Fragment eines Datasets an.

    Weitere Informationen zu `fetchMoreData` finden Sie unter [Abrufen weiterer Daten aus Power BI](fetch-more-data.md).

* Ereignisdienst

    Power BI kann Berichte in eine PDF-Datei exportieren oder per E-Mail senden (nur zertifizierte Visuals werden unterstützt). Das Visual muss die API zum Rendern von Ereignissen aufrufen, um Power BI zu benachrichtigen, dass das Rendering abgeschlossen ist und in eine PDF-Datei exportiert bzw. per E-Mail versendet werden kann.

    Weitere Informationen finden Sie unter [Exportieren von Berichten aus Power BI in eine PDF-Datei](../../consumer/end-user-pdf.md).

    Hier finden Sie weitere Informationen zum [Rendern von Ereignissen](event-service.md).

## <a name="next-steps"></a>Nächste Schritte

Sind Sie Webentwickler und möchten eigene Visualisierungen erstellen und zu AppSource hinzufügen? Lesen Sie [Entwickeln eines Power BI-Visuals](./custom-visual-develop-tutorial.md), und informieren Sie sich, wie [Power BI-Visuals in AppSource veröffentlicht werden](../office-store.md).
