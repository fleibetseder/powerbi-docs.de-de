---
title: Problembehandlung für Power BI Gateway – Personal
description: Problembehandlung für Power BI Gateway – Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271829"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Problembehandlung für Power BI Gateway – Personal

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

In den folgenden Abschnitten werden einige häufige Fehler erläutert, die beim Verwenden von Power BI Gateway – Personal möglicherweise auftreten.

## <a name="update-to-the-latest-version"></a>Aktualisieren auf die neueste Version

Die aktuelle Version des Gateways für den persönlichen Gebrauch ist das **lokale Datengateway (Personal)** . Aktualisieren Sie Ihre Installation mit dieser Version.

Bei einer veralteten Gatewayversion können viele Probleme auftreten.  Es ist ratsam sicherzustellen, dass Sie immer die aktuelle Version verwenden. Wenn Sie das Gateway einen Monat oder länger nicht mehr aktualisiert haben, sollten Sie die aktuelle Version des Gateways installieren. Überprüfen Sie dann, ob Sie das Problem reproduzieren können.

## <a name="installation"></a>Installation
Das **persönliche Gateway ist 64 Bit** : Wenn es sich um einen 32-Bit-Computer handelt, können Sie das persönliche Gateway nicht installieren. Das Betriebssystem muss eine 64-Bit-Version aufweisen. Installieren Sie entweder eine 64-Bit-Version von Windows, oder installieren Sie das persönliche Gateway auf einem 64-Bit-Computer.

