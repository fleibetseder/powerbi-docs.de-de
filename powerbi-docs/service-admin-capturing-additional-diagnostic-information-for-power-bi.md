---
title: Erfassen von zusätzlichen Diagnoseinformationen
description: Diese Anweisungen bieten zwei mögliche Optionen für die manuelle Erfassung von zusätzlichen Diagnoseinformationen aus dem Webclient von Power BI.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 370ac3fad6f31c214ecafad7762acd8219831218
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873703"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Erfassen von zusätzlichen Diagnoseinformationen für Power BI

Dieser Artikel enthält Anweisungen für die manuelle Erfassung von zusätzlichen Diagnoseinformationen aus dem Webclient von Power BI.

1. Navigieren Sie mit Microsoft Edge oder Internet Explorer zu [Power BI](https://app.powerbi.com).

1. Drücken Sie **F12**, um die Microsoft Edge-Entwicklertools zu öffnen.

   ![Screenshot der Registerkarte „Elemente“ der Microsoft Edge-Entwicklertools.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Wählen Sie die Registerkarte **Network** (Netzwerk) aus. Es wird der Datenverkehr aufgelistet, der bereits erfasst wurde.

   ![Screenshot der Registerkarte „Netzwerk“ der Microsoft Edge-Entwicklertools.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Sie können:

    * Im Fenster browsen und jedes eventuell auftretende Problem reproduzieren.

    * Das Entwicklertoolsfenster während der Sitzung jederzeit durch Drücken von F12 aus- und einblenden.

1. Zum Beenden der Profilerstellungssitzung das rote Quadrat auf der Registerkarte **Netzwerk** im Entwicklertoolbereich auswählen.

   ![Screenshot der Registerkarte „Netzwerk“ der Microsoft Edge-Entwicklertools mit einer Legende zur Schaltfläche „Stop“.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Wählen Sie das Diskettensymbol aus, um die Daten als HTTP-Archivdatei (HAR) zu exportieren.

   ![Screenshot der Registerkarte „Netzwerk“ der Microsoft Edge-Entwicklertools mit einer Legende zum Diskettensymbol.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Geben Sie einen Dateinamen ein, und speichern Sie die HAR-Datei.

    Die HAR-Datei enthält alle Informationen über Netzwerkanforderungen zwischen dem Browserfenster und Power BI, darunter:

    * Die Aktivitäts-IDs für jede Anforderung.

    * Den genauen Zeitstempel für jede Anforderung.

    * Alle an den Client zurückgegebenen Fehlerinformationen.

    Diese Ablaufverfolgung enthält außerdem die Daten, die zum Füllen der auf dem Bildschirm angezeigten visuellen Objekte verwendet werden.

1. Sie können die HAR-Datei angeben, um die Überprüfung zu unterstützen.

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
