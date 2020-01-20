---
title: Programmgesteuertes Konfigurieren von Anmeldeinformationen für Power BI
description: Anleitung zum programmgesteuerten Konfigurieren von Power BI-Anmeldeinformationen für die Automatisierung
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836595"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Programmgesteuertes Konfigurieren von Anmeldeinformationen für Power BI

Folgen Sie diesen Schritten, um Anmeldeinformationen für Power BI programmgesteuert zu konfigurieren.

## <a name="configure-a-credential-flow-for-data-sources"></a>Konfigurieren eines Anmeldeinformationsflows für Datenquellen

1. Rufen Sie [Datenquellen aufrufen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) auf, um die Datenquellen des Datasets anzeigen zu lassen. Im Antworttext für jede Datenquelle sind Typ, Verbindungsdetails, Gateway und Datenquellen-ID angegeben.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Erstellen Sie je nach Anmeldeinformationstyp eine Anmeldeinformationenzeichenfolge gemäß der [Datenquellenupdatebeispiele](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource).

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Erstellen Sie die Details zu Anmeldeinformationen.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Rufen Sie [Datenquelle aktualisieren](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) auf, um Anmeldeinformationen mithilfe des Gateways und der Datenquellen-ID aus Schritt 1 und mit den Details zu Anmeldeinformationen aus Schritt 4 festzulegen.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Abgelaufener lokaler Datenquellen-Anmeldeinformationsflow

1. [Befolgen Sie die Schritte 1 und 2 aus dem vorherigen Szenario.](#configure-a-credential-flow-for-data-sources)

2. Rufen Sie [Gateway abrufen](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) auf, um den öffentlichen Gateway-Schlüssel abzurufen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Verschlüsseln Sie die Anmeldeinformationenzeichenfolge mit dem öffentlichen Gateway-Schlüssel. Verschiedene Gatewayversionen können unterschiedliche Größen für den öffentlichen Schlüssel aufweisen.
    
    Weitere Informationen finden Sie im Beispiel im SDK-Code, der im PowerBI-CSharp GitHub-Repository verfügbar ist, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Erstellen Sie mit den verschlüsselten Anmeldeinformationen Details zu Anmeldeinformationen.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Rufen Sie [Datenquelle aktualisieren](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) auf, um Anmeldeinformationen festzulegen.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Konfigurieren einer neuen Datenquelle für ein Datengateway

1. Installieren Sie das [lokale Datengateway](https://powerbi.microsoft.com/gateway/) auf Ihrem Computer.

2. Rufen Sie [Gateway abrufen](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) auf, um die Gateway-ID und den öffentlichen Schlüssel abzurufen.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Erstellen Sie wie im vorherigen Szenario Details zu Anmeldeinformationen mithilfe des öffentlichen Gateway-Schlüssels, den Sie im Schritt [Abgelaufener lokaler Datenquellen-Anmeldeinformationsflow](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway) abgerufen haben.

4. Erstellen Sie den Anforderungstext.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. Rufen Sie die [API zum Erstellen von Datenquellen](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) auf.

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>Problembehandlung

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>No gateway and data source ID found when calling get data sources (Beim Aufrufen von „Get Datasource“ wurde keine Gateway- und Datenquellen-ID gefunden)

Dieser Fehler bedeutet, dass das Dataset nicht an ein Gateway gebunden ist. Bei der Erstellung eines neuen Datasets wird auf dem Cloudgateway des Benutzers für jede Cloudverbindung automatisch eine Datenquelle ohne Anmeldeinformationen erstellt. Dieses Gateway wird verwendet, um die Anmeldeinformationen für Cloudverbindungen zu speichern.

Nachdem Sie das Dataset erstellt haben, wird eine automatische Bindung zwischen dem Dataset und einem passenden Gateway hergestellt, die übereinstimmende Datenquellen für alle Verbindungen enthält. Wenn es kein solches Gateway oder mehrere passende Gateways gibt, schlägt die automatische Bindung fehl.

Erstellen Sie – sofern vorhanden – die fehlenden lokalen Datenquellen, und binden Sie das Dataset manuell an ein Gateway, indem Sie [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (An Gateway binden) verwenden.

Wenn Sie Gateways anzeigen lassen möchten, die gebunden werden könnten, verwenden Sie [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Gateways anzeigen).