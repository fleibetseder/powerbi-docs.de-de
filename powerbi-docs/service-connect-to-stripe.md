---
title: Herstellen einer Verbindung mit Stripe mithilfe von Power BI
description: Stripe für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ddcbee2c6d60541db0d71ea5ccfbfd5e6cf037ac
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184581"
---
# <a name="connect-to-stripe-with-power-bi"></a>Herstellen einer Verbindung mit Stripe mithilfe von Power BI
Visualisieren und durchsuchen Sie Ihre Stripe-Daten in Power BI mithilfe des Power BI-Inhaltspakets. Das Power BI Stripe-Inhaltspaket ruft Daten zu Kunden, Gebühren, Ereignissen und Rechnungen ab. Die Daten umfassen die neuesten 10.000 Ereignisse und 5.000 Gebühren innerhalb der letzten 30 Tage. Der Inhalt wird automatisch einmal täglich nach einem von Ihnen gesteuerten Zeitplan aktualisiert. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [Stripe-Inhaltspaket](https://app.powerbi.com/getdata/services/stripe) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich „Daten abrufen“ aus.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Wählen Sie **Stripe** &gt; **Abrufen** aus.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Geben Sie Ihren [API-Schlüssel](https://dashboard.stripe.com/account/apikeys) für Stripe ein, um die Verbindung herzustellen.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. Der Importvorgang startet automatisch. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell (mit einem Sternzeichen gekennzeichnet) angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](power-bi-overview.md)

[Abrufen von Daten in Power BI](service-get-data.md)

