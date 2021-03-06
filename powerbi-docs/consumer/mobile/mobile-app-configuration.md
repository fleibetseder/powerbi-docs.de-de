---
title: Konfigurationseinstellungen für die Power BI-App
description: Anpassen des Verhaltens von Power BI mithilfe des MDM-Tools
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: painbar
ms.openlocfilehash: 58b2f96b069815af448352b3b54875dc4d6b27ee
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538265"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Remotekonfiguration der Power BI-App mithilfe des Tools für die mobile Geräteverwaltung

Die Power BI Mobile-App für iOS und Android unterstützt App-Einstellungen, mit denen Administratoren von MDM-Diensten (mobile Geräteverwaltung) wie Intune das Verhalten der App anpassen können.

Die Power BI Mobile-App unterstützt die folgenden Konfigurationsszenarios:

* Berichtsserverkonfiguration (iOS und Android)
* Datenschutzeinstellungen (iOS und Android)
* Interaktionseinstellungen (Android)

## <a name="report-server-configuration-ios-and-android"></a>Berichtsserverkonfiguration (iOS und Android)

Die Power BI-App für iOS und Android ermöglicht Administratoren, die Berichtsserverkonfigurationen remote an registrierte Geräte zu pushen.

| Schlüssel | Typ | Beschreibung |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Zeichenfolge | Berichtsserver-URL<br><br>Muss mit http/https beginnen.|
| com.microsoft.powerbi.mobile.ServerUsername | Zeichenfolge | [Optional]<br><br>Der Benutzername, der zum Verbinden des Servers verwendet wird.<br><br>Wenn keiner vorhanden ist, fordert die App den Benutzer auf, den Benutzernamen für die Verbindung einzugeben.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Zeichenfolge | [Optional]<br><br>Der Standardwert ist „Berichtsserver“.<br><br>Ein Anzeigename, der in der App zur Darstellung des Servers verwendet wird. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolescher Wert | [Optional]<br><br>Der Standardwert ist TRUE. Wenn der Wert TRUE festgelegt ist, werden sämtliche Berichtsserverdefinitionen überschrieben, die möglicherweise bereits auf dem mobilen Gerät gespeichert sind. Alle Server, die bereits konfiguriert wurden, werden gelöscht. Wenn die Außerkraftsetzung auf TRUE festgelegt ist, wird dadurch auch verhindert, dass der Benutzer diese Konfiguration entfernt.<br><br>Bei FALSE werden die mithilfe von Push übertragenen Werte hinzugefügt, und vorhandene Einstellungen werden beibehalten. Wenn dieselbe Server-URL bereits in der mobilen App konfiguriert ist, werden keine Änderungen an der Konfiguration durch die App vorgenommen. Die App fordert den Benutzer nicht dazu auf, für denselben Server noch mal eine Authentifizierung durchzuführen. |

## <a name="data-protection-settings-ios"></a>Datenschutzeinstellungen (iOS)

Die Power BI-App für iOS und Android bietet Administratoren die Möglichkeit, die Standardkonfiguration der Sicherheits- und Datenschutzeinstellungen anzupassen. Sie können erzwingen, dass Benutzer Face ID, Touch ID oder ihren Passcode bereitstellen müssen, wenn sie auf die Power BI-App zugreifen.

| Schlüssel | Typ | Beschreibung |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolescher Wert | Der Standardwert ist FALSE. <br><br>Biometrische Methoden wie TouchID oder FaceID können für den Zugriff von Benutzern auf die App auf ihrem Gerät erforderlich sein. Wenn dies der Fall ist, werden biometrische Methoden zusätzlich zur Authentifizierung verwendet.<br><br>Microsoft empfiehlt bei Verwendung von App-Schutzrichtlinien das Deaktivieren dieser Einstellung, um zwei Aufforderungen hinsichtlich des Zugriffs zu verhindern. |

## <a name="interaction-settings-android"></a>Interaktionseinstellungen (Android)

Die Power BI-App für Android bietet Administratoren die Möglichkeit, die Interaktionseinstellungen zu konfigurieren, wenn die Standardeinstellungen für Interaktionen für mehrere Benutzergruppen in einer Organisation geändert werden müssen. 

| Schlüssel | Typ | Werte | Beschreibung |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Zeichenfolge |  <nobr>single-tap</nobr> (einfaches Tippen)<br><nobr>double-tap</nobr> (Doppeltippen) | Konfiguriert, ob durch das Tippen auf ein Visual auch ein Datenpunkt ausgewählt wird. |
| ccom.microsoft.powerbi.mobile.RefreshAction | Zeichenfolge |  <nobr>pull-to-refresh</nobr> (Zum Aktualisieren nach unten ziehen)<br>aus. | Konfiguriert, ob dem Benutzer eine Schaltfläche zum Aktualisieren des Berichts zur Verfügung gestellt wird oder ob er das Feature „Zum Aktualisieren nach unten ziehen“ verwenden soll. |
| com.microsoft.powerbi.mobile.FooterAppearance | Zeichenfolge |  docked (gedockt)<br>dynamisch | Konfiguriert, ob die Fußzeile des Berichts am unteren Rand angedockt oder automatisch ausgeblendet wird. |

## <a name="deploying-app-configuration-settings"></a>Bereitstellen von App-Konfigurationseinstellungen

Im folgenden werden die Schritte zum Erstellen einer App-Konfigurationsrichtlinie aufgeführt. Sobald Sie die Konfigurationsrichtlinie erstellt haben, können Sie ihre Einstellungen Benutzergruppen zuweisen.

1. Verbinden Sie Ihr MDM-Tool.
2. Erstellen Sie einen Namen und eine neue Richtlinie für die App-Konfiguration.
3. Wählen Sie aus, an welchen Benutzer diese Richtlinie für die App-Konfiguration verteilt wird.
4. Erstellen Sie Schlüssel-Wert-Paare für die Einstellung, die Sie mithilfe von Push an Ihre Benutzer übertragen möchten.

Mithilfe des Intune-Portals können Administratoren diese Einstellungen ganz einfach über App-Konfigurationsrichtlinien in der Power BI-App bereitstellen. Dabei werden alle MDM-Anbieter unterstützt. Wenn Sie nicht Intune verwenden, finden Sie Informationen zum Bereitstellen dieser Einstellungen in der MDM-Dokumentation.

## <a name="next-steps"></a>Nächste Schritte

* Laden Sie die Power BI Mobile-App aus dem [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) oder aus [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409) herunter.
* Folgen Sie [@MSPowerBI auf Twitter](https://twitter.com/MSPowerBI)
* Werden Sie Teil der [Power BI-Community](https://community.powerbi.com/), um sich mit den Mitgliedern auszutauschen
