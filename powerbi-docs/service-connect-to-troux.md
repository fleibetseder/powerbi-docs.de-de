---
title: Herstellen einer Verbindung mit Troux mithilfe von Power BI
description: Troux für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9152538204089ed9c75b69b79a08dc7496a8cca9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61156158"
---
# <a name="connect-to-troux-for-power-bi"></a>Herstellen einer Verbindung mit Troux für Power BI
Mit dem Troux-Inhaltspaket können Sie Ihr Unternehmensarchitektur-Repository direkt in Power BI auf ganz neue Weise visualisieren. Das Inhaltspaket eröffnet Ihnen eine Reihe von Einsichten in Ihre Geschäftsperspektiven, die Anwendungen, die diese Perspektiven bereitstellen, und die Technologien, die diese Anwendungen unterstützen. All das in Power BI umfassend anpassbar.

Stellen Sie eine Verbindung zum [Troux-Inhaltspaket](https://app.powerbi.com/getdata/services/troux) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-troux/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-troux/services.png)
3. Wählen Sie **Troux** \> **Abrufen** aus.
   
   ![](media/service-connect-to-troux/troux.png)
4. Geben Sie Ihre Troux-OData-URL an. Unten finden Sie Einzelheiten zum [Suchen dieser Parameter](#FindingParams).
   
   ![](media/service-connect-to-troux/params.png)
5. Wählen Sie als **Authentifizierungsmethode** **Standard** aus, und geben Sie Ihren Benutzernamen und Ihr Kennwort ein (Groß- und Kleinschreibung müssen beachtet werden), und wählen Sie dann **Anmelden**aus.
   
    ![](media/service-connect-to-troux/creds.png)
6. Nach der Genehmigung wird der Importvorgang automatisch gestartet. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
     ![](media/service-connect-to-troux/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Zugriff auf den Troux-OData-Feed und Troux 9.5.1 oder höher sind erforderlich.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Ihr Kundenbetreuungsteam kann Ihnen die eindeutige URL für Ihren Troux-OData-Feed zur Verfügung stellen

## <a name="troubleshooting"></a>Problembehandlung
Wenn nach der Eingabe der Anmeldeinformationen ein Timeoutfehler angezeigt wird, versuchen Sie, die Verbindung erneut herzustellen.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

