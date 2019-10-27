---
title: Verwenden von SSO (Single Sign-On, Einmaliges Anmelden) bei lokalen Datenquellen
description: Konfigurieren Ihres Gateways zur Aktivierung des SSO von Power BI bei lokalen Datenquellen
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b1379bb783b090362215eaf7c317bbea435d1eec
ms.sourcegitcommit: e533c65607bbba0f620fddabd6b107e5933772c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72259934"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Übersicht: Single Sign-On für Gateways in Power BI

Sie können nahtlose Verbindungen mit SSO gewährleisten und für Power BI-Berichte und -Dashboards das Aktualisieren aus lokalen Daten in Echtzeit ermöglichen, indem Sie Ihr lokales Datengateway entweder mit der eingeschränkten Delegierung von Kerberos oder Security Assertion Markup Language (SAML) konfigurieren. Das lokale Datengateway unterstützt das einmalige Anmelden über DirectQuery. Damit werden Verbindungen mit lokalen Datenquellen hergestellt.

Folgende Datenquellen werden derzeit unterstützt:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) und [SAML](service-gateway-sso-saml.md))
* SAP BW-Anwendungsserver ([Kerberos](service-gateway-sso-kerberos.md))
* SAP BW-Nachrichtenserver ([Kerberos](service-gateway-sso-kerberos.md)), Öffentliche Vorschau
* Oracle ([Kerberos](service-gateway-sso-kerberos.md)), Öffentliche Vorschau
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

Das einmalige Anmelden (SSO) für [M-Erweiterungen](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md) wird derzeit nicht unterstützt.

Wenn ein Benutzer mit einem DirectQuery-Bericht im Power BI-Dienst interagiert, kann jeder Kreuzfilter-, Segmentierungs-, Sortier- und Berichtsbearbeitungsvorgang Abfragen bewirken, die live für die zugrunde liegende Datenquelle ausgeführt werden. Wenn SSO für die Datenquelle konfiguriert ist, werden Abfragen unter der Identität des Benutzers ausgeführt, der mit Power BI interagiert (d.h. über die Webumgebung oder mobile Power BI-Apps). Somit sieht jeder Benutzer genau die Daten, für die er in der zugrunde liegenden Datenquelle über Berechtigungen verfügt – bei aktiviertem einmaligen Anmelden erfolgt keine Zwischenspeicherung freigegebener Daten für verschiedene Benutzer.

## <a name="query-steps-when-running-sso"></a>Abfrageschritte beim Ausführen von SSO

Eine mit SSO ausgeführte Abfrage umfasst drei Schritte, wie in der folgenden Abbildung veranschaulicht.

![SSO-Abfrageschritte](media/service-gateway-sso-overview/sso-query-steps.png)

Es folgen weitere Details zu diesen Schritten:

1. Der **Power BI-Dienst** enthält für jede Abfrage den *Benutzerprinzipalnamen* (UPN, d. h. der voll qualifizierte Benutzernamen des Benutzers, der zurzeit beim Power BI-Dienst angemeldet ist), wenn eine Abfrageanforderung an das konfigurierte Gateway gesendet wird.

2. Das Gateway muss den Azure Active Directory-UPN einer lokalen Active Directory-Identität zuordnen.

   a.  Wenn Azure AD DirSync (auch als *Azure AD Connect* bezeichnet) konfiguriert ist, erfolgt die Zuordnung automatisch im Gateway.

   b.  Andernfalls kann das Gateway den Azure AD-UPN suchen und einem lokalen AD-Benutzer zuordnen. Dies erfolgt durch eine Suche in der lokalen Active Directory-Domäne.

3. Der Prozess des Gatewaydiensts nimmt die Identität des zugeordneten lokalen Benutzers an, öffnet die Verbindung mit der zugrunde liegenden Datenbank und sendet die Abfrage. Das Gateway muss nicht auf denselben Computern wie die Datenbank installiert sein.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie sich nun grundlegend mit SSO über das Gateway auskennen, können Sie sich ausführlichere Informationen zu Kerberos und SAML ansehen:

* [Einmaliges Anmelden (SSO): Kerberos](service-gateway-sso-kerberos.md)
* [Einmaliges Anmelden (SSO): SAML](service-gateway-sso-saml.md)
