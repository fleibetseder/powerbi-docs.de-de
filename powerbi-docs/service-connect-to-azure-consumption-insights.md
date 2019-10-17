---
title: Herstellen einer Verbindung mit Microsoft Azure Consumption Insights mithilfe von Power BI
description: Microsoft Azure Consumption Insights für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020439"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Herstellen einer Verbindung mit Microsoft Azure Consumption Insights mithilfe von Power BI
Untersuchen und überwachen Sie mit dem Power BI-Inhaltspaket Ihre Microsoft Azure-Nutzungsdaten im Power BI-Dienst. Die Daten werden einmal täglich automatisch aktualisiert.

Stellen Sie eine Verbindung mit dem [Inhaltspaket „Microsoft Azure Consumption Insights“](https://app.powerbi.com/getdata/services/azureconsumption) für den Power BI-Dienst her.

> [!NOTE]
> Wenn Sie die Einrichtung stärker anpassen möchten, verwenden Sie den [Azure Consumption Insights-Connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Klicken Sie im Power BI-Dienst unten im linken Navigationsbereich auf **Daten abrufen**.
   
    ![Daten abrufen](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![Dienste abrufen](media/service-connect-to-azure-consumption-insights/services.png)
3. Wählen Sie **Microsoft Azure Consumption Insights** \> **Jetzt anfordern** aus. 
   
   ![Jetzt anfordern](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Geben Sie die Anzahl der Monate, für die Sie Daten importieren möchten, und Ihre Azure Enterprise-Registrierungsnummer ein. Nachstehend finden Sie weitere Informationen zum [Suchen dieser Parameter](#FindingParams).
   
    ![Herstellen einer Verbindung mit Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Geben Sie zum Herstellen der Verbindung Ihren Zugriffsschlüssel ein. Sie finden Ihren Registrierungsschlüssel im Azure EA-Portal. 
   
    ![Microsoft Azure Consumption Insights: Schlüssel](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Der Importvorgang startet automatisch. Nach Abschluss des Vorgangs werden im Navigationsbereich ein neues Dashboard, ein Bericht und ein Modell angezeigt. Wählen Sie das Dashboard aus, um die importierten Daten anzuzeigen.
   
   ![Microsoft Azure Consumption Insights-Dashboard](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Das Inhaltspaket Microsoft Azure Consumption Insights enthält monatliche Berichtsdaten für den Bereich der Monate, den Sie beim Herstellen der Verbindung angegeben haben. Der Bereich ist ein bewegliches Zeitfenster, sodass die enthaltenen Datumsangaben bei Aktualisierung des Datasets aktualisiert werden.

## <a name="system-requirements"></a>Systemanforderungen
Das Inhaltspaket erfordert Zugriff auf die Enterprise-Features im Azure-Portal. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Suchen von Parametern
Die Power BI-Berichterstellung steht für direkte EA-, Partner und indirekte Kunden zur Verfügung, die Abrechnungsinformationen anzeigen können. Im folgenden Abschnitt finden Sie Informationen, wie Sie die zum Herstellen der Verbindung erforderlichen Werte ermitteln können.

**Anzahl Monate**

* Die Anzahl der Monate (1-36), für die Sie Daten importieren möchten.

**Registrierungsnummer**

* Ihre Azure Enterprise-Registrierungsnummer, die sich auf dem Startbildschirm des [Azure Enterprise-Portals](https://ea.azure.com/) unter **Registrierungsdetails** befindet.
  
    ![Registrierungsnummer](media/service-connect-to-azure-consumption-insights/params2.png)

**Zugriffsschlüssel**

* Ihren Schlüssel finden Sie im Azure Enterprise Portal unter **Nutzung herunterladen** > **API-Zugriffsschlüssel**.
  
    ![Zugriffsschlüssel](media/service-connect-to-azure-consumption-insights/creds2.png)

**Zusätzliche Hilfe**

* Um zusätzliche Hilfe zum Einrichten des Azure Enterprise Power BI-Pakets zu erhalten, melden Sie sich am Azure Enterprise-Portal an, um unter **Hilfe** die API-Hilfedatei anzuzeigen. Weitere Anweisungen finden Sie auch unter **Berichte** -> **Nutzung herunterladen** -> **API-Zugriffsschlüssel**.
* Wenn Sie die Einrichtung stärker anpassen möchten, verwenden Sie den [Azure Consumption Insights-Connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop.

## <a name="next-steps"></a>Nächste Schritte

[Azure Consumption Insights-Connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop

[Abrufen von Daten in Power BI](service-get-data.md)

