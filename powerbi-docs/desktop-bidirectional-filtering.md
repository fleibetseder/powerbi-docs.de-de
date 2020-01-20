---
title: Bidirektionale Kreuzfilterung in Power BI Desktop
description: Aktivieren der Kreuzfilterung mithilfe von DirectQuery in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8aeae0075ed32a832c27f475ef3786b7df76576c
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761770"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Aktivieren der bidirektionalen Kreuzfilterung für DirectQuery in Power BI Desktop

Beim Filtern von Tabellen zum Erstellen der entsprechenden Anzeige von Daten stehen Berichtersteller (und Datenmodellierer) vor Herausforderungen, wenn sie festlegen, wie bei einem Bericht das Filtern angewendet wird. Der Filterkontext einer Tabelle besteht nur auf der einen Seite der Beziehung, jedoch nicht auf der anderen Seite. Dies erfordert oftmals komplexe DAX-Formeln, um die gewünschten Ergebnisse zu erzielen.

Mit der bidirektionalen Kreuzfilterung haben Berichtersteller (und Datenmodellierer) nun eine bessere Kontrolle darüber, wie bei der Arbeit mit verknüpften Tabellen Filter angewendet werden, indem es Filtern ermöglicht wird, auf *beide* Seiten einer Tabellenbeziehung angewendet zu werden. Dies wird erreicht, indem der Filterkontext auf eine zweite verknüpfte Tabelle auf der anderen Seite einer Tabellenbeziehung verteilt wird.

## <a name="detailed-whitepaper-for-bidirectional-cross-filtering"></a>Detailliertes Whitepaper für die bidirektionale Kreuzfilterung
Es ist ein [detailliertes Whitepaper](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) verfügbar, das die bidirektionale Kreuzfilterung in Power BI Desktop erklärt (das Whitepaper deckt auch SQL Server Analysis Services 2016 ab, da beide sich gleich verhalten).

* Herunterladen des Whitepapers [Bidirectional cross-filtering for Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx) (Bidirektionale Kreuzfilterung für Power BI Desktop)

## <a name="enabling-bidirectional-cross-filtering-for-directquery"></a>Aktivieren der bidirektionalen Kreuzfilterung für DirectQuery

Folgendes muss ausgewählt sein, um die Kreuzfilterung im Dialogfeld **Beziehung bearbeiten** für eine Beziehung zu aktivieren:

* **Kreuzfilterrichtung** muss auf **Beide** festgelegt sein
* Die Option **Sicherheitsfilter in beide Richtungen anwenden** muss ebenfalls ausgewählt sein

  ![](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Verwenden Sie beim Erstellen von DAX-Formeln für die Kreuzfilterung in Power BI Desktop *UserPrincipalName* (oft mit der Anmeldung eines Benutzers, z.B. <em>joe@contoso.com</em>, identisch) anstelle von *UserName*. Daher müssen Sie möglicherweise eine verknüpfte Tabelle erstellen, die den *UserName* einem *UserPrincipalName* (oder z.B. EmployeeID) zuordnet.

Weitere Informationen und Beispiele zur Funktionsweise der bidirektionalen Kreuzfilterung finden Sie in dem weiter oben in diesem Artikel genannten [Whitepaper](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

