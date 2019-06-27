---
ms.openlocfilehash: e24218e2a465619fdfbfc279d3cc45370202dd6e
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66814778"
---
## <a name="sign-in-account"></a>Das Anmeldekonto

Benutzer melden sich mit einem Geschäfts-, Schul- oder Unikonto an. Dieses Konto ist Ihr **Organisationskonto**. Wenn Sie sich für ein Office 365-Angebot registriert haben und nicht Ihre tatsächliche geschäftliche E-Mail-Adresse angegeben haben, könnte es wie „nancy@contoso.onmicrosoft.com“ aussehen. Ihr Konto wird in einem Mandanten in Azure Active Directory (AAD) gespeichert. In den meisten Fällen entspricht der UPN Ihres AAD-Kontos der E-Mail-Adresse.

## <a name="windows-service-account"></a>Windows-Dienstkonto

Das lokale Datengateway ist so konfiguriert, dass *NT SERVICE\PBIEgwService* als Anmeldeinformationen für den Windows-Dienst verwendet wird. Standardmäßig ist die Anmeldung als Dienst auf dem Computer zulässig, auf dem Sie das Gateway installieren. Bei dem Konto handelt es sich nicht um dasselbe Konto, das zum Verbinden mit lokalen Datenquellen verwendet wird. Es ist auch nicht Ihr Geschäfts-, Schul- oder Unikonto, mit dem Sie sich bei Clouddiensten anmelden.

> [!NOTE]
> Wenn Sie den persönlichen Modus ausgewählt haben, konfigurieren Sie das Windows-Dienstkonto separat.

