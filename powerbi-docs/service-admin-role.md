---
title: Grundlegendes zur Power BI-Administratorrolle
description: Dieser Artikel beschreibt die Rolle des Power BI-Dienstadministrators und wie Sie diese in Ihrer Organisation verwenden können.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a6121ca16250de9765557b9c9acbf73b513723ee
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699910"
---
# <a name="understanding-the-power-bi-service-administrator-role"></a>Grundlegendes zur Rolle „Power BI-Dienstadministrator“

Erfahren Sie, wie Sie Rolle des Power BI-Dienstadministrators in Ihrer Organisation verwenden können. Benutzer mit dieser Rolle verfügen über vollständige Kontrolle über einen Power BI-Mandanten und die zugehörigen Verwaltungsfunktionen – mit Ausnahme der Lizenzierung.

Die Rolle des Power BI-Dienstadministrators kann Benutzern zugewiesen werden, die Zugriff auf das Power BI-Verwaltungsportal benötigen, ohne dass diesen Benutzern auch vollständiger Administratorzugriff auf Office 365 gewährt wird.

Administratoren für die Office 365-Benutzerverwaltung weisen Benutzern im Microsoft 365 Admin Center oder mithilfe eines PowerShell-Skripts die Rolle des Power BI-Dienstadministrators zu. Sobald ein Benutzer zugewiesen wurde, erhält er Zugriff auf das [Power BI-Verwaltungsportal](service-admin-portal.md). Dort kann der Benutzer auf Nutzungsmetriken des Mandanten zugreifen und die Verwendung von Power BI-Funktionen im Mandanten steuern.

## <a name="limitations-and-considerations"></a>Einschränkungen und Überlegungen

Die Rolle „Power BI-Dienstadministrator“ bietet keine Berechtigungen für die folgenden Aktivitäten:

* Ändern von Benutzern und Lizenzen im Microsoft 365 Admin Center

* Zugreifen auf die Überwachungsprotokolle. Weitere Informationen finden Sie unter [Verwenden von Überwachung in der Organisation](service-admin-auditing.md).

## <a name="assign-users-to-the-admin-role-in-office-365"></a>Zuweisen von Benutzern zur Administratorrolle in Office 365

Führen Sie folgende Schritte aus, um Benutzern im Microsoft 365 Admin Center die Rolle des Power BI-Dienstadministrators zuzuweisen.

1. Rufen Sie im [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage) **Benutzer** > **Aktive Benutzer** auf.

    ![Microsoft 365 Admin Center](media/service-admin-role/powerbi-admin-users.png)

1. Wählen Sie den Benutzer aus, dem Sie die Rolle zuweisen möchten.

1. Klicken Sie unter **Rollen** auf **Bearbeiten**.

    ![Bearbeiten von Rollen](media/service-admin-role/powerbi-admin-edit-roles.png)

1. Wählen Sie **Benutzerdefinierter Administrator** > **Power BI-Dienstadministrator**.

    ![Power BI-Dienstadministrator](media/service-admin-role/powerbi-admin-role.png)

1. Klicken Sie auf **Speichern** und dann auf **Schließen**.

Daraufhin sollte für den Benutzer **Power BI-Dienstadministrator** als Rolle aufgeführt werden.

![Rollen](media/service-admin-role/powerbi-admin-role-set.png)

## <a name="assign-users-to-the-admin-role-with-powershell"></a>Zuweisen von Benutzern zur Administratorrolle mit PowerShell

Sie können auch PowerShell verwenden, um Benutzer zu Rollen zuzuweisen. Benutzer werden in Azure Active Directory (Azure AD) verwaltet. Wenn Sie noch nicht über das Azure AD-PowerShell-Modul verfügen, [laden Sie die neueste Version herunter, und installieren Sie sie](https://www.powershellgallery.com/packages/AzureAD/).

1. Stellen Sie zunächst eine Verbindung mit Azure AD her:
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. Rufen Sie dann die **ObjectId** für die Rolle **Power BI-Dienstadministrator** ab. Sie können den Befehl [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) ausführen, um die **ObjectId** abzurufen.

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    In diesem Fall lautet die **ObjectId** der Rolle „00f79122-c45d-436d-8d4a-2c0c6ca246bf“.

1. Rufen Sie als Nächstes die **ObjectId** des Benutzers ab. Diese können Sie mit dem Befehl [Get-AzureADUser](/powershell/module/azuread/get-azureaduser) ermitteln.

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. Um das Mitglied der Rolle zuzuweisen, führen Sie den Befehl [Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember) aus.

    | Parameter | Beschreibung |
    | --- | --- |
    | ObjectId |Die ObjectId der Rolle |
    | RefObjectId |Die ObjectId des Mitglieds. |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```

## <a name="next-steps"></a>Nächste Schritte

[Verwalten von Power BI in Ihrer Organisation](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI-Verwaltungsportal](service-admin-portal.md)  

Weitere Fragen? [Stellen Sie Ihre Frage in der Power BI-Community.](https://community.powerbi.com/)