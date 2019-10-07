---
title: Hinzufügen von Hyperlinks (URLs) zu einer Tabelle
description: In diesem Thema erfahren Sie, wie Sie Hyperlinks (URLs) einer Tabelle hinzufügen. Mit Power BI Desktop fügen Sie einer Tabelle oder Matrix Hyperlinks (URLs) hinzu. Dann können Sie entweder in Power BI Desktop oder dem Power BI-Dienst diese Hyperlinks Ihren Berichtstabellen und Matrizen hinzuzufügen.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/30/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: b158e968d0fd35859cfd293177a7273e8311d5b2
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715290"
---
# <a name="add-hyperlinks-urls-to-a-table"></a>Hinzufügen von Hyperlinks (URLs) zu einer Tabelle
In diesem Thema erfahren Sie, wie Sie Hyperlinks (URLs) einer Tabelle hinzufügen. Mit Power BI Desktop fügen Sie einer Tabelle oder Matrix Hyperlinks (URLs) hinzu. Dann können Sie entweder in Power BI Desktop oder dem Power BI-Dienst diese Hyperlinks Ihren Berichtstabellen und Matrizen hinzuzufügen. 

![Tabelle mit Links](media/power-bi-hyperlinks-in-tables/hyperlinkedtable.png)

> [!NOTE]
> Sie können Hyperlinks in [Kacheln in Dashboards](service-dashboard-edit-tile.md) und [Textfeldern in Dashboards](service-dashboard-add-widget.md) dynamisch mit dem Power BI-Dienst erstellen. Sie können Hyperlinks in [Textfeldern in Berichten](service-add-hyperlink-to-text-box.md) dynamisch mit dem Power BI-Dienst und Power BI Desktop erstellen.
> 

## <a name="to-create-a-hyperlink-in-a-table-or-matrix-using-power-bi-desktop"></a>So erstellen Sie mithilfe von Power BI Desktop einen Hyperlink in einer Tabelle oder Matrix
Sie können Hyperlinks in Tabellen und Matrizen in Power BI Desktop, jedoch nicht im Power BI-Dienst erstellen. Sie können außerdem Hyperlinks in Power Pivot für Excel erstellen, bevor Sie die Arbeitsmappe in Power BI importieren. Beide Methoden werden nachfolgend beschrieben.

## <a name="create-a-table-or-matrix-hyperlink-in-power-bi-desktop"></a>Erstellen eines Tabellen- oder Matrix-Hyperlinks in Power BI Desktop
Das Verfahren zum Hinzufügen eines Hyperlinks hängt davon ab, ob Sie die Daten importiert oder über DirectQuery eine Verbindung mit ihnen hergestellt haben. Beide Szenarien werden nachfolgend beschrieben.

### <a name="for-data-imported-into-power-bi"></a>Für in Power BI importierte Daten
1. Wenn der Hyperlink nicht bereits als Feld im Dataset vorhanden ist, fügen Sie ihn mit Power BI Desktop als [benutzerdefinierte Spalte](desktop-common-query-tasks.md) hinzu.
2. Wählen Sie in der Datenansicht die Spalte aus, und wählen Sie auf der Registerkarte **Modellierung** das Dropdownmenü für **Datenkategorie** aus.
   
    ![Dropdownliste „Datenkategorie“](media/power-bi-hyperlinks-in-tables/pbi_data_category.png)
3. Wählen Sie **Web-URL**aus.
4. Wechseln Sie zur Berichtsansicht, und erstellen Sie mit dem als Web-URL kategorisierten Feld eine Tabelle oder Matrix. Die Hyperlinks werden blau und unterstrichen angezeigt.

    ![Blaue und unterstrichene Links](media/power-bi-hyperlinks-in-tables/power-bi-table-with-hyperlinks2.png)

    > [!NOTE]
    > Die URLs müssen mit **http://, https://** oder **www** beginnen.
    >
   
