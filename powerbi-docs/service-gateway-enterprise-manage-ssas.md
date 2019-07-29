---
title: Verwalten Ihrer Datenquelle – Analysis Services
description: So verwalten Sie On-premises data gateway und die zu diesem Gateway gehörigen Datenquellen. Dies bezieht sich auf Analysis Services im mehrdimensionalen und tabellarischen Modus.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271641"
---
# <a name="manage-your-data-source---analysis-services"></a>Verwalten Ihrer Datenquelle – Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Nach der [Installation des lokalen Datengateways](/data-integration/gateway/service-gateway-install) müssen Sie [Datenquellen hinzufügen](service-gateway-data-sources.md#add-a-data-source), die mit dem Gateway verwendet werden können. In diesem Artikel wird beschrieben, wie Sie für die geplante Aktualisierung oder für Liveverbindungen mit Gateways und Analysis Services-Datenquellen arbeiten.

Weitere Informationen zum Einrichten einer Liveverbindung mit Analysis Services [finden Sie in diesem Video.](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be)

> [!NOTE]
> Wenn Sie über eine Analysis Services-Datenquelle verfügen, müssen Sie das Gateway auf einem Computer installieren, der der gleichen Gesamtstruktur oder Domäne wie der Analysis Services-Server angehört.

## <a name="add-a-data-source"></a>Hinzufügen einer Datenquelle

