---
title: Zertifizierte Power BI-Visuals
description: Anforderungen und Vorgehensweise für das Einreichen eines benutzerdefinierten Visuals zur Zertifizierung Sowie eine Liste bereits zertifizierter Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: maghan
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 05/9/2019
ms.openlocfilehash: d806a0ed35a6e8270a154708279faacefeb6e510
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195716"
---
# <a name="get-a-power-bi-visual-certified"></a>So lassen Sie sich ein Power BI-Visual zertifizieren

## <a name="what-are-_certified_-power-bi-visuals"></a>Was sind **_zertifizierte_** Power BI-Visuals?

Zertifizierte Power Bi-Visuals sind Visuals im **Marketplace**, die bestimmte **festgelegte Codeanforderungen** erfüllen, die vom **Microsoft Power BI-Team** getestet und genehmigt wurden. Sobald ein benutzerdefiniertes Visual zertifiziert wurde, bietet es mehr Funktionen. Beispielsweise können Sie [PowerPoint exportieren](consumer/end-user-powerpoint.md) und das Visual in E-Mails anzeigen, die Sie erhalten, wenn ein Benutzer [Berichtsseiten abonniert](consumer/end-user-subscribe.md).

**Zertifizierte Power BI-Visuals** werden genauso wie [Standardvisuals für Power BI](power-bi-custom-visuals.md) verwendet. Zertifizierte Power BI-Visuals können dem **Power BI-Dienst** oder einem **Power BI Desktop-Bericht** hinzugefügt werden und in **Power BI Mobile** sowie **Power BI Embedded** angezeigt werden.

Die durchgeführten Tests wurden entworfen, um zu überprüfen, ob das Visual nicht auf externe Dienste oder Ressourcen zugreift. **Microsoft** ist *nicht* der Autor von Power BI-Visuals von Drittanbietern, und Kunden wird empfohlen, direkt mit dem Autor Kontakt aufzunehmen, um die Funktionalität eines solchen Visuals zu überprüfen.

Dieser Zertifizierungsprozess ist ein optionaler Prozess, und es obliegt den Entwicklern zu entscheiden, ob ihr Visual im Marketplace zertifiziert werden soll.  

**Nicht zertifizierte Power BI-Visuals** sind nicht zwangsläufig unsicher. Einige Visuals sind nicht zertifiziert, da sie mindestens einem Punkt der [Zertifizierungsanforderungen](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) nicht entsprechen. Beispiele hierfür sind die Herstellung einer Verbindung zu einem externen Dienst wie Kartenvisuals oder Visuals, die kommerzielle Bibliotheken verwenden.

