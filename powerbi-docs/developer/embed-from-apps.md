---
title: Einbetten von Berichten oder Dashboards aus Apps
description: Erfahren Sie, wie Sie einen Bericht oder ein Dashboard aus einer Power BI-App anstatt aus einem Arbeitsbereich integrieren bzw. einbetten.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
ms.date: 11/27/2018
ms.openlocfilehash: 6d0094eb252584d9c3529db19ec5a733731118ec
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74264947"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Einbetten von Berichten oder Dashboards aus Apps

In Power BI können Sie Apps erstellen, um zusammengehörige Dashboards und Berichte an einem Ort zusammenfassen. Anschließend können Sie die Apps für große Personengruppen in Ihrer Organisation veröffentlichen. Die Verwendung der Apps ist dann wichtig, wenn Ihre Benutzer Power BI-Benutzer sind. Sie können dann mithilfe von Power BI-Apps Inhalte für sie freigeben. In diesem Artikel lernen Sie einige Schritte zum schnellen Einbetten von Inhalten aus einer veröffentlichten Power BI-App in eine Drittanbieteranwendung kennen.

## <a name="grab-a-report-embedurl-for-embedding"></a>Abrufen einer Berichts-embedURL für die Einbettung

1. Instanziieren Sie die Anwendung in einem Benutzerarbeitsbereich, d.h. **Mein Arbeitsbereich**. Geben Sie ihn für sich selbst frei, oder leiten Sie einen anderen Benutzer an, diesen Flow zu durchlaufen.

2. Öffnen Sie den gewünschten Bericht im Power BI-Dienst.

3. Wechseln Sie zu **Datei** > **In SharePoint Online einbetten**, und rufen Sie die embedURL für den Bericht ab. Im nachstehenden Screenshot wird ein embedURL-Beispiel gezeigt. Alternativ können Sie die GetReports/GetReport-REST-API aufrufen und das entsprechende embedURL-Berichtfeld aus der Antwort extrahieren. Die REST-Aufruf sollte keine Arbeitsbereichs-ID als Teil der URL enthalten, da die App im Arbeitsbereich des Benutzers instanziiert wurde.

    ![Einbetten aus Apps](media/embed-from-apps/embed-from-app.png)

4. Verwenden Sie die in Schritt 3 abgerufene embedURL mit dem JavaScript SDK.

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Abrufen einer Dashboard-embedURL für die Einbettung

1. Instanziieren Sie die Anwendung in einem Benutzerarbeitsbereich, d.h. **Mein Arbeitsbereich**. Geben Sie ihn für sich selbst frei, oder leiten Sie einen anderen Benutzer an, diesen Flow zu durchlaufen.

2. Alternativ rufen Sie die GetDashboards REST-API auf, und extrahieren Sie das entsprechende Dashboard-embedURL-Feld aus der Antwort. Die REST-Aufruf sollte keine Arbeitsbereichs-ID als Teil der URL enthalten, da die App im Arbeitsbereich des Benutzers instanziiert wurde.

3. Verwenden Sie die in Schritt 2 abgerufene embedURL mit dem JavaScript SDK.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie aus Arbeitsbereichen für Drittanbieterkunden und Ihre Organisation einbetten:

> [!div class="nextstepaction"]
>[Embed for third-party customers (Einbetten für Drittanbieterkunden)](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Embed for your organization (Einbetten für Ihre Organisation)](embed-sample-for-your-organization.md)
