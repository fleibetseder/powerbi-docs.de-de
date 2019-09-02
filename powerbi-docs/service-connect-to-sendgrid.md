---
title: Herstellen einer Verbindung mit SendGrid mithilfe von Power BI
description: SendGrid für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a05d78cfb0c1e34f0ec263f5455982cd4064905b
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185819"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Herstellen einer Verbindung mit SendGrid mithilfe von Power BI
Mit dem Power BI-Inhaltspaket für SendGrid erhalten Sie Einblicke in Ihr SendGrid-Konto, und Sie können Statistiken extrahieren. Mithilfe des SendGrid-Inhaltspakets können Sie die SendGrid-Statistik in einem Dashboard visualisieren.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie die Verbindung zum [SendGrid-Inhaltspaket](https://app.powerbi.com/getdata/services/sendgrid) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. Wählen Sie das **SendGrid**-Inhaltspaket aus, und klicken Sie auf **Abrufen**.
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. Geben Sie nach der entsprechenden Aufforderung Ihren SendGrid-Benutzernamen und das zugehörige Kennwort an. Wählen Sie **Anmelden**aus.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Nachdem Power BI die Daten importiert hat, werden im linken Navigationsbereich ein neues Dashboard, ein Bericht und ein Dataset mit Ihrer E-Mail-Statistik für die letzten 90 Tage angezeigt. Neue Elemente werden mit einem gelben Sternchen \* markiert.
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Folgende Metriken sind im SendGrid-Dashboard verfügbar:

* Allgemeine E-Mail-Statistik – Anforderungen, Zugestellt, Zurückgesendet, blockierter Spam, Spambericht usw.
* E-Mail-Statistik nach Kategorie
* E-Mail-Statistik nach Geografie
* E-Mail-Statistik nach Internetdienstanbieter
* E-Mail-Statistik nach Gerät, Client, Browser

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](power-bi-overview.md)

[Abrufen von Daten](service-get-data.md)

