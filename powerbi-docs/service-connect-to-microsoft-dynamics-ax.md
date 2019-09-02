---
title: Herstellen einer Verbindung mit einem Microsoft Dynamics AX-Inhaltspaket mithilfe von Power BI
description: Microsoft Dynamics AX-Inhaltspaket für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6a13c7fa6e1c33c3a839b4c835c991c143b77072
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185865"
---
# <a name="connect-to-microsoft-dynamics-ax-content-pack-with-power-bi"></a>Herstellen einer Verbindung mit einem Microsoft Dynamics AX-Inhaltspaket mithilfe von Power BI
Microsoft Dynamics AX bietet drei Power BI-Inhaltspakete, die jeweils auf bestimmte geschäftliche Benutzer zugeschnitten sind. Das Inhaltspaket für die Finanzleistung wurde eigens für CFOs entwickelt und erlaubt Einblicke in die Finanzlage Ihres Unternehmens. Das Inhaltspaket für die Handelskanalleistung ist auf Channel-Manager ausgerichtet und dient der Umsatzanalyse, um direkt aus den Handelsdaten Trends abzuleiten und Erkenntnisse zu gewinnen. Die Kostenverwaltung ist für COOs und CFOs bestimmt. Sie enthält Details zur Leistung von Vorgängen.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie eine Verbindung mit dem Microsoft Dynamics AX-Inhaltspaket für die [Handelskanalleistung](https://app.powerbi.com/getdata/services/dynamics-ax-retail-channel-performance), die [Finanzleistung](https://app.powerbi.com/getdata/services/dynamics-ax-financial-performance) oder die [Kostenverwaltung](https://app.powerbi.com/getdata/services/dynamics-ax-cost-management) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/services.png)
3. Wählen Sie eines der Dynamics AX-Inhaltspakete und dann **Abrufen** aus.
   
   ![](media/service-connect-to-microsoft-dynamics-ax/mdax.png)
4. Geben Sie die URL Ihrer Dynamics AX 7-Umgebung an. Unten finden Sie Einzelheiten zum [Suchen dieser Parameter](#FindingParams).
   
   ![](media/service-connect-to-microsoft-dynamics-ax/params.png)
5. Wählen Sie als **Authentifizierungsmethode** die Option **oAuth2** \> **Anmelden** aus. Wenn Sie dazu aufgefordert werden, geben Sie Ihre Dynamics AX-Anmeldeinformationen ein.
   
    ![](media/service-connect-to-microsoft-dynamics-ax/creds.png)
   
    ![](media/service-connect-to-microsoft-dynamics-ax/creds2.png)
6. Nach der Genehmigung wird der Importvorgang automatisch gestartet. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
     ![](media/service-connect-to-microsoft-dynamics-ax/dashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Das jeweilige Inhaltspaket nutzt den Dynamics AX 7-OData-Feed, um die nötigen Daten zur Leistungsanalyse für Handelskanäle, Finanzen oder zur Kostenverwaltung zu importieren.

## <a name="system-requirements"></a>Systemanforderungen
Für dieses Inhaltspaket ist eine Dynamics AX 7-Umgebungs-URL erforderlich, und der Benutzer muss Zugriff auf den OData-Feed haben.

## <a name="finding-parameters"></a>Suchen von Parametern
<a name="FindingParams"></a>

Die Dynamics AX 7-Umgebungs-URL finden Sie im Browser, wenn Sie sich als Benutzer anmelden. Kopieren Sie einfach die URL der Dynamics AX-Stammumgebung in das Power BI-Dialogfeld.

## <a name="troubleshooting"></a>Problembehandlung
Je nach Größe Ihrer Instanz kann es eine gewisse Zeit dauern, bis die Daten geladen sind. Wenn in Power BI leere Berichte angezeigt werden, überprüfen Sie bitte, ob Sie Zugriff auf die für diese Berichte benötigten OData-Tabellen haben.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

