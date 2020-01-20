---
title: Verschlüsseln von Anmeldeinformationen
description: 'Exemplarische Vorgehensweise: Verschlüsseln von Anmeldeinformationen für lokale Gateway-Datenquellen'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836624"
---
# <a name="encrypt-credentials"></a>Verschlüsseln von Anmeldeinformationen

Wenn Sie [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Datenquelle erstellen) oder [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Datenquelle aktualisieren) in einem **lokalen Unternehmensgateway** mit der [Power BI-REST-API](https://docs.microsoft.com/rest/api/power-bi/) aufrufen, müssen die Werte für die Anmeldeinformationen mithilfe des öffentlichen Schlüssels des Gateways verschlüsselt werden.

Im folgenden Codebeispiel wird gezeigt, wie die Anmeldeinformationen in .NET verschlüsselt werden.

Anmeldeinformationen, die an die EncodeCredentials-Methode übergeben werden, sollten je nach Anmeldeinformationstyp eines der folgenden Formate aufweisen:

**Einfache/Windows-Anmeldeinformationen**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Wichtige Anmeldeinformationen**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2-Anmeldeinformationen**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Anonyme Anmeldeinformationen**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Verschlüsseln von Anmeldeinformationen**

Verschlüsseln Sie den Wert der Anmeldeinformationen mit dem öffentlichen Schlüssel des Gateways. Verschiedene Gatewayversionen können unterschiedliche Größen für den öffentlichen Schlüssel aufweisen.

Weitere Informationen finden Sie im Beispiel im SDK-Code, der im PowerBI-CSharp GitHub-Repository verfügbar ist, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)