---
title: Zertifizierte Power BI-Visuals
description: Anforderungen und Vorgehensweise für das Einreichen eines benutzerdefinierten Visuals zur Zertifizierung Sowie eine Liste bereits zertifizierter Power BI-Visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999742"
---
# <a name="get-a-power-bi-visual-certified"></a>So lassen Sie sich ein Power BI-Visual zertifizieren

Zertifizierte Power Bi-Visuals sind Visuals im *Marketplace*, die bestimmte *festgelegte Codeanforderungen* erfüllen, die vom *Microsoft Power BI-Team* getestet und genehmigt wurden. Mit den Tests wird sichergestellt, dass ein Visual nicht auf externe Dienste oder Ressourcen zugreift.

Zertifizierte Power BI-Visuals und [Power BI-Standardvisuals](power-bi-custom-visuals.md) werden auf die gleiche Weise verwendet. Sie können zu [Power BI Desktop](../desktop-what-is-desktop.md) und dem [Power BI-Dienst](../power-bi-service-overview.md) hinzugefügt und mit [mobilen Power BI-Apps](../consumer/mobile/mobile-apps-for-mobile-devices.md) sowie [Power BI Embedded](embedding.md) angezeigt werden.

Der Zertifizierungsprozess ist optional. Entwickler entscheiden selbst, ob sie ihr Power BI-Visual im Marketplace zertifizieren lassen möchten. Wenn ein Power BI-Visual zertifiziert wurde, bietet es mehr Features. Beispielsweise können Sie ein Visual [nach PowerPoint exportieren](../consumer/end-user-powerpoint.md) oder in empfangenen E-Mails anzeigen, wenn ein Benutzer [Berichtsseiten abonniert](../consumer/end-user-subscribe.md).

Nicht zertifizierte Power BI-Visuals sind nicht zwangsläufig unsicher. Einige Visuals sind nicht zertifiziert, da sie mindestens einem Punkt der [Zertifizierungsanforderungen](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) nicht entsprechen. Beispiele hierfür sind die Herstellung einer Verbindung zu einem externen Dienst wie Kartenvisuals oder Visuals, die kommerzielle Bibliotheken verwenden.

