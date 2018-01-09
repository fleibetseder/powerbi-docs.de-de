---
title: SQL Server Analysis Services-Livedaten in Power BI
description: "SQL Server Analysis Services-Livedaten in Power BI. Dies erfolgt über eine Datenquelle, die für ein Enterprise-Gateway konfiguriert wurde."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 6925dc9bcf3e500af18cf63c62f6cb33c297392b
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2017
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>SQL Server Analysis Services-Livedaten in Power BI
In Power BI gibt es zwei Möglichkeiten, die Verbindung mit einem SQL Server Analysis Services-Liveserver herzustellen. In **Daten abrufen** können Sie eine Verbindung mit einem SQL Server Analysis Services-Server oder aber mit einer [Power BI Desktop-Datei](service-desktop-files.md) bzw. einer [Excel-Arbeitsmappe](service-excel-workbook-files.md) herstellen, die bereits mit einem Analysis Services-Server verbunden ist.

 >[!IMPORTANT]
 >* Zum Herstellen einer Verbindung mit einem Analysis Services-Liveserver muss ein lokales Datengateway von einem Administrator installiert und konfiguriert werden. Weitere Informationen finden Sie unter [Lokales Datengateway](service-gateway-onprem.md).
 >* Wenn Sie das Gateway verwenden, bleiben Ihre Daten lokal verfügbar.  Die von Ihnen auf Basis dieser Daten erstellten Berichte werden im Power BI-Dienst gespeichert. 
 >* [Die F&A-Abfragen in natürlicher Sprache](service-q-and-a-direct-query.md) sind für Analysis Services-Liveverbindungen in der Vorschauversion verfügbar.

## <a name="to-connect-to-a-model-from-get-data"></a>So stellen Sie über „Daten abrufen“ eine Verbindung zu einem Modell her
1. Klicken Sie unter **Mein Arbeitsbereich** auf **Daten abrufen**. Sie können auch zu einem Gruppenarbeitsbereich wechseln, sofern verfügbar.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)
2. Wählen Sie **Datenbanken und mehr** aus.
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)
3. Wählen Sie **SQL Server Analysis Services** > **Verbinden** aus. 
   
   ![](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)
4. Wählen Sie einen Server aus. Wenn keine der hier aufgeführten Server angezeigt werden, wurde entweder kein Gateway und keine Datenquelle konfiguriert oder Ihr Konto ist nicht auf der Registerkarte **Benutzer** der Datenquelle im Gateway aufgeführt. Wenden Sie sich an Ihren Administrator.
5. Wählen Sie das Modell aus, mit dem Sie eine Verbindung herstellen möchten. Dieses kann tabellarisch oder mehrdimensional sein.

Nachdem Sie die Verbindung mit dem Modell hergestellt haben, wird es auf der Power BI-Website unter **Mein Arbeitsbereich/Datasets**angezeigt. Bei einem Wechsel zu einem Gruppenarbeitsbereich wird das Dataset in der Gruppe angezeigt.

![](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Dashboardkacheln
Wenn Sie visuelle Elemente aus einem Bericht auf dem Dashboard anheften, werden die angehefteten Kacheln automatisch alle 10 Minuten aktualisiert. Wenn die Daten auf Ihrem lokalen Analysis Services-Server aktualisiert werden, werden die Kacheln nach 10 Minuten automatisch aktualisiert.

## <a name="next-steps"></a>Nächste Schritte
[Lokales Datengateway](service-gateway-onprem.md)  
[Verwalten von Analysis Services-Datenquellen](service-gateway-enterprise-manage-ssas.md)  
[Problembehandlung beim lokalen Datengateway](service-gateway-onprem-tshoot.md)  
Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
