---
title: Flächenkartogramme (Choroplethenkarten) in Power BI
description: Dokumentation zum Erstellen von Flächenkartogrammen (Choroplethenkarten) in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2fa8fa5248ee1e4330804205b2cedb64021b1913
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839756"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Flächenkartogramme (Choroplethenkarten) in Power BI
In einem Flächenkartogramm wird mithilfe von Schattierungen, Farben oder Mustern angezeigt, in welchem Verhältnis Werte innerhalb eines geografischen Gebiets stehen.  Diese relativen Unterschiede werden mithilfe von Schattierungen angezeigt, wobei hell eine geringe Menge/Häufigkeit und dunkel eine große Menge/Häufigkeit anzeigt.    

![Karte der USA](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>An Bing gesendete Informationen
Power BI arbeitet mit Bing zusammen, um Standardkartenkoordinaten bereitzustellen (ein Prozess, der als Geocodierung bezeichnet wird). Wenn Sie im Power BI-Dienst oder in Power BI Desktop eine Kartenvisualisierung erstellen, werden die Daten in den Buckets **Standort**, **Breitengrad** und **Längengrad** (die dazu verwendet werden, diese Visualisierung zu erstellen) an Bing gesendet.

Sie oder der Administrator müssen möglicherweise die Firewall aktualisieren, um den Zugriff auf die von Bing für die Geocodierung verwendeten URLs zuzulassen.  Diese URLs lauten:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Weitere Informationen zu den an Bing gesendeten Daten sowie Tipps für eine erfolgreichere Geocodierung finden Sie unter [Tipps und Tricks für Power BI-Kartenvisualisierungen](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Einsatz von Flächenkartogrammen
Flächenkartogramme sind gut für folgende Zwecke geeignet:

* Zum Anzeigen quantitativer Informationen auf einer Karte
* Zum Anzeigen räumlicher Muster und Beziehungen
* Bei standardisierten Daten
* Bei der Arbeit mit sozioökonomischen Daten
* Wenn bestimmte Regionen von Bedeutung sind
* Für einen Überblick in Bezug auf die Verteilung über geografische Standorte hinweg

### <a name="prerequisites"></a>Voraussetzungen
- Power BI-Dienst oder Power BI Desktop
- Sales and Marketing Sample

Im Tutorial wird der Power BI-Dienst und nicht Power BI Desktop verwendet.

## <a name="create-a-basic-filled-map"></a>Erstellen eines grundlegenden Flächenkartogramms
In diesem Video wird eine einfache Karte erstellt und in ein Flächenkartogramm umgewandelt.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>Abrufen von Daten und Hinzufügen einer neuen leeren Seite zu dem Bericht
1. Um ein eigenes Flächenkartogramm zu erstellen, [laden Sie das Beispiel für Vertrieb und Marketing herunter](../sample-datasets.md). Melden Sie sich zu diesem Zweck bei Power BI an, und wählen Sie **Daten abrufen \> Beispiele \> Vertrieb und Marketing\> Verbinden** aus. Sie können die **Power BI Sales and Marketing**-App auch auf appsource.com abrufen. 

2. Öffnen Sie den Bericht „Sales and Marketing“.

   ![Der Bericht „Sales and Marketing“ wird geöffnet.](media/power-bi-visualization-filled-maps-choropleths/power-bi-report-canvas.png)
3. Power BI öffnet den Bericht. Klicken Sie auf **Bericht bearbeiten**, um den Bericht in der [Bearbeitungsansicht](../service-interact-with-a-report-in-editing-view.md) zu öffnen.

4. Fügen Sie eine neue Seite hinzu, indem Sie auf das gelbe Pluszeichen am unteren Rand des Zeichenbereichs klicken.

    ![Registerkarte „Bericht“](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>Erstellen eines Flächenkartogramms
1. Wählen Sie im Bereich „Felder“ das Feld **Geo** \> **Bundesstaat** aus.    

   ![Häkchen im gelben Kontrollkästchen neben „State“](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
5. [Wandeln Sie das Diagramm](power-bi-report-change-visualization-type.md) in ein Flächenkartogramm um. Beachten Sie, dass sich **Bundesstaat** jetzt im Bereich **Standort** befindet. Bing Maps verwendet das Feld unter **Standort**bereich, um die Karte zu erstellen.  Gültige Orte umfassen z. B. Länder, Bundesländer, Landkreise, Städte, Postleitzahlen usw. Bing Maps bietet verschiedene Formen für Orte auf der ganzen Welt. Ohne einen gültigen Wert im Bereich „Ort“ kann Power BI kein Flächenkartogramm erstellen.  

   ![Vorlagen mit dem hervorgehobenen Symbol für Flächenkartogramme](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filtern Sie die Karte, um nur die kontinentalen USA anzuzeigen.

   a.  Suchen Sie im unteren Teil des Visualisierungsbereichs nach **Filter** .

   b.  Zeigen Sie auf **Bundesland** , und klicken Sie auf das Erweiterungssymbol.  
   ![Filter auf visueller Ebene zeigt „State(All)“ an](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Aktivieren Sie das Kontrollkästchen **Alle**, und deaktivieren Sie das Kontrollkästchen **AK**.

   ![Dropdownliste für State, in der die Optionen „All“ und „AK“ nicht ausgewählt ist](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Wählen Sie **SalesFact** \> **Stimmung**, um diese Option zum Bereich **Farbsättigung** hinzuzufügen. Das Feld im Bereich **Farbsättigung** steuert die Schattierung der Karte.  
   ![Sentiment im Feld für die Farbsättigung](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map.png)
8. Das Flächenkartogramm ist grün und rot schattiert. Rot steht dabei für schlechtere und grün für bessere (d.h. positive) Stimmungsdaten.  Wenn Sie Wyoming (WY) markieren, sehen Sie, dass dieser Bundesstaat über einen positiven Stimmungswert (74) verfügt.  
   ![Schwarzes Dialogfeld zeigt „State“ und „Sentiment“](media/power-bi-visualization-filled-maps-choropleths/power-bi-wy.png)
9. [Speichern Sie den Bericht](../service-report-save.md).
##    <a name="adjust-the-color-formatting"></a>Anpassen der Farbformatierung
Mithilfe von Power BI können Sie die Darstellung Ihres Flächenkartogramms umfassend steuern.
1. Wählen Sie das Farbrollersymbol aus, um den Bereich „Formatierung“ zu öffnen.

    ![Formatierungsbereich](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-colors.png)

2. Klicken Sie auf **Datenfarben**, um die Farboptionen anzuzeigen.
3. Legen Sie die Mindest- und Maximalfarben auf gelb und blau fest. Fügen Sie anschließend basierend auf Ihren Daten die Mindest- und Maximalfarben hinzu. Verschieben Sie die Steuerelemente, bis Ihnen das Ergebnis gefällt. 

    ![Abweichende Farben](media/power-bi-visualization-filled-maps-choropleths/power-bi-color.png)

## <a name="highlighting-and-cross-filtering"></a>Hervorheben und Kreuzfiltern
Informationen zur Verwendung des Filterbereichs finden Sie unter [Hinzufügen eines Filters zu einem Bericht in Power BI](../power-bi-report-add-filter.md).

Das Markieren eines Orts in einem Flächenkartogramm ermöglicht das Kreuzfiltern anderer Visualisierungen auf der Berichtsseite – und umgekehrt.

1. Speichern Sie zunächst den Bericht, indem Sie auf **Datei > Speichern** klicken. 

2. Kopieren Sie das Flächenkartogramm, indem Sie STRG+C drücken.

3. Klicken Sie unten im Berichtsbereich auf die Registerkarte **Stimmung**, um die Seite mit dem Stimmungsbericht zu öffnen.

    ![Registerkarte „Stimmung“: ausgewählt](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Bewegen Sie die Visuals auf der Seite, und ändern Sie deren Größe, um Platz zu schaffen. Drücken Sie anschließend STRG+V, um das Flächenkartogramm aus dem vorherigen Bericht einzufügen.

   ![Flächenkartogramm zur Seite „Stimmung“ hinzugefügt](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Wählen Sie auf dem Flächenkartogramm einen Bundesstaat aus.  Dadurch werden die anderen Visualisierungen auf der Seite hervorgehoben. Wenn Sie hier beispielsweise **Texas** auswählen, sehen Sie, dass der Stimmungswert bei 74 liegt. Texas befindet sich im Central District \#23.   
   ![Texas ausgewählt](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Wählen Sie in dem Liniendiagramm „VanArsdel - Sentiment by Month“ (VanArsdel – Stimmung nach Monat) aus. Dadurch wird das Flächenkartogramm gefiltert, sodass nur die Stimmungsdaten für VanArsdel und nicht für die Konkurrenz angezeigt werden.  
   ![Neue Schattierung](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
Kartendaten sind unter Umständen nicht eindeutig.  Neben Paris in Frankreich gibt es auch noch ein Paris in Texas. Ihre geografischen Daten sind wahrscheinlich in separaten Spalten gespeichert – eine Spalte für den Ortsnamen, eine Spalte für den Namen des Bundeslands oder des Landkreises usw. Für Bing ist es daher nicht eindeutig, welches Paris gemeint ist. Wenn das Dataset bereits Daten für die Breiten- und Längengrade enthält, umfasst Power BI spezielle Felder, mithilfe derer die Kartendaten eindeutig zugeordnet werden können. Ziehen Sie das Feld mit den Breitengraddaten in den Bereich „Visualisierungen \> Breitengrad“.  Führen Sie für den Längengrad die gleichen Schritte aus.    

![Bereiche für Visualisierungen und Felder](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Wenn Sie zum Bearbeiten des Datasets in Power BI Desktop berechtigt sind, erfahren Sie in diesem Video, wie Sie Mehrdeutigkeiten in Karten beheben.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

[Führen Sie zum Aktualisieren des Datasets diese Anweisungen aus](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7), wenn Sie zwar über Bearbeitungszugriff für das Dataset, aber nicht über Zugriff auf die Breiten- und Längengraddaten verfügen.

Weitere Hilfe zu Kartenvisualisierungen finden Sie unter [Tipps und Tricks für Kartenvisualisierungen](../power-bi-map-tips-and-tricks.md).

## <a name="next-steps"></a>Nächste Schritte

[Formenzuordnung](desktop-shape-map.md)

[Visualisierungstypen in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)