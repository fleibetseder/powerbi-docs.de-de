---
title: "Power BI-Verwaltungsportal"
description: "Das Verwaltungsportal ermöglicht die Mandantenverwaltung von Power BI in Ihrer Organisation. Es enthält Elemente wie z. B. Nutzungsmetriken und Zugriff auf das Office 365 Admin Center und die Einstellungen."
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
ms.date: 11/27/2017
ms.author: asaxton
ms.openlocfilehash: d831363d6afa88aa94d78776f59f81ba8ba96299
ms.sourcegitcommit: 85302d577895e779466df55aa02e5785ab2e3138
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2017
---
# <a name="power-bi-admin-portal"></a>Power BI-Verwaltungsportal

Das Verwaltungsportal ermöglicht die Mandantenverwaltung von Power BI in Ihrer Organisation. Es enthält Elemente wie z. B. Nutzungsmetriken und Zugriff auf das Office 365 Admin Center und die Einstellungen.

Die Mandantenverwaltung von Power BI für Ihr Unternehmen erfolgt über das Power BI-Verwaltungsportal. Auf das Verwaltungsportal können alle Benutzer zugreifen, die globale Administratoren in Office 365 sind oder der Power BI-Dienstadministratorrolle zugewiesen wurden. Weitere Informationen zur Power BI-Dienstadministratorrolle finden Sie unter [Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md).

Für alle Benutzer wird **Verwaltungsportal** unter dem Zahnradsymbol angezeigt. Ein Benutzer, der kein Administrator ist, sieht nur den Abschnitt **Premium-Einstellungen** und nur die Kapazitäten, für die er die Berechtigung zum Verwalten hat.

## <a name="how-to-get-to-the-admin-portal"></a>Gewusst wie: Anzeigen des Verwaltungsportals

Ihr Konto muss in Office 365 oder Azure Active Directory als **Globaler Administrator** markiert oder der Power BI-Dienstadministratorrolle zugewiesen sein, damit Sie Zugriff auf das Power BI-Verwaltungsportal erhalten. Weitere Informationen zur Power BI-Dienstadministratorrolle finden Sie unter [Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md). Führen Sie zum Zugreifen auf das Power BI-Verwaltungsportal die folgenden Schritte aus.

1. Wählen Sie das Zahnradsymbol für die Einstellungen oben rechts im Power BI-Dienst aus.
2. Wählen Sie **Verwaltungsportal** aus.

![](media/service-admin-portal/powerbi-admin-settings.png)

Es gibt innerhalb des Portals fünf Registerkarten. Diese werden nachfolgend beschrieben.

