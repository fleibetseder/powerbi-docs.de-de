---
title: Leitfaden zum Bereitstellen eines Datengateways für Power BI
description: Informationen zu bewährten Methoden und Überlegungen für das Bereitstellen eines Gateways für Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271724"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Leitfaden zum Bereitstellen eines Datengateways für Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Dieser Artikel bietet eine Anleitung sowie Überlegungen zur Bereitstellung eines Datengateways für Power BI in Ihrer Netzwerkumgebung.

Informationen zum Herunterladen, Installieren, Konfigurieren und Verwalten des lokalen Datengateways finden Sie unter [What is an on-premises data gateway (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-onprem). Weitere Informationen zum lokalen Datengateway und Power BI finden Sie zudem im [Microsoft Power BI-Blog](https://powerbi.microsoft.com/blog/) und in der [Microsoft Power BI-Community](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Hinweise zur Installation für das lokale Datengateway

Bevor Sie das lokale Datengateway für Ihren Power BI-Clouddienst installieren, sollten Sie einiges beachten. Dies wird in den folgenden Abschnitten beschrieben.

### <a name="number-of-users"></a>Anzahl von Benutzern

Die Anzahl der Benutzer, die einen Bericht nutzen, der das Gateway verwendet, ist eine wichtige Metrik bei der Entscheidung, wo das Gateway installiert werden soll. Hier sind einige Fragen, die es zu berücksichtigen gilt:

* Verwenden Benutzer diese Berichte zu unterschiedlichen Tageszeiten?
* Welche Arten von Verbindungen verwenden sie (DirectQuery oder Import)?
* Verwenden alle Benutzer denselben Bericht?

Wenn alle Benutzer gleichzeitig auf einen angegebenen Bericht zugreifen, sollten Sie sicherstellen, dass Sie das Gateway auf einem Computer installieren, der all diese Anforderungen verarbeiten kann (die folgenden Abschnitte enthalten Leistungsindikatoren sowie Mindestanforderungen, die Ihnen dabei helfen, dies zu bestimmen).

Es existiert eine Einschränkung in **Power BI**, die nur *ein* Gateway pro *Bericht* zulässt. Also auch wenn ein Bericht auf mehreren Datenquellen basiert, müssen all diese Datenquellen ein einzelnes Gateway durchlaufen. Wenn jedoch ein Dashboard auf *mehreren* Berichten basiert, können Sie ein dediziertes Gateway für jeden beitragenden Bericht verwenden, um die Gatewaylast zwischen den Berichten zu verteilen, die zu diesem einzelnen Dashboard beitragen.

### <a name="connection-type"></a>Verbindungstyp

**Power BI** bietet zwei Arten von Verbindungen: **DirectQuery** und **Import**. Nicht alle Datenquellen unterstützen beide Verbindungstypen, und viele verschiedene Gründe tragen möglicherweise dazu bei, dass jeweils ein Typ bevorzugt wird, z.B. Sicherheitsanforderungen, Leistung, Datenlimits und Datenmodellgrößen. Weitere Informationen zum Verbindungstyp und unterstützten Datenquellen finden Sie in der [Liste der verfügbaren Datenquellentypen](service-gateway-data-sources.md#list-of-available-data-source-types).

Je nachdem, welcher Verbindungstyp verwendet wird, kann die Gatewaynutzung variieren. Sie sollten beispielsweise versuchen, wenn möglich **DirectQuery**-Datenquellen von **ScheduledRefresh**-Datenquellen zu trennen (vorausgesetzt, sie befinden sich in unterschiedlichen Berichten und können getrennt werden). Dadurch wird verhindert, dass sich im Gateway tausende DirectQuery-Anforderungen in der Warteschlange befinden, wenn gleichzeitig die morgendlich geplante Aktualisierung eines großen Datenmodells stattfindet,das für das Hauptdashboard des Unternehmens verwendet wird. Berücksichtigen Sie deshalb Folgendes:

* Für die **geplante Aktualisierung**: Je nach Abfragegröße und Anzahl der pro Tag auftretenden Aktualisierungen können Sie sich zwischen den empfohlenen Mindestanforderungen für die Hardware und das Upgrade auf einen Computer mit höherer Leistung entscheiden. Wenn eine bestimmte Abfrage nicht reduziert ist, treten Transformationen auf dem Gatewaycomputer auf, und daher profitiert der Gatewaycomputer von mehr verfügbarem RAM.

* Für **DirectQuery**: Jedes Mal, wenn ein Benutzer den Bericht öffnet oder Daten ansieht, wird eine Abfrage gesendet. Wenn also mehr als 1.000 Benutzer gleichzeitig auf die Daten zugreifen, müssen Sie sicherstellen, dass Ihr Computer über robuste und leistungsfähige Hardwarekomponenten verfügt. Mehr CPU-Kerne führen zu einem besseren Durchsatz für eine **DirectQuery**-Verbindung.

Die Anforderungen für einen für die Installation geeigneten Computer finden Sie in den [Installationsanforderungen](/data-integration/gateway/service-gateway-install#requirements) für das lokale Datengateway.

### <a name="location"></a>Standort

Der Speicherort der Gatewayinstallation kann erhebliche Auswirkungen auf Ihre Abfrageleistung haben. Stellen Sie also sicher, dass sich Ihr Gateway, die Speicherorte der Datenquelle sowie der Power BI-Mandant so nah wie möglich beieinander befinden, um die Netzwerklatenz zu reduzieren. Um den Speicherort Ihres Power BI-Mandaten im Power BI-Dienst zu bestimmen, wählen Sie das Fragezeichen **?** in der oberen rechten Ecke aus, und wählen Sie dann **Info** aus.

![Ermitteln des Speicherorts des Power BI-Mandanten](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Wenn Sie das Power BI-Gateway mit Azure Analysis Services verwenden möchten, stellen Sie zudem sicher, dass die Datenbereiche übereinstimmen. Weitere Informationen zum Festlegen von Datenbereichen für mehrere Dienste finden Sie in [diesem Video](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/).

## <a name="next-steps"></a>Nächste Schritte

* [Konfigurierung von Proxyeinstellungen](/data-integration/gateway/service-gateway-proxy)  
* [Lokales Datengateway – Problembehandlung](service-gateway-onprem-tshoot.md)  
* [On-premises data gateway FAQ - Power BI (Häufig gestellte Fragen zum lokalen Datengateway – Power BI)](service-gateway-power-bi-faq.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

