---
title: Problembehandlung bei der planmäßigen Aktualisierung für Azure SQL-Datenbanken
description: Problembehandlung bei der planmäßigen Aktualisierung für Azure SQL-Datenbanken in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4bc14b9a3d863732c581e8a144d612d864d65af8
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391830"
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
