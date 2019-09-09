---
title: PowerShell-Cmdlets, REST-APIs und das .NET SDK für Administratoren
description: Erfahren Sie, wie Sie Power BI mit Skripts und durch das Programmieren von APIs verwalten können.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: da19eaffff7abfd8edd745cdb58c008ea40eee8a
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70751504"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-Cmdlets, REST-APIs und das .NET SDK für die Power BI-Verwaltung
Mit Power BI können Administratoren für häufige Tasks mit PowerShell-Cmdlets Skripts erstellen. Außerdem stellt es REST-APIs zur Verfügung und bietet ein .NET SDK zum Entwickeln von Verwaltungslösungen. In diesem Thema finden Sie eine Liste von Cmdlets und dazugehörigen SDK-Methoden und REST-API-Endpunkten. Weitere Informationen finden Sie unter:

- [PowerShell-Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) und [PowerShell-Dokumentation](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- [REST-API-Dokumentation](https://docs.microsoft.com/rest/api/power-bi/admin)
- [.NET SDK-Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> Die nachstehenden Cmdlets müssen mit `-Scope Organization` aufgerufen werden, damit sie für den Mandanten für die Verwaltung ausgeführt werden.

| **Name des Cmdlet** | **Aliase** | **SDK-Methode** | **REST-API-Endpunkt** | **Beschreibung** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/V | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Ruft die Datenquellen eines angegebenen Datasets ab |
| `Get-PowerBIDataset` | N/V | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Ruft die Liste aller Datasets im Power BI-Mandanten ab |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Ruft die Liste aller Arbeitsbereiche im Power BI-Mandanten ab |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Fügt einen Benutzer einem angegeben Arbeitsbereich als Mitglied hinzu |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Entfernt die Mitgliedschaft eines Benutzers aus einem angegebenen Arbeitsbereich |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Stellt einen gelöschten Arbeitsbereich wieder her |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Aktualisiert die Eigenschaften eines angegebenen Arbeitsbereichs |
| `Get-PowerBIDataset -WorkspaceId` | N/V | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Ruft die Datasets in einem Arbeitsbereich ab |
| `Get-PowerBIReport` | N/V | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Ruft die Liste aller Berichte im Power BI-Mandanten ab |
| `Get-PowerBIDashboard` | N/V | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Ruft die Liste aller Dashboard im Power BI-Mandanten ab |
| `Get-PowerBIDashboard -WorkspaceId` | N/V | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Ruft die Dashboards in einem angegebenen Arbeitsbereich ab |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Ruft die Kacheln eines angegebenen Dashboards ab |
| `Get-PowerBIReport` | N/V | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Ruft die Berichte in einem angegebenen Arbeitsbereich ab |
| `Get-PowerBIImport` | N/V | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Ruft die Liste aller Importe im Power BI-Mandanten ab |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/V | N/V | Anmelden bei Power BI und Starten einer Sitzung |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/V | N/V | Abmelden von Power BI und Beenden der laufenden Sitzung |
| `Invoke-PowerBIRestMethod`| N/V | N/V | N/V | Senden willkürlicher REST-API-Aufrufe an Power BI |
| `Get-PowerBIAccessToken`| N/V | N/V | N/V | Abrufen des Power BI-Zugriffschlüssels in einer Sitzung |
| `Resolve-PowerBIError`| N/V | N/V | N/V | Abrufen ausführlicher Fehlerinformationen zu Cmdlet-Aufrufen, die mit einem Fehler abgeschlossen wurden |
