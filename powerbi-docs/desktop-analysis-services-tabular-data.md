---
title: Verwenden tabellarischer Analysis Services-Daten in Power BI Desktop
description: Analysis Services-Tabellendaten in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7ce20b8b6dc382cdafe61bde3e9305197fd33ea6
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75762069"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Verbinden mit tabellarischen Analysis Services-Daten in Power BI Desktop
Mit Power BI Desktop verfügen Sie über zwei Möglichkeiten, eine Verbindung mit tabellarischen Modellen von SQL Server Analysis Services herzustellen und Daten aus diesen Modellen abzurufen: Durchsuchen mit Live-Verbindung oder Auswählen und Importieren von Elementen in Power BI Desktop.

Sehen wir uns das einmal näher an.

**Erkunden mit Liveverbindung**: Bei Verwendung einer Liveverbindung werden Elemente im tabellarischen Modell oder einer Perspektive, wie Tabellen, Spalten und Maße, in der Liste der Power BI Desktop-Felder angezeigt. Die erweiterte Visualisierung und Bericht-Tools von Power BI Desktop bieten Ihnen neue und hoch interaktive Möglichkeiten zum Untersuchen Ihres tabellarischen Modells.

Bei einer Liveverbindung werden keine Daten aus dem tabellarischen Modell in Power BI Desktop importiert. Bei jeder Interaktion mit einer Visualisierung fragt Power BI Desktop das tabellarische Modell ab und berechnet die angezeigten Ergebnisse. Ihnen werden immer die aktuellsten Daten angezeigt, die entweder über den letzten Verarbeitungszeitpunkt oder über die Tabellen für direkte Abfragen im tabellarischen Modell verfügbar sind. 

Beachten Sie, dass tabellarische Modelle eine hohe Sicherheit bieten. Die in Power BI Desktop angezeigten Elemente hängen von Ihren Berechtigungen für das tabellarische Modell ab, mit dem Sie verbunden sind.

Dynamische Berichte, die Sie in Power BI Desktop erstellt haben, können Sie durch die Veröffentlichung auf Ihrer Power BI-Website freigeben. Wenn Sie eine Power BI Desktop-Datei mit einer Liveverbindung mit einem tabellarischen Modell auf Ihrer Power BI-Website veröffentlichen möchten, muss ein lokales Datengateway installiert sein und von einem Administrator konfiguriert werden. Lesen Sie zu diesem Thema den Artikel [Lokales Datengateway](service-gateway-onprem.md).

**Auswählen und Importieren von Elementen in Power BI-Desktop**: Wenn Sie eine Verbindung mit dieser Option herstellen, können Sie Elemente, wie Tabellen, Spalten und Maße, in Ihrem tabellarischen Modell bzw. einer Perspektive auswählen und in ein Power BI Desktop-Modell laden. Mit dem erweiterten Abfrage-Editor von Power BI Desktop können Sie Ihre Suche noch weiter präzisieren. Mithilfe der Modellierungsfunktionen von Power BI Desktop können Sie die Daten noch weitergehender modellieren. Zwischen Power BI Desktop und dem tabellarischen Modell wird keine Live-Verbindung aufrechterhalten. Sie können dann Ihr Power BI Desktop-Modell offline untersuchen oder auf Ihrer Power BI-Website veröffentlichen.

## <a name="to-connect-to-a-tabular-model"></a>So stellen Sie eine Verbindung mit einem tabellarischen Modell her
1. Klicken Sie in Power BI Desktop auf der Registerkarte **Start** auf **Daten abrufen**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata.png)
2. Klicken Sie auf **SQL Server Analysis Services-Datenbank**und dann auf **Verbinden**.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. Geben Sie den Namen des Servers ein, und wählen Sie einen Verbindungsmodus aus. 
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. Dieser Schritt hängt von dem von Ihnen ausgewählten Verbindungsmodus ab:

* Wenn Sie eine Live-Verbindung herstellen, wählen Sie im Navigator ein tabellarisches Modell oder eine Perspektive aus.
  
  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
* Wenn Sie Auswählen und Importieren von Elementen verwenden, wählen Sie im Navigator ein tabellarisches Modell oder eine Perspektive aus. Weiter können Sie nur bestimmte Tabellen oder Spalten zum Laden auswählen. Um Ihre Daten vor dem Laden zu modellieren, rufen Sie den Abfrage-Editor auf, indem Sie auf "Bearbeiten" klicken. Wenn Sie dies abgeschlossen haben, klicken Sie auf "Laden", um die Daten in Power BI Desktop zu importieren.

  ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
**Frage:** Benötige ich ein lokales Datengateway?

**Antwort:** Das kommt darauf an. Wenn Sie Power BI Desktop verwenden, um eine Live-Verbindung mit einem tabellarischen Modell herzustellen, jedoch keine Veröffentlichung auf Ihrer Power BI-Website beabsichtigen, benötigen Sie kein Gateway. Wenn Sie jedoch eine Veröffentlichung auf Ihrer Power BI-Website beabsichtigen, benötigen Sie ein Datengateway, um eine sichere Kommunikation zwischen dem Power BI-Dienst und dem lokalen Analysis Services-Server sicherzustellen. Wenden Sie sich unbedingt an Ihren Analysis Services Server-Administrator, bevor Sie ein Datengateway installieren.

Wenn Sie „Elemente auswählen“ und „Daten abrufen“ auswählen, importieren Sie tabellarische Modelldaten direkt in Ihre Power BI Desktop-Datei. Daher ist kein Gateway erforderlich.

