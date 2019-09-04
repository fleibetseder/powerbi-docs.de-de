---
title: Konfigurationseinstellungen für die Power BI-iOS-App
description: Benutzerspezifisches Anpassen des Verhaltens von Power BI für iOS mithilfe des MDM-Tools
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160152"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Remotekonfiguration der Power BI-iOS-App mithilfe des Tools für die Masterdatenverwaltung (MDM)

Die mobile Power BI-iOS-App unterstützt App-Einstellungen, die Administratoren für Office 365 und die Masterdatenverwaltung (MDM) wie Intune das Anpassen des Verhaltens der App ermöglichen.

Die mobile Power BI-App für iOS unterstützt die folgenden Konfigurationsszenarios:

- Berichtsserverkonfiguration
- Datenschutzeinstellungen

## <a name="report-server-configuration"></a>Berichtsserverkonfiguration

Mit der Power BI-iOS-App können Administratoren Berichtsserverkonfigurationen remote mithilfe von „Push“ auf registrierte Geräte übertragen.

| Schlüssel | Typ | Beschreibung |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Zeichenfolge | Berichtsserver-URL<br><br>Muss mit http/https beginnen.|
| com.microsoft.powerbi.mobile.ServerUsername | Zeichenfolge | [Optional]<br><br>Der Benutzername, der zum Verbinden des Servers verwendet wird.<br><br>Wenn keiner vorhanden ist, fordert die App den Benutzer auf, den Benutzernamen für die Verbindung einzugeben.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Zeichenfolge | [Optional]<br><br>Der Standardwert ist „Berichtsserver“.<br><br>Ein Anzeigename, der in der App zur Darstellung des Servers verwendet wird. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolescher Wert | [Optional]<br><br>Der Standardwert ist TRUE. Wenn der Wert TRUE festgelegt ist, werden sämtliche Berichtsserverdefinitionen überschrieben, die möglicherweise bereits auf dem mobilen Gerät gespeichert sind. Alle Server, die bereits konfiguriert wurden, werden gelöscht. Wenn die Außerkraftsetzung auf TRUE festgelegt ist, wird dadurch auch verhindert, dass der Benutzer diese Konfiguration entfernt.<br><br>Bei FALSE werden die mithilfe von Push übertragenen Werte hinzugefügt, und vorhandene Einstellungen werden beibehalten. Wenn dieselbe Server-URL bereits in der mobilen App konfiguriert ist, werden keine Änderungen an der Konfiguration durch die App vorgenommen. Die App fordert den Benutzer nicht dazu auf, für denselben Server noch mal eine Authentifizierung durchzuführen. |

## <a name="data-protection-setting"></a>Datenschutzeinstellung

Die Power BI-iOS-App bietet Administratoren die Möglichkeit, die Standardkonfiguration für Sicherheits- und Datenschutzeinstellungen anzupassen. Sie können erzwingen, dass Benutzer ihre Face ID, Touch ID oder ihren Passcode bereitstellen müssen, wenn sie auf die Power BI-App zugreifen.

| Schlüssel | Typ | Beschreibung |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolescher Wert | Der Standardwert ist FALSE. <br><br>Biometrische Methoden wie TouchID oder FaceID können für den Zugriff von Benutzern auf die App auf ihrem Gerät erforderlich sein. Wenn dies der Fall ist, werden biometrische Methoden zusätzlich zur Authentifizierung verwendet.<br><br>Microsoft empfiehlt bei Verwendung von App-Schutzrichtlinien das Deaktivieren dieser Einstellung, um zwei Aufforderungen hinsichtlich des Zugriffs zu verhindern. |

## <a name="deploying-app-configuration-settings"></a>Bereitstellen von App-Konfigurationseinstellungen

Führen Sie die folgenden Schritte aus, um eine App-Konfigurationsrichtlinie zu erstellen. Nachdem die Konfigurationsrichtlinie erstellt wurde, können Sie die Einstellungen Benutzergruppen zuweisen.

1. Verbinden Sie Ihr MDM-Tool.

2. Erstellen Sie einen Namen und eine neue Richtlinie für die App-Konfiguration.

3. Wählen Sie aus, an welchen Benutzer diese Richtlinie für die App-Konfiguration verteilt wird.

4. Erstellen Sie Schlüssel-Wert-Paare für die Einstellung, die Sie mithilfe von Push an Ihre Benutzer übertragen möchten.

Mithilfe des Intune-Portals können Administratoren diese Einstellungen ganz einfach über App-Konfigurationsrichtlinien in Power BI-iOS-Apps bereitstellen.
Dabei werden alle MDM-Anbieter unterstützt. Wenn Sie Intune nicht verwenden, finden Sie Informationen zum Bereitstellen dieser Einstellungen in der MDM-Dokumentation.

## <a name="next-steps"></a>Nächste Schritte

* Laden Sie die [mobile Power BI iPhone-App](http://go.microsoft.com/fwlink/?LinkId=522062) herunter.
* Folgen Sie [@MSPowerBI auf Twitter](https://twitter.com/MSPowerBI)
* Werden Sie Teil der [Power BI-Community](http://community.powerbi.com/), um sich mit den Mitgliedern auszutauschen
