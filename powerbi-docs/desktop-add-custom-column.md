---
title: Hinzufügen einer benutzerdefinierten Spalte in Power BI Desktop
description: Schnelles Erstellen einer neuen benutzerdefinierten Spalte in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5633370259662141296550aa3d5d2343ac4fedaa
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408558"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Hinzufügen einer benutzerdefinierten Spalte in Power BI Desktop
Mit dem **Abfrage-Editor** in **Power BI Desktop** können Sie dem Modell einfach eine neue benutzerdefinierte Datenspalte hinzufügen. Sie können mit einfachen Schaltflächen die benutzerdefinierte Spalte erstellen und umbenennen, um [M-Formeln](https://msdn.microsoft.com/library/mt270235.aspx) zum Definieren der benutzerdefinierten Spalte zu entwerfen. Die M-Formel weist einen [umfassenden Funktionsreferenz-Inhaltssatz](https://msdn.microsoft.com/library/mt779182.aspx) auf. 

![](media/desktop-add-custom-column/add-custom-column_01.png)

Das Erstellen einer benutzerdefinierten Spalte ist ein weiterer **angewendeter Schritt** für die Abfrage, die Sie im **Abfrage-Editor** erstellen. Das bedeutet, dass sie jederzeit geändert oder verschoben werden kann.

## <a name="use-query-editor-to-add-a-new-custom-column"></a>Hinzufügen einer neuen benutzerdefinierten Spalte mithilfe des Abfrage-Editors
Starten Sie zum Erstellen einer neuen benutzerdefinierten Spalte den **Abfrage-Editor**. Wählen Sie hierzu in **Power BI Desktop** auf dem Menüband **Start** die Option **Abfragen bearbeiten** aus.

![](media/desktop-add-custom-column/add-column-from-example_02.png)

Wenn der **Abfrage-Editor** gestartet wurde und Sie Daten geladen haben, können Sie eine benutzerdefinierte Spalte hinzufügen. Wählen Sie hierzu auf dem Menüband die Registerkarte **Spalte hinzufügen** und dann **Benutzerdefinierte Spalte** aus.

![](media/desktop-add-custom-column/add-custom-column_02.png)

Das im folgenden Abschnitt beschriebene Fenster **Benutzerdefinierte Spalte hinzufügen** wird angezeigt.

## <a name="the-add-custom-column-window"></a>Das Fenster „Benutzerdefinierte Spalte hinzufügen“
Im Fenster **Benutzerdefinierte Spalte hinzufügen** wird im rechten Bereich die Liste der verfügbaren Felder angezeigt, und oben wird der Name der benutzerdefinierten Spalte angezeigt (Sie können sie umbenennen, indem Sie in diesem Textfeld einen neuen Namen eingeben). Außerdem wird die [**M**-Formel](https://msdn.microsoft.com/library/mt779182.aspx) angezeigt, die Sie für die Definition der neuen benutzerdefinierten Spalte erstellen (oder eingeben), indem Sie Felder aus dem rechten Bereich einfügen, Operatoren hinzufügen und weitere Aktionen ausführen. 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Erstellen von Formeln für die benutzerdefinierte Spalte
Sie können in der Liste **Verfügbare Spalten** auf der rechten Seite ein Feld auswählen und auf **<< Einfügen** klicken, um es der Formel für die benutzerdefinierte Spalte hinzuzufügen. Sie können auch einfach auf eine Spalte in der Liste doppelklicken, um es hinzuzufügen.

Während Sie die Formel eingeben, um die Spalte zu erstellen, wird am unteren Rand des Fensters in Echtzeit (während der Eingabe) angegeben, ob Syntaxfehler gefunden werden. Wenn alles in Ordnung ist, wird ein grünes Häkchen angezeigt.

![](media/desktop-add-custom-column/add-custom-column_04.png)

Wenn die Syntax einen Fehler enthält, werden ein gelbes Warnsymbol zusammen mit dem erkannten Fehler und ein Link angezeigt, über den der Cursor (in der Formel) an die Position des erkannten Fehlers verschoben wird.

![](media/desktop-add-custom-column/add-custom-column_05.png)

Wenn Sie auf **OK** klicken, wird die benutzerdefinierte Spalte dem Modell hinzugefügt, und den **Angewendeten Schritten** der Abfrage wird der Schritt **Hinzugefügte benutzerdefinierte Spalte** hinzugefügt.

![](media/desktop-add-custom-column/add-custom-column_06.png)

Wenn Sie im Bereich **Angewendete Schritte** auf den Schritt **Hinzugefügte benutzerdefinierte Spalte** doppelklicken, wird erneut das Fenster **Benutzerdefinierte Spalte hinzufügen** angezeigt. In diesem ist die benutzerdefinierte Formel, die Sie erstellt haben, bereits geladen, und Sie können sie ggf. ändern.

## <a name="using-the-advanced-editor-for-custom-columns"></a>Verwenden des erweiterten Editors für benutzerdefinierte Spalten
Sie können auch mit dem **erweiterten Editor** benutzerdefinierte Spalten erstellen (und jeden Schritt der Abfrage ändern). Wählen Sie im **Abfrage-Editor** die Registerkarte **Ansicht** und dann **Erweiterter Editor** aus, um den **erweiterten Editor** anzuzeigen.

![](media/desktop-add-custom-column/add-custom-column_07.png)

Der **Erweiterte Editor** bietet Ihnen vollständige Kontrolle über Ihre Abfrage.

## <a name="next-steps"></a>Nächste Schritte
Es gibt weitere Möglichkeiten zum Erstellen einer benutzerdefinierten Spalte. Zu diesen zählt das Erstellen einer Spalte anhand von Beispielen, die Sie im **Abfrage-Editor** angeben. Weitere Informationen zum Erstellen von benutzerdefinierten Spalten aus Beispielen finden Sie im folgenden Artikel:

* [Hinzufügen einer Spalte aus einem Beispiel in Power BI Desktop](desktop-add-column-from-example.md)
* [Power Query M-Referenz](/powerquery-m/power-query-m-reference)  