Wenn Sie Webentwickler sind und selbst Power BI-Visuals erstellen und zu [Microsoft AppSource](https://appsource.microsoft.com) hinzufügen möchten, beginnen Sie mit dem Tutorial  [Entwickeln eines Power BI-Visuals](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft** ist *nicht* der Autor von Power BI-Visuals von Drittanbietern. Wir raten Kunden, direkt mit dem Autor eines Drittanbieter-Power BI-Visuals Kontakt aufzunehmen, um die Funktionalität des Visuals zu verifizieren.

> [!IMPORTANT]
> Microsoft kann ein Power BI-Visual nach eigenem Ermessen aus der [Liste zertifizierter Visuals](#list-of-power-bi-visuals-that-have-been-certified) entfernen.

## <a name="certification-requirements"></a>Zertifizierungsanforderungen

Um Ihr Power BI-Visual [zertifizieren](#get-a-power-bi-visual-certified) zu lassen, stellen Sie sicher, dass das Visual die in diesem Abschnitt aufgeführten Anforderungen erfüllt. 

> [!TIP]
> Wir empfehlen die Nutzung von EsLint mit dem standardmäßigen Sicherheitsregelsatz, um Ihren Code vor der Übermittlung vorab zu überprüfen.

* Im Microsoft-Verkäuferdashboard oder in Partner Center genehmigt: Ihr Power BI-Visual sollte sich in unserem [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) befinden.
* Das Power BI-Visual wurde mit der *API-Version 2.5* oder höher geschrieben.
* Das Coderepository kann durch das Power BI-Team überprüft werden. Beispielsweise kann dem Team über GitHub ein lesbares Format des Quellcodes (JavaScript oder TypeScript) zur Verfügung gestellt werden.

    >[!NOTE]
    > Sie müssen Ihren Code nicht öffentlich in GitHub freigeben.

* Coderepository-Anforderungen:
  * Folgende Dateien müssen enthalten sein:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Der Ordner *node_modules* darf nicht enthalten sein (fügen Sie *node_modules* zur GITIGNORE-Datei hinzu).
  * Der Befehl *npm install* darf keine Fehler zurückgeben.
  * Der Befehl *npm audit* darf keine Warnungen mit hohem oder mittlerem Schweregrad zurückgeben.
  * Der Befehl *pbiviz package* darf keine Fehler zurückgeben.
  * [TSlint von Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) muss ohne überschriebene Konfigurationen enthalten sein. Dieser Befehl darf keine lint-Fehler zurückgeben.
   * Das kompilierte Paket des Power BI-Visuals muss mit dem übermittelten Paket übereinstimmen (die md5-Hashwerte beider Dateien müssen gleich sein).
* Quellcode-Anforderungen:
   * Das Power BI-Visual muss die [API zum Rendern von Ereignissen](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/) unterstützen.
   * Stellen Sie sicher, dass kein beliebiger/dynamischer Code ausgeführt wird (bad: eval(), unsafe to use of settimeout(), requestAnimationFrame(), setinterval(eine Funktion mit Benutzereingaben), Ausführen von Benutzereingaben/-daten).
   * Stellen Sie sicher, dass DOM sicher bearbeitet wird (bad: innerHTML, D3.html(<Benutzer-/Dateneingabe>), Bereinigung für Benutzereingaben/Daten vor dem Hinzufügen zum DOM verwenden).
   * Stellen Sie sicher, dass die Browserkonsole keinerlei JavaScript-Fehler oder -Ausnahmen für Eingabedaten ausgibt. Benutzer verwenden Ihr Power BI-Visual möglicherweise mit einem anderen, unerwarteten Datenbereich, für den beim Visual keine Fehler auftreten dürfen. Sie können diesen [Beispielbericht](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) als Testdataset verwenden.

* Wenn Eigenschaften in *capabilities.json* geändert werden, stellen Sie sicher, dass diese keine zu Störungen bei vorhandenen Benutzerberichten verursachen.

* Achten Sie darauf, dass Ihr Power BI-Visual den [Richtlinien für Power BI-Visuals](./guidelines-powerbi-visuals.md) entspricht.
    
* Ihr Code darf nur öffentlich überprüfbare OSS-Komponenten wie öffentliche JavaScript- oder TypeScript-Bibliotheken verwenden. Der Quellcode muss zur Überprüfung verfügbar sein und darf keine bekannten Sicherheitsrisiken aufweisen. Wir können überprüfen, ob ein benutzerdefiniertes Visual eine kommerzielle Komponente verwendet.

* Das Power BI-Visual darf nicht auf externe Dienste oder Ressourcen zugreifen. Beispielsweise dürfen aus Power BI keine HTTP/S- oder WebSocket-Anforderungen an Dienste gesendet werden. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Übermitteln eines Power BI-Visual zur Zertifizierung

Sie können über Partner Center eine Zertifizierung Ihres Power BI-Visuals durch das Power BI-Team anfordern.

>[!TIP]
>Der Zertifizierungsprozess für ein Power BI-Visual kann einige Zeit in Anspruch nehmen. Wenn Sie ein neues Power BI-Visual erstellen, empfiehlt es sich, dieses über Partner Center zu veröffentlichen, bevor Sie eine Power BI-Zertifizierung anfordern. Damit wird sichergestellt, dass sich die Veröffentlichung Ihres Visuals nicht verzögert.

So fordern Sie eine Power BI-Zertifizierung an:

1. Melden Sie sich bei Partner Center an.
2. Wählen Sie auf der **Übersichtsseite** Ihre Power BI-Visual aus, und wechseln Sie zur Seite **Produkteinrichtung**.
3. Aktivieren Sie das Kontrollkästchen **Power BI-Zertifizierung anfordern**.
4. Geben Sie auf der Seite **Überprüfen und veröffentlichen** im Textfeld **Hinweise für Zertifizierung** einen Link zum Quellcode sowie die Anmeldeinformationen für den Zugriff darauf an.

>[!NOTE]
> Wenn Sie sich gerade mitten im Übermittlungsprozess für ein Power BI-Visual befinden und das [Verkäuferdashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (das alte Verwaltungstool) verwenden müssen, lesen Sie die Anweisungen für den [Übermittlungsprozess für die Zertifizierung auf dem Verkäuferdashboard](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Liste der Power BI-Visuals mit Zertifizierung

| Link | Video |
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

Weitere Informationen zu Visuals finden Sie in den [häufig gestellten Fragen zu zertifizierten Visuals](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Nächste Schritte

* [Entwickeln eines benutzerdefinierten Visuals für Power BI](../developer/custom-visual-develop-tutorial.md)
* [Wiedergabeliste benutzerdefinierter visueller Elemente von Microsoft auf YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisierungen in Power BI](../visuals/power-bi-report-visualizations.md)  
* [Benutzerdefinierte Visualisierungen in Power BI](power-bi-custom-visuals.md)  
* [Veröffentlichen von Power BI-Visuals in Microsoft AppSource](../developer/office-store.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)
