---
title: Erweiterter Bearbeitungsmodus in Power BI-Visuals
description: In diesem Artikel wird erläutert, wie Sie in Power BI-Visuals erweiterte UI-Steuerelemente festlegen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 19714db2d1307ac9d7eb8861955870ba9988539e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880326"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Erweiterter Bearbeitungsmodus in Power BI-Visuals

Wenn Sie in Ihrem Power BI-Visual erweiterte UI-Steuerelemente benötigen, können Sie den Modus „Erweiterte Bearbeitung“ nutzen. Wenn Sie sich im Bearbeitungsmodus des Berichts befinden, können Sie auf die Schaltfläche **Bearbeiten** klicken, um den Bearbeitungsmodus auf **Erweitert** festzulegen. Das Visual kann anhand des `EditMode`-Flags bestimmen, ob diese UI-Steuerelemente anzeigt werden sollen.

Der Modus „Erweiterte Bearbeitung“ wird vom Visual standardmäßig nicht unterstützt. Falls ein anderes Verhalten gewünscht ist, können Sie dies explizit in der *capabilities.json*-Datei des Visuals angeben, indem Sie die `advancedEditModeSupport`-Eigenschaft festlegen.

Mögliche Werte:

- `0`: NotSupported

- `1`: SupportedNoAction

- `2`: SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Wechseln zum Modus „Erweiterte Bearbeitung“

In den folgenden Fällen wird die Schaltfläche **Bearbeiten** angezeigt:

* Die Eigenschaft `advancedEditModeSupport` ist in der *capabilities.json*-Datei entweder auf `SupportedNoAction` oder auf `SupportedInFocus` festgelegt.

* Das Visual wird im Berichtsbearbeitungsmodus angezeigt.

Wenn die Eigenschaft `advancedEditModeSupport` in der *capabilities.json*-Datei fehlt oder auf `NotSupported` festgelegt ist, wird die Schaltfläche **Bearbeiten** nicht angezeigt.

![Aktivieren des Bearbeitungsmodus](./media/edit-mode.png)

Wenn Sie auf **Bearbeiten** klicken, empfängt das Visual einen update()-Aufruf, bei dem EditMode auf `Advanced` festgelegt ist. Abhängig von dem Wert, der in der *capabilities.json*-Datei festgelegt wird, treten die folgenden Aktionen auf:

* `SupportedNoAction`: Es ist keine weitere Aktion durch den Host erforderlich.
* `SupportedInFocus`: Der Host öffnet das Visual im Fokusmodus.

## <a name="exit-advanced-edit-mode"></a>Beenden des Modus „Erweiterte Bearbeitung“

Die Schaltfläche **Zurück zum Bericht** wird im folgenden Fall angezeigt:

* Die `advancedEditModeSupport`-Eigenschaft in der *capabilities.json*-Datei ist auf `SupportedInFocus` festgelegt.