**Frage:** Was ist der Unterschied zwischen einer Live-Verbindung mit einem tabellarischen Modell im Power BI-Dienst gegenüber einer Live-Verbindung in Power BI Desktop?

**Antwort:** Bei einer Live-Verbindung mit einem tabellarischen Modell Ihrer Website im Power BI-Dienst mit einer lokal in Ihrem Unternehmen vorhandenen Analysis Services-Datenbank ist ein lokales Datengateway erforderlich, um eine sichere Kommunikation zwischen diesen sicherzustellen. Bei einer Live-Verbindung mit einem tabellarischen Modell in Power BI Desktop benötigen Sie kein Gateway, da sowohl Power BI Desktop als auch der Analysis Services-Server, mit denen Sie die Verbindung herstellen, in Ihrer Organisation lokal ausgeführt werden. Wenn Sie jedoch Ihre Power BI Desktop-Datei auf Ihrer Power BI-Website veröffentlichen, ist ein Gateway erforderlich.

**Frage:** Kann ich, wenn ich eine Live-Verbindung hergestellt habe, auch eine Verbindung zu einer anderen Datenquelle in derselben Power BI Desktop-Datei herstellen?

**Antwort:** Nein. Sie können keine Livedaten untersuchen und auch keine Verbindung mit einem anderen Datenquellentyp in derselben Datei herstellen. Wenn Sie bereits Daten importiert oder eine Verbindung mit einer anderen Datenquelle in einer Power BI Desktop-Datei hergestellt haben, müssen Sie für eine Live-Untersuchung eine neue Datei erstellen.

**Frage:** Kann ich, wenn ich eine Live-Verbindung erstellt habe, das Modell oder die Abfrage in Power BI Desktop bearbeiten?

**Antwort:** Sie können in Power BI Desktop Measures auf Berichtsebene erstellen, aber alle anderen Abfrage- und Modellierungsfeatures sind beim Untersuchen von Livedaten deaktiviert.

**Frage:** Ist eine von mir erstellte Live-Verbindung sicher?

**Antwort:** Ja. Ihre aktuellen Windows-Anmeldeinformationen werden für die Verbindung mit dem Analysis Services-Server verwendet. Sie können Basic- oder gespeicherte Anmeldeinformationen bei der Untersuchung von Livedaten weder im Power BI-Dienst noch im Power BI Desktop verwenden.

**Frage:** Im Navigator werden ein Modell und eine Perspektive angezeigt. Was ist der Unterschied?

**Antwort:** Eine Perspektive ist eine bestimmte Ansicht eines tabellarischen Modells. Sie enthält ggf. nur bestimmte Tabellen, Spalten oder Maße in Abhängigkeit von einem speziellen Datenanalysebedarf. Ein tabellarisches Modell enthält immer mindestens eine-Perspektive, die alles, was im Modell enthalten ist, umfassen kann. Wenn Sie nicht sicher sind, was Sie auswählen sollen, wenden Sie sich an Ihren Administrator.

**Frage:** Gibt es Funktionen von Analysis Services, die das Verhalten von Power BI verändern?

**Antwort:** Ja. Abhängig von den Funktionen, die Ihr tabellarisches Modell verwendet, kann sich die Benutzeroberfläche in Power BI Desktop ändern. Beispiele hierfür sind:
* Möglicherweise sehen Sie die Measures im Modell oben in der Feldliste gruppiert und nicht in Tabellen neben den Spalten. Keine Sorge! Sie können sie trotzdem wie gewohnt verwenden, es ist nur einfacher, sie auf diese Weise zu finden.
* Wenn im tabellarischen Modell Berechnungsgruppen definiert sind, können Sie diese nur in Verbindung mit Modellmeasures verwenden und nicht mit impliziten Measures, die Sie durch Hinzufügen von numerischen Feldern zu einem Visual erstellen. Das Modell könnte auch das Flag **DiscourageImplicitMeasures** manuell festgelegt haben, was den gleichen Effekt hat. Weitere Informationen finden Sie unter [Berechnungsgruppen in Analysis Services](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups#benefits).

## <a name="to-change-the-server-name-after-initial-connection"></a>So ändern Sie den Namen des Servers nach der ersten Verbindung
Nachdem Sie eine Power BI Desktop-Datei mit einer Live-Verbindung erstellt haben, kann es in einigen Fällen erforderlich sein, die Verbindung auf einen anderen Server umzuschalten. Wenn Sie beispielsweise Ihre Power BI-Desktop-Datei bei der Verbindung mit einem Entwicklungsserver und vor der Veröffentlichung im Power BI-Dienst erstellt haben, möchten Sie die Verbindung zum Produktionsserver umschalten.

1. Wählen Sie im Menüband **Abfragen bearbeiten** aus.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_editquery.png)
2. Geben Sie den neuen Namen ein.
   
   ![](media/desktop-analysis-services-tabular-data/pbid_sqlas_chname_dialog.png)
   
   
## <a name="troubleshooting"></a>Problembehandlung 
In der folgenden Liste sind alle bekannten Probleme beim Verbinden mit SQL Server Analysis Services (SSAS) und Azure Analysis Services aufgeführt. 

* **Fehler: Das Modellschema konnte nicht geladen werden**: Dieser Fehler tritt normalerweise nur dann auf, wenn der Benutzer, der versucht, eine Verbindung mit Analysis Services herzustellen, keine Zugriffsberechtigungen für die Datenbank/das Modell besitzt.

