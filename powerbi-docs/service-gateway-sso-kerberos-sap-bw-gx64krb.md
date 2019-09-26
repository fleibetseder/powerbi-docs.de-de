---
title: Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP BW mithilfe von gx64krb5
description: Konfigurieren Ihres SAP BW-Servers, um einmaliges Anmelden vom Power BI-Dienst mithilfe von gx64krb5 zu aktivieren
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106329"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Verwenden von Kerberos für SSO (Single Sign-On, Einmaliges Anmelden) bei SAP BW mithilfe von gx64krb5

In diesem Artikel wird beschrieben, wie Sie Ihren SAP BW-Server dafür konfigurieren, dass SSO vom Power BI-Dienst mithilfe von gx64krb5 aktiviert wird.

> [!NOTE]
> Sie können die Schritte in diesem Artikel zusätzlich zu den Schritten in [Konfigurieren von Kerberos-SSO](service-gateway-sso-kerberos.md) ausführen, um eine Aktualisierung von auf SAP BW Application Server basierenden Berichten zu ermöglichen, die Kerberos SSO im Power BI-Dienst verwenden. Microsoft empfiehlt jedoch die Verwendung von CommonCryptoLib als SNC-Bibliothek. SAP bietet keine Unterstützung für gx64krb5 mehr, und die Schritte, die für die Konfiguration für die Nutzung mit dem Gateway erforderlich sind, sind im Vergleich mit CommonCryptoLib deutlich komplexer. Informationen zum Konfigurieren von SSO mithilfe von CommonCryptoLib finden Sie unter [Konfigurieren von SAP BW für SSO mithilfe von CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Sie sollten die Konfiguration für CommonCryptoLib _oder_ gx64krb5 abschließen. Führen Sie nicht die Konfigurationsschritte für beide Bibliotheken aus.

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>Einrichten von gx64krb5/gsskrb5 auf dem Gatewaycomputer und dem SAP BW-Server

> [!NOTE]
> `gx64krb5` und `gsskrb5` werden von SAP nicht mehr aktiv unterstützt. Weitere Informationen finden Sie im [SAP-Hinweis 352295](https://launchpad.support.sap.com/#/notes/352295). Beachten Sie auch, dass `gx64krb5` keine SSO-Verbindungen vom Datengateway zu SAP BW-Nachrichtenservern zulässt. Nur Verbindungen mit SAP BW-Anwendungsservern sind möglich. Diese Einschränkung auf Anwendungsserver entfällt, wenn Sie [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) als SNC-Bibliothek verwenden. Andere SNC-Bibliotheken lassen sich möglicherweise ebenfalls für BW SSO einsetzen, sie werden aber nicht offiziell von Microsoft unterstützt.

`gx64krb5` \ `gsskrb5` muss sowohl vom Client als auch vom Server genutzt werden, damit eine SSO-Verbindung über das Gateway hergestellt werden kann, d.h. Client und Server müssen die gleiche SNC-Bibliothek verwenden.

1. Laden Sie `gx64krb5` aus dem [SAP-Hinweis 2115486](https://launchpad.support.sap.com/) herunter (S-User von SAP erforderlich). Stellen Sie sicher, dass Sie mindestens über Version 1.0.11.x verfügen. Laden Sie außerdem `gsskrb5` (die 32-Bit-Version der Bibliothek) herunter, wenn Sie die SSO-Verbindung im SAP-GUI testen möchten, bevor Sie die SSO-Verbindung über das Gateway versuchen (empfohlen). Die 32-Bit-Version ist für das Testen mit dem SAP-GUI erforderlich, da das SAP-GUI nur als 32-Bit-Version verfügbar ist.

1. Speichern Sie `gx64krb5` an einem Ort auf Ihrem Gatewaycomputer, auf den der Benutzer Ihres Gatewaydiensts zugreifen kann (und auch das SAP-GUI, falls Sie die SSO-Verbindung per SAP Logon testen möchten). Sowohl der Gatewaydienstbenutzer als auch die Active Directory-Benutzer (AD), deren Identität der Dienstbenutzer annimmt, benötigen Lese-und Ausführungsberechtigungen für die DLL. Es wird empfohlen, der Gruppe „Authentifizierte Benutzer“ Berechtigungen für die DLL zu erteilen. Zu Testzwecken können Sie diese Berechtigungen auch explizit dem Gatewaydienstbenutzer und dem Active Directory-Benutzer erteilen, die Sie für den Test verwenden möchten.

1. Wenn Ihr BW-Server noch nicht mithilfe von gx64krb5/gsskrb5 für SSO konfiguriert wurde, legen Sie eine weitere Kopie auf Ihrem SAP BW-Servercomputer an einem Speicherort ab, auf den der SAP BW-Server zugreifen kann. 

1. Legen Sie auf dem Client- und Servercomputer die Umgebungsvariablen `SNC_LIB` oder `SNC_LIB_64` fest. Wenn Sie gsskrb5 verwenden, legen Sie die `SNC_LIB`-Variable auf den absoluten Pfad von gsskrb5.dll fest. Wenn Sie gx64krb5 verwenden, legen Sie die `SNC_LIB_64`-Variable auf den absoluten Pfad von gx64krb5.dll fest.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>Konfigurieren eines SAP BW-Dienstbenutzers und Aktivieren der SNC-Kommunikation

Führen Sie diesen Abschnitt aus, wenn Sie Ihren SAP BW-Server noch nicht für SNC-Kommunikation (d.h. SSO) mithilfe von gx64krb5/gsskrb5 konfiguriert haben.

> [!NOTE]
> In diesem Abschnitt wird davon ausgegangen, dass Sie bereits einen Dienstbenutzer für BW erstellt und einen passenden SPN an ihn gebunden haben (d.h. etwas, das mit `SAP/` beginnt).

1. Gewähren Sie dem Dienstbenutzer Zugriff auf Ihren SAP BW-Anwendungsserver:

    1. Fügen Sie auf dem SAP BW-Servercomputer den Dienstbenutzer der lokalen Administratorgruppe hinzu. Öffnen Sie hierzu das Programm „Computerverwaltung“, und doppelklicken Sie auf die lokale Administratorgruppe für Ihren Server.

        ![Screenshot: Programm „Computerverwaltung“](media/service-gateway-sso-kerberos/computer-management.png)

    1. Doppelklicken Sie auf die lokale Administratorgruppe, und wählen Sie **Hinzufügen** aus, um Ihren Dienstbenutzer der Gruppe hinzuzufügen. Wählen Sie **Namen überprüfen** aus, um sicherzustellen, dass Sie den Namen korrekt eingegeben haben. Wählen Sie **OK**aus.

1. Legen Sie den Dienstbenutzer des SAP BW-Servers als den Benutzer fest, der den SAP BW-Serverdienst auf dem SAP BW-Servercomputer startet.

    1. Öffnen Sie **Ausführen**, und geben Sie „Services.msc“ ein. Suchen Sie nach dem Dienst für die Instanz Ihres SAP BW-Anwendungsservers. Klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Eigenschaften** aus.

        ![Screenshot: „Dienste“ mit hervorgehobener Option „Eigenschaften“](media/service-gateway-sso-kerberos/server-properties.png)

    1. Wechseln Sie zur Registerkarte **Anmelden**, und ändern Sie den Benutzer in Ihren SAP BW-Dienstbenutzer. Geben Sie das Kennwort des Benutzers ein, und wählen Sie **OK** aus.

1. Melden Sie sich über SAP Logon bei Ihrem Server an, und legen Sie mithilfe der Transaktion RZ10 folgende Profilparameter fest:

    1. Legen Sie den Profilparameter „snc/identity/as“ auf „p:\<von Ihnen erstellter SAP BW-Dienstbenutzer\>“ fest (Beispiel: p:BWServiceUser@MYDOMAIN.COM). Beachten Sie das „p:“, das dem UPN des Dienstbenutzers vorangestellt ist. Das Präfix lautet nicht „p:CN=“ wie bei Verwendung der Common Crypto-Bibliothek als SNC-Bibliothek.

    1. Legen Sie den Profilparameter „snc/gssapi\_lib“ auf \<Pfad zu gsskrb5.dll/gx64krb5.dll auf dem BW-Servercomputer\> fest (die verwendete Bibliothek hängt von der Bitanzahl des Betriebssystems ab). Vergessen Sie nicht, die Bibliothek an einem Ort zu speichern, auf den der SAP BW-Anwendungsserver zugreifen kann.

    1. Legen Sie außerdem folgende zusätzliche Profilparameter fest, bei denen Sie den Wert nach Bedarf ändern können. Beachten Sie, dass Clients durch die letzten fünf Optionen über SAP Logon eine Verbindung mit dem SAP BW-Server herstellen können, ohne dass SNC konfiguriert wurde.

        | **Einstellung** | **Wert** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Legen Sie die Eigenschaft „snc/enable“ auf 1 fest.

1. Wenn Sie diese Profilparameter festgelegt haben, öffnen Sie auf dem Servercomputer die SAP-Verwaltungskonsole, und starten Sie die SAP BW-Instanz neu. Sollte der Server nicht starten, vergewissern Sie sich, dass Sie die Profilparameter korrekt festgelegt haben. Weitere Informationen zu den Einstellungen für die Profilparameter finden Sie in der [SAP-Dokumentation](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Bei Bedarf steht im weiteren Verlauf der Dokumentation auch ein Problembehandlungsabschnitt zur Verfügung.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Zuordnen eines SAP BW-Benutzers zu einem Active Directory-Benutzer

Wenn die noch nicht erfolgt ist, ordnen Sie einen Active Directory-Benutzer dem Benutzer eines SAP BW-Anwendungsservers zu, und testen Sie die SSO-Verbindung in SAP Logon.

1. Melden Sie sich über SAP Logon bei Ihrem SAP BW-Server an. Führen Sie die Transaktion SU01 aus.

1. Geben Sie für **User** (Benutzer) den SAP BW-Benutzer ein, für den Sie SSO-Verbindungen aktivieren möchten. (Auf dem vorherigen Screenshot wird die Berechtigung für „BIUSER“ festgelegt.) Klicken Sie auf der Symbolleiste des SAP Logon-Fensters auf das **Bearbeitungssymbol** (Stift).

    ![Screenshot: SAP BW-Bildschirm für die Benutzerverwaltung](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Wählen Sie die Registerkarte **SNC** aus. Geben Sie im Eingabefeld „SNC name“ (SNC-Name) die Zeichenfolge „p:\<Ihr Active Directory-Benutzer\>@\<Ihre Domäne\>“ ein. Achten Sie auf die erforderliche Zeichenfolge „p:“, die dem UPN des Active Directory-Benutzers vorangestellt sein muss. Der angegebene Active Directory-Benutzer muss zu der Person oder Organisation gehören, für die Sie den SSO-Zugriff auf den SAP BW-Anwendungsserver gewähren möchten. Geben Sie beispielsweise p:testuser@TESTDOMAIN.COM ein, wenn Sie dem Benutzer „testuser\@TESTDOMAIN.COM“ SSO-Zugriff gewähren möchten.

    ![Screenshot: SAP BW-Bildschirm für die Benutzerverwaltung](media/service-gateway-sso-kerberos/maintain-users.png)

1. Wählen Sie in der Nähe der linken oberen Bildschirmecke auf das **Speichersymbol** (Diskette).

### <a name="test-sign-in-by-using-sso"></a>Testen der Anmeldung mit SSO

Überprüfen Sie, ob Sie sich mithilfe von SAP Logon über SSO als der Active Directory-Benutzer anmelden können, für den Sie gerade den SSO-Zugriff aktiviert haben.

1. Melden Sie sich als der Active Directory-Benutzer, für den Sie soeben den SSO-Zugriff aktiviert haben, bei einem Computer an, auf dem SAP Logon installiert ist. Starten Sie SAP Logon, und erstellen Sie eine neue Verbindung.

1. Wählen Sie im Fenster **Create New System Entry** (Neuen Systemeintrag erstellen) die Optionen **User Specified System** (Benutzerdefiniertes System) > **Next** (Weiter) aus.

    ![Screenshot: Bildschirm zum Erstellen eines neuen Systemeintrags](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Geben Sie auf dem nächsten Bildschirm die entsprechenden Details (einschließlich Anwendungsserver, Instanznummer und System-ID) ein. Wählen Sie **Finish** (Fertig stellen) aus.

1. Klicken Sie mit der rechten Maustaste auf die neue Verbindung, und wählen Sie **Properties** (Eigenschaften) aus. Wählen Sie die Registerkarte **Network** (Netzwerk) aus. Geben Sie im Textfeld **SNC Name** (SNC-Name) die Zeichenfolge „p:\<UPN des SAP BW-Dienstbenutzers\>“ ein (Beispiel: p:BWServiceUser@MYDOMAIN.COM). Wählen Sie dann **OK** aus.

    ![Screenshot: Bildschirm mit den Systemeintragseigenschaften](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Doppelklicken Sie auf die Verbindung, die Sie gerade erstellt haben, um eine SSO-Verbindung mit dem SAP BW-Server herzustellen. Wenn die Verbindung erfolgreich ist, fahren Sie mit dem nächsten Schritt fort. Gehen Sie die vorherigen Schritt in dieser Dokumentation andernfalls erneut durch, um sicherzustellen, dass diese ordnungsgemäß durchgeführt wurden. Alternativ können Sie den untenstehenden Abschnitt zur Problembehandlung lesen. Hinweis: Wenn Sie in diesem Kontext keine SSO-Verbindung mit dem SAP BW-Server herstellen können, können Sie auch im Gatewaykontext keine SSO-Verbindung mit dem SAP BW-Server herstellen.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Hinzufügen von Registrierungseinträgen zum Gatewaycomputer

Fügen Sie die erforderlichen Registrierungseinträge zur Registrierung des Computers hinzu, auf dem das Gateway installiert ist, sowie zu den Computern, die für die Verbindung von Power BI Desktop vorgesehen sind. Auszuführende Befehle:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Hinzufügen einer neuen Datenquelle vom Typ „SAP BW-Anwendungsserver“ zum Power BI-Dienst oder Bearbeiten einer vorhandenen Datenquelle

1. Geben Sie im Konfigurationsfenster der Datenquelle genau wie bei der Anmeldung beim SAP BW-Server über Power BI Desktop den **Hostnamen**, die **Systemnummer** und die **Client-ID** des Anwendungsservers ein.

1. Geben Sie im Feld **Name des SNC-Partners** Folgendes ein: p:\<SPN, den Sie Ihrem SAP BW-Dienstbenutzer zugeordnet haben\>. Wenn der SPN z.B. „SAP/BWServiceUser@MYDOMAIN.COM“ lautet, geben Sie „p:SAP/BWServiceUser@MYDOMAIN.COM“ im Feld **Name des SNC-Partners** ein.

1. Wählen Sie **SNC_LIB** oder **SNC_LIB_64** als SNC-Bibliothek aus. Vergewissern Sie sich, dass „SNC_LIB_64“ auf dem Gatewaycomputer auf „gx64krb5.dll“ verweist. Alternativ können Sie die Option „Benutzerdefiniert“ auswählen und den absoluten Pfad zu gx64krb5.dll (auf dem Gatewaycomputer) angeben.

1. Aktivieren Sie das Kontrollkästchen **SSO über Kerberos für DirectQuery-Abfragen verwenden**, und wählen Sie **Anwenden** aus. Wenn die Testverbindung nicht erfolgreich ist, überprüfen Sie, dass das Setup und die Konfigurationsschritte ordnungsgemäß durchgeführt wurden.

1. [Ausführen eines Power BI-Berichts](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Problembehandlung

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>Problembehandlung der gx64krb5/gsskrb5-Konfiguration

Sollten Probleme mit der Installation von gx64krb5/gsskrb5 oder mit SSO-Verbindungen über SAP Logon auftreten, gehen Sie wie folgt vor.

* Die Serverprotokolle („...work\dev\_w0“ auf dem Servercomputer) können beim Behandeln von Problemen hilfreich sein, die beim Setup von gx64krb5/gsskrb5 auftreten. Dies gilt insbesondere dann, wenn der SAP BW-Server nicht startet, nachdem die Profilparameter geändert wurden.

* Falls Sie den SAP BW-Dienst aufgrund eines Anmeldefehlers nicht starten können, haben Sie möglicherweise das falsche Kennwort angegeben, als Sie den Benutzer zum Starten von SAP BW festgelegt haben. Überprüfen Sie das Kennwort, indem Sie sich bei einem Computer in Ihrer Active Directory-Umgebung als der SAP BW-Dienstbenutzer anmelden.

* Sollte eine Fehlermeldung im Zusammenhang mit SQL-Anmeldeinformationen angezeigt werden, überprüfen Sie, ob Sie dem Dienstbenutzer Zugriff auf die SAP BW-Datenbank gewährt haben.

* Unter Umständen wird folgende Meldung angezeigt: „(GSS-API) specified target is unknown or unreachable“ ((GSS-API) Das angegebene Ziel ist unbekannt oder nicht erreichbar.). Das bedeutet in der Regel, dass Sie den falschen SNC-Namen angegeben haben. Vergewissern Sie sich, dass Sie in der Clientanwendung nur „p:“ verwendet haben (nicht etwa „p:CN=“ oder eine andere Zeichenfolge außer dem UPN des Dienstbenutzers).

* Unter Umständen wird folgende Meldung angezeigt: „(GSS-API) An invalid name was supplied“ ((GSS-API) Ein ungültiger Name wurde angegeben.). Vergewissern Sie sich, dass „p:“ im Wert des SNC-Identitätsprofilparameters des Servers enthalten ist.

* Unter Umständen wird folgende Meldung angezeigt: „(SNC error) the specified module could not be found“ ((SNC-Fehler) Das angegebene Modul wurde nicht gefunden.). Dieser Fehler ist üblicherweise darauf zurückzuführen, dass sich `gsskrb5.dll/gx64krb5.dll` an einem Speicherort befindet, auf den nur mit erweiterten Berechtigungen (Administratorrechten) zugegriffen werden kann.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Behandeln von Problemen mit der Gatewaykonnektivität

1. Überprüfen Sie die Gatewayprotokolle. Öffnen Sie die Anwendung für die Gatewaykonfiguration, und wählen Sie **Diagnose** > **Protokolle exportieren** aus. Die neuesten Fehler befinden sich jeweils am Ende der Protokolldatei.

    ![Screenshot: Lokales Datengateway mit hervorgehobener Diagnose](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Aktivieren Sie die SAP BW-Ablaufverfolgung, und überprüfen Sie die generierten Protokolldateien. Es sind verschiedene SAP BW-Ablaufverfolgungen verfügbar. Weitere Informationen finden Sie in der SAP-Dokumentation.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum **lokalen Datengateway** und zu **DirectQuery** finden Sie in den folgenden Ressourcen:

* [What is an on-premises data gateway? (Was ist ein lokales Datengateway?)](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Von DirectQuery unterstützte Datenquellen](desktop-directquery-data-sources.md)
* [DirectQuery und SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery und SAP HANA](desktop-directquery-sap-hana.md)
