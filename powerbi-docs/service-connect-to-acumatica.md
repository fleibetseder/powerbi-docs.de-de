---
title: Herstellen einer Verbindung mit Acumatica mithilfe von Power BI
description: "Acumatica für Power BI"
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: dd64f4fb4651e393e770dda9323c10356424c780
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-acumatica-with-power-bi"></a>Herstellen einer Verbindung mit Acumatica mithilfe von Power BI
Mit dem Power BI-Acumatica-Inhaltspaket können Sie schnell Erkenntnisse aus Ihren Verkaufschancendaten gewinnen. Power BI ruft Ihre Daten ab, einschließlich Verkaufschancen, Konten und Kunden, und erstellt dann auf der Grundlage dieser Daten ein Standarddashboard und zugehörige Berichte.

Stellen Sie eine Verbindung mit dem [Acumatica- Inhaltspaket](https://app.powerbi.com/getdata/services/acumatica) her, oder erfahren Sie mehr über die [Integration von Acumatica](https://powerbi.microsoft.com/integrations/acumatica) in Power BI.

>[!NOTE]
>Die Mindestversion von Acumatica für dieses Inhaltspaket ist 5.2.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-acumatica/getdata3.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-acumatica/getdata2.png)
3. Wählen Sie **Acumatica** \> **Abrufen** aus.
   
   ![](media/service-connect-to-acumatica/acumatica.png)
4. Geben Sie Ihren Acumatica-OData-Endpunkt ein. Mithilfe eines OData-Endpunkts kann ein externes System Daten bei Acumatica abrufen. Ein Acumatica-OData-Endpunkt weist das folgende Format auf und sollte HTTPS verwenden:
   
     https://[Websitedomäne]/odata/[Firmenname]
   
   Der Firmenname ist nur erforderlich, wenn Sie eine Bereitstellung mit mehreren Unternehmen haben. Weitere Informationen zum Auffinden dieses Parameters in Ihrem Acumatica-Konto finden Sie unten.
   
   ![](media/service-connect-to-acumatica/parameters.png)
5. Wählen Sie als Authentifizierungsmethode **Standard**aus. Geben Sie den Benutzernamen und das Kennwort Ihres Acumatica-Kontos ein, und klicken Sie dann auf **Anmelden**.
   
    ![](media/service-connect-to-acumatica/creds2.png)
6. Nachdem die Daten von Power BI importiert wurden, werden im linken Navigationsbereich ein neues Dashboard, ein Bericht und ein Dataset angezeigt. Neue Elemente sind mit einem gelben Sternchen (\*) gekennzeichnet, das nach dem Auswählen ausgeblendet wird. Nach Auswahl des Dashboards wird ein Layout ähnlich wie das folgende gezeigt:
   
    ![](media/service-connect-to-acumatica/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](service-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](service-dashboard-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Ihr Dataset ist auf eine tägliche Aktualisierung festgelegt. Sie können jedoch das Aktualisierungsintervall ändern oder es über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Dieses Inhaltspaket erfordert mindestens die Acumatica-Version 5.2. Prüfen Sie die Version mit Ihrem Acumatica-Administrator.

## <a name="finding-parameters"></a>Suchen von Parametern
**Acumatica OData-Endpunkt**

Der Acumatica-OData-Endpunkt weist das folgende Format auf und sollte HTTPS verwenden:

    https://[sitedomain]/odata/[companyname]

Wenn Sie bei Acumatica angemeldet sind, wird die Domäne der Anwendungswebsite in der Adressleiste des Browsers angezeigt. Im Beispiel unten ist die Domäne der Website „https://pbi.acumatica.com“, wenn dafür ein Endpunkt bereitgestellt werden soll, hat er daher das Format „https://pbi.acumatica.com/odata“.

 ![](media/service-connect-to-acumatica/url.png)

Der Firmenname ist nur erforderlich, wenn Sie eine Bereitstellung mit mehreren Unternehmen haben. Diese Informationen finden Sie auf der Acumatica-Anmeldeseite.

![](media/service-connect-to-acumatica/signin2.png)

## <a name="troubleshooting"></a>Problembehandlung
Wenn Sie sich nicht anmelden können, überprüfen Sie, ob der angegebene Automatica-OData-Endpunkt das richtige Format aufweist.

    https://<application site domain>/odata/<company name>

Wenn beim Herstellen der Verbindung Probleme auftreten, überprüfen Sie gemeinsam mit Ihrem Administrator Ihre Acumatica-Version. Für dieses Inhaltspaket ist die Version 5.2 oder höher erforderlich.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)