Wenn bei der Authentifizierung Ihres Proxyservers Probleme auftreten, ändern Sie das Windows-Dienstkonto in ein Domänenbenutzerkonto oder verwaltetes Dienstkonto. Weitere Informationen finden Sie unter [Proxykonfiguration](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

## <a name="ports"></a>Ports

Das Gateway stellt eine ausgehende Verbindung mit Azure Service Bus her. Die Kommunikation erfolgt über diese ausgehenden Ports: TCP 443 (Standard), 5671, 5672, 9350 bis 9354.  Das Gateway benötigt keine eingehenden Ports.

Es wird empfohlen, die IP-Adressen der Liste zugelassener IP-Adressen für Ihren Datenbereich in Ihrer Firewall hinzuzufügen. Sie können die [IP-Liste des Microsoft Azure-Rechenzentrums](https://www.microsoft.com/download/details.aspx?id=41653) herunterladen, die wöchentlich aktualisiert wird. Alternativ können Sie die Liste der erforderlichen Ports abrufen, indem Sie den [Network port test (Netzwerkporttests)](../service-gateway-onprem-tshoot.md#network-ports-test) in der lokalen Datengatewayanwendung ausführen. Das Gateway verwendet für die Kommunikation mit Azure Service Bus die IP-Adresse zusammen mit dem vollständig qualifizierten Domänennamen (Fully Qualified Domain Name, FQDN). Wenn Sie für das Gateway Kommunikation per HTTPS erzwingen, verwendet das Gateway ausschließlich den FQDN, und es erfolgt keine Kommunikation mithilfe von IP-Adressen.


> [!NOTE]
> Die IP-Adressen in der Liste der Azure-Datacenter-IP-Adressen sind in CIDR-Notation angegeben. Beispielsweise bedeutet „10.0.0.0/24“ nicht „10.0.0.0 bis 10.0.0.24“. Erfahren Sie mehr zur [CIDR-Notation](http://whatismyipaddress.com/cidr).

Es folgt eine Liste der vollqualifizierten Domänennamen, die vom Gateway verwendet werden.

| Domänennamen | Ausgehende Ports | Beschreibung |  |
|-----------------------------|----------------|--------------------------------------------------------------------------------------------------------------------|---|
| *.download.microsoft.com | 80 | Wird zum Herunterladen des Installationsprogramms verwendet. Diese Domäne wird auch von der Datengateway-App zur Überprüfung der Version und der Region des Gateways verwendet. |  |
| *.powerbi.com | 443 | Wird zum Identifizieren des entsprechenden Power BI-Clusters verwendet. |  |
| *.analysis.windows.net | 443 | Wird zum Identifizieren des entsprechenden Power BI-Clusters verwendet. |  |
| *.login.windows.net | 443 | Wird zum Authentifizieren der Datengateway-App mit Azure Active Directory/OAuth2 verwendet. |  |
| *.servicebus.windows.net | 5671-5672 | Wird für das Advance Message Queueing Protocol (AMQP) verwendet. |  |
| *.servicebus.windows.net | 443, 9350-9354 | Wird von Listenern an Service Bus Relay über TCP verwendet (erfordert 443 für die Zugriffssteuerung auf den Tokenabruf). |  |
| *.frontend.clouddatahub.net | 443 | Veraltet – nicht mehr erforderlich. Wird in Zukunft aus der Dokumentation entfernt. |  |
| *.core.windows.net | 443 | Wird von Dataflows in Power BI verwendet, um Daten in Azure Data Lake zu schreiben. |  |
| login.microsoftonline.com | 443 | Wird zum Authentifizieren der Datengateway-App mit Azure Active Directory/OAuth2 verwendet. |  |
| *. msftncsi.com | 443 | Wird vom Power BI-Dienst zum Testen der Internetverbindung und der Erreichbarkeit des Gateways verwendet. |  |
| *.microsoftonline-p.com | 443 | Wird zum Authentifizieren der Datengateway-App mit Azure Active Directory/OAuth2 verwendet. |  |
| | |

> [!NOTE]
> Sobald das Gateway installiert und registriert ist, sind nur die von Azure Service Bus benötigten Ports/IPs erforderlich (servicebus.windows.net). Sie können die Liste der erforderlichen Ports abrufen, indem Sie den [Network port test (Netzwerkporttests)](../service-gateway-onprem-tshoot.md#network-ports-test) in der lokalen Datengatewayanwendung ausführen.

## <a name="forcing-https-communication-with-azure-service-bus"></a>Erzwingen der HTTPS-Kommunikation mit Azure Service Bus

Sie können erzwingen, dass das Gateway zur Kommunikation mit Azure Service Bus anstelle von TCP das HTTPS-Protokoll verwendet.

> [!NOTE]
> Auf Empfehlung von Azure Service Bus wird ab dem Release von Juni 2019 bei neuen Installationen (nicht Updates) standardmäßig das HTTPS-Protokoll anstelle von TCP verwendet.

Ändern Sie die Datei *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*, indem Sie den Wert wie im Codeausschnitt des folgenden Paragrafen von `AutoDetect` zu `Https` ändern, um die Kommunikation über HTTPS zu erzwingen. Diese Datei befindet sich (standardmäßig) unter *C:\Programme\Lokales Datengateway*.

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

Beim Wert des *ServiceBusSystemConnectivityModeString*-Parameters muss die Groß-/Kleinschreibung beachtet werden. Gültige Werte sind *AutoDetect* und *Https*.

Alternativ können Sie mithilfe der Gatewaybenutzeroberfläche dieses Verhalten des Gateways erzwingen. Wählen Sie auf der Gateway-Benutzeroberfläche **Netzwerk** aus, und wählen Sie dann für **Azure Service Bus-Konnektivitätsmodus** die Option **Ein** aus.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_01.png)

Wenn Sie nach dem Durchführen der Änderung **Übernehmen** (eine Schaltfläche, die nur angezeigt wird, wenn Sie eine Änderung vornehmen) auswählen, wird der *Windows-Dienst Gateway* automatisch neu gestartet, damit die Änderung wirksam werden kann.

In ähnlichen Situationen in der Zukunft können Sie den *Windows-Dienst Gateway* über das Dialogfeld neu starten, indem Sie **Diensteinstellungen** und dann *Jetzt neu starten* auswählen.

![](./media/gateway-onprem-accounts-ports-more/gw-onprem_02.png)

## <a name="support-for-tls-12"></a>Unterstützung für TLS 1.2

Standardmäßig verwendet das lokale Datengateway Transport Layer Security (TLS) 1.2 für die Kommunikation mit dem Power BI-Dienst. Um sicherzustellen, dass für sämtlichen Datenverkehr im Gateway TLS 1.2 verwendet wird, müssen Sie auf dem Computer, auf dem der Gatewaydienst ausgeführt wird, möglicherweise die folgenden Registrierungsschlüssel hinzufügen oder ändern:

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]"SchUseStrongCrypto"=dword:00000001
```

> [!NOTE]
> Durch Hinzufügen bzw. Ändern dieser Registrierungsschlüssel wird die Änderung auf alle .NET-Anwendungen angewendet. Weitere Informationen zu den Registrierungsänderungen mit Auswirkungen auf TLS für andere Anwendungen finden Sie unter [TLS-Registrierungseinstellungen (Transport Layer Security)](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings).

## <a name="how-to-restart-the-gateway"></a>So starten Sie das Gateway neu

Das Gateway wird als Windows-Dienst ausgeführt. Sie können es wie jeden anderen Windows-Dienst starten und beenden. In der Eingabeforderung müssen Sie daher wie folgt vorgehen:

1. Starten Sie auf dem Computer, auf dem das Gateway ausgeführt wird, eine Administratoreingabeaufforderung.
2. Verwenden Sie den folgenden Befehl zum Beenden des Diensts.
   
   net stop PBIEgwService
3. Verwenden Sie den folgenden Befehl zum Starten des Diensts.
   
   net start PBIEgwService

