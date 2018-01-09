---
title: Verwendung des SAP BW-Connectors in Power BI Desktop
description: Verwendung des SAP BW-Connectors in Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 13f6a3fa5fc5ae5c2bea2fb6b91250216eebcc01
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2017
---
# <a name="use-the-sap-bw-connector-in-power-bi-desktop"></a>Verwendung des SAP BW-Connectors in Power BI Desktop
Mit Power BI Desktop können Sie auf Daten aus **SAP Business Warehouse (BW)** zuzugreifen.

## <a name="installation-of-sap-bw-connector"></a>Installation des SAP BW-Connectors
Um den **SAP BW-Connector** zu verwenden, befolgen Sie die nachstehenden Installationsschritte:

1. Installieren Sie die **SAP NetWeaver**-Bibliothek auf dem lokalen Computer. Sie erhalten die **SAP Netweaver**-Bibliothek von Ihrem SAP-Administrator oder direkt über das [SAP Software Download Center](https://support.sap.com/swdc). Da die Struktur des **SAP Software Download Center** regelmäßig überarbeitet wird, können wir keine genaueren Angaben zu dieser Website machen. Diese **SAP NetWeaver**-Bibliothek ist in der Regel auch in der Installation der SAP Client Tools enthalten.
   
   Sie können nach *SAP-Hinweis 1025361* suchen, um den Downloadpfad für die neueste Version zu ermitteln. Stellen Sie sicher, dass die Architektur für die **SAP NetWeaver**-Bibliothek (32 Bit oder 64 Bit) mit Ihrer Installation von **Power BI Desktop** übereinstimmt, und installieren Sie dann alle Dateien im **SAP NetWeaver RFC SDK** gemäß dem SAP-Hinweis.
2. Das Dialogfeld **Daten abrufen** enthält einen Eintrag für **SAP Business Warehouse Server** in der Kategorie **Datenbank**.
   
   ![](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="sap-bw-connector-features"></a>Funktionen des SAP BW-Connectors
Die Preview-Version des **SAP BW-Connectors** in Power BI Desktop ermöglicht Benutzern das Importieren von Daten aus ihren **SAP Business Warehouse Server**-Cubes. Sie können auch DirectQuery mit dem **SAP BW-Connector** verwenden. Geben Sie Werte für *Server*, *Systemnummer* und *Client-ID* ein, um eine Verbindung herzustellen.

![](media/desktop-sap-bw-connector/sap_bw_3a.png)

Sie können auch zwei zusätzliche **Erweiterte Optionen** angeben: Sprachcode und eine benutzerdefinierte MDX-Anweisung, die für den angegebenen Server ausgeführt wird.

![](media/desktop-sap-bw-connector/sap_bw_4a.png)

Wenn keine MDX-Anweisung angegeben wurde, wird Ihnen das Fenster **Navigator** angezeigt, das die Liste der Cubes, die auf dem Server verfügbar sind, darstellt sowie die Möglichkeit, einen Drilldown auszuführen und Elemente aus den verfügbaren Cubes auszuwählen, einschließlich Dimensionen und Measures. Power BI macht Abfragen und Cubes verfügbar, die wiederum über [BW Open Analysis Interface OLAP BAPIs](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm) verfügbar gemacht wurden.

Wenn Sie ein oder mehrere Elemente aus dem Server auswählen, wird abhängig von ihrer Auswahl eine Vorschau der Ausgabetabelle erstellt.

![](media/desktop-sap-bw-connector/sap_bw_5.png)

Das Fenster **Navigator** bietet auch einige **Anzeigeoptionen**, mit denen Sie die folgenden Schritte ausführen können:

* **Anzeige *Nur ausgewählte Elemente* im Vergleich zu *Alle Elemente* (Standardansicht):** Diese Option dient der Überprüfung des endgültigen Satzes von ausgewählten Elementen. Um eine alternative Möglichkeit der Darstellung dieser Auswahl anzuzeigen, wählen Sie die *Spaltennamen* im Bereich *Vorschau* aus.
* **Datenvorschau aktivieren (Standardverhalten):** Sie können auch steuern, ob die Datenvorschau in diesem Dialogfeld angezeigt werden soll. Das Deaktivieren der Datenvorschau verringert die Serveraufrufe, da keine Daten für die Vorschau mehr angefordert werden.
* **Technischer Name:** SAP BW unterstützt das Konzept von *technischen Namen* für Objekte innerhalb eines Cubes. Durch technische Namen kann ein Cube-Besitzer *benutzerfreundliche* Namen für Cubeobjekte verfügbar machen, statt nur die *physischen Namen* für diese Objekte im Cube.

![](media/desktop-sap-bw-connector/sap_bw_6.png)

Nach dem Auswählen aller erforderlichen Objekte im **Navigator** können Sie entscheiden, was Sie als Nächstes tun möchten, indem Sie dazu eine der folgenden Schaltflächen unten auf dem Fenster **Navigator** auswählen:

* Durch klicken auf **Laden** veranlassen Sie, dass der gesamten Satz von Zeilen für die Ausgabetabelle in das Power BI Desktop-Datenmodell geladen wird. Sie gelangen daraufhin zur Ansicht **Bericht**, wo Sie beginnen können, die Daten zu visualisieren oder weitere Änderungen mithilfe der Ansicht **Daten** oder **Beziehungen** durchzuführen.
* Wenn Sie **Bearbeiten** auswählen, wird der **Abfrage-Editor** geöffnet, in dem Sie zusätzliche Schritte zur Datentransformation und zum Filtern ausführen können, bevor der gesamte Satz von Zeilen in das Datenmodell für Power BI Desktop geladen wird.

Denken sie daran, dass Sie zusätzlich zum Importieren von Daten aus **SAP BW** Cubes, Daten aus einer Vielzahl anderer Datenquellen in Power BI Desktop importieren können und sie dann zu einem einzelnen Bericht zusammenfassen können. Dies stellt alle möglichen interessante Szenarios für die Berichterstellung und Analyse auf der Basis von **SAP BW**-Daten dar.

## <a name="troubleshooting"></a>Problembehandlung
Dieser Abschnitt enthält die Fehlerbehebung (und Lösungen) für die Arbeit mit dieser Preview-Version des **SAP BW**-Connectors.

1. Bei numerischen Daten aus **SAP BW** werden als Dezimaltrennzeichen Punkte statt Kommas zurückgegeben. Beispielsweise wird 1,000,000 als 1.000.000 zurückgegeben.
   
   **SAP BW** gibt Dezimaldaten entweder mit *,* (Komma) oder mit *.* (Punkt) als Dezimaltrennzeichen zurück. Um anzugeben, welches dieser Zeichen von **SAP BW** als Dezimaltrennzeichen verwendet werden soll, ruft der von **Power BI Desktop** verwendete Treiber *BAPI_USER_GET_DETAIL* auf. Dieser Aufruf gibt eine Struktur mit dem Namen **DEFAULTS** zurück, die das Feld *DCPFM* enthält, in dem die *Schreibweise des Dezimalformats* gespeichert wird. Es akzeptiert einen der folgenden drei Werte:
   
       ‘ ‘ (space) = Decimal point is comma: N.NNN,NN
       'X' = Decimal point is period: N,NNN.NN
       'Y' = Decimal point is N NNN NNN,NN
   
   Kunden, die dieses Problem gemeldet haben, stellten fest, dass der Aufruf von *BAPI_USER_GET_DETAIL* für einen bestimmten Benutzer (den Benutzer, für den die falschen Daten angezeigt werden) mit einer Fehlermeldung wie der folgenden fehlschlägt:
   
       You are not authorized to display users in group TI:
           <item>
               <TYPE>E</TYPE>
               <ID>01</ID>
               <NUMBER>512</NUMBER>
               <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
               <LOG_NO/>
               <LOG_MSG_NO>000000</LOG_MSG_NO>
               <MESSAGE_V1>TI</MESSAGE_V1>
               <MESSAGE_V2/>
               <MESSAGE_V3/>
               <MESSAGE_V4/>
               <PARAMETER/>
               <ROW>0</ROW>
               <FIELD>BNAME</FIELD>
               <SYSTEM>CLNTPW1400</SYSTEM>
           </item>
   
   Um diesen Fehler zu beheben, müssen Benutzer den SAP-Administrator bitten, dem in Power BI verwendeten SAPBW-Benutzer das Recht zum Ausführen von *BAPI_USER_GET_DETAIL* zu gewähren. Außerdem sollten Sie sicherstellen, dass der Benutzer über den erforderlichen *DCPFM*-Wert verfügt, wie weiter oben in dieser Problembehandlungslösung beschrieben.
2. **Konnektivität für SAP BEx-Abfragen**
   
   Sie können **BEx**-Abfragen in Power BI Desktop ausführen, indem Sie eine bestimmte Eigenschaft aktivieren, wie in folgender Abbildung dargestellt:
   
   ![](media/desktop-sap-bw-connector/sap_bw_8.png)
