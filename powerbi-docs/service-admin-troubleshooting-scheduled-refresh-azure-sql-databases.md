---
title: Problembehandlung bei der planmäßigen Aktualisierung für Azure SQL-Datenbanken
description: Problembehandlung bei der planmäßigen Aktualisierung für Azure SQL-Datenbanken in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d71a1202ba996b70c7477a33ccab936bebbfc5e
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542803"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Problembehandlung bei der planmäßigen Aktualisierung für Azure SQL-Datenbanken in Power BI

Ausführliche Informationen zur Aktualisierung finden Sie unter [Aktualisieren von Daten in Power BI](refresh-data.md) und [Konfigurieren von geplanten Aktualisierungen](refresh-scheduled-refresh.md).

Wenn Sie beim Einrichten der planmäßigen Aktualisierung für die Azure SQL-Datenbank bei der Bearbeitung der Anmeldeinformationen einen Fehler mit Fehlercode 400 erhalten, versuchen Sie Folgendes, um die entsprechende Firewall-Regel einzurichten:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

1. Wechseln Sie zu der Instanz von Azure SQL-Datenbank, für die Sie die Aktualisierung konfigurieren.

1. Wählen Sie oben auf dem Blatt **Übersicht** die Option **Serverfirewall festlegen** aus.

1. Stellen Sie auf dem Blatt **Firewalleinstellungen** sicher, dass **Allow access to Azure services** (Zugriff auf Azure-Dienste erlauben) auf **ON** (EIN) festgelegt ist.

    ![„Zulässige Dienste“ in Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
