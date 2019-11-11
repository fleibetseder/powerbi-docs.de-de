---
title: Erstellen benutzerdefinierter Power BI-Antwortseiten für Cortana
description: Erstellen von benutzerdefinierten Antwortseiten für Cortana in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 06f155676dffa7b5f87ce61a8b342708793ef2c6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73853744"
---
# <a name="use-power-bi-service-or-power-bi-desktop-to-create-a-custom-answer-page-for-cortana"></a>Verwenden des Power BI-Diensts oder von Power BI Desktop zum Erstellen einer benutzerdefinierten Antwortseite für Cortana
Verwenden Sie sämtliche Funktionen von Power BI zum Erstellen von speziellen Berichtsseiten, die als *Cortana-Antwortseiten* (und gelegentlich als *Cortana-Antwortkarten*) bezeichnet werden und zur Beantwortung von Cortana-Fragen entworfen wurden.

> [!IMPORTANT]
> Die Cortana-Integration in Power BI wird eingestellt. Ab dem 11. Juni funktioniert Cortana nicht mehr für Dashboards und Berichte.

![](media/service-cortana-answer-cards/power-bi-cortana.png)

## <a name="before-you-begin"></a>Vorbereitung
Insgesamt gibt es vier Dokumente, in denen Sie ausführliche Anweisungen zum Einrichten und Verwenden von Cortana für Power BI erhalten. Sofern nicht bereits geschehen, lesen Sie zuerst Artikel 1. Artikel 2 ist besonders wichtig, denn darin werden einige Schritte beschrieben, die Sie ausführen müssen, ehe Sie Cortana-Antwortseiten verwenden können.

**Artikel 1**: [Informationen zur Zusammenarbeit von Cortana und Power BI](service-cortana-intro.md)

**Artikel 2**: [Zum Durchsuchen von Power BI-Berichten: Aktivieren von Cortana für den Zugriff auf Power BI-Berichte](service-cortana-enable.md)

**Artikel 3**: Dieser Artikel

**Artikel 4**: [Behandeln von Problemen](service-cortana-troubleshoot.md)

## <a name="create-a-cortana-answer-page-designed-specifically-for-cortana"></a>Erstellen einer Cortana-Antwortseite, die speziell für Cortana entworfen wurde
Die Größe einer *Cortana-Antwortseite* in einem Bericht ist speziell für Cortana angepasst, sodass Cortana sie als Antwort auf eine Frage auf dem Bildschirm anzeigen kann. So erstellen Sie eine Antwortseite für Cortana:

1. Es wird empfohlen, mit einer leeren Berichtseite zu beginnen.
2. Klicken Sie im Bereich **Visualisierungen** erst auf das Farbrollersymbol und dann auf **Seitengröße** > **Typ** > **Cortana**.
   
    ![](media/service-cortana-answer-cards/pbi-cortana-page-size-new.png)
3. Erstellen Sie eine oder mehrere Visualisierungen, die in Cortana als Antwort auf eine bestimmte Frage (oder eine Reihe von Fragen) angezeigt werden sollen.

> [!NOTE]
> Momentan unterstützten Cortana-Antwortseiten keine Bilder, auf denen statische Bilder zu sehen sind. Sie können Bilder in Tabellen- oder Matrixvisuals einbeziehen, die dynamisch mithilfe von Pull basierend auf einer URL in Ihren Daten übertragen werden. 
> 
> 

4. Stellen Sie sicher, dass alle Visualisierungen auf die Seite passen. Ändern Sie optional die Anzeigeoptionen, Datenbeschriftungen, Farben und Hintergründe.  
   
    ![](media/service-cortana-answer-cards/pbi_cortana_modify-new.png)
5. Benennen Sie die Seite, und fügen Sie alternative Namen hinzu. Cortana verwendet diese Namen bei der Suche nach Ergebnissen. Wählen Sie im Bereich **Visualisierungen** das Pinselsymbol und dann **Seiteninformationen** aus. Aktivieren Sie Q&A für diese Visualisierung durch Verschieben des Schiebereglers auf **Ein**.
   
    ![](media/service-cortana-answer-cards/pbi_cortana_names-newer.png)
   
   > [!TIP]
   > Um die Ergebnisse zu verbessern, sollten Sie keine Wörter verwenden, die auch Spaltennamen sind.
   > 
   > 
6. Wenn der Bericht über Filter auf Seitenebene verfügt, sollten Sie **Einfachauswahl erforderlich** festlegen (optional). Cortana zeigt diesen Bericht nur dann als Antwort an, wenn ein einziges der Filterelemente in der Frage angegeben ist. **Einfachauswahl erforderlich** wird unten im Bereich **Filter** angezeigt.
   
   > [!NOTE]
   > Damit Cortana einen Bericht mit Seitenebenenfiltern anzeigen kann, muss **Einfachauswahl erforderlich** nicht festgelegt werden. Beispiel: Die Aufforderung „Verkäufe für Charlotte Lindseys anzeigen“ erzeugt unabhängig von der Einstellung „Einfachauswahl erforderlich“ eine Antwortseite.
   > 
   > 
   
     ![](media/service-cortana-answer-cards/pbi-cortana-single-selection-new.png)
   
      Wenn Sie Cortana beispielsweise folgende Fragen stellen:
   
   * „Verkäufe nach Ladenname anzeigen“: Diese Antwortseite wird nicht angezeigt, da Sie keines der Elemente zum erforderlichen Seitenebenenfilter hinzugefügt haben.
   * „Verkäufe für Cary Lindseys und Charlotte Lindseys anzeigen“: Diese Antwortseite wird nicht angezeigt, da Sie mehr als ein Element aus dem erforderlichen Seitenebenenfilter angegeben haben.
   * „Verkäufe für Charlotte Lindseys anzeigen“: Diese Antwortseite wird angezeigt.
     
     = „Umsätze anzeigen“: Diese Antwortseite wird nicht angezeigt, da Sie keines der Elemente zum erforderlichen Seitenebenenfilter hinzugefügt haben.

> [!IMPORTANT]
> Bevor Cortana auf Ihre Cortana-Antwortseite zugreifen kann, müssen Sie [das Dataset für Cortana aktivieren](service-cortana-enable.md).
> 
> 

## <a name="how-does-cortana-order-the-results"></a>Wie sortiert Cortana die Ergebnisse?
Ergebnisse mit hoch bewerteten Antworten (z.B. vollständige Übereinstimmung mit einem angegebenen Seitennamen) werden als erstes als *beste Übereinstimmung* in Cortana angezeigt. Mehrere beste Übereinstimmungen können angezeigt werden, wenn in Power BI mehrere Cortana-Antwortseiten vorhanden sind. Mittel oder niedrig bewertete Antworten, z.B. Antworten, die nicht auf dem Namen einer Antwortseite basieren, oder eine Frage mit Wörtern, die von Power BI nicht verstanden wurden, werden als Links unter den besten Übereinstimmungen in Cortana aufgeführt.

> [!NOTE]
> Wenn Power BI ein neues Dataset oder eine benutzerdefinierte Cortana-Antwortseite hinzugefügt und für Cortana aktiviert wird, kann es bis zu 30 Minuten dauern, bis Ergebnisse in Cortana angezeigt werden. Durch das Anmelden und Abmelden bei Windows 10 oder einen Neustart des Cortana-Prozesses in Windows 10 werden neue Inhalte sofort angezeigt.
> 
> 

## <a name="next-steps"></a>Nächste Schritte
[Verwenden von Cortana mit Power BI](service-cortana-intro.md)

Können Sie Cortana immer noch nicht mit Power BI verwenden?  Verwenden Sie die [Cortana-Problembehandlung](service-cortana-troubleshoot.md).

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](https://community.powerbi.com/)

