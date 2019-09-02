---
title: Herstellen einer Verbindung mit Prevedere mithilfe von Power BI
description: Prevedere für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8abf93b30b976aea1d0164238d173abe1be260e8
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185367"
---
# <a name="connect-to-prevedere-with-power-bi"></a>Herstellen einer Verbindung mit Prevedere mithilfe von Power BI
Erhalten Sie Zugriff auf exklusive und kritische Finanzdaten, um Ihr Geschäft zuverlässig und proaktiv voranzutreiben.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [Prevedere-Inhaltspaket](https://app.powerbi.com/getdata/services/prevedere) für Power BI her.

>[!NOTE]
>Wenn Sie kein vorhandener Prevedere-Benutzer sind, verwenden Sie zum Ausprobieren den [Beispielschlüssel](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html).

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-prevedere/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-prevedere/services.png)
3. Wählen Sie **Prevedere** und anschließend **Abrufen** aus.
   
   ![](media/service-connect-to-prevedere/connect.png)
4. Wählen Sie als **Authentifizierungsmethode** die Option **Schlüssel** aus, und geben Sie Ihren Prevedere-API-Schlüssel ein.
   
    ![](media/service-connect-to-prevedere/creds.png)
5. Wählen Sie **Anmelden** aus, um den Importvorgang zu starten. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
     ![](media/service-connect-to-prevedere/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Das Inhaltspaket erhält Einblick in Ihre Einzelhandelsprognosen, Vorhersagemodelle, Leitindikatoren und mehr.

## <a name="system-requirements"></a>Systemanforderungen
Dieses Inhaltspaket benötigt den Zugriff auf einen Prevedere-API-Schlüssel oder den Beispielschlüssel (siehe unten).

## <a name="finding-parameters"></a>Suchen von Parametern
<a name="FindingParams"></a>

Bestehende Kunden können mithilfe ihrer API-Schlüssel auf ihre Daten zugreifen. Wenn Sie noch kein Kunde sind, sehen Sie ein Beispiel der Daten und Analysen, indem Sie den [Beispielschlüssel](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html) verwenden.

## <a name="troubleshooting"></a>Problembehandlung
Je nach Größe Ihrer Instanz kann es eine gewisse Zeit dauern, bis die Daten geladen sind.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

