---
title: "Übersicht über das Inhaltspaketprogramm für den Power BI-Dienst"
description: "Zertifizierungsprogramm für Inhaltspakete"
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/09/2017
ms.author: asaxton
ms.openlocfilehash: 4a8ea2acfcfe41192b82addfe52dbe67a0df8088
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Übersicht über das Inhaltspaketprogramm für den Power BI-Dienst
Bei einem Inhaltspaket handelt es sich um sofort einsetzbare Inhalte, mit denen Benutzer unmittelbar Einblicke in eine Quelle gewinnen können. Ein Inhaltspaket konzentriert sich in der Regel auf ein bestimmtes Geschäftsszenario und ermöglicht Einblicke in eine Rolle, eine Domäne oder einen Workflow.

Unabhängige Softwarehersteller können Vorlageninhaltspakete erstellen, mit denen Kunden eine Verbindung mit ihren eigenen Konten herstellen und diese instanziieren können. Als Domänenexperten können sie die Daten so freigeben, dass diese von Geschäftskunden mühelos genutzt werden können. Die Inhaltspakete bieten Ad-hoc-Überwachung und -Analysen für Ihre Kunden ohne übermäßige Investition in die Berichterstellungsinfrastruktur. 

Diese von unabhängigen Softwareanbietern erstellten Vorlageninhaltspakete können an das Power BI-Team übermittelt werden, damit sie im Power BI-Inhaltspaketkatalog (app.powerbi.com/getdata/services) und in Microsoft AppSource (appsource.microsoft.com) öffentlich verfügbar gemacht werden. Ein Beispiel für die Nutzung eines öffentlichen Inhaltspakets finden Sie [hier](template-content-pack-experience.md).

## <a name="overview"></a>Übersicht
Das allgemeine Verfahren zum Entwickeln und Einreichen eines Vorlageninhaltspakets umfasst mehrere Schritte.

 ![Verfahren](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Überprüfen der Anforderungen](#requirements) und Sicherstellen, dass sie erfüllt werden
2. [Erstellen von Inhalten](template-content-pack-authoring.md#queries) in Power BI Desktop
3. [Erstellen eines Dashboards](template-content-pack-authoring.md#dashboard) auf „PowerBI.com“
4. [Testen des Inhaltspakets](template-content-pack-testing.md) in Ihrer Organisation
5. [Übermitteln](template-content-pack-testing.md#submission) der Inhalte zur Veröffentlichung an Power BI

<a name="requirements"></a>

## <a name="requirements"></a>Anforderungen
Zum Erstellen und Übermitteln eines Inhaltspakets, das im Power BI-Dienst und in AppSource veröffentlicht werden soll, müssen die folgenden Anforderungen erfüllt werden:

* Sie haben eine SaaS-Anwendung, die von Geschäftsbenutzern verwendet wird.
* Die SaaS-Anwendung enthält Benutzerdaten, die in Power BI visuell dargestellt werden können.
* Die SaaS-Anwendung verfügt über eine API, auf die über das öffentliche Internet zugegriffen werden kann. Im Idealfall handelt es sich bei der API um eine REST-basierte API oder einen OData-Feed. Power BI-Inhaltspakete unterstützen verschiedene Authentifizierungstypen, z.B. Standardauthentifizierung, OAuth 2.0 und API-Schlüssel. 
* Unterzeichnete Partnervereinbarung. Dies erfolgt beim [Übermitteln](template-content-pack-testing.md#submission).

Weitere Informationen zu den technischen Anforderungen finden Sie im Abschnitt zur [Erstellung](template-content-pack-authoring.md).

## <a name="business-scenario"></a>Geschäftsszenario
Inhaltspakete bieten Einblicke und Metriken mit Schwerpunkt auf einem bestimmten Geschäftsszenario. Das Verständnis Ihrer Zielgruppe und die Vorteile, die sich für sie aus dem Inhaltspaket ergeben, helfen sicherzustellen, dass Ihre Benutzer mit den bereitgestellten Inhalten Erfolge erzielen.

### <a name="tips"></a>Tipps
* Ermitteln Sie Ihre Zielgruppe und die Aufgabe, die sie zu bewerkstelligen versucht.  
* Konzentrieren Sie sich auf einen bestimmten Zeitraum (die letzten 90 Tage) oder die letzten n Ergebnisse.  
* Importieren Sie nur die auf Ihr Szenario bezogenen Tabellen oder Spalten.  
* Erwägen Sie die Bereitstellung mehrerer Inhaltspakete für separate, eindeutige Szenarios.  

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen
**Kann ich ein Inhaltspaket für den Power BI-Dienst für die SaaS-Anwendung eines Drittanbieters erstellen, die ich nicht besitze?**

Nein, zurzeit ist eine unterzeichnete Partnervereinbarung mit dem Besitzer der SaaS-Anwendung erforderlich, damit das Inhaltspaket im Dienst veröffentlicht werden kann.

**Ich habe keine öffentliche Entwickler-API für meinen Dienst. Kann ich trotzdem ein Inhaltspaket für den Power BI-Dienst erstellen, das die Daten direkt aus dem Datenspeicher abruft?**

Nein, für Inhaltspakete für den Power BI-Dienst ist eine Entwickler-API erforderlich, die über das öffentliche Internet zugänglich ist.

**Welche Arten von APIs werden von Dienstinhaltspaketen unterstützt und welche Authentifizierungstypen können verwendet werden?**

Inhaltspakete für den Power BI-Dienst unterstützen alle REST-APIs und OData-Feeds. Power BI kann mit mehreren Authentifizierungstypen arbeiten, u.a. Standardauthentifizierung, OAuth2.0 und Web API-Schlüssel. Weitere Informationen zu den technischen Anforderungen finden Sie im Artikel zur [Erstellung](template-content-pack-authoring.md#dashboard).

**Ich habe weitere Fragen zu Dienstinhaltspaketen. Wie kann ich Sie kontaktieren?**

Sie können Ihre Fragen per E-Mail an pbiservicesapps@microsoft.com senden.

## <a name="support"></a>Support
Unterstützung bei der Entwicklung erhalten Sie unter [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Diese Website wird aktiv betreut und verwaltet. Kundenanfragen werden schnell an das entsprechende Team weitergeleitet.

## <a name="next-step"></a>Nächster Schritt
[Erstellung](template-content-pack-authoring.md)
