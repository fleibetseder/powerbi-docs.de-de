---
title: Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP HANA
description: Konfigurieren Ihres SAP HANA-Servers, um einmaliges Anmelden vom Power BI-Dienst zu aktivieren
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4e94781b3a424e894e0f0e2209ec48efb25c5db5
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106306"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP HANA

In diesem Artikel wird beschrieben, wie Sie Ihren SAP HANA-Server dafür konfigurieren, dass SSO vom Power BI-Dienst aktiviert wird.

> [!NOTE]
> Führen Sie die Schritte in diesem Artikel zusätzlich zu den Schritten in [Konfigurieren von Kerberos-SSO](service-gateway-sso-kerberos.md) aus, bevor Sie versuchen, einen SAP HANA-basierten Bericht, der Kerberos-SSO verwendet, zu aktualisieren.

## <a name="enable-sso-for-sap-hana"></a>Aktivieren von SSO für SAP HANA

Gehen Sie folgendermaßen vor, um SSO für SAP HANA zu aktivieren:

* Vergewissern Sie sich, dass auf dem SAP HANA-Server die erforderliche Mindestversion ausgeführt wird (abhängig von der Plattformebene Ihres SAP HANA-Servers):
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Installieren Sie auf dem Gatewaycomputer den aktuellen HANA-ODBC-Treiber von SAP.  Die Mindestversion ist die HANA-ODBC-Version 2.00.020.00 vom August 2017.

Stellen Sie sicher, dass der SAP HANA-Server für Kerberos-basiertes SSO konfiguriert wurde. Weitere Informationen zum Einrichten von SSO für SAP HANA mit Kerberos finden Sie im SAP HANA Security Guide im Thema [Single Sign-On Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Einmaliges Anmelden mit Kerberos). Sehen Sie sich außerdem die Links auf dieser Seite an – insbesondere den SAP-Hinweis 1837331 (HOWTO HANA DBSSO Kerberos/Active Directory).

Wir empfehlen außerdem, diese zusätzlichen Schritte durchzuführen, die eine geringfügige Verbesserung der Leistung bewirken können.

1. Suchen Sie im Gatewayinstallationsverzeichnis die folgende Konfigurationsdatei, und öffnen Sie sie: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Suchen Sie die Eigenschaft *FullDomainResolutionEnabled*, und ändern Sie ihren Wert in *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Jetzt können Sie [einen Power BI-Bericht ausführen](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum **lokalen Datengateway** und zu **DirectQuery** finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
