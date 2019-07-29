---
title: Lokales Datengateway – Problembehandlung
description: Dieser Artikel erläutert Wege, wie Sie Probleme behandeln können, die mit dem lokalen Datengateway und Power BI auftreten. Er bietet eventuell Hilfestellungen für bekannte Probleme und nennt Tools, die Sie unterstützen.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: a013b42f1cd7cc9b2c5c24f9636683a52687ceb8
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271398"
---
# <a name="troubleshoot-gateways---power-bi"></a>Lokales Datengateway – Problembehandlung

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

In diesem Artikel werden einige häufige Probleme erläutert, die beim Verwenden des **lokalen Datengateways** mit Power BI auftreten können. Wenn bei Ihnen ein Fehler auftritt, der hier nicht aufgelistet ist, können Sie die [Communitywebsite](http://community.powerbi.com) von Power BI wenden oder ein [Supportticket](http://powerbi.microsoft.com/support) erstellen.

## <a name="configuration"></a>Konfiguration

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>Fehler: Der Power BI-Dienst hat gemeldet, dass das lokale Gateway nicht erreichbar ist. Starten Sie das Gateway neu, und versuchen Sie es erneut.

Am Ende der Konfiguration wird der Power BI-Dienst erneut aufgerufen, um das Gateway zu überprüfen. Der Power BI-Dienst hat dabei das Gateway nicht als live gemeldet. Das Neustarten des Windows-Diensts könnte bewirken, dass die Kommunikation anschließend erfolgreich ist. Für weitere Details können Sie die Protokolle wie im Artikel [Sammeln von Protokollen aus der lokalen Datengateway-App](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app) beschrieben sammeln und überprüfen.

## <a name="data-sources"></a>Datenquellen

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>Fehler: Verbindung nicht möglich. Details: „Ungültige Anmeldeinformationen für die Verbindung.“

In **Details anzeigen** wird die von der Datenquelle empfangene Fehlermeldung angezeigt. Für SQL Server sollte etwa Folgendes angezeigt werden:

    Login failed for user 'username'.

Achten Sie darauf, dass Benutzername und Kennwort richtig sind. Überprüfen Sie auch, ob anhand dieser Anmeldeinformationen eine Verbindung mit der Datenquelle hergestellt werden kann. Achten Sie auch darauf, dass das verwendete Konto der ausgewählten **Authentifizierungsmethode**entspricht.

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>Fehler: Verbindung nicht möglich. Details: „Es kann keine Verbindung mit der Datenbank hergestellt werden.“

Wir konnten die Verbindung mit dem Server, jedoch nicht mit der angeforderten Datenbank herstellen. Überprüfen Sie den Namen der Datenbank sowie die erforderliche Berechtigung des Benutzers für den Zugriff auf die Datenbank.

In **Details anzeigen** wird die von der Datenquelle empfangene Fehlermeldung angezeigt. Für SQL Server sollte etwa Folgendes angezeigt werden:

    Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>Fehler: Verbindung nicht möglich. Details: „Unbekannter Fehler in Datengateway.“

Dieser Fehler kann aus verschiedenen Gründen auftreten. Achten Sie darauf, dass Sie von dem Computer, auf dem das Gateway ausgeführt wird, eine Verbindung mit der Datenquelle herstellen können. Es könnte auch an einem nicht erreichbaren DHCP-Server liegen.

In **Details anzeigen** wird der Fehlercode **DM_GWPipeline_UnknownError** angezeigt.

Sie können auch in den Ereignisprotokollen nach weiteren Details suchen: „Ereignisprotokolle“ > **Anwendungs- und Dienstprotokolle** > **Dienst Lokales Datengateway**.

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>Fehler: "Beim Herstellen einer Verbindung mit \<Server\> ist ein Fehler aufgetreten." Details: „Das Datengateway wurde erreicht, aber das Gateway kann nicht auf die lokale Datenquelle zugreifen.“

Wir konnten keine Verbindung mit der angegebenen Datenquelle herstellen. Überprüfen Sie die für diese Datenquelle angegebenen Informationen.

In **Details anzeigen** wird der Fehlercode **DM_GWPipeline_Gateway_DataSourceAccessError** angezeigt.

Wenn die zugrunde liegende Fehlermeldung ähnlich wie die folgende ist, bedeutet dies, dass das Konto, das Sie für die Datenquelle verwenden, keinem Serveradministrator für diese Analysis Services-Instanz gehört. [Weitere Informationen](https://docs.microsoft.com/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)

    The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.

Wenn die zugrunde liegende Fehlermeldung der folgenden ähnelt, könnte dies bedeuten, dass das Verzeichnisattribut [token-groups-global-and-universal](https://msdn.microsoft.com/library/windows/desktop/ms680300.aspx) (TGGAU) womöglich nicht im Servicekonto für Analysis Services vorhanden ist:

    The username or password is incorrect.

Bei Domänen, die mit Windows-Versionen vor Windows 2000 kompatibel sind, ist das TGGAU-Attribut aktiviert. Allerdings aktivieren die meisten neu erstellten Domänen dieses Attribut nicht standardmäßig. Weitere Informationen zu diesem Thema finden Sie [hier](https://support.microsoft.com/kb/331951).

Sie können dies wie folgt überprüfen.

1. Verbinden Sie sich mit dem Analysis Services-Computer in SQL Server Management Studio. Schließen Sie in den erweiterten Verbindungseigenschaften EffectiveUserName für den betreffenden Benutzer ein, und prüfen Sie, ob der Fehler erneut auftritt.
2. Sie können das Active Directory-Tool „Dsacls“ verwenden, um zu überprüfen, ob das Attribut aufgeführt ist. Dieses Tool befindet sich auf einem Domänencontroller. Sie müssen wissen, wie der spezifische Domänenname für das Konto lautet, und ihn an das Tool weitergeben.

        dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"

    Das Ergebnis wird in etwa das folgende sein:

            Allow BUILTIN\Windows Authorization Access Group
                                          SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                          READ PROPERTY

Um dieses Problem zu beheben, müssen Sie das TGGAU-Attribut auf dem Konto aktivieren, das für den Analysis Services-Windows-Dienst verwendet wird.

#### <a name="another-possibility-for-username-or-password-incorrect"></a>Eine weitere mögliche Ursache für die Meldung „User name or password incorrect“ (Benutzername oder Kennwort falsch).

Dieser Fehler kann auch dadurch verursacht werden, dass sich der Analysis Services-Server in einer anderen Domäne als die Benutzer befindet und keine bidirektionale Vertrauensstellung eingerichtet ist.

In diesem Fall müssen Sie mit Ihren Domänenadministratoren zusammenarbeiten, um die Vertrauensstellung zwischen den Domänen zu überprüfen.

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Datengateway-Datenquellen können nicht im Bereich „Daten abrufen“ für Analysis Services über den Power BI-Dienst angezeigt werden.

Stellen Sie sicher, dass Ihr Konto auf der Registerkarte **Benutzer** der Datenquelle in der Gateway-Konfiguration aufgelistet ist. Wenn Sie keinen Zugriff auf das Gateway haben, wenden Sie sich an den Administrator des Gateways, und bitten Sie ihn um die Überprüfung. Die in der Analysis Services-Liste aufgeführte Datenquelle ist nur für Konten in der Liste **Benutzer** sichtbar.

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>Fehler: Für die Datenquellen in diesem Dataset wurde kein Gateway installiert oder konfiguriert.

Stellen Sie sicher, dass Sie mindestens eine Datenquelle zum Gateway hinzugefügt haben. Der Vorgang wird im Abschnitt „Hinzufügen einer Datenquelle“ unter [Verwalten eines Power BI-Gateways](service-gateway-data-sources.md#add-a-data-source) beschrieben. Wenn das Gateway nicht im Verwaltungsportal unter **Gateways verwalten** aufgeführt wird, löschen Sie den Cache Ihres Browsers, oder melden Sie sich ab und dann wieder an.

## <a name="datasets"></a>Datasets

### <a name="error-there-is-not-enough-space-for-this-row"></a>Fehler: Für diese Zeile ist nicht ausreichend Platz vorhanden.

Dieser Fehler tritt auf, wenn eine einzelne Zeile größer als 4 MB ist. Finden Sie in diesem Fall heraus, um welche Zeile in der Datenquelle es sich handelt, und versuchen Sie, die Zeile herauszufiltern oder deren Größe zu verringern.

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>Fehler: Der angegebene Servername stimmt nicht mit dem Servernamen auf dem SQL Server-SSL-Zertifikat überein.

Dieser Fehler kann auftreten, wenn der allgemeine Name des Zertifikats für den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) des Servers gilt, Sie jedoch nur den NetBIOS-Namen des Servers angegeben haben. Dies verursacht eine Nichtübereinstimmung für das Zertifikat. Um dieses Problem zu beheben, muss in der Gatewaydatenquelle und in der PBIX-Datei der FQDN des Servers als Servername verwendet werden.

### <a name="i-dont-see-the-on-premises-data-gateway-present-when-configuring-scheduled-refresh"></a>"I don't see the on-premises data gateway present when configuring scheduled refresh" (Beim Konfigurieren der geplanten Aktualisierung wird das lokale Datengateway nicht angezeigt).

Dies kann durch unterschiedliche Szenarien verursacht werden.

1. In Power BI Desktop wurden andere Server- und Datenbanknamen als in der für das Gateway konfigurierten Datenquelle eingegeben. Sie müssen die gleichen Werte aufweisen. Dabei wird die Groß-/Kleinschreibung nicht beachtet.
2. Ihr Konto ist nicht auf der Registerkarte **Benutzer** der Datenquelle in der Gatewaykonfiguration aufgelistet. Sie müssen den Administrator des Gateways bitten, Ihr Konto dieser Liste hinzuzufügen.
3. Die Power BI Desktop-Datei verfügt über mehrere Datenquellen, und nicht alle dieser Datenquellen sind für das Gateway konfiguriert. Jede Datenquelle muss für das Gateway definiert sein, damit das Gateway in der geplanten Aktualisierung angezeigt wird.

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>Fehler: Für die empfangenen unkomprimierten Daten auf dem Gatewayclient wurde das Limit überschritten.

Das Limit beträgt genau 10 GB unkomprimierte Daten pro Tabelle. Wenn dieses Problem auftritt, haben Sie geeignete Möglichkeiten, es einzuschränken und zu vermeiden. Insbesondere hilft es, die Verwendung konstanter und langer Zeichenfolgenwerte zu reduzieren und stattdessen einen normalisierten Schlüssel zu verwenden oder die Spalte zu entfernen (sofern sie nicht verwendet wird).

## <a name="reports"></a>Berichte

### <a name="report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>"Report could not access the data source because you do not have access to our data source via an on-premises data gateway" (Bericht konnte nicht auf die Datenquelle zugreifen, weil Sie nicht über ein lokales Datengateway auf die Datenquelle zugreifen können).

Hierfür gibt es meist eine der folgenden Ursachen.

1. Die Datenquelleninformationen stimmen nicht mit dem Inhalt des zugrunde liegenden Datasets überein. Der Server- und der Datenbankname der Datenquelle, die für On-premises data gateway definiert ist, müssen mit Ihren Angaben in Power BI Desktop übereinstimmen. Wenn Sie in Power BI Desktop eine IP-Adresse verwenden, muss die Datenquelle für das lokale Datengateway ebenfalls eine IP-Adresse verwenden.
2. Auf den Gateways Ihrer Organisation sind keine Datenquellen verfügbar. Sie können die Datenquelle auf einem neuen oder vorhandenen lokalen Datengateway konfigurieren.

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>Fehler: Fehler beim Zugriff auf die Datenquelle. Bitte wenden Sie sich an den Gatewayadministrator.

Wenn dieser Bericht eine Liveverbindung mit Analysis Services verwendet, könnte ein Problem mit einem an EffectiveUserName übergebenen Wert auftreten, der entweder nicht gültig ist oder über keine Berechtigungen auf dem Analysis Services-Computer verfügt. Ein Authentifizierungsproblem ist normalerweise darauf zurückzuführen, dass der Wert, der an EffectiveUserName übergeben wird, mit keinem lokalen Benutzerprinzipalnamen (user principal name; UPN) übereinstimmt.

Sie können Folgendes tun, um dies zu bestätigen.

1. Suchen Sie den effektiven Benutzernamen innerhalb der [Gatewayprotokolle](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).
2. Wenn Sie den zu übergebenden Wert ermittelt haben, überprüfen Sie, ob er korrekt ist. Falls es sich um Ihren Benutzer handelt, können Sie den folgenden Befehl in einer Eingabeaufforderung ausführen, um den UPN herauszufinden. Der UPN sieht wie eine E-Mail-Adresse aus.

        whoami /upn

Sie können optional anzeigen, was Power BI von Azure Active Directory erhält.

1. Wechseln Sie zu [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer).
2. Wählen Sie **Sign in** (Anmelden) in der rechten oberen Ecke aus.
3. Führen Sie die folgende Abfrage aus. Ihnen wird eine umfassende JSON-Antwort angezeigt.

        https://graph.windows.net/me?api-version=1.5
4. Suchen Sie nach **userPrincipalName**.

Wenn Ihr Azure Active Directory-UPN nicht mit Ihrem lokalen Active Directory-UPN übereinstimmt, können Sie die Funktion [Benutzernamen zuordnen](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources) verwenden, um ihn durch einen gültigen Wert zu ersetzen. Alternativ können Sie sich entweder an Ihren Mandantenadministrator oder an Ihren lokalen Active Directory-Administrator wenden, damit er Ihren UPN ändert.

## <a name="kerberos"></a>Kerberos

Wenn der zugrundeliegende Datenbankserver und das lokale Datengateway nicht ordnungsgemäß für die [eingeschränkte Kerberos-Delegierung](service-gateway-sso-kerberos.md) konfiguriert sind, aktivieren Sie die [ausführliche Protokollierung](/data-integration/gateway/service-gateway-performance#slow-performing-queries) am Gateway. Führen Sie außerdem zur Problembehandlung eine Fehlersuche durch, und sehen Sie sich dabei zunächst die Fehler bzw. Ablaufverfolgungen in den Protokolldateien des Gateways an. Informationen zum Sammeln von Gatewayprotokollen für die Ansicht finden Sie unter [Sammeln von Protokollen aus der lokalen Datengateway-App](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app).

### <a name="impersonationlevel"></a>ImpersonationLevel

Das ImpersonationLevel bezieht sich auf die SPN-Einrichtung oder die lokale Richtlinieneinstellung.

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**Lösung**

Folgen Sie diesen Schritten zur Lösung des Problems:

1. Richten Sie einen SPN für das lokale Gateway ein.
2. Richten Sie eine eingeschränkte Delegierung in Ihrem Active Directory (AD) ein.

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException: Fehler beim Erstellen einer Windows-Identität für den Benutzer „userid“.

Die Ausnahme „FailedToImpersonateUserException“ tritt auf, wenn Sie im Auftrag eines Benutzers nicht die Identität wechseln können. Dies kann auch passieren, wenn das Konto, zu dessen Identität Sie wechseln möchten, von einer anderen Domäne als derjenigen stammt, auf der sich die Gatewaydienstdomäne befindet (dies ist eine Einschränkung).

**Lösung**

* Vergewissern Sie sich, dass die oben im Abschnitt „ImpersonationLevel“ beschriebene Konfiguration korrekt ist.
* Stellen Sie sicher, dass die Benutzeridentität, zu der Sie versuchen zu wechseln, ein gültiges AD-Konto ist.

### <a name="general-error-1033-error-while-parsing-the-protocol"></a>„General error; 1033 error while parsing the protocol“ (Allgemeiner Fehler: Fehler 1033 bei Protokollanalyse)

Fehler 1033 tritt auf, sobald Ihre externe ID, die in SAP HANA konfiguriert ist, nicht mit den Anmeldeinformationen übereinstimmt, wenn die Identität des Benutzers über den UPN (alias@domain.com) gewechselt wird. In den Protokollen sehen Sie die Meldung „Original UPN 'alias@domain.com' replaced with a new UPN 'alias@domain.com'“ (Original-UPN durch neue UPN ersetzt).

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**Lösung**

* Der imitierte Benutzer muss für SAP HANA das Attribut „sAMAccountName“ in AD (Benutzeralias) verwenden. Ist dieses nicht korrekt, wird Fehler 1033 angezeigt.

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount.png)

* In den Protokollen wird „sAMAccountName“ (Alias) und nicht der UPN angezeigt, bei dem es sich um den Alias gefolgt von der Domäne handelt (alias@doimain.com).

    ![sAMAccount](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Kommunikationsverbindungsfehler;-10709 Verbindungsfehler (RTE:[-1] Kerberos-Fehler. Hauptversion: „Sonstiger Fehler [851968]“, Nebenversion: „Im Sicherheitspaket sind keine Anmeldeinformationen verfügbar.“

Die Fehlermeldung „-10709 Connection failed error“ (Fehler 10709: Verbindung fehlgeschlagen) wird angezeigt, wenn Ihre Delegierung nicht ordnungsgemäß in AD konfiguriert wurde.

**Lösung**

* Stellen Sie sicher, dass der SAP Hana-Server auf der Registerkarte „Delegierung“ im AD für das Gatewaydienstkonto vorhanden ist.

   ![Registerkarte „Delegierung“](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="refresh-history"></a>Verlauf aktualisieren

Beim Verwenden des Gateways für die planmäßige Aktualisierung können Sie über die Option **Verlauf aktualisieren** erkennen, welche Fehler aufgetreten sind, und nützliche Daten für eine Supportanfrage abrufen. Sie können sowohl geplante Aktualisierungen als auch Aktualisierungen nach Bedarf anzeigen. In den folgenden Schritten wird beschrieben, wie Sie zur Option **Verlauf aktualisieren** gelangen.

1. Wählen Sie im Power BI-Navigationsbereich in **Datasets** für das Dataset &gt; Menü öffnen &gt;**Aktualisierung planen** aus.

    ![Auswählen der Option „Aktualisierung planen“](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. Wählen Sie unter **Einstellungen für...** &gt;**Aktualisierung planen** die Option **Verlauf aktualisieren** aus.

    ![Auswählen der Option „Verlauf aktualisieren“](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![Anzeige der Option „Verlauf aktualisieren“](media/service-gateway-onprem-tshoot/refresh-history.png)

Weitere Informationen zur Problembehandlung bei Aktualisierungsszenarien finden Sie im Artikel [Problembehandlung bei Aktualisierungsszenarien](refresh-troubleshooting-refresh-scenarios.md).

## <a name="fiddler-trace"></a>Ablaufverfolgung mit Fiddler

[Fiddler](http://www.telerik.com/fiddler) ist ein kostenloses Tool von Telerik, mit dem HTTP-Verkehr überwacht werden kann. Sie können den Datenaustausch zwischen dem Power BI-Dienst und dem Clientcomputer verfolgen. So können Sie Fehler und ähnliche Informationen anzeigen.

![Verwenden der Fiddler-Ablaufverfolgung](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>Nächste Schritte

* [Problembehandlung für das lokale Datengateway](/data-integration/gateway/service-gateway-tshoot)
* [Konfigurieren von Proxyeinstellungen für das lokale Datengateway](/data-integration/gateway/service-gateway-proxy)  
* [Verwalten Ihrer Datenquelle – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Verwalten Ihrer Datenquelle –SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Verwalten Ihrer Datenquelle – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Verwalten der Datenquelle – Import/Geplante Aktualisierung](service-gateway-enterprise-manage-scheduled-refresh.md)  

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)
