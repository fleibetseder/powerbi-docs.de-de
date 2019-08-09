---
title: Bring Your Own Key für Verschlüsselungsschlüssel in Power BI (Vorschauversion)
description: Erfahren Sie, wie Sie Ihre eigenen Verschlüsselungsschlüssel in Power BI Premium verwenden können.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2019
LocalizationGroup: Premium
ms.openlocfilehash: d1a057f56237a0609f3330d4728c7dfcded84a71
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391122"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Bring Your Own Key für Verschlüsselungsschlüssel in Power BI (Vorschauversion)

Power BI verschlüsselt sowohl _ruhende Daten_ als auch _Daten während der Übertragung_. Standardmäßig verwendet Power BI von Microsoft verwaltete Schlüssel zur Verschlüsselung Ihrer Daten. Sie können in Power BI Premium auch Ihre eigenen Schlüssel für ruhende Daten verwenden, die in ein Dataset importiert werden. Weitere Informationen finden Sie weiter unten unter [Was bei Datenquellen und Speicher zu beachten ist](#data-source-and-storage-considerations). Dieser Ansatz wird als _Bring Your Own Key_ (BYOK) bezeichnet.

## <a name="why-use-byok"></a>Was sind die Vorteile von BYOK?

Durch BYOK können Complianceanforderungen leichter erfüllt werden, in denen Schlüsselvereinbarungen mit dem Cloud-Dienstanbieter (in diesem Fall Microsoft) getroffen werden. Mit BYOK stellen Sie die Verschlüsselungsschlüssel für Ihre ruhenden Power BI-Daten auf Anwendungsebene selbst bereit und können diese verwalten. Deshalb haben Sie die volle Kontrolle und können die Schlüssel Ihrer Organisation widerrufen, wenn Sie sich dazu entscheiden, den Dienst zu verlassen. Durch den Widerruf der Schlüssel kann der Dienst die Daten nicht mehr lesen.

## <a name="data-source-and-storage-considerations"></a>Was bei Datenquellen und Speicher zu beachten ist

Wenn Sie BYOK verwenden möchten, müssen Sie Daten aus einer PBIX-Datei (Power BI Desktop) in den Power BI-Dienst hochladen. Sie können BYOK nicht in den folgenden Szenarios verwenden:

- Analysis Services-Liveverbindungen
- Excel-Arbeitsmappen (es sei denn, die Daten werden zuerst in Power BI Desktop importiert)
- Pushdatasets

BYOK gilt nur für das der PBIX-Datei zugeordnete Dataset und nicht für die Abfrageergebniscaches für Kacheln und Visuals.

## <a name="configure-azure-key-vault"></a>Konfigurieren des Azure Key Vault

In diesem Abschnitt erfahren Sie, wie der Azure Key Vault, ein Tool zum sicheren Speichern von und Zugreifen auf Geheimnisse, z. B. Verschlüsselungsschlüssel, konfiguriert wird. Sie können einen vorhandenen Schlüsseltresor verwenden, um Ihre Verschlüsselungsschlüssel zu speichern, oder Sie können einen neuen speziell für Power BI erstellen.

Die Anweisungen in diesem Abschnitt setzen grundlegende Kenntnisse des Azure Key Vault voraus. Weitere Informationen finden Sie unter [What is Azure Key Vault? (Was ist der Azure Key Vault?)](/azure/key-vault/key-vault-whatis). Sie können Ihren Schlüsseltresor folgendermaßen konfigurieren:

1. Fügen Sie den Power BI-Dienst als Dienstprinzipal für den Schlüsseltresor mit Berechtigungen zum Packen und Entpacken hinzu.

1. Erstellen sie einen RSA-Schlüssel mit einer Länge von 4096 Bit (oder verwenden Sie einen vorhandenen Schlüssel dieses Typs) mit Berechtigungen zum Packen und Entpacken.

    > [!IMPORTANT]
    > Power BI BYOK unterstützt nur RSA-Schlüssel mit einer Länge von 4096 Bit.

1. Empfohlen: Achten Sie darauf, dass die Option _Vorläufiges Löschen_ für den Schlüsseltresor aktiviert ist.

### <a name="add-the-service-principal"></a>Hinzufügen des Dienstprinzipals

1. Klicken Sie im Azure-Portal in Ihrem Schlüsseltresor unter **Access policies** (Zugriffsrichtlinien) auf **Add New** (Neue hinzufügen).

1. Suchen Sie unter **Select principal** (Prinzipal auswählen) nach Microsoft.Azure.AnalysisServices, und wählen Sie dieses aus.

    > [!NOTE]
    > Wenn Sie „Microsoft. Azure.AnalysisServices“ nicht finden können, ist wahrscheinlich dem Azure-Abonnement, das Ihrem Azure Key Vault zugeordnet ist, nie eine Power BI-Ressource zugeordnet worden. Suchen Sie stattdessen nach der folgenden Zeichenfolge: 00000009-0000-0000-c000-000000000000.

1. Aktivieren Sie unter **Key permissions** (Schlüsselberechtigungen) **Unwrap key** (Schlüssel entpacken) und **Wrap key** (Schlüssel packen).

    ![PBIX-Dateikomponenten](media/service-encryption-byok/service-principal.png)

1. Klicken Sie auf **OK** und anschließend auf **Speichern**.

### <a name="create-an-rsa-key"></a>Erstellen eines RSA-Schlüssels

1. Wählen Sie in Ihrem Schlüsseltresor unter **Schlüssel** **Generate/Import** (Generieren/Importieren) aus.

1. Wählen Sie RSA als **Schlüsseltyp** aus, und geben Sie 4096 als **Größe des RSA-Schlüssels** an.

    ![PBIX-Dateikomponenten](media/service-encryption-byok/create-rsa-key.png)

1. Wählen Sie **Erstellen** aus.

1. Wählen Sie unter **Schlüssel** den Schlüssel aus, den Sie erstellt haben.

1. Wählen Sie die GUID für die **aktuelle Version** des Schlüssel aus.

1. Achten Sie darauf, dass **Schlüssel packen** und **Schlüssel entpacken** aktiviert sind. Kopieren Sie den **Key Identifier** (Schlüsselbezeichner), den Sie bei der Aktivierung von BYOK in Power BI benötigen.

    ![PBIX-Dateikomponenten](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>Die Option zum vorläufigen Löschen

Es wird empfohlen, dass Sie die Option [soft-delete](/azure/key-vault/key-vault-ovw-soft-delete) in Ihrem Schlüsseltresor aktivieren, um Datenverluste zu vermeiden, wenn Schlüssel oder Schlüsseltresore versehentlich gelöscht werden. Sie müssen [PowerShell](/azure/key-vault/key-vault-soft-delete-powershell) in Ihrem Schlüsseltresor verwenden, um die Eigenschaft „soft-delete“ zu aktivieren, da diese Option noch nicht über das Azure-Portal verfügbar ist.

Wenn der Azure Key Vault ordnungsgemäß konfiguriert wurde, können Sie BYOK für Ihren Mandanten aktivieren.

## <a name="enable-byok-on-your-tenant"></a>Aktivieren von BYOK in Ihrem Mandanten

Sie können BYOK mit [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin) auf Mandantenebene aktivieren, indem Sie zunächst die Verschlüsselungsschlüssel in Ihrem Power BI-Mandanten hinzufügen, die Sie erstellt und im Azure Key Vault gespeichert haben. Anschließend weisen Sie diese Verschlüsselungsschlüssel je einer Premium-Kapazität zu, um den Inhalt in dieser Kapazität zu verschlüsseln.

### <a name="important-considerations"></a>Wichtige Hinweise

Beachten Sie folgende Punkte, bevor Sie BYOK aktivieren:

- Momentan können Sie BYOK nicht mehr deaktivieren, sobald Sie es einmal aktiviert haben. Je nachdem, wie Sie Parameter für `Add-PowerBIEncryptionKey` angeben, können Sie bestimmen, wie Sie BYOK für eine oder mehrere Kapazitäten verwenden. Sie können hinzugefügte Schlüssel nicht mehr aus Ihrem Mandanten entfernen. Weitere Informationen finden Sie weiter unten unter [Aktivieren von BYOK](#enable-byok).

- Sie können Arbeitsbereiche, die BYOK verwenden, nicht _direkt_ von einer dedizierten Kapazität in Power BI Premium in eine gemeinsam genutzte Kapazität verschieben. Dazu müssen Sie zunächst den betreffenden Arbeitsbereich in eine dedizierte Kapazität verschieben, in der BYOK nicht aktiviert ist.

### <a name="enable-byok"></a>Aktivieren von BYOK

Sie müssen Mandantenadministrator im Power BI-Dienst und mit dem Cmdlet `Connect-PowerBIServiceAccount` angemeldet sein, um BYOK aktivieren zu können. Verwenden Sie dann [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey), um BYOK zu aktivieren. Dies wird im folgenden Beispiel veranschaulicht:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Führen Sie `Add-PowerBIEncryptionKey` mit unterschiedlichen Werten für –`-Name` und `-KeyVaultKeyUri` aus, um mehrere Schlüssel hinzuzufügen. 

Das Cmdlet akzeptiert zwei Parameter, die sich auf die Verschlüsselung für vorhandene und zukünftige Kapazitäten auswirken. Standardmäßig ist keiner der Parameter festgelegt:

- `-Activate`: Gibt an, dass dieser Schlüssel für alle noch nicht verschlüsselten Kapazitäten im Mandanten verwendet wird.

- `-Default`: Gibt an, dass dieser Schlüssel jetzt der Standardschlüssel für den gesamten Mandanten ist. Wenn Sie eine neue Kapazität erstellen, erbt die Kapazität den Schlüssel.

> [!IMPORTANT]
> Wenn Sie `-Default` angeben, werden alle Kapazitäten, die nachfolgend in Ihrem Mandanten erstellt werden, mit dem angegebenen Schlüssel (oder dem neuen Standardschlüssel) verschlüsselt. Sie können den Standardvorgang nicht rückgängig machen und daher in Ihrem Mandanten keine Premium-Kapazität mehr erstellen, die nicht BYOK verwendet.

Verwenden Sie [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) zum Festlegen des Verschlüsselungsschlüssel für eine oder mehrere Power BI-Kapazitäten, nachdem Sie BYOK in Ihrem Mandanten aktiviert haben:

```powershell
Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
```

Sie können festlegen, wie BYOK in Ihrem Mandanten verwendet wird. Rufen Sie z. B. `Add-PowerBIEncryptionKey` ohne `-Activate` oder `-Default` auf, um eine einzelne Kapazität zu verschlüsseln. Rufen Sie anschließend `Set-PowerBICapacityEncryptionKey` für die Kapazität auf, in der Sie BYOK aktivieren möchten.

## <a name="manage-byok"></a>Verwalten von BYOK

Power BI stellt zusätzliche Cmdlets zum Verwalten von BYOK in Ihrem Mandanten zur Verfügung:

- Verwenden Sie [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity), um den Schlüssel abzurufen, der von einer Kapazität aktuell verwendet wird:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- Verwenden Sie [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey), um den Schlüssel abzurufen, den Ihr Mandant aktuell verwendet:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Verwenden Sie [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus), um zu überprüfen, ob die Datasets in einem Arbeitsbereich verschlüsselt sind und ob ihr Verschlüsselungsstatus mit dem Arbeitsbereich synchron ist:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Beachten Sie, dass die Verschlüsselung auf Kapazitätsebene aktiviert wird, Sie den Verschlüsselungsstatus aber auf Datasetebene für den angegebenen Arbeitsbereich abrufen.

- Verwenden Sie [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey), um die Version des Schlüssels, der für die Verschlüsselung verwendet wird, zu wechseln (oder zu _rotieren_). Das Cmdlet aktualisiert `-KeyVaultKeyUri` für `-Name` des Schlüssels:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```
