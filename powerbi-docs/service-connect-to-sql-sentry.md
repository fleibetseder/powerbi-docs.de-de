---
title: Herstellen einer Verbindung mit SQL Sentry mithilfe von Power BI
description: "SQL Sentry für Power BI"
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 97a799ade391d0691ff7ecd4c362ce225ffa0ab9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-sql-sentry-with-power-bi"></a>Herstellen einer Verbindung mit SQL Sentry mithilfe von Power BI
Das Analysieren Ihrer mithilfe von SQL Sentry gesammelten Leistungsdaten ist mit Power BI ganz einfach. Power BI ruft Ihre Daten ab und erstellt auf Basis dieser Daten ein Standarddashboard und zugehörige Berichte.

Stellen Sie eine Verbindung zum [SQL Sentry-Inhaltspaket](https://app.powerbi.com/groups/me/getdata/services/sql-sentry) für Power BI her.

>[!NOTE]
>Für das Herstellen der Verbindung sind Zugriff auf ein SQL Sentry-Konto, das Sie für die Verbindung mit „http://cloud.sqlsentry.com“ verwenden, und die ID der zu überwachenden Datenbank erforderlich.  Hinweise, wie Sie die Datenbank-ID finden, sind unten aufgeführt.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-sql-sentry/pbi_getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-sql-sentry/pbi_getservices.png) 
3. Wählen Sie **SQL Sentry \> Abrufen** aus.
   
   ![](media/service-connect-to-sql-sentry/sqlsentry.png)
4. Geben Sie die **Datenbank-ID** der Datenbank ein, die Sie in Power BI überwachen möchten. Weitere Einzelheiten zum [Ermitteln dieses Werts](#FindingParams) finden Sie unten.
   
   ![](media/service-connect-to-sql-sentry/img2400.png)
5. Wählen Sie für die Authentifizierungsmethode **oAuth2 \> Anmelden** aus.
   
   Geben Sie bei der entsprechenden Aufforderung Ihre Anmeldeinformationen für „cloud.sqlsentry.com“ ein, und führen Sie den SQL Sentry-Authentifizierungsvorgang aus.
   
   ![](media/service-connect-to-sql-sentry/img6400.png)
   
   Wenn Sie die Verbindung zum ersten Mal herstellen, werden Sie von Power BI aufgefordert, den Lesezugriff auf Ihr Konto zu erteilen. Klicken Sie auf „Erteilen“, um den Importvorgang zu starten.  Dies kann je nach der im Konto enthaltenen Datenmenge einige Minuten dauern.
   
   ![](media/service-connect-to-sql-sentry/img7400.png)
6. Nachdem die Daten von Power BI importiert wurden, werden im linken Navigationsbereich ein neues Dashboard, ein Bericht und ein Dataset angezeigt. Neue Elemente werden mit einem gelben Sternchen (\*) markiert:
   
   ![](media/service-connect-to-sql-sentry/img8200.png)
7. Wählen Sie das SQL Sentry-Dashboard aus.
   
   Dies ist der Standarddashboard, das Power BI zum Anzeigen Ihrer Daten erstellt. Sie können dieses Dashboard anpassen, damit Ihre Daten auf die gewünschte Weise angezeigt werden.
   
   ![](media/service-connect-to-sql-sentry/img9dashboard800.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](service-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](service-dashboard-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Ihr Dataset ist auf eine tägliche Aktualisierung festgelegt. Sie können jedoch das Aktualisierungsintervall ändern oder es über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Die folgenden Daten sind über SQL Sentry in Power BI verfügbar:

| Tabellenname | Beschreibung |
| --- | --- |
| Verbindung |Diese Tabelle enthält Informationen über Ihre definierten SQL Sentry-Verbindungen. |
| Datum (Date)<br /> |Diese Tabelle enthält die Datumswerte von heute zurück zum frühesten Datum, an dem Leistungsdaten gesammelt und aufbewahrt wurden. |
| Downtime<br /> |Diese Tabelle enthält Informationen über die Ausfallzeiten und Betriebszeiten für jeden überwachten Server in Ihrer Umgebung. |
| Memory Usage<br /> |Diese Tabelle enthält Daten über den verfügbaren oder freien Arbeitsspeicher auf jedem Ihrer Server.<br /> |
| Server<br /> |Diese Tabelle enthält Datensätze für jeden Server in Ihrer Umgebung. |
| Server Health<br /> |Diese Tabelle enthält Daten zu sämtlichen Ereignissen, die durch benutzerdefinierte Bedingungen in Ihrer Umgebung generiert wurden, einschließlich Schweregrad und Anzahl. |

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Die **Datenbank-ID** können Sie ermitteln, indem Sie sich in einem neuen Webbrowserfenster bei <https://cloud.sqlsentry.com> anmelden.  Die **Datenbank-ID** ist auf der Hauptübersichtsseite aufgelistet:

    ![](media/service-connect-to-sql-sentry/database2.png)

Die **Datenbank-ID** wird außerdem auf dem Bildschirm „Datenbankdetails“ angezeigt:

    ![](media/service-connect-to-sql-sentry/database.png)


## <a name="troubleshooting"></a>Problembehandlung
Wenn Daten von einigen Ihrer Apps nicht in Power BI angezeigt werden, prüfen Sie nach, ob Sie die richtige Datenbank-ID verwenden und über die erforderliche Autorität zum Anzeigen der Daten verfügen. 

Wenn Sie nicht der Besitzer der SQL Sentry-Datenbank sind, die mit <https://cloud.sqlsentry.com>synchronisiert wird, wenden Sie sich an Ihren Administrator, um sicherzustellen, dass Sie die erforderlichen Rechte zum Anzeigen der gesammelten Daten besitzen.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)
