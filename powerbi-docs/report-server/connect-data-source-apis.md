---
title: Ändern der Datenquellen-Verbindungszeichenfolgen mit PowerShell
description: Ändern von Datenquellen-Verbindungszeichenfolgen mithilfe von APIs in PowerShell – Power BI-Berichtsserver.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2019
ms.author: maggies
ms.openlocfilehash: 5cdf29c71ef3e5f8dc02799945cf76ccc518dabe
ms.sourcegitcommit: df8bcc65f0df69bf1fc1d47eb06575742eac1622
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "75953746"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Ändern von Datenquellen-Verbindungszeichenfolgen in Power BI-Berichten mithilfe von PowerShell – Power BI-Berichtsserver.


Sie können Datenquellen-Verbindungszeichenfolgen in Power BI-Berichten auf Power BI-Berichtsservern mithilfe von APIs in PowerShell verwenden. 

> [!NOTE]
> Derzeit kann diese Funktion nur für DirectQuery verwendet werden. Unterstützung für den Import und die Datenaktualisierung ist geplant.

1. Installieren Sie die PowerShell-Cmdlets des Power BI-Berichtsservers. Die Cmdlets und Installationsanweisungen finden Sie unter [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

2. Rufen Sie die vorhandenen Datenquelleninformationen für die Power BI-Datei über die PowerShell-Commandlets ab:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    So zeigen Sie Informationen für die erste im Power BI-Bericht enthaltene Datenquelle an: 

    ```powershell
    $dataSources[0]
    ```

3. Aktualisieren Sie die Verbindungs- und Anmeldeinformationen nach Bedarf. Wenn Sie die Verbindungszeichenfolge aktualisieren und die Datenquelle verwendet gespeicherte Anmeldeinformationen, müssen Sie das Kontokennwort angeben. 

    So aktualisieren Sie eine Datenquellen-Verbindungszeichenfolge:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    So ändern Sie den Typ der Datenquellen-Anmeldeinformationen:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    So ändern Sie den Benutzernamen/das Kennwort für die Datenquelle:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Speichern Sie die aktualisierten Anmeldeinformationen wieder auf dem Server.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen für paginierte Berichte auf dem Power BI-Berichtsserver](connect-data-sources.md) 

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)
