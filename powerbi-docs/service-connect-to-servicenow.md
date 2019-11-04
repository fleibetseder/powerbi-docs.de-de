---
title: Herstellen einer Verbindung mit ServiceNow mithilfe von Power BI
description: ServiceNow für Power BI
author: KesemSharabi
ms.author: sarinas
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
LocalizationGroup: Connect to services
ms.openlocfilehash: 4abf01163dbf454ee75b04e5d519ec2292b6e80c
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060784"
---
# <a name="connect-to-servicenow-with-power-bi-for-incident-reporting"></a>Herstellen einer Verbindung mit ServiceNow mithilfe von Power BI für Berichte über Vorfälle
ServiceNow bietet mehrere Produkte und Lösungen für die Optimierung Ihres Unternehmens, u. a. Unternehmens-, Betriebs- und IT-Verwaltung. Dieses Inhaltspaket umfasst mehrere Berichte und Informationen zu offenen, kürzlich gelösten und kürzlich geschlossenen Vorfällen.  

Stellen Sie eine Verbindung mit dem Power BI-Inhaltspaket für [ServiceNow-Vorfälle](https://app.powerbi.com/getdata/services/servicenow) her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-servicenow/pbi_getdata.png) 
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-servicenow/pbi_getservices.png) 
3. Wählen Sie **ServiceNow-Vorfälle** \> **Abrufen** aus.
   
   ![](media/service-connect-to-servicenow/connect.png)
4. Geben Sie die URL der ServiceNow-Instanz und den Bereich für die zu importierenden Tage/Datensätze ein. Beachten Sie, dass der Importvorgang beendet wird, sobald ein Grenzwert erreicht wird.
   
   ![](media/service-connect-to-servicenow/params.png)
5. Wenn Sie dazu aufgefordert werden, geben Sie Ihre ServiceNow-Anmeldeinformationen für die **Standardauthentifizierung** ein. Beachten Sie, dass das einmalige Anmelden zurzeit nicht unterstützt wird. Weitere Informationen zu den Systemanforderungen finden Sie unten.
   
   ![](media/service-connect-to-servicenow/creds.png)
6. Nach Abschluss der Anmeldung wird den Importvorgang gestartet. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
    ![](media/service-connect-to-servicenow/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Zum Herstellen der Verbindung benötigen Sie Folgendes:  

* Ein Konto, das mit Standardauthentifizierung auf „IhreOrganisation.service-now.com“ zugreifen kann (einmaliges Anmelden wird in dieser Version nicht unterstützt)  
* Das Konto muss die Rolle „rest_service“ und Lesezugriff auf die Liste der Vorfälle haben.  

## <a name="troubleshooting"></a>Problembehandlung
Wenn beim Laden ein Fehler mit den Anmeldeinformationen auftritt, überprüfen Sie die unten aufgeführten Zugriffsanforderungen. Wenn Sie über die richtigen Berechtigungen verfügen und trotzdem Probleme auftreten, wenden Sie sich an Ihren ServiceNow-Administrator, um sicherzustellen, dass Sie über alle zusätzlichen Berechtigungen verfügen, die möglicherweise für Ihre benutzerdefinierte Instanz benötigt werden.

Überprüfen Sie bei langen Ladezeiten die Anzahl der Vorfälle und die Anzahl der Tage, die für die Verbindung angegeben wurden, und erwägen Sie, die Werte zu reduzieren.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](fundamentals/power-bi-overview.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

