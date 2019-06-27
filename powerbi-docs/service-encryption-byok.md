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
ms.date: 06/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 7adcfeec771796aa9fe322512f8ca8584559cea0
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829386"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Bring Your Own Key für Verschlüsselungsschlüssel in Power BI (Vorschauversion)

Power BI verschlüsselt sowohl _ruhende Daten_ als auch _Daten während der Übertragung_. Standardmäßig verwendet Power BI von Microsoft verwaltete Schlüssel zur Verschlüsselung Ihrer Daten. Sie können in Power BI Premium auch Ihre eigenen Schlüssel für ruhende Daten verwenden, die in ein Dataset importiert werden. Weitere Informationen finden Sie weiter unten unter [Was bei Datenquellen und Speicher zu beachten ist](#data-source-and-storage-considerations). Dieser Ansatz wird als _Bring Your Own Key_ (BYOK) bezeichnet.

## <a name="why-use-byok"></a>Was sind die Vorteile von BYOK?

Durch BYOK können Complianceanforderungen leichter erfüllt werden, in denen Schlüsselvereinbarungen mit dem Cloud-Dienstanbieter (in diesem Fall Microsoft) getroffen werden. Mit BYOK stellen Sie die Verschlüsselungsschlüssel für Ihre ruhenden Power BI-Daten auf Anwendungsebene selbst bereit und können diese verwalten. Deshalb haben Sie die volle Kontrolle und können die Schlüssel Ihrer Organisation widerrufen, wenn Sie sich dazu entscheiden, den Dienst zu verlassen. Durch den Widerruf der Schlüssel kann der Dienst die Daten nicht mehr lesen.

## <a name="data-source-and-storage-considerations"></a>Was bei Datenquellen und Speicher zu beachten ist

Wenn Sie BYOK verwenden möchten, müssen Sie Daten aus einer PBIX-Datei (Power BI Desktop) in den Power BI-Dienst hochladen. Wenn Sie eine Verbindung mit den Datenquellen in Power BI Desktop herstellen, müssen Sie für den Import einen Speichermodus angeben. Sie können BYOK nicht in den folgenden Szenarios verwenden:

- DirectQuery
- Analysis Services-Liveverbindungen
- Excel-Arbeitsmappen (es sei denn, die Daten werden zuerst in Power BI Desktop importiert)
- Pushdatasets

Im nächsten Abschnitt erfahren Sie, wie Sie den Azure Key Vault konfigurieren. Dort speichern Sie Ihre Verschlüsselungsschlüssel für BYOK.

## <a name="configure-azure-key-vault"></a>Konfigurieren des Azure Key Vault

Der Azure Key Vault ist ein Tool zum sicheren Speichern von und Zugreifen auf Geheimnisse, z. B. Verschlüsselungsschlüssel. Sie können einen vorhandenen Schlüsseltresor verwenden, um Ihre Verschlüsselungsschlüssel zu speichern, oder Sie können einen neuen speziell für Power BI erstellen.

Die Anweisungen in diesem Abschnitt setzen grundlegende Kenntnisse des Azure Key Vault voraus. Weitere Informationen finden Sie unter [What is Azure Key Vault? (Was ist der Azure Key Vault?)](/azure/key-vault/key-vault-whatis). Sie können Ihren Schlüsseltresor folgendermaßen konfigurieren:

1. Fügen Sie den Power BI-Dienst als Dienstprinzipal für den Schlüsseltresor mit Berechtigungen zum Packen und Entpacken hinzu.

1. Erstellen sie einen RSA-Schlüssel mit einer Länge von 4096 Bit (oder verwenden Sie einen vorhandenen Schlüssel dieses Typs) mit Berechtigungen zum Packen und Entpacken.

1. Empfohlen: Achten Sie darauf, dass die Option _Vorläufiges Löschen_ für den Schlüsseltresor aktiviert ist.

### <a name="add-the-service-principal"></a>Hinzufügen des Dienstprinzipals

1. Klicken Sie im Azure-Portal in Ihrem Schlüsseltresor unter **Access policies** (Zugriffsrichtlinien) auf **Add New** (Neue hinzufügen).

1. Suchen Sie unter **Select principal** (Prinzipal auswählen) nach Microsoft.Azure.AnalysisServices, und wählen Sie dieses aus.

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

Sie können BYOK mit PowerShell auf Mandantenebene aktivieren, indem Sie zunächst die Verschlüsselungsschlüssel in Ihrem Power BI-Mandanten hinzufügen, die Sie erstellt und im Azure Key Vault gespeichert haben. Anschließend weisen Sie diese Verschlüsselungsschlüssel je einer Premium-Kapazität zu, um den Inhalt in dieser Kapazität zu verschlüsseln.

### <a name="important-considerations"></a>Wichtige Hinweise

Beachten Sie folgende Punkte, bevor Sie BYOK aktivieren:

- Momentan können Sie BYOK nicht mehr deaktivieren, sobald Sie es einmal aktiviert haben. Je nachdem, wie Sie Parameter für `Add-PowerBIEncryptionKey` angeben, können Sie bestimmen, wie Sie BYOK für eine oder mehrere Kapazitäten verwenden. Sie können hinzugefügte Schlüssel nicht mehr aus Ihrem Mandanten entfernen. Weitere Informationen finden Sie weiter unten unter [Aktivieren von BYOK](#enable-byok).

- Sie können Arbeitsbereiche, die BYOK verwenden, nicht _direkt_ von einer dedizierten Kapazität in Power BI Premium in eine gemeinsam genutzte Kapazität verschieben. Dazu müssen Sie zunächst den betreffenden Arbeitsbereich in eine dedizierte Kapazität verschieben, in der BYOK nicht aktiviert ist.

### <a name="enable-byok"></a>Aktivieren von BYOK

Sie müssen Mandantenadministrator im Power BI-Dienst und mit dem Cmdlet `Connect-PowerBIServiceAccount` angemeldet sein, um BYOK aktivieren zu können. Verwenden Sie dann `Add-PowerBIEncryptionKey`, um BYOK. Dies wird im folgenden Beispiel veranschaulicht:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Das Cmdlet akzeptiert drei Parameter, die sich auf die Verschlüsselung für vorhandene und zukünftige Kapazitäten auswirken. Standardmäßig ist keiner der Parameter festgelegt:

- `-Activate`: Gibt an, dass dieser Schlüssel für alle vorhandenen Kapazitäten im Mandanten verwendet wird.

- `-Default`: Gibt an, dass dieser Schlüssel jetzt der Standardschlüssel für den gesamten Mandanten ist. Wenn Sie eine neue Kapazität erstellen, erbt die Kapazität den Schlüssel.

- `-DefaultAndActivate`: Gibt an, dass dieser Schlüssel für alle vorhandenen Kapazitäten im Mandanten und alle neu erstellten Kapazitäten verwendet wird.

Wenn Sie `-Default` oder `-DefaultAndActivate` angeben, werden alle Kapazitäten, die nachfolgend in diesem Mandanten erstellt werden, mit dem angegebenen Schlüssel (oder dem neuen Standardschlüssel) verschlüsselt. Sie können den Standardvorgang nicht rückgängig machen. D. h., Sie können keine Premium-Kapazität in Ihrem Mandanten mehr erstellen, die nicht BYOK verwendet.

Sie können festlegen, wie BYOK in Ihrem Mandanten verwendet wird. Rufen Sie z. B. `Add-PowerBIEncryptionKey` ohne `-Activate`, `-Default` oder `-DefaultAndActivate` auf, um eine einzelne Kapazität zu verschlüsseln. Rufen Sie anschließend `Set-PowerBICapacityEncryptionKey` für die Kapazität auf, in der Sie BYOK aktivieren möchten.

## <a name="manage-byok"></a>Verwalten von BYOK

Power BI stellt zusätzliche Cmdlets zum Verwalten von BYOK in Ihrem Mandanten zur Verfügung:

- Verwenden Sie `Get-PowerBIEncryptionKey`, um den Schlüssel abzurufen, den Ihr Mandant aktuell verwendet:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Verwenden Sie `Get-PowerBIWorkspaceEncryptionStatus`, um zu überprüfen, ob die Datasets in einem Arbeitsbereich verschlüsselt sind und ob ihr Verschlüsselungsstatus mit dem Arbeitsbereich synchron ist:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Beachten Sie, dass die Verschlüsselung auf Kapazitätsebene aktiviert wird, Sie den Verschlüsselungsstatus aber auf Datasetebene für den angegebenen Arbeitsbereich abrufen.

- Verwenden Sie `Set-PowerBICapacityEncryptionKey`, um den Verschlüsselungsschlüssel für die Power BI-Kapazität zu aktualisieren:

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
    ```

- Verwenden Sie `Use Switch-PowerBIEncryptionKey`, um den aktuell verwendeten Verschlüsselungsschlüssel zu wechseln (oder zu _rotieren_). Das Cmdlet aktualisiert `-KeyVaultKeyUri` für `-Name` des Schlüssels:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```