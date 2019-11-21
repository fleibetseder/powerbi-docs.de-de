---
title: Herstellen einer Verbindung mit Azure-Überwachungsprotokollen mithilfe von Power BI
description: Azure-Überwachungsprotokolle für Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: d0bd4e90dac6e71d95c38bed83f1c9507acc4fd3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855392"
---
# <a name="connect-to-azure-audit-logs-with-power-bi"></a>Herstellen einer Verbindung mit Azure-Überwachungsprotokollen mithilfe von Power BI
Mit dem Azure-Überwachungsprotokoll-Inhaltspaket können Sie die in den Überwachungsprotokollen gespeicherten Informationen analysieren und visualisieren. Power BI ruft Ihre Daten ab und erstellt ein Standard-Dashboard sowie Berichte basierend auf diesen Daten.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem [Azure-Überwachungsprotokoll-Inhaltspaket](https://app.powerbi.com/getdata/services/azure-audit-logs) her, oder informieren Sie sich über die [Integration von Azure-Überwachungsprotokollen](https://powerbi.microsoft.com/integrations/azure-audit-logs) in Power BI.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im Navigationsbereich **Daten abrufen** aus.  
   
    ![](media/service-connect-to-azure-audit-logs/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.  
   
    ![](media/service-connect-to-azure-audit-logs/services.png) 
3. Wählen Sie **Azure-Überwachungsprotokolle**  >  **Abrufen** aus.  
   
   ![](media/service-connect-to-azure-audit-logs/azureauditlogs.png)
4. Wenn Sie dazu aufgefordert werden, geben Sie Ihre **Azure-Abonnement-ID**ein. Informationen zum Suchen Ihrer [Abonnement-ID](#FindingParams) finden Sie weiter unten.   
   
    ![](media/service-connect-to-azure-audit-logs/parameters.png)
5. Wählen Sie als **Authentifizierungsmethode** die Option **oAuth2** \> **Anmelden** aus.
   
    ![](media/service-connect-to-azure-audit-logs/creds.png)
6. Geben Sie die Anmeldeinformationen für Ihr Konto ein, um den Anmeldevorgang abzuschließen.
   
    ![](media/service-connect-to-azure-audit-logs/login.png)
7. Power BI ruft Ihre Azure-Überwachungsprotokolldaten ab und erstellt für Sie ein gebrauchsfertiges Dashboard und einen Bericht. 
   
    ![](media/service-connect-to-azure-audit-logs/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="system-requirements"></a>Systemanforderungen
Das Azure-Überwachungsprotokoll-Inhaltspaket erfordert Zugriff auf Überwachungsprotokolle im Azure-Portal. Weitere Informationen finden Sie [hier](/azure/azure-resource-manager/resource-group-audit/).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Es gibt zwei einfache Möglichkeiten, Ihre Abonnement-ID zu suchen.

1. Über https://portal.azure.com -&gt; Durchsuchen &gt; Abonnements &gt; Abonnement-ID
2. Über https://manage.windowsazure.com -&gt; Einstellungen &gt; Abonnement-ID

Ihre Abonnement-ID besteht aus einer langen Abfolge von Zahlen und Zeichen, ähnlich wie im obigen Beispiel in Schritt \#4. 

## <a name="troubleshooting"></a>Problembehandlung
Wenn ein Fehler aufgrund der Anmeldeinformationen oder beim Aktualisieren aufgrund ungültiger Anmeldeinformationen angezeigt wird, löschen Sie alle Instanzen des Azure-Überwachungsprotokoll-Inhaltspakets, und stellen Sie die Verbindung erneut her.

## <a name="next-steps"></a>Nächste Schritte
[Was ist Power BI?](fundamentals/power-bi-overview.md)  
[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)  

