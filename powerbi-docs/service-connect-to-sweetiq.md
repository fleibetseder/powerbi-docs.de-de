---
title: Herstellen einer Verbindung mit SweetIQ mithilfe von Power BI
description: "SweetIQ für Power BI"
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
ms.openlocfilehash: df80e986a4ad42018c5ba036c2e47e684dba65d3
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-sweetiq-with-power-bi"></a>Herstellen einer Verbindung mit SweetIQ mithilfe von Power BI
Das Power BI-Inhaltspaket ruft Daten per Pull von Ihrem SweetIQ-Konto ab und generiert ohne weitere Konfiguration Inhalte, die Ihnen das problemlose Durchsuchen Ihrer Daten ermöglichen. Verwenden Sie das SweetIQ-Inhaltspaket, um Daten zu Ihren Standorten, Auflistungen, Bewertungen und Rezensionen zu analysieren. Die Daten werden täglich aktualisiert, um sicherzustellen, dass sie auf dem neuesten Stand sind.

Stellen Sie die Verbindung zum [SweetIQ-Inhaltspaket](https://app.powerbi.com/groups/me/getdata/services/sweetiq) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Klicken Sie im Navigationsbereich auf der linken Seite auf **Daten abrufen**.
   
    ![](media/service-connect-to-sweetiq/getdata.png)
2. Wählen Sie **SweetIQ** aus, und klicken Sie auf **Abrufen**.
   
    ![](media/service-connect-to-sweetiq/sweetiq.png)
3. Geben Sie Ihre SweetIQ-Client-ID an. Dies ist normalerweise ein alphanumerischer Wert. Einzelheiten zum Ermitteln dieses Werts finden Sie unten.
   
    ![](media/service-connect-to-sweetiq/parameter.png)
4. Wählen Sie die Authentifizierungsart **Schlüssel** aus, und geben  Sie Ihren Sweet IQ-API-Schlüssel ein. Dies ist normalerweise ein alphanumerischer Wert. Einzelheiten zum Ermitteln dieses Werts finden Sie unten.
   
    ![](media/service-connect-to-sweetiq/credentials.png)
5. Power BI beginnt mit dem Laden Ihrer Daten, was je nach der Menge der Daten in Ihrem Konto einige Zeit in Anspruch nehmen kann. Sobald das Laden abgeschlossen ist, werden im linken Navigationsbereich ein neues Dashboard, ein Bericht und ein Dataset angezeigt.
   
    ![](media/service-connect-to-sweetiq/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](service-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](service-dashboard-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Ihr Dataset ist auf eine tägliche Aktualisierung festgelegt. Sie können jedoch das Aktualisierungsintervall ändern oder es über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="finding-parameters"></a>Suchen von Parametern
Die Client-ID und der API-Schlüssel für dieses Inhaltspaket sind nicht mit Ihrem SweetIQ-Benutzernamen und dem zugehörigen Kennwort identisch .

Wählen Sie eine Client-ID für einen der Clients aus, auf die Ihr Konto Zugriff hat. Sie finden die Liste der Clients unter "Clientverwaltung" in Ihrem SweetIQ-Konto.

Wenden Sie sich an Ihren Administrator, um den API-Schlüssel zu erhalten, um auf die Daten für einen spezifischen Client zuzugreifen.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)
