---
title: Erstellen eines SSL-Zertifikats
description: Problemumgehung zum manuellen Erstellen von Zertifikaten für den Entwicklerserver
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425434"
---
# <a name="creating-ssl-certificate"></a>Erstellen eines SSL-Zertifikats

Führen Sie den folgenden Befehl aus, um das Zertifikat mit dem PowerShell-Cmdlet „New-SelfSignedCertificate“ unter Windows 8 oder höher zu generieren.

Das Tool erfordert die Installation von OpenSSL für **Windows** **7**. Das Hilfsprogramm `openssll` muss über die Befehlszeile verfügbar sein.

Zum Installieren von OpenSSL besuchen Sie [https://www.openssl.org](https://www.openssl.org) oder [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries).

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Erstellen eines Zertifikats (Mac OS X)

Normalerweise sind OpenSSL-Hilfsprogramme in Linux- oder Mac OS X-Betriebssystemen verfügbar.

Andernfalls können Sie diese über

den *Brew*-Paket-Manager

```cmd
brew install openssl
brew link openssl --force
```

oder mithilfe von *MacPorts* installieren.

```cmd
sudo port install openssl
```

Nach der Installation von OpenSSL rufen Sie Folgendes auf, um ein neues Zertifikat zu generieren:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Erstellen eines Zertifikats (Linux)

Falls keine OpenSSL-Hilfsprogramme in Ihrem Linux-Betriebssystem verfügbar sind, können Sie die Installation mit den folgenden Befehlen ausführen.

*APT*-Paket-Manager:

```cmd
sudo apt-get install openssl
```

*Yellowdog Updater*:

```cmd
yum install openssl
```

*Redhat*-Paket-Manager:

```cmd
rpm install openssl
```

Wenn OpenSSL bereits im Betriebssystem verfügbar ist, rufen Sie

```cmd
pbiviz --create-cert
```

auf, um ein neues Zertifikat zu generieren.

Alternativ können Sie eins von [https://www.openssl.org](https://www.openssl.org) oder [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) abrufen.

## <a name="generate-certificate-manually"></a>Manuelles Generieren eines Zertifikats

Sie können Zertifikate angeben, die von beliebigen Tools generiert wurden.

Wenn OpenSSL im System installiert ist, können Sie den folgenden Befehl ausführen, um ein neues Zertifikat zu generieren:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

In der Regel befinden sich PowerBI-visuals-tools-Webserverzertifikate unter

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

für die globale Instanz der Tools

oder

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

für die lokale Instanz der Tools.

Speichern Sie die Zertifikatdatei unter `PowerBICustomVisualTest_public.cer` und den privaten Schlüssel unter `PowerBICustomVisualTest_public.key`, wenn Sie das PEM-Format verwenden.
Speichern Sie die Zertifikatdatei unter `PowerBICustomVisualTest_public.pfx`, wenn Sie das PFX-Format verwenden.

Wenn die PFX-Zertifikatdatei eine Passphrase erfordert, müssen Sie diese in

```cmd
\PowerBI-visuals-tools\config.json
```

im server-Abschnitt angeben:

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
