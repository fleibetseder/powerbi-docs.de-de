---
title: Herstellen einer Verbindung mit ClickDimensions mithilfe von Power BI
description: ClickDimensions für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 98be77e2cfe53e535dd322317246549a6b4324a4
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185963"
---
# <a name="connect-to-clickdimensions-with-power-bi"></a>Herstellen einer Verbindung mit ClickDimensions mithilfe von Power BI
Das ClickDimensions-Inhaltspaket für Power BI ermöglicht es Benutzern, ClickDimensions-Marketingdaten in Power BI zu verwenden. Dadurch erhalten Management-Teams bessere Einblicke in den Erfolg ihrer Vertriebs- und Marketingbemühungen. Visualisieren und analysieren Sie E-Mail-Interaktionen, Webseitenbesuche und Formularübermittlungen in Power BI-Dashboards und -Berichten.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [ClickDimensions-Inhaltspaket](https://app.powerbi.com/getdata/services/click-dimensions) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-clickdimensions/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-clickdimensions/services.png)
3. Wählen Sie **ClickDimensions** \> **Abrufen** aus.
   
   ![](media/service-connect-to-clickdimensions/clickdimensions.png)
4. Geben Sie den Ort Ihres Rechenzentrums an (USA, EU oder Australien), und wählen Sie **Weiter** aus.
   
   ![](media/service-connect-to-clickdimensions/params.png)
5. Wählen Sie als **Authentifizierungsmethode** **Standard** \> **Anmelden** aus. Geben Sie Ihre ClickDimensions-Anmeldeinformationen ein, wenn Sie dazu aufgefordert werden. Nachstehend finden Sie weitere Informationen zum [Suchen dieser Parameter](#FindingParams).
   
    ![](media/service-connect-to-clickdimensions/creds.png)
6. Nach der Genehmigung wird der Importvorgang automatisch gestartet. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
     ![](media/service-connect-to-clickdimensions/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Zum Verbinden mit dem Power BI-Inhaltspaket müssen Sie das entsprechende Rechenzentrum für Ihr Konto bereitstellen und sich mit Ihrem ClickDimensions-Konto anmelden. Wenn Sie nicht sicher sind, welches Rechenzentrum Sie bereitstellen müssen, überprüfen Sie dies zusammen mit Ihrem Administrator.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Der Kontoschlüssel befindet sich in den CRM-Einstellungen \> ClickDimensions-Einstellungen. Kopieren Sie den Kontoschlüssel aus den ClickDimensions-Einstellungen, und fügen Sie ihn in das Feld „Benutzername“ ein.  

![](media/service-connect-to-clickdimensions/crm.png)  

Kopieren Sie das Power BI-Token aus den ClickDimensions-Einstellungen, und fügen Sie es in das Feld „Kennwort“ ein. Das Power BI-Token befindet sich in den CRM-Einstellungen \> ClickDimensions-Einstellungen.  

![](media/service-connect-to-clickdimensions/crm2.png)  

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