**Fehler bei der Installation von des persönlichen Gateways als Dienst, obwohl Sie ein lokaler Administrator des Computers sind**: Bei der Installation kann ein Fehler auftreten, wenn der Benutzer Mitglied der lokalen Administratorgruppe des Computers ist, die Gruppenrichtlinien die Anmeldung dieses Benutzernamens als Dienst jedoch nicht erlauben. Stellen Sie zunächst sicher, dass die Gruppenrichtlinien die Anmeldung von Benutzern als Dienst zulassen. Wir arbeiten an einer Korrektur für dieses Problem. [Weitere Informationen](https://technet.microsoft.com/library/cc739424.aspx)

**Timeout beim Vorgang**: Diese Meldung wird häufig angezeigt, wenn der Computer (physischer Computer oder VM), auf dem Sie das persönliche Gateway installieren, über einen Einzelkernprozessor verfügt. Schließen Sie eventuell geöffnete Anwendungen, deaktivieren Sie alle nicht benötigten Prozesse, und versuchen Sie die Installation erneut.

**Das Datenverwaltungsgateway und der Analysis Services Connector können nicht auf demselben Computer wie das persönliche Gateway installiert werden** – Wenn auf dem Computer bereits ein Analysis Services-Connector oder ein Datenverwaltungsgateway installiert ist, müssen Sie den Connector oder das Gateway zuerst deinstallieren. Versuchen Sie dann, das persönliche Gateway zu installieren.

> [!NOTE]
> Wenn während der Installation ein Fehler auftritt, können Sie in den Setupprotokollen möglicherweise hilfreiche Informationen zum Lösen des Problems finden. Weitere Informationen finden Sie unter [Setupprotokolle](#SetupLogs).
> 
> 

 **Proxykonfiguration:** Es treten möglicherweise Probleme beim Konfigurieren des persönlichen Gateways auf, wenn für Ihre Umgebung ein Proxy erforderlich ist. Weitere Informationen zum Konfigurieren von Proxyinformationen finden Sie unter [Konfigurieren von Proxyeinstellungen für das lokale Datengateway](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Zeitplanaktualisierung
**Fehler: Die in der Cloud gespeicherten Anmeldeinformationen sind nicht vorhanden.**

Dieser Fehler kann z.B. in den Einstellungen für \<dataset\> auftreten, wenn Sie eine Zeitplanaktualisierung geplant und anschließend Personal Gateway deinstalliert und erneut installiert haben. Bei der Deinstallation des persönlichen Gateways werden die Datenquellen-Anmeldeinformationen für ein Dataset, die für die Aktualisierung konfiguriert wurden, aus dem Power BI-Dienst entfernt.

**Lösung:** Navigieren Sie in Power BI zu den Aktualisierungseinstellungen für ein Dataset. Wählen Sie in „Datenquellen verwalten“ eine beliebige Datenquelle mit einem Fehler **Anmeldeinformationen bearbeiten** aus, und melden Sie sich dann wieder bei der Datenquelle an.

**Fehler: Die für das Dataset bereitgestellten Anmeldeinformationen sind ungültig. Aktualisieren Sie die Anmeldeinformationen mithilfe einer Aktualisierung oder im Dialogfeld „Datenquelleneinstellungen“, um fortzufahren.**

**Lösung**: Wenn Sie eine Nachricht bezüglich Anmeldeinformationen erhalten, könnte Folgendes zutreffen:

* Achten Sie darauf, dass die für die Anmeldung bei Datenquellen verwendeten Benutzernamen und Kennwörter aktuell sind. Navigieren Sie in Power BI zu den Aktualisierungseinstellungen für das Dataset. Wählen Sie in „Datenquellen verwalten“ **Anmeldeinformationen bearbeiten** aus, um die Anmeldeinformationen für die Datenquelle zu aktualisieren.
* Mashups zwischen einer Cloud-Quelle und einer lokalen Quelle in einer einzelnen Abfrage werden im persönlichen Gateway nicht aktualisiert, wenn eine der Quellen OAuth als Authentifizierungsmethode verwendet. Ein Beispiel hierfür ist ein Mashup zwischen CRM Online und einem lokalen SQL Server. Das Mashup funktioniert nicht, da CRM Online OAuth erfordert.
  
  Dieser Fehler ist bekannt und wird derzeit untersucht. Um das Problem zu umgehen, können für die Cloudquelle und die lokale Quelle getrennte Abfragen verwendet werden. Diese können dann in einer Merge- oder Append-Abfrage zusammengeführt werden.

**Fehler: Nicht unterstützte Datenquelle.**

**Lösung:** Wenn in den Einstellungen für die Zeitplanaktualisierung eine Nachricht zu einer nicht unterstützten Datenquelle angezeigt wird, kann das Folgendes bedeuten: 

* Die Aktualisierung der Datenquelle wird von Power BI aktuell nicht unterstützt. 
* Die Excel-Arbeitsmappe enthält kein Datenmodell, sondern nur Arbeitsblattdaten. Power BI unterstützt die Aktualisierung zurzeit nur, wenn die hochgeladene Excel-Arbeitsmappe ein Datenmodell enthält. Achten Sie beim Importieren von Daten in Excel mithilfe von Power Query darauf, die Option zum Laden von Daten in ein Datenmodell zu aktivieren. Mit dieser Option wird sichergestellt, dass die Daten in ein Datenmodell importiert werden. 

**Fehler: [Daten können nicht verbunden werden] &lt;Abfragteteil&gt;/&lt;…&gt;/&lt;…&gt; greift auf Datenquellen mit Sicherheitsstufen zu, die nicht gemeinsam verwendet werden können. Erstellen Sie diese Datenkombination neu.**

**Lösung**: Dieser Fehler wird durch die Einschränkungen der Datenschutzstufe verursacht sowie durch die Arten der verwendeten Datenquellen.

**Fehler: Datenquellenfehler: Der Wert „\[Tabelle\]“ kann nicht in den Typ „Tabelle“ konvertiert werden.**

**Lösung**: Dieser Fehler wird durch die Einschränkungen der Datenschutzstufe verursacht sowie durch die Arten der verwendeten Datenquellen.

**Fehler: Für diese Zeile ist nicht ausreichend Platz vorhanden.**

Dieser Fehler tritt auf, wenn eine einzelne Zeile größer als 4 MB ist. Suchen Sie die entsprechende Zeile in der Datenquelle, und versuchen Sie, die Zeile herauszufiltern oder deren Größe zu verringern.

## <a name="data-sources"></a>Datenquellen
**Fehlender Datenanbieter** – Das persönliche Gateway unterstützt nur 64-Bit-Systeme. Auf demselben Computer, auf dem Personal Gateway installiert ist, muss eine 64-Bit-Version der Datenanbieter installiert sein. Wenn beispielsweise die Datenquelle im Dataset Microsoft Access ist, müssen Sie den 64-Bit-ACE-Anbieter auf demselben Computer wie Personal Gateway installieren.  

>[!NOTE]
>Wenn Sie die 32-Bit-Version von Excel verwenden, können Sie keinen 64-Bit-ACE-Anbieter auf dem gleichen Computer installieren.

**Windows-Authentifizierung wird für Access-Datenbanken nicht unterstützt** – Power BI unterstützt zurzeit für Access-Datenbanken nur „anonym“. Wir arbeiten an einer Lösung, Windows-Authentifizierung für Access-Datenbanken zu ermöglichen.

**Anmeldefehler beim Eingeben von Anmeldeinformationen für eine Datenquelle** – Wenn bei der Eingabe von Windows-Anmeldeinformationen für eine Datenquelle dieser oder ein ähnlicher Fehler angezeigt wird, verwenden Sie möglicherweise noch eine alte Version von Personal Gateway. [Installieren Sie die neueste Version von Power BI Gateway – Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Fehler: Anmeldefehler beim Auswählen von Windows-Authentifizierung für eine Datenquelle, die ACE OLEDB verwendet** – Wenn beim Eingeben von Datenquellen-Anmeldeinformationen für eine Datenquelle, die den ACE-OLEDB-Anbieter verwendet, dieser Fehler angezeigt wird:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI unterstützt derzeit keine Windows-Authentifizierung für eine Datenquelle, die den ACE-OLEDB-Anbieter verwendet.

**Lösung:** Zur Umgehung dieses Fehlers können Sie die **anonyme Authentifizierung** auswählen. Bei ACE-OLEDB-Legacyanbietern sind anonyme Anmeldeinformationen gleichbedeutend mit Windows-Anmeldeinformationen.

## <a name="tile-refresh"></a>Kachelaktualisierung
Falls ein Fehler beim Aktualisieren von Dashboardkacheln auftritt, lesen Sie folgenden Artikel.

[Problembehandlung für Kachelfehler](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Tools zur Problembehandlung
### <a name="refresh-history"></a>Verlauf aktualisieren
Mit **Verlauf aktualisieren** können Sie sehen, welche Fehler aufgetreten sind, und Sie erhalten nützliche Daten, wenn Sie eine Supportanfrage erstellen müssen. Sie können sowohl geplante Aktualisierungen als auch Aktualisierungen nach Bedarf anzeigen. Hier ist beschrieben, wie Sie zur Option **Verlauf aktualisieren** gelangen.

1. Wählen Sie im Power BI-Navigationsbereich in **Datasets** für das Dataset &gt; Menü öffnen &gt;**Aktualisierung planen** aus.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. Wählen Sie unter **Einstellungen für...** die Option **Verlauf aktualisieren** aus.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Ereignisprotokolle
Es gibt mehrere Ereignisprotokolle, die Informationen liefern können. Die ersten beiden, **Datenverwaltungsgateway** und **PowerBIGateway**, sind vorhanden, wenn Sie der Administrator des Computers sind.  Wenn Sie kein Administrator sind und das persönliche Gateway verwenden, werden die Protokolleinträge im Protokoll **Anwendung** angezeigt.

Die Protokolle **Datenverwaltungsgateway** und **PowerBIGateway** befinden sich unter **Anwendungs- und Dienstprotokolle**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Ablaufverfolgung mit Fiddler
[Fiddler](http://www.telerik.com/fiddler) ist ein kostenloses Tool von Telerik, mit dem HTTP-Verkehr überwacht werden kann. Sie können die Kommunikation zwischen dem Power BI-Dienst und dem Clientcomputer verfolgen. Mit dieser Kommunikation können Sie Fehler und ähnliche Informationen anzeigen.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Setupprotokolle
Wenn das **persönliche Gateway** nicht installiert werden kann, wird ein Link zum Anzeigen des Setupprotokolls eingeblendet. Darin können Details zum Fehler enthalten sein. Diese Protokolle sind Windows-Installationsprotokolle, auch MSI-Protokolle genannt. Sie können recht komplex und schwierig zu lesen sein. Der resultierende Fehler taucht in der Regel unten auf, das Bestimmen der Fehlerursache ist jedoch nicht trivial. Es könnte sich dabei um das Ergebnis von Fehlern in einem anderen Protokoll oder das Ergebnis eines Fehlers weiter oben im Protokoll handeln.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Sie können alternativ auch im Ordner **Temp** (%temp%) nach Dateien suchen, die mit **Power\_BI\_** beginnen.

> [!NOTE]
> Wenn Sie auf „%temp%“ zugreifen, gelangen Sie unter Umständen in einen Unterordner von „temp“. Die Dateien mit **Power\_BI\_** befinden sich im Stamm des temp-Verzeichnisses.  Sie müssen also ggf. ein oder zwei Ebenen nach oben navigieren.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von Proxyeinstellungen für das lokale Datengateway](/data-integration/gateway/service-gateway-proxy)  
[Datenaktualisierung](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Problembehandlung für Kachelfehler](refresh-troubleshooting-tile-errors.md)  
[Problembehandlung beim lokalen Datengateway](service-gateway-onprem-tshoot.md)  
Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

