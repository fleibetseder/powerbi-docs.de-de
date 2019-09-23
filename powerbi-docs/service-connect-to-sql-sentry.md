---
title: Herstellen einer Verbindung mit SQL Sentry mithilfe von Power BI
description: SQL Sentry für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 1fc8decc70ade009a7c4236686cfe9cf72adb54d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61161700"
---
# <a name="connect-to-sql-sentry-with-power-bi"></a>Herstellen einer Verbindung mit SQL Sentry mithilfe von Power BI
Das Analysieren Ihrer mithilfe von SQL Sentry gesammelten Leistungsdaten ist mit Power BI ganz einfach. Power BI ruft Ihre Daten ab und erstellt auf Basis dieser Daten ein Standarddashboard und zugehörige Berichte.

Stellen Sie eine Verbindung zum [SQL Sentry-Inhaltspaket](https://app.powerbi.com/groups/me/getdata/services/sql-sentry) für Power BI her.

>[!NOTE]
>Für das Herstellen der Verbindung ist Zugriff auf ein SQL Sentry-Konto erforderlich, das Sie verwenden, um sich mit http://cloud.sqlsentry.com und einer Datenbank-ID zu verbinden.  Hinweise, wie Sie die Datenbank-ID finden, sind unten aufgeführt.

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

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

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

Wenn Sie nicht der Besitzer der SQL Sentry-Datenbank sind, die nach <https://cloud.sqlsentry.com> synchronisiert wird, wenden Sie sich an Ihren Administrator, um sicherzustellen, dass Sie die erforderlichen Rechte zum Anzeigen der gesammelten Daten besitzen.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](power-bi-overview.md)

[Abrufen von Daten in Power BI](service-get-data.md)