* [Nutzungsmetriken](#usage-metrics)
* [Benutzer](#users)
* [Überwachungsprotokolle](#audit-logs)
* [Mandanteneinstellungen](#tenant-settings)
* [Premium-Einstellungen](#premium-settings)
* [Einbindungscodes](#embed-codes)

![](media/service-admin-portal/powerbi-admin-landing-page.png)

## <a name="usage-metrics"></a>Nutzungsmetriken
Die erste Registerkarte im Verwaltungsportal heißt **Nutzungsmetriken**. Der Bericht zu den Nutzungsmetriken erlaubt Ihnen das Überwachen der Nutzung in Power BI für Ihre Organisation. Außerdem können Sie darüber feststellen, welche Benutzer und Gruppen in Power BI für Ihre Organisation am aktivsten sind.

> [!NOTE]
> Beim ersten Zugriff auf das Dashboard oder beim Anzeigen des Dashboards nach einem längeren Zeitraum wird zunächst wahrscheinlich ein Ladebildschirm angezeigt, während das Dashboard geladen wird.

Nachdem das Dashboard geladen wurde, werden zwei Abschnitte von Kacheln angezeigt. Der erste Abschnitt enthält Nutzungsdaten für einzelne Benutzer, und der zweite Abschnitt enthält ähnliche Informationen für die Gruppen in Ihrer Organisation.

Im Folgenden sehen Sie, was in den einzelnen Kacheln angezeigt wird:

* Anzahl der verschiedenen Dashboards, Berichte und Datasets im Arbeitsbereich eines Benutzers
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* Das am häufigsten verwendete Dashboard nach Anzahl von Benutzern, die darauf zugreifen können. Wenn Sie z. B. ein Dashboard für drei Benutzer freigegeben haben und dieses auch einem Inhaltspaket hinzugefügt haben, mit dem zwei andere Benutzer verbunden sind, beträgt die Anzahl 6 (1 + 3 + 2).
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* Der beliebteste Inhalt, mit dem Benutzer Verbindungen herstellen. Dies kann alles sein, worauf Benutzer durch den Vorgang zum Abrufen von Daten zugreifen können, z. B. SaaS-Pakete, organisationsbezogene Inhaltspakete, Dateien oder Datenbanken.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* Eine Ansicht der aktivsten Benutzer basierend auf der Anzahl von Dashboards. Dies können von den Benutzern selbst erstellte Dashboards sein, aber auch Dashboards, die für sie freigegeben wurden.
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* Eine Ansicht der aktivsten Benutzer basierend auf der Anzahl von Berichten
  
    ![](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

Der zweite Abschnitt zeigt dieselben Informationen basierend auf Gruppen an. So können Sie sehen, welche Gruppen in Ihrer Organisation besonders aktiv sind und welche Art von Informationen sie verwenden.

Mit diesen Informationen erhalten Sie wichtige Einblicke in die Verwendung von Power BI in Ihrer Organisation. Außerdem können Sie sehr schnell ermitteln, welche Benutzer und Gruppen in Ihrer Organisation besonders aktiv sind.

## <a name="users"></a>Benutzer

Die zweite Registerkarte im Verwaltungsportal ist **Benutzer verwalten**. Die Benutzerverwaltung für Power BI erfolgt im Office 365 Admin Center. Über diesen Bereich erreichen Sie sehr schnell die Bereiche zum Verwalten von Benutzern, Administratoren und Gruppen in Office 365.

![](media/service-admin-portal/powerbi-admin-manage-users.png)

Wenn Sie auf **Zum O365 Admin Center wechseln** klicken, gelangen Sie direkt zur Startseite von Office 365 Admin Center, auf der Sie die Benutzer Ihres Mandanten verwalten können.

![](media/service-admin-portal/powerbi-admin-o365-admin-center.png)

## <a name="audit-logs"></a>Überwachungsprotokolle

Die dritte Registerkarte im Verwaltungsportal ist **Überwachungsprotokolle**. Die Protokolle sind im Office 365 Security & Compliance Center gespeichert. Über diesen Abschnitt können Sie schnell auf diesen Bereich in Office 365 zugreifen. 

Weitere Informationen zu Überwachungsprotokollen finden Sie unter [Überwachen von Power BI in Ihrer Organisation](service-admin-auditing.md).

## <a name="tenant-settings"></a>Mandanteneinstellungen

Die dritte Registerkarte im Verwaltungsportal ist **Mandanteneinstellungen**. Über die Mandanteneinstellungen können Sie besser steuern, welche Features in Ihrer Organisation zur Verfügung gestellt werden. Wenn Sie über vertrauliche Daten verfügen, die geschützt werden müssen, sind möglicherweise einige unserer Features für Ihre Organisation nicht sinnvoll, oder Sie können ein bestimmtes Feature nur für eine bestimmte Gruppe verfügbar machen. Sie können diese Funktion in diesem Fall in Ihrem Mandanten deaktivieren.

![](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> Es dauert bis zu zehn Minuten, bis die Einstellung für alle Benutzer in Ihrem Mandanten wirksam werden.

Abhängig von den von Ihnen angegebenen Einstellungen können Einstellungen drei Status aufweisen.

### <a name="disabled-for-the-entire-organization"></a>Für die gesamte Organisation deaktiviert

Sie können ein Feature deaktivieren und festlegen, dass es nicht von Benutzern verwendet werden kann.

![](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

### <a name="enabled-for-the-entire-organization"></a>Für die gesamte Organisation aktiviert

Sie können ein Feature für die gesamte Organisation aktivieren, sodass alle Benutzer Zugriff auf dieses Feature haben.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

### <a name="enabled-for-a-subset-of-the-organization"></a>Für einen Teilsatz der Organisation aktiviert

Sie können ein Feature auch für einen Teil Ihrer Organisation aktivieren. Dies kann auf unterschiedliche Weise erfolgen. Sie können das Feature für die gesamte Organisation mit Ausnahme einer bestimmten Gruppe von Benutzern aktivieren.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

Sie können auch das Feature nur für eine bestimmte Gruppe von Benutzern aktivieren und außerdem für eine Gruppe von Benutzern deaktivieren. So stellen Sie sicher, dass bestimmte Benutzer keinen Zugriff auf das Feature haben, auch wenn sie Mitglied der Gruppe sind, für die der Zugriff aktiviert ist.

![](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

## <a name="export-and-sharing-settings"></a>Einstellungen für Export und Freigabe

### <a name="share-content-to-external-users"></a>Freigeben von Inhalten für externe Benutzer

Benutzer in der Organisation können Dashboards für Benutzer außerhalb der Organisation freigeben.

![](media/service-admin-portal/powerbi-admin-sharing-external.png)

### <a name="publish-to-web"></a>Webveröffentlichung

Benutzer in der Organisation können Berichte im Web veröffentlichen. [Weitere Informationen](service-publish-to-web.md)

![](media/service-admin-portal/powerbi-admin-publish-to-web.png)

Die Benutzer sehen auf der Benutzeroberfläche unterschiedliche Optionen, abhängig von der Einstellung zum Veröffentlichen im Web.

|Ausgewählt |Für die gesamte Organisation aktiviert |Für die gesamte Organisation deaktiviert |Bestimmte Sicherheitsgruppen   |
|---------|---------|---------|---------|
|**Im Web veröffentlichen** im Menü **Datei** des Berichts.|Für alle aktiviert|Nicht für alle sichtbar|Nur für autorisierte Benutzer oder Gruppen sichtbar|
|**Einbindungscodes verwalten** unter **Einstellungen**|Für alle aktiviert|Für alle aktiviert|Für alle aktiviert<br><br>Option * **Löschen** nur für autorisierte Benutzer oder Gruppen<br>* **Codes abrufen** für alle aktiviert|
|**Einbindungscodes** im Verwaltungsportal|Es wird einer der folgenden Status angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert|Als Status wird **Deaktiviert** angezeigt.|Es wird einer der folgenden Status angezeigt:<br>* Aktiv<br>* Nicht unterstützt<br>* Blockiert<br><br>Wenn ein Benutzer gemäß den Mandanteneinstellungen nicht autorisiert ist, wird als Status **Verletzt** angezeigt.|
|Vorhandene veröffentlichte Berichte|Alle aktiviert|Alle deaktiviert|Berichte werden weiterhin für alle gerendert.|

### <a name="export-data"></a>Daten exportieren

Benutzer in der Organisation können Daten aus einer Kachel oder Visualisierung exportieren. [Weitere Informationen](power-bi-visualization-export-data.md)

![](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> Durch Deaktivieren von **Daten exportieren** wird zudem verhindert, dass Benutzer das Feature **In Excel analysieren** sowie die Liveverbindung des Power BI-Diensts verwenden können.

### <a name="export-reports-as-powerpoint-presentations"></a>Berichte als PowerPoint-Präsentationen exportieren

Benutzer in der Organisation können Power BI-Berichte als PowerPoint-Dateien exportieren. [Weitere Informationen](service-publish-to-powerpoint.md)

![](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>Drucken von Dashboards und Berichten

Benutzer in der Organisation können Dashboards und Berichte drucken. [Weitere Informationen](service-print.md)

![](media/service-admin-portal/powerbi-admin-print-dashboard.png)

![](media/service-admin-portal/powerbi-admin-print-report.png)

## <a name="content-pack-settings"></a>Inhaltspaketeinstellungen

### <a name="publish-content-packs-to-the-entire-organization"></a>Inhaltspakete für gesamte Organisation veröffentlichen

Benutzer in der Organisation können Inhaltspakete in der gesamten Organisation veröffentlichen.

![](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-organizational-content-packs"></a>Erstellen von Vorlagenpaketen mit Organisationsinhalten

Benutzer in der Organisation können Vorlageninhaltspakete erstellen, die Datasets verwenden, die auf einer Datenquelle in Power BI Desktop basieren.

## <a name="integration-settings"></a>Integrationseinstellungen

### <a name="ask-questions-about-data-using-cortana"></a>Stellen von Fragen zu Daten mithilfe von Cortana
Benutzer in der Organisation können mithilfe von Cortana Fragen zu ihren Daten stellen.

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>Verwenden von In Excel analysieren mit lokalen Datasets
Benutzer in der Organisation können Excel verwenden, um lokale Power BI-Datasets anzuzeigen und mit ihnen zu interagieren. [Weitere Informationen](service-analyze-in-excel.md)

> [!NOTE]
> Durch das Deaktivieren von **Daten exportieren** wird zudem verhindert, dass Benutzer das Feature **In Excel analysieren** verwenden.

### <a name="user-arcgis-maps-for-power-bi-preview"></a>Verwenden von ArcGIS Maps für Power BI (Vorschau)

Benutzer in der Organisation können ArcGIS Maps von ESRI für Power BI-Visualisierungen (Vorschau) verwenden. [Weitere Informationen](power-bi-visualization-arcgis.md)

## <a name="r-visuals-settings"></a>Einstellungen für R-Visualisierungen

### <a name="interact-with-an-dshare-r-visuals"></a>Interagieren mit und Freigeben von R-Visualisierungen

Benutzer in der Organisation können mit visuellen Elementen, die mit R-Skripts erstellt wurden, interagieren und diese freigeben. [Weitere Informationen](service-r-visuals.md)

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="audit-settings"></a>Überwachungseinstellungen

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>Erstellen von Überwachungsprotokollen für interne Aktivitätsüberwachung und Konformität

Benutzer in der Organisation können Aktionen überwachen, die in Power BI von anderen Benutzern in der Organisation ausgeführt werden. [Weitere Informationen](service-admin-auditing.md)

Diese Einstellung muss aktiviert sein, damit Überwachungsprotokolleinträge aufgezeichnet werden.

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="dashboard-settings"></a>Dashboardeinstellungen

### <a name="data-classification-for-dashboards"></a>Datenklassifizierung für Dashboards

Benutzer in der Organisation können Dashboards mit Klassifizierungen markieren, die Dashboardsicherheitsstufen angeben. [Weitere Informationen](service-data-classification.md)

> [!NOTE]
> Diese Einstellung gilt für die gesamte Organisation und kann nicht auf bestimmte Gruppen beschränkt werden.

## <a name="developer-settings"></a>Entwicklereinstellungen

### <a name="embed-content-in-apps"></a>Inhalt in Apps einbetten

Benutzer in der Organisation können Power BI-Dashboards und -Berichte in SaaS-Anwendungen (Software as a Service) einbetten. Ist diese Einstellung deaktiviert, ist es Benutzern nicht möglich, die REST-APIs zu verwenden, um Power BI-Inhalt in ihre Anwendungen einzubetten.

## <a name="premium-settings"></a>Premium-Einstellungen

Über die Registerkarte „Premium-Einstellungen“ können Sie jede Power BI Premium-Kapazität verwalten, die für Ihre Organisation erworben wurde. Alle Benutzer in Ihrer Organisation sehen die Registerkarte „Premium-Einstellungen“, können deren Inhalt aber nur sehen, wenn sie entweder als **Kapazitätsadministrator** oder als Benutzer zugewiesen sind, der Zuweisungsberechtigungen hat. Hat ein Benutzer keine Berechtigungen, wird die folgende Meldung angezeigt.

![](media/service-admin-portal/premium-settings-no-access.png "No access to Premium settings") (Kein Zugriff auf Premium-Einstellungen)

Weitere Informationen zum Verwalten von Premium-Einstellungen finden Sie unter [Verwalten von Power BI Premium](service-admin-premium-manage.md).

## <a name="embed-codes"></a>Einbindungscodes

![Einbindungscodes innerhalb des Power BI-Verwaltungsportals](media/service-admin-portal/embed-codes.png)

Als Administrator können Sie die Einbindungscodes anzeigen, die für Ihren Mandanten generiert werden. Als Aktionen können Sie den Bericht anzeigen und den Einbindungscode löschen, um ihn zu widerrufen.

## <a name="next-steps"></a>Nächste Schritte

[Grundlegendes zur Power BI-Administratorrolle](service-admin-role.md)  
[Überwachen von Power BI in Ihrer Organisation](service-admin-auditing.md)  
[Verwalten von Power BI Premium](service-admin-premium-manage.md)  
[Verwalten von Power BI in Ihrer Organisation](service-admin-administering-power-bi-in-your-organization.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](http://community.powerbi.com/)