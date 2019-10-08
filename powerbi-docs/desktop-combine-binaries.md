---
title: Kombinieren von (binären) Dateien in Power BI Desktop
description: Einfaches Kombinieren von (binären) Datenquellen in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8a5b4c7cb484b296ccab395e18eb2b0089ffd5c7
ms.sourcegitcommit: e2c5d4561455c3a4806ace85defbc72e4d7573b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327819"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Kombinieren von (binären) Dateien in Power BI Desktop
Ein sehr effizienter Ansatz zum Importieren von Daten in **Power BI Desktop** ist das Kombinieren mehrerer Dateien, die das gleiche Schema aufweisen, in einer einzelnen logischen Tabelle. Dieser beliebte Ansatz wurde vereinfacht und erweitert, wie in diesem Artikel beschrieben.

Wählen Sie **Daten abrufen > Datei > Ordner** aus, um mit dem Kombinieren von Dateien aus demselben Ordner zu beginnen.

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>Verhalten beim Kombinieren von Dateien
Sie können **(binäre) Dateien kombinieren**, indem Sie **Dateien kombinieren** auswählen, entweder auf der Registerkarte **Start** des Menübands im **Abfrage-Editor** oder in der Spalte selbst.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

Die Transformation **Dateien kombinieren** weist das folgende Verhalten auf:

* Die Transformation **Dateien kombinieren** analysiert jede Eingabedatei und bestimmt das richtige zu verwendende Dateiformat, z.B. *Text*-, *Excel-Arbeitsmappen*- oder *JSON*-Datei.
* Die Transformation ermöglicht Ihnen die Auswahl eines bestimmten Objekts aus der ersten Datei, z. B. einer *Excel-Arbeitsmappe*, das extrahiert werden soll.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Über **Dateien kombinieren** werden anschließend automatisch folgende Abfragen ausgeführt:
  
  * Erstellen einer Musterabfrage, die alle erforderlichen Extraktionsschritte in einer einzelnen Datei ausführt.
  * Erstellen einer *Funktionsabfrage*, die die Datei-/Binäreingabe in die *Musterabfrage* parametrisiert. Die Musterabfrage und die Funktionsabfrage werden verknüpft, sodass Änderungen an der Musterabfrage in der Funktionsabfrage wiedergegeben werden.
  * Anwenden der *Funktionsabfrage* mit Eingabebinärdateien auf die ursprüngliche Abfrage (z. B. auf die *Ordner*-Abfrage), sodass die Funktionsabfrage für Binäreingaben in jeder Zeile angewendet wird. Anschließend wird die resultierende Datenextraktion als Spalten der obersten Ebene erweitert.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Der Umfang Ihrer Auswahl in einer Excel-Arbeitsmappe beeinflusst das Verhalten von kombinierten Binärdateien. Beispielsweise können Sie ein bestimmtes Arbeitsblatt auswählen, um das Arbeitsblatt zu kombinieren, oder Sie können den Stamm auswählen, um die vollständige Datei zu kombinieren. Wenn Sie einen Ordner auswählen, werden die in diesem Ordner gefundenen Dateien kombiniert. 


Mit dem Verhalten von **Dateien kombinieren** können Sie alle Dateien in einem bestimmten Ordner einfach kombinieren, solange sie den gleichen Dateityp und die gleiche Struktur (z. B. die gleichen Spalten) aufweisen.

Außerdem können Sie einfach zusätzliche Transformations- oder Extraktionsschritte anwenden, indem Sie die automatisch erstellte *Musterabfrage* ändern. Dabei müssen Sie keine Schritte der *Funktionsabfrage* ändern und keine zusätzlichen Schritte für sie erstellen. Alle Änderungen an der *Musterabfrage* werden automatisch in der verknüpften *Funktionsabfrage* generiert.

## <a name="next-steps"></a>Nächste Schritte
Sie können mithilfe von Power BI Desktop eine Verbindung mit Daten jeglicher Art herstellen. Weitere Informationen zu Datenquellen finden Sie in folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit CSV-Dateien in Power BI Desktop](desktop-connect-csv.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

