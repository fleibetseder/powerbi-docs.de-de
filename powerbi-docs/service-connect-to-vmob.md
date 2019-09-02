---
title: Herstellen einer Verbindung mit VMob mithilfe von Power BI
description: VMob für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e6c63d93c876377da7a5d36e814431dfda8665c3
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185784"
---
# <a name="connect-to-vmob-with-power-bi"></a>Herstellen einer Verbindung mit VMob mithilfe von Power BI
Das Nachverfolgen und Durchsuchen Ihrer VMob-Daten ist mit Power BI und dem VMob-Inhaltspaket problemlos möglich. Power BI ruft folgende Daten ab: Benutzerstatistik des Gesamtzeitraums sowie der letzten 30 Tage, Leistungskennzahlen Einzelhandel der letzten 30 Tage und Kampagnen-Leistung der letzten 30 Tage.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie die Verbindung zum [VMob-Inhaltspaket](https://app.powerbi.com/getdata/services/vmob) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
    ![](media/service-connect-to-vmob/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-vmob/services.png)
3. Wählen Sie **VMob** \> **Abrufen** aus.
   
   ![](media/service-connect-to-vmob/vmob.png)
4. Geben Sie nach Aufforderung Ihre VMob-URL ein, und klicken Sie auf die Schaltfläche „Weiter“. Diese URL wird separat von VMob bereitgestellt.
   
    ![](media/service-connect-to-vmob/params.png)
5. Wählen Sie in der Dropdownliste für die Authentifizierungsmethode **Basic** aus, geben Sie den VMob-Benutzernamen und das Kennwort ein, und klicken Sie auf die Schaltfläche **Anmelden** .
   
    ![](media/service-connect-to-vmob/creds.png)
6. Der Importvorgang beginnt automatisch, und Power BI ruft die VMob-Daten ab, um ein vorgefertigtes Dashboard und einen Bericht zu erstellen.
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