Sind Sie Webentwickler und möchten eigene Visualisierungen erstellen und zu  **[Microsoft AppSource](https://appsource.microsoft.com)** hinzufügen? Weitere Informationen finden Sie unter  **[Entwickeln eines benutzerdefinierten Visuals für Power BI](developer/custom-visual-develop-tutorial.md)** .

## <a name="removal-of-power-bi-certified-power-bi-visuals"></a>Entfernen von Power BI-Visuals mit Power BI-Zertifizierung

Microsoft kann nach eigenem Ermessen ein Visual aus der Liste [zertifizierter Visuals](#list-of-power-bi-visuals-that-have-been-certified) entfernen.

## <a name="getting-a-custom-visualcertified"></a>Abrufen eines zertifizierten benutzerdefinierten Visuals

### <a name="certification-requirements"></a>Zertifizierungsanforderungen

Stellen Sie sicher, dass Ihr benutzerdefiniertes Visual folgenden Anforderungen entspricht, damit es [zertifiziert](#get-a-power-bi-visual-certified) werden kann:  

* Es muss von Microsoft AppSource genehmigt sein. Ihr benutzerdefiniertes Visual sollte sich in unserem [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) befinden.
* Das benutzerdefinierte visuelle Element wurde mit der **API-Version 2.5** oder höher geschrieben.
* Das Coderepository muss dem Power BI-Team zur Überprüfung zur Verfügung stehen (z.B. Quellcode – JavaScript oder TypeScript – in einem uns verfügbaren Format in GitHub, das für Menschen lesbar ist).

    >[!Note]
    > Sie müssen Ihren Code nicht öffentlich in GitHub freigeben.
* Coderepository-Anforderungen:
   * Der minimal erforderliche Satz von Dateien muss enthalten sein:
      * .gitignore
      * capabilities.json
      * pbiviz.json
      * package.json
      * package-lock.json
      * tsconfig.json
   * Der Ordner „node_modules“ darf nicht enthalten sein (fügen Sie „node_modules“ der GITIGNORE-Datei hinzu)
   * Der **npm install**-Befehl darf keine Fehler zurückgeben.
   * Der **npm audit**-Befehl darf keine Warnungen mit hoher oder mittlerer Stufe zurückgeben.
   * Der **pbiviz package**-Befehl darf keine Fehler zurückgeben.
   * [TSlint from Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) muss ohne außer Kraft gesetzte Konfigurationen enthalten sein, und dieser Befehl darf keine lint-Fehler zurückgeben.
   * Das kompilierte Paket des benutzerdefinierten visuellen Elements muss mit dem gesendeten Paket übereinstimmen (die md5-Hashwerte beider Dateien sollten gleich sein).
* Quellcode-Anforderungen:
   * Das visuelle Element muss die [Rendering Events-API](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/) unterstützen.
   * Stellen Sie sicher, dass kein beliebiger/dynamischer Code ausgeführt wird (bad: eval(), unsafe to use of settimeout(), requestAnimationFrame(), setinterval(eine Funktion mit Benutzereingaben), Ausführen von Benutzereingaben/-daten).
   * Stellen Sie sicher, dass DOM sicher bearbeitet wird (bad: innerHTML, D3.html(<Benutzer-/Dateneingabe>), Bereinigung für Benutzereingaben/Daten vor dem Hinzufügen zum DOM verwenden).
   * Stellen Sie sicher, dass es in der Browserkonsole keine JavaScript-Fehler/-Ausnahmen für Eingabedaten gibt. Benutzer verwenden Ihr visuelles Element möglicherweise mit einem anderen, unerwarteten Datenbereich, dabei darf das visuelle Element nicht versagen. Sie können [diesen Beispielbericht](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) als Testdataset verwenden.

* Wenn Eigenschaften in „capabilities.json“ geändert werden, stellen Sie sicher, dass sie nicht zu Störungen bei vorhandenen Benutzerberichten führen.

* Achten Sie darauf, dass das visuelle Element die [Richtlinien für Power BI-Visuals](https://docs.microsoft.com/en-us/power-bi/developer/guidelines-powerbi-visuals#guidelines-for-power-bi-visuals-with-additional-purchases) einhält. **Wasserzeichen sind nicht zulässig**.

* Ihr Visual darf nur öffentlich überprüfbare OSS-Komponenten besitzen (öffentliche JS-Bibliotheken oder TypeScript. Der Quellcode ist für die Überprüfung verfügbar und besitzt keine bekannten Sicherheitsrisiken). Wir können überprüfen, ob ein benutzerdefiniertes Visual eine kommerzielle Komponente verwendet.

* Das Visual greift nicht auf externe Dienste oder Ressourcen zu. Unter anderem gehen keine HTTP/S- oder WebSocket-Anforderungen von Power BI oder anderen Diensten aus. 

> [!TIP]
> Es wird empfohlen, dass Sie EsLint mit dem standardmäßigen verwendeten Sicherheitsregelsatz nutzen, um Ihren Code vor der Einreichung zu überprüfen.

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Vorgang zum Einreichen eines benutzerdefinierten visuellen Elements zur Zertifizierung

So reichen Sie ein benutzerdefiniertes visuelles Element zur Zertifizierung ein

1. Senden Sie eine E-Mail an den Power BI-Support für Power BI-Visuals (pbicvsupport@microsoft.com). Fügen Sie der E-Mail die folgende Informationen hinzu:
    * Titel: Zertifizierungsanforderung für Visual
    * Link zum GitHub-Repository, in dem der vom Menschen lesbare Quellcode gehostet wird
    * [Befolgen der Anforderungen](#certification-requirements)
    * Übergeben des Codereviews

2. Das Microsoft-Team für Power BI-Visuals benachrichtigt Sie, sobald Ihr benutzerdefiniertes Visual zertifiziert und der [Liste der zertifizierten Visuals](#list-of-power-bi-visuals-that-have-been-certified) hinzugefügt wurde oder mit einem Bericht zu den zu behebenden Problemen abgelehnt wurde. Es ist Aufgabe des Entwicklers, eine offene Kommunikation mit Microsoft zu pflegen und seine zertifizierten Visuals bei Bedarf zu aktualisieren.

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Liste der Power BI-Visuals mit Zertifizierung

| Link zu AppSource | Link zum Video |
| --- | --- |
| [3AG Systems – Bar Chart With Relative Variance (3AG Systems: Balkendiagramm mit relativer Varianz)](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [3AG Systems – Column Chart With Relative Variance (3AG Systems: Säulendiagramm mit relativer Varianz)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [Advanced Donut Visual (Erweitertes Ringdiagrammvisual)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [Advanced Network Visualization (Erweiterte Netzwerkvisualisierung)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [Advanced TimeSeries Visual (Erweitertes TimeSeries-Visual)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [Advanced Combo Visual (Erweitertes Combovisual)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [Aster-Plot](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft-Kalender](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Schleifendiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Video](https://youtu.be/So5xKMSpVJI) |
| [Kastengrafikdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Kastengrafikdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Video](https://youtu.be/JoHaFLfhXdo) |
| [Ziegeldiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Video](https://youtu.be/hA3DOsvn2xY) |
| [Blasendiagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Bullet-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Video](https://youtu.be/AOlsFYkfkcw) |
| [Bullet-Diagramm von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Video](https://youtu.be/mtvUNl9bMjA) |
| [Kalender von Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Kerzendiagramm von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Video](https://youtu.be/nT_18gyRxPo) |
| [Karte mit Zuständen von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet-Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Video](https://youtu.be/AQvd2FhRyCI) |
| [Kreisförmiges Messgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Video](https://youtu.be/9NHXALkBXuY) |
| [Clusterzuordnung](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Zylindrisches Messgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Video](https://youtu.be/DgdoWi7Gcxo) |
| [Messuhrdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Punktdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Punktdiagramm von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Video](https://youtu.be/By16pX9KT40) |
| [Drilldown-Kartogramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Drilldown-Choroplethenkarte](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Drilldown-Säulendiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Video](https://youtu.be/lBy2gQQ5YsQ) |
| [Drilldown-Säulendiagramm für zeitbasierte Daten](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Video](https://youtu.be/T_mRou18vx0) |
| [Drilldown-Ringdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Video](https://youtu.be/AUVFrSHmPeo) |
| [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamic Tooltip von MAQ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [Video](https://youtu.be/Z-tl97BpEr0) |
| [Erweitertes Punktdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Video](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten-Waffeldiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filtern nach Liste von Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Video](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Video](https://youtu.be/YsTa7uyJ4sg) |
| [Trichterdiagramm mit Quelle von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Video](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Video](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt-Diagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Video](https://youtu.be/vJLV9JRCpI8) |
| [Globe Data Bars](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Grid by MAQ Software (Raster von MAQ Software)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Video](https://youtu.be/VOPoDJgZfOY) |
| [Hierarchiediagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Video](https://youtu.be/0ZGzJaq_KT4) |
| [Histogramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Histogramm mit Punkten von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Video](https://youtu.be/-ILF--wExrw) |
| [Horizontales Trichterdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Video](https://youtu.be/SudZei68PPo) |
| [Bild von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Bildraster](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Designer für Infografiken](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [KPI-Diagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [KPI Column von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Video](https://youtu.be/rU0xoOlIq1U) |
| [KPI-Raster von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Video](https://youtu.be/dM4PvZh71V0) |
| [KPI-Indikator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [KPI-Ticker von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Video](https://youtu.be/cudG4gsZ2V8) |
| [Linearmessgerät von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Video](https://youtu.be/7_jFaM30dkc) |
| [LineDot-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Video](https://youtu.be/90FLCKpgicA) |
| [Multi-KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Overview von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Wiedergabeachse (dynamischer Slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Video](https://youtu.be/IvfIP3E6-1Q) |
| [Power-KPI-Matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Video](https://youtu.be/1enze8pcGzY) |
| [Pulse-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Video](https://youtu.be/DQWdcQtjDVw) |
| [Quadrant Chart by MAQ Software (Quadrant-Diagramm von MAQ Software)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Video](https://youtu.be/ppBnyhqWNC0) |
| [Netzdiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Ringdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Video](https://youtu.be/pDToHDFHnq8) |
| [Drehbares Diagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Video](https://youtu.be/d5xBCMmb3hU) |
| [Sankey-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Video](https://youtu.be/WWP9wVUHGaA) |
| [Punktdiagramm von Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Scroller](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Intelligenter Filter von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Video](https://youtu.be/gcJsDDRQq28) |
| [Sparkline von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Video](https://youtu.be/0m3Vnvso9tY) |
| [Stream-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Synoptic Panel von OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Tabellenheatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Video](https://youtu.be/C3OXdETbS9o) |
| [Textfilter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Text-Wrapper von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Thermometer von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Video](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush-Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Timeline-Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Video](https://youtu.be/ozMtZ4_NZ10) |
| [Timeline von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Video](https://youtu.be/szNi9YgXFJc) |
| [Tornado-Diagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Video](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Handelsdiagramm von MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Video](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimative Varianz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Video](https://youtu.be/pDYF8iZxERs) |
| [Ultimatives Wasserfalldiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Video](https://youtu.be/0BZsVCQdEkc) |
| [Benutzerliste von CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Waffeldiagramm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Video](https://youtu.be/1vRqYUsm3Vk) |
| [Wortwolke](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Video](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>HÄUFIG GESTELLTE FRAGEN

Weitere Informationen zu Visuals finden Sie in den [häufig gestellten Fragen zu zertifizierten Visuals](#get-a-power-bi-visual-certified).

## <a name="next-steps"></a>Nächste Schritte

* [Entwickeln eines benutzerdefinierten Visuals für Power BI](developer/custom-visual-develop-tutorial.md)
* [Wiedergabeliste benutzerdefinierter visueller Elemente von Microsoft auf YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisierungen in Power BI](visuals/power-bi-report-visualizations.md)  
* [Benutzerdefinierte Visualisierungen in Power BI](power-bi-custom-visuals.md)  
* [Veröffentlichen von Power BI-Visuals in Microsoft AppSource](developer/office-store.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
