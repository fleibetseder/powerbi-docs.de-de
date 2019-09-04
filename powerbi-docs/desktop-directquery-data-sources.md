---
title: Von DirectQuery in Power BI unterstützte Datenquellen
description: Rufen Sie eine Liste der Datenquellen ab, die DirectQuery verwenden können.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 5455a5f3b4bda6cf6d63825222822c4acfa5f03a
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70159945"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Von DirectQuery in Power BI unterstützte Datenquellen

**Power BI Desktop** und der **Power BI-Dienst** verfügen über viele Datenquellen, mit denen Sie Verbindungen herstellen und auf deren Daten Sie zugreifen können. Dieser Artikel beschreibt, welche Datenquellen für Power BI die als **DirectQuery** bezeichnete Verbindungsmethode unterstützen. Weitere Informationen zu DirectQuery finden Sie unter [**DirectQuery in Power BI**](desktop-directquery-about.md).

Die folgenden Datenquellen unterstützen DirectQuery in Power BI:

* Amazon Redshift
* AtScale (Beta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL-Datenbank](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Google BigQuery
* HDInsight Interactive Query
* IBM DB2-Datenbank
* IBM Netezza
* Impala (Version 2.x)
* MarkLogic
* Oracle-Datenbank (Version 12 und höher)
* Oracle Essbase
* SAP Business Warehouse-Anwendungsserver
* SAP Business Warehouse-Nachrichtenserver
* SAP HANA
* Snowflake
* Spark (Version 0.9 und höher)
* SQL Server
* Teradata-Datenbank
* Vertica

Datenquellen, auf deren Namen **(Beta)** oder **(Vorschau)** folgt, unterliegen noch Änderungen und werden für den Einsatz in Produktionsumgebungen nicht unterstützt. Möglicherweise werden sie auch nach dem Veröffentlichen eines Berichts im **Power BI-Dienst** nicht unterstützt, was bedeutet, dass das Öffnen eines veröffentlichten Berichts oder das Untersuchen des Datasets zu einem Fehler führen kann.

Der einzige Unterschied zwischen als **(Beta)** und als **(Vorschau)** gekennzeichneten Datenquellen besteht darin, dass **(Vorschau)** -Datenquellen als Vorschaufunktion aktiviert werden müssen, um zur Verwendung verfügbar zu sein. Um einen **(Vorschau)** -Datenconnector zu aktivieren, wechseln Sie in **Power BI Desktop** zu **Datei > Optionen und Einstellungen > Optionen** und dann zu **Vorschaufeatures**.

> [!NOTE]
> DirectQuery-Abfragen an SQL Server erfordern die Authentifizierung mit aktuellen Anmeldeinformationen für die Windows-Authentifizierung oder Datenbankanmeldeinformationen, um Zugang herzustellen. Alternative Anmeldeinformationen werden nicht unterstützt.
>

## <a name="on-premises-gateway-requirements"></a>Anforderungen an lokale Gateways
Die folgende Tabelle gibt an, ob für das Herstellen von Verbindungen mit der angegebenen Datenquelle nach dem Veröffentlichen eines Berichts im **Power BI-Dienst** ein **Lokales Datengateway** erforderlich ist.

| Quelle | Gateway erforderlich? |
| --- | --- |
| Amazon Redshift |Nein |
| Azure HDInsight Spark (Beta) |Nein |
| Azure SQL-Datenbank |Nein |
| Azure SQL Data Warehouse |Nein |
| Google BigQuery |Nein |
| IBM Netezza |Ja |
| Impala (Version 2.x) |Ja |
| Oracle-Datenbank |Ja |
| SAP Business Warehouse-Anwendungsserver |Ja |
| SAP Business Warehouse-Nachrichtenserver |Im **Power BI-Dienst** noch nicht unterstützt |
| SAP HANA |Ja |
| Snowflake |Ja |
| Spark (Beta) (Version 0.9 und höher) |Ja |
| SQL Server |Ja |
| Teradata-Datenbank |Ja |

## <a name="single-sign-on-sso-for-directquery-sources"></a>Einmaliges Anmelden (SSO) für DirectQuery-Quellen

Wenn die Option „SSO“ aktiviert ist und Benutzer auf Berichte zugreifen, die auf der Datenquelle beruhen, werden deren authentifizierte Azure AD-Anmeldeinformationen von Power BI in den Abfragen an die zugrunde liegende Datenquelle gesendet. Dadurch wird sichergestellt, dass die auf Datenquellenebene konfigurierten Sicherheitseinstellungen in Power BI berücksichtigt werden.

Die SSO-Option gilt für alle Datasets, die diese Datenquelle verwenden. Sie hat keine Auswirkungen auf das Authentifizierungsverfahren, das bei Importszenarien verwendet wird. Die folgenden Datenquellen unterstützen SSO für Verbindungen mithilfe von DirectQuery:

- Azure SQL-Datenbank
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) wird nicht unterstützt. Benutzer, die SSO mit DirectQuery verwenden möchten, müssen von MFA ausgenommen werden.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu DirectQuery finden Sie in den folgenden Ressourcen:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [Lokales Datengateway](service-gateway-onprem.md)

