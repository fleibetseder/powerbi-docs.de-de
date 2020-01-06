---
title: Anpassen von QuickInfos in Power BI Desktop
description: Erstellen Sie benutzerdefinierte QuickInfos für Visualisierungen mithilfe von Drag & Drop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: efbae4250b7b3cab18892cf519bfac5da3a88e1b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73868671"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Anpassen von QuickInfos in Power BI Desktop
QuickInfos sind eine elegante Methode zum Bereitstellen von kontextbezogenen Informationen und Details zu Datenpunkten in einer Visualisierung. Die folgende Abbildung zeigt eine QuickInfo zu einem Diagramm in Power BI Desktop.

![Standard-QuickInfo](media/desktop-custom-tooltips/custom-tooltips-1.png)

Wenn eine Visualisierung erstellt wird, werden in der Standard-QuickInfo der Wert und die Kategorie Datenpunkts angezeigt. Es gibt viele Fälle, in denen es hilfreich ist, die QuickInfo-Informationen anzupassen und mehr Kontext und Informationen für die Benutzer bereitzustellen, die die Visualisierung anzeigen. Mit QuickInfos können Sie zusätzliche Datenpunkte angeben, die als Teil der QuickInfo angezeigt werden.

## <a name="how-to-customize-tooltips"></a>Anpassen von QuickInfos
Zum Erstellen einer benutzerdefinierten QuickInfo ziehen Sie im Bereich **Felder** unter **Visualisierungen** ein Feld in den Bucket **QuickInfos**, wie in der folgenden Abbildung dargestellt. In der folgenden Abbildung wurden zwei Felder im Bucket **QuickInfos** eingefügt.

![Hinzufügen von QuickInfo-Feldern](media/desktop-custom-tooltips/custom-tooltips-2.png)

Wenn QuickInfos zum Feldbereich hinzugefügt wurden und der Benutzer den Mauszeiger auf einen Datenpunkt in der Visualisierung hält, werden die Werte für diese Felder in der QuickInfo angezeigt.

![Benutzerdefinierte QuickInfo](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>Anpassen von QuickInfos mit Aggregation oder Schnellberechnungen
Sie können eine QuickInfo weiter anpassen, indem Sie eine Aggregationsfunktion oder eine *Schnellberechnung* auswählen. Klicken Sie hierfür auf den Pfeil neben dem Feld im Bucket **QuickInfos**, und wählen Sie eine der verfügbaren Optionen aus.

![QuickInfo mit Schnellberechnung](media/desktop-custom-tooltips/custom-tooltips-4.png)

Es gibt viele Methoden zum Anpassen von **QuickInfos** mit beliebigen Feldern im Dataset, um schnell Informationen und Einblicke für die Benutzer zu übermitteln, die Ihre Dashboards oder Berichte anzeigen.

