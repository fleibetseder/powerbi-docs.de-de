---
title: Dynamische Bindung
description: Erfahren Sie, wie ein Bericht mithilfe von dynamischer Bindung eingebettet wird.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8110023de4df28f65129bd53203cec9752acc1af
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864445"
---
# <a name="dynamic-binding"></a>Dynamische Bindung

Die dynamische Bindung ermöglicht die dynamische Auswahl eines Datasets während des Einbettens eines Berichts. Bericht und Dataset müssen sich dabei nicht im gleichen Arbeitsbereich befinden. Endbenutzer sehen verschiedene Ergebnisse, abhängig vom ausgewählten Dataset.

Beide Arbeitsbereiche (jener, der den Bericht enthält, und jener, der das Dataset enthält) müssen einer Kapazität zugewiesen sein.

Das Einbetten eines Berichts mithilfe von dynamischer Bindung besteht aus zwei Phasen:
1. Generieren eines Tokens
2. Anpassen des Konfigurationsobjekts

## <a name="generating-a-token"></a>Generieren eines Tokens
Verwenden Sie zum Generieren eines Tokens die [API zum Generieren eines Einbettungstokens für mehrere Elemente](embed-sample-for-customers.md#multiEmbedToken).

Dynamische Bindung wird für beide Einbettungsszenarien unterstützt *Einbetten für Ihre Organisation* und *Einbetten für Ihre Kunden*.

| Solution                   | Token                               | Anforderungen                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Einbetten für Ihre Organisation* | Zugriffstoken für Power BI-Benutzer     | Der Benutzer, dessen Azure AD-Token verwendet wird, muss über passende Berechtigungen für alle Artefakte verfügen.                                                                    |
| *Einbetten für Ihre Kunden*    | Zugriffstoken für Benutzer, die kein Power BI verwenden | Es muss Berechtigungen sowohl für den Bericht als auch für das dynamisch gebundene Dataset umfassen. Verwenden Sie die neue API, um ein Einbettungstoken zu generieren, das mehrere Artefakte unterstützt. |

## <a name="adjusting-the-config-object"></a>Anpassen des Konfigurationsobjekts
Fügen Sie dem Konfigurationsobjekt `datasetBinding` hinzu. Verwenden Sie das Beispiel unten auf der Seite als Referenz.

Wenn Sie gerade erst in das Einbetten in Power BI einsteigen, arbeiten Sie diese Tutorials durch, um zu erfahren, wie Sie Power BI-Inhalte einbetten können:
* [Einbetten von Power BI-Inhalten in eine Anwendung für Ihre Kunden](embed-sample-for-customers.md)
* [Tutorial: Einbetten von Power BI-Inhalten in eine Anwendung für Ihre Organisation](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Beispiel
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```