Weitere Informationen zum Hinzufügen einer Datenquelle finden Sie unter [Hinzufügen einer Datenquelle](service-gateway-data-sources.md#add-a-data-source). Wählen Sie „Analysis Services“ als **Datenquellentyp**, wenn Sie eine Verbindung mit einem mehrdimensionalen oder tabellarischen Server herstellen.

![Hinzufügen der Analysis Services-Datenquelle](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

Sie sollten die Angaben für die Datenquelle vervollständigen, insbesondere für **Server** und **Datenbank**. **Benutzername** und **Kennwort** werden wie von Ihnen eingegeben vom Gateway verwendet, um eine Verbindung mit der Analysis Services-Instanz herzustellen.

> [!NOTE]
> Das von Ihnen eingegebene Windows-Konto muss über Administratorberechtigungen für die Instanz verfügen, mit der Sie eine Verbindung herstellen. Wenn für das Kennwort dieses Konto ein Ablauf festgelegt ist, erhalten Benutzer möglicherweise einen Verbindungsfehler, wenn das Kennwort für die Datenquelle nicht aktualisiert wurde. Weitere Informationen zum Speichern von Anmeldeinformationen finden Sie unter [Speichern verschlüsselter Anmeldeinformationen in der Cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Ausfüllen der Einstellungen zur Datenquelle](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

Klicken Sie auf **Hinzufügen**, nachdem Sie alle Angaben eingetragen haben. Sie können diese Datenquelle jetzt für die geplante Aktualisierung oder Live-Verbindungen mit einer lokalen Analysis Services-Instanz verwenden. Bei erfolgreicher Ausführung wird *Verbindung hergestellt* angezeigt.

![Anzeigen des Verbindungsstatus](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>Erweiterte Einstellungen

Optional können Sie die Datenschutzebene für die Datenquelle konfigurieren. Diese steuert, wie Daten kombiniert werden können. Diese wird nur für die geplante Aktualisierung verwendet und gilt nicht für Live-Verbindungen. Weitere Informationen zu Datenschutzebenen für Ihre Datenquelle finden Sie unter [Datenschutzebenen (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Festlegen der Datenschutzebene](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Benutzernamen bei Analysis Services

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Bei jeder Interaktion eines Benutzers mit einem Bericht, der mit Analysis Services verbunden ist, wird der effektive Benutzername an das Gateway und von dort aus an Ihren lokalen Analysis Services-Server übergeben. Als effektiver Benutzer wird die E-Mail-Adresse, mit der Sie sich bei Power BI anmelden, an Analysis Services übergeben. Diese wird in der Verbindungseigenschaft [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth) übergeben. Diese E-Mail-Adresse muss mit einem in der lokalen Active Directory-Domäne definierten Benutzerprinzipalnamen (UPN) übereinstimmen. Der UPN ist eine Eigenschaft des Active Directory-Kontos. Das Windows-Konto muss dann in einer Analysis Services-Rolle vorhanden sein. Wenn in Active Directory keine Übereinstimmung gefunden werden kann, wird die Anmeldung nicht erfolgreich durchgeführt. Weitere Informationen zu Active Directory und Benutzernamen finden Sie unter [Benutzernamenattribute](https://msdn.microsoft.com/library/ms677605.aspx).

Sie können auch [Ihren Power BI-Anmeldename einem lokalen Verzeichnis-UPN zuordnen](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Zuordnen von Benutzernamen zu Analysis Services-Datenquellen

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI ermöglicht die Zuordnung von Benutzernamen zu Analysis Services-Datenquellen. Sie können Regeln konfigurieren, um einen in Power BI angemeldeten Benutzernamen einem Namen zuzuordnen, der in EffectiveUserName über die Analysis Services-Verbindung übergeben wird. Diese Funktion zur Zuordnung von Benutzernamen ist eine hervorragende Möglichkeit, das Problem zu umgehen, wenn Ihr Benutzername für AAD nicht mit einem UPN in Ihrem lokalen Active Directory übereinstimmt. Wenn Ihre E-Mail-Adresse beispielsweise nancy@contoso.onmicrsoft.com lautet, könnten Sie diese nancy@contoso.com zuordnen. Dieser Wert würde dann an das Gateway übergeben.

Es gibt zwei Möglichkeiten, Benutzernamen für Analysis Services zuzuordnen:

* Manuelles Neuzuordnen von Benutzern
* Lokale Suche von Active Directory-Eigenschaften, um AAD-UPNs Active Directory-Benutzern zuzuordnen (Zuordnung mit AD-Suche)

Obwohl es möglich ist, eine manuelle Zuordnung mit dem zweiten Ansatz durchzuführen, wäre dies sehr zeitaufwändig und schwer zu verwalten. Es ist besonders schwierig, wenn der Musterabgleich nicht ausreicht – z.B. wenn sich die Domänennamen oder Benutzerkontennamen zwischen AAD und AD vor Ort unterscheiden. Daher wird das manuelle Zuordnen im Rahmen des zweiten Ansatzes nicht empfohlen.

Diese beiden Ansätze werden nacheinander in den folgenden beiden Abschnitten beschrieben.

### <a name="manual-user-name-re-mapping"></a>Manuelles Neuzuordnen von Benutzernamen

Sie können für Analysis Services-Datenquellen benutzerdefinierte UPN-Regeln (User Principal Name, Benutzerprinzipalname) Regeln konfigurieren. Dies hilft Ihnen, wenn der Anmeldename für den Power BI-Dienst nicht mit Ihrem lokale Verzeichnis-UPN übereinstimmt. Wenn Sie sich bei Power BI mit john@contoso.com anmelden, Ihr lokaler Verzeichnis-UPN aber john@contoso.local lautet, können Sie eine Zuordnungsregel konfigurieren, damit john@contoso.local an Analysis Services übergeben wird.

Den Bildschirm für die UPN-Zuordnung rufen Sie wie folgt auf.

1. Klicken Sie auf das **Zahnradsymbol**, und wählen Sie **Gateways verwalten** aus.
2. Erweitern Sie das Gateway, das die Analysis Services-Datenquelle enthält. Wenn Sie noch keine Analysis Services-Datenquelle erstellt haben, können Sie dies jetzt nachholen.
3. Wählen Sie die Datenquelle und dann die Registerkarte **Benutzer** aus.
4. Wählen Sie **Benutzernamen zuordnen** aus.

    ![Bildschirm „UPN-Zuordnung“](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

Sie sehen dann Optionen zum Hinzufügen von Regeln und zum Testen eines gegebenen Benutzers.

> [!NOTE]
> Es kann vorkommen, dass Sie versehentlich einen Benutzer ändern. Beispiel: Wenn Sie für **Ersetzen (Ursprünglicher Name)** <em>@contoso.com</em> und für **Durch (Neuer Name)** <em>@contoso.local</em> eingeben, wird bei allen Benutzern, deren Anmeldename <em>@contoso.com</em> enthält, dieser Teil durch <em>@contoso.local</em> ersetzt. Wenn Sie für **Ersetzen (Ursprünglicher Name)** außerdem <em>dave@contoso.com</em> und für **Durch (Neuer Name)** <em>dave@contoso.local</em> eingeben, wird ein Benutzer mit dem Anmeldenamen v-dave@contoso.com als v-dave<em>@contoso.local</em> gesendet.

### <a name="ad-lookup-mapping"></a>Zuordnung mit AD-Suche

Führen Sie die Schritte in diesem Abschnitt aus, um eine lokale AD-Eigenschaftensuche durchzuführen und AAD-UPNs Active Directory-Benutzern neu zuzuordnen. Gehen wir zunächst auf die Funktionsweise ein.

Im **Power BI-Dienst** geschieht Folgendes:

* Für jede Abfrage eines Power BI-AAD-Benutzers bei einem lokalen SSAS-Server wird eine UPN-Zeichenfolge übergeben. Beispiel:     firstName.lastName@contoso.com

> [!NOTE]
> Alle manuellen UPN-Benutzerzuordnungen, die in der Power BI-Datenquellenkonfiguration definiert sind, werden angewendet, *bevor* die Zeichenfolge mit dem Benutzernamen an das lokale Datengateway gesendet wird.

Führen Sie am lokalen Datengateway mit konfigurierbarer Benutzerzuordnung Folgendes aus:

1. Suchen Sie nach dem zu durchsuchenden Active Directory-Verzeichnis (automatisch oder konfigurierbar).
2. Suchen Sie nach dem Attribut der AD-Person (z.B. *E-Mail*), basierend auf der eingehenden UPN-Zeichenfolge („firstName.lastName@contoso.com“) aus dem **Power BI-Dienst**.
3. Wenn die AD-Suche zu einem Fehler führt, wird versucht, den übergebenen UPN als EffectiveUser in SSAS zu verwenden.
4. Bei erfolgreicher AD-Suche wird *UserPrincipalName* der betreffenden AD-Person abgerufen.
5. Das E-Mail-Attribut *UserPrincipalName* wird als *EffectiveUser* an SSAS übergeben. Beispiel: <em>Alias@corp.on-prem.contoso</em>.

Konfigurieren des Gateways für die Durchführung der AD-Suche:

1. [Herunterladen und Installieren des aktuellen Gateways](/data-integration/gateway/service-gateway-install)

2. Im Gateway müssen Sie den **Dienst des lokalen Datengateways** so ändern, dass er mit einem Domänenkonto ausgeführt wird (und nicht mit einem lokalen Dienstkonto – andernfalls funktioniert die AD-Suche zur Laufzeit nicht ordnungsgemäß). Wechseln Sie zur [App für das lokale Datengateway](/data-integration/gateway/service-gateway-app) auf Ihrem Computer und dann zu **Diensteinstellungen > Dienstkonto**. Vergewissern Sie sich, dass Sie über den Wiederherstellungsschlüssel für das Gateway verfügen, da Sie es auf demselben Computer wiederherstellen müssen (es sei denn, Sie möchten stattdessen ein neues Gateway erstellen). Sie müssen den Gateway-Dienst neu starten, damit die Änderung wirksam wird.

3. Navigieren Sie als Administrator zum Installationsordner des Gateways, *C:\Programme\On-premises data gateway*, um sicherzustellen, dass Sie über Schreibberechtigungen verfügen, und öffnen Sie die Datei *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

4. Bearbeiten Sie die folgenden beiden Konfigurationswerte gemäß *Ihren* Active Directory-Attributkonfigurationen für Ihre AD-Benutzer. Die unten aufgeführten Konfigurationswerte sind nur Beispiele – Sie müssen die Ihrer Active Directory-Konfiguration entsprechenden Werte angeben. Da bei den folgenden Konfigurationen die Groß-/Kleinschreibung zu berücksichtigen ist, achten Sie darauf, dass sie mit den Werten in Active Directory übereinstimmen.

    ![Azure Active Directory-Einstellungen](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    Wenn kein Wert für die ADServerPath-Konfiguration angegeben ist, verwendet das Gateway standardmäßig den globalen Katalog. Sie können auch mehrere Werte für ADServerPath angeben. Alle Werte müssen wie im folgenden Beispiel durch ein Semikolon getrennt werden.

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    Das Gateway analysiert die Werte für ADServerPath von links nach rechts, bis eine Übereinstimmung gefunden wird. Wenn keine Übereinstimmung gefunden wird, wird der ursprüngliche UPN verwendet. Stellen Sie sicher, dass das Konto, das den Gatewaydienst (PBIEgwService) ausführt, Abfrageberechtigungen für alle AD-Server besitzt, die Sie in ADServerPath angeben.

    Das Gateway unterstützt zwei Arten von ADServerPath-Konfigurationen, wie in den folgenden Beispielen.

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. Starten Sie den Dienst **Lokales Datengateway** neu, damit die Konfigurationsänderung wirksam wird.

### <a name="working-with-mapping-rules"></a>Arbeiten mit Zuordnungsregeln

Um eine Zuordnungsregel zu erstellen, geben Sie einen Wert für **Ursprünglicher Name** und **Neuer Name** ein und wählen dann **Hinzufügen** aus.

| Feld | Beschreibung |
| --- | --- |
| Ersetzen (Ursprünglicher Name) |Die E-Mail-Adresse, mit der Sie sich bei Power BI angemeldet haben. |
| Durch (Neuer Name) |Der Wert, durch den Sie ihn ersetzten möchten. Das Ergebnis der Ersetzung wird an die Eigenschaft *EffectiveUserName* für die Analysis Services-Verbindung übergeben. |

![Erstellen einer Zuordnungsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

Wenn Sie ein Element in der Liste auswählen, können Sie es mithilfe der **Richtungspfeile** an eine andere Position verschieben mit **Löschen** entfernen.

![Neuanordnen eines Elements in der Liste](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>Verwenden eines Platzhalters (\*)

Sie können für die Zeichenfolge in **Ersetzen (Ursprünglicher Name)** einen Platzhalter verwenden. Dieser kann nur einzeln und nicht zusammen mit anderen Teilen der Zeichenfolge verwendet werden. Dadurch können Sie alle Benutzer abdecken und an die Datenquelle einen einzelnen Wert übergeben. Dies ist hilfreich, wenn Sie möchten, dass alle Benutzer in der Organisation die gleichen Benutzernamen in der lokalen Umgebung verwenden.

### <a name="test-a-mapping-rule"></a>Testen von Zuordnungsregeln

Sie können überprüfen, womit ein ursprünglicher Namen ersetzt wird, indem Sie einen Wert für **Ursprünglicher Name** eingeben und **Regel testen** auswählen.

![Testen einer Zuordnungsregel](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> Es dauert einige Minuten, bis der Dienst Regeln verwendet, die gespeichert wurden. Im Browser wird die Regel sofort verwendet.

### <a name="limitations-for-mapping-rules"></a>Einschränkungen für Zuordnungsregeln

Die Zuordnung für die zu konfigurierende Datenquelle. Dies ist keine globale Einstellung. Wenn Sie über mehrere Analysis Services-Datenquellen verfügen, müssen Sie die Benutzer für jede Datenquelle zuordnen.

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Authentifizierung gegenüber einer Analysis Services-Livedatenquelle

Bei jeder Interaktion eines Benutzers mit Analysis Services, wird der effektive Benutzername an das Gateway und von dort aus an Ihren lokalen Analysis Services-Server übergeben. Als effektiver Benutzer wird der Benutzerprinzipalname (UPN) – üblicherweise die E-Mail-Adresse, mit der Sie sich in der Cloud anmelden – an Analysis Services übergeben. Der UPN wird in der Verbindungseigenschaft „EffectiveUserName“ übergeben. Diese E-Mail-Adresse muss mit einem in der lokalen Active Directory-Domäne definierten UPN übereinstimmen. Der UPN ist eine Eigenschaft des Active Directory-Kontos. Das Windows-Konto muss dann in einer Analysis Services-Rolle vorhanden sein, um Zugriff auf den Server zu erhalten. Die Anmeldung wird nicht erfolgreich durchgeführt, wenn in Active Directory keine Übereinstimmung gefunden werden kann.

Analysis Services kann darüber hinaus eine Filterfunktion basierend auf diesem Konto bereitstellen. Es kann sowohl auf Grundlage eines rollenbasierten Sicherheitsmodells als auch auf Grundlage eines Sicherheitsmodells auf Zeilenebene gefiltert werden.

## <a name="role-based-security"></a>Rollenbasierte Sicherheit

Modelle stellen Sicherheit auf der Grundlage von Benutzerrollen bereit. Rollen werden für ein bestimmtes Modellprojekt während der Erstellung in den SQL Server Data Tools – Business Intelligence (SSDT-BI) oder nach der Bereitstellung des Modells mithilfe von SQL Server Management Studio (SSMS) definiert. Rollen enthalten Mitglieder, die anhand ihres Windows-Benutzernamens oder ihrer Windows-Gruppe angegeben sind. Rollen definieren die Berechtigungen eines Benutzers zu Abfragen oder Aktionen im Modell. In der Praxis werden die meisten Benutzer einer Rolle mit Leseberechtigungen angehören. Andere Rollen sind für Administratoren mit der Berechtigung zum Verarbeiten von Elementen, Verwalten von Datenbankfunktionen und Verwalten anderer Rollen vorgesehen.

## <a name="row-level-security"></a>Sicherheit auf Zeilenebene

Sicherheit auf Zeilenebene ist eine für Analysis Services charakteristische Funktion. Modelle können dynamische Sicherheitseinstellungen auf Zeilenebene bereitstellen. Im Gegensatz zu Rollen, von denen mindestens eine erforderlich ist, die Benutzer enthält, ist dynamische Sicherheit für tabellarische Modelle grundsätzlich nicht erforderlich. Allgemein ausgedrückt definiert dynamische Sicherheit den Lesezugriff eines Benutzers auf Daten bis hinunter zu einer bestimmten Zeile in einer bestimmten Tabelle. Ähnlich wie Rollen beruht dynamische Sicherheit auf Zeilenebene auf den Windows-Benutzernamen von Benutzern.

Die Berechtigung eines Benutzers, Daten des Modells abzufragen und anzuzeigen, wird erstens durch die Rollen bestimmt, deren Mitglied sein Windows-Benutzerkonto ist, und zweitens durch die dynamische Sicherheit auf Zeilenebene, sofern sie konfiguriert ist.

Das Implementieren von rollenbasierter Sicherheit und dynamischer Sicherheit auf Zeilenebene in Modellen würde den Rahmen dieses Artikels sprengen. Weitere Informationen finden Sie unter [Rollen (SSAS – tabellarisch)](https://msdn.microsoft.com/library/hh213165.aspx) und [Sicherheitsrollen (Analysis Services – mehrdimensionale Daten)](https://msdn.microsoft.com/library/ms174840.aspx) auf MSDN. Eine besonders fundierte Darstellung der Sicherheit in tabellarischen Modellen finden Sie im Whitepaper [Securing the Tabular BI Semantic Model](https://msdn.microsoft.com/library/jj127437.aspx) (Sichern des semantischen BI-Tabellenmodells).

## <a name="what-about-azure-active-directory"></a>Welche Rolle spielt Azure Active Directory?

Die Clouddienste von Microsoft verwenden [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) für die Authentifizierung von Benutzern. Azure Active Directory ist der Mandant, der die Benutzernamen und Sicherheitsgruppen enthält. In der Regel entspricht die E-Mail-Adresse, mit der sich ein Benutzer anmeldet, dem UPN des Kontos.

Welcher Rolle gehört mein lokales Active Directory an?

Damit Analysis Services bestimmen kann, ob ein Benutzer, der eine Verbindung mit ihm herstellt, einer Rolle angehört, die über Berechtigungen zum Lesen von Daten verfügt, muss der Server den von AAD an das Gateway und an den Analysis Services-Server übergebenen effektiven Benutzernamen konvertieren. Der Analysis Services-Server übergibt den effektiven Benutzernamen an einen Windows Active Directory-Domänencontroller (DC). Der Active Directory-DC überprüft dann, ob der effektive Benutzername ein gültiger UPN ist, und gibt den Windows-Benutzernamen des betreffenden Benutzers an den Analysis Services-Server zurück.

EffectiveUserName kann nicht auf einem Analysis Services-Server verwendet werden, der nicht mit der Domäne verknüpft ist. Der Analysis Services-Server muss einer Domäne angehören, um Anmeldefehler zu vermeiden.

### <a name="how-do-i-tell-what-my-upn-is"></a>Woher weiß ich meinen UPN?

Sie kennen möglicherweise nicht Ihren UPN und sind auch kein Domänenadministrator. Sie können den folgenden Befehl von Ihrer Arbeitsstation ausführen, um den UPN für Ihr Konto zu ermitteln.

    whoami /upn

Das Ergebnis ähnelt einer E-Mail-Adresse, es handelt sich aber um den UPN für Ihr Domänenkonto. Wenn Sie eine Analysis Services-Datenquelle für Liveverbindungen verwenden und dies nicht die E-Mail-Adresse ist, mit der Sie sich bei Power BI anmelden, lesen Sie die Informationen unter [Zuordnen von Benutzernamen](#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synchronisieren eines lokalen Active Directorys mit Azure Active Directory

Ihre lokalen Active Directory-Konten sollten denen in Azure Active Directory entsprechen, wenn Sie planen, Analysis Services-Liveverbindungen zu verwenden. Ebenso wie der UPN der Konten übereinstimmen muss.

Die Clouddienste haben nur Kenntnis von Konten in Azure Active Directory. Es spielt keine Rolle, wenn Sie ein Konto in Ihrem lokalen Active Directory hinzufügen. Wenn es in AAD nicht vorhanden ist, kann es nicht verwendet werden. Es gibt verschiedene Möglichkeiten, Ihre lokalen Active Directory-Konten mit Azure Active Directory abzugleichen.

1. Sie können Konten in Azure Active Directory manuell hinzufügen.

   Sie können im Azure-Portal oder im Microsoft 365 Admin Center ein Konto erstellen, bei dem der Kontoname dem UPN des lokalen Active Directory Domain Services-Kontos entspricht.

2. Sie können das [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis)-Tool verwenden, um lokale Konten mit Ihrem Azure Active Directory-Mandanten zu synchronisieren.

   Das Azure AD Connect-Tool umfasst Optionen für die Verzeichnissynchronisierung und das Einrichten der Authentifizierung wie die Kennworthashsynchronisierung, die Passthrough-Authentifizierung und den Verbund. Wenn Sie weder ein Mandantenadministrator noch ein lokaler Domänenadministrator sind, müssen Sie sich für diese Konfiguration an Ihren IT-Administrator wenden.

Mit Azure AD Connect können Sie sicherstellen, dass der UPN Ihres AAD-Kontos und der Ihres lokalen Active Directory-Kontos übereinstimmen.

> [!NOTE]
> Das Synchronisieren von Konten mithilfe des Azure AD Connect-Tools erstellt neue Konten in Ihrem AAD-Mandanten.

## <a name="using-the-data-source"></a>Verwenden der Datenquelle

Nachdem Sie die Datenquelle erstellt haben, kann diese mit Liveverbindungen oder durch eine geplante Aktualisierung verwendet werden.

> [!NOTE]
> Die Namen des Servers und der Datenbank müssen in Power BI Desktop und der Datenquelle innerhalb des lokalen Datengateways übereinstimmen.

Der Link zwischen Ihrem Dataset und der Datenquelle innerhalb des Gateways basiert auf dem Namen Ihres Servers und Ihrer Datenbank. Diese müssen übereinstimmen. Wenn Sie z.B. eine IP-Adresse für den Servernamen in Power BI Desktop angeben, müssen Sie die IP-Adresse für die Datenquelle innerhalb der Gatewaykonfiguration verwenden. Wenn Sie *SERVER\INSTANZ* verwenden, müssen Sie in Power BI Desktop dieselbe Instanz verwenden, die auch in der für das Gateway konfigurierten Datenquelle verwendet wird.

Dies gilt für Liveverbindungen ebenso wie für geplante Aktualisierungen.

### <a name="using-the-data-source-with-live-connections"></a>Verwenden der Datenquelle mit Liveverbindungen

Stellen Sie sicher, dass die Namen des Servers und der Datenbank in Power BI Desktop und der für das Gateway konfigurierten Datenquelle übereinstimmen. Stellen Sie außerdem sicher, dass der Benutzer auf der Registerkarte **Benutzer** der Datenquelle aufgeführt ist, um Datasets über eine Liveverbindung veröffentlichen zu können. Sie treffen die Auswahl für Liveverbindungen in Power BI Desktop beim Importieren der Daten.

Nach der Veröffentlichung von Power BI Desktop oder mit **Daten abrufen** sollten Ihre Berichte funktionieren. Es kann nach dem Erstellen der Datenquelle im Gateway mehrere Minuten dauern, bis die Verbindung genutzt werden kann.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Verwenden der Datenquelle mit geplanten Aktualisierungen

Wenn Sie auf der Registerkarte **Benutzer** der im Gateway konfigurierten Datenquelle aufgeführt sind und die Namen des Servers und der Datenbank übereinstimmen, wird das Gateway als Option für geplante Aktualisierungen angezeigt.

![Anzeigen der Benutzer](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Einschränkungen der Liveverbindungen von Analysis Services

Sie können eine Liveverbindung für tabellarische oder mehrdimensionale Instanzen verwenden.

| **Serverversion** | **Erforderliche SKU** |
| --- | --- |
| 2012 SP1 CU4 oder höher |Business Intelligence und Enterprise SKU |
| 2014 |Business Intelligence und Enterprise SKU |
| 2016 |Standard-SKU oder höher |

* Die Formatierung auf Zellenebene sowie Übersetzungsfunktionen werden nicht unterstützt.
* Aktionen und benannte Mengen werden nicht für Power BI verfügbar gemacht. Dennoch können Sie eine Verbindung mit mehrdimensionalen Cubes herstellen, die auch Aktionen oder benannte Mengen enthalten, und Sie können entsprechende Visualisierungen und Berichte erstellen.

## <a name="next-steps"></a>Nächste Schritte

* [Problembehandlung beim lokalen Datengateway](/data-integration/gateway/service-gateway-tshoot)
* [Lokales Datengateway – Power BI](service-gateway-onprem-tshoot.md)

Weitere Fragen? [Wenden Sie sich an die Power BI-Community](http://community.powerbi.com/)

