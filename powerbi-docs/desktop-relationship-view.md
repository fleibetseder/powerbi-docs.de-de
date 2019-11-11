---
title: Beziehungsansicht in Power BI Desktop
description: Beziehungsansicht in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a39f675077d72698b62138aa1b9d56c5bf6a6958
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877839"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Beziehungsansicht in Power BI Desktop
Die **Beziehungsansicht** zeigt alle Tabellen, Spalten und Beziehungen in Ihrem Modell. Dies kann besonders hilfreich sein, wenn Ihr Modell über komplexe Beziehungen zwischen vielen Tabellen verfügt.

Schauen wir uns das mal an.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Symbol „Beziehungsansicht“: Klicken Sie darauf, um das Modell in der Beziehungsansicht zu zeigen.

**B.** Beziehung: Sie können den Mauszeiger über eine Beziehung führen, um die verwendeten Spalten anzuzeigen. Doppelklicken Sie auf eine Beziehung, um sie im Dialogfeld **Beziehung bearbeiten** zu öffnen. 

In der obigen Abbildung sehen Sie, dass die Tabelle *Stores* über die Spalte *StoreKey* verfügt, die mit der Tabelle *Sales* verknüpft ist, die ebenfalls eine Spalte *StoreKey* besitzt. Wir sehen, dass dies eine *N zu Eins*-Beziehung (\*: 1) ist und dass das Symbol in der Mitte der Zeile den Kreuzfilter so anzeigt, dass die Richtung auf *Beide* festgelegt ist. Der Pfeil auf dem Symbol zeigt die Richtung des Filterkontextflows.

Weitere Informationen über Beziehungen finden Sie unter [Erstellen und Verwalten von Beziehungen in Power BI Desktop](desktop-create-and-manage-relationships.md).

