---
title: Planen von Berichten im Berichts-Generator von Power BI
description: Mithilfe des paginierten Berichts-Generators von Power BI können Sie viele Arten paginierter Berichte erstellen. Die Grundlage für einen hilfreichen und einfach verständlichen Bericht ist seine vorherige Planung.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fd4a318d7a61f6f2298de6b9d5d23ad2ae063d28
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840508"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Planen von Berichten im Berichts-Generator von Power BI
  Mithilfe des paginierten Berichts-Generators von Power BI können Sie viele Arten paginierter Berichte erstellen. Sie können beispielsweise Berichte erstellen, in denen eine Zusammenfassung von oder detaillierte Informationen zu Umsatzdaten, Marketing- und Umsatztrends, Funktionsberichte oder Dashboards angezeigt werden. Sie können auch Berichte erstellen, die Text im Rich Text Format (RTF) nutzen, z. B. für Verkaufsaufträge, Produktkataloge oder Serienbriefe. Alle diese Berichte werden mithilfe verschiedener Kombinationen derselben grundlegenden Bausteine im Berichts-Generator erstellt. Die Grundlage für einen hilfreichen und einfach verständlichen Bericht ist seine vorherige Planung. Diese Dinge sollten Sie berücksichtigen, bevor Sie loslegen:  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>In welchem Format soll der Bericht angezeigt werden?
  
Berichte können online in einem Browser gerendert werden, z. B. über das Power BI-Portal, oder in andere Formate exportiert werden, z. B. Excel, Word oder PDF. Das endgültige Format für Ihren Bericht zu bestimmen, ist eine wichtige Überlegung, da nicht alle Features für alle Exportformate verfügbar sind. 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>In welcher Struktur sollen die Daten angezeigt werden?
  
Sie können Daten als Tabelle, Matrix (ähnlich eines Kreuztabellen- oder PivotTable-Berichts), Diagramm, als Freiformstrukturen oder einer beliebigen Kombination dieser Möglichkeiten anzeigen lassen. Weitere Informationen finden Sie unter [Tables, Matrices, and Lists in Power BI Report Builder (Tabellen, Matrizen und Listen im Berichts-Generator in Power BI)](report-builder-tables-matrices-lists.md).  
  
## <a name="how-do-you-want-your-report-to-look"></a>Wie soll Ihr Bericht aussehen?
  
Der Berichts-Generator stellt viele Berichtselemente zur Verfügung, die Sie Ihrem Bericht hinzufügen können, z. B. um die Lesbarkeit zu vereinfachen, wichtige Informationen hervorzuheben oder die Zielgruppe beim Navigieren im Bericht zu unterstützen. Wenn Sie wissen, wie der Bericht aussehen soll, können Sie bestimmen, ob Sie Berichtselemente wie Textfelder, Rechtecke, Bilder und Linien benötigen. Vielleicht möchten Sie auch, dass Elemente angezeigt oder ausgeblendet werden, eine Dokumentstruktur hinzufügen, Drillthroughberichte oder Unterberichte einbinden oder andere Berichte verlinken.   
  
## <a name="should-the-data-be-filtered"></a>Sollten die Daten gefiltert werden?
  
Vielleicht möchten Sie auch, dass der Bericht nur bestimmte Benutzer oder bestimmte Speicherorte abdeckt, oder möglicherweise auch nur einen bestimmten Zeitraum. Wenn Sie die Berichtsdaten filtern möchten, können Sie Parameter verwenden, um nur die gewünschten Daten abzurufen und anzuzeigen. Weitere Informationen finden Sie unter [Report parameters in Power BI Report Builder (Berichtsparameter im Berichts-Generator von Power BI)](paginated-reports-parameters.md).  
  
## <a name="do-you-need-to-create-calculations"></a>Müssen Berechnungen erstellt werden? 
  
     Sometimes, your data source and datasets do not contain the exact fields that you need for your report. In that situation, you might have to create your own calculated fields. For example, you might want to multiply the price per unit times the quantity to get a line item sales amount. Expressions are also used to provide conditional formatting and other advanced features. For more information, see [Expressions in Power BI Report Builder](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>Sollen Berichtselemente anfangs ausgeblendet sein?
  
Überlegen Sie sich, ob Sie möchten, dass Berichtselemente ausgeblendet werden, einschließlich Datenbereichen und Gruppen und Spalten, wenn der Bericht das erste Mal ausgeführt wird. So könnte beispielsweise zuerst eine zusammenfassende Tabelle angezeigt werden, und dann könnten Sie einen Drilldown in die detaillierten Daten ausführen. 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>Wie soll Ihr Bericht zugestellt werden?  
  
     You can save your report to your local computer and continue to work on it, or run it locally for your own information. However, to share your report with others, you need to save the report to Power BI. Saving it to Power BI lets others run it whenever they want to. Alternatively, you can set up a subscription and e-mail delivery of the report to other individuals. You can have the report delivered in a specific export format if you prefer. 
  
## <a name="next-steps"></a>Nächste Schritte

- [Was sind paginierte Berichte in Power BI Premium? (Vorschau)](paginated-reports-report-builder-power-bi.md)
