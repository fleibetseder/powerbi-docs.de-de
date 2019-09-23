---
title: Herstellen einer Verbindung mit einer Impala-Datenbank in Power BI Desktop
description: Einfaches Verbinden mit und Verwenden von einer Impala-Datenbank in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0befceba2651ad4f8f414d3669c5830c07ece06d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514192"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Herstellen einer Verbindung mit einer Impala-Datenbank in Power BI Desktop
In Power BI Desktop können Sie eine Verbindung mit einer **Impala**-Datenbank herstellen und die zugrunde liegenden Daten wie alle anderen Datenquellen in Power BI Desktop verwenden.

## <a name="connect-to-an-impala-database"></a>Herstellen einer Verbindung mit einer Impala-Datenbank
So stellen Sie eine Verbindung zu einer **Impala**-Datenbank her 

1. Wählen Sie in Power BI Desktop im Menüband **Start** die Option **Daten abrufen** aus. 

2. Wählen Sie in den Kategorien auf der linken Seite **Datenbank** aus. Daraufhin wird **Impala** angezeigt.

    ![Daten abrufen](media/desktop-connect-impala/connect_impala_2.png)

3. Geben oder fügen Sie in das angezeigte Fenster **Impala** den Namen des Impala-Servers ein. Wählen Sie dann **OK** aus. Sie können Daten direkt in Power BI **Importieren** oder **DirectQuery** verwenden. Weitere Informationen finden Sie unter [Verwendung von DirectQuery](desktop-use-directquery.md).

    ![Impala-Fenster](media/desktop-connect-impala/connect_impala_3a.png)

4. Wenn Sie dazu aufgefordert werden, geben Sie Ihre Anmeldeinformationen ein, oder stellen Sie anonym eine Verbindung her. Der Impala-Connector unterstützt die anonyme, Standard- (Benutzername + Kennwort) und Windows-Authentifizierung.

    ![Impala-Connector](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > Wenn Sie Ihren Benutzernamen und Ihr Kennwort für einen bestimmten **Impala**-Server einfügen, verwendet Power BI Desktop für darauffolgende Verbindungen die gleichen Anmeldeinformationen. Sie können diese Anmeldeinformationen unter **Datei > Optionen und Einstellungen > Datenquelleneinstellungen** ändern.


5. Nach dem Verbinden wird das Fenster **Navigator** angezeigt, in dem Sie die Daten sehen, die auf dem Server verfügbar sind. Wählen Sie aus diesen Daten die Elemente aus, die Sie in **Power BI Desktop** importieren und verwenden möchten.

    ![Navigator-Fenster](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Überlegungen und Einschränkungen
Beachten Sie Folgendes für den **Impala**-Connector:

* Der Impala-Connector wird auf dem lokalen Datengateway mit einem der drei unterstützten Authentifizierungsmechanismen unterstützt.

## <a name="next-steps"></a>Nächste Schritte
Es gibt viele verschiedene Datenquellen, mit denen Sie über Power BI Desktop eine Verbindung herstellen können. Weitere Informationen zu Datenquellen finden Sie in den folgenden Ressourcen:

* [Was ist Power BI Desktop?](desktop-what-is-desktop.md)
* [Datenquellen in Power BI Desktop](desktop-data-sources.md)
* [Strukturieren und Kombinieren von Daten mit Power BI Desktop](desktop-shape-and-combine-data.md)
* [Verbinden mit Excel in Power BI Desktop](desktop-connect-excel.md)   
* [Eingeben von Daten direkt in Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

