---
title: Verwenden von benutzerdefinierten Datenconnectors mit dem lokalen Datengateway
description: Sie können benutzerdefinierte Datenconnectors mit dem lokalen Datengateway verwenden.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271806"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Verwenden von benutzerdefinierten Datenconnectors mit dem lokalen Datengateway

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Mithilfe der Datenconnectors für Power BI können Sie eine Verbindung zu Daten einer App, eines Diensts oder einer Datenquelle herstellen und auf diese zugreifen. Sie können benutzerdefinierte Datenconnectors entwickeln und diese in Power BI Desktop verwenden.

Weitere Informationen zum Entwickeln benutzerdefinierter Datenconnectors für Power BI finden auf der GitHub-Seite zum [Datenconnector SDK](http://aka.ms/dataconnectors). Diese Seite enthält Informationen zu den ersten Schritten sowie Beispiele für Power BI und Power Query.

Wenn Sie Berichte in Power BI Desktop erstellen, die benutzerdefinierte Datenconnectors nutzen, können Sie das lokale Datengateway dazu verwenden, diese Berichte über den Power BI-Dienst zu aktualisieren.

## <a name="how-to-enable-and-use-this-capability"></a>Aktivieren und Verwenden dieser Funktion

Wenn Sie die Version vom Juli 2018 oder eine höhere Version des lokalen Datengateways installieren, wird in der App des lokalen Datengateways die Registerkarte **Connectors** mit der Option angezeigt, einen Ordner auszuwählen, aus dem benutzerdefinierte Connectors geladen werden sollen. Wählen Sie einen Ordner aus, auf den der Benutzer zugreifen kann, der den Gatewaydienst (standardmäßig *NT SERVICE\PBIEgwService*) ausführt. Das Gateway lädt automatisch die benutzerdefinierten Connectordateien in diesem Ordner, die dann in der Liste der Datenconnectors angezeigt werden.

![Benutzerdefinierter Connector 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Wenn Sie das lokale Datengateway (persönlicher Modus) verwenden, können Sie an dieser Stelle Ihren Power BI-Bericht im Power BI-Dienst hochladen und das Gateway zum Aktualisieren verwenden.

Für das lokale Datengateway müssen Sie immer noch eine Datenquelle für Ihren benutzerdefinierten Connector erstellen. Auf der Seite „Gatewayeinstellungen“ im Power BI-Dienst sollte eine neue Option angezeigt werden, wenn Sie dem Gatewaycluster erlauben, benutzerdefinierte Connectors mit diesem Cluster zu verwenden. Vergewissern Sie sich, dass für alle Gateways im Cluster das Update vom Juli 2018 oder höher installiert ist, damit diese Option verfügbar ist. Wählen Sie nun diese Option aus, um das Verwenden von benutzerdefinierten Connectors mit diesem Cluster zu aktivieren.

![Benutzerdefinierter Connector 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

Wenn diese Option aktiviert ist, werden Ihre benutzerdefinierten Connectors als verfügbare Datenquellen angezeigt, die Sie in diesem Gatewaycluster erstellen können. Nach dem Erstellen einer Datenquelle mit Ihrem neuen benutzerdefinierten Connector können Sie die Power BI-Berichte aktualisieren, die diesen benutzerdefinierten Connector im Power BI-Dienst verwenden.

![Benutzerdefinierter Connector 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen

* Stellen Sie sicher, dass der erstellte Ordner für den Gatewaydienst im Hintergrund zugänglich ist. In der Regel ist der Zugriff auf Ordner unter Windows-Ordnern oder Systemordnern Ihres Benutzers nicht möglich. Die App des lokalen Datengateways zeigt eine Nachricht an, wenn der Ordner nicht zugänglich ist (gilt nicht für die persönliche Version des Gateways).
* Damit benutzerdefinierte Connectors mit dem lokalen Datengateway verwendet werden können, muss in deren Code ein „TestConnection“-Abschnitt implementiert werden. Dies ist nicht erforderlich, wenn benutzerdefinierte Connectors mit Power BI Desktop verwendet werden. Sie können einen benutzerdefinierten Connector nutzen, der zwar mit Power BI Desktop, aber nicht mit dem Gateway verwendet werden kann. Weitere Informationen zur Implementierung eines „TestConnection“-Abschnitts finden Sie in [dieser Dokumentation](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support).

## <a name="next-steps"></a>Nächste Schritte

* [Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Verwalten Ihrer Datenquelle –SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Verwalten Ihrer Datenquelle – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Verwalten der Datenquelle – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [Configure proxy settings for the on-premises data gateway (Konfigurieren von Proxyeinstellungen für das lokale Datengateway)](/data-integration/gateway/service-gateway-proxy)  
* [Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) von Power BI bei lokalen Datenquellen](service-gateway-sso-kerberos.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
