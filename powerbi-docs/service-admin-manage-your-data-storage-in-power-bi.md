---
title: Verwalten des Datenspeichers in Ihren Arbeitsbereichen
description: Hier erfahren Sie, wie Sie den Datenspeicher in Ihrem individuellen oder allgemeinen Arbeitsbereich verwalten, um sicherzustellen, dass Sie weiterhin Berichte und Datasets veröffentlichen können.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: f8e7240b34e20a3d18443cadb5265c5d0d870790
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73873658"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Verwalten des Datenspeichers in Power BI-Arbeitsbereichen

Hier erfahren Sie, wie Sie den Datenspeicher in Ihrem individuellen oder allgemeinen Arbeitsbereich verwalten, um sicherzustellen, dass Sie weiterhin Berichte und Datasets veröffentlichen können.

Benutzer und Arbeitsbereiche weisen jeweils eigene Datenkapazitäten auf:

* Alle Benutzer verfügen über maximal 10 GB Datenspeicher.
* Benutzer mit einer Power BI Pro-Lizenz können Arbeitsbereiche mit jeweils maximal 10 GB Datenspeicher erstellen.
* In einer Premium-Kapazität wird ein Arbeitsbereich nicht auf den Speicher eines Power BI Pro-Benutzers angerechnet.

Auf Mandantenebene darf der gesamte genutzte Datenspeicher für alle Pro-Benutzer und Arbeitsbereiche im Mandanten 10 GB je Pro-Benutzer nicht überschreiten.

Informieren Sie sich über weitere Funktionen des [Power BI-Preismodells](https://powerbi.microsoft.com/pricing).

Ihr Datenspeicher umfasst die eigenen Datasets und Excel-Berichte sowie die Elemente, die andere Benutzer für Sie freigegeben haben. Datasets sind alle Datenquellen, die Sie hochgeladen haben oder mit denen eine Verbindung hergestellt wurde. Zu diesen Datenquellen zählen die Dateien in Power BI Desktop und die von Ihnen verwendeten Excel-Arbeitsmappen. Folgende Elemente sind ebenfalls in der Datenkapazität enthalten:

* Excel-Bereiche, die an Dashboards angeheftet sind.
* Lokale Reporting Services-Visualisierungen, die an Power BI-Dashboards angeheftet sind.
* Hochgeladene Bilder.

Die Größe des freigegebenen Dashboards hängt von den angehefteten Elementen ab. Wenn Sie beispielsweise Elemente aus zwei Berichten anheften, die auf zwei verschiedenen Datasets basieren, wird die Größe von beiden Datasets bestimmt.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Verwalten Ihrer eigenen Elemente

Prüfen Sie den in Ihrem Power BI-Konto genutzten Datenspeicher, und verwalten Sie das Konto.

1. Wechseln Sie im Navigationsbereich zu **Mein Arbeitsbereich**, um den eigenen Speicher zu verwalten.
   
    ![Mein Arbeitsbereich](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Wählen Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in der rechten oberen Ecke \> **Persönlichen Speicher verwalten** aus.
   
    Die obere Leiste zeigt, wie viel Ihres Speicherlimits Sie verwendet haben.
   
    ![Speicherbegrenzung verwalten](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Die Datasets und Berichte werden auf zwei Registerkarten unterteilt:
   
    **In meinem Besitz:** Sie haben diese Berichte und Datasets in Ihr Power BI-Konto hochgeladen, darunter Dienstdatasets wie Salesforce und Dynamics CRM.  
    **Im Besitz anderer Benutzer:** Andere Benutzer haben diese Berichte und Datasets für Sie freigegeben.
1. Wählen Sie das Papierkorbsymbol aus, um ein Dataset oder einen Bericht zu löschen ![Papierkorbsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Bedenken Sie, dass Sie oder andere Benutzer über Berichte und Dashboards verfügen können, die auf einem Dataset basieren. Wenn Sie das Dataset löschen, funktionieren diese Berichte und Dashboards nicht mehr.

## <a name="manage-your-workspace"></a>Verwalten Ihres Arbeitsbereichs
1. Wählen Sie den Pfeil neben **Arbeitsbereiche** \> und den Namen des Arbeitsbereichs aus.
   
    ![Einen Arbeitsbereich auswählen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Wählen Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in der rechten oberen Ecke \> **Gruppenspeicher verwalten** aus.
   
    Die obere Leiste zeigt, wie viel des Speicherlimits der Gruppe verwendet wurde.
   
    ![Den Speicher des Arbeitsbereichs verwalten](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Die Datasets und Berichte werden auf zwei Registerkarten unterteilt:
   
    **In unserem Besitz:** Sie oder ein anderer Benutzer haben diese Berichte und Datasets in das Power BI-Konto der Gruppe hochgeladen, darunter Dienstdatasets wie Salesforce und Dynamics CRM.
    **Im Besitz anderer Benutzer:** Andere Benutzer haben diese Berichte und Datasets für Ihre Gruppe freigegeben.
3. Wählen Sie das Papierkorbsymbol aus, um ein Dataset oder einen Bericht zu löschen ![Papierkorbsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Jedes Mitglied eines Arbeitsbereichs, das über Bearbeitungsberechtigungen verfügt, ist zum Löschen von Datasets und Berichten im Arbeitsbereich berechtigt.
   > 
   > 

Bedenken Sie, dass Sie oder andere Benutzer in der Gruppe über Berichte und Dashboards verfügen können, die auf einem Dataset basieren. Wenn Sie das Dataset löschen, funktionieren diese Berichte und Dashboards nicht mehr.

## <a name="dataset-limits"></a>Dataset-Beschränkungen
Es besteht eine Beschränkung von 1 GB pro Dataset, das in Power BI importiert wird. Wenn Sie sich für die Excel-Benutzeroberfläche entschieden haben, anstatt die Daten zu importieren, beträgt die Obergrenze für das Dataset 250 MB.

## <a name="what-happens-when-you-reach-a-limit"></a>Was geschieht, wenn Sie einen Grenzwert erreichen?
Wenn Sie den Grenzwert der Datenkapazität erreichen, werden entsprechende Hinweise des Diensts angezeigt. 

Wenn Sie das Zahnradsymbol ![Zahnradsymbol](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)auswählen, sehen Sie einen roten Balken, der angibt, dass Sie Ihren Grenzwert der Datenkapazität überschritten haben.

![Speicherlimit wurde erreicht](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Dieser Grenzwert wird auch unter **Persönlichen Speicher verwalten** angezeigt.

 ![Verwalten des persönlichen Speichers, Speicherbegrenzung erreicht](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Wenn Sie versuchen, eine Aktion auszuführen, bei der einer der Grenzwerte erreicht wird, wird Ihnen eine entsprechende Meldung angezeigt. Sie können Ihren Speicher [verwalten](#manage), um die Speichermenge zu verringern und den Grenzwert zu unterschreiten.

 ![Ihr Speicherlimit wurde überschritten](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)