1. Wenn keine lange URL in einer Tabelle angezeigt werden soll, können Sie stattdessen ein Linksymbol  ![Linksymbol](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) anzeigen lassen. Beachten Sie, dass Symbole nicht in Matrizen angezeigt werden können.
   
    Wählen Sie das Diagramm aus, um es zu aktivieren.

    Formatierungssymbol auswählen ![Farbrollensymbol](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png) aus, um die Registerkarte „Formatierung“ zu öffnen.

    Erweitern Sie **Werte**, suchen Sie das **URL-Symbol**, und aktivieren Sie es mit **Ein**.

    ![URL-Symbol aktivieren](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (Optional) [Veröffentlichen Sie den Bericht aus Power BI Desktop im Power BI-Dienst](/learn/modules/publish-share-power-bi/2-publish-reports), und öffnen Sie den Bericht im Power BI-Dienst. Die Hyperlinks werden hier ebenfalls geöffnet.

### <a name="for-data-connected-with-directquery"></a>Für über DirectQuery verbundene Daten
Im DirectQuery-Modus kann keine neue Spalte erstellt werden.  Wenn die Daten jedoch bereits URLs enthalten, können Sie diese in Hyperlinks umwandeln.

1. Erstellen Sie in der Berichtsansicht eine Tabelle mit einem Feld, das URLs enthält.
2. Wählen Sie die Spalte aus, und wählen Sie anschließend auf der Registerkarte **Modellierung** das Dropdownmenü für **Datenkategorie** aus.
3. Wählen Sie **Web-URL**aus. Die Hyperlinks werden blau und unterstrichen angezeigt.
4. (Optional) [Veröffentlichen Sie den Bericht aus Power BI Desktop im Power BI-Dienst](/learn/modules/publish-share-power-bi/2-publish-reports), und öffnen Sie den Bericht im Power BI-Dienst. Die Hyperlinks werden hier ebenfalls geöffnet.

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>Erstellen eines Tabellen- oder Matrix-Hyperlinks in Power Pivot für Excel
Sie können Ihren Power BI-Tabellen und -Matrizen auch Hyperlinks hinzufügen, indem Sie die Hyperlinks im Dataset erstellen, bevor Sie das betreffende Dataset aus Power BI importieren bzw. eine Verbindung damit herstellen. In diesem Beispiel wird eine Excel-Arbeitsmappe verwendet.

1. Öffnen Sie die Arbeitsmappe in Excel.
2. Wählen Sie die Registerkarte **PowerPivot** und anschließend **Verwalten**.
   
   ![Öffnen von PowerPivot in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. Wenn PowerPivot geöffnet wird, wählen Sie die Registerkarte **Erweitert** aus.
   
   ![Registerkarte „PowerPivot – Erweitert“](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. Platzieren Sie den Cursor in der Spalte, die die URLs enthält, die in Links in Power BI-Tabellen umgewandelt werden sollen.
   
   > [!NOTE]
   > Die URLs müssen mit **http://, https://** oder **www** beginnen.
   > 
5. Wählen Sie in der Gruppe **Berichtseigenschaften** die Dropdownliste **Datenkategorie** und wählen Sie dann **Web-URL**aus. 
   
   ![Dropdownliste „Datenkategorie“ in Excel](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. Stellen Sie aus dem Power BI-Dienst oder Power BI Desktop eine Verbindung mit dieser Arbeitsmappe her, oder importieren Sie sie.
7. Erstellen Sie eine Tabellenvisualisierung, die das URL-Feld enthält.
   
   ![Erstellen einer Tabelle in Power BI mit URL-Feld](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>Zu beachtende Aspekte und Problembehandlung
F: Kann ich eine benutzerdefinierte URL als Link in einer Tabelle oder Matrix verwenden?    
A: Nein. Sie können ein Linksymbol verwenden. Wenn Sie benutzerdefinierten Text für Ihre Links benötigen und die Liste der URLs kurz ist, sollten Sie stattdessen ein Textfeld verwenden.


## <a name="next-steps"></a>Nächste Schritte
[Visualisierungen in Power BI-Berichten](visuals/power-bi-report-visualizations.md)

[Grundlegende Konzepte für Designer im Power BI-Dienst](service-basic-concepts.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

