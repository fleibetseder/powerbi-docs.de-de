---
title: Herstellen einer Verbindung mit Twilio mithilfe von Power BI
description: Twilio für Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 61099a24f4ba0630ddf982eadf867e24bdb097a2
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185801"
---
# <a name="connect-to-twilio-with-power-bi"></a>Herstellen einer Verbindung mit Twilio mithilfe von Power BI
Mit dem Microsoft Twilio-Inhaltspaket für Power BI können Sie Ihre Daten in Power BI abrufen und ein fertig konfiguriertes [Twilio-Dashboard](https://powerbi.microsoft.com/integrations/twilio) und einen Bericht erstellen, die Erkenntnisse zu Ihren Daten bieten. Sie können Ihre benutzerdefinierten Berichte und das Dashboard auch für das von Power BI erstellte Dataset erstellen. Die Daten werden einmal täglich aktualisiert werden, damit immer die aktuellen Daten angezeigt werden.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Stellen Sie die Verbindung zum [Twilio-Inhaltspaket](https://app.powerbi.com/getdata/services/twilio) für Power BI her.

## <a name="how-to-connect"></a>Herstellen der Verbindung
1. Wählen Sie unten im linken Navigationsbereich **Daten abrufen** aus.
   
   ![](media/service-connect-to-twilio/pbi_getdata.png) 
2. Wählen Sie im Feld **Dienste** die Option **Abrufen**aus.
   
   ![](media/service-connect-to-twilio/pbi_getservices.png) 
3. Wählen Sie **Twilio** \> **Abrufen** aus.
   
   ![](media/service-connect-to-twilio/twilio.png)
4. Wählen Sie als **Authentifizierungsmethode** die Option **oAuth2** \> Anmelden aus. Geben Sie bei der entsprechenden Aufforderung Ihre Twilio-Anmeldeinformationen an, und autorisieren Sie die Power BI-Anwendung für den Zugriff auf Ihre Daten.
   
   ![](media/service-connect-to-twilio/pbi_twilio_login.png)
5. Dadurch wird das Importieren der Daten aus Ihrem Twilio-Konto gestartet, und Ihr Dashboard wird mit den in den letzten 30 Tagen verwendeten Anrufen und Nachrichten gefüllt. 
   
   ![](media/service-connect-to-twilio/pbi_twilio_db.png)

**Was nun?**

* Versuchen Sie, am oberen Rand des Dashboards [im Q&A-Feld eine Frage zu stellen](consumer/end-user-q-and-a.md).
* [Ändern Sie die Kacheln](service-dashboard-edit-tile.md) im Dashboard.
* [Wählen Sie eine Kachel aus](consumer/end-user-tiles.md), um den zugrunde liegenden Bericht zu öffnen.
* Zwar ist Ihr Dataset auf tägliche Aktualisierung festgelegt, jedoch können Sie das Aktualisierungsintervall ändern oder über **Jetzt aktualisieren** nach Bedarf aktualisieren.

## <a name="whats-included"></a>Inhalt
Die Details für alle Anruf- und Nachrichtentransaktionen für die letzten 30 Tage. Sie können für diese Daten alle Arten von Analysen und Aggregationen durchführen.

Eine Reihe von bereits aggregierten Statistiken, die Sie möglicherweise im Auge behalten möchten. Dieser Satz umfasst Folgendes:

        All Time Calls Count  
        All Time Calls Duration  
        All Time Calls Price  
        All Time Messages Price  
        All Time Messages Count  
        All Time Count of Phone Numbers  
        All Time Price of Phone Numbers  
        All Time Twilio Client Calls Price  
        All Time Twilio Client Calls Duration  
        All Time Twilio Client Calls Count  
        All Time Total Price  
        All Time Inbound Calls Price  
        All Time Inbound Calls Duration  
        All Time Inbound Calls Count  
        All Time Outbound Calls Price  
        All Time Outbound Calls Duration  
        All Time Outbound Calls Count  
        This Month Calls Price  
        This Month Calls Duration  
        This Month Calls Count  
        This Month Messages Count  
        This Month Messages Price  
        This Month Count of Phone Numbers  
        This Month Price of Phone Numbers  
        This Month Twilio Client Calls Price  
        This Month Twilio Client Calls Duration  
        This Month Twilio Client Calls Count  
        This Month Total Price  
        This Month Inbound Calls Price  
        This Month Inbound Calls Duration  
        This Month Inbound Calls Count  
        This Month Outbound Calls Price  
        This Month Outbound Calls Duration  
        This Month Outbound Calls Count  
        This Month Inbound Messages Price  
        This Month Inbound Messages Count  
        This Month Outbound Messages Price  
        This Month Outbound Messages Count

## <a name="troubleshooting"></a>Problembehandlung
Wenn für die letzten 30 Tage eine große Datenmenge vorliegt (Hunderttausende Transaktionen), kann beim Datenabruf ein Fehler auftreten. Das Problem ist bekannt und wir arbeiten an der Behebung. Wenn das Problem in der Zwischenzeit auftritt, verwenden Sie den Supportlink am oberen Rand der Power BI-Seite, um uns entsprechend zu informieren. Wir werden uns dann zwecks weiterer Untersuchungen an Sie wenden.

## <a name="next-steps"></a>Nächste Schritte
[Erste Schritte mit Power BI](service-get-started.md)

[Abrufen von Daten in Power BI](service-get-data.md)

