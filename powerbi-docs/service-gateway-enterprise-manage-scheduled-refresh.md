---
title: Verwalten der Datenquelle – Import/Geplante Aktualisierung
description: So verwalten Sie On-premises data gateway und die zu diesem Gateway gehörigen Datenquellen. Dieser Artikel bezieht sich auf Datenquellen, die mit Import/Geplante Aktualisierung verwendet werden können.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2a3cdc3e6c4fc4f18613994a919f8ab733df5e14
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271700"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Verwalten der Datenquelle – Import/Geplante Aktualisierung

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Nach der [Installation des lokalen Datengateways](/data-integration/gateway/service-gateway-install) müssen Sie [Datenquellen hinzufügen](service-gateway-data-sources.md#add-a-data-source), die mit dem Gateway verwendet werden können. In diesem Artikel wird untersucht, wie mit Gateways und Datenquellen gearbeitet wird, die für die geplante Aktualisierung im Gegensatz zu DirectQuery oder Live-Verbindungen verwendet werden.

## <a name="add-a-data-source"></a>Hinzufügen einer Datenquelle

Weitere Informationen zum Hinzufügen einer Datenquelle finden Sie unter [Add a data source (Hinzufügen einer Datenquelle)](service-gateway-data-sources.md#add-a-data-source).

Alle aufgeführten Datenquellentypen können für die geplante Aktualisierung mit dem lokalen Datengateway verwendet werden. Analysis Services, SQL Server und SAP HANA können für die geplante Aktualisierung oder DirectQuery/Live-Verbindungen verwendet werden.

![Datenquelle auswählen](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Sie sollten dann die Angaben für die Datenquelle vervollständigen, zu denen die Quell- und Anmeldeinformationen gehören, die für den Zugriff auf die Datenquelle verwendet werden.

> [!NOTE]
> Alle Abfragen der Datenquelle werden mithilfe dieser Anmeldeinformationen durchgeführt. Weitere Informationen zum Speichern von Anmeldeinformationen finden Sie unter [Storing encrypted credentials in the cloud (Speichern verschlüsselter Anmeldeinformationen in der Cloud)](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Auffüllen der Datenquelleneinstellungen](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

Eine Liste der Datenquellentypen, die mit geplanten Aktualisierungen verwendet werden können, finden Sie unter [Liste der verfügbaren Datenquellentypen](service-gateway-data-sources.md#list-of-available-data-source-types).

Klicken Sie auf **Hinzufügen**, nachdem Sie alle Angaben eingetragen haben. Sie können jetzt diese Datenquelle für die geplante Aktualisierung mit Ihren lokalen Daten verwenden. Bei erfolgreicher Ausführung wird *Verbindung erfolgreich* angezeigt.

![Anzeigen des Verbindungsstatus](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

### <a name="advanced-settings"></a>Erweiterte Einstellungen

Optional können Sie die Datenschutzebene für die Datenquelle konfigurieren. Diese steuert, wie Daten kombiniert werden können. Diese wird nur für die geplante Aktualisierung verwendet Weitere Informationen zu Datenschutzebenen für Ihre Datenquelle finden Sie unter [Privacy levels (Power Query) (Datenschutzebenen (Power Query))](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Festlegen der Datenschutzebene](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>Verwenden der Datenquelle für geplanten Aktualisierungen

Nachdem Sie die Datenquelle erstellt haben, kann diese mit DirectQuery-Verbindungen oder durch eine geplante Aktualisierung verwendet werden.

> [!NOTE]
> Die Namen des Servers und der Datenbank müssen in Power BI Desktop und der Datenquelle innerhalb des lokalen Datengateways übereinstimmen.

Der Link zwischen Ihrem Dataset und der Datenquelle innerhalb des Gateways basiert auf dem Namen Ihres Servers und Ihrer Datenbank. Diese müssen übereinstimmen. Wenn Sie z. B. eine IP-Adresse für den Servernamen in Power BI Desktop angeben, müssen Sie die IP-Adresse für die Datenquelle innerhalb der Gatewaykonfiguration verwenden. Wenn Sie *SERVER\INSTANZ* verwenden, müssen Sie in Power BI Desktop dieselbe Instanz verwenden, die auch in der für das Gateway konfigurierten Datenquelle verwendet wird.

Wenn Sie auf der Registerkarte **Benutzer** der im Gateway konfigurierten Datenquelle aufgeführt sind und die Namen des Servers und der Datenbank übereinstimmen, wird das Gateway als Option für geplante Aktualisierungen angezeigt.

![Anzeigen der Benutzer](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Wenn Ihr Dataset mehrere Datenquellen enthält, muss jede dieser Datenquellen dem Gateway hinzugefügt werden. Wenn eine oder mehrere Datenquellen dem Gateway nicht hinzugefügt werden, wird das Gateway nicht als für die geplante Aktualisierung verfügbar angezeigt.

## <a name="limitations"></a>Einschränkungen

Für das lokale Datengateway wird das Authentifizierungsschema OAuth nicht unterstützt. Datenquellen, die OAuth erfordern, können nicht hinzugefügt werden. Wenn Ihr Dataset über eine Datenquelle verfügt, die OAuth erfordert, kann das Gateway nicht für die geplante Aktualisierung verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

* [Problembehandlung beim lokalen Datengateway](/data-integration/gateway/service-gateway-tshoot)
* [Lokales Datengateway – Problembehandlung](service-gateway-onprem-tshoot.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
