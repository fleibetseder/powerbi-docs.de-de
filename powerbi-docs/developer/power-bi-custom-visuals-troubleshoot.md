---
title: Problembehandlung bei der Entwicklung von Power BI-Visuals
description: In diesem Artikel werden einige häufige Probleme erläutert, die beim Entwickeln oder Erstellen eines benutzerdefinierten Power BI-Visuals auftreten können.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: troubleshooting
ms.subservice: powerbi-custom-visuals
ms.date: 11/06/2018
ms.openlocfilehash: c2680a5818488a7822f38b8286a3e5a1782a487a
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74999765"
---
# <a name="troubleshoot-power-bi-visuals"></a>Problembehandlung bei Power BI-Visuals

## <a name="debug"></a>Debuggen

**Pbiviz-Befehl wurde nicht gefunden (oder ähnliche Fehler)**

Wenn Sie `pbiviz` über die Befehlszeile Ihres Terminals ausführen, sollte das Hilfefenster angezeigt werden. Wenn dies nicht der Fall ist, war die Installation fehlerhaft. Stellen Sie sicher, dass Sie mindestens Version 4.0 von NodeJS installiert haben.

**Das Debug-Visual wird nicht auf der Registerkarte „Visualisierungen“ angezeigt**

Die Debug-Visualisierung sieht wie ein Eingabeaufforderungssymbol auf der Registerkarte **Visualisierungen** aus.

![Auswahl des Visuals](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

Wenn sie nicht angezeigt wird, vergewissern Sie sich, dass Sie sie in den Power BI-Einstellungen aktiviert haben.

> [!NOTE]
> Die Debug-Visualisierung ist derzeit nur im Power BI-Dienst und nicht in Power BI Desktop oder in der mobilen App verfügbar. Die gepackte Visualisierung kann aber überall ausgeführt werden.

**Server für visuelle Elemente kann nicht erreicht werden**

Führen Sie den Server für Visuals mit dem Befehl `pbiviz start` über die Befehlszeile Ihres Terminals im Stammverzeichnis des Visualprojekts aus. Wenn der Server nicht ausgeführt wird, wurden vermutlich die SSL-Zertifikate nicht ordnungsgemäß installiert.

Zögern Sie nicht, sich mit Fragen, Kommentaren oder Problemen an das Power BI-Visuals-Supportteam zu wenden: *pbicvsupport@microsoft.com*  .

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in den [häufig gestellten Fragen zu Power BI-Visuals](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals).