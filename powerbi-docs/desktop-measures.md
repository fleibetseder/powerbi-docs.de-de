---
title: Verwenden von Measures in Power BI Desktop
description: Measures in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/29/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: d5ada41ef4941f14118b777e37e731337a5282d0
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715399"
---
# <a name="measures-in-power-bi-desktop"></a>Measures in Power BI Desktop

**Power BI Desktop** hilft Ihnen, Einblicke in Ihre Daten mit nur ein paar Mausklicks zu gewinnen. Manchmal enthalten diese Daten aber einfach nicht alles, was Sie für die Antwort auf Ihre drängendsten Fragen benötigen. Measures können Ihnen in dieser Situation weiterhelfen.

Measures werden in einigen der am häufigsten verwendeten Datenanalysen verwendet. Einfache Zusammenfassungen wie Summen, Mittelwerte, Mindestwerte, Höchstwerte und Anzahlen können über den Bereich „Felder“ festgelegt werden. Die berechneten Ergebnisse von Measures ändern sich ständig in Reaktion auf Ihre Interaktion mit Berichten und ermöglichen so eine schnelle und dynamische Untersuchung von Daten ohne Vorlauf. Sehen wir uns das einmal näher an. Weitere Informationen finden Sie unter [Erstellen berechneter Measures](/learn/modules/model-data-power-bi/4b-create-calculated-measures).

## <a name="understanding-measures"></a>Grundlegendes zu Measures

In **Power BI Desktop** werden Measures in der **Berichtsansicht** oder in der **Datenansicht** angezeigt. Von Ihnen selbst erstellte Measures werden in der Feldliste mit einem Rechnersymbol angezeigt. Sie können Measures nach Belieben benennen und sie einer neuen oder vorhandenen Visualisierung ganz wie jedes andere Feld hinzufügen.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Vielleicht sind auch **Quickmeasures** für Sie interessant. Hierbei handelt es sich um vordefinierte Measures, die in Dialogfeldern ausgewählt werden können. Sie bieten eine ideale Möglichkeit, schnell Measures zu erstellen. Zudem empfehlen sie sich, um die DAX-Syntax kennenzulernen, indem Sie sich die automatisch erstellten DAX-Formeln einmal näher ansehen. Lesen Sie den folgenden Artikel: [Quickmeasures](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions

Measures berechnen ein Ergebnis mithilfe einer Ausdrucksformel. Zum Erstellen eigener Measures verwenden Sie die [DAX-Formelsprache](https://msdn.microsoft.com/library/gg413422.aspx) (Data Analysis Expressions). DAX beinhaltet eine Bibliothek mit über 200 Funktionen, Operatoren und Konstrukten. Die Bibliothek bietet immense Flexibilität beim Erstellen von Measures zum Berechnen von Ergebnissen für nahezu jede benötigte Datenanalyse.

DAX-Formeln sind Excel-Formeln ziemlich ähnlich. DAX weist sogar viele der gleichen Funktionen auf wie Excel, z.B. DATUM, SUMME und LINKS. Aber die DAX-Funktionen sind für relationale Daten ausgelegt, wie wir sie in Power BI Desktop verwenden.

## <a name="lets-look-at-an-example"></a>Betrachten wir dazu ein Beispiel.
Lea ist Vertriebsmanagerin bei Contoso. Lea wird gebeten, Umsatzprognosen für Handelspartner für das nächste Geschäftsjahr zu erstellen. Lea entscheidet sich, ihren Schätzungen die Umsatzbeträge des letzten Jahres zugrunde zu legen und geht von einer jährlichen Steigerung von sechs Prozent aus, die sich aus verschiedenen Werbeaktionen ergeben, die für das nächste halbe Jahr geplant sind.

Um die Schätzungen zu melden, importiert Lea die Umsatzdaten des letzten Jahres in Power BI Desktop. Lea findet das Feld „SalesAmount“ (Umsatzbetrag) in der Tabelle „Reseller Sales“ (Umsätze von Handelspartnern). Da die importierten Daten nur die Umsätze des letzten Jahres enthalten, benennt Lea das Feld „SalesAmount“ (Umsatzbetrag) in „Last Years Sales“ (Umsätze Vorjahr) um. Anschließend zieht Lea „Last Years Sales“ auf den Berichtszeichenbereich. Das Feld wird im visualisierten Diagramm als Einzelwert dargestellt, bei dem es sich um die Summe aller Umsätze von Handelspartnern aus dem letzten Jahr handelt.

Lea fällt auf, dass eine Berechnung automatisch durchgeführt wurde, obwohl sie selbst keine Berechnung angegeben hat. Power BI Desktop hat ein eigenes Measure erstellt, indem er alle Werte aus „Umsätze letztes Jahr“ addiert hat.

Lea benötigt jedoch ein Measure zum Berechnen der Prognosen für das nächste Jahr, das auf den Umsätzen des letzten Jahres basiert, multipliziert mit 1,06, um dem erwarteten Wachstum der Geschäftsaktivitäten von 6 Prozent Rechnung zu tragen. Für diese Berechnung erstellt Lea ihr eigenes Measure. Mithilfe des Features „Neues Measure“ erstellt sie ein neues Measure und gibt dann die folgende DAX-Formel ein:

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Lea zieht dann ihr neues Measure „Projected Sales“ (Projizierte Umsätze) auf das Diagramm.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Sehr schnell und mit minimalem Aufwand hat Lea nun ein Measure zum Berechnen der geplanten Umsatzzahlen erstellt. Sie kann ihre Prognosen (Schätzung) noch genauer analysieren, indem sie nach bestimmten Handelspartnern filtert oder dem Bericht andere Felder hinzufügt.

## <a name="data-categories-for-measures"></a>Datenkategorien für Measures

Sie können auch die Datenkategorien für Measures auswählen. 

Dadurch können Sie unter anderem Measures zum dynamischen Erstellen von URLs verwenden und die Datenkategorie als Web-URL markieren. 

Sie können Tabellen erstellen, die die Measures als Web-URLs anzeigen, und Sie können auf die URL klicken, die basierend auf Ihrer Auswahl erstellt wird. Dies ist insbesondere dann nützlich, wenn Sie eine Verknüpfung mit anderen Power BI-Berichten mithilfe von [URL-Filterparametern](service-url-filters.md) erstellen möchten.


## <a name="organizing-your-measures"></a>Organisieren Ihrer Measures

Measures verfügen über eine *Hometabelle*, in der definiert wird, wo sie in der Feldliste zu finden sind. Sie können deren Position ändern, indem Sie eine Position aus den Tabellen in Ihrem Modell auswählen.

![Auswählen einer Tabelle für Ihr Measure](media/desktop-measures/measures-03.png)

Sie können Felder in einer Tabelle auch in *Anzeigeordnern* organisieren. Wählen auf der linken Seite des Power BI Desktop-Fensters **Modellansicht** aus, wählen Sie anschließend das zu verschiebende Feld aus, das sich auf dem Zeichenbereich in der Liste befindet. Im Eigenschaftenbereich wird ein Textfeld für **Anzeigeordner** angezeigt. Wenn ein Name in das Feld **Anzeigeordner** eingegeben wird, wird der Ordner erstellt, und das ausgewählte Feld wird in diesen Ordner verschoben.

![Erstellen eines Felds für Measures](media/desktop-measures/measures-04.gif)

Sie können Unterordner erstellen, indem Sie einen umgekehrten Schrägstrich verwenden. Beispielsweise erstellt *Finance\Currencies* (Finanzen/Währungen) einen Ordner *Finance* (Finanzen) und darin einen Ordner *Currencies* (Währungen).

Sie können einstellen, dass ein Feld in mehreren Ordnern angezeigt wird, indem Sie ein Semikolon verwenden, um die Ordnernamen zu trennen. Zum Beispiel führt die Aufteilung *Products\Names;Departments* (Produkte\Namen;Abteilungen) dazu, dass das Feld im Ordner *Departments* (Abteilungen) und im Ordner *Names* (Namen) innerhalb eines *Products*-Ordners (Produkte) angezeigt wird.

Schließlich können Sie eine spezielle Tabelle erstellen, die nur Measures enthält, die grundsätzlich oben in der **Feldliste** angezeigt werden. Erstellen Sie hierzu eine Tabelle mit nur einer Spalte. Sie können **Daten eingeben** nutzen, um die Tabelle zu erstellen. Verschieben Sie dann die Measures in diese Tabelle. Blenden Sie schließlich die Spalte (nicht die Tabelle) aus, die Sie erstellt haben. Sie müssen die **Feldliste** schließen und erneut öffnen, damit Power BI Desktop sie richtig anzeigen kann. Klicken Sie dazu auf das Chevron am oberen Rand der **Feldliste**.

![Organisieren von Measures und diese oben in der Feldliste beibehalten](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>Weitere Informationen
Wir haben Ihnen hier nur eine kurze Einführung in Measures vorgestellt, aber es gibt noch viel mehr, das Ihnen hilft, das Erstellen eigener Measures zu lernen. Sehen sich unbedingt das [Tutorial: Erstellen eigener Measures in Power BI Desktop](desktop-tutorial-create-measures.md) an, für das Sie eine Beispieldatei herunterladen und schrittweise Lektionen zum Erstellen weiterer Measures abrufen können.  

Wenn Sie sich eingehender mit DAX befassen möchten, lesen Sie [DAX-Grundlagen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Die [DAX-Referenz](https://msdn.microsoft.com/library/gg413422.aspx) stellt detaillierte Artikel zu den einzelnen Funktionen, zu Syntax, Operatoren und Benennungskonventionen zur Verfügung. DAX ist schon seit mehreren Jahren in Power Pivot in Excel und SQL Server Analysis Services verfügbar. Aus diesem Grund sind noch viele weitere Ressourcen verfügbar. Sehen Sie sich unbedingt das [DAX-Ressourcencenter-Wiki](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx) an, in dem kompetente Mitglieder der BI-Community ihre DAX-Kenntnisse mit anderen teilen.



