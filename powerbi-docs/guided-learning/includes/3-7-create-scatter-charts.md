---
ms.openlocfilehash: cab4d5f47c7e0518bae3c11b3f298802cb67f6d7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61396821"
---
Wenn Sie zwei verschiedene Measures, z. B. Stückverkäufe und Umsatzerlös, vergleichen möchten, wird als Visualisierung häufig ein Punktdiagramm verwendet.

![](media/3-7-create-scatter-charts/3-7_1.png)

Wählen Sie zum Erstellen eines leeren Diagramms die Option **Punktdiagramm** im Bereich **Visualisierungen** aus. Ziehen Sie die beiden Felder, die Sie vergleichen möchten, vom Bereich **Felder** auf die Bucketoptionen *X-Achse* und *Y-Achse*. Nun wird in der Mitte des Punktdiagramms wahrscheinlich nur eine kleine Blase angezeigt. Sie müssen dem Bucket *Details* ein Measure hinzufügen, um anzugeben, wie die Daten segmentiert werden sollen. Wenn Sie beispielsweise die Stückverkäufe mit dem Umsatzerlös vergleichen, möchten Sie die Daten möglicherweise nach Kategorie, Hersteller oder Verkaufsmonat untergliedern.

Durch Hinzufügen eines weiteren Felds zum Bucket *Legende* werden die Blasen entsprechend dem Wert des Felds farbkodiert. Sie können zudem dem Bucket *Größe* ein Feld hinzufügen, um die Blasengröße entsprechend diesem Wert zu ändern.

![](media/3-7-create-scatter-charts/3-7_2.png)

Punktdiagramme verfügen außerdem über zahlreiche visuelle Formatierungsoptionen, z. B. Aktivieren einer Kontur für die einzelnen farbigen Blasen und Umschalten einzelner Beschriftungen. Sie können auch die Datenfarben für andere Diagrammtypen ändern.

![](media/3-7-create-scatter-charts/3-7_3.png)

Sie können eine Animation der Änderungen des Blasendiagramms im Verlauf der Zeit erstellen, indem Sie dem Bucket *Wiedergabeachse* einen zeitbasierten Wert hinzufügen. Wenn Sie während der Animation auf eine Blase klicken, wird der entsprechende Ablauf angezeigt.

![](media/3-7-create-scatter-charts/3-7_4.png)

>[!NOTE]
>Wenn in einem Punktdiagramm nur eine Blase angezeigt wird, liegt das daran, dass die Daten in Power BI standardmäßig aggregiert werden. Fügen Sie dem Bucket *Details* im Bereich **Visualisierungen** eine Kategorie hinzu, damit weitere Blasen angezeigt werden.
> 
> 

